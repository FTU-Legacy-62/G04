**Thành viên: **

Ngô Thị Diễm Phúc - MSV: 2312380804

**1. Vai trò trong dự án**

Tôi đảm nhiệm ba trách nhiệm chính trong suốt quá trình thực hiện dự án.

Với vai trò là Backend Developer, tôi chịu trách nhiệm phát triển logic
tài chính cốt lõi và logic gameplay của hệ thống, bao gồm việc triển
khai các hàm calculate_metrics, final_score, và process_phase. Các thành
phần này tạo thành nền tảng cho cơ chế đánh giá tài chính, cơ chế tính
điểm và quy trình xử lý theo từng phase của game.

Với vai trò là Input Structure Designer, tôi thiết kế biểu mẫu nộp dự án
được sử dụng trong play.html, xác định các trường thông tin đầu vào bắt
buộc, kiểu dữ liệu, ràng buộc kiểm tra hợp lệ và các khoảng giá trị được
chấp nhận. Tôi cũng xây dựng cấu trúc đầu vào của người chơi, trong đó
quy định các thông tin tài chính và vận hành mà mỗi người chơi cần cung
cấp khi tạo một dự án.

Với vai trò là Tester, tôi thực hiện kiểm thử thủ công toàn bộ game sau
mỗi lần tích hợp code quan trọng. Công việc này bao gồm xác minh chức
năng hệ thống, xác định lỗi và các trường hợp biên, ghi nhận vấn đề và
trao đổi báo cáo lỗi với các thành viên liên quan trong nhóm để xử lý.

**2. Dấu ấn cá nhân trong sản phẩm**

Một trong những đóng góp chính của tôi là thiết kế và triển khai hệ
thống nộp dự án và đánh giá tài chính. Tôi đã thiết kế toàn bộ Project
Submission Form, đây là giao diện chính để người chơi tạo và nộp các dự
án startup của mình. Biểu mẫu được cấu trúc thành sáu nhóm đầu vào tài
chính và vận hành, bao gồm quy mô dự án, giá bán và kênh bán hàng, cơ
cấu chi phí, dự báo sản xuất, chi phí vận hành và cơ cấu vốn. Để đảm bảo
cả tính dễ sử dụng và sự cân bằng của game, tôi xác định các giá trị mặc
định, ràng buộc kiểm tra hợp lệ, khoảng giá trị được chấp nhận và
tooltip giải thích cho từng trường. Nhờ đó, biểu mẫu cung cấp một nguồn
dữ liệu dự án nhất quán và đáng tin cậy cho toàn bộ mô phỏng.

Dựa trên cấu trúc đầu vào này, tôi triển khai hàm calculate_metrics()
trong app.py, đóng vai trò là công cụ đánh giá tài chính cốt lõi của
game. Hàm này xử lý dữ liệu do người chơi nộp và tạo ra một tập hợp đầy
đủ các chỉ số tài chính, bao gồm intrinsic score, valuation sanity, ROI
norm, monthly burn, available cash, runway, funding progress, estimated
valuation, raw ROI, và regulatory risk. Các chỉ số này cung cấp đánh giá
định lượng về hiệu quả dự án và mức độ hấp dẫn đầu tư, tạo cơ sở cho cả
quá trình ra quyết định của investor bot và hệ thống leaderboard. Do đó,
project submission form và financial metrics engine cùng nhau cấu thành
một phần quan trọng trong chức năng cốt lõi của game, kết nối đầu vào
của người chơi với kết quả đầu tư và tiến trình gameplay tổng thể.

**3. Các nhiệm vụ thực tế đã thực hiện**

**3.1. Thiết kế Project Input Form**

Tôi chịu trách nhiệm thiết kế project submission form được người chơi sử
dụng để tạo hồ sơ startup trong game. Công việc này bao gồm xác định sáu
nhóm thông tin cần thiết cho việc đánh giá tài chính, cụ thể là project
scale, pricing and sales channels, cost of goods sold (COGS), production
forecasts, fixed operating costs, và capital structure. Với mỗi nhóm,
tôi xác định các trường đầu vào cụ thể mà người chơi bắt buộc phải hoàn
thành.

