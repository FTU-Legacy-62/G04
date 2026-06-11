**Thành viên:** 

Ngô Thị Diễm Phúc - MSV: 2312380804

**1\. Vai trò trong dự án**

Tôi đảm nhiệm ba trách nhiệm chính trong suốt quá trình thực hiện dự án.

Với vai trò là Backend Developer, tôi chịu trách nhiệm phát triển logic tài chính cốt lõi và logic gameplay của hệ thống, bao gồm việc triển khai các hàm calculate_metrics, final_score, và process_phase. Các thành phần này tạo thành nền tảng cho cơ chế đánh giá tài chính, cơ chế tính điểm và quy trình xử lý theo từng phase của game.

Với vai trò là Input Structure Designer, tôi thiết kế biểu mẫu nộp dự án được sử dụng trong play.html, xác định các trường thông tin đầu vào bắt buộc, kiểu dữ liệu, ràng buộc kiểm tra hợp lệ và các khoảng giá trị được chấp nhận. Tôi cũng xây dựng cấu trúc đầu vào của người chơi, trong đó quy định các thông tin tài chính và vận hành mà mỗi người chơi cần cung cấp khi tạo một dự án.

Với vai trò là Tester, tôi thực hiện kiểm thử thủ công toàn bộ game sau mỗi lần tích hợp code quan trọng. Công việc này bao gồm xác minh chức năng hệ thống, xác định lỗi và các trường hợp biên, ghi nhận vấn đề và trao đổi báo cáo lỗi với các thành viên liên quan trong nhóm để xử lý.

**2\. Dấu ấn cá nhân trong sản phẩm**

Một trong những đóng góp chính của tôi là thiết kế và triển khai hệ thống nộp dự án và đánh giá tài chính. Tôi đã thiết kế toàn bộ Project Submission Form, đây là giao diện chính để người chơi tạo và nộp các dự án startup của mình. Biểu mẫu được cấu trúc thành sáu nhóm đầu vào tài chính và vận hành, bao gồm quy mô dự án, giá bán và kênh bán hàng, cơ cấu chi phí, dự báo sản xuất, chi phí vận hành và cơ cấu vốn. Để đảm bảo cả tính dễ sử dụng và sự cân bằng của game, tôi xác định các giá trị mặc định, ràng buộc kiểm tra hợp lệ, khoảng giá trị được chấp nhận và tooltip giải thích cho từng trường. Nhờ đó, biểu mẫu cung cấp một nguồn dữ liệu dự án nhất quán và đáng tin cậy cho toàn bộ mô phỏng.

Dựa trên cấu trúc đầu vào này, tôi triển khai hàm calculate_metrics() trong app.py, đóng vai trò là công cụ đánh giá tài chính cốt lõi của game. Hàm này xử lý dữ liệu do người chơi nộp và tạo ra một tập hợp đầy đủ các chỉ số tài chính, bao gồm intrinsic score, valuation sanity, ROI norm, monthly burn, available cash, runway, funding progress, estimated valuation, raw ROI, và regulatory risk. Các chỉ số này cung cấp đánh giá định lượng về hiệu quả dự án và mức độ hấp dẫn đầu tư, tạo cơ sở cho cả quá trình ra quyết định của investor bot và hệ thống leaderboard. Do đó, project submission form và financial metrics engine cùng nhau cấu thành một phần quan trọng trong chức năng cốt lõi của game, kết nối đầu vào của người chơi với kết quả đầu tư và tiến trình gameplay tổng thể.

**3\. Các nhiệm vụ thực tế đã thực hiện**

**3.1. Thiết kế Project Input Form**

Tôi chịu trách nhiệm thiết kế project submission form được người chơi sử dụng để tạo hồ sơ startup trong game. Công việc này bao gồm xác định sáu nhóm thông tin cần thiết cho việc đánh giá tài chính, cụ thể là project scale, pricing and sales channels, cost of goods sold (COGS), production forecasts, fixed operating costs, và capital structure. Với mỗi nhóm, tôi xác định các trường đầu vào cụ thể mà người chơi bắt buộc phải hoàn thành.

Thay vì sử dụng các đầu vào được tổng hợp ở mức quá cao, tôi thiết kế một số trường với mức độ chi tiết lớn hơn nhằm cải thiện độ chính xác của các phép tính tài chính. Ví dụ, COGS được tách thành material cost, packaging cost, labour cost, và defect rate, cho phép hệ thống backend tính gross margin một cách thực tế hơn. Ngoài ra, tôi thiết lập các ràng buộc kiểm tra hợp lệ, khoảng giá trị được chấp nhận và đơn vị đo lường cho tất cả các trường nhằm ngăn các đầu vào phi thực tế hoặc không hợp lệ ảnh hưởng đến mô phỏng. Tôi cũng chuẩn bị nội dung giải thích được hiển thị trong các information modal liên kết với từng phần của biểu mẫu, giúp người chơi hiểu mục đích, đơn vị và khoảng giá trị được chấp nhận của từng đầu vào mà không cần tham khảo tài liệu bên ngoài.

