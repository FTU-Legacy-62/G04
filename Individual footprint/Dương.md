# TRƯỜNG ĐẠI HỌC NGOẠI THƯƠNG
NHA408E(2526-2)GD2.01
**DẤU ẤN CÁ NHÂN**
**FUN(D) RAISING**

Vũ Bách Dương
Mã sinh viên: 2312380808
Vai trò: Thiết kế UX/UI | Triển khai Frontend | Trải nghiệm người dùng
Nhóm 4 | Hà Nội, tháng 6 năm 2026

---

## Thông tin thành viên & Tổng quan vai trò

---

## Vai trò trong dự án
| Vai trò | Thiết kế UX/UI & Triển khai Frontend |
Tôi chịu trách nhiệm toàn bộ những gì người chơi và người quản trò nhìn thấy và tương tác trong FUN(D) RAISING: thiết kế UX, ngôn ngữ thiết kế trực quan, và toàn bộ phần triển khai frontend. Tôi đã xây dựng hai tệp HTML/CSS/JavaScript: host.html (bảng điều khiển quản lý trò chơi) và play.html (màn hình tương tác của người chơi) giao tiếp với API của Jin, hiển thị trạng thái trò chơi theo thời gian thực, xử lý tất cả các sự kiện nhập liệu của người chơi, và hiển thị kết quả tính toán.

Trong kiến trúc của nhóm, tôi là tầng Giao diện người dùng. Frontend của tôi gửi các yêu cầu HTTP đến các route API của Jin, nhận phản hồi JSON, và cập nhật giao diện trình duyệt để phản ánh trạng thái trò chơi hiện tại. Tôi cũng thực hiện polling API mỗi 2 giây để cung cấp cập nhật bảng xếp hạng và chỉ số gần như theo thời gian thực mà không cần kết nối WebSocket liên tục.

Công việc của tôi là thứ làm cho FUN(D) RAISING trở nên có thể nhìn thấy và chơi được. Mọi đóng góp của các thành viên khác trong nhóm đều trở nên hữu hình khi được hiển thị trên màn hình thông qua giao diện của tôi.

---

## Dấu ấn cá nhân trong sản phẩm

### Bảng điều khiển Host (host.html)

Tôi đã thiết kế và triển khai bảng điều khiển host từ đầu. Phiên bản đầu tiên cung cấp cho người tổ chức trò chơi các tính năng thiết yếu: biểu mẫu tạo phòng (tên phòng, số lượng người chơi), danh sách link tham gia trực tiếp, bảng tiến trình trò chơi theo thời gian thực, nhật ký sự kiện, và bảng xếp hạng cập nhật mỗi 2 giây. Các nút điều khiển của host được phân biệt rõ ràng bằng màu sắc và vị trí.

Sau nhiều vòng kiểm thử từ góc độ người dùng (nhắm đến giảng viên tổ chức trong môi trường lớp học), tôi đã thêm các cải tiến sau để nâng cao đáng kể trải nghiệm người dùng:

1. Việc sao chép thủ công nhiều link tham gia riêng lẻ dễ xảy ra lỗi với các giảng viên quản lý lớp học lớn, vì vậy tôi đã thêm nút "Sao chép tất cả" để người dùng có thể sao chép tất cả link tham gia vào clipboard chỉ bằng một cú nhấp. Giảng viên giờ thể dán trực tiếp vào email, ứng dụng nhắn tin, hoặc slide bài giảng.

2. Giảng viên thường cần chia một lớp lớn thành nhiều nhóm chơi nhỏ hơn (ví dụ: 24 sinh viên → 6 phòng 4 người chơi). Thiết kế ban đầu chỉ hỗ trợ một phòng hoạt động tại một thời điểm. Vì vậy, tôi đã triển khai bộ chọn dropdown phòng và nút "Tạo phòng mới" ngay trong bảng điều khiển host. Host giờ có thể tạo, đặt tên, chuyển đổi và theo dõi nhiều phòng cùng lúc từ một bảng điều khiển duy nhất. Mỗi phòng duy trì trạng thái trò chơi, danh sách người chơi và tiến trình giai đoạn độc lập.

3. Các host cần kiểm tra lại các giai đoạn đã hoàn thành để chấm điểm, giải quyết tranh chấp, hoặc lấy ví dụ giảng dạy, nhưng không có dữ liệu lịch sử nào được lưu. Vì vậy, tôi đã xây dựng dropdown lưu trữ giai đoạn, lưu lại mọi giai đoạn đã hoàn thành. Khi chọn một giai đoạn, một modal chi tiết hiển thị: Tỷ lệ tài trợ, tiền mặt hiện có và thay đổi dòng tiền của từng người chơi (màu xanh cho dương, màu đỏ cho âm). Các bảng giao dịch bot tổng hợp cho thấy loại bot nào đã đầu tư hoặc rút tiền từ người chơi nào, với tổng số tiền cho mỗi người chơi. Điều này biến bảng điều khiển thành một hồ sơ kiểm tra đầy đủ cho phân tích sau trò chơi và chấm điểm.

4. Trong quá trình phát triển, các lỗi backend khiến việc debug trở nên khó khăn. Tôi cần khả năng hiển thị để biết hệ thống đang làm gì. Vì vậy, tôi đã thêm bảng nhật ký sự kiện ban đầu với mục đích debug. Sau khi nhận ra giá trị của nó cho việc điều hành lớp học, tôi quyết định giữ lại nó như một tính năng vĩnh viễn. Nhật ký này đã trở nên thiết yếu cho việc xử lý sự cố trực tiếp trong lớp học và tính minh bạch trong giảng dạy.

5. Người chơi chọn các quy mô dự án khác nhau (Nhỏ = 5 giai đoạn, Trung bình = 7 giai đoạn, Lớn = 9 giai đoạn). Việc so sánh điểm trực tiếp giữa các quy mô là không công bằng vì các dự án quy mô lớn hơn có nhiều giai đoạn hơn để tích lũy tài trợ. Thay vì một bảng xếp hạng duy nhất, tôi đã triển khai ba bảng xếp hạng riêng biệt, một cho mỗi quy mô (Nhỏ/Trung bình/Lớn). Mỗi bảng xếp hạng chỉ xếp hạng những người chơi trong quy mô đó, đảm bảo so sánh công bằng. Host có thể thấy cả bảng xếp hạng tổng thể (để tham khảo nhanh) và bảng xếp hạng theo quy mô (để đánh giá công bằng) cạnh nhau.

6. Các phiên bản đầu có quá nhiều nút điều khiển, khiến host bối rối về nút nào cần nhấn. Sau nhiều vòng kiểm thử với người dùng, tôi đã gộp các điều khiển thành ba nút được đặt nhãn rõ ràng:

| Nút | Chức năng | Khi nào được kích hoạt |
|---|---|---|
| CHẠY GIAI ĐOẠN | Đưa trò chơi sang giai đoạn tiếp theo | Chỉ khi tất cả người chơi đang hoạt động đã sẵn sàng |
| KẾT THÚC TRÒ CHƠI | Dừng trò chơi trước khi hoàn thành tất cả các giai đoạn | Luôn có thể dùng trong khi trò chơi đang diễn ra |
| ĐẶT LẠI TRÒ CHƠI | Xóa tất cả dữ liệu trò chơi; người chơi khởi động lại bằng cùng phòng và link | Luôn có thể dùng; lý tưởng cho các trận demo |

Bảng điều khiển host là trung tâm chỉ huy của toàn bộ trò chơi. Nếu nó gặp sự cố hoặc gây nhầm lẫn cho giảng viên, trò chơi không thể được tiến hành. Các cải tiến của tôi — quản lý đa phòng, sao chép link một nhấp, lưu trữ giai đoạn với dòng tiền, bảng xếp hạng công bằng theo quy mô, và ba nút điều khiển rõ ràng — trực tiếp giải quyết các nhu cầu thực tế trong lớp học được xác định qua kiểm thử. Các tính năng này biến hệ thống từ một nguyên mẫu dễ hỏng thành một công cụ giảng dạy sẵn sàng cho việc sử dụng thực tế mà một giảng viên có thể tự tin vận hành trước 30+ sinh viên mà không cần hỗ trợ kỹ thuật.