Thay vì sử dụng các đầu vào được tổng hợp ở mức quá cao, tôi thiết kế
một số trường với mức độ chi tiết lớn hơn nhằm cải thiện độ chính xác
của các phép tính tài chính. Ví dụ, COGS được tách thành material cost,
packaging cost, labour cost, và defect rate, cho phép hệ thống backend
tính gross margin một cách thực tế hơn. Ngoài ra, tôi thiết lập các ràng
buộc kiểm tra hợp lệ, khoảng giá trị được chấp nhận và đơn vị đo lường
cho tất cả các trường nhằm ngăn các đầu vào phi thực tế hoặc không hợp
lệ ảnh hưởng đến mô phỏng. Tôi cũng chuẩn bị nội dung giải thích được
hiển thị trong các information modal liên kết với từng phần của biểu
mẫu, giúp người chơi hiểu mục đích, đơn vị và khoảng giá trị được chấp
nhận của từng đầu vào mà không cần tham khảo tài liệu bên ngoài.

  -------------------------------------------------------------------------------
  **Group**    **Input      **Short Description**  **Unit**    **Constraints**
               Name**                                          
  ------------ ------------ ---------------------- ----------- ------------------
  Scale        Project size Chọn quy mô dự án:                 Small / Medium /
                            Small (5 phases),                  Large
                            Medium (7 phases),                 
                            Large (9 phases).                  

  Price &      Retail price Giá niêm yết của một   USD         10--1000
  Channels                  sản phẩm trước khi trừ             
                            bất kỳ khoản phí kênh              
                            nào.                               

  Price &      E-commerce   Phí nền tảng cho các   \%          0--100
  Channels     fee          marketplace trực                   
                            tuyến, ví dụ Shopee,               
                            Amazon.                            

  Price &      Retail fee   Chiết khấu thương      \%          0--100
  Channels                  mại/biên lợi nhuận                 
                            dành cho các đối tác               
                            bán lẻ vật lý, ví dụ               
                            siêu thị, cửa hàng                 
                            tiện lợi.                          

  Price &      Direct       Chi phí bán hàng thông \%          0--100
  Channels     channel fee  qua website hoặc                   
                            fanpage riêng, ví dụ               
                            payment gateway.                   

  COGS         Direct       Nguyên vật liệu, linh  USD         0.1--100
               materials    kiện hoặc bộ phận được             
                            sử dụng để sản xuất                
                            một sản phẩm.                      

  COGS         Direct       Chi phí hộp, túi, nhãn USD         0.1--100
               packaging    hoặc hướng dẫn sử dụng             
                            cho một sản phẩm.                  

  COGS         Direct labor Tiền lương của công    USD         0.1--100
                            nhân nhà máy lắp ráp               
                            hoặc xử lý sản phẩm,               
                            được tính biến đổi                 
                            theo từng đơn vị.                  

  COGS         Defect       Tỷ lệ phần trăm sản    \%          0--10
               allowance    phẩm bị mất do hư                  
               (%)          hỏng, làm lại hoặc vấn             
                            đề chất lượng.                     

  Production   Month 1      Số lượng sản phẩm dự   units       0--100,000
  Forecast     units        kiến bán ra trong                  
                            tháng đầu tiên sau khi             
                            ra mắt.                            

  Production   Month 3      Doanh số dự kiến trong units       0--100,000
  Forecast     units        tháng thứ 3 sau khi ra             
                            mắt.                               

  Production   Month 6      Doanh số hàng tháng dự units       0--100,000
  Forecast     units        kiến sau 6 tháng kể từ             
                            khi ra mắt.                        

  Monthly      Fixed        Chi phí hàng tháng     USD/month   1,000--100,000
  Operating    operating    KHÔNG thay đổi theo                
  Costs        cost         sản lượng: tiền thuê               
                            văn phòng, lương quản              
                            lý, tiện ích, v.v.                 

  Monthly      Marketing    Ngân sách hàng tháng   USD/month   0--100,000
  Operating    cost         cho quảng cáo, khuyến              
  Costs                     mãi, influencer                    
                            campaigns.                         

  Capital      Owner equity Tiền mặt do            USD         0--300,000
  Structure                 founders/co-founders               
                            đầu tư.                            

  Capital      Bank loan    Khoản vay từ ngân hàng USD         0--300,000
  Structure                 hoặc quỹ nợ.                       

  Capital      Loan         Lãi suất hằng năm của  %/year      5--100
  Structure    interest     khoản vay.                         
               rate                                            

  Capital      Equity       Tỷ lệ phần trăm công   \%          0.1--99.9
  Structure    offered (%)  ty được bán cho nhà                
                            đầu tư trong vòng gọi              
                            vốn này.                           

               Target       Số tiền mà người chơi  USD         Small:
               funding      đặt mục tiêu huy động              30,000--99,999
                            từ nhà đầu tư.                     Medium:
                                                               100,000--251,999
                                                               Large:
                                                               252,000--500,000
  -------------------------------------------------------------------------------

Table 1. Input table

**3.2. Phát triển Backend Financial Engine**

Tôi phát triển công cụ đánh giá tài chính cốt lõi của game, chủ yếu
thông qua việc triển khai hàm calculate_metrics(proj). Hàm này xử lý dữ
liệu dự án thô do người chơi nộp và tạo ra các chỉ số tài chính được sử
dụng xuyên suốt mô phỏng. Các chỉ số này bao gồm sáu thành phần của
intrinsic score --- gross margin, burn rate, growth potential, revenue
scale, capital efficiency, và leverage --- cũng như valuation sanity,
ROI norm, estimated valuation, runway, và regulatory risk.

Trong các lần phát triển sau đó, tôi tinh chỉnh mô hình đánh giá bằng
cách đưa security và regulatory risk penalties vào quá trình tính
intrinsic score. Các khoản penalty này làm giảm mức độ hấp dẫn của dự án
khi các chỉ số liên quan đến compliance hoặc security thấp hơn ngưỡng
được chấp nhận, qua đó khuyến khích chiến lược người chơi cân bằng và
thực tế hơn.