|     |     |     |     |     |
| --- | --- | --- | --- | --- |
| **Group** | **Input Name** | **Short Description** | **Unit** | **Constraints** |
| Scale | Project size | Chọn quy mô dự án: Small (5 phases), Medium (7 phases), Large (9 phases). |     | Small / Medium / Large |
| Price & Channels | Retail price | Giá niêm yết của một sản phẩm trước khi trừ bất kỳ khoản phí kênh nào. | USD | 10–1000 |
| Price & Channels | E-commerce fee | Phí nền tảng cho các marketplace trực tuyến, ví dụ Shopee, Amazon. | %   | 0–100 |
| Price & Channels | Retail fee | Chiết khấu thương mại/biên lợi nhuận dành cho các đối tác bán lẻ vật lý, ví dụ siêu thị, cửa hàng tiện lợi. | %   | 0–100 |
| Price & Channels | Direct channel fee | Chi phí bán hàng thông qua website hoặc fanpage riêng, ví dụ payment gateway. | %   | 0–100 |
| COGS | Direct materials | Nguyên vật liệu, linh kiện hoặc bộ phận được sử dụng để sản xuất một sản phẩm. | USD | 0.1–100 |
| COGS | Direct packaging | Chi phí hộp, túi, nhãn hoặc hướng dẫn sử dụng cho một sản phẩm. | USD | 0.1–100 |
| COGS | Direct labor | Tiền lương của công nhân nhà máy lắp ráp hoặc xử lý sản phẩm, được tính biến đổi theo từng đơn vị. | USD | 0.1–100 |
| COGS | Defect allowance (%) | Tỷ lệ phần trăm sản phẩm bị mất do hư hỏng, làm lại hoặc vấn đề chất lượng. | %   | 0–10 |
| Production Forecast | Month 1 units | Số lượng sản phẩm dự kiến bán ra trong tháng đầu tiên sau khi ra mắt. | units | 0–100,000 |
| Production Forecast | Month 3 units | Doanh số dự kiến trong tháng thứ 3 sau khi ra mắt. | units | 0–100,000 |
| Production Forecast | Month 6 units | Doanh số hàng tháng dự kiến sau 6 tháng kể từ khi ra mắt. | units | 0–100,000 |
| Monthly Operating Costs | Fixed operating cost | Chi phí hàng tháng KHÔNG thay đổi theo sản lượng: tiền thuê văn phòng, lương quản lý, tiện ích, v.v. | USD/month | 1,000–100,000 |
| Monthly Operating Costs | Marketing cost | Ngân sách hàng tháng cho quảng cáo, khuyến mãi, influencer campaigns. | USD/month | 0–100,000 |
| Capital Structure | Owner equity | Tiền mặt do founders/co-founders đầu tư. | USD | 0–300,000 |
| Capital Structure | Bank loan | Khoản vay từ ngân hàng hoặc quỹ nợ. | USD | 0–300,000 |
| Capital Structure | Loan interest rate | Lãi suất hằng năm của khoản vay. | %/year | 5–100 |
| Capital Structure | Equity offered (%) | Tỷ lệ phần trăm công ty được bán cho nhà đầu tư trong vòng gọi vốn này. | %   | 0.1–99.9 |
|     | Target funding | Số tiền mà người chơi đặt mục tiêu huy động từ nhà đầu tư. | USD | Small: 30,000–99,999 Medium: 100,000–251,999 Large: 252,000–500,000 |

Table 1. Input table

**3.2. Phát triển Backend Financial Engine**

Tôi phát triển công cụ đánh giá tài chính cốt lõi của game, chủ yếu thông qua việc triển khai hàm calculate_metrics(proj). Hàm này xử lý dữ liệu dự án thô do người chơi nộp và tạo ra các chỉ số tài chính được sử dụng xuyên suốt mô phỏng. Các chỉ số này bao gồm sáu thành phần của intrinsic score — gross margin, burn rate, growth potential, revenue scale, capital efficiency, và leverage — cũng như valuation sanity, ROI norm, estimated valuation, runway, và regulatory risk.

Trong các lần phát triển sau đó, tôi tinh chỉnh mô hình đánh giá bằng cách đưa security và regulatory risk penalties vào quá trình tính intrinsic score. Các khoản penalty này làm giảm mức độ hấp dẫn của dự án khi các chỉ số liên quan đến compliance hoặc security thấp hơn ngưỡng được chấp nhận, qua đó khuyến khích chiến lược người chơi cân bằng và thực tế hơn.