---

### Màn hình người chơi — Nộp dự án (play.html, chế độ nộp dự án)

Tôi đã triển khai biểu mẫu nộp dự án với sáu nhóm phần: Quy mô dự án (với các ràng buộc mục tiêu tài trợ tự động khớp), Giá & Kênh bán hàng, Giá vốn hàng bán, Dự báo sản xuất, Chi phí vận hành hàng tháng, và Vốn & Cổ phần.

Sau khi xem xét phiên bản đầu tiên của trò chơi, tôi đã đề nghị Phúc, người xử lý logic nhập liệu của trò chơi, chia các đầu vào thành các nhóm phù hợp và thảo luận với cô ấy về các ràng buộc thích hợp cho từng trường nhập liệu và giải thích ngắn gọn của chúng mà tôi hiển thị trong một cửa sổ popup có thể được kích hoạt bằng cách nhấp vào nút "?".

Biểu mẫu xác thực ở phía người chơi trước khi nộp và cung cấp thông báo lỗi rõ ràng. Sau khi nộp, màn hình chuyển trực tiếp sang giao diện xây dựng bộ bài mà không cần tải lại trang, và người chơi không thể hoàn tác việc nộp.

---

### Màn hình người chơi — Xây dựng bộ bài (play.html, chế độ xây dựng bộ bài)

Tôi đã xây dựng giao diện xây dựng bộ bài cho phép người chơi chọn chính xác 22 lá bài hoạt động từ một lưới trực quan với màu sắc (đỏ cho Tấn công, xanh dương cho Phòng thủ, tím cho Vốn) và tối đa 3 lá bài phản ứng. Mỗi lá bài được hiển thị dưới dạng ô có thể nhấp, hiển thị tên, chi phí năng lượng và mô tả.

- Thêm bộ đếm lựa chọn hiển thị số lựa chọn hiện tại (ví dụ: 'Đã chọn: 15/22') để dễ theo dõi hơn.
- Thêm nút Tự động chọn bộ bài ngẫu nhiên để điền nhanh một lựa chọn hợp lệ mà người chơi có thể sửa đổi. Tính năng này từng phục vụ mục đích kiểm thử, vì chúng tôi có nhiều lá bài để chọn nhưng không có nhiều thời gian, và tôi đã quyết định giữ lại nó trong trường hợp người chơi muốn thử vận may.
- Nút Xác nhận bộ bài gửi lựa chọn lên API của Jin, và hành động không thể hoàn tác.

---

### Màn hình người chơi — Chế độ chơi (play.html, chế độ chơi)

Tôi đã triển khai màn hình chơi cốt lõi hiển thị:
- Chỉ số tiến trình tài trợ với phần trăm, bộ đếm năng lượng nạp lại mỗi giai đoạn, thanh hype và transparency, bốn màn hình chỉ số tài chính (Intrinsic, Valuation, ROI, Runway), banner sự kiện kịch bản hiện tại,
- Bộ bài 5 lá với tên, chi phí và mô tả cho mỗi lá bài, bảng danh sách nhà đầu tư hiển thị loại bot và số tiền đầu tư của mỗi bot, ba nút hành động (Chơi bài, Mulligan, Sẵn sàng), và phần lá bài phản ứng được kích hoạt khi đáp ứng điều kiện kích hoạt.

Ở cuối trang có danh sách tất cả các giao dịch bot với người chơi, được sử dụng cho kiểm thử và debug, và được giữ lại vì lý do kiểm duyệt.

---

### Modal trợ giúp

Ngoài nút "?" bên cạnh mỗi trường nhập liệu, người chơi còn có nút "sách" nổi, kích hoạt thanh bên hiển thị luật chơi. Nút này có sẵn trên mọi màn hình, đảm bảo người chơi hiểu trò chơi, nâng cao giá trị giáo dục.

---

### Ngôn ngữ thiết kế trực quan

Tôi đã thiết lập hệ thống thiết kế trực quan được sử dụng xuyên suốt ứng dụng: bảng màu tím và lavender, nền gradient, các ô bài bo góc với độ sâu bóng, phân cấp typography theo chủ đề khởi nghiệp, và điều chỉnh bố cục responsive cho màn hình tablet và di động. Thiết kế cố tình tránh thẩm mỹ trò chơi thông thường và sử dụng hình ảnh phù hợp với môi trường kinh doanh để củng cố bối cảnh giáo dục.

---

## Các nhiệm vụ đã hoàn thành