Tôi cũng triển khai hàm final_score(proj, phases_used, metrics), có chức
năng xác định thứ hạng cuối cùng của người chơi khi game kết thúc. Mô
hình tính điểm kết hợp bốn khía cạnh --- fundraising performance,
fundraising speed, return on investment, và transparency --- đồng thời
áp dụng các hệ số điều chỉnh bổ sung và funding bonuses để phản ánh
project size và fundraising outcomes.

  ---------------------------------------------------------------------------------------------------------------
  **Indicator /         **Formula in Code**                              **Why This         **Why Needed in
  Component**                                                            Metric**           Game**
  --------------------- ------------------------------------------------ ------------------ ---------------------
  Step 0                Step 0 -Pre-processing (shared by all indicators Step 0             Step 0
  -Pre-processing       below)                                           -Pre-processing    -Pre-processing
  (shared by all                                                         (shared by all     (shared by all
  indicators below)                                                      indicators below)  indicators below)

  price_real            total_fees = fee_ecom + fee_retail + fee_direct  Doanh thu ròng     Nếu không có bước
                        price_real = price × (1 − total_fees/100)        thực tế trên mỗi   này, gross margin sẽ
                                                                         đơn vị sau khi trả bị tính sai --- một
                                                                         commission cho các dự án có thể trông có
                                                                         kênh. Người chơi   vẻ có lợi nhuận nhưng
                                                                         nhập một mức giá   thực tế lại mất tiền
                                                                         duy nhất, nhưng    cho các kênh. Bot sẽ
                                                                         doanh thu thực tế  bị dẫn dắt sai và đầu
                                                                         phải trừ phí kênh. tư vào các dự án yếu.

  cogs_unit             cogs_unit = (material + packaging + labor) ×     Chi phí sản xuất   Việc tách COGS thành
                        (1 + defect_rate/100)                            thực tế trên mỗi   4 trường theo thiết
                                                                         đơn vị, bao gồm tỷ kế form phản ánh cơ
                                                                         lệ hao hụt.        cấu chi phí thực. Các
                                                                         defect_rate 5% có  dự án cần nhiều lao
                                                                         nghĩa là cần sản   động bị penalty mạnh
                                                                         xuất 105 đơn vị để hơn khi defect_rate
                                                                         bán được 100 đơn   cao.
                                                                         vị.                

  monthly_burn          monthly_burn = fixed_cost + marketing_cost +     Tổng dòng tiền bắt Đây là chỉ số sinh
                        loan × interest_rate/100/12                      buộc phải chi hằng tồn quan trọng: một
                                                                         tháng, không phụ   startup hết tiền
                                                                         thuộc vào sản      trước khi huy động đủ
                                                                         lượng bán hàng.    vốn sẽ phá sản. Chỉ
                                                                         Bao gồm fixed      số này được sử dụng
                                                                         costs, marketing,  để tính burn_score,
                                                                         và lãi vay hằng    runway, và kiểm tra
                                                                         tháng.             bankruptcy trong
                                                                                            process_phase.

  Group A -Intrinsic    Group A -Intrinsic Score (max 100 points, 6      Group A -Intrinsic Group A -Intrinsic
  Score (max 100        components)                                      Score (max 100     Score (max 100
  points, 6 components)                                                  points, 6          points, 6 components)
                                                                         components)        

  gm_score (0--30 pts)  gm = (price_real − cogs_unit) / price_real if gm Gross margin đo    Bot sử dụng intrinsic
                        \> 0.2: score = 20 + 10×(1−e\^{−5×(gm−0.2)/0.6}) lường lợi nhuận    score làm cơ sở cho
                        else: score = max(0, 20×(gm/0.2))                gộp trên mỗi đơn   quyết định đầu tư.
                                                                         vị doanh thu. Đây  gm_score có trọng số
                                                                         là thành phần có   cao nhất vì trong các
                                                                         trọng số cao nhất  startup thực tế,
                                                                         (30 pts) vì là chỉ gross margin là chỉ
                                                                         số nền tảng nhất   số đầu tiên mà nhà
                                                                         --- một dự án có   đầu tư xem xét --- nó
                                                                         margin âm không    cho thấy còn lại bao
                                                                         thể tồn tại dài    nhiêu để trang trải
                                                                         hạn. Hàm mũ phía   fixed costs và tạo
                                                                         trên 0.2 thưởng    lợi nhuận.
                                                                         cho các dự án có   
                                                                         margin cao nhưng   
                                                                         với hiệu ứng lợi   
                                                                         ích biên giảm dần. 

  burn_score (0--20     burn_rate = monthly_burn / target_funding if     Burn rate = tỷ lệ  Một dự án có burn
  pts)                  burn_rate \< 0.3: score = 15 +                   giữa chi phí hằng  rate cao sẽ hết tiền
                        5×(1−e\^{−4×(0.3−r)/0.25}) else: score = max(0,  tháng và tổng      trước khi hoàn tất
                        15×(1−(r−0.3)/0.7))                              target funding.    vòng gọi vốn. Bot cần
                                                                         Chỉ số này đo tốc  nhận diện điều này
                                                                         độ startup đốt     --- nếu không, bot sẽ
                                                                         tiền. Ngưỡng 0.3   đầu tư vào các
                                                                         có nghĩa là khi    startup sắp phá sản.
                                                                         chi tiêu hằng      burn_score tự nhiên
                                                                         tháng vượt 30%     định hướng bot tránh
                                                                         target funding thì xa các dự án "high
                                                                         bắt đầu bị         burn, low runway".
                                                                         penalty.           

  growth_score (0--20   growth = (units_m6 / units_m1) − 1 if growth \>  Tỷ lệ tăng trưởng  Game mô phỏng nhiều
  pts)                  0: score = 10 + 10×(1−e\^{−3×g/0.5}) else: score sản lượng từ tháng phase. Một dự án có
                        = max(0, 10×(1+g/0.5))                           1 đến tháng 6, đo  tăng trưởng sản lượng
                                                                         lường động lực     mạnh sẽ tự nhiên thu
                                                                         phát triển của dự  hút bot qua nhiều
                                                                         án. Hàm mũ thưởng  vòng --- điều này
                                                                         cho tăng trưởng    thực tế vì nhà đầu tư
                                                                         nhanh với lợi ích  không chỉ xem trạng
                                                                         biên giảm dần ---  thái hiện tại mà còn
                                                                         ngăn người chơi    xem quỹ đạo phát
                                                                         khai thác hệ thống triển.
                                                                         bằng cách nhập     
                                                                         units_m6 quá cao.  

  revenue_score (0--10  avg_units = (units_m1 + units_m6) / 2            Doanh thu hằng năm revenue_year cũng
  pts)                  revenue_year = avg_units × 12 × price_real score dự kiến, được      được sử dụng để tính
                        = min(10, log10(revenue_year/100000)/2 × 10)     scale theo log.    estimated_valuation
                                                                         Thang log có nghĩa thông qua P/S ratio.
                                                                         là một dự án \$1B  Các dự án có doanh
                                                                         không được điểm    thu cao hơn nhận
                                                                         cao gấp 10 lần một valuation cao hơn ---
                                                                         dự án \$100M ---   nhưng không tuyến
                                                                         phản ánh cách nhà  tính. Trọng số 10
                                                                         đầu tư thực sự     pts, thấp hơn GM và
                                                                         đánh giá quy mô    burn, vì quy mô quan
                                                                         tuyệt đối.         trọng nhưng kém quan
                                                                                            trọng hơn efficiency.

  efficiency_score      annual_profit = (price_real−cogs_unit) ×         ROE (Return on     Một startup sử dụng
  (0--10 pts)           units_m6×12 − burn×12 roe = annual_profit /      Equity) đo lợi     vốn hiệu quả tạo ra
                        total_capital score = min(10, roe×10)            nhuận tạo ra trên  nhiều lợi nhuận hơn
                                                                         mỗi đơn vị vốn.    đối thủ với cùng một
                                                                         Không giống        lượng vốn. Bot cần
                                                                         gm_score chỉ đo tỷ phân biệt giữa
                                                                         lệ, chỉ số này đo  "profitable" và
                                                                         lợi nhuận tuyệt    "efficient" --- hai
                                                                         đối sau fixed      khái niệm này không
                                                                         costs --- một dự   giống nhau.
                                                                         án có margin cao   
                                                                         nhưng fixed costs  
                                                                         quá lớn sẽ bị      
                                                                         penalty tại đây.   

  leverage_score (0--10 debt_ratio = loan / owner_equity if ratio \<     Đánh giá cấu trúc  Phản ánh nguyên lý
  pts)                  0.5: score = 5 + ratio×10 elif ratio ≤ 1.5:      debt-to-equity.    tài chính: một mức nợ
                        score = 10−(ratio−0.5)×5 else: score = max(0,    Hàm hình thang: tỷ nhất định là tốt do
                        5−(ratio−1.5)×3)                                 lệ thấp (0--0.5)   tạo leverage, nhưng
                                                                         nhận điểm trung    quá nhiều nợ là nguy
                                                                         bình vì quá thận   hiểm. Một dự án tài
                                                                         trọng; tỷ lệ vừa   trợ hoàn toàn bằng
                                                                         phải (0.5--1.5)    equity sẽ bỏ lỡ lợi
                                                                         nhận điểm cao nhất ích leverage; các dự
                                                                         vì leverage tốt;   án over-leveraged sẽ
                                                                         tỷ lệ cao (\>1.5)  thấy monthly_burn
                                                                         bị penalty vì rủi  tăng do lãi vay và
                                                                         ro mất khả năng    đối mặt với nguy cơ
                                                                         thanh toán.        bankruptcy cao hơn.

  security_penalty &    sec_pen = max(0, (50−security)/5) reg_pen =      Trừ điểm intrinsic Được bổ sung sau khi
  reg_risk_penalty      reg_risk / 10 intrinsic = max(0,                 đối với các dự án  kiểm thử cho thấy bot
                        intrinsic−sec_pen−reg_pen)                       bỏ qua security và không thể phân biệt
                                                                         regulatory         các dự án thiếu cẩn
                                                                         compliance. Mỗi 5  trọng về compliance.
                                                                         điểm security dưới Các penalty này buộc
                                                                         50 bị trừ 1 pt;    người chơi phải cân
                                                                         mỗi 10% reg_risk   nhắc security và
                                                                         bị trừ 1 pt. Áp    licensing --- không
                                                                         dụng sau khi cả 6  chỉ tối ưu tài chính.
                                                                         components đã được 
                                                                         tính.              

  Group B -Valuation &  Group B -Valuation & ROI                         Group B -Valuation Group B -Valuation &
  ROI                                                                    & ROI              ROI

  estimated_valuation   ps_ratio = 3.0 (baseline) if hype\>70: ps_ratio  Sử dụng P/S ratio  Valuation là kết quả
                        += 2 elif hype\<30: ps_ratio −= 1 if             (Price-to-Sales)   quan trọng mà người
                        growth\>0.5: ps_ratio += 1.5 ps_ratio =          --- phương pháp    chơi nhìn thấy trên
                        clamp(ps_ratio, 1.5, 15) valuation =             định giá phổ biến  dashboard. Hype ảnh
                        revenue_year × ps_ratio                          cho các startup    hưởng đến P/S vì
                                                                         chưa có lợi nhuận. trong thực tế, các
                                                                         Mức baseline là    startup "hot" luôn
                                                                         3×, được điều      được định giá cao hơn
                                                                         chỉnh theo hype    fundamentals --- điều
                                                                         (market sentiment) này phản ánh chính
                                                                         và growth.         xác thị trường VC.
                                                                         clamp(1.5, 15)     
                                                                         ngăn valuation phi 
                                                                         lý.                

  roi_norm              raw_roi = max(0,                                 ROI được chuẩn hóa final_score sử dụng
                        (valuation−total_invested)/total_invested×100)   về \[0, 100\] bằng roi_norm để tính
                        roi_norm = min(100, 20×log10(raw_roi+1))         hàm log để tránh   roi_score. Bot cũng
                                                                         outlier. Một dự án sử dụng nó gián tiếp
                                                                         ROI 10% và 1000%   thông qua
                                                                         không nên khác     attractiveness(). Các
                                                                         nhau 100 lần về    dự án có ROI tốt giữ
                                                                         điểm --- thang log được khoản đầu tư của
                                                                         làm mượt khoảng    bot qua nhiều phase.
                                                                         cách này.          

  valuation_sanity      mult = valuation / revenue_year if mult \< 1:    Kiểm tra valuation Ngăn người chơi thao
                        score = 30−(1−mult)/1×30 elif mult ≤ 3: score =  có "healthy" hay   túng revenue_year để
                        80+(mult−1)/2×20 elif mult ≤ 5: score =          không --- P/S      làm tăng valuation
                        80−(mult−3)/2×40 else: score = max(0,            1--3× được xem là  một cách giả tạo. Bot
                        40−(mult−5)/2×40)                                hợp lý và nhận     nhận diện các dự án
                                                                         điểm cao nhất; P/S overvalued và đầu tư
                                                                         \<1, tức           ít hơn --- tương tự
                                                                         undervalued, hoặc  cách các VC thực tế
                                                                         \>5, tức           từ chối các thương vụ
                                                                         overvalued, bị     có mức giá chào quá
                                                                         penalty. Hàm hình  cao.
                                                                         thang phản ánh     
                                                                         vùng valuation tối 
                                                                         ưu.                

  reg_risk              base = 20 if has_license else 80 if legal_cost ≥ Regulatory risk    Được sử dụng trong
                        5% target_funding: base += 20 reg_risk =         tổng hợp từ: có    reg_risk_penalty, tức
                        clamp(base−transparency/10, 0, 100)              license (−60       trừ intrinsic, và
                                                                         risk), đầu tư vào  trong
                                                                         legal costs (−20   attractiveness() của
                                                                         risk),             bot. Các dự án có
                                                                         transparency cao   reg_risk cao bị bot
                                                                         làm giảm thêm rủi  tránh né --- phản ánh
                                                                         ro. Đây là chỉ số  rằng regulatory risk
                                                                         ngược --- càng cao là lý do phổ biến
                                                                         càng xấu.          nhất khiến startup
                                                                                            thất bại tại Việt
                                                                                            Nam.

  runway                avail = available_cash (or equity + loan) runway Số tháng một       process_phase sử dụng
                        = floor(avail / monthly_burn) = 999 if           startup có thể tồn runway, gián tiếp
                        monthly_burn = 0                                 tại với lượng tiền thông qua
                                                                         mặt hiện tại. Đây  available_cash, để
                                                                         là chỉ số đơn giản kiểm tra bankruptcy
                                                                         nhưng quan trọng   sau mỗi phase. Người
                                                                         nhất: nếu runway   chơi nhìn thấy runway
                                                                         \< remaining       trên dashboard ---
                                                                         phases, dự án gần  đây là chỉ số trực
                                                                         như chắc chắn phá  quan nhất về thời
                                                                         sản trước khi huy  gian còn lại.
                                                                         động đủ vốn.       
  ---------------------------------------------------------------------------------------------------------------