Tôi cũng triển khai hàm final_score(proj, phases_used, metrics), có chức năng xác định thứ hạng cuối cùng của người chơi khi game kết thúc. Mô hình tính điểm kết hợp bốn khía cạnh — fundraising performance, fundraising speed, return on investment, và transparency — đồng thời áp dụng các hệ số điều chỉnh bổ sung và funding bonuses để phản ánh project size và fundraising outcomes.

|     |     |     |     |
| --- | --- | --- | --- |
| **Indicator / Component** | **Formula in Code** | **Why This Metric** | **Why Needed in Game** |
| Step 0 -Pre-processing (shared by all indicators below) | Step 0 -Pre-processing (shared by all indicators below) | Step 0 -Pre-processing (shared by all indicators below) | Step 0 -Pre-processing (shared by all indicators below) |
| price_real | total_fees = fee_ecom + fee_retail + fee_direct price_real = price × (1 − total_fees/100) | Doanh thu ròng thực tế trên mỗi đơn vị sau khi trả commission cho các kênh. Người chơi nhập một mức giá duy nhất, nhưng doanh thu thực tế phải trừ phí kênh. | Nếu không có bước này, gross margin sẽ bị tính sai — một dự án có thể trông có vẻ có lợi nhuận nhưng thực tế lại mất tiền cho các kênh. Bot sẽ bị dẫn dắt sai và đầu tư vào các dự án yếu. |
| cogs_unit | cogs_unit = (material + packaging + labor) × (1 + defect_rate/100) | Chi phí sản xuất thực tế trên mỗi đơn vị, bao gồm tỷ lệ hao hụt. defect_rate 5% có nghĩa là cần sản xuất 105 đơn vị để bán được 100 đơn vị. | Việc tách COGS thành 4 trường theo thiết kế form phản ánh cơ cấu chi phí thực. Các dự án cần nhiều lao động bị penalty mạnh hơn khi defect_rate cao. |
| monthly_burn | monthly_burn = fixed_cost + marketing_cost + loan × interest_rate/100/12 | Tổng dòng tiền bắt buộc phải chi hằng tháng, không phụ thuộc vào sản lượng bán hàng. Bao gồm fixed costs, marketing, và lãi vay hằng tháng. | Đây là chỉ số sinh tồn quan trọng: một startup hết tiền trước khi huy động đủ vốn sẽ phá sản. Chỉ số này được sử dụng để tính burn_score, runway, và kiểm tra bankruptcy trong process_phase. |
| Group A -Intrinsic Score (max 100 points, 6 components) | Group A -Intrinsic Score (max 100 points, 6 components) | Group A -Intrinsic Score (max 100 points, 6 components) | Group A -Intrinsic Score (max 100 points, 6 components) |
| gm_score (0–30 pts) | gm = (price_real − cogs_unit) / price_real if gm > 0.2: score = 20 + 10×(1−e^{−5×(gm−0.2)/0.6}) else: score = max(0, 20×(gm/0.2)) | Gross margin đo lường lợi nhuận gộp trên mỗi đơn vị doanh thu. Đây là thành phần có trọng số cao nhất (30 pts) vì là chỉ số nền tảng nhất — một dự án có margin âm không thể tồn tại dài hạn. Hàm mũ phía trên 0.2 thưởng cho các dự án có margin cao nhưng với hiệu ứng lợi ích biên giảm dần. | Bot sử dụng intrinsic score làm cơ sở cho quyết định đầu tư. gm_score có trọng số cao nhất vì trong các startup thực tế, gross margin là chỉ số đầu tiên mà nhà đầu tư xem xét — nó cho thấy còn lại bao nhiêu để trang trải fixed costs và tạo lợi nhuận. |
| burn_score (0–20 pts) | burn_rate = monthly_burn / target_funding if burn_rate < 0.3: score = 15 + 5×(1−e^{−4×(0.3−r)/0.25}) else: score = max(0, 15×(1−(r−0.3)/0.7)) | Burn rate = tỷ lệ giữa chi phí hằng tháng và tổng target funding. Chỉ số này đo tốc độ startup đốt tiền. Ngưỡng 0.3 có nghĩa là khi chi tiêu hằng tháng vượt 30% target funding thì bắt đầu bị penalty. | Một dự án có burn rate cao sẽ hết tiền trước khi hoàn tất vòng gọi vốn. Bot cần nhận diện điều này — nếu không, bot sẽ đầu tư vào các startup sắp phá sản. burn_score tự nhiên định hướng bot tránh xa các dự án “high burn, low runway”. |
| growth_score (0–20 pts) | growth = (units_m6 / units_m1) − 1 if growth > 0: score = 10 + 10×(1−e^{−3×g/0.5}) else: score = max(0, 10×(1+g/0.5)) | Tỷ lệ tăng trưởng sản lượng từ tháng 1 đến tháng 6, đo lường động lực phát triển của dự án. Hàm mũ thưởng cho tăng trưởng nhanh với lợi ích biên giảm dần — ngăn người chơi khai thác hệ thống bằng cách nhập units_m6 quá cao. | Game mô phỏng nhiều phase. Một dự án có tăng trưởng sản lượng mạnh sẽ tự nhiên thu hút bot qua nhiều vòng — điều này thực tế vì nhà đầu tư không chỉ xem trạng thái hiện tại mà còn xem quỹ đạo phát triển. |
| revenue_score (0–10 pts) | avg_units = (units_m1 + units_m6) / 2 revenue_year = avg_units × 12 × price_real score = min(10, log10(revenue_year/100000)/2 × 10) | Doanh thu hằng năm dự kiến, được scale theo log. Thang log có nghĩa là một dự án $1B không được điểm cao gấp 10 lần một dự án $100M — phản ánh cách nhà đầu tư thực sự đánh giá quy mô tuyệt đối. | revenue_year cũng được sử dụng để tính estimated_valuation thông qua P/S ratio. Các dự án có doanh thu cao hơn nhận valuation cao hơn — nhưng không tuyến tính. Trọng số 10 pts, thấp hơn GM và burn, vì quy mô quan trọng nhưng kém quan trọng hơn efficiency. |
| efficiency_score (0–10 pts) | annual_profit = (price_real−cogs_unit) × units_m6×12 − burn×12 roe = annual_profit / total_capital score = min(10, roe×10) | ROE (Return on Equity) đo lợi nhuận tạo ra trên mỗi đơn vị vốn. Không giống gm_score chỉ đo tỷ lệ, chỉ số này đo lợi nhuận tuyệt đối sau fixed costs — một dự án có margin cao nhưng fixed costs quá lớn sẽ bị penalty tại đây. | Một startup sử dụng vốn hiệu quả tạo ra nhiều lợi nhuận hơn đối thủ với cùng một lượng vốn. Bot cần phân biệt giữa “profitable” và “efficient” — hai khái niệm này không giống nhau. |
| leverage_score (0–10 pts) | debt_ratio = loan / owner_equity if ratio < 0.5: score = 5 + ratio×10 elif ratio ≤ 1.5: score = 10−(ratio−0.5)×5 else: score = max(0, 5−(ratio−1.5)×3) | Đánh giá cấu trúc debt-to-equity. Hàm hình thang: tỷ lệ thấp (0–0.5) nhận điểm trung bình vì quá thận trọng; tỷ lệ vừa phải (0.5–1.5) nhận điểm cao nhất vì leverage tốt; tỷ lệ cao (>1.5) bị penalty vì rủi ro mất khả năng thanh toán. | Phản ánh nguyên lý tài chính: một mức nợ nhất định là tốt do tạo leverage, nhưng quá nhiều nợ là nguy hiểm. Một dự án tài trợ hoàn toàn bằng equity sẽ bỏ lỡ lợi ích leverage; các dự án over-leveraged sẽ thấy monthly_burn tăng do lãi vay và đối mặt với nguy cơ bankruptcy cao hơn. |
| security_penalty & reg_risk_penalty | sec_pen = max(0, (50−security)/5) reg_pen = reg_risk / 10 intrinsic = max(0, intrinsic−sec_pen−reg_pen) | Trừ điểm intrinsic đối với các dự án bỏ qua security và regulatory compliance. Mỗi 5 điểm security dưới 50 bị trừ 1 pt; mỗi 10% reg_risk bị trừ 1 pt. Áp dụng sau khi cả 6 components đã được tính. | Được bổ sung sau khi kiểm thử cho thấy bot không thể phân biệt các dự án thiếu cẩn trọng về compliance. Các penalty này buộc người chơi phải cân nhắc security và licensing — không chỉ tối ưu tài chính. |
| Group B -Valuation & ROI | Group B -Valuation & ROI | Group B -Valuation & ROI | Group B -Valuation & ROI |
| estimated_valuation | ps_ratio = 3.0 (baseline) if hype>70: ps_ratio += 2 elif hype&lt;30: ps_ratio −= 1 if growth&gt;0.5: ps_ratio += 1.5 ps_ratio = clamp(ps_ratio, 1.5, 15) valuation = revenue_year × ps_ratio | Sử dụng P/S ratio (Price-to-Sales) — phương pháp định giá phổ biến cho các startup chưa có lợi nhuận. Mức baseline là 3×, được điều chỉnh theo hype (market sentiment) và growth. clamp(1.5, 15) ngăn valuation phi lý. | Valuation là kết quả quan trọng mà người chơi nhìn thấy trên dashboard. Hype ảnh hưởng đến P/S vì trong thực tế, các startup “hot” luôn được định giá cao hơn fundamentals — điều này phản ánh chính xác thị trường VC. |
| roi_norm | raw_roi = max(0, (valuation−total_invested)/total_invested×100) roi_norm = min(100, 20×log10(raw_roi+1)) | ROI được chuẩn hóa về \[0, 100\] bằng hàm log để tránh outlier. Một dự án ROI 10% và 1000% không nên khác nhau 100 lần về điểm — thang log làm mượt khoảng cách này. | final_score sử dụng roi_norm để tính roi_score. Bot cũng sử dụng nó gián tiếp thông qua attractiveness(). Các dự án có ROI tốt giữ được khoản đầu tư của bot qua nhiều phase. |
| valuation_sanity | mult = valuation / revenue_year if mult < 1: score = 30−(1−mult)/1×30 elif mult ≤ 3: score = 80+(mult−1)/2×20 elif mult ≤ 5: score = 80−(mult−3)/2×40 else: score = max(0, 40−(mult−5)/2×40) | Kiểm tra valuation có “healthy” hay không — P/S 1–3× được xem là hợp lý và nhận điểm cao nhất; P/S &lt;1, tức undervalued, hoặc &gt;5, tức overvalued, bị penalty. Hàm hình thang phản ánh vùng valuation tối ưu. | Ngăn người chơi thao túng revenue_year để làm tăng valuation một cách giả tạo. Bot nhận diện các dự án overvalued và đầu tư ít hơn — tương tự cách các VC thực tế từ chối các thương vụ có mức giá chào quá cao. |
| reg_risk | base = 20 if has_license else 80 if legal_cost ≥ 5% target_funding: base += 20 reg_risk = clamp(base−transparency/10, 0, 100) | Regulatory risk tổng hợp từ: có license (−60 risk), đầu tư vào legal costs (−20 risk), transparency cao làm giảm thêm rủi ro. Đây là chỉ số ngược — càng cao càng xấu. | Được sử dụng trong reg_risk_penalty, tức trừ intrinsic, và trong attractiveness() của bot. Các dự án có reg_risk cao bị bot tránh né — phản ánh rằng regulatory risk là lý do phổ biến nhất khiến startup thất bại tại Việt Nam. |
| runway | avail = available_cash (or equity + loan) runway = floor(avail / monthly_burn) = 999 if monthly_burn = 0 | Số tháng một startup có thể tồn tại với lượng tiền mặt hiện tại. Đây là chỉ số đơn giản nhưng quan trọng nhất: nếu runway < remaining phases, dự án gần như chắc chắn phá sản trước khi huy động đủ vốn. | process_phase sử dụng runway, gián tiếp thông qua available_cash, để kiểm tra bankruptcy sau mỗi phase. Người chơi nhìn thấy runway trên dashboard — đây là chỉ số trực quan nhất về thời gian còn lại. |