| Nhiệm vụ | Mô tả | Đầu vào | Đầu ra |
|---|---|---|---|
| THIẾT KẾ & TRIỂN KHAI host.html — Phần thiết lập phòng | Xây dựng bảng tạo phòng ban đầu với ô nhập tên phòng, bộ chọn số người chơi (2-10), và nút "Tạo phòng". Thêm chỉ báo trạng thái kết nối để hiển thị tình trạng backend. | Host nhập tên phòng, chọn số người chơi. | Biểu mẫu thiết lập được hiển thị với xác thực (tối thiểu 2, tối đa 10 người chơi). Nút kích hoạt POST đến /api/create_room. |
| THIẾT KẾ & TRIỂN KHAI host.html — Quản lý link tham gia | Xây dựng danh sách link động hiển thị sau khi tạo phòng. Mỗi người chơi có một link tham gia độc nhất. Thêm nút "Sao chép tất cả" để sao chép tất cả link vào clipboard bằng một nhấp. | ID phòng và chỉ số người chơi từ phản hồi backend. | Danh sách link có thể nhấp/sao chép được hiển thị. Clipboard API sao chép văn bản được định dạng (Người chơi 1 - URL, Người chơi 2 - URL...). |
| THIẾT KẾ & TRIỂN KHAI host.html — Bảng tiến trình trò chơi | Xây dựng bảng hiển thị giai đoạn hiện tại, giai đoạn tối đa, số người chơi đã tham gia, và huy hiệu trạng thái trò chơi (Chờ/Đang chọn bộ bài/Đang chơi/Đã kết thúc). | Dữ liệu từ endpoint /api/rooms/{room_id}. | Bộ đếm cập nhật trực tiếp và huy hiệu trạng thái với mã màu (xanh = đang hoạt động, đỏ = đã kết thúc). |
| THIẾT KẾ & TRIỂN KHAI host.html — Dropdown lưu trữ giai đoạn | Xây dựng dropdown lựa chọn được điền bằng các giai đoạn đã hoàn thành. Mỗi tùy chọn hiển thị số giai đoạn và ngày. Kết nối với trình xem chi tiết. | Mảng chi tiết giai đoạn từ phản hồi backend. | Dropdown với các tùy chọn như "Giai đoạn 1 (2025-01-15)". Việc chọn kích hoạt hiển thị chi tiết. |
| THIẾT KẾ & TRIỂN KHAI host.html — Modal chi tiết giai đoạn | Xây dựng chế độ xem chi tiết hiển thị bảng dòng tiền (theo người chơi) và bảng giao dịch bot. Định dạng tiền tệ với hỗ trợ locale. Mã màu đầu tư (xanh) so với rút tiền (đỏ). | Hành động bot tổng hợp và dữ liệu dòng tiền người chơi từ backend. | Cửa sổ modal với hai bảng. Dòng tiền hiển thị tiền mặt bắt đầu/kết thúc. Bảng bot chỉ hiển thị các giao dịch tổng hợp. |
| THIẾT KẾ & TRIỂN KHAI host.html — Bảng xếp hạng tổng thể | Xây dựng bảng xếp hạng hiển thị tất cả người chơi được sắp xếp theo điểm. Bao gồm % tài trợ, hype, transparency, điểm và huy hiệu trạng thái (Đang hoạt động/Đã hoàn thành/Phá sản). | Mảng người chơi từ /api/rooms/{room_id}. | Bảng xếp hạng được sắp xếp với các chỉ báo trạng thái trực quan và thanh tiến trình tài trợ. |
| THIẾT KẾ & TRIỂN KHAI host.html — Bảng xếp hạng theo quy mô | Xây dựng ba bảng xếp hạng riêng biệt (quy mô Nhỏ/Trung bình/Lớn). Mỗi bảng chỉ hiển thị người chơi của quy mô đó, được sắp xếp theo điểm. | Mảng người chơi với logic phát hiện quy mô (sử dụng max_phase hoặc trường quy mô rõ ràng). | Ba phần có thể thu gọn/mở rộng. Các quy mô trống hiển thị placeholder "Không có người chơi". |
| THIẾT KẾ & TRIỂN KHAI host.html — Trình xem nhật ký sự kiện | Xây dựng khu vực nhật ký có thể cuộn hiển thị các sự kiện trò chơi theo thứ tự thời gian đảo ngược (mới nhất ở trên cùng). Giới hạn ở 40-50 mục cuối. | Mảng nhật ký từ phản hồi polling backend. | Các mục nhật ký được tạo kiểu với dấu thời gian khi có. Tự động cuộn lên đầu khi có mục mới. |
| THIẾT KẾ & TRIỂN KHAI host.html — Các nút điều khiển | Xây dựng các nút Chạy giai đoạn, Kết thúc trò chơi và Đặt lại trò chơi. Vô hiệu hóa phù hợp dựa trên trạng thái trò chơi (ví dụ: Chạy giai đoạn bị vô hiệu hóa nếu không phải tất cả người chơi đã sẵn sàng). | Trạng thái trò chơi từ polling backend. | Các nút thay đổi trạng thái bật/tắt động. Yêu cầu POST đến các endpoint tương ứng khi nhấp. |
| THIẾT KẾ & TRIỂN KHAI play.html — Biểu mẫu nộp dự án (6 phần) | Xây dựng biểu mẫu nộp đầy đủ với các phần: Quy mô, Giá & Kênh bán, COGS, Dự báo sản xuất, OPEX hàng tháng, Cơ cấu vốn. | Đầu vào của người chơi cho 15+ trường tài chính. Các ràng buộc được áp dụng (giá trị min/max theo trường). | Biểu mẫu với xác thực nội tuyến, tooltip trợ giúp (biểu tượng ?) và trạng thái focus mượt mà. |
| THIẾT KẾ & TRIỂN KHAI play.html — Logic quy mô với mục tiêu tài trợ | Triển khai bộ chọn quy mô (S/M/L) tự động đề xuất phạm vi tài trợ mục tiêu. Cho phép ghi đè thủ công với xác thực theo ràng buộc quy mô. | Lựa chọn quy mô (S/M/L). Đầu vào tài trợ mục tiêu thủ công. | Trường tài trợ mục tiêu cập nhật placeholder dựa trên quy mô. Xác thực ngăn các giá trị ngoài phạm vi. |
| THIẾT KẾ & TRIỂN KHAI play.html — Modal tooltip trợ giúp | Xây dựng hệ thống modal giải thích chỉ số tài chính. Thêm biểu tượng "?" bên cạnh mỗi phần. Viết giải thích ngôn ngữ đơn giản cho Giá trị nội tại, Độ hợp lý định giá, Chuẩn ROI, Runway và tất cả các trường nhập liệu. | Nhấp vào biểu tượng "?" kích hoạt mở modal. Nội dung tự viết dựa trên kiến thức kinh doanh/tài chính. | Modal popup với tiêu đề, giải thích từng trường, đơn vị và ràng buộc. Nhấp bên ngoài hoặc nút đóng để đóng. |
| THIẾT KẾ & TRIỂN KHAI play.html — Nộp biểu mẫu & Chuyển màn hình | Triển khai nộp biểu mẫu đến /api/submit_project. Khi thành công, ẩn bảng nộp và hiển thị giao diện xây dựng bộ bài. Khi thất bại, hiển thị thông báo lỗi mà không mất dữ liệu đã nhập. | Dữ liệu biểu mẫu thu thập qua DOM. Yêu cầu POST đến backend. | Chuyển bảng mượt mà. Thông báo thành công được hiển thị. Thông báo lỗi hiển thị nội tuyến. |
| THIẾT KẾ & TRIỂN KHAI play.html — Lưới bài xây dựng bộ bài | Xây dựng hiển thị lưới cho thấy tất cả 42 lá bài hoạt động (3 cột trên di động, 4 trên máy tính). Mỗi lá bài hiển thị tên, chi phí, mô tả và chỉ báo nhóm trực quan (viền mã màu). | Mảng ActiveCardsMaster được tải từ /api/card_lists. | Lưới lá bài có thể cuộn. Lá bài được tạo kiểu với màu phù hợp theo nhóm (đỏ tấn công, xanh phòng thủ, tím vốn). |
| THIẾT KẾ & TRIỂN KHAI play.html — Logic lựa chọn bộ bài | Triển khai chọn/bỏ chọn bằng nhấp. Theo dõi các chỉ số đã chọn bằng JavaScript Set. Bắt buộc chính xác 22 lá bài hoạt động (chặn lựa chọn thứ 23). Hiển thị bộ đếm thời gian thực. | Sự kiện nhấp của người chơi trên các phần tử lá bài. | Bộ đếm cập nhật trực tiếp (ví dụ: "Đã chọn: 12/22"). Không thể vượt quá 22. Lá bài đã chọn được làm nổi bật trực quan. |
| THIẾT KẾ & TRIỂN KHAI play.html — Lá bài phản ứng | Xây dựng lưới riêng biệt cho 10 lá bài phản ứng. Cho phép tối đa 3 lựa chọn. Hiển thị tên, mô tả, điều kiện kích hoạt (nếu hiển thị). | Mảng ReactionCardsMaster từ /api/card_lists. | Lưới phản ứng với logic lựa chọn tương tự. Bộ đếm hiển thị "Đã chọn: 0/3". |
| THIẾT KẾ & TRIỂN KHAI play.html — Nút tự động chọn | Triển khai nút "Tự động chọn bộ bài ngẫu nhiên" chọn ngẫu nhiên 22 lá bài hoạt động và 0-3 lá bài phản ứng. Cập nhật UI và bộ đếm mà không tự động nộp. | Tạo chỉ số ngẫu nhiên sử dụng Math.random(). | UI bộ bài cập nhật ngay lập tức hiển thị lựa chọn ngẫu nhiên mới. Người chơi vẫn có thể chỉnh sửa trước khi xác nhận. |
| THIẾT KẾ & TRIỂN KHAI play.html — Nộp bộ bài | Triển khai nút xác nhận thu thập các chỉ số đã chọn và gửi POST đến /api/submit_deck. Khi thành công, ẩn giao diện xây dựng bộ bài và bắt đầu polling trò chơi. | SelectedActive (Set) và SelectedReaction (Set). Chuyển đổi thành mảng. | Yêu cầu POST được gửi. Thông báo thành công. Chuyển sang chế độ polling trò chơi. |
| THIẾT KẾ & TRIỂN KHAI play.html — Thống kê tiêu đề chế độ chơi | Xây dựng tiêu đề hiển thị tên người chơi, tỷ lệ tài trợ, năng lượng còn lại và giai đoạn hiện tại. Thêm thanh tiến trình tài trợ với gradient fill. | Dữ liệu thời gian thực từ polling /api/player_state. | Thống kê cập nhật trực tiếp. Thanh tài trợ animate thay đổi chiều rộng. |
| THIẾT KẾ & TRIỂN KHAI play.html — Thanh Hype & Transparency | Xây dựng hai thanh đo dọc hoặc ngang hiển thị giá trị Hype (hồng) và Transparency (xanh lá) từ 0-100. Thêm hiển thị văn bản phần trăm. | Giá trị hype và transparency từ trạng thái người chơi. | Thanh tiến trình mã màu với chuyển đổi chiều rộng mượt mà. |
| THIẾT KẾ & TRIỂN KHAI play.html — Bảng chỉ số | Xây dựng bảng nhỏ hiển thị Giá trị nội tại, Độ hợp lý định giá, Chuẩn ROI và tháng Runway. Định dạng số đến 1 chữ số thập phân. | Đối tượng metrics từ phản hồi API trạng thái người chơi. | Hiển thị lưới nhỏ gọn của bốn chỉ số chính. |
| THIẾT KẾ & TRIỂN KHAI play.html — Bài trên tay | Xây dựng lưới hiển thị 5 lá bài hoạt động từ tay người chơi. Mỗi lá bài hiển thị tên, chi phí, mô tả và màu nhóm. Nhấp để chọn một lá bài (làm nổi bật trực quan). | Mảng current_hand từ trạng thái người chơi. | Lưới lá bài tương tác. Lá bài đã chọn có nền màu hồng nổi bật. |
| THIẾT KẾ & TRIỂN KHAI play.html — Các nút hành động | Xây dựng nút Chơi bài (gửi chỉ số lá bài đã chọn đến backend), Mulligan (tốn 1 năng lượng, rút lại tay), và Sẵn sàng (báo hiệu hoàn thành giai đoạn). | Sự kiện nhấp nút. Trạng thái năng lượng và mulligan_used từ backend. | Nút bị vô hiệu hóa khi hành động không khả dụng (ví dụ: Chơi bài bị vô hiệu hóa nếu không có lá bài được chọn hoặc không đủ năng lượng). |
| THIẾT KẾ & TRIỂN KHAI play.html — Banner kịch bản | Xây dựng banner hiển thị tên sự kiện/kịch bản ngẫu nhiên hiện tại. Cập nhật mỗi giai đoạn. | Trường last_scenario từ trạng thái người chơi. | Banner màu với biểu tượng sự kiện và tên kịch bản. |
| THIẾT KẾ & TRIỂN KHAI play.html — Kích hoạt phản ứng | Xây dựng bảng động xuất hiện khi có lá bài phản ứng. Mỗi phản ứng hiển thị dưới dạng nút có thể nhấp. Gửi POST đến /api/use_reaction khi nhấp. | Mảng triggers từ trạng thái người chơi (available_reactions). | Bảng chỉ xuất hiện khi có trigger. Các nút biến mất sau khi sử dụng (bị xóa khỏi mảng). |
| THIẾT KẾ & TRIỂN KHAI play.html — Danh sách nhà đầu tư | Xây dựng danh sách hiển thị các bot đã đầu tư vào dự án của người chơi. Mỗi mục hiển thị loại bot và số tiền đã đầu tư. | Mảng investors từ trạng thái người chơi (được lọc cho số tiền > 0). | Danh sách đơn giản với biểu tượng cá voi, loại bot và tiền tệ được định dạng. |
| THIẾT KẾ & TRIỂN KHAI play.html — Bảng kết thúc trò chơi | Xây dựng modal toàn màn hình hiển thị điểm cuối, chỉ số cuối (% tài trợ, hype, transparency, quy mô), và bảng xếp hạng đối thủ được sắp xếp theo điểm. | Trạng thái trò chơi cuối từ polling sau khi game_ended = true. | Bảng kết thúc với hiển thị điểm lớn. Bảng xếp hạng với làm nổi bật hàng cho người chơi hiện tại. |
| THIẾT KẾ & TRIỂN KHAI CẢ HAI — Thanh bên luật chơi | Xây dựng thanh bên trượt ra (cạnh phải) với luật chơi đầy đủ và mẹo nhanh. Thêm nút biểu tượng sách nổi để mở/đóng. Triển khai nhấp overlay và phím ESC để đóng. | Nội dung hướng dẫn trò chơi tự viết dựa trên tài liệu dự án. | Thanh bên trượt vào từ bên phải. Overlay làm tối nền. Responsive trên di động (max-width 90vw). |
| THIẾT KẾ & TRIỂN KHAI CẢ HAI — Bố cục Responsive | Triển khai CSS media queries cho tablet (768px) và di động (480px). Xếp chồng lưới, giảm padding, điều chỉnh kích thước font, và chuyển đổi bố cục nhiều cột thành một cột. | Các lớp responsive Tailwind CSS + media queries tùy chỉnh. | Bố cục thích ứng linh hoạt với mọi kích thước màn hình. Không cuộn ngang trên di động. |
| THIẾT KẾ & TRIỂN KHAI CẢ HAI — Chỉ báo trạng thái kết nối | Xây dựng banner hiển thị trạng thái kết nối backend (xanh = đã kết nối, đỏ = đã ngắt kết nối, vàng = đang kết nối). Cập nhật dựa trên kiểm tra sức khỏe fetch. | Fetch định kỳ đến /api/health. | Thanh trạng thái với emoji và văn bản thông báo. Tự động thử lại khi thất bại. |
| KIỂM THỬ — Kiểm thử đơn vị Frontend — Xác thực biểu mẫu | Kiểm thử tất cả 15+ trường nhập liệu trong biểu mẫu nộp dự án. Xác minh ràng buộc min/max, xác thực kiểu dữ liệu và các trường hợp biên (trường trống, giá trị ngoài phạm vi, số âm). | Các trường hợp kiểm thử thủ công: giá trị tối thiểu, tối đa, giá trị biên (0, 100), đầu vào văn bản không hợp lệ. | Tất cả trường từ chối đầu vào không hợp lệ. Thông báo lỗi hiển thị nội tuyến. Biểu mẫu không thể nộp với dữ liệu không hợp lệ. |
| KIỂM THỬ — Kiểm thử đơn vị Frontend — Ràng buộc xây dựng bộ bài | Kiểm thử giới hạn lựa chọn: không thể vượt quá 22 lá bài hoạt động, không thể vượt quá 3 lá bài phản ứng. Kiểm thử bỏ chọn giảm bộ đếm. Kiểm thử nút nộp bị vô hiệu hóa cho đến khi chọn đúng 22 lá. | Nhấp 23 lá bài hoạt động. Nhấp 4 lá bài phản ứng. Bỏ chọn xuống còn 21 lá bài hoạt động. | Cảnh báo kích hoạt tại giới hạn. Nút nộp chỉ được bật khi đủ 22 lá bài hoạt động. |
| KIỂM THỬ — Kiểm thử tích hợp Frontend — Mô phỏng API | Mô phỏng phản hồi backend cho mỗi endpoint API để kiểm thử hành vi frontend mà không có backend trực tiếp. Kiểm thử các đường thành công (200 OK) và lỗi (400, 404, 500). | Phản hồi fetch mô phỏng sử dụng logic điều kiện hoặc điều chỉnh mạng trong DevTools trình duyệt. | Frontend xử lý cả thành công (cập nhật UI, chuyển màn hình) và lỗi (cảnh báo, hiển thị dự phòng) một cách linh hoạt. |
| KIỂM THỬ — Kiểm thử tích hợp Frontend — Polling & Cập nhật thời gian thực | Kiểm thử cơ chế polling 2 giây. Xác minh UI chỉ cập nhật khi chữ ký dữ liệu thay đổi (không re-render không cần thiết). Kiểm thử polling tiếp tục sau lỗi mạng. | Mở trình duyệt với hai tab (người chơi + host). Mô phỏng hành động trong tab người chơi. Xác minh tab host cập nhật trong vòng 2-3 giây. | Cả hai màn hình đồng bộ. Không có UI bị giật khi dữ liệu không thay đổi. Polling tiếp tục sau khi mạng phục hồi. |
| KIỂM THỬ — Kiểm thử tích hợp Frontend — Giới hạn năng lượng & Mulligan | Kiểm thử tiêu thụ năng lượng: chơi bài giảm năng lượng theo chi phí bài. Kiểm thử Mulligan giảm năng lượng 1. Kiểm thử không thể Mulligan hai lần mỗi giai đoạn. Kiểm thử không thể chơi bài với năng lượng không đủ. | Chơi bài chi phí 1, 2, 3. Thử Mulligan khi năng lượng về 0. Thử Mulligan lần hai trong cùng giai đoạn. | Bộ đếm năng lượng giảm đúng. Nút Mulligan bị vô hiệu hóa sau lần dùng đầu. Nút Chơi bị vô hiệu hóa khi năng lượng < chi phí bài. |
| KIỂM THỬ — Kiểm thử tích hợp Frontend — Kích hoạt lá bài phản ứng | Kiểm thử lá bài phản ứng xuất hiện khi điều kiện kích hoạt được đáp ứng (ví dụ: transparency < 30, hype > 80, runway < 3). Kiểm thử lá bài phản ứng biến mất sau khi sử dụng. Xác minh chi phí năng lượng (3) bị trừ. | Mô phỏng transparency thấp qua backend hoặc endpoint kiểm thử. Nhấp nút phản ứng. Kiểm tra bảng sau khi sử dụng. | Bảng phản ứng xuất hiện. Nhấp kích hoạt POST và xóa nút. Năng lượng giảm 3. |
| KIỂM THỬ — Kiểm thử tích hợp Frontend — Luồng giai đoạn | Kiểm thử chu kỳ giai đoạn đầy đủ: người chơi sẵn sàng → host chạy giai đoạn → người chơi thấy tay mới, kịch bản mới, năng lượng đặt lại (3), trạng thái sẵn sàng đặt lại. Kiểm thử qua 3+ giai đoạn. | Người chơi nhấp Sẵn sàng. Host nhấp Chạy giai đoạn. Lặp lại cho nhiều giai đoạn. | Sau mỗi giai đoạn: tay cập nhật, kịch bản thay đổi, năng lượng đặt lại về 3, trạng thái sẵn sàng đặt lại về false. |
| KIỂM THỬ — Kiểm thử đầu cuối — Mô phỏng trò chơi đầy đủ (2-4 người chơi) | Mô phỏng một trò chơi hoàn chỉnh từ tạo phòng đến xếp hạng cuối cùng. Kiểm thử: tạo phòng → 2 người chơi nộp dự án → cả hai nộp bộ bài → host chạy giai đoạn 1-7 → trò chơi kết thúc → hiển thị xếp hạng cuối cùng. | 2-4 tab/cửa sổ trình duyệt (một host, 2-4 người chơi). Hoàn thành tất cả các bước thủ công. | Trò chơi hoàn thành mà không có sự cố. Xếp hạng cuối cùng hiển thị điểm chính xác. Tất cả người chơi thấy bảng kết thúc. |
| KIỂM THỬ — Kiểm thử đầu cuối — Trường hợp biên & Phục hồi lỗi | Kiểm thử: người chơi tham gia sau khi trò chơi bắt đầu (không được phép). Host nhấp Chạy giai đoạn trước khi tất cả người chơi sẵn sàng (hiển thị lỗi). Người chơi ngắt kết nối giữa trò chơi (polling thử lại). | Mô phỏng tham gia muộn. Thử chạy với trạng thái sẵn sàng chưa đầy đủ. Tắt mạng trong DevTools giữa chừng polling. | Thông báo lỗi thích hợp được hiển thị. Tham gia muộn bị từ chối. Polling thử lại tự động sau khi mạng khôi phục. |
| KIỂM THỬ — Kiểm thử trình duyệt & Thiết bị | Kiểm thử trên Chrome, Firefox, Safari (máy tính). Kiểm thử trên iPhone Safari và Android Chrome (di động). Xác minh bố cục responsive, tương tác cảm ứng (chạm để chọn bài) và kích thước nút. | BrowserStack hoặc thiết bị vật lý. Kiểm thử thủ công tất cả luồng chính. | Giao diện và chức năng nhất quán trên các trình duyệt. Mục tiêu cảm ứng ít nhất 44x44px trên di động. |
| KIỂM THỬ — Kiểm thử hiệu suất — Trạng thái trò chơi lớn | Kiểm thử với 10 người chơi (tối đa) và 200 bot. Xác minh polling (khoảng cách 2 giây) không gây lag UI. Xác minh lịch sử giai đoạn với 9 giai đoạn × 200 hành động bot vẫn responsive. | Tạo phòng với 10 người chơi (mô phỏng qua nhiều tab). Chạy trò chơi đến giai đoạn 9. Theo dõi tab hiệu suất DevTools trình duyệt. | UI vẫn responsive (<100ms frame time). Modal chi tiết giai đoạn tải trong vòng 1 giây. Không bị rò bộ nhớ. |
| KIỂM THỬ — Chuẩn bị demo — Diễn tập kịch bản | Chuẩn bị kịch bản demo 5 phút bao gồm: tạo phòng → nộp dự án người chơi → chọn bộ bài → gameplay giai đoạn 1 → host chạy giai đoạn → giai đoạn 2 với kích hoạt phản ứng → xếp hạng cuối cùng. | Kịch bản viết với ước tính thời gian. Các lần diễn tập. | Trình diễn demo mượt mà, tự tin. Không có khoảng dừng hay do dự. |
| KIỂM THỬ — Chuẩn bị demo — Xác minh sửa lỗi | Trước demo, kiểm thử lại tất cả các đường quan trọng trước đây đã thất bại. Xác minh: xác thực biểu mẫu, giới hạn lựa chọn bộ bài, hệ thống năng lượng, kích hoạt phản ứng, chuyển giai đoạn, chấm điểm cuối. | Danh sách kiểm tra regression. Thực hiện thủ công từng trường hợp kiểm thử. | Không còn lỗi nghiêm trọng. Tất cả tính năng trước đây bị hỏng đều hoạt động. |
| KIỂM THỬ — Hoàn thiện Frontend — Regression trực quan | So sánh UI hiện tại với các mockup thiết kế. Xác minh khoảng cách, màu sắc, font chữ, viền, bóng và trạng thái hover khớp với hệ thống thiết kế. | So sánh trực quan cạnh nhau (trình duyệt so với Figma/ảnh chụp màn hình). | Căn chỉnh pixel hoàn hảo hoặc gần hoàn hảo. Tạo kiểu nhất quán trên tất cả các thành phần. |

