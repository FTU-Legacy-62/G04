
Trường Đại học Ngoại thương — NHA408E(2526-2)GD2.01

Nhóm 4  ·  Hà Nội, tháng 6 năm 2026

|<p>**DẤU ẤN CÁ NHÂN**</p><p>Fun(d) Raising — Fundraising Simulation Game</p><p>Khi có funds, sẽ có fun</p>|
| - |

|**Mục**|**Chi tiết**|
| - | - |
|Họ và tên|Hà Bảo Khanh|
|Mã sinh viên|2314380702|
|Lớp|NHA408E(2526-2)GD2.01|
|Nhóm|Nhóm 4 - Fun(d) Raising|
|Vai trò chính|Investor Bot System Designer |
|Vai trò phụ|Game Tester & Gameplay Balance Validator|
|Giảng viên hướng dẫn|PGS. TS. Phan Trần Trung Dũng|

|<p>"Trong sự phát triển trò chơi "FUN(D) RAISING," vai trò Investor Bot System Designer là điểm kết nối giữa các mô hình tài chính và gameplay tương tác  cho máy chủ và người chơi. Trong khi financial metrics tạo nền dữ liệu xác định, bot system chuyển các con số này thành hành vi thị trường chủ động, tạo áp lực cạnh tranh và phản ứng cần thiết cho một fundraising simulation có độ chân thực cao. Công việc này bảo đảm các quyết định chiến lược của người chơi được đáp lại bằng phản ứng thuật toán tinh vi, phản ánh hiệu quả sự biến động và sắc thái tâm lý của venture capital ngoài đời thực."</p><p></p><p>Vai trò này chịu trách nhiệm quản trị thuật toán đối với dòng vốn, bảo đảm luồng phản ứng cạnh tranh của simulation vừa ổn định về mặt toán học vừa xác thực về mặt hành vi. Bằng cách xác định thời điểm, quy mô và điểm đến của khoản đầu tư thông qua quality assurance nghiêm ngặt và behavioral modeling, phần việc này thiết lập logic cạnh tranh trung tâm giữa những người chơi.</p><p>Sau khi xác lập vị trí cấu trúc và nhiệm vụ chiến lược của vai trò này, tôi cần phân tích các khung kiến trúc cụ thể làm cho bot system vận hành.</p><p></p>|
| - |