Table 2. Calculate_metrics(proj): All Financial Indicators

|     |     |     |     |
| --- | --- | --- | --- |
| **Component** | **Formula in Code** | **Weight & Rationale** | **Why Needed in Game** |
| funding_score (max 40 pts) | funding_score = funding_progress × 40 | Trọng số 40% — cao nhất. Lý do: mục tiêu cốt lõi của game là fundraising thành công. Một dự án huy động được 100% target nhận 40 pts; 50% nhận 20 pts. Trọng số cao nhất đảm bảo điều kiện chiến thắng chính được phản ánh mạnh nhất trong điểm số. | Nếu funding_score chỉ chiếm 20–25%, người chơi có thể thắng mà không huy động đủ funding, làm mất logic cốt lõi của game. 40% đảm bảo mục tiêu chính không thể bị bỏ qua. |
| speed_score (max 20 pts) | if complete_phase is not None: speed = 20×(1−(complete_phase−1)/(max_phase−1)) else: speed = 0 | Trọng số 20%. Công thức tuyến tính: hoàn thành ở phase 1 nhận 20 pts, hoàn thành ở phase cuối nhận 0 pts. Trọng số bằng với roi_score và trans_score: speed là lợi thế cạnh tranh, không phải yêu cầu bắt buộc — quan trọng nhưng không quan trọng hơn ROI. | Tạo cạnh tranh khi nhiều người chơi đều huy động đủ funding. Nếu không có speed_score, game sẽ trở nên phẳng khi mọi người đều hoàn thành. Đồng thời phản ánh thực tế: gọi vốn nhanh giúp tiết kiệm burn và tận dụng tốt hơn market timing. |
| roi_score (max 20 pts) | roi_score = min(20, (roi_norm/100) × 20) | Trọng số 20%. roi_norm đã được chuẩn hóa về \[0, 100\] trong calculate_metrics, nên ánh xạ trực tiếp sang \[0, 20\]. Bằng với speed_score: ROI tốt thể hiện thiết kế dự án chất lượng cao nhưng không phải yếu tố quyết định — đây là yếu tố phân định khi cần so sánh. | Thưởng cho người chơi thiết kế các dự án có ROI thực sự cao, không chỉ những dự án huy động đủ funding. Ngăn chiến lược “spam many small investments” — bot chỉ đầu tư mạnh vào các dự án có ROI cao. |
| trans_score (max 20 pts) | trans_score = max(0, min(20, (transparency/100) × 20)) | Trọng số 20%. Transparency là chỉ số người chơi xây dựng thông qua cards và actions (0–100). Ánh xạ tuyến tính sang \[0, 20\]. Bằng với trọng số ROI vì transparency là điều kiện tiên quyết mà nhà đầu tư yêu cầu — nếu không có nó, ngay cả các dự án ROI cao cũng bị bot tránh. | Buộc người chơi đầu tư vào transparency, không chỉ tối ưu tài chính. Phản ánh thực tế: các startup thiếu transparency, như không có audit hoặc reporting, sẽ bị nhà đầu tư từ chối ngay cả khi số liệu có vẻ tốt. |
| scale_factor | scale_map = {S:0.8, M:0.9, L:1.0} final = raw × scale_factor × bonus | Hệ số điều chỉnh dựa trên project scale được chọn khi bắt đầu game. Scale S khó gọi vốn hơn nên nhận 0.8, tức điểm tối đa thấp hơn; Scale L nhận 1.0. Đây không phải penalty — chỉ là cơ chế cân bằng game cho các lựa chọn scale khác nhau. | Nếu không có scale_factor, người chơi sẽ luôn chọn Scale L để có điểm cao hơn. Hệ số này tạo trade-off: Scale S huy động ít tiền hơn và có thể hoàn thành sớm, tức speed_score cao, nhưng tổng điểm bị nhân với 0.8. |
| funding_bonus | funding_bonus = (1 + funding_progress)/2 final = raw × scale_factor × funding_bonus | Hệ số nhân bonus ở cuối game, dao động từ 0.5–1.0 dựa trên funding_progress. Dự án huy động 100%: bonus = 1.0. Huy động 0%: bonus = 0.5, tức một nửa điểm. Mục đích là khuếch đại khoảng cách giữa dự án thành công và thất bại. | Nếu không có funding_bonus, một dự án huy động 60% và một dự án huy động 100% vẫn có thể đạt điểm tương tự nếu ROI/speed tốt. Bonus này đảm bảo funding_progress có tác động phi tuyến — huy động càng nhiều, điểm tăng càng nhanh. |

