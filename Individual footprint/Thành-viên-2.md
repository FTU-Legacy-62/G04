**Individual Footprint của Nguyễn Ngọc Minh**

**MSSV:** 2313380019

**1\. Vai trò trong dự án**

Trong dự án này, tôi phụ trách phần thiết kế dữ liệu gameplay và xây dựng logic card/scenario cho startup fundraising game. Nói rõ hơn, tôi là người xây bộ dữ liệu nền cho game gồm SCENARIOS, ACTIVE_CARDS_FULL, REACTION_CARDS, quy tắc chuẩn hóa tag bằng TAG_ALIASES, các hàm nối scenario với card như normalize_tag(), normalize_tags(), card_matches_scenario(), hai hàm rút bài draw_hand_with_cost_ladder() và draw_hand_no_duplicate_color_cost(), cùng hàm kiểm tra chất lượng dữ liệu validate_master_data(). Toàn bộ các thành phần này xuất hiện trực tiếp trong file logic tôi nộp ở bản cuối.

Vai trò của tôi nằm ở lớp logic gameplay, tức là phần kết nối giữa dữ liệu game và trải nghiệm người chơi. Lớp logic này quy định cách các tình huống trong game được tạo ra, cách các thẻ được lựa chọn theo từng scenario, cách chỉ số của startup thay đổi sau mỗi hành động và cách hệ thống xác định khi nào người chơi cần dùng reaction card. Trong bài, tôi đã định nghĩa rõ các chỉ số mà gameplay tác động tới như hype, visibility, trust_all, transparency, reg_risk, runway, funding_boost_percent, security, whale_trust, cogs và sell_pressure_reduce. Nhờ đó, ý tưởng “vận hành startup và gọi vốn” được chuyển thành một hệ thống luật rõ ràng, có thể chạy được bằng code và có thể giải thích được trong phần demo.

Điểm tôi phụ trách không chỉ là tạo danh sách thẻ và scenario, mà là xây dựng một hệ thống dữ liệu có logic để game vận hành hợp lý. Tôi cần đảm bảo dữ liệu đủ đa dạng để tạo chiều sâu cho gameplay, cấu trúc dữ liệu đủ rõ ràng, và các quy tắc đủ nhất quán để mỗi scenario trong game đều có 1 bộ card phù hợp. Vì vậy, tôi tổ chức dữ liệu thành 24 scenario, 42 active cards và 10 reaction cards, chia theo nhóm màu, nhóm chiến lược và điều kiện phản ứng khẩn cấp. Nhờ đó, sản phẩm có được phần gameplay mang tính quyết định và chiến lược, nơi người chơi phải cân nhắc giữa tăng trưởng, niềm tin, rủi ro pháp lý, runway và khả năng gọi vốn.

Ngoài phần thiết kế dữ liệu gameplay và logic card/scenario, tôi cũng tham gia với vai trò Game Tester cho sản phẩm cuối cùng. Cụ thể, tôi kiểm thử các luồng vận hành chính của game như tạo phòng, submit project, submit deck, bắt đầu phase, chơi card, dùng Mulligan, kích hoạt reaction card, xử lý bankruptcy, End Game, Reset Game và kiểm tra khả năng lưu dữ liệu sau khi restart Flask server. Việc tham gia testing giúp tôi không chỉ kiểm tra phần logic do mình xây dựng, mà còn đảm bảo các phần của nhóm sau khi tích hợp có thể vận hành đúng trong một luồng game hoàn chỉnh.

**2\. Dấu ấn cá nhân trong sản phẩm**

Dấu ấn cá nhân rõ nhất của tôi trong sản phẩm là việc tôi xây dựng phần nền cho gameplay: hệ thống scenario, active card, reaction card và logic kết nối giữa tình huống với lựa chọn của người chơi. Tôi không chỉ tạo ra dữ liệu để game hiển thị, mà cố gắng thiết kế một hệ thống ra quyết định có logic, trong đó mỗi phase đều có bối cảnh, mỗi card đều có vai trò, và mỗi lựa chọn đều tạo ra tác động cụ thể đến startup.

Trước hết, tôi xây dựng bộ 24 scenario được chia thành 4 nhóm: Market, Internal, External và Regulatory. Các scenario được thiết kế dựa trên những tình huống gần với thực tế vận hành startup như lãi suất tăng, thị trường gọi vốn chậm lại, chi phí vận hành vượt ngân sách, sự cố bảo mật dữ liệu, tin đồn truyền thông tiêu cực, nhà cung cấp giao hàng chậm hoặc áp lực từ cơ quan quản lý. Nhờ vậy, game không bị lặp lại qua từng phase, mà luôn có những biến động khác nhau buộc người chơi phải điều chỉnh chiến lược.