---

## Các tệp, tính năng và thành phần đã đóng góp

### Templates

- **templates/host.html**: bảng điều khiển host hoàn chỉnh, được tác giả hoàn toàn bởi tôi. Bao gồm cấu trúc HTML, CSS nhúng và JavaScript cho các lệnh gọi API, polling và cập nhật DOM.
- **templates/play.html**: giao diện người chơi hoàn chỉnh bao gồm tất cả ba chế độ xem (nộp, xây dựng bộ bài, gameplay), được tác giả hoàn toàn bởi tôi. Bao gồm cấu trúc HTML, CSS nhúng và JavaScript cho các lệnh gọi API, polling, tương tác bài và chuyển đổi chế độ xem.

### Tài sản thiết kế

- Bảng màu (tím/lavender/teal), hệ thống typography, thiết kế ô bài và nền gradient được tạo bởi tôi và áp dụng nhất quán trên cả hai tệp template.
- Nội dung modal trợ giúp (giải thích chỉ số bằng ngôn ngữ đơn giản) được viết bởi tôi.

---

## Bằng chứng đóng góp

### Bằng chứng code

- Hai tệp html host.html và play.html chủ yếu được code bởi tôi, trong khi Jin, người có vai trò kết nối giữa frontend và backend, thỉnh thoảng đăng nhập để đảm bảo rằng tất cả các polling đang gọi đúng API trong backend.
- Toàn bộ lịch sử commit có thể được xem trong git của nhóm.