Table 3. Final_score(proj, phases_used, metrics): End-Game Score

**3.3. Testing and Quality Assurance**

Ngoài trách nhiệm phát triển, tôi thực hiện kiểm thử rộng rãi trong suốt vòng đời dự án.

|     |     |     |     |
| --- | --- | --- | --- |
| **No.** | **Test Scenario** | **Expected Result** | **Actual Result** |
| 1   | Tạo phòng 2-player, nộp project + deck, host chạy phase → game bắt đầu ở phase 1 | Mỗi player có 5 cards, một random event xuất hiện ở mỗi phase | Pass |
| 2   | Một player chưa submitted deck, host chạy phase → error 'Players X have not submitted deck' | Thông báo lỗi rõ ràng | Pass |
| 3   | Player plays a card (play_card) → energy giảm, card biến mất khỏi hand, effects được áp dụng sau khi run phase | Energy giảm, card biến mất, hype/transparency stats thay đổi | Pass |
| 4   | Player uses Mulligan → energy giảm, new hand (5 random cards). Using Mulligan twice in one phase → error. Insufficient energy for Mulligan → error | Hành vi đúng với các thông báo lỗi rõ ràng | Pass |
| 5   | available_cash của một project giảm xuống 0 → bị đánh dấu bankrupt, không tham gia các phase tiếp theo | Log 'BANKRUPT', project bị loại khỏi active play | Pass |
| 6   | Reaction card với điều kiện runway <= 2 → nút 'Activate' xuất hiện, sau khi sử dụng thì runway bonus được áp dụng | Trigger đúng, effect được áp dụng | Pass |
| 7   | Host clicks 'End Game' → leaderboard hiển thị temporary scores dựa trên phases completed | Scores xuất hiện | Pass |
| 8   | Host clicks 'Reset Game' → toàn bộ dữ liệu được reset về trạng thái ban đầu, players có thể re-submit projects | Reset đúng | Pass |
| 9   | Restart Flask server → rooms in progress vẫn tồn tại, players có thể reconnect | SQLite persistent storage | Pass |
| 10  | 4 players, mỗi player có scale khác nhau (S, M, L) → max phases khác nhau tương ứng (5, 7, 9) | Mỗi player kết thúc ở một phase khác nhau | Pass |
| 11  | Projects đã kết thúc hoặc bankrupt — player tiếp tục nhấn action buttons | Notification displayed | Pass |
| 12  | Selecting more cards than allowed | Notification displayed | Pass |
| 13  | Không phải tất cả players đã readied up khi host runs game do bankruptcy, eliminated players, hoặc phase limits | Host notification. Game continues normally | Pass |