Dấu ấn của tôi cũng thể hiện ở bộ 42 active cards được chia thành 3 nhóm chiến lược: Market Momentum, Resilience & Trust và Capital & Governance. Việc chia nhóm này giúp gameplay không chỉ xoay quanh tăng trưởng, mà còn yêu cầu người chơi cân bằng giữa mở rộng thị trường, bảo vệ niềm tin, kiểm soát rủi ro và gọi vốn. Mỗi card đều có cost và effect riêng, nên card không chỉ là một hành động cộng điểm đơn giản, mà đại diện cho một quyết định kinh doanh cụ thể. Khi thiết kế card, tôi cố gắng tạo sự phân hóa rõ giữa các mức energy cost. Thẻ cost 1 thường là hành động nhỏ, nhanh và tác động nhẹ; thẻ cost 2 là hành động có quy mô trung bình, xử lý một vấn đề cụ thể rõ hơn; còn thẻ cost 3 là quyết định lớn, có tác động mạnh nhưng đi kèm đánh đổi. Điều này giúp người chơi không thể chỉ chọn thẻ tốn nhiều energy vì nghĩ rằng sẽ được cộng nhiều điểm hơn, mà phải cân nhắc xem lợi ích của card có đáng với chi phí, rủi ro hoặc tác động phụ hay không.

Phần reaction card cũng là một dấu ấn quan trọng của tôi trong sản phẩm. Tôi thiết kế lại bộ reaction card theo hướng tập trung vào các tình huống cứu nguy thật sự, đặc biệt là các vấn đề liên quan đến runway thấp, tiền mặt còn lại ít, monthly burn quá cao, cash ratio suy giảm và áp lực nhà đầu tư rút vốn. Các reaction card chỉ được kích hoạt khi startup rơi vào trạng thái nguy hiểm hoặc có tín hiệu rõ ràng cho thấy sắp gặp khủng hoảng. Nhờ vậy, reaction card giữ đúng vai trò là công cụ cứu nguy có điều kiện, chứ không phải một loại thẻ hỗ trợ thông thường mà người chơi có thể dùng bất cứ lúc nào.

Một điểm khác thể hiện dấu ấn cá nhân của tôi là hệ thống card-matching logic. Tôi xây dựng hàm card_matches_scenario() giúp xác định card nào thật sự phù hợp với tình huống hiện tại dựa trên điểm giao giữa tags của scenario và counters của card.

Bên cạnh đó, tôi xây dựng logic rút bài theo hướng có chiến lược hơn. Thay vì phát bài hoàn toàn ngẫu nhiên, hệ thống có thể ưu tiên những card liên quan đến scenario hiện tại và nhóm thẻ chính thông qua primary_group. Hàm draw_hand_with_cost_ladder() giúp hand của người chơi có nhiều mức phản ứng khác nhau, từ lựa chọn nhỏ đến lựa chọn mạnh hơn. Điều này làm cho game có cảm giác phản hồi theo tình huống, thay vì người chơi nhận bài ngẫu nhiên và không liên quan đến vấn đề đang xảy ra.

Tóm lại, dấu ấn cá nhân của tôi nằm ở việc biến phần dữ liệu scenario và card thành một hệ thống gameplay có logic. Scenario tạo áp lực, card tạo lựa chọn, reaction card tạo cơ chế cứu nguy, còn tag matching và logic rút bài giúp các phần này kết nối với nhau. Nhờ đó, sản phẩm cuối cùng không chỉ là một game chọn thẻ đơn giản, mà là một mô phỏng nhỏ về quá trình vận hành startup, nơi người chơi phải cân nhắc giữa tăng trưởng, chi phí, niềm tin, gọi vốn, rủi ro và khả năng sống sót.

**3\. Những việc đã thực sự làm**

Các công việc tôi thực sự làm không phải chỉ là “viết code”, mà là xây một hệ thống gameplay hoàn chỉnh từ dữ liệu, quy tắc cho đến kiểm tra. Cụ thể, tôi đã làm những phần sau:

3.1. Xây dựng hệ thống scenario cho game

Tôi xây dựng bộ 24 scenario cho game và chia đều thành 4 nhóm Market, Internal, External, Regulatory, mỗi nhóm 6 tình huống. Mỗi scenario đều có id, name, desc, cat, tags, delta. Điều này giúp game có nguồn biến động đủ đa dạng để phản ánh nhiều loại rủi ro và cơ hội mà một startup có thể gặp.

Ví dụ:

{"id": 1, "name": "Market Liquidity Improves and Capital Becomes Easier to Raise", "cat": "Market", "tags": \["market_opportunity", "capital_availability"\], "delta": {"price": 0.04, "hype": 10, "funding_boost_percent": 3}},

Các scenario được thiết kế để tạo ra áp lực thật cho người chơi trong từng phase. Với delta của scenario, tôi thiết kế các tình huống xấu làm giảm các chỉ số quan trọng như hype, trust_all, runway, funding_boost_percent, transparency hoặc làm tăng reg_risk và cogs. Do đó, nếu người chơi bỏ qua việc chọn card hoặc không phản ứng đúng với tình huống, startup sẽ dần yếu đi theo thời gian. Điều này giúp gameplay có áp lực thật và người chơi không thể “hack game” bằng cách không chọn card để đạt điểm cao.

Các scenario cũng được xây dựng dựa trên những tình huống gần với thực tế vận hành startup, ví dụ thị trường gọi vốn chậm lại, lãi suất tăng, nhu cầu khách hàng giảm, chi phí vận hành vượt ngân sách, sản phẩm bị phàn nàn, sự cố bảo mật dữ liệu, tin đồn truyền thông tiêu cực, nhà cung cấp giao hàng chậm hoặc áp lực từ cơ quan quản lý. Nhờ vậy, mỗi phase trong game không chỉ là một lượt chơi ngẫu nhiên, mà giống như một tình huống kinh doanh mà người chơi phải xử lý.

3.2. Xây dựng hệ thống active card