Table 2. Calculate_metrics(proj): All Financial Indicators

  -------------------------------------------------------------------------------------------------
  **Component**   **Formula in Code**                       **Weight &           **Why Needed in
                                                            Rationale**          Game**
  --------------- ----------------------------------------- -------------------- ------------------
  funding_score   funding_score = funding_progress × 40     Trọng số 40% --- cao Nếu funding_score
  (max 40 pts)                                              nhất. Lý do: mục     chỉ chiếm 20--25%,
                                                            tiêu cốt lõi của     người chơi có thể
                                                            game là fundraising  thắng mà không huy
                                                            thành công. Một dự   động đủ funding,
                                                            án huy động được     làm mất logic cốt
                                                            100% target nhận 40  lõi của game. 40%
                                                            pts; 50% nhận 20     đảm bảo mục tiêu
                                                            pts. Trọng số cao    chính không thể bị
                                                            nhất đảm bảo điều    bỏ qua.
                                                            kiện chiến thắng     
                                                            chính được phản ánh  
                                                            mạnh nhất trong điểm 
                                                            số.                  

  speed_score     if complete_phase is not None: speed =    Trọng số 20%. Công   Tạo cạnh tranh khi
  (max 20 pts)    20×(1−(complete_phase−1)/(max_phase−1))   thức tuyến tính:     nhiều người chơi
                  else: speed = 0                           hoàn thành ở phase 1 đều huy động đủ
                                                            nhận 20 pts, hoàn    funding. Nếu không
                                                            thành ở phase cuối   có speed_score,
                                                            nhận 0 pts. Trọng số game sẽ trở nên
                                                            bằng với roi_score   phẳng khi mọi
                                                            và trans_score:      người đều hoàn
                                                            speed là lợi thế     thành. Đồng thời
                                                            cạnh tranh, không    phản ánh thực tế:
                                                            phải yêu cầu bắt     gọi vốn nhanh giúp
                                                            buộc --- quan trọng  tiết kiệm burn và
                                                            nhưng không quan     tận dụng tốt hơn
                                                            trọng hơn ROI.       market timing.

  roi_score (max  roi_score = min(20, (roi_norm/100) × 20)  Trọng số 20%.        Thưởng cho người
  20 pts)                                                   roi_norm đã được     chơi thiết kế các
                                                            chuẩn hóa về \[0,    dự án có ROI thực
                                                            100\] trong          sự cao, không chỉ
                                                            calculate_metrics,   những dự án huy
                                                            nên ánh xạ trực tiếp động đủ funding.
                                                            sang \[0, 20\]. Bằng Ngăn chiến lược
                                                            với speed_score: ROI "spam many small
                                                            tốt thể hiện thiết   investments" ---
                                                            kế dự án chất lượng  bot chỉ đầu tư
                                                            cao nhưng không phải mạnh vào các dự án
                                                            yếu tố quyết định    có ROI cao.
                                                            --- đây là yếu tố    
                                                            phân định khi cần so 
                                                            sánh.                

  trans_score     trans_score = max(0, min(20,              Trọng số 20%.        Buộc người chơi
  (max 20 pts)    (transparency/100) × 20))                 Transparency là chỉ  đầu tư vào
                                                            số người chơi xây    transparency,
                                                            dựng thông qua cards không chỉ tối ưu
                                                            và actions (0--100). tài chính. Phản
                                                            Ánh xạ tuyến tính    ánh thực tế: các
                                                            sang \[0, 20\]. Bằng startup thiếu
                                                            với trọng số ROI vì  transparency, như
                                                            transparency là điều không có audit
                                                            kiện tiên quyết mà   hoặc reporting, sẽ
                                                            nhà đầu tư yêu cầu   bị nhà đầu tư từ
                                                            --- nếu không có nó, chối ngay cả khi
                                                            ngay cả các dự án    số liệu có vẻ tốt.
                                                            ROI cao cũng bị bot  
                                                            tránh.               

  scale_factor    scale_map = {S:0.8, M:0.9, L:1.0} final = Hệ số điều chỉnh dựa Nếu không có
                  raw × scale_factor × bonus                trên project scale   scale_factor,
                                                            được chọn khi bắt    người chơi sẽ luôn
                                                            đầu game. Scale S    chọn Scale L để có
                                                            khó gọi vốn hơn nên  điểm cao hơn. Hệ
                                                            nhận 0.8, tức điểm   số này tạo
                                                            tối đa thấp hơn;     trade-off: Scale S
                                                            Scale L nhận 1.0.    huy động ít tiền
                                                            Đây không phải       hơn và có thể hoàn
                                                            penalty --- chỉ là   thành sớm, tức
                                                            cơ chế cân bằng game speed_score cao,
                                                            cho các lựa chọn     nhưng tổng điểm bị
                                                            scale khác nhau.     nhân với 0.8.

  funding_bonus   funding_bonus = (1 + funding_progress)/2  Hệ số nhân bonus ở   Nếu không có
                  final = raw × scale_factor ×              cuối game, dao động  funding_bonus, một
                  funding_bonus                             từ 0.5--1.0 dựa trên dự án huy động 60%
                                                            funding_progress. Dự và một dự án huy
                                                            án huy động 100%:    động 100% vẫn có
                                                            bonus = 1.0. Huy     thể đạt điểm tương
                                                            động 0%: bonus =     tự nếu ROI/speed
                                                            0.5, tức một nửa     tốt. Bonus này đảm
                                                            điểm. Mục đích là    bảo
                                                            khuếch đại khoảng    funding_progress
                                                            cách giữa dự án      có tác động phi
                                                            thành công và thất   tuyến --- huy động
                                                            bại.                 càng nhiều, điểm
                                                                                 tăng càng nhanh.
  -------------------------------------------------------------------------------------------------