Table 4. Test list

**4\. Proof of contribution**

GitHub Commits: https://github.com/khanhhabao7/nhap-fintech/commits?author=ngongodiemphuc-svg

**5\. Cách đóng góp của tôi kết nối với sản phẩm cuối cùng**

Đóng góp của tôi được tích hợp xuyên suốt toàn bộ gameplay pipeline, từ thời điểm người chơi nộp một startup project cho đến bảng xếp hạng cuối cùng được hiển thị khi game kết thúc. Trên thực tế, hệ thống vận hành theo một luồng liên tục gồm Form Input → Backend Financial Engine → Investor Bots → User Interface → Reaction Cards, và tôi đã đóng góp vào một số giai đoạn quan trọng của quy trình này.

Project submission form trong play.html đóng vai trò là điểm đầu vào cho toàn bộ dữ liệu do người chơi tạo ra. Tôi thiết kế cấu trúc form, xác định mười một trường đầu vào bắt buộc, thiết lập validation rules, và lựa chọn các giá trị mặc định cũng như khoảng giá trị phù hợp. Mục tiêu là cho phép người chơi nhập thông tin kinh doanh một cách trực quan, chẳng hạn selling price, production costs, và projected sales volume, đồng thời đảm bảo backend luôn nhận được dữ liệu đầy đủ và hợp lệ.