Tôi thiết kế bộ 42 active cards và chia thành 3 nhóm chiến lược: Market Momentum màu đỏ, Resilience & Trust màu xanh lá, và Capital & Governance màu tím. Mỗi nhóm có 14 card và được gán tự động bằng prefix của id: các card bắt đầu bằng A thuộc nhóm đỏ, các card bắt đầu bằng D thuộc nhóm xanh lá, còn các card bắt đầu bằng C thuộc nhóm tím.

Việc chia nhóm này giúp game không bị nghiêng hẳn về tăng trưởng, cũng không bị nghiêng hẳn về compliance hay fundraising, mà buộc người chơi phải cân bằng giữa mở rộng, phòng thủ và gọi vốn. Nhóm Market Momentum tập trung vào các hành động tạo tăng trưởng, tăng độ chú ý và cải thiện nhu cầu thị trường. Nhóm Resilience & Trust tập trung vào việc phục hồi niềm tin, xử lý rủi ro vận hành, bảo mật, pháp lý và minh bạch. Nhóm Capital & Governance tập trung vào gọi vốn, quản trị, runway, investor confidence và khả năng sống sót tài chính.

Mỗi card đều có cấu trúc rõ ràng gồm id, name, cost, type, desc, counters và effect. Điều này giúp card không chỉ là nội dung hiển thị trên giao diện, mà còn là một hành động chiến lược có tác động cụ thể lên trạng thái của startup.

Ví dụ:

{"id": "A1", "name": "Low-Budget Target Ads", "cost": 1, "type": "red", "desc": "Run a small paid ad test to increase demand and visibility.", "counters": \["demand", "marketing_eff", "visibility"\], "effect": {"hype": 6, "visibility": 5, "cost_percent": 1}},

3.3. Cân bằng effect của card theo mức energy cost

Tôi trực tiếp tham gia thiết kế và cân bằng effect của card theo ba mức energy cost để tạo sự khác biệt rõ ràng về quy mô hành động, mức độ tác động và rủi ro đi kèm.

Thẻ cost 1 đại diện cho các hành động nhỏ, nhanh và ít tốn tài nguyên. Đây thường là những việc startup có thể làm ngay trong ngắn hạn, như chạy quảng cáo nhỏ, đăng bài truyền thông, cập nhật cộng đồng, trả lời phàn nàn khách hàng hoặc cắt giảm một phần chi phí không cần thiết. Vì quy mô nhỏ nên effect của nhóm này chỉ cải thiện nhẹ một vài chỉ số, ví dụ tăng nhẹ hype, visibility, trust_all, transparency hoặc giảm nhẹ cogs. Nhóm thẻ này phù hợp để xử lý tình huống nhẹ hoặc tạo cải thiện ban đầu, nhưng không đủ mạnh để đảo ngược một khủng hoảng lớn.

Thẻ cost 2 đại diện cho các hành động có quy mô trung bình, cần nhiều công sức và kế hoạch hơn. Đây là các hoạt động như chiến dịch marketing rõ ràng hơn, cải thiện funnel, rà soát bảo mật, chuẩn bị tài liệu pháp lý, xây dựng kế hoạch vốn lưu động hoặc làm lại dự báo runway. Effect của nhóm này mạnh hơn cost 1 vì nó thường xử lý trực tiếp một vấn đề cụ thể, chẳng hạn tăng đáng kể transparency, trust_all, funding_boost_percent, giảm reg_risk, giảm cogs, hoặc kéo dài runway thêm một mức vừa phải, tuy nhiên player cũng sẽ tốn 1 lượng tài nguyên nhất định khi sử dụng nhóm thẻ này. Nhóm cost 2 là lựa chọn cân bằng giữa hiệu quả và chi phí, phù hợp khi người chơi muốn xử lý vấn đề nghiêm túc nhưng chưa cần dùng đến hành động lớn.

Thẻ cost 3 đại diện cho các quyết định lớn, có tính chiến lược và ảnh hưởng mạnh đến hướng đi của startup. Đây có thể là chiến dịch mở rộng quy mô lớn, tái định vị thương hiệu, gọi vốn khẩn cấp, lập quỹ dự phòng, xử lý sự cố an ninh mạng hoặc hợp tác đầu tư chiến lược. Vì quy mô lớn nên effect của cost 3 thường tăng mạnh các chỉ số như hype, visibility, funding_boost_percent, trust_all, whale_trust, security hoặc runway. Tuy nhiên, nhóm này phải có trade-off để tránh mất cân bằng, ví dụ tăng cost_percent (player sẽ tốn nhiều chi phí để thực hiện những hành động lớn này), do đó sẽ làm giảm runway, bên cạnh đó, 1 số thẻ cũng làm giảm trust_all, giảm hype hoặc làm giảm sức hấp dẫn gọi vốn trong ngắn hạn. Điều này khiến người chơi không thể chỉ chọn thẻ mạnh nhất, mà phải cân nhắc xem lợi ích lớn đó có đáng với chi phí và rủi ro đi kèm hay không.

Tóm lại, việc chia ra ba mức cost này giúp gameplay có logic hơn. Nhờ vậy, người chơi phải lựa chọn theo tình trạng thật của startup, thay vì chỉ tối ưu điểm cộng trên từng lá bài.

3.4. Thiết kế cách kết nối scenario và card