Table 3. Final_score(proj, phases_used, metrics): End-Game Score

**3.3. Testing and Quality Assurance**

Ngoài trách nhiệm phát triển, tôi thực hiện kiểm thử rộng rãi trong suốt
vòng đời dự án.

  -------------------------------------------------------------------------------
  **No.**   **Test Scenario**                  **Expected Result**     **Actual
                                                                       Result**
  --------- ---------------------------------- ----------------------- ----------
  1         Tạo phòng 2-player, nộp project +  Mỗi player có 5 cards,  Pass
            deck, host chạy phase → game bắt   một random event xuất   
            đầu ở phase 1                      hiện ở mỗi phase        

  2         Một player chưa submitted deck,    Thông báo lỗi rõ ràng   Pass
            host chạy phase → error \'Players                          
            X have not submitted deck\'                                

  3         Player plays a card (play_card) →  Energy giảm, card biến  Pass
            energy giảm, card biến mất khỏi    mất, hype/transparency  
            hand, effects được áp dụng sau khi stats thay đổi          
            run phase                                                  

  4         Player uses Mulligan → energy      Hành vi đúng với các    Pass
            giảm, new hand (5 random cards).   thông báo lỗi rõ ràng   
            Using Mulligan twice in one phase                          
            → error. Insufficient energy for                           
            Mulligan → error                                           

  5         available_cash của một project     Log \'BANKRUPT\',       Pass
            giảm xuống 0 → bị đánh dấu         project bị loại khỏi    
            bankrupt, không tham gia các phase active play             
            tiếp theo                                                  

  6         Reaction card với điều kiện runway Trigger đúng, effect    Pass
            \<= 2 → nút \'Activate\' xuất      được áp dụng            
            hiện, sau khi sử dụng thì runway                           
            bonus được áp dụng                                         

  7         Host clicks \'End Game\' →         Scores xuất hiện        Pass
            leaderboard hiển thị temporary                             
            scores dựa trên phases completed                           

  8         Host clicks \'Reset Game\' → toàn  Reset đúng              Pass
            bộ dữ liệu được reset về trạng                             
            thái ban đầu, players có thể                               
            re-submit projects                                         

  9         Restart Flask server → rooms in    SQLite persistent       Pass
            progress vẫn tồn tại, players có   storage                 
            thể reconnect                                              

  10        4 players, mỗi player có scale     Mỗi player kết thúc ở   Pass
            khác nhau (S, M, L) → max phases   một phase khác nhau     
            khác nhau tương ứng (5, 7, 9)                              

  11        Projects đã kết thúc hoặc bankrupt Notification displayed  Pass
            --- player tiếp tục nhấn action                            
            buttons                                                    

  12        Selecting more cards than allowed  Notification displayed  Pass

  13        Không phải tất cả players đã       Host notification. Game Pass
            readied up khi host runs game do   continues normally      
            bankruptcy, eliminated players,                            
            hoặc phase limits                                          
  -------------------------------------------------------------------------------