Hàm calculate_metrics() đóng vai trò là công cụ đánh giá tài chính trung tâm của game và là điểm kết nối quan trọng nhất giữa phần việc của tôi với đóng góp của các thành viên khác trong nhóm. Hệ thống investor bot của Khanh phụ thuộc vào đầu ra của calculate_metrics() thông qua hàm attractiveness(), trong đó sử dụng các chỉ số như intrinsic score, valuation sanity, ROI norm, growth potential, runway, và regulatory risk để xác định investment behaviour.

Các financial indicators tương tự cũng được sử dụng bởi backend APIs của Jin. Thông qua các endpoint như /api/player_state, các metrics được tạo ra từ phép tính của tôi được chuyển đến frontend và hiển thị cho người chơi dưới dạng Intrinsic Score, Valuation, ROI, Runway, và các performance indicators khác.

Phần việc của tôi cũng có liên hệ chặt chẽ với reaction card system của Minh. Reaction cards được thiết kế để cung cấp hỗ trợ hoặc can thiệp khi một startup gặp khó khăn tài chính. Để xác định khi nào các cards này nên được trigger, hệ thống của Minh dựa vào các warning signals được tạo ra bởi financial metrics engine.

Ngoài ra, tôi triển khai game-start validation logic được thực thi khi host khởi tạo phase đầu tiên của game. Trước khi hệ thống chuyển từ deck-selection stage sang active gameplay, quy trình validation kiểm tra rằng số lượng người chơi yêu cầu đã tham gia phòng và tất cả participants đã submitted decks.

Đóng góp của tôi cũng mở rộng đến giai đoạn cuối của gameplay cycle thông qua hàm final_score(). Khi game kết thúc, hàm này tính final score cho từng startup dựa trên fundraising performance, fundraising speed, ROI, transparency, và scale adjustments.

Cuối cùng, các hoạt động kiểm thử của tôi đóng góp vào độ tin cậy và tính ổn định tổng thể của sản phẩm. Sau mỗi lần tích hợp code quan trọng, tôi thực hiện kiểm thử thủ công end-to-end đối với toàn bộ gameplay flow, xác định lỗi và các trường hợp biên, ghi nhận vấn đề và trao đổi báo cáo lỗi với các thành viên liên quan trong nhóm.

**6\. Bài học cá nhân rút ra**

Một trong những bài học quan trọng nhất mà tôi học được từ dự án này là việc hiểu lý thuyết tài chính và triển khai nó trong phần mềm là hai thách thức hoàn toàn khác nhau. Mặc dù trước đó tôi đã học các khái niệm như gross margin, burn rate, ROE, và leverage, quá trình phát triển hàm calculate_metrics() cho thấy việc biết công thức là chưa đủ. Thách thức thực sự nằm ở việc xử lý các trường hợp biên và đảm bảo rằng các phép tính vẫn có ý nghĩa trong mọi tình huống.