---

## Tài liệu đề xuất

- Bảng công việc cá nhân Phần E trong đề xuất giữa kỳ ghi lại năm nhiệm vụ của tôi: thiết kế màn hình host, màn hình nộp dự án/xây dựng bộ bài, màn hình gameplay, modal giải thích và tính hấp dẫn/responsive của giao diện. Những điều này khớp với các tính năng đã triển khai.

---

## Đóng góp này kết nối với sản phẩm cuối như thế nào

- Nếu không có frontend của tôi, trò chơi không thể được chơi. Logic backend (chỉ số của Phúc, bot của Khánh, API của Jin) tạo ra các đầu ra chính xác nhưng không có cách nào nhận đầu vào của người chơi hoặc hiển thị kết quả mà không có HTML và JavaScript của tôi.
- Các route API của Jin được gọi độc quyền từ các trình xử lý sự kiện JavaScript và hàm polling của tôi. API được thiết kế phối hợp với tôi để phù hợp với nhu cầu của frontend.
- Nội dung bài của Minh (tên, mô tả, chi phí, loại) được hiển thị trong giao diện xây dựng bộ bài và chế độ xem tay bài khi chơi. Người chơi trải nghiệm thiết kế bài của Minh thông qua UI của tôi.
- Các chỉ số tài chính của Phúc (nội tại, định giá, ROI, runway) được hiển thị trong các bảng chỉ số của tôi và giải thích qua các modal trợ giúp của tôi. Giải thích của tôi là giao diện chính cho nội dung giáo dục của trò chơi.
- Các quyết định đầu tư bot của Khánh được hiển thị trong bảng danh sách nhà đầu tư của tôi, cung cấp phản hồi thời gian thực cho người chơi về loại nhà đầu tư nào đang hỗ trợ dự án của họ.