Sau khi xây dựng riêng hệ thống scenario và hệ thống card, tôi thiết kế phần kết nối giữa hai phần này thông qua tags của scenario và counters của card. Mục tiêu là đảm bảo mỗi scenario đều có ít nhất một hướng phản ứng phù hợp, thay vì để người chơi gặp tình huống nhưng lại nhận các card không liên quan.

Tôi thiết kế hệ thống tags cho scenario để mô tả loại áp lực mà scenario tạo ra cho startup. Ví dụ, scenario liên quan đến thị trường xấu sẽ có các tag như market_down, funding, runway; scenario về chi phí sẽ có cost, runway, supply; scenario về pháp lý sẽ có regulatory, legal, disclosure_pressure; scenario về sản phẩm hoặc truyền thông sẽ có product, reputation, visibility hoặc demand.

Song song với đó, tôi gắn bộ counters tương ứng cho từng card để mô tả loại vấn đề mà card có thể xử lý. Ví dụ, các card marketing sẽ counter những vấn đề liên quan đến demand, visibility, competition; các card phòng thủ sẽ counter reputation, security, regulatory; còn các card vốn và governance sẽ counter funding, capital_availability, investor_confidence, funding_readiness. Nhờ vậy, mỗi card không chỉ là một hành động độc lập, mà có vai trò rõ ràng trong việc phản ứng với một nhóm tình huống cụ thể.

Tôi cũng viết cơ chế chuẩn hóa tag bằng TAG_ALIASES. Cụ thể, các tag như demand, price, cost, runway, funding, transparency được chuẩn hóa thành demand_pressure, price_pressure, cost_pressure, runway_pressure, funding_pressure, disclosure_pressure. Nhờ vậy, tôi tránh được việc scenario và card dùng hai cách gọi khác nhau cho cùng một vấn đề, và giảm nguy cơ mismatch trong logic chọn thẻ.

Về logic, một card được xem là phù hợp khi tags của scenario và counters của card có ít nhất một điểm giao nhau sau khi được chuẩn hóa. Điều này giúp quá trình rút bài không phải random hoàn toàn, mà có định hướng theo vấn đề người chơi đang gặp. Ví dụ, nếu scenario gây áp lực về runway và funding, hệ thống sẽ ưu tiên các card có khả năng xử lý runway hoặc funding; nếu scenario liên quan đến security hoặc regulatory, hệ thống sẽ ưu tiên các card xử lý bảo mật, compliance hoặc minh bạch.

Phần này giúp hạn chế lỗi gameplay quan trọng: không có card phù hợp để đánh, khiến người chơi bị động hoàn toàn trước scenario. Vì vậy, bằng cách thiết kế tags, counters, chuẩn hóa tag và logic matching, tôi giúp gameplay công bằng hơn.

3.5. Thiết kế cơ chế ưu tiên nhóm thẻ và rút bài

Ngoài tag/counter, tôi còn dùng thêm SCENARIO_PRIMARY_GROUP để xác định nhóm thẻ chính nên được ưu tiên cho từng scenario. Ví dụ, scenario thiên về tăng trưởng hoặc demand sẽ ưu tiên nhóm card Market Momentum; scenario liên quan đến rủi ro vận hành, pháp lý hoặc niềm tin sẽ ưu tiên nhóm card Resilience & Trust; còn scenario liên quan đến gọi vốn, runway hoặc investor confidence sẽ ưu tiên nhóm card Capital & Governance. Cách này giúp hand của người chơi không bị phát ngẫu nhiên theo kiểu “có gì lấy nấy”, mà vẫn bám sát loại vấn đề đang xảy ra trong game.

Tôi thiết kế logic rút bài theo hướng vừa đảm bảo tính phù hợp, vừa giữ sự đa dạng. Hàm rút bài sẽ ưu tiên chọn card thuộc primary_group của scenario và có counters khớp với tags của scenario. Đồng thời, hệ thống cố gắng lấy đủ các mức cost 1, cost 2 và cost 3 để người chơi có cả lựa chọn nhỏ, lựa chọn trung bình và lựa chọn mạnh. Nhờ vậy, khi gặp một scenario, người chơi không chỉ có card liên quan để đánh, mà còn có nhiều mức phản ứng khác nhau tùy theo chiến lược và tài nguyên còn lại.

Tôi viết hai hàm rút bài chiến lược. draw_hand_with_cost_ladder() cố gắng rút một hand có đủ cost 1, cost 2, cost 3 và ưu tiên primary_group của scenario trước; còn draw_hand_no_duplicate_color_cost() hạn chế việc các card có cùng mức cost ở trong cùng 1 group xuất hiện. Nhờ vậy, hand của người chơi có nhiều lựa chọn hơn và không bị “toàn thẻ yếu” hoặc “toàn thẻ cùng màu”.

3.6. Thiết kế hệ thống reaction card

Tôi thiết kế lại hệ thống reaction card theo hướng tập trung vào các tình huống khẩn cấp thật sự liên quan đến khả năng sống sót của startup, đặc biệt là các vấn đề về runway thấp, tiền mặt còn lại ít, monthly burn quá cao, cash ratio suy giảm và áp lực nhà đầu tư rút vốn.