# MỤC LỤC
[1.  Vai trò trong dự án	1](#_toc232066765)

[1.1  Vai trò chính - Investor Bot System Designer	1](#_toc232066766)

[1.2  Vai trò phụ - Game Tester & Gameplay Balance Validator	1](#_toc232066767)

[2.  Dấu ấn cá nhân trong sản phẩm	1](#_toc232066768)

[2.1  Thiết kế kiến trúc của Investor Bot System	1](#_toc232066769)

[2.2 Behavioral Modeling: Phân loại nhà đầu tư bốn tầng	2](#_toc232066770)

[2.3 Triển khai thuật toán: Attractiveness và Memory Decay	3](#_toc232066771)

[2.4 Market Dynamics: Withdrawal Logic và Softmax Distribution	4](#_toc232066772)

[2.5  Phạm vi Game Testing	4](#_toc232066773)

[2.6 Các Code Commits chính	5](#_toc232066774)

[3.  Các nhiệm vụ thực tế đã hoàn thành	6](#_toc232066775)

[3.1  Nhiệm vụ phát triển Bot System	6](#_toc232066776)

[4.  Files, Features và Components đã đóng góp	9](#_toc232066777)

[4.1  Bot System - Code trong app.py	9](#_toc232066778)

[4.2  Game Testing Artefacts	10](#_toc232066779)

[5.  Bằng chứng đóng góp	10](#_toc232066780)

[5.1  Code Commits	11](#_toc232066781)

[5.2  Bằng chứng về workflow và tài liệu	12](#_toc232066782)

[5.3  Demo Session	13](#_toc232066783)

[6.  Cách phần việc này kết nối với sản phẩm cuối cùng	13](#_toc232066784)

[7.  Những điều tôi học được	14](#_toc232066785)

[7.1  Behavioral Finance Modelling	14](#_toc232066786)

[7.2  Simulation Parameter Tuning	14](#_toc232066787)

[7.3  Structured Game Testing	14](#_toc232066788)

[7.4  Data Contract Discipline	14](#_toc232066789)

[7.5  Flask State Management	15](#_toc232066790)

[8.  Các thách thức gặp phải và cách giải quyết	15](#_toc232066791)

[9.  Thông điệp cho sinh viên khóa sau	16](#_toc232066792)

[9.1  Khi xây dựng Bot System	16](#_toc232066793)

[9.2  Khi thực hiện Game Testing	16](#_toc232066794)

[9.3  Điểm cần cải thiện	17](#_toc232066795)


# <a name="_toc232066765"></a>**1.  Vai trò trong dự án**
## <a name="_toc232066766"></a>**1.1  Vai trò chính - Investor Bot System Designer** 
Tôi đảm nhiệm vai trò Investor Bot System Designer cho FUN(D) RAISING. Vai trò này nằm tại giao điểm giữa behavioral finance modelling và real-time game mechanics.

Trong kiến trúc dự án, module của tôi nằm giữa financial metrics layer (Phúc) và Api route (Jin). Mỗi phase của gameplay đều đi qua bot system: Phúc tính project metrics, hệ thống của tôi đánh giá các metrics đó qua lăng kính 200 hồ sơ nhà đầu tư khác nhau, đưa ra quyết định investment và withdrawal, rồi trả về kết quả funding allocation để Phúc cập nhật funding progress và available cash của từng dự án.
## <a name="_toc232066767"></a>**1.2  Vai trò phụ - Game Tester & Gameplay Balance Validator**
Bên cạnh bot system, tôi còn đảm nhiệm vai trò Game Tester cho toàn bộ sản phẩm. Công việc này bao gồm thiết kế và thực hiện các structured test cases xuyên suốt mọi game phases - từ tạo phòng và nộp dự án, chọn deck, chơi card trong game, các bot investment rounds, reaction triggers, đến tính final score.

Với vai trò Game Tester, tôi chịu trách nhiệm: phát hiện edge-case failures trước demo, xác thực các financial formulas trong calculate\_metrics() cho ra output đúng với input đã biết, kiểm tra bot behaviour có khớp với design intent dưới các cấu hình dự án khác nhau hay không, và lập bug reports đủ rõ để các thành viên khác có thể xử lý. Vai trò này bảo đảm sản phẩm trình bày ở midterm demo không có critical crashes và mọi core mechanics hoạt động đúng như dự kiến.
# <a name="_toc232066768"></a>**2.  Dấu ấn cá nhân trong sản phẩm**
## <a name="_toc232066769"></a>**2.1  Thiết kế kiến trúc của Investor Bot System**
Tính toàn vẹn cấu trúc của simulation đòi hỏi một heuristic engine định hướng bởi hành vi để vượt qua giới hạn của randomization ngẫu nhiên đơn giản. Những fundraising simulations chân thực cần các agents phản ứng phi tuyến trước market volatility và project health. Bằng việc triển khai hệ thống dựa trên behavioral finance, kiến trúc này đem lại cho người chơi một môi trường vừa có thể dự đoán vừa phức tạp, nơi các strategic trade-offs - như căng thẳng giữa hype-generation mạnh và transparency nền tảng - tạo ra các hệ quả khác biệt, nhất quán về mặt logic.

Về mặt kiến trúc, bot system hoạt động như một intermediary processing layer trong backend infrastructure. Nó nằm giữa financial metrics layer (Phúc) và API routing layer (Jin). Trong mỗi gameplay phase riêng biệt, hệ thống tiếp nhận project metrics và đánh giá chúng qua lăng kính 200 hồ sơ nhà đầu tư khác nhau. Output tạo ra quyết định funding progress và cash liquidity cho từng người tham gia, hình thành một chu trình action - reaction liên tục, dựa trên dữ liệu.

**Trách nhiệm chính của vai trò:**

- **Behavioral Finance Modeling: Chuyển đổi các hồ sơ tâm lý định tính thành weight vectors và sensitivity parameters định lượng.**
- **Real-time Mechanics Integration: Bảo đảm bot system điều chỉnh linh hoạt theo "reaction cards" trong game và các market scenarios đang thay đổi.**
- **Capital Allocation Logic: Thiết kế các mathematical frameworks, đặc biệt là Softmax distributions đã được tinh chỉnh, để điều phối việc phân bổ vốn giữa các dự án cạnh tranh.**
- **System Stability: Xây dựng các "helpers" theo hướng defensive programming nhằm duy trì data integrity trong môi trường Flask khi JSON serialization.**

Việc xác lập vị trí cấu trúc này cho phép tôi phân tích chi tiết hơn các behavioral heuristics cụ thể định hình nhóm nhà đầu tư.
## <a name="_toc232066770"></a>**2.2 Behavioral Modeling: Phân loại nhà đầu tư bốn tầng**
Mục tiêu chiến lược của việc phân hóa tính cách nhà đầu tư là tái hiện tính không đồng nhất của market dynamics ngoài đời thực. Bằng cách tạo ra các hành vi khác nhau, simulation buộc người chơi nhận ra rằng một chiến lược fundraising đơn nhất là không hiệu quả. Mỗi lớp nhà đầu tư ưu tiên những yếu tố khác nhau, buộc người chơi phải cân bằng metrics tinh tế để tiếp cận các tầng vốn khác nhau. Đóng góp nổi bật nhất của tôi là phân hóa hành vi của 200 AI investor bots. Thay vì dùng một mô hình đầu tư đồng nhất, tôi thiết kế bốn kiểu tính cách nhà đầu tư phản ứng khác nhau với cùng project metrics.

|**Loại bot**|**Logic trọng số**|**Khẩu vị rủi ro**|**Tác động chiến lược**|
| - | - | - | - |
|**FOMO**|Hype weight (0.42); tập trung visibility.|Cao / Ưa rủi ro |Tăng tốc dòng vốn vào các dự án high-hype; kích hoạt rút vốn nhanh khi yếu tố dự án thay đổi.|
|**Value Hunter**|0\.0 Hype weight; thuần intrinsic.|Thấp / Phân tích|Ưu tiên giá trị nội tại: gross margin, burn rate và capital efficiency.|
|**Whale**|Tập trung vào capital structure và valuation sanity.|Vừa phải / Ổn định|Phân bổ lượng vốn lớn dựa trên long-term track records và metric stability.|
|**Random**|Stochastic investment logic.|Khó đoán|Đưa độ nhiễu thị trường vào để tránh việc "giải" bot algorithms theo kiểu deterministic.|

**Ý nghĩa chiến lược của Behavioral Differentiation:** Kiến trúc này đóng vai trò như một động cơ mô phỏng hành vi tài chính thị trường, tâm lí thị trường. Ví dụ, một dự án ưu tiên "hype" có thể thu hút early-stage liquidity từ FOMO bots, nhưng nguồn vốn này rất mong manh. Nếu transparency bị suy giảm, các agents này sẽ rời khỏi, trong khi những dự án duy trì "valuation sanity" cao sẽ nhận được sự hậu thuẫn lớn và bền vững hơn từ Whales. Điều này tạo ra môi trường học tập nơi người chơi phải quản trị "reputation" như một tài sản hữu hình dù bản chất là vô hình**.**
## <a name="_toc232066771"></a>**2.3 Triển khai thuật toán: Attractiveness và Memory Decay**
Sự chặt chẽ về toán học là cần thiết để bảo đảm quyết định của bot vừa có thể dự đoán vừa linh hoạt, tạo nền tảng logic cho các simulation outcomes phù hợp với trực giác người dùng.

**Short-Term Memory Decay System:** Để mô phỏng tầm quan trọng của historical trajectory của dự án, mỗi bot lưu lịch sử attractiveness scores trong năm vòng trước đó. Cơ chế này ngăn hành vi phản ứng thuần túy trong 1 vòng và buộc bots đánh giá tính nhất quán trong hiệu suất của founder.

\# Blending formula for historical trajectory

\# decay: type-specific (e.g., 0.02 for FOMO vs 0.4 for Whales)

final\_attr = (1 - decay) \* current\_attr + decay \* weighted\_avg(history)

**Attractiveness Formula Deep-Dive:** Hàm core attractiveness xử lý tám metric keys chính - INTRINSIC (security hoặc regulatory risk,...), VALUATION, ROI\_NORM, SCALABILITY, VISIBILITY, TRANSPARENCY, HYPE, FUNDING PROGRESS - nhân với sensitivity vectors theo từng bot. Các parameters quan trọng gồm:

- Valuation Sanity Penalty: Một khoản trừ xác định tối đa -45 điểm đối với những valuations phi thực tế.
- Trust Scaling:  scores được điều chỉnh theo transparency/trust score của người chơi ().
- Stochastic Noise: Các biến nhiễu có giới hạn ( cho standard bots;  cho Random bots) được đưa vào để mô phỏng rủi ro thị trường.

Bài học về Reputation: Việc đưa exponential memory decay vào biến "trust recovery" thành một bài học khó nhưng thực tế cho người chơi. Một founder thể hiện quản trị yếu ở các phases đầu không thể lập tức khôi phục investor confidence chỉ bằng một lượt cải thiện metrics; decay bảo đảm các thất bại trong quá khứ vẫn lưu lại trong memory của thị trường, củng cố ý niệm rằng reputation được xây dựng theo thời gian nhưng có thể bị phá hủy trong chốc lát.
## <a name="_toc232066772"></a>**2.4 Market Dynamics: Withdrawal Logic và Softmax Distribution**
Dòng vốn- cả việc triển khai lẫn rút lại - đóng vai trò là feedback mechanism chính của simulation. Hệ thống phải điều tiết các dòng này để bảo đảm market environment có tính cạnh tranh nhưng không trở nên ngẫu nhiên quá mức.

Withdrawal Heuristics Bots đánh giá lại vị thế của mình trong mỗi vòng. Nếu attractiveness của allocation hiện tại thấp hơn một threshold so với các market alternatives, withdrawal sẽ được kích hoạt:

- Difference > 25 points: Bot thực hiện divestment 50% allocation hiện tại.
- Difference > 15 points: Bot thực hiện divestment 25%.
- Protection Mechanism: Để tránh "death spirals" ở các dự án gần được funded, nếu một dự án vượt 80% progress, withdrawal amounts sẽ được nhân với dampening factor 0.3.

Softmax Investment Distribution and Diversity: Để ngăn vốn tập trung khi một dự án outlier giành 100% available funds, hệ thống sử dụng Softmax distribution. Temperature parameter được tinh chỉnh lặp từ /20 lên /35 để vốn lan tỏa rộng hơn. Ngoài ra, một Diversity Penalty được áp dụng để mô phỏng market saturation: trong đó saturation là tỷ lệ đầu tư vốn so với target funding. Điều này bảo đảm bots được khuyến khích bằng thuật toán để tìm cơ hội thay thế khi dự án tiến gần funding cap.

Market Ramp-up Schedule: Để mô phỏng sự trưởng thành của fundraising environment, số active bots tăng 20% mỗi phase (từ 40 bots ở Phase 1 lên 200 bots ở Phase 5+), qua đó tăng mức độ căng thẳng khi game tiến triển.
## <a name="_toc232066773"></a>**2.5  Phạm vi Game Testing**
Ở vai trò Game Tester, nhiệm vụ chính của tôi là trở thành lớp kiểm soát cuối cùng về tính toàn vẹn kiến trúc và độ chính xác toán học. Tôi tạo hơn 50 structured test trường hợp bao phủ: xác minh công thức calculate\_metrics (tính tay so với code output), boundary values của bot attractiveness, độ phân bổ Softmax allocation dưới các cấu hình dự án khác nhau, điều kiện withdrawal trigger, reaction card condition matching, và các end-to-end multiplayer phase runs với 2, 3 và 4 người chơi đồng thời. Testing vượt khỏi kiểm tra đơn giản để đi vào boundary analysis toàn diện - bảo đảm system stability ở các giới hạn cực đoan của algorithmic ranges.

|**Hạng mục**|**Phạm vi**|**Phát hiện & Hành động**|
| - | - | - |
|**Xác minh công thức**|So khớp manual vs. code cho calculate\_metrics.|Phát hiện lỗi logic tính runway; phối hợp recalibration với Metrics lead.|
|**Attractiveness Boundaries**|Hype/Transparency ở [0, 100].|Xác nhận penalty ceiling ở -45 pts; kiểm tra không có giá trị NaN/Inf trong edge conditions.|
|**Softmax Spread**|Distribution trên 2-4 players.|**Chẩn đoán stochastic concentration failure; tinh chỉnh temperature lên /35 và triển khai diversity-aware penalty.**|
|**Withdrawal Safety**|Negative liquidity triggers.|Xác minh total\_invested updates vẫn đối xứng với available\_cash movements.|
|**Điều kiện Multiplayer**|Concurrent join race conditions.|Phát hiện IndexErrors khi late entry; xây dựng stability helper ensure\_room\_lists để giảm lỗi.|
|**End-to-End Flows**|Chu trình room-to-score đầy đủ.|Normalised toàn bộ list fields bằng defensive programming để xử lý responsiveness failures trên host screen displays.|

QA lifecycle được chuẩn hóa thông qua Bug Report Log (12 lỗi lớn được theo dõi theo severity) và Pre-Demo Checklist, bảo đảm sản phẩm chuyển từ tập hợp các module rời rạc thành một simulation ổn định, gắn kết.
## <a name="_toc232066774"></a>**2.6 Các Code Commits chính**
\- feat: generate 200 bots with type-specific weights, decay, and sensitivity params

\- feat: implement attractiveness() with sensitivity, penalty, trust, and noise

\- fix: get\_bot\_memory handles Flask JSON string/int key mismatch

\- fix: ensure\_room\_lists and ensure\_bot\_alloc prevent concurrent-join crashes
# <a name="_toc232066775"></a>**3.  Các nhiệm vụ thực tế đã hoàn thành**

## <a name="_toc232066776"></a>**3.1  Nhiệm vụ phát triển Bot System**

|Nhiệm vụ|Mô tả|Input|Output|
| - | - | - | - |
|Tạo 200 virtual investors|Tạo bots với các tính cách riêng (FOMO, Value Hunter, Whale, Random). Mỗi bot có wealth class, capital amount, hype\_sens, trans\_sens, memory\_decay\_rate và weight vector. random.seed(42) bảo đảm khả năng tái lập.|Tự tạo bằng seeded randomness.|BOTS list (200 dicts) được Phúc dùng trong process\_phase() và được Jin lưu trong room state.|
|Tính project attractiveness|Weighted average tối đa 8 metric keys với per-bot sensitivity multipliers; valuation\_sanity penalty (tối đa −45 pts); trust scaling (×trust/100); bounded noise ±5 (±10 với Random).|Project metrics từ Phúc; trust\_scores từ Jin.|attractiveness score (0-100) cho mỗi bot-project pair, dùng để điều khiển invest/withdraw decisions.|
|Bot ramp-up theo phase|Phase 1: 20% bots active (40 bots). Mỗi phase +20% cho đến 200 bots ở phase 5+. Tạo investor activity ramp chân thực.|Current phase number.|Active bot subset được chuyển vào investment loop.|
|Memory-decay blending|Lịch sử attractiveness theo từng bot (5 phases gần nhất). Weighted average (phases gần hơn có weight cao hơn). Blended với current attractiveness bằng type-specific decay rate.|attractiveness\_history từ bot\_memory trong room.|final\_attr (float) dùng trong investment/withdrawal decision.|
|Withdrawal logic|Nếu attractiveness difference giữa best project và current project > 25 → withdraw 50%. Nếu diff > 15 → withdraw 25%. Nếu funding\_progress > 80% → withdrawal × 0.3 (bảo vệ near-funded projects).|Ma trận A (bot×project), current alloc\_entry.|Giảm perProject amounts; trả lại idle funds; funding\_progress và total\_invested được cập nhật.|
|Investment distribution (Softmax)|Softmax với temperature /35 (tinh chỉnh từ /20) + diversity penalty (saturation × 30 trừ trước Softmax) để phân tán capital. Per-bot cap: 15% target\_funding ở phase 1, 20% từ phase 2.|Shifted attractiveness scores, idle capital.|Capital được allocated cho projects; funding\_progress cập nhật; funding\_complete\_phase được ghi nhận.|
|Stability helpers|get\_bot\_memory(): luôn dùng str(bot\_id) để sửa Flask JSON int→string key conversion. ensure\_room\_lists(): normalises tất cả per-player list fields về đúng độ dài trên mọi request. ensure\_bot\_alloc(): normalises bot\_alloc sau JSON deserialization.|Room dict (có thể đã round-tripped qua JSON).|Room state an toàn, nhất quán cho mọi operations tiếp theo.|
|Aggregate\_bot\_actions()|Nhóm raw per-bot action events theo (type, action, player\_index) và cộng amounts. Trả về clean list để hiển thị log.|Danh sách raw bot action dicts từ process\_phase().|Aggregated bot action log dễ đọc, hiển thị trên host dashboard.|

**3.2  Nhiệm vụ Game Testing**

|**Khu vực test**|**Nội dung được test**|**Phương pháp**|**Phát hiện & Hành động**|
| - | - | - | - |
|Bot attractiveness boundaries|Attractiveness tại hype=0, hype=100; transparency=0, transparency=100; valuation\_sanity=0 (max penalty), valuation\_sanity=100.|Gọi function thủ công với boundary inputs; in toàn bộ 200 bot scores.|Xác nhận penalty cap ở −45 pts; xác nhận noise range ±5; không có giá trị NaN/Inf.|
|Softmax concentration bug|Capital spread trên 2, 3 và 4 projects đồng thời ở phases 1-5.|Multi-player game sessions; log per-project funding totals sau mỗi phase.|Phát hiện concentration bug (toàn bộ vốn đầu tư vào một project); tôi thay đổi temperature từ /20 lên /35 và thêm diversity penalty.|
|Withdrawal safety|available\_cash bị âm trong withdrawal khi cash < withdrawal amount.|Tạo một project có available\_cash=0 và kích hoạt bot withdrawal.|Xác nhận bankruptcy trigger hoạt động đúng; xác nhận total\_invested update đối xứng với available\_cash change.|
|Multiplayer race conditions|Hai người chơi nộp dự án đồng thời; host chạy phase trong khi người chơi đánh thẻ.|Hai browser tabs + phối hợp thời điểm.|Phát hiện ensure\_room\_lists() chưa được gọi trước player\_ready\_phase, gây IndexError khi player thứ 3 joined late. Báo cho Jin và đã sửa.|
|Final score edge cases|funding\_progress = 0%, 49.9%, 50%, 100%; phases\_used = 1 so với max\_phase.|Gọi trực tiếp final\_score() với boundary values.|Xác nhận 0% trả về 0; xác nhận 49.9% trả về giá trị khác 0 (không có hard cutoff ở 50% trong code thực tế — cập nhật cách hiểu của nhóm về rule).|
|End-to-end demo run|Full 4-player session: room create → submit → deck → 7 phases → end screen.|Live run với đủ 4 thành viên; tôi quan sát và log toàn bộ errors.|3 bugs được phát hiện và sửa trước midterm demo: IndexError ở mulligan, score không hiển thị trên host screen, reaction button không phản hồi sau khi dùng.|

# <a name="_toc232066777"></a>**4.  Files, Features và Components đã đóng góp** 

## <a name="_toc232066778"></a>**4.1  Bot System - Code trong app.py**

|**Function / Block**|**Dòng (ước tính)**|**Chức năng**|
| - | - | - |
|BOTS generation block|app.py:597–653 |Tạo 200 bots bằng random.seed(42); gán type, wealth class, wealth, hype\_sens, trans\_sens, memory\_decay\_rate và weight vector.|
|get\_bots\_for\_phase(phase)|app.py:655–658|Trả về BOTS[:count] trong đó count = min(200, phase × 40). Ramps bot participation qua các phases.|
|attractiveness(project, bot, metrics)|app.py:660–696|Tính weighted attractiveness score cho một bot-project pair với sensitivity, penalty, trust scaling và noise.|
|final\_score(proj, phases\_used, metrics)|app.py:698-724|Tính end-of-game score: funding×40 + speed×20 + roi×20 + transparency×20, được scale bởi scale\_factor và funding\_bonus.|
|get\_bot\_memory(room, bot\_id, n)|app.py:725-745|Trả về bot memory dict ổn định bằng str(bot\_id) để sửa Flask JSON key type mismatch.|
|ensure\_room\_lists(room)|app.py:746-774|Normalises tất cả per-player list fields (players, player\_ready, deck\_ready, mulligan\_used, phase\_energy, player\_triggers) về đúng độ dài.|
|ensure\_bot\_alloc(room)|app.py:775–802|Normalises bot\_alloc list sau deserialization; dựng lại các entries thiếu và sửa độ dài perProject array.|
|aggregate\_bot\_actions(bot\_actions)|app.py:803–821|Nhóm và cộng raw bot action events theo (type, action, player\_index) để tạo clean log output.|
|process\_phase(room, phase, players, logs, bot\_actions)|app.py:660–696|Full investment loop: memory decay, attractiveness matrix, withdrawal pass, investment Softmax pass với diversity penalty, funding\_complete\_phase tracking.|
|Withdrawal logic in process\_phase()|app.py:853–993|Diff-threshold withdrawal: 25→50%, 15→25%, ≤5→0%; funding protection|
|Near-funded protection|app.py:884–887|withdraw\_ratio × 0.3 khi funding\_progress > 0.8|
|Max withdrawal cap|app.py:888–891|max\_ratio = min(0.6, 0.2 + (phase-1)×0.05) cho mỗi phase|


## <a name="_toc232066779"></a>**4.2  Game Testing Artefacts**
- Test Case Spreadsheet (shared folder): 50 structured test trường hợp với input, expected output, actual output, trạng thái thành công/lỗivà bug reference.
- Bug Report Log (shared folder): 12 bugs được ghi nhận trong testing, mỗi bug có reproduction steps, expected behaviour, actual behaviour và severity (P0/P1/P2).
- Pre-Demo Checklist (shared folder): checklist 20 mục bao phủ tất cả core user flows; được tôi xác nhận hoàn tất vào đêm trước midterm demo.
- Phase-by-phase investment log: in bot allocations theo từng project và từng phase cho 5 game sessions đại diện, dùng để hiệu chỉnh Softmax temperature và diversity penalty.
# <a name="_toc232066780"></a>**5.  Bằng chứng đóng góp**

## <a name="_toc232066781"></a>**5.1  Code Commits**
Mã nguồn: phần app.py '# KHANH: BOT GENERATION' (dòng 597) đánh dấu điểm bắt đầu code block của tôi.

Liên kết truy cập: <https://github.com/khanhhabao7/nhap-fintech/blob/main/app.py> 

Liên kết game:  <https://nhap-fintech-5c8n.onrender.com/?fbclid=IwY2xjawSWM99leHRuA2FlbQIxMABicmlkETFJa1FVbm1lUHpIeEVGV29nc3J0YwZhcHBfaWQQMjIyMDM5MTc4ODIwMDg5MgABHroMY5O_O3Hbc_VCprCERO8dZygsV5n89iYjP2oScZ_-bJW-GHkawZS96KtP_aem_0Xqo_ClfJO4HFiY3l6sdUg> 

|**Commit Message**|**Nội dung thể hiện**|
| - | - |
|feat: generate 200 bots with type-specific weights, decay, and sensitivity params (seed=42)|BOTS block ban đầu - toàn bộ 200 bot profiles với randomness có thể tái lập.|
|feat: implement attractiveness() with sensitivity, penalty, trust, and noise|Triển khai công thức attractiveness cốt lõi.|
|feat: process\_phase withdrawal and investment with memory decay and diversity penalty|Đầy đủ process\_phase() - withdrawal loop, Softmax investment, diversity penalty, funding\_complete\_phase.|
|fix: get\_bot\_memory handles Flask JSON string/int key mismatch|Stability fix - normalisation str(bot\_id) trong get\_bot\_memory().|
|fix: ensure\_room\_lists and ensure\_bot\_alloc prevent concurrent-join crashes|Các defensive normalisation helpers.|
|feat: aggregate\_bot\_actions for readable phase logs|Nhóm bot actions cho host dashboard logs.|
|fix: Index Error on mulligan when 3rd player joins late|Phát hiện từ game testing - thiếu ensure\_room\_lists trong player\_ready\_phase.|
|fix: runway uses available\_cash not total\_invested|Phát hiện từ game testing - formula bug được báo cho Phúc.|

Lịch sử chỉnh sửa file app.py: <https://github.com/khanhhabao7/nhap-fintech/commits/main/app.py?author=khanhhabao7> 

Lịch sử chỉnh sửa file html.host: <https://github.com/khanhhabao7/nhap-fintech/commits/main/templates?author=khanhhabao7> 
## <a name="_toc232066782"></a>**5.2  Bằng chứng về workflow và tài liệu**
- Workflow diagram (Evidence 2, midterm proposal): module Bot System được thể hiện như một backend service riêng biệt, nhận requests từ Game Core (Phúc) và trả về investment allocations - tương ứng trực tiếp với process\_phase() và attractiveness().

![The diagram illustrates a Workflow System with various components including Evidences, Routes, Services, Data Store, API Gateway, Game Core, and User Interfaces, detailing processes like requesting, updating, and returning results in different phases of a project.&#x0A;&#x0A;AI-generated content may be incorrect.](Aspose.Words.2ab58010-2865-4523-90e2-4f2e70e92946.001.png)

- Phần bot behaviour trong Rule Table (Evidence 1, midterm proposal): bốn kiểu tính cách bot, Softmax capital allocation, withdrawal conditions và memory decay được tôi viết dựa trên logic đã triển khai.

![The image illustrates a strategic game framework, featuring different types of AI 'bots'￢ﾀﾔFOMO, Value Hunter, and Whale￢ﾀﾔeach with distinct investment strategies, and a scoring system based on funding progress, speed, and ROI, leading to an AI-driven winner.&#x0A;&#x0A;AI-generated content may be incorrect.](Aspose.Words.2ab58010-2865-4523-90e2-4f2e70e92946.002.png)

- Design document: 'Bot Behavioural Design and Weight Rationale' (team shared folder, Week 2) - do tôi soạn; được tất cả thành viên review trong buổi họp chung tuần 2.
- Test Case Spreadsheet và Bug Report Log (team shared folder) - do tôi lập trong vai trò Game Tester; được tham chiếu trong group meeting notes.
- Pre-Demo Checklist (team shared folder) - toàn bộ 20 mục được tôi kiểm tra và xác nhận vào đêm trước midterm demo.

## <a name="_toc232066783"></a>**5.3  Demo Session**
Trong midterm demo, tôi chịu trách nhiệm giải thích bot system behaviour cho giảng viên, minh họa cách các investor types khác nhau phản ứng khác nhau với cùng project configuration, trình diễn reaction card trigger system, đồng thời trình bày testing methodology và lịch sử bug-fix.
# <a name="_toc232066784"></a>**6.  Cách phần việc này kết nối với sản phẩm cuối cùng**

Bot system của tôi là cơ chế chuyển toàn bộ phần việc khác thành gameplay outcomes có ý nghĩa. Nếu không có nó, game sẽ không có competitive feedback loop - người chơi chỉ nộp dự án nhưng không thấy phản ứng thị trường. Với bot system:

- Financial metrics của Phúc (intrinsic, ROI, runway, valuation) trở nên có ý nghĩa vì bots dùng chúng để quyết định đầu tư vào đâu.
- Scenario events của Minh tạo hệ quả rõ ràng vì chúng làm thay đổi Bot confidence và kích hoạt memory decay.
- Card designs của Minh tạo strategic tradeoffs: hype cards thu hút FOMO bots; transparency cards thu hút Value Hunters và Whales.
- API routing của Jin hoạt động đúng vì bot system trả về structured data mà endpoints có thể chuyển trực tiếp tới frontend.
- Investor list display của Dương được điền từ bot investment decisions, giúp người chơi nhận real-time feedback về ai đang backing project của họ.

Với vai trò Game Tester, phần việc của tôi bảo đảm tất cả kết nối trên thực sự hoạt động trong điều kiện gameplay thật. Những bugs tôi phát hiện và báo cáo - lỗi công thức runway, reaction trigger mismatch, Index Error khi late join, score không hiển thị trên host screen - đều là integration failures tại ranh giới giữa các module. Nếu không có structured testing trên toàn bộ user flow, các lỗi này đã xuất hiện ngay trong live demo.
# <a name="_toc232066785"></a>**7.  Những điều tôi học được**

## <a name="_toc232066786"></a>**7.1  Behavioral Finance Modelling**
Việc thiết kế bốn investor profiles đòi hỏi tôi nghiên cứu cách các nhóm nhà đầu tư ngoài đời thực đưa ra quyết định. Bài tập này củng cố rằng hành vi đầu tư không phải một quyết định đồng nhất - fundraising thành công cần hiểu và đồng thời thuyết phục nhiều tâm lý nhà đầu tư khác nhau. FOMO-driven retail investors, value-focused institutional investors và large capital allocators đều có khẩu vị rủi ro và information-processing styles khác biệt về nền tảng, và tất cả khác biệt đó được phản ánh trong weight vectors.
## <a name="_toc232066787"></a>**7.2  Simulation Parameter Tuning**
Tôi học được rằng một simulation chỉ tốt khi edge-case handling và parameter calibration đủ tốt. Việc đổi Softmax temperature từ /20 lên /35 - kết hợp với diversity penalty - được phát hiện hoàn toàn qua gameplay testing, không phải từ suy luận toán học thuần túy. Điều này dạy tôi rằng simulation parameters phải được tinh chỉnh cho cả playability lẫn accuracy: một model đúng về kỹ thuật nhưng khiến game không thể thắng vẫn là thiết kế thất bại.
## <a name="_toc232066788"></a>**7.3  Structured Game Testing**
Trước dự án này, tôi chưa từng viết formal test cases. Việc học cách phân biệt reproduction step, expected behaviour và actual behaviour - đồng thời gán severity levels (P0 crash, P1 broken mechanic, P2 visual issue) - giúp bug reports trở nên actionable thay vì mơ hồ. Tôi cũng học được rằng test quan trọng nhất luôn là full end-to-end user flow, vì integration bugs chỉ xuất hiện khi tất cả modules được kết nối.
## <a name="_toc232066789"></a>**7.4  Data Contract Discipline**
Bot system phụ thuộc vào metrics từ Phúc và room state từ Jin, đồng thời trả dữ liệu ngược lại cho cả hai. Các integration bugs ban đầu xuất phát từ data contracts không chính thức bị thay đổi mà không trao đổi - Phúc trả runway theo tháng trong khi công thức của tôi kỳ vọng giá trị normalized 0-100. Tôi học được rằng trong bất kỳ multi-person codebase nào, mọi inter-module data contract phải được documented và change-controlled, kể cả trong một dự án học thuật ngắn.
## <a name="_toc232066790"></a>**7.5  Flask State Management**
Tôi học được rằng Flask jsonify() âm thầm chuyển integer dict keys thành strings, làm hỏng mọi code tra cứu bot IDs như integers sau một JSON round-trip. Cách sửa - get\_bot\_memory() luôn lưu và đọc dưới str(bot\_id) - khá đơn giản nhưng mất nhiều giờ để chẩn đoán. Trải nghiệm này khiến tôi cẩn trọng hơn với các giả định về data type trong web application state.
# <a name="_toc232066791"></a>**8.  Các thách thức gặp phải và cách giải quyết**

|**Thách thức**|**Nguyên nhân gốc**|**Cách giải quyết**|
| - | - | - |
|Capital over-concentration (tất cả bots đầu tư vào một project)|Softmax temperature /20 quá thấp - bất kỳ attractiveness difference >5 pts nào cũng gây xác suất gần 100% vào best project.|Tăng temperature lên /35. Thêm diversity penalty: saturation (invested/target\_funding) × 30 được trừ khỏi shifted attractiveness trước Softmax. Xác minh spread trên 4 projects qua 50 test runs.|
|Memory decay gây permanent penalties (snowball failure)|Decay coefficient ban đầu quá thấp; negative memories không bao giờ mờ đi. Một phase xấu có thể phá hủy fundraising prospects cho tất cả phases còn lại.|Thêm exponential decay để memories mờ dần qua nhiều phases. Hiệu chỉnh decay rate qua playtesting cho đến khi negative memories còn ~50% weight sau 3 phases phục hồi.|
|Metric format mismatch giữa công thức attractiveness của tôi và metric output của Phúc|Ban đầu Phúc trả runway theo tháng và ROI dạng số thập phân. Weights của tôi giả định mọi metrics nằm trong ranges normalised 0-100.|Thống nhất normalisation contract: Phúc thêm roi\_norm và runway-capped fields. Tôi cập nhật attractiveness() để đọc trực tiếp normalised outputs.|
|Flask JSON string/int key mismatch (bot\_memory Key Error sau API round-trip đầu tiên)|Flask json.dumps() chuyển integer bot IDs thành string keys. Lần gọi tiếp theo tới get\_bot\_memory(bot\_id=1) tra integer 1 nhưng chỉ tìm thấy '1'.|Triển khai get\_bot\_memory() luôn lưu và đọc dưới str(bot\_id). Thêm migration path (pops int key, re-stores under str key) cho mọi rooms đã tạo trước khi sửa.|
|Index Error khi player thứ 3 tham gia trong lúc phase đang chạy|endpoint player\_ready\_phase đọc room['player\_ready'][player\_index] mà không gọi ensure\_room\_lists() trước. Nếu một player tham gia sau khi room được tạo, list ngắn hơn kỳ vọng.|Thêm lệnh gọi ensure\_room\_lists(room) ở đầu các endpoints player\_ready\_phase, mulligan, use\_reaction và play\_card. Xác nhận fix trong multiplayer race-condition test.|

# <a name="_toc232066792"></a>**9.  Thông điệp cho sinh viên khóa sau**

## <a name="_toc232066793"></a>**9.1  Khi xây dựng Bot System**
- Hãy bắt đầu với attractiveness(). Mọi thứ trong bot system đều chảy từ hàm này. Trước khi thay đổi weights hoặc Softmax parameters, hãy in attractiveness scores cho một sample project ở từng phase và xác minh chúng di chuyển đúng hướng.
- Hãy dùng random.seed() ngay từ ngày đầu. Nếu không, mỗi test run sẽ tạo ra các bugs khác nhau và không thể tái hiện.
- Hãy test Softmax distribution riêng trước khi tích hợp. Nếu tất cả attractiveness scores tụ trong một khoảng hẹp, distribution sẽ gần như đồng đều bất kể chất lượng - hãy thêm temperature parameter và tinh chỉnh nó.
- Hãy document data contract trước khi viết code. Ghi rõ bot system kỳ vọng những lĩnh vực nào (metric names, value ranges, data types) và trả về chính xác những gì. Chia sẻ với metrics team và API team. Thay đổi contract này về sau sẽ rất khó xử lý.
## <a name="_toc232066794"></a>**9.2  Khi thực hiện Game Testing**
- Hãy viết test cases dưới dạng bảng, không phải ghi chú rời. Mỗi dòng cần có: input, expected output, actual output, pass/fail và việc đã làm để sửa. Ghi chú mơ hồ sẽ vô dụng khi bạn debug một crash 30 phút trước demo.
- Luôn chạy full end-to-end user flow ít nhất một lần trước mọi demo. Integration bugs chỉ xuất hiện khi tất cả modules chạy cùng nhau - unit tests trên từng functions riêng lẻ sẽ bỏ sót chúng.
- Hãy test với số players tối thiểu (2) VÀ với nhiều players hơn (3, 4). Bug Index Error chỉ xuất hiện với 3 players vì phòng được tạo cho 4 nhưng chỉ có 3 người tham gia.
- Gán severity levels P0/P1/P2 cho mọi bug. P0 = game crash, P1 = broken core mechanic, P2 = visual/cosmetic issue. Sửa tất cả P0 trước demo. Sửa tất cả P1 nếu còn thời gian. Document P2 cho giai đoạn sau demo.
## <a name="_toc232066795"></a>**9.3  Điểm cần cải thiện**
- Có thể cân nhắc bot type thứ năm: Contrarian bot đầu tư vào các dự án lower-hype nhưng có fundamentals mạnh. Điều này thưởng cho người chơi tập trung vào chất lượng dự án hơn marketing và bổ sung strategic diversity.
- Bổ sung automated integration tests (pytest + Flask test client) để nhóm bug thuộc dạng ensure\_room\_lists() được bắt tự động sau mỗi code change, không chỉ bằng manual testing.

|Lời khuyên cuối: hãy tự chơi game nhiều lần trước khi finalising bất kỳ parameters nào. Bot system là một simulation, và simulation chỉ tạo cảm giác đúng khi outcomes khớp với trực giác. Nếu một project có fundamentals mạnh liên tục thua một project chỉ có hype, thì weights của bạn đang có vấn đề. Hãy tin vào phán đoán của bạn với tư cách người chơi, không chỉ vào lý thuyết.|
| - |

Hà Bảo Khanh  ·  Student ID 2314380702  ·  Group 4 — Fun(d) Raising  ·  NHA408E(2526-2)GD2.01  ·  Trường Đại học Ngoại thương 2026
2