Table 4. Test list

**4. Proof of contribution**

GitHub Commits:
<https://github.com/khanhhabao7/nhap-fintech/commits?author=ngongodiemphuc-svg>

**5. Cách đóng góp của tôi kết nối với sản phẩm cuối cùng**

Đóng góp của tôi được tích hợp xuyên suốt toàn bộ gameplay pipeline, từ
thời điểm người chơi nộp một startup project cho đến bảng xếp hạng cuối
cùng được hiển thị khi game kết thúc. Trên thực tế, hệ thống vận hành
theo một luồng liên tục gồm Form Input → Backend Financial Engine →
Investor Bots → User Interface → Reaction Cards, và tôi đã đóng góp vào
một số giai đoạn quan trọng của quy trình này.

Project submission form trong play.html đóng vai trò là điểm đầu vào cho
toàn bộ dữ liệu do người chơi tạo ra. Tôi thiết kế cấu trúc form, xác
định mười một trường đầu vào bắt buộc, thiết lập validation rules, và
lựa chọn các giá trị mặc định cũng như khoảng giá trị phù hợp. Mục tiêu
là cho phép người chơi nhập thông tin kinh doanh một cách trực quan,
chẳng hạn selling price, production costs, và projected sales volume,
đồng thời đảm bảo backend luôn nhận được dữ liệu đầy đủ và hợp lệ.