---

## Những gì tôi đã học được cá nhân

### Về các dự án khởi nghiệp và động lực gọi vốn cộng đồng

Mặc dù có những hạn chế về thời gian và năng lực, nhóm chúng tôi đã cố gắng làm cho trò chơi trở nên thực tế nhất có thể trong khi vẫn giữ được giá trị giải trí và quan trọng nhất là tác động giáo dục. Thông qua quá trình này, tôi đã có được những hiểu biết thực tế về việc chuẩn bị khởi nghiệp:

- **Kiến thức tài chính cơ bản** – logic đằng sau các chỉ số chính, quy mô giá cả và số lượng sản phẩm thực tế, các nguồn tài trợ và chi phí liên quan của chúng.
- **Hành vi nhà đầu tư** – các loại nhà đầu tư khác nhau và mô hình ra quyết định tổng quát của họ.
- **Các kịch bản thực tế** – hiểu các chỉ báo sức khỏe dự án từ Phúc, học các chiến lược phản công cho các kịch bản khủng hoảng khác nhau từ Minh, và phân tích tâm lý nhà đầu tư từ Khánh.

Làm việc với frontend buộc tôi phải hiểu sâu mọi yếu tố tôi đặt trên màn hình. Ngoài bản thân trò chơi, giờ đây tôi hiểu rõ hơn nhiều về cách các nền tảng gọi vốn cộng đồng như Kickstarter hay Crowdspace hoạt động, kiến thức tôi có thể áp dụng nếu tôi tham gia các nền tảng như vậy trong tương lai.

### Về thiết kế UX cho thông tin phức tạp

FUN(D) RAISING hiển thị một lượng lớn thông tin tài chính đồng thời: tiến trình tài trợ, năng lượng, hype, transparency, bốn điểm chỉ số, năm lá bài trên tay, danh sách nhà đầu tư và các nút hành động. Tôi đã học được rằng việc trình bày thông tin phức tạp một cách rõ ràng đòi hỏi thiết kế phân cấp cẩn thận để làm cho mọi thứ minh bạch và dễ hiểu, quyết định thông tin nào quan trọng nhất và cho nó sự nổi bật trực quan nhất. Ví dụ, tỷ lệ phần trăm tiến trình tài trợ là con số quan trọng nhất trên màn hình gameplay, vì vậy nó xuất hiện lớn nhất và ở trên cùng; hoặc một dự án cần nhiều đầu vào từ các module khác nhau, vì vậy việc chia chúng thành các phần sẽ không chỉ dễ theo dõi hơn mà còn giúp thống nhất logic của người chơi.

### Về phát triển Frontend và sử dụng AI

Là một sinh viên tài chính chưa từng phải code hay thực sự học về lập trình ngoài mức bề mặt, tôi đã học cách tận dụng sức mạnh của AI để phục vụ mình. Ở giai đoạn đầu tiên, tôi yêu cầu DeepSeek cung cấp toàn bộ code cho phiên bản đơn giản nhất bằng cách nhập luật trò chơi, đầu vào dự án và các chỉ số cần thiết. Cụ thể, tôi yêu cầu nó cung cấp cho tôi phiên bản "demo", có nghĩa là code sẽ điền vào các khoảng trống được cho là sẽ được polling từ backend bằng dữ liệu cứng, để tôi có thể thực sự thấy tất cả các trang với logic thiết kế tôi muốn áp dụng mà không cần phải chạy backend.

Sau đó, tôi sử dụng VS Code để chạy code và tạo phiên bản demo trực tiếp, nơi tôi có thể thực hiện các thay đổi trên code và màn hình sẽ cập nhật gần như theo thời gian thực. VS Code có một mô hình AI tích hợp, mà tôi sử dụng để điều chỉnh mọi thứ tôi muốn thêm: thay đổi chủ đề của trò chơi, chia trang nhập dự án thành các phần, nút "?"... Điều này giúp tôi sửa code chỉ ở nơi tôi muốn, và việc nhập toàn bộ code là không cần thiết. Tuy nhiên, có giới hạn về số lượng token miễn phí có thể sử dụng mỗi tháng, vì vậy tôi nhanh chóng hết và phải quay lại DeepSeek.

Vì tôi không có kinh nghiệm, tôi không biết nơi nào cần điều chỉnh trong code. Do đó mỗi lần tôi muốn thực hiện thay đổi, tôi phải dán toàn bộ tệp vào DeepSeek. Tuy nhiên, khi code quá dài, mô hình AI bắt đầu cố tình bỏ qua các dòng code, dẫn đến nhiều hàm nhỏ bị cắt. Để khắc phục điều này, tôi đã học cách đọc code và có ý tưởng về nơi cần sửa, và chỉ yêu cầu DeepSeek sửa module đó.

Đối với các lỗi tôi không thể giải quyết, tôi dán toàn bộ tệp vào Claude, mạnh hơn cho code nhưng tiêu tốn nhiều token hơn, và mô hình sẽ cung cấp cho tôi phiên bản đã được sửa. Đôi khi phiên bản đã sửa thất bại, tôi sẽ đến gặp cố vấn và tìm ra vấn đề cũng như giải pháp.

| Giai đoạn | Công cụ | Mục đích |
|---|---|---|
| Tạo MVP | DeepSeek | Yêu cầu code đầy đủ cho phiên bản demo với dữ liệu backend cứng – cho phép tôi hình dung các trang và logic thiết kế mà không cần chạy máy chủ backend |
| Lặp lại trực tiếp | VS Code + Copilot | Sử dụng xem trước trực tiếp để thấy các thay đổi cập nhật theo thời gian thực; áp dụng AI để điều chỉnh chủ đề, chia phần đầu vào, thêm nút trợ giúp, v.v. |
| Sửa lỗi mục tiêu | DeepSeek | Sau khi hết giới hạn token miễn phí của Copilot, tôi đã học đọc code đủ tốt để xác định nơi cần thay đổi – sau đó chỉ dán các module liên quan thay vì toàn bộ tệp |
| Giải quyết lỗi | Claude | Đối với các lỗi tôi không thể giải quyết, tôi dán toàn bộ code vào Claude (mạnh hơn cho code, nhưng tốn nhiều token). Khi các sửa lỗi vẫn thất bại, tôi tham khảo ý kiến người cố vấn để chẩn đoán nguyên nhân gốc rễ |