Tôi đặt MAX_REACTION_CARDS_PER_GAME = 3 để giới hạn số lần người chơi có thể dùng reaction card trong một ván. Điều này giúp reaction card giữ đúng vai trò là công cụ cứu nguy có giới hạn, không trở thành một cơ chế để người chơi liên tục sửa sai hoặc thay thế chiến lược chính. Nhờ giới hạn này, người chơi vẫn phải quản lý startup cẩn thận trong các lượt bình thường, vì reaction card chỉ đóng vai trò hỗ trợ khi tình hình đã thật sự nghiêm trọng.

Tôi xây dựng bộ 7 reaction cards, trong đó mỗi thẻ đều có cấu trúc rõ ràng gồm id, name, cost, trigger, condition, desc, cost_percent và effect. Ví dụ:

{

&nbsp;       "id": "R1",

&nbsp;       "name": "Emergency Bridge Cash",

&nbsp;       "cost": 3,

&nbsp;       "trigger": "on_near_bankruptcy",

&nbsp;       "condition": {"metric": "runway", "operator": "<=", "value": 1},

&nbsp;       "desc": "Secure emergency bridge cash when the startup is almost out of runway.",

&nbsp;       "cost_percent": 2,

&nbsp;       "effect": {

&nbsp;           "runway": 2,

&nbsp;           "funding_boost_percent": 4,

&nbsp;           "trust_all": -4,

&nbsp;           "hype": -3,

&nbsp;       }

&nbsp;   },

Các reaction card được thiết kế xoay quanh các ngưỡng tài chính quan trọng của startup, ví dụ runway còn rất thấp, runway ở mức cảnh báo, monthly burn lớn hơn available cash, available cash không đủ che phủ hai tháng burn, cash ratio dưới 20%, cash ratio nằm trong vùng cảnh báo 20% - 30%, hoặc áp lực rút vốn của nhà đầu tư vượt 70%.

Tôi cân bằng effect của reaction card theo hướng có khả năng hỗ trợ người chơi thoát khỏi tình huống nguy hiểm, nhưng không hoàn toàn miễn phí. Các thẻ cứu nguy thường giúp tăng runway, giảm cogs, cải thiện một phần funding_boost_percent hoặc giảm áp lực rút vốn. Tuy nhiên, để giữ cân bằng, một số thẻ sẽ làm giảm hype, giảm trust_all và các thẻ sẽ đều phát sinh cost_percent. Điều này thể hiện rằng các quyết định khẩn cấp có thể giúp startup sống sót thêm, nhưng vẫn phải trả giá bằng chi phí, hình ảnh thị trường hoặc niềm tin của nhà đầu tư.

3.7. Kiểm tra dữ liệu trước khi tích hợp

Tôi viết hàm validate_master_data() để kiểm tra dữ liệu trước khi tích hợp vào app. Hàm này xác nhận tổng số scenario phải là 24, active cards là 42, reaction cards là 7, kiểm tra trùng ID, kiểm tra từng active card có đủ key bắt buộc, và kiểm tra phân bố group phải là {"red": 14, "green": 14, "purple": 14}. Đây là phần tôi thêm vào để giảm rủi ro lỗi dữ liệu và hỗ trợ demo ổn định hơn.

3.8. Tham gia kiểm thử sản phẩm cuối cùng

Ngoài việc xây dựng scenario, active card, reaction card, logic matching và logic rút bài, tôi còn tham gia kiểm thử sản phẩm cuối cùng với vai trò tester. Tôi xây dựng và thực hiện bảng test case để kiểm tra các luồng chính của game, bao gồm tạo phòng, submit project và deck, host chạy phase, chơi card, dùng Mulligan, kích hoạt reaction card, xử lý bankruptcy, End Game, Reset Game và kiểm tra lưu trữ dữ liệu.

Tôi kiểm thử cả trường hợp hoạt động bình thường và trường hợp lỗi. Ví dụ, tôi kiểm tra việc tạo phòng 2 người, người chơi submit project và deck, host bắt đầu phase, mỗi người chơi nhận 5 lá bài và scenario xuất hiện theo từng phase. Tôi cũng kiểm tra các lỗi như người chơi chưa submit deck nhưng host vẫn chạy phase, chọn quá số lượng card cho phép, chưa Ready nhưng host chạy phase, dùng Mulligan khi không đủ energy, hoặc tiếp tục thao tác khi đã bankrupt hoặc kết thúc.

Bên cạnh đó, tôi kiểm tra các tác động trong gameplay như energy giảm sau khi chơi card, card biến mất khỏi hand, các chỉ số như hype hoặc transparency thay đổi đúng theo effect, dự án bị đánh dấu bankrupt khi available_cash xuống 0, và reaction card chỉ kích hoạt khi thỏa điều kiện như runway thấp hoặc tình trạng tài chính nguy hiểm. Tôi cũng kiểm tra End Game, Reset Game, nhiều người chơi có scale khác nhau như S, M, L, và khả năng lưu trạng thái bằng SQLite sau khi restart Flask server.

Kết quả kiểm thử cho thấy các kịch bản chính đều đạt yêu cầu. Việc testing giúp nhóm xác nhận các phần gameplay logic, API, UI, dữ liệu card/scenario và cơ chế lưu trữ đã tích hợp ổn định hơn, từ đó giúp sản phẩm cuối cùng vận hành tốt hơn khi demo.

**4\. File, logic, dữ liệu và bằng chứng đóng góp**

Link commit