Hàm calculate_metrics() đóng vai trò là công cụ đánh giá tài chính trung
tâm của game và là điểm kết nối quan trọng nhất giữa phần việc của tôi
với đóng góp của các thành viên khác trong nhóm. Hệ thống investor bot
của Khanh phụ thuộc vào đầu ra của calculate_metrics() thông qua hàm
attractiveness(), trong đó sử dụng các chỉ số như intrinsic score,
valuation sanity, ROI norm, growth potential, runway, và regulatory risk
để xác định investment behaviour.

Các financial indicators tương tự cũng được sử dụng bởi backend APIs của
Jin. Thông qua các endpoint như /api/player_state, các metrics được tạo
ra từ phép tính của tôi được chuyển đến frontend và hiển thị cho người
chơi dưới dạng Intrinsic Score, Valuation, ROI, Runway, và các
performance indicators khác.

Phần việc của tôi cũng có liên hệ chặt chẽ với reaction card system của
Minh. Reaction cards được thiết kế để cung cấp hỗ trợ hoặc can thiệp khi
một startup gặp khó khăn tài chính. Để xác định khi nào các cards này
nên được trigger, hệ thống của Minh dựa vào các warning signals được tạo
ra bởi financial metrics engine.

Ngoài ra, tôi triển khai game-start validation logic được thực thi khi
host khởi tạo phase đầu tiên của game. Trước khi hệ thống chuyển từ
deck-selection stage sang active gameplay, quy trình validation kiểm tra
rằng số lượng người chơi yêu cầu đã tham gia phòng và tất cả
participants đã submitted decks.

Đóng góp của tôi cũng mở rộng đến giai đoạn cuối của gameplay cycle
thông qua hàm final_score(). Khi game kết thúc, hàm này tính final score
cho từng startup dựa trên fundraising performance, fundraising speed,
ROI, transparency, và scale adjustments.

Cuối cùng, các hoạt động kiểm thử của tôi đóng góp vào độ tin cậy và
tính ổn định tổng thể của sản phẩm. Sau mỗi lần tích hợp code quan
trọng, tôi thực hiện kiểm thử thủ công end-to-end đối với toàn bộ
gameplay flow, xác định lỗi và các trường hợp biên, ghi nhận vấn đề và
trao đổi báo cáo lỗi với các thành viên liên quan trong nhóm.

**6. Bài học cá nhân rút ra**