**Bài học chính: AI là một trợ lý mạnh mẽ, nhưng việc dán mù quáng toàn bộ tệp dẫn đến các hàm bị bỏ sót và logic bị hỏng khi code vượt quá giới hạn context. Phát triển kiến thức code cơ bản — ngay cả khi không phải kỹ sư — cải thiện đáng kể chất lượng cộng tác với AI.**

### Về cộng tác nhóm trong các dự án liên chức năng

Nhóm chúng tôi có các kỹ năng đa dạng: một số thành viên xử lý logic backend, những người khác thiết kế các mô hình tài chính, trong khi tôi tập trung vào frontend và UX. Điều này đã dạy tôi:

- **Dịch thuật là một kỹ năng**: giao tiếp các khái niệm tài chính với người suy nghĩ bằng code (và ngược lại) đòi hỏi nỗ lực có chủ đích. Không phải ai cũng có cùng từ vựng.
- **Hình dung các phụ thuộc**: tôi đã học cách lập bản đồ các phần tử frontend nào phụ thuộc vào đầu ra backend nào, giúp nhóm tránh các nút thắt tích hợp.
- **Căn chỉnh không đồng bộ**: chúng tôi đã sử dụng tài liệu chia sẻ để theo dõi các quyết định thiết kế, đảm bảo mọi người đồng bộ mặc dù có giờ làm việc khác nhau.

**Bài học có giá trị nhất: khoảng cách kỹ thuật có thể được thu hẹp, nhưng khoảng cách giao tiếp làm chìm đắm dự án.**

### Về quản lý rủi ro và kiểm soát phạm vi

Với các ràng buộc của chúng tôi (thời gian, năng lực kỹ thuật, quy mô nhóm), chúng tôi liên tục đối mặt với sự đánh đổi giữa tham vọng và thực hiện. Tôi đã học:

- **Ưu tiên tính năng**: không phải mọi ý tưởng hay đều thuộc về MVP. Chúng tôi đã loại bỏ một số cơ chế thú vị nhưng không thiết yếu để tập trung vào các mục tiêu giáo dục cốt lõi.
- **Nguyên mẫu thất bại nhanh**: trước khi cam kết với các tính năng phức tạp, chúng tôi đã xây dựng các nguyên mẫu giấy nhanh hoặc demo cứng để kiểm thử xem chúng có thực sự cải thiện gameplay không.

---

## Những thách thức gặp phải và cách tôi xử lý

### Thách thức 1: Cơ sở hạ tầng hiện tại không thể xử lý lượng thông tin cần hiển thị trên Frontend

Tôi muốn màn hình host hiển thị một nhật ký sự kiện toàn diện ghi lại hành động của host, người chơi và bot đồng thời. Tuy nhiên, thành viên backend của tôi thông báo rằng cơ sở hạ tầng hiện tại của chúng tôi không thể hỗ trợ khối lượng dữ liệu thời gian thực này, đặc biệt khi số lượng người chơi được kết nối vượt quá 10.

**Giải pháp:** Chúng tôi đã đạt được điểm cân bằng thực tế thông qua thảo luận nhóm:
- Nhật ký sự kiện làm mới mỗi giai đoạn thay vì tích lũy vô thời hạn.
- Chỉ ghi lại hành động bot, giảm overhead bộ nhớ.
- Hành động của người chơi và host vẫn được xử lý nhưng không được ghi lại liên tục.

Sự đánh đổi này bảo tồn giá trị giáo dục của nhật ký trong khi giữ cho hệ thống ổn định dưới tải.

### Thách thức 2: Hiển thị các nút debug trên host

Trong giai đoạn phát triển đầu, màn hình host có bốn nút thay vì ba nút cuối. Ngoài "Bắt đầu giai đoạn tiếp theo", "Kết thúc trò chơi" và "Đặt lại trò chơi", còn có thêm nút "Đặt lại giai đoạn". Chức năng của nó là khởi động lại giai đoạn hiện tại (ví dụ: xóa tất cả các lựa chọn của người chơi và hành động bot trong Giai đoạn 5, cho phép mọi người làm lại quyết định của họ). Điều này hữu ích trong quá trình kiểm thử để hoàn tác các sai lầm bất cẩn và quan sát kỹ luồng gameplay. Tuy nhiên, tính năng này có chi phí:
- Tăng khối lượng công việc cho các nhà phát triển backend.
- Tạo ra sự gián đoạn và chậm chạp hệ thống do độ phức tạp của việc quay lại trạng thái.

**Giải pháp:** Tôi đã quyết định xóa hoàn toàn nút "Đặt lại giai đoạn". Điều này:
- Giảm bớt gánh nặng đáng kể cho nhóm backend.
- Cải thiện hiệu suất hệ thống tổng thể.
- Làm cho trò chơi thực tế hơn: trong các quyết định thực tế, không có nút hoàn tác.

### Thách thức 3: Thay đổi cấu trúc phản hồi API làm hỏng Frontend

Trong quá trình phát triển tích cực, các thành viên nhóm đôi khi thay đổi cấu trúc phản hồi API (đổi tên trường, thêm mức lồng nhau, chuyển đổi mảng thành từ điển) mà không thông báo trước cho tôi. Mỗi thay đổi như vậy gây ra các lỗi JavaScript im lặng làm hỏng việc hiển thị trang theo những cách không thể đoán trước.

**Giải pháp:** Tôi đã phát triển giải pháp hai phần:
- **Code phòng thủ** – Tôi đã học cách sử dụng F12 Developer Tools để điều tra lỗi một cách có hệ thống. Sau đó tôi đã thêm các kiểm tra null phòng thủ và optional chaining (?.) xuyên suốt code hiển thị. Giờ đây, các trường bị thiếu hoặc đổi tên tạo ra hiển thị trống thay vì sự cố toàn trang.
- **Cải tiến quy trình** – Tôi đã thiết lập một quy chuẩn giao tiếp với Jin: bất kỳ thay đổi nào đối với cấu trúc phản hồi API phải được thông báo trong chat nhóm trước khi được merge. Điều này cho tôi thời gian để cập nhật frontend chủ động thay vì phản ứng với các bản build bị hỏng.

### Thách thức 4: Đồng bộ trạng thái thời gian thực trên nhiều màn hình người chơi

Trong một trò chơi nhiều người chơi nơi mỗi người chơi có bộ bài riêng và các quyết định dựa trên giai đoạn, việc giữ cho mọi màn hình đồng bộ theo thời gian thực hóa ra khó khăn hơn dự kiến. Người chơi đôi khi thấy dữ liệu cũ — ví dụ, một lá bài họ đã chơi vẫn xuất hiện có sẵn trên màn hình của họ, dẫn đến nhầm lẫn và hành động trùng lặp.

Nguyên nhân gốc rễ có hai yếu tố: thứ tự sự kiện WebSocket không nhất quán và frontend lưu trạng thái cục bộ mà không xác minh với máy chủ.

**Giải pháp:** Tôi đã triển khai chiến lược đồng bộ ba lớp:

| Lớp | Cách tiếp cận | Kết quả |
|---|---|---|
| Nguồn sự thật chính | Mỗi màn hình phải tải lại trạng thái từ máy chủ ở đầu mỗi giai đoạn | Loại bỏ drift cache cục bộ |
| Cập nhật lạc quan với rollback | UI cập nhật ngay khi hành động người chơi, nhưng hoàn nguyên nếu máy chủ từ chối | Bảo tồn tốc độ phản hồi trong khi đảm bảo tính đúng đắn |
| Kiểm tra heartbeat | Client gửi tín hiệu "vẫn còn sống" định kỳ; máy chủ đẩy đồng bộ trạng thái đầy đủ nếu phát hiện không khớp | Bắt được sự không đồng bộ trước khi người chơi nhận thấy |

