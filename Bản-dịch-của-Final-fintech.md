**BÁO CÁO CHI TIẾT DỰ ÁN: FUN(D RASING- MÔ PHỎNG QUÁ TRÌNH GỌI VỐN CHO STARTUP**

**MỤC LỤC**

[1\. Thông tin chung 1](#_Toc232092481)

[2\. Vấn đề mà nhóm muốn giải quyết 3](#_Toc232092482)

[3\. Target Users 3](#_Toc232092483)

[4.Chức năng hiện tại của sản phẩm 3](#_Toc232092484)

[5\. Dữ liệu đầu vào 4](#_Toc232092485)

[6\. Logic và Quy tắc xử lý 6](#_Toc232092486)

[7\. Luồng người dùng 19](#_Toc232092487)

[8\. Dữ liệu đầu ra 20](#_Toc232092488)

[9\. Các lựa chọn thiết kế chính 21](#_Toc232092489)

[10\. Những điều nhóm đã làm tốt 21](#_Toc232092490)

[11\. Những hạn chế hiện tại 22](#_Toc232092491)

[12\. Những điều nhóm đã học được 22](#_Toc232092492)

[13\. Gợi ý cho sinh viên tương lai 23](#_Toc232092493)

# 1\. Thông tin chung

Dự án **FUN(D) RAISING** không chỉ là một trò chơi mô phỏng; mà là một công cụ giáo dục (EdTech) phức tạp được thiết kế để giải quyết các thách thức thực tiễn trong tài chính doanh nghiệp và tâm lý học hành vi. Bạn sẽ vào vai người sáng lập dự án, quản lý các chỉ số như tiến độ gây quỹ và tính minh bạch, đồng thời thuyết phục các nhà đầu tư đạt được mục tiêu qua từng giai đoạn. Trò chơi phù hợp cho sinh viên kinh tế, những người đam mê khởi nghiệp, hoặc bất cứ ai muốn học hỏi trong khi chơi và học hỏi về gọi vốn cộng đồng. Sản phẩm này giúp chuyển đổi các công thức khô khan thành phản xạ ra quyết định thực tiễn.

**Thông tin dự án:**

|     |     |
| --- | --- |
| Criteria | Chi tiết |
| **Tên sản phẩm** | FUN(D) RAISING |
| **Slogan** | "When you have fund you have fun" |
| **Mã nhóm** | G04 |
| **Kho lưu trữ** | [Link GitHub G04](https://github.com/FTU-Legacy-62/G04) |
| **Link demo** | Thông tin này sẽ được cập nhật sau khi bài tập cuối cùng được nộp. |
| **Lớp học** | NHA408E(2526-2)GD2.01 |
| **Instructor** | Assoc. Prof. Dr. Phan Tran Trung Dung |

**Danh sách thành viên nhóm:**

1.  **Vu Bach Duong** - 2312380808
2.  **Kim Hye Jin** - 2312380803
3.  **Ha Bao Khanh** - 2314380702
4.  **Nguyen Ngoc Minh** - 2313380019
5.  **Ngo Thi Diem Phuc** - 2312380804

**_Tổng thể_**_:_Trong giáo dục tài chính hiện đại, rủi ro lớn nhất là khoảng cách giữa lý thuyết và thực tiễn. FUN(D) RAISING đóng vai trò như một "buffer zone" chiến thuật, nơi các sai sót trong cơ cấu vốn hoặc quản lý lòng tin có thể được xác định và khắc phục mà không gây nguy hại đến sự tồn tại thực sự của doanh nghiệp.

# 2\. Vấn đề mà nhóm muốn giải quyết

Tình hình hiện tại cho thấy sự bất đối xứng thông tin nghiêm trọng giữa các nhà sáng lập và nhà đầu tư. Sinh viên và các công ty khởi nghiệp giai đoạn đầu thường nắm vững các công thức định giá nhưng lại thiếu "bản năng sinh tồn" để hiểu cách các chỉ số tài chính tương tác với tâm lý thị trường.

- **Phân tích thách thức:**Việc kết nối các chỉ số hoạt động (Lợi nhuận gộp, Tỷ lệ chi tiêu, Thời gian hoạt động còn lại) với các biến số tâm lý (Nỗi sợ bỏ lỡ cơ hội, sự tự tin, khả năng chấp nhận rủi ro) thường đòi hỏi một cái giá rất cao bằng tiền mặt hoặc nhiều năm kinh nghiệm quý báu.
- **Các bên bị ảnh hưởng:** Sinh viên ngành tài chính cần được rèn luyện trong môi trường áp lực cao, và các nhà sáng lập giai đoạn đầu thường bước vào vòng gọi vốn đầu tiên với sự thiếu kinh nghiệm về chiến thuật.

Vì vậy, việc thiếu kinh nghiệm thực tiễn nguy hiểm hơn là thiếu công thức lý thuyết. Định giá không thực tế hoặc thiếu minh bạch về cấu trúc vốn là nguyên nhân hàng đầu dẫn đến thất bại của các công ty khởi nghiệp trong vòng gọi vốn đầu tiên. Dự án này giải quyết khoảng trống đó bằng cách chuyển đổi kiến ​​thức thành phản xạ chiến lược.

# 3\. Target Users

Việc xác định đối tượng mục tiêu giúp tối ưu hóa độ sâu của các kịch bản mô phỏng, đảm bảo cả tính thử thách và giá trị giáo dục.

- **Phân khúc người dùng:**
    - **Sinh viên ngành Tài chính:** Cần có môi trường thực hành rủi ro thấp để nhận được phản hồi định lượng ngay lập tức.
    - **Pre-seed/Founder:**Cần phải thử nghiệm các chiến lược huy động vốn khác nhau và hiểu cách cân bằng giữa sự cường điệu và tính minh bạch.
- **Nhu cầu cốt lõi:** Hệ thống phản hồi tức thời về tình trạng dự án cho phép thử nghiệm và điều chỉnh liên tục để xây dựng tư duy quản lý dòng tiền và quan hệ với nhà đầu tư.
- **Ngữ cảnh sử dụng:** Sản phẩm này phù hợp cho các buổi học hoặc các buổi hội thảo khởi nghiệp nhóm từ 2-10 người, có người điều phối.

# 4.Chức năng hiện tại của sản phẩm

FUN(D) RAISING là một nền tảng mô phỏng tài chính đa người chơi hoàn chỉnh dựa trên web, tích hợp một công cụ tính toán tài chính tinh vi.

- **Quản lý phiên:** Người chủ trì tạo phòng, điều phối các giai đoạn và theo dõi bảng xếp hạng theo thời gian thực.
- **Khởi động dự án chuyên sâu:** Các nhà sản xuất thiết lập hồ sơ tài chính bao gồm từ giá bán và chi phí sản xuất đến cơ cấu vốn chi tiết.
- **Cơ chế trò chơi thẻ bài chiến thuật:**

42 Active cards được phân loại thành 3 nhóm, và các lá bài cũng được cân bằng theo 3 cấp độ energy cost để phân biệt giữa các hành động nhỏ, trung bình và các quyết định chiến lược lớn. 3 nhóm thẻ:

- - **Động lực thị trường (Đỏ):** Thúc đẩy tăng trưởng và sự sôi động của thị trường.
    - **Khả năng phục hồi và niềm tin (Xanh):**Tăng cường lòng tin và tính minh bạch.
    - **Vốn và Quản trị (Tím):** Tối ưu hóa cơ cấu vốn và quản trị.

Hệ thống Reaction cards: 7 thẻ phản ứng tập trung vào các tình huống khẩn cấp liên quan đến sự tồn tại của công ty khởi nghiệp.

**Hệ thống 200 Investor Bot:**

- - **FOMO:** Theo dõi xu hướng và thông tin trên truyền thông.
    - **Value Hunter:** Hãy tập trung vào các chỉ số cơ bản (Điểm nội tại).
    - **Whale:** Các nhà đầu tư lớn cực kỳ nhạy cảm với cơ cấu vốn và Tính hợp lý của định giá.
    - **Ngẫu nhiên:** Thể hiện sự biến động và bất ổn của thị trường.
- Từ đó việc sử dụng các bot với hồ sơ tâm lý khác nhau tạo ra một thị trường khách quan và nhất quán. Ngoài việc chơi thắng game, nhà đầu tư còn phải học cách phản ứng với các loại dòng vốn khác nhau, phát triển tư duy chọn lọc để lựa chọn các dự án phù hợp.

# 5\. Dữ liệu đầu vào

Độ tin cậy của kết quả mô phỏng phụ thuộc vào độ chính xác của dữ liệu đầu vào. Hệ thống áp dụng các ngưỡng nghiêm ngặt được rút ra từ điều kiện thực tế.

|     |     |
| --- | --- |
| **Đầu vào hoặc thông tin** | **Ý nghĩa tài chính** |
| Quy mô dự án | Quy mô dự án ảnh hưởng đến mục tiêu tài trợ và số giai đoạn. |
| Giá bán lẻ (USD) | Giá niêm yết trước khi trừ chiết khấu kênh phân phối |
| Phí thương mại điện tử (%) | Phí nền tảng thị trường |
| Phí bán lẻ (%) | Chiết khấu thương mại dành cho các đối tác bán lẻ truyền thống |
| Phí kênh trực tiếp (%) | Chi phí bán hàng thông qua trang web/fanpage riêng |
| Nguyên liệu trực tiếp (USD) | Nguyên liệu thô trên mỗi đơn vị |
| Đóng gói trực tiếp (USD) | Mỗi sản phẩm bao gồm hộp, túi, nhãn, sách hướng dẫn sử dụng. |
| Chi phí nhân công trực tiếp (USD) | Tiền lương công nhân mỗi đơn vị sản phẩm |
| Mức độ lỗi (%) | Tỷ lệ sản phẩm bị hư hỏng do lỗi (0 - 10%) |
| Month 1 units | Doanh số dự kiến ​​trong tháng đầu tiên (0–100.000) |
| Month 3 units | Doanh số dự kiến ​​trong tháng 3 (0–100.000) |
| Month 6 units | Doanh số dự kiến ​​trong tháng thứ 6 (0–100.000) |
| Chi phí vận hành cố định (USD/tháng) | Chi phí hàng tháng không thay đổi theo sản lượng (1.000–100.000) |
| Chi phí tiếp thị (USD/tháng) | Ngân sách hàng tháng cho quảng cáo, khuyến mãi (0–100.000) |
| Vốn chủ sở hữu (USD) | Vốn đầu tư của các nhà sáng lập (0–300.000) |
| Vay ngân hàng (USD) | Số tiền vay từ ngân hàng (0–300.000) |
| Lãi suất cho vay (%/năm) | Lãi suất cho vay hàng năm (5–100%) |
| Cổ phần được chào bán (%) | Tỷ lệ phần trăm cổ phần công ty được bán cho nhà đầu tư (0,1–99,9%) |
| Mục tiêu gây quỹ (USD) | Số tiền cần huy động từ các nhà đầu tư (tùy thuộc vào quy mô) |
| Scenario events (ngẫu nhiên từ 24 scenarios) | Mô phỏng các rủi ro/cơ hội về thị trường, nội bộ và pháp lý. |
| Active cards (người chơi chọn từ bộ bài) | Quyết định chiến lược ngắn hạn |
| Reaction cards (được kích hoạt bởi điều kiện) | Ứng phó khủng hoảng |
| Các tùy chọn của bot đầu tư (200 bot với trọng số, memory decay, độ nhạy) | Mô phỏng các hành vi khác nhau của nhà đầu tư. |
| Tất cả dữ liệu tài chính và thị trường | Đánh giá tổng thể về công ty khởi nghiệp |

# 6\. Logic và Quy tắc xử lý

Bộ máy tài chính là "trái tim" của hệ thống, xử lý dữ liệu thông qua sáu lớp logic liên kết chặt chẽ:

|     |     |     |     |
| --- | --- | --- | --- |
| **Chỉ báo / Thành phần** | **Công thức trong mã** | **Tại sao lại chọn chỉ số này?** | **Vì sao cần thiết trong trò chơi** |
| Bước 0 - Xử lý sơ bộ (áp dụng cho tất cả các chỉ số bên dưới) |     |     |     |
| price_real | total_fees = fee_ecom + fee_retail + fee_direct price_real = price × (1 − total_fees/100) | Doanh thu ròng thực tế trên mỗi đơn vị sau khi trừ phí kênh. Người chơi nhập một mức giá duy nhất, nhưng doanh thu thực tế phải trừ đi phí kênh. | Nếu không có điều này, tỷ suất lợi nhuận gộp sẽ bị tính toán sai - một dự án trông có vẻ sinh lời nhưng thực chất lại đang thua lỗ cho các kênh phân phối. Bot sẽ bị đánh lừa và đầu tư vào các dự án yếu kém. |
| cogs_unit | cogs_unit = (material + packaging + labor) × (1 + defect_rate/100) | Chi phí sản xuất thực tế trên mỗi đơn vị sản phẩm, bao gồm cả tỷ lệ phế phẩm. Tỷ lệ lỗi 5% yêu cầu 105 đơn vị để bán được 100 đơn vị. | Việc phân tách giá vốn hàng bán (COGS) thành 4 lĩnh vực (theo thiết kế biểu mẫu) phản ánh cấu trúc chi phí thực tế. Các dự án thâm dụng lao động sẽ bị phạt nặng hơn khi tỷ lệ lỗi cao. |
| monthly_burn | monthly_burn = fixed_cost + marketing_cost + loan × interest_rate/100/12 | Tổng chi phí tiền mặt bắt buộc hàng tháng, không phụ thuộc vào doanh số bán hàng. Bao gồm chi phí cố định, chi phí tiếp thị và lãi vay hàng tháng. | Chỉ số sống còn quan trọng: một công ty khởi nghiệp hết tiền mặt trước khi huy động đủ vốn sẽ phá sản. Được sử dụng để tính toán burn_score, runway và kiểm tra phá sản trong process_phase. |
| Nhóm A - Điểm nội tại (tối đa 100 điểm, 6 thành phần) |     |     |     |
| gm_score (0–30 pts) | gm = (price_real − cogs_unit) / price_real if gm > 0.2: score = 20 + 10×(1−e^{−5×(gm−0.2)/0.6}) else: score = max(0, 20×(gm/0.2)) | Tỷ suất lợi nhuận gộp đo lường lợi nhuận gộp trên mỗi đô la doanh thu. Đây là chỉ số có trọng số cao nhất (30 điểm) vì nó là thước đo cơ bản nhất - một dự án có tỷ suất lợi nhuận âm không thể tồn tại lâu dài. Hàm số mũ trên 0,2 sẽ thưởng cho các dự án có tỷ suất lợi nhuận cao với lợi nhuận giảm dần. | Bot sử dụng điểm nội tại làm cơ sở cho các quyết định đầu tư. gm_score có trọng số cao nhất vì trong các công ty khởi nghiệp thực tế, biên lợi nhuận gộp là điều đầu tiên các nhà đầu tư xem xét - nó cho thấy còn lại bao nhiêu để trang trải chi phí cố định và tạo ra lợi nhuận. |
| burn_score (0–20 pts) | burn_rate = monthly_burn / target_funding if burn_rate < 0.3: score = 15 + 5×(1−e^{−4×(0.3−r)/0.25}) else: score = max(0, 15×(1−(r−0.3)/0.7)) | Tỷ lệ tiêu hao tiền = tỷ lệ chi tiêu hàng tháng so với tổng số vốn mục tiêu. Chỉ số này đo lường tốc độ tiêu hao tiền mặt của công ty khởi nghiệp. Ngưỡng 0,3 có nghĩa là việc chi tiêu hơn 30% vốn mục tiêu hàng tháng bắt đầu bị phạt. | Một dự án có chi phí hoạt động cao sẽ hết tiền trước khi hoàn tất vòng gọi vốn. Bot cần nhận ra điều này - nếu không, nó sẽ đầu tư vào các công ty khởi nghiệp sắp phá sản. Chỉ số burn_score giúp bot tránh xa các dự án "chi phí hoạt động cao, thời gian hoạt động ngắn". |
| growth_score (0–20 pts) | growth = (units_m6 / units_m1) − 1 if growth > 0: score = 10 + 10×(1−e^{−3×g/0.5}) else: score = max(0, 10×(1+g/0.5)) | Tốc độ tăng trưởng khối lượng từ tháng 1 đến tháng 6, đo lường đà phát triển của dự án. Hàm số mũ thưởng cho sự tăng trưởng nhanh chóng với lợi nhuận giảm dần - ngăn chặn việc gian lận bằng cách nhập số lượng đơn vị/tháng 6 bị thổi phồng. | Trò chơi mô phỏng nhiều giai đoạn. Một dự án có tốc độ tăng trưởng mạnh mẽ sẽ tự nhiên thu hút bot qua nhiều vòng gọi vốn - điều này rất thực tế: nhà đầu tư không chỉ nhìn vào tình trạng hiện tại mà còn nhìn vào quỹ đạo phát triển. |
| revenue_score (0–10 pts) | avg_units = (units_m1 + units_m6) / 2 revenue_year = avg_units × 12 × price_real score = min(10, log10(revenue_year/100000)/2 × 10) | Doanh thu dự kiến ​​hàng năm, được biểu diễn theo thang logarit. Thang logarit có nghĩa là một dự án 1 tỷ đô la không đạt điểm gấp 10 lần so với một dự án 100 triệu đô la - điều này phản ánh cách các nhà đầu tư thực sự đánh giá quy mô tuyệt đối. | Doanh thu theo năm cũng được sử dụng để tính toán giá trị ước tính thông qua tỷ lệ P/S. Các dự án có doanh thu cao hơn sẽ có giá trị định giá cao hơn - nhưng không theo tỷ lệ tuyến tính. Trọng số là 10 điểm (thấp hơn lợi nhuận gộp và chi phí hoạt động) vì quy mô quan trọng nhưng ít quan trọng hơn hiệu quả. |
| efficiency_score (0–10 pts) | annual_profit = (price_real−cogs_unit) × units_m6×12 − burn×12 roe = annual_profit / total_capital score = min(10, roe×10) | ROE (Tỷ suất lợi nhuận trên vốn chủ sở hữu) đo lường lợi nhuận tạo ra trên mỗi đơn vị vốn. Không giống như gm_score đo lường tỷ lệ, chỉ số này đo lường lợi nhuận tuyệt đối sau khi trừ đi chi phí cố định - một dự án có tỷ suất lợi nhuận cao nhưng chi phí cố định quá lớn sẽ bị đánh giá thấp ở đây. | Một công ty khởi nghiệp sử dụng vốn hiệu quả sẽ tạo ra lợi nhuận cao hơn so với các đối thủ cạnh tranh khi sử dụng cùng một lượng vốn. Bot cần phân biệt giữa các dự án "có lợi nhuận" và các dự án "hiệu quả" - chúng không giống nhau. |
| leverage_score (0–10 pts) | debt_ratio = loan / owner_equity if ratio < 0.5: score = 5 + ratio×10 elif ratio ≤ 1.5: score = 10−(ratio−0.5)×5 else: score = max(0, 5−(ratio−1.5)×3) | Đánh giá cấu trúc nợ trên vốn chủ sở hữu. Hàm hình thang: tỷ lệ thấp (0–0,5) được điểm trung bình (quá thận trọng); tỷ lệ vừa phải (0,5–1,5) được điểm cao nhất (đòn bẩy tốt); tỷ lệ cao (>1,5) bị trừ điểm (rủi ro mất khả năng thanh toán). | Phản ánh các nguyên tắc tài chính: một lượng nợ nhất định là tốt (đòn bẩy), nhưng quá nhiều lại nguy hiểm. Một dự án được tài trợ hoàn toàn bằng vốn chủ sở hữu sẽ bỏ lỡ lợi ích của đòn bẩy; các dự án sử dụng đòn bẩy quá mức sẽ thấy chi phí hoạt động hàng tháng tăng lên cùng với lãi suất và đối mặt với rủi ro phá sản cao hơn. |
| security_penalty & reg_risk_penalty | sec_pen = max(0, (50−security)/5) reg_pen = reg_risk / 10 intrinsic = max(0, intrinsic−sec_pen−reg_pen) | Trừ điểm nội tại đối với các dự án bỏ qua vấn đề an ninh và tuân thủ quy định. Cứ mỗi 5 điểm an ninh dưới 50 sẽ bị trừ 1 điểm; cứ mỗi 10% rủi ro quy định sẽ bị trừ 1 điểm. Áp dụng sau khi tất cả 6 thành phần được tính toán. | Được thêm vào sau khi thử nghiệm cho thấy bot không thể phân biệt được các dự án thiếu cẩn trọng trong việc tuân thủ quy định. Những hình phạt này buộc người chơi phải xem xét vấn đề bảo mật và cấp phép - chứ không chỉ tối ưu hóa tài chính. |
| Nhóm B - Định giá & ROI |     |     |     |
| estimated_valuation | ps_ratio = 3.0 (baseline) if hype>70: ps_ratio += 2 elif hype&lt;30: ps_ratio −= 1 if growth&gt;0.5: ps_ratio += 1.5 ps_ratio = clamp(ps_ratio, 1.5, 15) valuation = revenue_year × ps_ratio | Sử dụng tỷ lệ P/S (Giá trên Doanh thu) - phương pháp định giá phổ biến cho các công ty khởi nghiệp chưa có lợi nhuận. Mức cơ sở là 3×, được điều chỉnh theo sự cường điệu (tâm lý thị trường) và tốc độ tăng trưởng. clamp(1.5, 15) ngăn chặn các định giá phi lý. | Định giá là một kết quả quan trọng mà các nhà đầu tư nhìn thấy trên bảng điều khiển. Sự thổi phồng ảnh hưởng đến tỷ lệ P/S vì trên thực tế, các công ty khởi nghiệp đang nổi luôn được định giá cao hơn các yếu tố cơ bản - điều này phản ánh chính xác thị trường đầu tư mạo hiểm. |
| roi_norm | raw_roi = max(0, (valuation−total_invested)/total_invested×100) roi_norm = min(100, 20×log10(raw_roi+1)) | ROI được chuẩn hóa về \[0, 100\] bằng cách sử dụng hàm logarit để tránh các giá trị ngoại lệ. Một dự án có ROI 10% và 1000% không nên chênh lệch nhau 100 lần về điểm số - thang logarit làm giảm sự chênh lệch này. | final_score sử dụng roi_norm để tính toán roi_score. Bot cũng sử dụng nó một cách gián tiếp thông qua attractiveness(). Các dự án có ROI tốt sẽ giữ được sự đầu tư của bot qua nhiều giai đoạn. |
| valuation_sanity | mult = valuation / revenue_year if mult < 1: score = 30−(1−mult)/1×30 elif mult ≤ 3: score = 80+(mult−1)/2×20 elif mult ≤ 5: score = 80−(mult−3)/2×40 else: score = max(0, 40−(mult−5)/2×40) | Kiểm tra xem định giá có "lành mạnh" hay không - Tỷ lệ P/S từ 1–3 lần được coi là hợp lý (điểm cao nhất); P/S &lt;1 (định giá thấp) hoặc &gt;5 (định giá cao) sẽ bị phạt. Hàm hình thang phản ánh điểm tối ưu trong định giá. | Ngăn chặn người chơi lợi dụng việc thay đổi doanh thu theo năm để thổi phồng giá trị dự án một cách giả tạo. Bot nhận diện các dự án bị định giá quá cao và sẽ đầu tư ít hơn - tương tự như cách các nhà đầu tư mạo hiểm thực tế từ chối các thương vụ có giá chào bán quá cao. |
| reg_risk | base = 20 if has_license else 80 if legal_cost ≥ 5% target_funding: base += 20 reg_risk = clamp(base−transparency/10, 0, 100) | Rủi ro pháp lý tổng hợp từ: có giấy phép (−60 rủi ro), đầu tư vào chi phí pháp lý (−20 rủi ro), tính minh bạch cao giúp giảm rủi ro hơn nữa. Chỉ số nghịch đảo - càng cao càng tệ. | Được sử dụng trong reg_risk_penalty (trừ giá trị nội tại) và trong attractiveness() của bot. Các dự án có reg_risk cao sẽ bị bot tránh - phản ánh rằng rủi ro pháp lý là lý do phổ biến nhất khiến các công ty khởi nghiệp thất bại tại Việt Nam. |
| runway | avail = available_cash (or equity + loan) runway = floor(avail / monthly_burn) = 999 if monthly_burn = 0 | Một công ty khởi nghiệp có thể tồn tại được bao nhiêu tháng với lượng tiền mặt hiện có? Chỉ số đơn giản nhưng quan trọng nhất: nếu thời gian tồn tại (runway) ít hơn số giai đoạn còn lại (remaining stages), dự án gần như chắc chắn sẽ phá sản trước khi huy động đủ vốn. | process_phase sử dụng runway (một cách gián tiếp thông qua available_cash) để kiểm tra tình trạng phá sản sau mỗi giai đoạn. Người chơi có thể thấy runway trên bảng điều khiển - đây là chỉ báo trực quan nhất về thời gian còn lại. |

1.  **Tính toán các chỉ số cốt lõi:**
    - Net Price = Retail Price × (1 – Fees/100). (Condition: Net Price > Adjusted COGS).
    - Monthly Burn = Fixed Cost + Marketing + (Loan × Interest / 12).
    - Runway = Available Cash / Monthly Burn.
2.  **Điểm nội tại (0-100):** Tổng hợp từ 6 yếu tố có trọng số: Profit Margin (GM - 30 điểm), Burn Rate Control (20 điểm), Growth (20 điểm), Revenue Size (10 điểm), Efficiency (10 điểm), Leverage (10 điểm).
3.  **Định giá và ROI:**
    - **Valuation Sanity:** Đánh giá dựa trên tỷ lệ P/S từ **1.5x đến 15x**.
    - **ROI Norm:** 20 × log10(Estimated Valuation / Total Invested + 1), limit 100.
4.  **Logic đầu tư của Bot:** Sử dụng **Hàm Softmax** phân bổ vốn dựa trên mức độ hấp dẫn.
    - **Cơ chế rút tiền:**Robot sẽ rút vốn đầu tư nếu mức độ hấp dẫn của dự án giảm hơn **2.5 điểm** tổng hoặc giảm dần theo **5 điểm** chỉ trong một giai đoạn duy nhất.
    - **Memory decay:** Các bot học hỏi từ những sai lầm trong niềm tin trước đây và sử dụng chúng để giảm hiệu quả gây quỹ hiện tại của mình.
5.  **Điều kiện loại trừ (Phá sản):** Nếu số dư tiền mặt âm (**Tiền mặt < 0)** dự án bị loại ngay lập tức.
6.  **Công thức tính điểm cuối cùng:** Final Score = \[Funding_Progress × 30 + (100 – Phases_Used) × 0.2 + (ROI_Norm/100) × 30 + (Transparency/100) × 20\] × scale_factor × (1 + Funding_Progress).

|     |     |     |     |
| --- | --- | --- | --- |
| **Thành phần** | **Công thức trong Code** | **Trọng số và ý nghĩa** | **Vì sao cần thiết trong trò chơi** |
| funding_score (max 40 pts) | funding_score = funding_progress × 40 | Trọng số 40% - cao nhất. Lý do: mục tiêu cốt lõi của trò chơi là gây quỹ thành công. Một dự án gây quỹ được 100% mục tiêu sẽ nhận được 40 điểm; 50% sẽ nhận được 20 điểm. Trọng số cao nhất đảm bảo điều kiện chiến thắng chính được phản ánh rõ nét nhất trong điểm số. | Nếu điểm số tài trợ chỉ chiếm 20-25%, người chơi có thể thắng mà không cần huy động đủ vốn - làm mất đi logic cốt lõi của trò chơi. 40% đảm bảo mục tiêu chính không thể bị bỏ qua. |
| speed_score (max 20 pts) | if complete_phase is not None: speed = 20×(1−(complete_phase−1)/(max_phase−1)) else: speed = 0 | Trọng số 20%. Công thức tuyến tính: hoàn thành ở giai đoạn 1 được 20 điểm, ở giai đoạn cuối được 0 điểm. Trọng số bằng với điểm ROI và điểm giao dịch: tốc độ là lợi thế cạnh tranh, không phải là yêu cầu bắt buộc - quan trọng nhưng không quan trọng hơn ROI. | Tính năng này tạo ra sự cạnh tranh khi nhiều người chơi cùng huy động đủ vốn. Nếu không có speed_core, trò chơi sẽ trở nên nhàm chán khi mọi người đều hoàn thành. Nó cũng phản ánh thực tế: huy động vốn nhanh chóng giúp tiết kiệm chi phí và nắm bắt thời điểm thị trường tốt hơn. |
| roi_score (max 20 pts) | roi_score = min(20, (roi_norm/100) × 20) | Trọng số 20%. roi_norm đã được chuẩn hóa về \[0, 100\] trong calculate_metrics, vì vậy nó ánh xạ trực tiếp đến \[0, 20\]. Tương đương với speed_score: ROI tốt báo hiệu thiết kế dự án chất lượng cao nhưng không phải là yếu tố quyết định - nó chỉ là yếu tố phân định thắng thua. | Thưởng cho những người chơi thiết kế các dự án thực sự có ROI cao, chứ không chỉ những người huy động đủ vốn. Ngăn chặn chiến lược "đầu tư nhiều khoản nhỏ" - bot chỉ đầu tư mạnh vào các dự án có ROI cao. |
| trans_score (max 20 pts) | trans_score = max(0, min(20, (transparency/100) × 20)) | Trọng số 20%. Tính minh bạch là một chỉ số người chơi xây dựng thông qua các thẻ và hành động (0–100). Ánh xạ tuyến tính đến \[0, 20\]. Trọng số bằng với ROI vì tính minh bạch là điều kiện tiên quyết mà các nhà đầu tư yêu cầu - nếu thiếu nó, ngay cả những dự án có ROI cao cũng bị bot bỏ qua. | Điều này buộc các nhà đầu tư phải chú trọng vào tính minh bạch, chứ không chỉ tối ưu hóa tài chính. Nó phản ánh thực tế: các công ty khởi nghiệp thiếu minh bạch (không kiểm toán, không báo cáo) sẽ bị nhà đầu tư từ chối ngay cả khi các con số trông rất tốt. |
| scale_factor | scale_map = {S:0.8, M:0.9, L:1.0} final = raw × scale_factor × bonus | Hệ số điều chỉnh dựa trên quy mô dự án được chọn khi bắt đầu trò chơi. Quy mô S khó huy động vốn hơn nên được cộng thêm 0,8 điểm (điểm tối đa thấp hơn); Quy mô L được cộng thêm 1,0 điểm. Đây không phải là hình phạt - chỉ là sự cân bằng trò chơi cho các lựa chọn quy mô khác nhau. | Nếu không có scale_factor, người chơi sẽ luôn chọn Scale L để đạt điểm cao hơn. Hệ số này tạo ra sự đánh đổi: Scale S kiếm được ít tiền hơn và có thể hoàn thành sớm hơn (speed_score cao) nhưng tổng điểm được nhân với 0,8. |
| funding_bonus | funding_bonus = (1 + funding_progress)/2 final = raw × scale_factor × funding_bonus | Hệ số nhân thưởng cuối kỳ, dao động từ 0,5 đến 1,0 dựa trên tiến độ gây quỹ. Dự án gây quỹ được 100%: thưởng = 1,0. Dự án gây quỹ được 0%: thưởng = 0,5 (nửa điểm). Mục đích: làm nổi bật sự khác biệt giữa các dự án thành công và thất bại. | Nếu không có funding_bonus, một dự án huy động được 60% và một dự án huy động được 100% có thể đạt điểm tương đương nếu ROI/tốc độ tốt. Phần thưởng này đảm bảo funding_progress có hiệu ứng phi tuyến tính - huy động càng nhiều vốn, điểm càng tăng nhanh. |

Việc sử dụng hàm Softmax và cơ chế rút tiền nghiêm ngặt giúp mô phỏng tránh xa các thuật toán tuyến tính đơn điệu, tạo ra một thị trường phản ứng nhạy bén với các tín hiệu quản lý.

|     |     |     |     |
| --- | --- | --- | --- |
| Nhiệm vụ | Mô tả | Đầu vào | Đầu ra |
| Tạo 200 nhà đầu tư ảo | Tạo các bot với tính cách độc đáo (FOMO, Value Hunter, Whale, Random). Mỗi bot có một lớp tài sản, số vốn, hype_sens, trans_sens, memory_decay_rate và vectơ trọng lượng. random.seed(42) đảm bảo khả năng tái tạo. | Được tạo ra bằng phương pháp ngẫu nhiên có hạt giống. | Danh sách BOTS (200 từ điển) được Phuc sử dụng trong process_phase() và được Jin lưu trữ trong trạng thái phòng. |
| Tính toán mức độ hấp dẫn của dự án | Trung bình có trọng số tối đa 8 khóa chỉ số với hệ số nhân độ nhạy trên mỗi bot; hình phạt đánh giá_tính hợp lý (tối thiểu −45 điểm); trust scaling (×trust/100); bounded noise ±5 (±10 với Random). | Số liệu dự án từ Phúc; trust_scores từ Jin. | Mỗi cặp dự án-bot được gán một điểm số hấp dẫn (0-100) để hướng dẫn các quyết định đầu tư/rút vốn. |
| Quá trình tăng tốc của bot cho từng giai đoạn | Giai đoạn 1: 20% số bot đang hoạt động (40 bot). Mỗi giai đoạn tiếp theo sẽ tăng số lượng lên 20%, tối đa 200 bot ở giai đoạn 5 trở lên. Điều này tạo ra một sự gia tăng hoạt động đầu tư thực tế. | Số phase hiện tại. | Tập hợp con các bot đang hoạt động đã được đưa vào vòng đầu tư. |
| Sự pha trộn của memory-decay | Lịch sử mức độ hấp dẫn của mỗi bot (5 giai đoạn gần nhất). Trung bình có trọng số (các giai đoạn gần đây hơn có trọng số cao hơn). Kết hợp với mức độ hấp dẫn hiện tại bằng cách sử dụng tỷ lệ suy giảm đặc trưng cho từng loại. | attractiveness_history từ bot_memory trong room. | final_attr (float) được dùng trong quyết định đầu tư/rút tiền. |
| Logic rút tiền | Nếu chênh lệch độ hấp dẫn giữa dự án tốt nhất và dự án hiện tại > 25 → rút 50%. Nếu chênh lệch > 15 → rút 25%. Nếu tiến độ gây quỹ > 80% → rút 0,3 lần ( giữ lại các dự án sắp được tài trợ). | Ma trận A (bot×project), mục phân bổ hiện tại. | Giảm số tiền cho mỗi dự án; hoàn trả các khoản tiền nhàn rỗi; cập nhật funding_progress và total_invested. |
| Phân bổ đầu tư (Softmax) | Softmax với nhiệt độ /35 (đã điều chỉnh từ /20) + hình phạt đa dạng (độ bão hòa × 30 trừ Softmax) để phân tán vốn. Giới hạn mỗi bot: 15% mục tiêu tài trợ trong giai đoạn 1, 20% từ giai đoạn 2. | Điểm hấp dẫn thay đổi, vốn nhàn rỗi. | Kinh phí được phân bổ cho các dự án; bảng funding_progress được cập nhật; bảng funding_complete_phase được ghi lại. |
| Các yếu tố hỗ trợ ổn định | get_bot_memory(): luôn sử dụng str(bot_id) để sửa lỗi chuyển đổi khóa int→string trong Flask JSON. ensure_room_lists(): chuẩn hóa tất cả các trường danh sách cho mỗi người chơi về độ dài chính xác trong mỗi yêu cầu. ensure_bot_alloc(): chuẩn hóa bot_alloc sau khi giải mã JSON. | Từ điển phòng (có thể được chuyển đổi qua JSON). | Trạng thái phòng an toàn và ổn định được thiết lập cho tất cả các hoạt động tiếp theo. |
| Aggregate_bot_actions() | Gom các sự kiện hành động thô của từng bot theo (loại, hành động, chỉ số người chơi) và cộng tổng số lượng. Trả về một danh sách sạch để hiển thị nhật ký. | Danh sách các từ điển hành động thô của bot từ process_phase(). | Nhật ký hoạt động tổng hợp của bot rất dễ đọc và hiển thị trên bảng điều khiển của máy chủ. |

# 7\. Luồng người dùng

Trải nghiệm này được thiết kế để phân tách vai trò của điều phối chiến lược và thực thi dự án.

- LUỒNG MÁY CHỦ:

1\. Người chủ trì mở ứng dụng và nhấn vào "Tạo phòng".

2\. Hệ thống tạo ra các liên kết tham gia duy nhất cho mỗi vị trí người chơi (2–10 người chơi).

3\. Người chủ trì chia sẻ liên kết với người chơi.

4\. Người dẫn chương trình chờ tất cả người chơi nộp dự án và hoàn thành bộ bài của mình.

5\. Người chủ trì nhấp vào "Bắt đầu trò chơi" để bắt đầu Giai đoạn 1.

6\. Sau khi người chơi đã đánh bài và nhấp vào "Sẵn sàng", người điều khiển trò chơi nhấp vào "Bắt đầu giai đoạn".

7\. Hệ thống áp dụng các sự kiện ngẫu nhiên, hiệu ứng thẻ bài, các yếu tố kích hoạt phản ứng và quyết định của bot.

8\. Người điều hành theo dõi bảng xếp hạng và lặp lại từ bước 6 cho đến khi tất cả các giai đoạn hoàn tất.

9\. Người dẫn chương trình xem bảng xếp hạng cuối cùng và công bố người chiến thắng.

- LUỒNG CHƠI CỦA NGƯỜI CHƠI:

1\. Người chơi truy cập trang web thông qua một liên kết.

2\. Người chơi điền các chỉ số tài chính (quy mô, giá cả, giá vốn hàng bán, dự báo, chi phí hoạt động, vốn đầu tư).

3\. Người chơi chọn 22 lá bài chủ động và tối đa 3 lá bài phản ứng.

4\. Người chơi chờ người chủ trì bắt đầu trò chơi.

5\. Qua mỗi vòng chơi: Người chơi trải nghiệm các sự kiện ngẫu nhiên từ thị trường.

6\. Người chơi chọn chơi từ 5 lá bài, mỗi lá bài có giá trị tối đa là 3 năng lượng để chơi.

7\. (Tùy chọn) Người chơi xáo bài để rút 5 lá bài mới.

8\. (Tùy chọn) Người chơi kích hoạt thẻ phản ứng nếu điều kiện kích hoạt xảy ra trong quá trình chơi.

9\. Người chơi nhấp vào "Sẵn sàng". Khi tất cả người chơi đã sẵn sàng, huấn luyện viên sẽ bắt đầu giai đoạn này.

10\. Người chơi xem lại số liệu thống kê và cập nhật thứ hạng trên bảng xếp hạng sau khi việc lựa chọn bot hoàn tất.

11\. Lặp lại các bước 5–10 cho tất cả các giai đoạn. Xem điểm số cuối cùng khi trò chơi kết thúc.

# 8\. Dữ liệu đầu ra

Phản hồi tức thì là chìa khóa để học hỏi thông qua kinh nghiệm.

- **Bảng xếp hạng thời gian thực:** Cập nhật tỷ lệ phần trăm, mức độ lan truyền thông tin, tính minh bạch và dự báo điểm số.
- **Chi tiết dự án:** Hiển thị Giá trị nội tại, Valuation Sanity (dựa trên tỷ lệ P/S), Runway, Hype và danh sách các nhà đầu tư hiện tại.
- Tiền mặt và dòng tiền cho từng giai đoạn của người chơi.
- **Nhật ký sự kiện:** Ghi lại toàn bộ lịch sử giao dịch thẻ và quyết định của bot. Đây là dữ liệu vô cùng quan trọng cho quy trình. Điều này giúp các giảng viên phân tích quá trình ra quyết định của học sinh sau mỗi buổi chơi.

# 9\. Các lựa chọn thiết kế chính

Để tối ưu hóa giá trị giáo dục trong phạm vi nguồn lực hạn chế, chúng tôi đã đưa ra những lựa chọn chiến lược sau:

- **Cơ chế thẻ:** Việc đơn giản hóa lối chơi trắc nghiệm, vốn liên quan đến các tương tác kinh doanh phức tạp, thành các quyết định riêng lẻ cho phép người chơi tập trung vào sự đánh đổi và giảm bớt gánh nặng cho người tạo ra trò chơi.
- **200 Bot:** Sau khi tham khảo các nền tảng gọi vốn cộng đồng từ nhiều nguồn khác nhau, con số này đảm bảo tính nhất quán và áp lực cạnh tranh liên tục, bất kể quy mô lớp học.
- **Tối ưu hóa công cụ cho trải nghiệm người dùng (UX/UI):** Sử dụng Python Flask và HTML/JS thuần túy để ưu tiên nguồn lực cho các phép tính tài chính phức tạp hơn là các hiệu ứng giao diện người dùng hào nhoáng không cần thiết cho mục tiêu giáo dục công nghệ.
- **Giảm thiểu (MVP):** Thay thế WebSocket bằng cơ chế thăm dò HTTP 3 giây một lần để đảm bảo tính ổn định.**Trạng thái trong bộ nhớ** trong một giai đoạn phát triển ngắn.

# 10\. Những điều nhóm đã làm tốt

- **Ứng dụng tài chính:** Tích hợp thành công sáu lớp logic vào một vòng lặp trò chơi mượt mà. Lý luận tài chính toàn diện và nhất quán. Tất cả sáu công thức cốt lõi (điểm nội tại, tính hợp lý của định giá, tiêu chuẩn ROI, thời gian giữ chân khách hàng, sức hấp dẫn, điểm cuối cùng) đều được thực hiện và phối hợp chính xác.
- Hệ thống gồm 200 bot đã phân biệt thành công hành vi của nhà đầu tư dựa trên các chỉ số dự án. Các bot FOMO, Value Hunter, Whale và Random phản ứng khác nhau đối với cùng một dự án, tạo ra sự đa dạng trong giáo dục.
- **Tính nhất quán về chủ đề:**Thiết kế thẻ bài được cân nhắc kỹ lưỡng. Mỗi trong số 42 thẻ bài chủ động và 10 thẻ bài phản ứng đều phản ánh một chiến lược kinh doanh thực tế, và hệ thống đếm thẻ (thẻ nào phù hợp với tình huống nào) bổ sung thêm chiều sâu chiến lược.
- **Hoạt động từ đầu đến cuối:**Hệ thống hoạt động ổn định, cho phép từ 2 đến 10 người chơi cùng lúc mà không gặp lỗi đồng bộ nghiêm trọng.
- Hệ thống máy chủ đa người chơi xử lý các hành động đồng thời của người chơi và quản lý trạng thái phòng mà không gây ra sự cố đáng kể, đây là một thách thức kỹ thuật lớn.
- Mẫu giao diện người dùng (UI) bao gồm tất cả các màn hình cần thiết, bao gồm bảng điều khiển của chủ phòng, màn hình gửi dự án của người chơi, công cụ xây dựng bộ bài và màn hình trò chơi, với hệ thống phân cấp trực quan rõ ràng và tương tác thân thiện với người dùng.
- **Cấu trúc rõ ràng:** Việc phân tách rõ ràng giữa Dữ liệu, Số liệu, Bot và API giúp hệ thống dễ dàng mở rộng quy mô. Nhóm đã phân chia trách nhiệm rõ ràng theo kiến ​​trúc: Minh phụ trách dữ liệu và hệ thống gắn thẻ, Phuc phụ trách các số liệu tài chính và chấm điểm, Khanh phụ trách hệ thống bot và phản hồi thị trường, Jin phụ trách phần backend Flask và định tuyến API, và Duong phụ trách thiết kế UI/UX và triển khai frontend.

# 11\. Những hạn chế hiện tại

- **Sự mất cân bằng về quy mô:**Công thức chấm điểm hiện tại đang áp đặt những hình phạt quá nặng đối với các dự án lớn (9 giai đoạn) do các thành phần của dự án.Các pha được sử dụngtrong công thức.
- **Sự mất cân bằng về quy mô:**Công thức chấm điểm hiện tại đang áp đặt những hình phạt quá nặng đối với các dự án lớn (9 giai đoạn) do các thành phần của dự án.Các pha được sử dụngtrong công thức.
- Những người chơi kết thúc dự án với giai đoạn nhỏ phải chờ đợi người khác trong khi không làm gì có thể dẫn đến sự nhàm chán.
- Khi một dự án kết thúc hoặc phá sản, sẽ không có thông báo nào hiển thị trên màn hình. Người chơi vẫn cần tương tác với các yếu tố khác để thông báo hiện lên.
- Rất khó để đạt được điểm số tối đa cuối cùng vì các tiêu chí đánh giá có nhiều hình thức trừ điểm.

# 12\. Những điều nhóm đã học được

- **Tư duy logic trước khi tiếp xúc với giao diện:** Hoàn thiện mô hình tài chính trong Excel trước khi lập trình là một bài học vô cùng quan trọng.
- **Quản lý sự mở rộng phạm vi dự án:** Việc bổ sung các tính năng như giảm bộ nhớ của Bot hoặc Mulligan rất thú vị nhưng đã làm chậm quá trình ổn định hệ thống cốt lõi.
- **Thử nghiệm trò chơi:** Chỉ thông qua việc chơi game, chúng ta mới có thể khám phá ra những chiến lược tối ưu làm phá vỡ sự cân bằng của trò chơi.
- **Các quyết định tài chính luôn liên quan đến sự đánh đổi:** Mỗi lựa chọn trên thẻ đều cho thấy rằng việc cải thiện một chỉ số có thể làm giảm chỉ số khác. Ví dụ, chi tiêu nhiều hơn cho tiếp thị có thể làm tăng sự chú ý, nhưng cũng làm tăng chi phí và giảm nguồn vốn hoạt động. Điều này giúp nhóm hiểu rằng quản lý tài chính là sự cân bằng giữa lợi ích và rủi ro.
- **Hiệu quả sử dụng vốn ảnh hưởng đến sức hấp dẫn đối với nhà đầu tư:** Nhóm nghiên cứu nhận thấy rằng các nhà đầu tư thích những dự án có thể tạo ra tăng trưởng với nguồn vốn hợp lý. Một công ty khởi nghiệp cần quá nhiều vốn để đạt được doanh thu hạn chế có thể trông kém hiệu quả và kém hấp dẫn hơn.
- **Phương pháp định giá công ty khởi nghiệp sử dụng tỷ lệ P/S:** Nhóm đã học cách sử dụng tỷ lệ Giá trên Doanh thu (P/S) – một phương pháp phổ biến để định giá các công ty chưa có lợi nhuận. Tỷ lệ này được điều chỉnh dựa trên tốc độ tăng trưởng và sự “thổi phồng” của thị trường, phản ánh chính xác các hoạt động đầu tư mạo hiểm thực tế.
- **Các chỉ số tài chính để đánh giá dự án:** Trong quá trình xây dựng cơ chế định giá và gây quỹ, nhóm nhận thấy rằng các nhà đầu tư cộng đồng ưu tiên các đặc điểm của dự án trước tiên, tiếp theo là các đặc điểm của người gây quỹ, và cuối cùng là các đặc điểm của khoản đầu tư. Đó là lý do tại sao trò chơi bao gồm các chỉ số như Tỷ suất lợi nhuận gộp, Tỷ lệ chi tiêu, Thời gian hoạt động và Tỷ suất lợi nhuận đầu tư (ROI) – những yếu tố quan trọng mà các nhà đầu tư sử dụng để quyết định xem một dự án gây quỹ có đáng để đầu tư hay không.
- **Các loại rủi ro trong gọi vốn cộng đồng:** Khác với hình thức gây quỹ truyền thống, gọi vốn cộng đồng tiềm ẩn nhiều rủi ro cụ thể. Nhóm nghiên cứu nhận thấy rằng một dự án có thể không khả thi (không đáng để đầu tư) hoặc lợi nhuận kỳ vọng có thể không đạt được. Ngoài ra, gọi vốn cộng đồng...Bản thân các nền tảng phải đối mặt với rủi ro trong việc duy trì hoạt động và bảo vệ lợi ích của các bên liên quan. Những rủi ro này được mô phỏng trong trò chơi thông qua cơ chế phá sản, rủi ro pháp lý và sự thay đổi các chỉ số sau mỗi giai đoạn.

# 13\. Gợi ý cho sinh viên tương lai

- **Cải tiến thuật toán:** Sử dụng **Hàm logarit** thay vì sử dụng hàm tuyến tính cho hình phạt thời gian trong công thức tính điểm, cách tính này cân bằng cơ hội cho các dự án quy mô lớn.
- **Nâng cấp kỹ thuật:**Hãy chuyển sang sử dụng WebSockets để loại bỏ độ trễ khi thăm dò dữ liệu HTTP.
- **Các tính năng bổ sung:** Hãy thiết kế một màn hình "Phân tích sau trận đấu" chi tiết để giải thích cụ thể các yếu tố dẫn đến thành công/thất bại.
- Hiểu được sản phẩm mình làm đang là gì: Khi có được bức tranh tổng thể sản phẩm mình làm như nào thì khi code sẽ dễ nghĩ ra những cách giải quyết vấn đề
- Luôn đảm bảo ý tưởng của mọi thành viên trong nhóm hòa hợp: vì đây là dự án cả nhóm, mỗi người tác riêng làm phần của mọi người thì dễ nhưng khi nối lại với nhau thì mới nhận ra những phần tắc, hoặc không nối được. Vì vậy, để tiến trình làm việc nhanh và hiệu quả hơn, thành viên trong nhóm cần chủ động thông báo tiến trình phần làm việc của mình
- Đối với những thành viên chưa có kinh nghiệm về mảng code, thành viên đấy có thể nhận phần logic game. Ngược lại, với những thành viên có chút kinh nghiệm về mảng này có thể đảm nhận phần nối hoặc giao diện.

**Kết luận:** FUN(D) RAISING đã chứng minh tiềm năng to lớn trong việc hiện đại hóa giáo dục tài chính. Với những cải tiến thuật toán và nâng cấp trải nghiệm thời gian thực, nó sẽ là một công cụ mạnh mẽ cho bất kỳ ai muốn nắm vững kỹ năng gây quỹ khởi nghiệp.