Một trong những bài học quan trọng nhất mà tôi học được từ dự án này là
việc hiểu lý thuyết tài chính và triển khai nó trong phần mềm là hai
thách thức hoàn toàn khác nhau. Mặc dù trước đó tôi đã học các khái niệm
như gross margin, burn rate, ROE, và leverage, quá trình phát triển hàm
calculate_metrics() cho thấy việc biết công thức là chưa đủ. Thách thức
thực sự nằm ở việc xử lý các trường hợp biên và đảm bảo rằng các phép
tính vẫn có ý nghĩa trong mọi tình huống.

Dự án cũng nhấn mạnh tầm quan trọng then chốt của input validation. Khi
thiết kế project submission form, tôi nhận ra rằng các đầu vào không
chính xác hoặc phi thực tế của người dùng có thể dễ dàng làm sai lệch
toàn bộ quá trình đánh giá tài chính. Trải nghiệm này củng cố quan điểm
rằng input validation không phải là mối quan tâm thứ yếu, mà là một yêu
cầu nền tảng để xây dựng các hệ thống phần mềm đáng tin cậy.

Cuối cùng, kiểm thử toàn diện đóng vai trò quan trọng trong cả quá trình
học tập của tôi và thành công chung của dự án. Thông qua quá trình này,
tôi xác định các vấn đề như division-by-zero errors, unrealistic
infinite values, và invalid score calculations. Tôi học được rằng
testing không chỉ là quá trình tìm lỗi; đó là một hoạt động thiết yếu để
đảm bảo độ tin cậy của hệ thống, duy trì chất lượng gameplay và ngăn
ngừa các lỗi nghiêm trọng.

**7. Các thách thức đã gặp và cách giải quyết**

Trong quá trình phát triển, tôi gặp một số thách thức liên quan đến
system design, financial modelling, và testing. Thách thức đầu tiên liên
quan đến việc xác định mức độ chi tiết phù hợp cho project submission
form. Ban đầu, tôi cân nhắc sử dụng một trường COGS (Cost of Goods Sold)
duy nhất để đơn giản hóa việc nhập dữ liệu. Tuy nhiên, trong quá trình
triển khai calculate_metrics(), tôi nhận ra rằng cần có các giá trị
riêng biệt cho material costs, packaging costs, labour costs, và defect
rates để tạo ra các phép tính tài chính chính xác hơn. Để giải quyết vấn
đề này, tôi thiết kế lại cấu trúc form và chia COGS thành bốn trường
riêng biệt. Tôi cũng cung cấp các tooltip giải thích để giúp người chơi
hiểu mục đích của từng đầu vào.

Thách thức thứ hai liên quan đến việc cân bằng điểm số trong hàm
calculate_metrics(). Các phiên bản đầu của financial model tạo ra
intrinsic scores quá giống nhau giữa các dự án, khiến investor bots khó
phân biệt giữa các startup mạnh và yếu. Kết quả là investment behaviour
thiếu sự khác biệt có ý nghĩa. Để cải thiện khả năng phân hóa, tôi nhiều
lần điều chỉnh score weights, tinh chỉnh normalization methods, và bổ
sung các penalty mechanisms liên quan đến security và regulatory risk.
Những điều chỉnh này tạo ra phân phối điểm cân bằng hơn và cải thiện
chất lượng ra quyết định của bot.

Thách thức thứ ba liên quan đến hiệu quả kiểm thử. Vì dự án không có môi
trường automated testing, mỗi chu kỳ kiểm thử đều yêu cầu restart
server, tạo một game room mới và nhập lại thủ công thông tin dự án. Quá
trình này ngày càng tốn thời gian khi phát triển tiến triển. Để giảm
thiểu vấn đề, tôi thiết lập một bộ default input values tiêu chuẩn có
thể tái sử dụng trong các phiên kiểm thử. Các giá trị mặc định này không
chỉ tăng tốc quá trình testing mà còn được tích hợp vào phiên bản cuối
cùng của project submission form nhằm cung cấp cho người chơi các giá
trị khởi đầu thực tế.

**8. Thông điệp dành cho sinh viên tương lai**

Nhìn lại dự án này, có một số bài học có thể giúp sinh viên tương lai
tránh các khó khăn phổ biến và cải thiện quá trình phát triển.

Một trong những khuyến nghị quan trọng nhất là thiết kế toàn bộ gameplay
flow trước khi viết bất kỳ dòng code nào. Các nhóm nên xác lập trước
cách người dùng sẽ tương tác với hệ thống, họ sẽ cung cấp thông tin gì,
game sẽ tiến triển giữa các stage như thế nào, và output nào sẽ được
hiển thị ở từng bước.

Một bài học quan trọng khác liên quan đến input validation. Mặc dù
data-entry forms có thể trông như một thành phần tương đối đơn giản,
chúng lại là nền tảng của toàn bộ hệ thống. Validation rules và
constraints nên được xác định cẩn thận ngay từ đầu thay vì được thêm vào
như một phần bổ sung sau này.

Testing cũng quan trọng không kém. Nếu có thể, các nhóm nên phát triển
các automation scripts nhỏ để tạo test rooms, submit sample projects, và
execute gameplay phases tự động. Những công cụ như vậy có thể giảm đáng
kể effort kiểm thử và giúp xác định vấn đề trước các buổi demonstration.

Cuối cùng, các nhóm nên thiết lập shared data dictionary và coding
convention trước khi bắt đầu triển khai. Variable names, data
structures, field definitions, và naming standards nên được tất cả các
thành viên thống nhất từ giai đoạn đầu. Việc duy trì tính nhất quán
trong toàn bộ codebase có thể tiết kiệm đáng kể thời gian và giảm lỗi
trong quá trình phát triển.
