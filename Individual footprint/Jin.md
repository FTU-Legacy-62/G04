
|<p>**INDIVIDUAL FOOTPRINT**</p><p>**FUN(D) RAISING**</p><p>When you have funds you have fun!</p>|
| :-: |



**Foreign Trade University  |  Class NHA408E(2526-2)GD2.01**

**Instructor: Assoc. Prof. PhD. Phan Tran Trung Dung**

**Hanoi, June 2026**



|**Member**|**Student ID**|**Role**|
| :-: | :-: | :-: |
|**Kim Hye Jin**|2312380803|Team Leader · API Architect · System Integrator|


**Individual Footprint of Jin**

**Role:** *Team Leader | Flask Backend API & Routing | System Integration (Backend ↔ Frontend)*

**MỤC LỤC**

[1. Vai trò trong dự án	2](#_toc232080508)

[2. Dấu ấn cá nhân trong sản phẩm	2](#_toc232080509)

[3. Những gì tôi thực sự đã làm	3](#_toc232080510)

[4. Các tập tin, tính năng và thành phần được đóng góp	5](#_toc232080511)

[4.1. HỆ THỐNG API	5](#_toc232080512)

[4.2. Thành phần lưu trữ bền vững	9](#_toc232080513)

[4.3. Hàm tiện ích chuẩn hóa và xử lý lỗi	10](#_toc232080514)

[4.4. Kết nối logic game giữa các module	15](#_toc232080515)

[4.5. Kiểm thử	15](#_toc232080516)

[5. Bằng chứng về sự đóng góp	17](#_toc232080517)

[6. Công việc của tôi liên quan như thế nào đến sản phẩm cuối cùng?	18](#_toc232080518)

[7. Những điều tôi đã học được	18](#_toc232080519)

[8. Những thách thức và cách tôi vượt qua chúng	19](#_toc232080520)

[Thách thức 1: Lỗi không khớp kiểu dữ liệu khóa JSON	19](#_toc232080521)

[Thách thức 2: Phối hợp bốn phong cách lập trình khác nhau	19](#_toc232080522)

[Thách thức 3: Dùng AI để debug: một con dao hai lưỡi	19](#_toc232080525)

[9. Lời nhắn nhủ dành cho các sinh viên tương lai	20](#_toc232080523)

[10. Kết luận	20](#_toc232080524)



## <a name="_z74kdjhgxx2r"></a><a name="_toc232080508"></a>**1. Vai trò trong dự án**
Fun(d) Raising là một trò chơi mô phỏng gây quỹ khởi nghiệp dành cho nhiều người chơi (từ 2 đến 10 người). Mỗi người chơi xây dựng một dự án khởi nghiệp với các chỉ số tài chính, chọn bộ bài chiến lược (gồm thẻ tấn công, phòng thủ và thẻ phản ứng), rồi trải qua nhiều vòng (phase) dưới sự tác động của các sự kiện ngẫu nhiên và quyết định đầu tư của 200 bot nhà đầu tư với bốn loại tính cách khác nhau. Người dẫn trò (host) điều khiển nhịp độ trò chơi. Mục tiêu cuối cùng là đạt được số điểm cao nhất dựa trên tiến độ gọi vốn, tốc độ, ROI kỳ vọng và mức độ minh bạch.

Trong dự án này, tôi đảm nhận hai trách nhiệm lớn:

1. **Trưởng nhóm:** Điều phối, lập kế hoạch, giải quyết xung đột, đảm bảo các thành viên làm việc ăn ý và đúng tiến độ

1. **Kiến trúc sư API và Tích hợp hệ thống:** Xây dựng toàn bộ lớp backend Flask, định tuyến API, quản lý trạng thái phòng bền vững bằng SQLite, và kết nối các mô-đun riêng lẻ (dữ liệu của Minh, logic game của Phúc, bot của Khanh, giao diện của Dương) thành một ứng dụng thống nhất

Ban đầu, bốn thành viên phát triển bốn phần độc lập. Nếu không có một phần tích hợp trung tâm, chúng sẽ không thể giao tiếp với nhau. Công việc của tôi là xây dựng cầu nối, biến những mảnh ghép rời rạc thành một trò chơi hoàn chỉnh, nơi người chơi chỉ cần nhấp chuột và tận hưởng.

## <a name="_toc232080509"></a>**2. Dấu ấn cá nhân trong sản phẩm**
Tôi không phải là người tạo ra những phần dễ nhìn thấy nhất của trò chơi: tôi không thiết kế giao diện HTML/CSS (đó là công sức của Dương), cũng không xây dựng các thuật toán mô phỏng cốt lõi như caculate\_metrics hay bot\_attractiveness (của Phúc và Khanh). Tôi cũng không tự mình viết toàn bộ 24 scenarios hay 49 thẻ bài (đây là dữ liệu của Minh). Dấu ấn của tôi nằm ở chỗ kết nối tất cả chúng lại với nhau.

Phần việc của tôi gần như vô hình đối với người chơi, nhưng chính sự vô hình đó lại là sự thành công đối với tôi bởi nó chứng minh rằng tôi đã hoàn hảo trong việc khiến con game trở nên mượt trong trải nghiệm. Người chơi sẽ không bao giờ thấy trực tiếp các tuyến API hay cơ sở dữ liệu SQLite nhưng nếu thiếu đi chúng, trò chơi sẽ không thể khởi động, không thể lưu trạng thái, không thể xử lý các yêu cầu đồng thời. Điều khiến tôi tự hào nhất là khi một người chơi có thể trải qua toàn bộ hành trình một cách tự nhiên, không vấp váp:

+ Nhập link vào trình duyệt => thấy form nhập dự án
+ Điền số liệu => gửi đi => chuyển sang màn hình chọn bài
+ Chọn 22 thẻ Active và tối đa 3 thẻ Reaction => gửi Deck
+ Mỗi phase, người chơi thấy 5 lá bài trên tay, chơi bài, dùng Mulligan, kích reaction khi có điều kiện
+ Host nhấn “Run Phase” qua từng vòng
+ Kết thúc game, điểm số được hiển thị, bảng xếp hạng hiện ra

Tất cả những bước đó, từ đầu đến cuối, đều được chạy qua các API do tôi viết và trạng thái phòng do tôi quản lý. Giá trị lớn nhất của tôi không phải là một tính năng riêng lẻ, mà là sự tích hợp liền mạch, điều biến bốn module viết riêng rẽ thành một sản phẩm duy nhất có thể chạy từ đầu đến cuối mà không cần bất kỳ sự can thiệp thủ công nào.

## <a name="_toc232080510"></a>**3. Những gì tôi thực sự đã làm**
Trong dự án này, tôi không chỉ viết toàn bộ backend Flask mà còn là người kết nối các module rời rạc của các thành viên thành một hệ thống toàn chỉnh. Cụ thể:


|**Mảng công việc**|**Mô tả**|
| :-: | :-: |
|Hệ thống API|Xây dựng 23 route RESTful (5 route view + 18 route API) phục vụ host, người chơi và tiện ích. Mỗi API có xác thực input, xử lý logic, trả về JSON.|
|Lưu trữ bền vững|Thiết kế lớp SqliteRoomManager và hook save\_rooms để lưu trạng thái phòng vào SQLite, không mất dữ liệu khi restart server.|
|Hàm tiện ích chuẩn hóa|Viết 8 hàm xử lý lỗi JSON, chuẩn hóa cấu trúc phòng, gộp hành động bot, khởi tạo game, đánh giá điều kiện reaction.|
|Kết nối module Minh|Tích hợp dữ liệu thẻ (ACTIVE\_CARDS\_FULL, REACTION\_CARDS), kịch bản (SCENARIOS), hàm vẽ bài (draw\_hand\_no\_duplicate\_color\_cost) vào API.|
|Kết nối module Phúc|Gọi calculate\_metrics và final\_score trong các API trạng thái và run\_phase để tính chỉ số, điểm số.|
|Kết nối module Khánh|Gọi process\_phase trong run\_phase, cung cấp hàm get\_bot\_memory để Khánh sử dụng.|
|Kết nối giao diện Dương|Trả về template host.html, play.html và định dạng JSON phù hợp với frontend.|
|Kết nối chéo giữa các module|Thực hiện chuỗi xử lý trong run\_phase (Minh → Phúc → Khánh → Minh), viết evaluate\_condition dùng chung dữ liệu Minh và metrics Phúc.|
|Xử lý lỗi toàn cục|Bắt mọi ngoại lệ, trả về JSON lỗi thay vì stack trace HTML.|
|Tester|Kiểm thử thủ công toàn bộ luồng, chụp ảnh màn hình demo.|


## <a name="_toc232080511"></a>**4. Các tập tin, tính năng và thành phần được đóng góp**
### <a name="_sqy9hk500g7e"></a><a name="_toc232080512"></a>**4.1. Hệ thống API**

|**API (Tên - Đường dẫn)**|**Method**|**Input**|**Output**|**Mục đích & cách chạy**|**Code (dòng đầu – dòng cuối)**|
| :-: | :-: | :-: | :-: | :-: | :-: |
|Trang host – /|GET|không|host.html|Render host dashboard.|<p>@app.route('/')</p><p>def index(): return render\_template('host.html')</p>|
|Trang người chơi – /play/<room\_id>/<player\_index>|GET|room\_id, player\_index|play.html hoặc lỗi|Kiểm tra phòng, render play.html.|<p>@app.route('/play/<room\_id>/<int:player\_index>')</p><p>def play\_page(...): ... return render\_template('play.html', ...)</p>|
|Tạo phòng – /api/create\_room|POST|{"num\_players": 2-10, "room\_name": "..."}|{"room\_id": "...", "join\_links": [...], "status": "waiting\_for\_projects"}|Sinh UUID, khởi tạo dict phòng, sinh link join.|<p>@app.route('/api/create\_room', methods=['POST'])</p><p>def create\_room(): ...</p>|
|Tạo phòng (dashboard) – /api/rooms|POST|{"name": "...", "maxPlayers": 4}|{"id": "...", "name": "...", "maxPlayers": 4, "joinLinks": [...]}|Giống trên nhưng trả cấu trúc cho dashboard mới.|<p>@app.route('/api/rooms', methods=['POST'])</p><p>def api\_create\_room(): ...</p>|
|Force chọn deck – /api/start\_deck\_phase|POST|{"room\_id": "..."}|{"ok": true, "message": "..."}|Chuyển phòng từ waiting → choosing\_deck.|<p>@app.route('/api/start\_deck\_phase', methods=['POST'])</p><p>def start\_deck\_phase(): ...</p>|
|Chạy phase – /api/run\_phase|POST|{"room\_id": "..."}|{"ended": bool, "phase": int, "logs": [...], "game\_ended": bool}|Xử lý khởi tạo game hoặc thực thi phase (phức tạp nhất).|<p>@app.route('/api/run\_phase', methods=['POST'])</p><p>def run\_phase(): ... (code dài, xem trong tệp)</p>|
|Trạng thái host – /api/host\_state|GET|query ?room\_id=...|{"status":"...","phase":int,"rankings":[...],"logs":[...]}|Bảng xếp hạng, logs. Gọi calculate\_metrics (Phúc).|<p>@app.route('/api/host\_state', methods=['GET'])</p><p>def host\_state(): ...</p>|
|Chi tiết phòng – /api/rooms/<room\_id>|GET|room\_id|{"name":"...","maxPlayers":int,"phaseDetails":[...],"players":[...]}|Lấy thông tin + lịch sử phase.|<p>@app.route('/api/rooms/<room\_id>', methods=['GET'])</p><p>def api\_get\_room(room\_id): ...</p>|
|Next phase – /api/rooms/<room\_id>/next-phase|POST|room\_id|{"success": true, "phase": int}|Tăng phase thủ công (debug).|<p>@app.route('/api/rooms/<room\_id>/next-phase', methods=['POST'])</p><p>def api\_next\_phase(room\_id): ...</p>|
|Random event – /api/rooms/<room\_id>/random-event|POST|room\_id|{"success": true, "event": "..."}|Áp dụng kịch bản ngẫu nhiên từ SCENARIOS.|<p>@app.route('/api/rooms/<room\_id>/random-event', methods=['POST'])</p><p>def api\_random\_event(room\_id): ...</p>|
|Reset phase – /api/rooms/<room\_id>/reset-phase|POST|room\_id|{"success": true, "phase": int}|Giảm phase (debug).|<p>@app.route('/api/rooms/<room\_id>/reset-phase', methods=['POST'])</p><p>def api\_reset\_phase(room\_id): ...</p>|
|Kết thúc game – /api/rooms/<room\_id>/end|POST|room\_id|{"success": true}|Đánh dấu game ended.|<p>@app.route('/api/rooms/<room\_id>/end', methods=['POST'])</p><p>def api\_end\_game(room\_id): ...</p>|
|Reset game – /api/rooms/<room\_id>/reset|POST|room\_id|{"success": true}|Reset toàn bộ dữ liệu game.|<p>@app.route('/api/rooms/<room\_id>/reset', methods=['POST'])</p><p>def api\_reset\_game(room\_id): ...</p>|
|Gửi dự án – /api/submit\_project|POST|{"room\_id":"...","player\_index":0,"project":{...}}|{"ok":true,"submitted\_count":int,...}|Lưu dự án, khởi tạo runtime fields.|<p>@app.route('/api/submit\_project', methods=['POST'])</p><p>def submit\_project(): ...</p>|
|Gửi deck – /api/submit\_deck|POST|{"room\_id":"...","player\_index":0,"active\_indices":[...],"reaction\_indices":[...]}|{"ok":true,"game\_started":false}|Xác thực 22 active, 0‑3 reaction, lưu vào project.|<p>@app.route('/api/submit\_deck', methods=['POST'])</p><p>def submit\_deck(): ...</p>|
|Auto deck – /api/auto\_select\_deck|POST|{"room\_id":"...","player\_index":0}|{"ok":true,"active\_indices":[...],"reaction\_indices":[...],"message":"..."}|Random deck nhưng chưa submit.|<p>@app.route('/api/auto\_select\_deck', methods=['POST'])</p><p>def auto\_select\_deck(): ...</p>|
|Chơi thẻ – /api/play\_card|POST|{"room\_id":"...","player\_index":0,"card\_index":int}|{"ok":true,"message":"..."}|Lưu thẻ vào pending\_cards, trừ năng lượng.|<p>@app.route('/api/play\_card', methods=['POST'])</p><p>def play\_card(): ...</p>|
|Mulligan – /api/mulligan|POST|{"room\_id":"...","player\_index":0}|{"ok":true,"message":"..."}|Rút bài mới, giảm transparency, trust scores.|<p>@app.route('/api/mulligan', methods=['POST'])</p><p>def mulligan(): ...</p>|
|Ready phase – /api/player\_ready\_phase|POST|{"room\_id":"...","player\_index":0}|{"ok":true}|Đánh dấu sẵn sàng.|<p>@app.route('/api/player\_ready\_phase', methods=['POST'])</p><p>def player\_ready\_phase(): ...</p>|
|Dùng reaction – /api/use\_reaction|POST|{"room\_id":"...","player\_index":0,"reaction\_index":int}|{"ok":true,"message":"..."}|Kích hoạt reaction, áp dụng effect.|<p>@app.route('/api/use\_reaction', methods=['POST'])</p><p>def use\_reaction(): ...</p>|
|Trạng thái người chơi – /api/player\_state|GET|query ?room\_id=...&player\_index=...|{"hand":[...],"energy\_left":int,"hype":int,"metrics":{...},"triggers":[...]}|Trả về hand, metrics, triggers. Gọi calculate\_metrics.|<p>@app.route('/api/player\_state', methods=['GET'])</p><p>def player\_state(): ...</p>|
|Danh sách thẻ – /api/card\_lists|GET|không|{"active":[...],"reaction":[...],"total\_active":42,"total\_reaction":6}|Cung cấp dữ liệu thẻ cho deck builder.|<p>@app.route('/api/card\_lists', methods=['GET'])</p><p>def card\_lists(): return jsonify(...)</p>|
|Health check – /api/health|GET|không|{"status":"ok","message":"Backend đang chạy"}|Kiểm tra backend.|<p>@app.route('/api/health', methods=['GET'])</p><p>def health\_check(): return jsonify({'status':'ok','message':'Backend đang chạy'})</p>|

### <a name="_ufai2uz4m4ef"></a><a name="_toc232080513"></a>**4.2. Thành phần lưu trữ bền vững**

|**Thành phần**|**Loại**|**Input**|**Output**|**Mục đích & cách chạy**|**Code (dòng đầu – dòng cuối)**|
| :-: | :-: | :-: | :-: | :-: | :-: |
|SqliteRoomManager|Lớp|db\_path (mặc định 'game\_state.db'), key room\_id|Truy cập phòng qua rooms[room\_id], tự động persist|Dùng SQLite làm lưu trữ chính, cache trong g.rooms\_cache để tránh đọc lại DB trong cùng request. Hook teardown ghi xuống DB.|<p>class SqliteRoomManager:</p><p>def \_\_init\_\_(self, db\_path='game\_state.db'): ...</p><p>def \_get\_cache(self): ...</p><p>def \_\_getitem\_\_(self, key): ...</p><p>def \_\_setitem\_\_(self, key, value): ...</p><p>def \_\_contains\_\_(self, key): ...</p><p>def get(self, key, default=None): ...</p><p>def values(self): ...</p>|
|save\_rooms|Hook (@app.teardown\_request)|không (dùng g.rooms\_cache)|Ghi cache vào bảng rooms của SQLite|Tự động gọi sau mỗi request, lưu tất cả phòng đã thay đổi.|<p>@app.teardown\_request</p><p>def save\_rooms(exception=None):</p><p>if hasattr(g, 'rooms\_cache'):</p><p>with sqlite3.connect(rooms.db\_path) as conn:</p><p>for key, room in g.rooms\_cache.items():</p><p>conn.execute('INSERT OR REPLACE INTO rooms (id, data) VALUES (?, ?)', (key, json.dumps(room)))</p>|

### <a name="_6l5bspu4bk5e"></a><a name="_toc232080514"></a>**4.3. Hàm tiện ích chuẩn hóa và xử lý lỗi**

|**Hàm**|**Input**|**Output**|**Mục đích & cách chạy**|**Code (dòng đầu – dòng cuối)**|
| :-: | :-: | :-: | :-: | :-: |
|ensure\_room\_lists|room: dict|room sửa trực tiếp|Chuẩn hóa độ dài mảng (players, player\_ready, ...) bằng num\_players.|<p>def ensure\_room\_lists(room):</p><p>num\_players = int(room.get('num\_players') or len(room.get('players', [])) or 4)</p><p>room['num\_players'] = num\_players</p><p>list\_defaults = {...}</p><p>for key, default\_factory in list\_defaults.items(): ...</p><p>room.setdefault('pending\_cards', {}); ...</p>|
|ensure\_bot\_alloc|room: dict|room sửa trực tiếp|Tái tạo bot\_alloc từ BOTS, sửa perProject về độ dài đúng.|<p>def ensure\_bot\_alloc(room):</p><p>num\_players = ...; bot\_alloc = room.get('bot\_alloc')</p><p>if not isinstance(bot\_alloc, list): ...</p><p>by\_id = {entry.get('bot\_id'): entry for entry in bot\_alloc if isinstance(entry, dict)}</p><p>normalized = []</p><p>for bot in BOTS: ...</p><p>room['bot\_alloc'] = normalized</p>|
|get\_bot\_memory|room, bot\_id (int/str), player\_count|memory: dict|Lấy bộ nhớ bot, xử lý key int/string, tạo history mới nếu chưa có.|<p>def get\_bot\_memory(room, bot\_id, player\_count):</p><p>str\_key = str(bot\_id); int\_key = bot\_id</p><p>memory = room['bot\_memory'].get(str\_key)</p><p>if memory is None and int\_key in room['bot\_memory']: memory = room['bot\_memory'].pop(int\_key); room['bot\_memory'][str\_key] = memory</p><p>if memory is None: memory = {'attractiveness\_history': [[] for \_ in range(player\_count)]}</p><p>history = memory.setdefault('attractiveness\_history', [])</p><p>while len(history) < player\_count: history.append([])</p><p>return memory</p>|
|aggregate\_bot\_actions|bot\_actions: list[dict]|list[dict] đã gộp|Gom các hành động bot theo (bot\_type, action, player\_index), cộng dồn amount.|<p>def aggregate\_bot\_actions(bot\_actions):</p><p>grouped = {}</p><p>for action in bot\_actions or []:</p><p>key = (action.get('bot\_type','Unknown'), action.get('action','unknown'), action.get('player\_index',-1))</p><p>grouped[key] = grouped.get(key,0) + action.get('amount',0)</p><p>return [{'bot\_type':bt,'action':act,'player\_index':pi,'amount':amt} for (bt,act,pi),amt in sorted(grouped.items())]</p>|
|try\_start\_game|room: dict (status = choosing\_deck)|bool thành công, sửa room|Tính max\_phase, tạo bot\_alloc, chia bài, gán sự kiện, chuyển sang 'playing'.|<p>def try\_start\_game(room):</p><p>if room['status'] != 'choosing\_deck': return False</p><p>for i,p in enumerate(room['players']): if p and not room['deck\_ready'][i]: return False</p><p>max\_phase = max((p.get('max\_phase',5) for p in room['players'] if p), default=5)</p><p>room['max\_phase'] = max\_phase</p><p>room['bot\_alloc'] = [{'bot\_id':bot['id'], 'perProject':[0]\*room['num\_players'], 'idle':bot['wealth']} for bot in BOTS]</p><p>room['phase'] = 1; room['status'] = 'playing'</p><p>for idx,p in enumerate(room['players']):</p><p>if p and p.get('active\_deck'):</p><p>p['current\_hand'] = draw\_hand\_no\_duplicate\_color\_cost(p['active\_deck'],5)</p><p>p['energy\_left'] = 3; p['last\_scenario'] = random.choice(SCENARIOS)['name']</p><p>return True</p>|
|evaluate\_condition (kèm get\_metric\_value, compare)|cond: dict, proj: dict, metrics: dict|bool|Đánh giá điều kiện reaction (hỗ trợ all, so sánh, metric). Dùng cả dữ liệu từ proj và metrics.|<p>def evaluate\_condition(cond, proj, metrics):</p><p>def get\_metric\_value(metric\_def): ...</p><p>def compare(left, op, right): ...</p><p>if "all" in cond: return all(...)</p><p>if "left" in cond: ...</p><p>if "metric" in cond: ...</p><p>return False</p>|
|handle\_exception|Exception|JSON {"error": str}|Bắt mọi ngoại lệ, log stack trace, trả JSON lỗi thay vì HTML.|<p>@app.errorhandler(Exception)</p><p>def handle\_exception(e):</p><p>if isinstance(e, HTTPException): return jsonify({'error': e.description}), e.code</p><p>import traceback; traceback.print\_exc()</p><p>return jsonify({'error': f'Internal Server Error: {str(e)}'}), 500</p>|

###
### <a name="_n5pw4hxzv9s0"></a><a name="_cnipurknkty7"></a><a name="_toc232080515"></a>**4.4. Kết nối logic game giữa các module**

|**Kết nối**|**Module liên quan**|**Cách thực hiện**|
| :-: | :-: | :-: |
|Minh → API|Minh|<p>proj['active\_deck'] = [ACTIVE\_CARDS\_FULL[i] for i in active\_indices] trong submit\_deck</p><p>scenario = random.choice(SCENARIOS) trong run\_phase</p><p>p['current\_hand'] = draw\_hand\_no\_duplicate\_color\_cost(p['active\_deck'],5) trong try\_start\_game và run\_phase</p>|
|Phúc → API|Phúc|<p>metrics = calculate\_metrics(proj) trong player\_state, host\_state, run\_phase</p><p>score = final\_score(proj, max\_phase, metrics) trong player\_state, host\_state</p>|
|Khánh → API|Khánh|bot\_actions = []; process\_phase(room, phase, players, logs, bot\_actions) trong run\_phase|
|Khánh ← get\_bot\_memory|Gameplay|get\_bot\_memory(room, bot\_id, player\_count) – do thành viên này viết, Khánh gọi trong process\_phase|
|Dương → API|Backend|Route / và /play/... trả về host.html, play.html; các API trả JSON đúng cấu trúc (ví dụ rankings có name, funding, hype, score, deck\_ready)|
|Chuỗi Minh – Phúc – Khánh – Minh|Cả ba|Trong run\_phase: 1) Áp dụng SCENARIOS (Minh); 2) Áp dụng pending\_cards (Minh); 3) Gọi calculate\_metrics (Phúc); 4) Kiểm tra reaction (Minh + Phúc qua evaluate\_condition); 5) Gọi process\_phase (Khánh); 6) Gọi draw\_hand\_no\_duplicate\_color\_cost (Minh)|
###
### <a name="_ct5255pgxe84"></a><a name="_30ia8uyqj0js"></a><a name="_toc232080516"></a>**4.5. Kiểm thử**

|**STT**|**Kịch bản kiểm thử**|**Kết quả mong đợi**|**Kết quả thực tế**|
| :-: | :-: | :-: | :-: |
|1|Tạo phòng 2 người, submit project + deck, host run phase → game bắt đầu phase 1|Mỗi người có 5 lá bài, sự kiện ngẫu nhiên xuất hiện từng phase|Đạt|
|2|Một người chơi chưa submit deck, host run phase → báo lỗi "Players X chưa submit deck"|Thông báo lỗi rõ ràng|Đạt|
|3|Người chơi chơi một thẻ (play\_card) → giảm energy, thẻ biến mất khỏi hand, sau run phase hiệu ứng được áp dụng|Energy giảm, thẻ biến mất, chỉ số hype/transparency thay đổi|Đạt|
|4|Người chơi dùng Mulligan → energy giảm, hand mới (5 lá random)|<p>Nếu người chơi dùng 2 lần Mulligan 1 phase => báo lỗi</p><p>Nếu không đủ 1 energy mà dùng Mulligan => báo lỗi</p>|Đạt|
|5|Một dự án có available\_cash xuống 0 → bị đánh dấu bankrupt, không tham gia phase sau|Log "PHÁ SẢN", dự án biến mất khỏi vòng chơi|Đạt|
|6|Reaction card có điều kiện runway <= 2 → xuất hiện nút "Kích hoạt", sau khi dùng có hiệu ứng cộng runway|Trigger đúng, hiệu ứng được cộng|Đạt|
|7|Host nhấn "End Game" → bảng xếp hạng hiển thị điểm tạm thời (dựa trên số phase đã qua)|Điểm xuất hiện|Đạt|
|8|Host nhấn "Reset Game" → tất cả dữ liệu trở về trạng thái ban đầu, người chơi có thể submit lại project|Đúng|Đạt|
|9|Tắt rồi bật lại Flask server → các phòng đang chơi vẫn còn, người chơi có thể kết nối lại|SQLite lưu trữ bền vững|Đạt|
|10|4 người chơi, mỗi người có scale khác nhau (S, M, L) → số phase tối đa tương ứng (5,7,9)|Mỗi người kết thúc ở phase khác nhau|Đạt|
|11|Những dự án đã kết thúc, phá sản, người chơi tiếp tục bấm các nút chơi|Có thông báo báo về|Đạt|
|12|Chọn quá thẻ cho phép|Có thông báo báo về|Đạt|
|13|<p>Tất cả người chơi chưa Ready phase khi chạy game</p><p>Dù trong phòng chơi không đủ người, vì có người phá sản hoặc bị out hay hết phase</p>|<p>Thông báo về Host</p><p>Game vẫn chơi tiếp được</p>|Đạt|


## <a name="_tzvww0rzi3d9"></a><a name="_toc232080517"></a>**5. Bằng chứng về sự đóng góp**
Để minh chứng cho những điều trên, tôi có các bằng chứng cụ thể:

- Mã nguồn app.py trong kho lưu trữ cuối cùng: Dòng đầu tiên có chú thích # - JIN: API Routing, Flask app, Rooms management. Toàn bộ các @app.route và lớp SqliteRoomManager nằm trong phần đó. Bất kỳ ai mở file cũng thấy rõ phần của tôi.
- Lớp SqliteRoomManager từ định nghĩa class SqliteRoomManager: đến cuối hàm save\_rooms là do tôi viết hoàn toàn. Các thành viên khác không can thiệp vào file này ngoại trừ việc gọi các phương thức của nó.
- Hàm ensure\_room\_lists và ensure\_bot\_alloc – hai hàm này không có trong bất kỳ tài liệu thiết kế ban đầu nào; tôi đã thêm chúng sau khi phát hiện lỗi trong quá trình tích hợp. Chúng là "patches" độc đáo của riêng tôi.
- Nhật ký commit Github: [https://github.com/khanhhabao7/nhap-fintech/commits/main/app.py?author=kimhyejinhq-crypto&before=fd822f613c203bda71eef3323ef29e99dbb58ce4+](https://github.com/khanhhabao7/nhap-fintech/commits/main/app.py?author=kimhyejinhq-crypto&before=fd822f613c203bda71eef3323ef29e99dbb58ce4+35)
## <a name="_toc232080518"></a>**6. Công việc của tôi liên quan như thế nào đến sản phẩm cuối cùng?**
Nếu ví trò chơi như một cơ thể sống, thì các module của Minh, Phúc, Khánh, Dương là các cơ quan (tim, phổi, não, tay chân). Công việc của tôi là hệ thần kinh – kết nối tất cả, truyền tín hiệu, đảm bảo mọi bộ phận phối hợp nhịp nhàng. Cụ thể:

- Mọi cú nhấp chuột từ trình duyệt (gửi dự án, chọn bài, chơi bài, ready, dùng reaction) đều gửi request đến một API do tôi viết. Nếu các API đó sai hoặc thiếu, frontend sẽ không thể giao tiếp với backend.
- Dữ liệu trạng thái (tiến độ funding, điểm tin cậy, hand bài, năng lượng) được lưu trữ và phục hồi nhờ SqliteRoomManager. Nhờ đó, người chơi không bị mất tiến trình khi máy chủ khởi động lại – một yêu cầu quan trọng từ giảng viên.
- Các hàm chuẩn hóa (ensure\_room\_lists, ensure\_bot\_alloc) giống như những tấm lưới an toàn, bắt lỗi trước khi chúng làm sập game. Nếu không có chúng, trò chơi sẽ gặp lỗi IndexError hoặc KeyError bất cứ khi nào có sự bất thường trong dữ liệu.
- Trình xử lý lỗi toàn cục đảm bảo rằng người dùng không bao giờ thấy một stack trace xấu xí; thay vào đó, họ nhận được thông báo lỗi dạng JSON và có thể gửi phản hồi cho chúng tôi.

Nhờ những đóng góp này, bốn mô-đun độc lập đã được tích hợp thành một trò chơi hoàn chỉnh, có thể chạy từ đầu đến cuối mà không cần can thiệp thủ công. Đó là thành công lớn nhất của tôi trong dự án này.


## <a name="_toc232080519"></a>**7. Những điều tôi đã học được**
Khi bắt đầu dự án này, tôi nghĩ rằng làm lập trình viên backend nghĩa là viết thuật toán. Nhưng sau đó, tôi hiểu rằng phần khó nhất của lập trình phần mềm không phải là thuật toán bên trong một hàm, mà là sự tương tác giữa các hàm với nhau. Ngay khi bạn đưa ra một ranh giới mạng, hoặc chuyển dữ liệu từ mã của người này sang mã của người khác, những giả định nhỏ nhặt có thể trở thành những lỗi nghiêm trọng. Tôi đã học cách đọc mã của người khác trước khi tự viết mã của mình, và viết mã sao cho có khả năng phòng thủ tốt trước những dữ liệu nhận được.

Tôi cũng học được rằng việc lãnh đạo một nhóm lập trình viên không chỉ đơn thuần là đưa ra chỉ thị mà còn là tạo ra sự rõ ràng. Khi mọi người hiểu được cấu trúc phòng chia sẻ trông như thế nào và tại sao nó phải được thiết kế theo cách nhất định, họ đã ngừng vô tình làm hỏng công việc của nhau. Điều tốt nhất tôi đã làm với tư cách là người lãnh đạo không phải là đưa ra những quyết định kỹ thuật khó khăn nhất — mà là giải thích chúng đủ rõ ràng để cả nhóm có thể tự đưa ra quyết định một cách độc lập.

Về mặt kỹ thuật, tôi đã hiểu sâu hơn về vòng đời yêu cầu của Flask, quản lý kết nối SQLite và tầm quan trọng của ranh giới giao dịch trong môi trường đa người dùng. Trước đây tôi chưa từng xây dựng hệ thống quản lý phòng họp liên tục, và việc phải suy nghĩ về việc vô hiệu hóa bộ nhớ cache — ngay cả ở mức đơn giản nhất là "khi nào bộ nhớ cache trong bộ nhớ được ghi vào đĩa?" — đã dạy tôi rất nhiều điều về nơi trạng thái thực sự được lưu trữ trong một ứng dụng web.

## <a name="_toc232080520"></a>**8. Những thách thức và cách tôi vượt qua chúng**
### <a name="_toc232080521"></a>**Thách thức 1: Lỗi không khớp kiểu dữ liệu khóa JSON**
Đây là lỗi khó chịu nhất của dự án. Từ điển Python có thể có khóa kiểu số nguyên (bot\_id: 1, 2, 3). Khi các từ điển đó được chuyển đổi thành JSON và sau đó được giải mã ngược lại, tất cả các khóa đều trở thành chuỗi ("1", "2", "3"). Cấu trúc bot\_memory và trust\_scores sử dụng khóa số nguyên bên trong, vì vậy sau một lần truy cập qua bộ nhớ SQLite, mọi thao tác tìm kiếm đều thất bại mà không báo lỗi hoặc gây ra lỗi KeyError. Tôi đã khắc phục điều này bằng cách viết lại hàm get\_bot\_memory() với chuẩn hóa khóa chuỗi/số nguyên rõ ràng, và bằng cách kiểm tra kỹ lưỡng mọi nơi trong mã nguồn nơi ID bot được sử dụng làm khóa từ điển. Tôi đã mất vài giờ gỡ lỗi qua nhiều lần chạy thử nghiệm trước khi tìm ra nguyên nhân gốc rễ.

### <a name="_qqghfn8yg18v"></a><a name="_toc232080522"></a>**Thách thức 2: Phối hợp bốn phong cách lập trình khác nhau**
Mỗi thành viên đều có quy ước đặt tên, giả định dữ liệu và thói quen xử lý lỗi riêng. Các hàm đo lường của Phuc trả về các số liệu chính xác. Các hàm bot của Khanh sửa đổi danh sách người chơi tại chỗ và trả về None. Giao diện người dùng của Duong yêu cầu các tên trường JSON rất cụ thể. Việc làm cho tất cả chúng giao tiếp với nhau mà không cần viết lại công việc của bất kỳ ai là một quá trình thương lượng liên tục. Giải pháp của tôi là coi lớp API của mình như lớp dịch thuật: Tôi điều chỉnh dữ liệu đầu vào để phù hợp với những gì mỗi mô-đun mong đợi, và điều chỉnh đầu ra của mỗi mô-đun để phù hợp với những gì giao diện người dùng sử dụng. Điều này có nghĩa là các điểm cuối của tôi đôi khi dài dòng hơn mức cần thiết, nhưng trò chơi vẫn hoạt động.


### <a name="_qqghfn8yg18v"></a><a name="_toc232080525"></a>**Thách thức 3: Dùng AI để debug: một con dao hai lưỡi**

Tôi đã dùng ChatGPT, DeepSeek, Claude, Gemini rất nhiều. Mỗi lần gặp lỗi, tôi lại copy code vào hỏi. Có những lúc AI giúp tôi nhanh chóng tìm ra lỗi cú pháp. Nhưng có những lúc nó làm tôi điên tiết: nó "ăn mất code" – nghĩa là nó đưa ra giải pháp nhưng lại bỏ qua một phần quan trọng, hoặc viết lại toàn bộ hàm của tôi thành một thứ khác, làm tôi mất cả buổi tối để phục hồi. Thậm chí có lần tôi hỏi tại sao lỗi KeyError xảy ra, ChatGPT trả lời chung chung "hãy kiểm tra khóa", trong khi tôi đã kiểm tra cả trăm lần. Mãi sau tôi mới tự mò ra: do JSON biến số thành chuỗi.

Qua thử nghiệm nhiều công cụ, tôi thấy DeepSeek là chính xác và ít "ăn code" nhất. Tôi dùng DeepSeek nhiều hơn cả. Nhưng dù dùng AI nào, tôi cũng nhận ra một điều quan trọng: AI không thể thay thế việc tự đọc code. Có những lỗi mà chỉ có in log ra, ngồi nhìn từng dòng, mới thấy được. Tôi đã phải sửa đi sửa lại rất nhiều lần – có đoạn code tôi viết lại 5, 6 lần mới ổn. AI chỉ là trợ thủ, còn tôi vẫn là người phải hiểu.

## <a name="_7d4o97imhpef"></a><a name="_toc232080523"></a>**9. Lời nhắn nhủ dành cho các sinh viên tương lai**
Là một sinh viên tài chính không có kinh nghiệm gì về mảng code, tôi khuyên mọi người hãy nắm bắt được rõ ràng sản phẩm cuối cùng của mình trông như nào. Từ đó, khi xây dựng một sản phẩm cho riêng mình, bạn có thể vừa test luôn có lỗi gì không cũng như lệnh AI dễ dàng và nhanh gọn hơn. 

Vì là mọi người cùng code một lúc nên phải LUÔN LƯU lại bản đã chỉnh sửa của mình để tránh trường hợp người này sửa đè làm mất phần code của mình. 

Cố gắng lên hỏi ý kiến của instructor thật nhiều bởi càng nhiều góc nhìn thì sản phẩm của mình càng hoàn thiện, đặc biệt là góc nhìn của người có kinh nghiệm luôn đưa ra những lời khuyên đáng ghi chép.

## <a name="_z74kdjhgxx2r"></a><a name="_toc232080524"></a>**10. Kết luận** 

Fun(d) Raising không chỉ là một yêu cầu của môn học mà còn là một hành trình trưởng thành của tôi. Tôi bắt đầu với rất ít kinh nghiệm lập trình, nhưng dần học được cách thiết kế hệ thống, tích hợp các mô-đun, dẫn dắt một nhóm và giải quyết những vấn đề kỹ thuật thực tế.

Tôi đã từng bật khóc vì mất dữ liệu, bật cười khi giai đoạn đầu tiên cuối cùng cũng vận hành được, mất ngủ vì những lỗi triển khai, và cảm thấy vô cùng nhẹ nhõm khi lần chạy thử cuối cùng thành công. Hơn cả sản phẩm được tạo ra, dự án này đã dạy tôi về sự kiên trì, tinh thần làm việc nhóm và giá trị của việc học hỏi từ thất bại. Nhìn lại chặng đường đã qua, tôi tự hào không chỉ về những gì chúng tôi đã xây dựng, mà còn về sự trưởng thành của chính mình trong suốt quá trình ấy.