Ngoài ra, tôi đã thêm chỉ báo đồng bộ trực quan (một chấm xanh nhỏ chuyển sang màu cam khi client nghi ngờ không đồng bộ) để người chơi biết khi màn hình của họ được đồng bộ đầy đủ hay có thể đã cũ.

---

## Thông điệp cho các sinh viên tương lai

### Thiết kế cho mô hình tư duy của người dùng, không phải mô hình dữ liệu của code

Backend biểu diễn trạng thái trò chơi dưới dạng các từ điển lồng nhau sâu. Frontend không nên phản ánh cấu trúc này trực tiếp, thay vào đó nên trình bày thông tin theo thứ tự và nhóm phù hợp với người chơi, không phải theo thứ tự thuận tiện cho nhà phát triển backend. Khi thiết kế màn hình, bắt đầu với câu hỏi "người chơi cần biết gì ngay bây giờ?" và tổ chức hiển thị xung quanh câu trả lời đó.

### Xây dựng JavaScript phòng thủ từ đầu

Mỗi trường phản hồi API bạn hiển thị trong trình duyệt nên được kiểm tra xem có tồn tại không trước khi bạn cố sử dụng nó. Sử dụng optional chaining (response?.players?.[0]?.hype) và nullish coalescing (value ?? defaultValue) xuyên suốt code hiển thị của bạn. Một trường bị thiếu nên tạo ra hiển thị dự phòng linh hoạt ('--' hoặc 'Đang tải'). Một sai lầm đơn giản như gọi sai tên API có thể khiến toàn bộ màn hình không tải được.

---

## Những gì cần cải thiện

### Màn hình thông báo phá sản (Tính năng bị thiếu quan trọng)

Hiện tại, khi một người chơi phá sản, không có màn hình thông báo hay modal rõ ràng. Người chơi đơn giản thấy mình không thể thực hiện hành động, không có lời giải thích tại sao. Điều này gây ra nhầm lẫn, thất vọng và làm gián đoạn trải nghiệm học tập — đặc biệt đối với người chơi mới có thể không ngay lập tức kết nối trạng thái tài chính với việc không thể chơi.

**Giải pháp đề xuất:** Xây dựng một màn hình thông báo phá sản chuyên dụng:
- Kích hoạt ngay khi quỹ của người chơi giảm xuống dưới không.
- Giải thích tại sao phá sản xảy ra (ví dụ: "Bạn đã hết quỹ sau khi không đảm bảo được cam kết đầu tư").
- Đưa ra các bước tiếp theo rõ ràng: "Quay lại sảnh chờ" hoặc "Xem các vòng còn lại".
- Bao gồm tóm tắt trực quan về các chỉ số cuối của người chơi (tiến trình tài trợ, hype, transparency, năng lượng) cho mục đích học tập.

Đây là tính năng bị thiếu rõ ràng nhất hiện tại và nên được ưu tiên trước bất kỳ cải tiến nào khác.

### Phản hồi trực quan cho các quyết định đầu tư bot (Điểm mù UX)

Danh sách nhà đầu tư cập nhật im lặng bất cứ khi nào một bot đầu tư hoặc rút tiền. Mặc dù dữ liệu thay đổi chính xác, người chơi không nhận được tín hiệu trực quan rằng điều gì đó vừa xảy ra. Kết quả là, họ phải liên tục quét toàn bộ danh sách để phát hiện thay đổi — một quá trình tẻ nhạt và dễ xảy ra lỗi, đặc biệt khi có tối đa 200 nhà đầu tư đang hoạt động.

**Giải pháp đề xuất:** Thêm phản hồi trực quan nhẹ nhàng:
- Làm nổi bật đầu tư: Các hàng đầu tư mới nhấp nháy xanh lá ngắn (500ms) và hiển thị huy hiệu +X bên cạnh số tiền đóng góp.
- Làm nổi bật rút tiền: Các khoản đầu tư bị rút flash màu đỏ hoặc cam, hoặc mờ dần một cách linh hoạt.

Điều này làm cho danh sách nhà đầu tư cảm thấy sống động và responsive mà không cần animation nặng hay overhead hiệu suất.

### Thông báo lỗi quá kỹ thuật cho người chơi không phải nhà phát triển

Khi có gì đó xảy ra sai, chẳng hạn như lệnh gọi API thất bại, timeout, hoặc hành động không hợp lệ, các thông báo lỗi hiển thị cho người chơi thường là văn bản JavaScript thô hoặc ngoại lệ backend. Ví dụ, người chơi có thể thấy `TypeError: Cannot read property 'funding' of undefined` thay vì điều gì đó dễ đọc như "Không thể tải trạng thái trò chơi. Vui lòng làm mới trang."

**Giải pháp đề xuất:** Triển khai lớp xử lý lỗi thân thiện với người dùng và thêm nút "Sao chép chi tiết lỗi" cho người dùng nâng cao hoặc báo cáo lỗi, để các nhà phát triển vẫn nhận được thông tin kỹ thuật họ cần.

### Không có màn hình kết thúc cho người chơi có lượt chơi ngắn hơn (Thiếu cảm giác kết thúc cho những người thoát sớm)
 
Hiện tại, khi một người chơi hoàn thành lượt chơi của mình nhưng không phá sản, không có màn hình kết thúc hay cảm giác khép lại. Điều này thường xảy ra khi tổng số giai đoạn tối đa là 9, nhưng những người chơi chọn quy mô Nhỏ/Trung bình sẽ kết thúc trò chơi sớm hơn. Trò chơi đơn giản dừng lại với họ mà không có lời giải thích nào.
 
Điều này đặc biệt gây nhầm lẫn vì host và các người chơi khác có thể tiếp tục chơi, khiến người chơi có lượt ngắn hơn không chắc liệu trò chơi có còn đang diễn ra hay có điều gì đó bị hỏng.
 
**Giải pháp đề xuất:** Thêm màn hình "Hoàn thành lượt chơi" chuyên dụng cho những người chơi kết thúc trước khi trò chơi toàn cục kết thúc:
- Kích hoạt tự động khi người chơi đạt đến giai đoạn cuối cùng có sẵn của họ (ví dụ: Giai đoạn 5 trong tổng số 9).
- Hiển thị thông báo rõ ràng: "Bạn đã hoàn thành tất cả các giai đoạn có sẵn cho lượt chơi của mình".

### Không có tóm tắt cuối trò chơi hay tổng kết học tập

Khi trò chơi kết thúc, dù bằng cách hoàn thành tất cả các giai đoạn hay qua phá sản, hiện tại không có màn hình tóm tắt ngoại trừ đầu ra xếp hạng. Điều này làm suy yếu mục tiêu giáo dục của trò chơi.

**Giải pháp đề xuất:** Thiết kế màn hình tổng kết cuối trò chơi hiển thị:
- Phân tích điểm cuối: Tiến trình tài trợ, hype, transparency, năng lượng với giải thích.
- Dòng thời gian quyết định quan trọng: Danh sách đơn giản gồm 3–5 khoảnh khắc then chốt (ví dụ: "Bạn đã chấp nhận tài trợ cầu nối lãi suất cao ở Giai đoạn 2 → mất 15 transparency").
- So sánh với người chơi khác: Trung bình ẩn danh (ví dụ: "Hầu hết người chơi đạt 70% tài trợ vào Giai đoạn 5. Bạn đạt 45%.").
- Bài học chính được học: Một hành động có thể thực hiện được tạo ra dựa trên điểm yếu của người chơi (ví dụ: "Lần sau, hãy tập trung vào việc duy trì transparency — nó thu hút các nhà đầu tư có đạo đức").

Điều này biến trò chơi từ một hoạt động một lần thành một công cụ học tập thực sự, nơi người chơi rời đi với những hiểu biết cụ thể.