https://github.com/khanhhabao7/nhap-fintech/commits/main/app.py?author=nnm1012

**5\. Phần đóng góp đó kết nối thế nào với sản phẩm cuối cùng**

Phần tôi làm kết nối trực tiếp với sản phẩm cuối cùng vì đây là lớp dữ liệu và logic nền để các phần còn lại của game có thể vận hành.

Phần tôi làm có liên kết trực tiếp với phần của Phúc ở hai điểm chính: kiểm soát quá trình bắt đầu game và tính điểm kết quả. Trong giai đoạn chọn deck, phần code của Phúc kiểm tra người chơi đã tham gia đủ chưa, đã submit deck chưa và sau đó mới cho phép khởi tạo game. Bộ deck này được tạo từ ACTIVE_CARDS_FULL và REACTION_CARDS do tôi xây dựng, nên dữ liệu card của tôi là đầu vào cần thiết để quá trình chọn deck và bắt đầu game hoạt động đúng. Ngoài ra, scenario và card của tôi tạo ra các thay đổi lên trạng thái startup như hype, transparency, funding_progress, runway, security, etc. Các chỉ số này sau đó được phần calculate_metrics() và final_score() của Phúc sử dụng để tính hiệu quả vận hành và điểm cuối cùng. Vì vậy, phần tôi làm giúp hệ thống tính điểm không chỉ dựa trên dữ liệu ban đầu, mà phản ánh được cả quá trình người chơi ra quyết định, xử lý rủi ro và quản lý startup trong suốt game.

Phần scenario và hệ chỉ số tôi thiết kế cũng liên kết với Bot của Khanh. Sau khi scenario tác động đến các chỉ số như hype, transparency, visibility, funding_progress, security, reg_risk, available_cash hoặc runway, Bot sử dụng các chỉ số này để đánh giá độ hấp dẫn của từng startup. Vì vậy, scenario không chỉ ảnh hưởng đến người chơi, mà còn ảnh hưởng đến hành vi của bot đầu tư hoặc rút vốn.

Phần active card và reaction card tôi xây dựng được kết nối trực tiếp với API routing của Jin. Các route như submit_deck, auto_select_deck, card_lists, play_card và use_reaction đều cần truy cập vào ACTIVE_CARDS_FULL và REACTION_CARDS để trả danh sách thẻ, kiểm tra index thẻ, lưu deck người chơi đã chọn và xử lý khi người chơi dùng card. Nhờ có cấu trúc card đầy đủ gồm id, name, cost, type, desc, counters, condition và effect, API có thể validate lựa chọn của người chơi và lưu đúng dữ liệu vào trạng thái game.

Phần tôi làm cũng kết nối trực tiếp với giao diện của Dương. Các màn hình như chọn deck, hand của người chơi và bảng reaction card đều cần dữ liệu từ card dictionaries để hiển thị tên thẻ, mô tả, cost, nhóm thẻ và hiệu ứng. Nếu dữ liệu card không được tổ chức rõ ràng, giao diện sẽ khó hiển thị nhất quán. Vì vậy, việc tôi chuẩn hóa cấu trúc card giúp frontend có thể render nội dung dễ hơn và người chơi cũng dễ hiểu hơn khi nhìn vào từng lá bài.

Ngoài ra, các hàm rút bài như draw_hand_with_cost_ladder() và draw_hand_no_duplicate_color_cost() giúp phần gameplay khi chạy thực tế có tính liên kết hơn. Thay vì phát bài hoàn toàn ngẫu nhiên, logic rút bài có thể ưu tiên các card liên quan đến scenario hiện tại, đồng thời hạn chế việc hand bị trùng cùng màu hoặc cùng mức energy cost. Điều này giúp người chơi khi bước vào từng phase có nhiều lựa chọn hợp lý hơn, ví dụ có thẻ nhỏ để phản ứng nhanh, thẻ trung bình để xử lý vấn đề rõ ràng và thẻ mạnh để đưa ra quyết định lớn.

Thêm vào đó, phần validate_master_data() kết nối với sản phẩm cuối cùng ở vai trò kiểm tra chất lượng dữ liệu. Khi game có nhiều scenario và card, dữ liệu rất dễ bị thiếu key, trùng ID hoặc sai số lượng nhóm. Hàm validate giúp kiểm tra trước khi tích hợp, giảm khả năng lỗi khi chạy demo hoặc khi người chơi chọn deck. Nhờ đó, phần dữ liệu tôi xây dựng không chỉ dùng được trong nội dung game, mà còn hỗ trợ quá trình kiểm thử và ổn định sản phẩm.

Tóm lại, đóng góp của tôi liên kết với Game Core, Bot AI, API và UI, nên đóng vai trò như nền tảng dữ liệu và luật chơi để sản phẩm cuối cùng có thể vận hành thành một game hoàn chỉnh.

**6\. Điều cá nhân học được**

Qua phần việc này, tôi học được rằng thiết kế nội dung cho game không chỉ là nghĩ ra nhiều scenario và nhiều card, mà phải làm sao để từng nội dung đó có ý nghĩa trong gameplay. Khi xây dựng scenario và card, tôi phải nhìn cùng lúc từ hai góc độ: góc nhìn của người chơi và góc nhìn của hệ thống. Với người chơi, một scenario cần đủ thực tế để tạo cảm giác đang vận hành startup thật, còn một card cần đủ rõ để người chơi hiểu mình đang chọn hành động gì. Từ đó, tôi hiểu rằng nội dung game tốt không chỉ nằm ở phần mô tả hay tên thẻ, mà còn nằm ở việc nội dung đó có tạo ra quyết định hợp lý cho người chơi hay không.

