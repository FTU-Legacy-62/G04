# Fun(d) Raising – Mô phỏng gọi vốn khởi nghiệp

**Mã nhóm:** G04

## Thành viên nhóm

| Họ và tên | MSSV | Vai trò chính |
|-----------|------|----------------|
| Nguyễn Ngọc Minh | 2313380019 | Cấu trúc cơ sở dữ liệu, hệ thống kịch bản, engine thẻ bài và tester |
| Ngô Thị Diễm Phúc | 2312380804 | Chỉ số tài chính, cấu trúc nhập liệu của người chơi, điều khiển luồng game (host) và tester |
| Hà Bảo Khanh | 2314380702 | Hệ thống bot nhà đầu tư, quản lý phản ứng (reaction) và tester |
| Kim Hye Jin | 2312380803 | Trưởng nhóm, backend Flask, định tuyến API, quản lý phòng chơi và tester |
| Vũ Bạch Dương | 2312380808 | Thiết kế UX/UI, frontend và tester |

## Mô tả ngắn gọn sản phẩm

**Fun(d) Raising** là game web mô phỏng gọi vốn khởi nghiệp dành cho 2–10 người chơi. Mỗi người tự xây dựng dự án của mình (chọn quy mô, định giá, cơ cấu vốn, dự báo doanh thu), thiết kế bộ bài gồm 42 thẻ Active và tối đa 7 thẻ Reaction (người chơi phải chọn 22 thẻ Active và tối đa 3 thẻ Reaction). Qua nhiều vòng (5–9 vòng tuỳ theo quy mô), người chơi đối mặt với các sự kiện ngẫu nhiên (thị trường, nội bộ, pháp lý) và ra quyết định chơi bài để thu hút vốn từ 200 bot nhà đầu tư AI (FOMO, Value Hunter, Whale, Random). Người điều khiển (host) quản lý nhịp độ trận đấu, hệ thống tự động tính điểm cuối cùng dựa trên tiến độ gọi vốn, tốc độ, ROI và minh bạch – người có điểm cao nhất sẽ thắng.

## Vấn đề mà sản phẩm giải quyết

Sinh viên tài chính và những người muốn khởi nghiệp thiếu một môi trường an toàn, chi phí thấp để thực hành các quyết định gọi vốn ngoài đời thực. Trong thực tế, việc thử – sai chiến lược gọi vốn có thể gây hậu quả tài chính nghiêm trọng hoặc bỏ lỡ cơ hội.

Sản phẩm giải quyết vấn đề đó bằng cách cung cấp mô phỏng tương tác, nơi người dùng thấy ngay tác động của quyết định lên các chỉ số tài chính cốt lõi (biên lợi nhuận gộp, tốc độ đốt tiền, ROE, độ hợp lý của định giá, thời gian vận hành) và hành vi của nhà đầu tư. Điều này quan trọng vì nó ảnh hưởng trực tiếp đến khả năng huy động vốn thành công – kỹ năng sống còn với bất kỳ dự án khởi nghiệp nào.

## Đối tượng người dùng mục tiêu

- **Sinh viên Tài chính – Ngân hàng – Quản trị kinh doanh** cần hiểu mối liên hệ giữa quyết định tài chính (giá, giá vốn, đòn bẩy, kế hoạch chi tiêu) và kết quả gọi vốn thực tế.
- **Nhà sáng lập startup giai đoạn đầu** muốn thử nghiệm chiến lược gọi vốn, cân bằng “hype” ngắn hạn với “minh bạch” dài hạn, và học cách ứng phó với biến cố thị trường bất lợi.
- **Giảng viên** giảng dạy tài chính doanh nghiệp hoặc venture capital, dùng game làm công cụ tương tác trong lớp, giúp sinh viên trải nghiệm cạnh tranh gọi vốn trong môi trường học thuật.

## Tính năng chính

- **Mô phỏng nhiều người chơi với host điều khiển:** Host tạo phòng (2–10 người), điều khiển tiến trình vòng chơi, theo dõi tất cả người chơi theo thời gian thực qua bảng điều khiển riêng.
- **Hệ sinh thái bot nhà đầu tư AI:** 200 bot với 4 kiểu hành vi riêng biệt (FOMO, Value Hunter, Whale, Random) tự động đầu tư hoặc rút vốn dựa trên chỉ số tài chính và điểm hấp dẫn của từng dự án.
- **Mô phỏng tài chính động theo từng vòng:** Mỗi vòng, một sự kiện ngẫu nhiên được áp dụng (24 tình huống). Người chơi dùng năng lượng (3/vòng) để chơi thẻ chủ động, kích hoạt thẻ phản ứng khi đủ điều kiện. Hệ thống tính lại các chỉ số: Giá trị nội tại, độ hợp lý định giá, chỉ số ROI chuẩn hóa, thời gian vận hành, tiến độ gọi vốn.
- **Hệ thống thẻ bài chiến lược kết hợp sự kiện ngẫu nhiên:** Mỗi vòng, người chơi rút thẻ chủ động (từ bộ 22 thẻ tự thiết kế) và phản ứng với sự kiện thị trường, pháp lý, nội bộ hoặc bên ngoài; thẻ phản ứng có thể được kích hoạt tự động trong các tình huống khủng hoảng cụ thể.
- **Bảng xếp hạng theo quy mô và tổng thể:** Host có thể xem tiến độ thời gian thực, chỉ số hype, minh bạch và điểm của tất cả người chơi. Game tự động kết thúc khi tất cả dự án hoàn thành số vòng hoặc phá sản, hiển thị điểm cuối cùng (0–100) để xác định người thắng cuộc.

## Cách mở hoặc chạy sản phẩm

1. Mở link game: [https://g04-sh5t.onrender.com/](https://g04-sh5t.onrender.com/)
2. Host nhấn **"Create Room"** để tạo phiên chơi và nhận các link tham gia riêng cho mỗi người chơi.
3. Mỗi người chơi mở link riêng của mình và điền các thông số tài chính cho startup.
4. Mỗi người chơi xây dựng bộ bài: chọn đúng 22 thẻ chủ động và tối đa 3 thẻ phản ứng.
5. Khi tất cả sẵn sàng, host nhấn **"Start Game"** để bắt đầu Vòng 1.
6. Mỗi vòng: một sự kiện ngẫu nhiên được kích hoạt → người chơi rút 5 thẻ và dùng năng lượng để chơi bài → host nhấn **"Run Phase"** → bot đầu tư hoặc rút vốn → các chỉ số cập nhật trên bảng xếp hạng.
7. Lặp lại đủ số vòng tương ứng với quy mô dự án (Nhỏ: 5, Trung bình: 7, Lớn: 9).
8. Sau vòng cuối cùng, xem bảng xếp hạng và điểm số (0–100) để xác định người chiến thắng.