Dự án cũng nhấn mạnh tầm quan trọng then chốt của input validation. Khi thiết kế project submission form, tôi nhận ra rằng các đầu vào không chính xác hoặc phi thực tế của người dùng có thể dễ dàng làm sai lệch toàn bộ quá trình đánh giá tài chính. Trải nghiệm này củng cố quan điểm rằng input validation không phải là mối quan tâm thứ yếu, mà là một yêu cầu nền tảng để xây dựng các hệ thống phần mềm đáng tin cậy.

Cuối cùng, kiểm thử toàn diện đóng vai trò quan trọng trong cả quá trình học tập của tôi và thành công chung của dự án. Thông qua quá trình này, tôi xác định các vấn đề như division-by-zero errors, unrealistic infinite values, và invalid score calculations. Tôi học được rằng testing không chỉ là quá trình tìm lỗi; đó là một hoạt động thiết yếu để đảm bảo độ tin cậy của hệ thống, duy trì chất lượng gameplay và ngăn ngừa các lỗi nghiêm trọng.

**7\. Các thách thức đã gặp và cách giải quyết**

Trong quá trình phát triển, tôi gặp một số thách thức liên quan đến system design, financial modelling, và testing. Thách thức đầu tiên liên quan đến việc xác định mức độ chi tiết phù hợp cho project submission form. Ban đầu, tôi cân nhắc sử dụng một trường COGS (Cost of Goods Sold) duy nhất để đơn giản hóa việc nhập dữ liệu. Tuy nhiên, trong quá trình triển khai calculate_metrics(), tôi nhận ra rằng cần có các giá trị riêng biệt cho material costs, packaging costs, labour costs, và defect rates để tạo ra các phép tính tài chính chính xác hơn. Để giải quyết vấn đề này, tôi thiết kế lại cấu trúc form và chia COGS thành bốn trường riêng biệt. Tôi cũng cung cấp các tooltip giải thích để giúp người chơi hiểu mục đích của từng đầu vào.

Thách thức thứ hai liên quan đến việc cân bằng điểm số trong hàm calculate_metrics(). Các phiên bản đầu của financial model tạo ra intrinsic scores quá giống nhau giữa các dự án, khiến investor bots khó phân biệt giữa các startup mạnh và yếu. Kết quả là investment behaviour thiếu sự khác biệt có ý nghĩa. Để cải thiện khả năng phân hóa, tôi nhiều lần điều chỉnh score weights, tinh chỉnh normalization methods, và bổ sung các penalty mechanisms liên quan đến security và regulatory risk. Những điều chỉnh này tạo ra phân phối điểm cân bằng hơn và cải thiện chất lượng ra quyết định của bot.

Thách thức thứ ba liên quan đến hiệu quả kiểm thử. Vì dự án không có môi trường automated testing, mỗi chu kỳ kiểm thử đều yêu cầu restart server, tạo một game room mới và nhập lại thủ công thông tin dự án. Quá trình này ngày càng tốn thời gian khi phát triển tiến triển. Để giảm thiểu vấn đề, tôi thiết lập một bộ default input values tiêu chuẩn có thể tái sử dụng trong các phiên kiểm thử. Các giá trị mặc định này không chỉ tăng tốc quá trình testing mà còn được tích hợp vào phiên bản cuối cùng của project submission form nhằm cung cấp cho người chơi các giá trị khởi đầu thực tế.

**8\. Thông điệp dành cho sinh viên tương lai**

Nhìn lại dự án này, có một số bài học có thể giúp sinh viên tương lai tránh các khó khăn phổ biến và cải thiện quá trình phát triển.

Một trong những khuyến nghị quan trọng nhất là thiết kế toàn bộ gameplay flow trước khi viết bất kỳ dòng code nào. Các nhóm nên xác lập trước cách người dùng sẽ tương tác với hệ thống, họ sẽ cung cấp thông tin gì, game sẽ tiến triển giữa các stage như thế nào, và output nào sẽ được hiển thị ở từng bước.

Một bài học quan trọng khác liên quan đến input validation. Mặc dù data-entry forms có thể trông như một thành phần tương đối đơn giản, chúng lại là nền tảng của toàn bộ hệ thống. Validation rules và constraints nên được xác định cẩn thận ngay từ đầu thay vì được thêm vào như một phần bổ sung sau này.

Testing cũng quan trọng không kém. Nếu có thể, các nhóm nên phát triển các automation scripts nhỏ để tạo test rooms, submit sample projects, và execute gameplay phases tự động. Những công cụ như vậy có thể giảm đáng kể effort kiểm thử và giúp xác định vấn đề trước các buổi demonstration.

Cuối cùng, các nhóm nên thiết lập shared data dictionary và coding convention trước khi bắt đầu triển khai. Variable names, data structures, field definitions, và naming standards nên được tất cả các thành viên thống nhất từ giai đoạn đầu. Việc duy trì tính nhất quán trong toàn bộ codebase có thể tiết kiệm đáng kể thời gian và giảm lỗi trong quá trình phát triển.