Tôi cũng học được rằng thiết kế game là một quá trình phải chỉnh sửa nhiều lần. Ban đầu, có những card hoặc scenario nghe có vẻ hợp lý về mặt ý tưởng, nhưng khi đặt vào gameplay thì lại bị quá mạnh, quá yếu hoặc khó giải thích. Vì vậy, tôi phải điều chỉnh lại effect, delta, cost và cả nội dung mô tả để các thẻ có sự khác biệt rõ hơn giữa cost 1, cost 2 và cost 3. Qua đó, tôi nhận ra rằng một quyết định trong game không nên chỉ có lợi, mà cần có đánh đổi để người chơi phải cân nhắc. Đây là điều tôi học được nhiều nhất về cân bằng gameplay.

Về mặt cấu trúc dữ liệu, tôi học được tầm quan trọng của sự nhất quán. Khi scenario và card dùng các tag khác nhau cho cùng một ý nghĩa, ví dụ một bên dùng demand còn bên khác dùng demand_pressure, hệ thống matching có thể bị sai mà không báo lỗi rõ ràng. Việc xây dựng TAG_ALIASES, normalize_tag() và normalize_tags() giúp tôi hiểu rằng trong một project có nhiều dữ liệu và nhiều người cùng làm, cách đặt tên phải được chuẩn hóa từ đầu. Nếu không có quy ước chung, dữ liệu vẫn có thể nhìn đúng bằng mắt thường nhưng lại không kết nối được trong code.

Một bài học khác của tôi là dữ liệu gameplay không đứng riêng lẻ, mà ảnh hưởng đến nhiều phần khác trong sản phẩm. Scenario và card tôi xây dựng được Game Core dùng để chạy phase, API dùng để validate deck và xử lý card, Bot dùng các chỉ số sau khi scenario/card tác động để ra quyết định đầu tư hoặc rút vốn, còn UI dùng tên thẻ, mô tả, cost và effect để hiển thị cho người chơi. Vì vậy, khi tôi thay đổi một tag, một effect hoặc một cấu trúc card, thay đổi đó có thể ảnh hưởng đến nhiều module khác. Điều này giúp tôi hiểu rõ hơn tầm quan trọng của việc giữ dữ liệu ổn định và trao đổi với nhóm trước khi sửa các phần mà người khác đang phụ thuộc vào.

**7\. Khó khăn đã gặp và cách xử lý**

Khó khăn lớn nhất tôi gặp là làm sao để card xuất hiện hợp ngữ cảnh. Nếu game rút card hoàn toàn ngẫu nhiên, người chơi có thể gặp funding crisis nhưng lại nhận những lá chỉ có tác dụng marketing, và khi đó toàn bộ trải nghiệm sẽ trở nên vô lý. Tôi xử lý vấn đề này bằng cách thiết kế hệ tags cho scenario, counters cho card, rồi dùng card_matches_scenario() để kiểm tra phần giao nhau thực sự giữa scenario và card. Sau khi làm xong phần này, bộ thẻ mới bắt đầu khớp được với bộ scenario.

Khó khăn thứ hai là cân bằng độ mạnh của active card và reaction card, đặc biệt là phải tạo được sự phân hóa rõ ràng giữa các thẻ có mức energy cost khác nhau. Tôi không thể chỉ đặt cost cao hơn rồi cộng nhiều điểm hơn, vì như vậy người chơi sẽ có xu hướng chọn thẻ tốn nhiều energy nhất mà không cần suy nghĩ. Vì vậy, khi thiết kế card, tôi phải xác định trước mỗi mức cost đại diện cho loại hành động nào, rồi dựa vào đó để đặt tên thẻ, viết mô tả và gán effect tương ứng. Ví dụ, một thẻ gọi vốn khẩn cấp có thể giúp tăng funding_boost_percent và runway, nhưng cũng nên làm giảm trust_all hoặc hype vì nhà đầu tư có thể nhìn nhận startup đang gặp áp lực tài chính. Một thẻ marketing lớn có thể tăng mạnh hype và visibility, nhưng phải tốn chi phí hoặc làm giảm runway vì startup phải chi nhiều tiền để mở rộng. Nhờ cách cân bằng này, người chơi không thể chỉ nhìn thấy thẻ tốn nhiều energy là chọn ngay vì được cộng nhiều điểm. Thay vào đó, người chơi phải cân nhắc xem lợi ích của thẻ có đáng với chi phí và rủi ro đi kèm hay không. Đây là phần tôi thấy khó vì phải cân bằng cùng lúc giữa tính hấp dẫn của card, tính công bằng của game và sự hợp lý của từng effect trong bối cảnh vận hành startup.

Khó khăn thứ ba là đặt điều kiện kích hoạt cho reaction card sao cho thẻ chỉ xuất hiện trong tình huống thật sự khẩn cấp. Ban đầu, nếu reaction card chỉ dựa vào scenario hoặc điều kiện quá rộng, người chơi có thể kích hoạt thẻ cứu nguy quá dễ, khiến game mất cân bằng. Vì vậy, tôi phải xác định lại reaction card không phải là thẻ hỗ trợ thông thường, mà là cơ chế chỉ dùng khi startup đã rơi vào trạng thái nguy hiểm hoặc có tín hiệu rõ ràng cho thấy sắp gặp khủng hoảng. Để xử lý khó khăn này, trước hết tôi phải phân loại các trường hợp nào thật sự cần cứu nguy. Tôi chia thành hai nhóm chính: trường hợp gần phá sản và trường hợp có tín hiệu dẫn đến phá sản. Trường hợp gần phá sản là khi runway &lt;= 1, tức là startup gần như không còn thời gian để tiếp tục vận hành. Trường hợp có tín hiệu phá sản là khi runway = 2, monthly_burn &gt; available_cash, monthly_burn \* 2 > available_cash, cash_ratio < 0.2, hoặc áp lực rút vốn của nhà đầu tư quá cao. Những điều kiện này cho thấy startup chưa chắc đã phá sản ngay, nhưng nếu không xử lý thì rất dễ rơi vào khủng hoảng ở phase tiếp theo.

Sau khi xác định các tình huống cần cứu nguy, tôi mới đặt trigger và condition cho từng reaction card. Khó nhất là phải tránh việc các điều kiện bị trùng nhau quá nhiều. Ví dụ, nếu một startup có runway <= 1 thì rất có thể cũng thỏa các điều kiện về cash ratio thấp hoặc monthly burn cao. Nếu không phân biệt rõ mức độ nguy hiểm, hệ thống có thể hiện nhiều reaction card cùng lúc, làm người chơi có cơ hội dùng nhiều thẻ cứu nguy và khiến hiệu ứng phục hồi bị cộng dồn quá mạnh. Vì vậy, tôi phải thêm energy cost cho từng thẻ để người chơi không được chọn quá nhiều reaction card cho 1 phase, và thiết kế các điều kiện theo từng mức cảnh báo khác nhau: có thẻ dành cho cảnh báo sớm, có thẻ dành cho khủng hoảng tiền mặt, và có thẻ dành cho gần phá sản thật sự.

Nhờ cách xử lý này, reaction card giữ đúng vai trò là phao cứu sinh có điều kiện, chứ không phải công cụ cộng điểm thường xuyên. Người chơi chỉ có thể dùng reaction card khi startup thật sự có nguy cơ mất khả năng vận hành, đồng thời vẫn phải trả cost và chấp nhận trade-off. Đây là phần tôi thấy khó vì phải cân bằng giữa việc giúp người chơi có cơ hội phục hồi và việc giữ cho game vẫn có áp lực, có rủi ro và không quá dễ.

**8\. Lời nhắn cho sinh viên khóa sau**

Nếu sinh viên khóa sau tiếp tục phát triển phần này, tôi nghĩ điều quan trọng đầu tiên là hãy bắt đầu từ cấu trúc dữ liệu trước khi viết thêm code. Trước khi xây logic, cần xác định rõ hướng đi, ví dụ như một scenario phải có những trường nào, một card phải có những trường nào, các chỉ số nào được phép xuất hiện trong delta và effect, tag/counter được đặt theo quy tắc nào, và mỗi loại card sẽ dùng những giá trị nào. Nếu cấu trúc dữ liệu không rõ ngay từ đầu, càng về sau hệ thống càng dễ bị rối, vì mỗi người có thể đặt tên field hoặc tag theo một cách khác nhau.

Điều thứ hai là nội dung game nên bám vào bối cảnh thực tế, mỗi scenario nên bắt đầu từ một tình huống kinh doanh có thật hoặc gần với thực tế, ví dụ lãi suất tăng, nhà đầu tư giảm khẩu vị rủi ro, chi phí vận hành vượt ngân sách, nhà cung cấp giao hàng chậm, tin đồn tiêu cực trên truyền thông, hoặc cơ quan quản lý yêu cầu bổ sung tài liệu. Sau đó mới xác định tình huống đó sẽ ảnh hưởng đến chỉ số nào trong game. Tương tự, khi thêm card mới thì nên đặt ra câu hỏi “card này xử lý vấn đề gì, tác động đến chỉ số nào, và có đánh đổi gì không”. Một card marketing có thể tăng hype hoặc visibility, nhưng có thể tốn thêm chi phí. Một card gọi vốn có thể tăng funding_boost_percent hoặc runway, nhưng có thể làm giảm trust_all nếu đó là phương án khẩn cấp. Một card xử lý khủng hoảng có thể tăng transparency hoặc giảm rủi ro, nhưng không nhất thiết tạo tăng trưởng ngay.

Cuối cùng, tôi nghĩ khi phát triển tiếp phần gameplay logic, nên luôn giữ sự liên kết giữa scenario - card - effect - người chơi. Scenario phải tạo ra một áp lực rõ ràng, card phải là một phản ứng hợp lý với áp lực đó, effect phải phản ánh đúng tác động của hành động, và người chơi phải hiểu được vì sao lựa chọn của mình tạo ra kết quả như vậy. Nếu giữ được nguyên tắc này, game sẽ mang giá trị học tập cao hơn.

Tôi mong game sẽ tiếp tục được update và phát triển thêm trong các phiên bản sau, đặc biệt là ở phần mở rộng scenario, bổ sung card mới và cân bằng lại các chỉ số sau khi có thêm người chơi thử nghiệm.