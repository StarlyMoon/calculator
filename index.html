<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>計算機</title>
    <!-- PWA 配置 -->
    <link rel="manifest" href="data:application/manifest+json;utf8,{\"name\":\"計算機\",\"short_name\":\"計算機\",\"start_url\":\".\",\"display\":\"standalone\",\"background_color\":\"#17181c\",\"theme_color\":\"#17181c\"}">
    <!-- Supabase & CryptoJS SDK -->
    <script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/crypto-js/4.1.1/crypto-js.min.js"></script>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif; -webkit-user-select: none; user-select: none; }
        body { background-color: #17181c; color: #fff; height: 100vh; width: 100vw; overflow: hidden; display: flex; justify-content: center; align-items: center; }
        
        /* 計算機主體 */
        .calculator { width: 100%; height: 100%; max-width: 420px; padding: 24px; display: flex; flex-direction: column; position: relative; background: #17181c; }
        .top-icons { display: flex; justify-content: flex-end; height: 25px; }
        .secret-trigger { background: none; border: none; font-size: 26px; color: #616472; font-style: italic; font-family: serif; cursor: pointer; }
        .screen { flex: 1; display: flex; flex-direction: column; align-items: flex-end; justify-content: flex-end; padding-bottom: 15px; }
        .history { font-size: 16px; color: #8a8d9b; min-height: 20px; text-align: right; }
        .current { font-size: 36px; font-weight: 300; text-align: right; word-break: break-all; }
        .keypad { display: grid; grid-template-columns: repeat(4, 1fr); gap: 16px; padding-bottom: 10px; }
        .btn { aspect-ratio: 1; border-radius: 50%; border: none; background: #21232b; color: #fff; font-size: 24px; cursor: pointer; display: flex; justify-content: center; align-items: center; }
        .btn:active { transform: scale(0.94); }
        .btn.func { background: #2e313c; color: #a5a9b8; }
        .btn.operator { background: #ff9f0a; font-size: 28px; }

        /* 代數求解面板 (Fake Mode) */
        .algebra-panel { display: none; position: absolute; top: 60px; left: 24px; right: 24px; background: #21232b; border: 1px solid #353844; border-radius: 16px; padding: 16px; z-index: 5; }
        .algebra-panel h4 { color: #ff9f0a; margin-bottom: 8px; }
        .algebra-input { width: 45px; background: #17181c; border: 1px solid #353844; color: #fff; text-align: center; border-radius: 6px; padding: 4px; }

        /* 兩階段驗證 Modal */
        .modal-overlay { position: absolute; inset: 0; background: rgba(0,0,0,0.85); backdrop-filter: blur(5px); display: none; flex-direction: column; justify-content: center; align-items: center; padding: 24px; z-index: 100; }
        .modal-box { background: #21232b; border: 1px solid #353844; border-radius: 20px; padding: 24px; width: 100%; max-width: 320px; text-align: center; }
        .modal-box h3 { font-size: 18px; margin-bottom: 12px; }
        .modal-box p { font-size: 13px; color: #a5a9b8; margin-bottom: 16px; line-height: 1.4; }
        .modal-input { width: 100%; padding: 12px; background: #17181c; border: 1px solid #353844; border-radius: 10px; color: #fff; font-size: 15px; text-align: center; margin-bottom: 12px; outline: none; }
        .modal-btn-group { display: flex; gap: 10px; }
        .modal-btn { flex: 1; padding: 12px; border-radius: 10px; border: none; font-weight: 600; cursor: pointer; }
        .modal-btn.confirm { background: #ff9f0a; color: #fff; }
        .modal-btn.cancel { background: #2e313c; color: #a5a9b8; }

        /* 秘密通訊大廳 (Real Mode) */
        .chat-app { display: none; width: 100%; height: 100%; background: #0d0e12; flex-direction: row; position: relative; }
        .sidebar { width: 220px; background: #14151a; border-right: 1px solid #21232b; display: flex; flex-direction: column; padding: 16px 10px; }
        .sidebar h2 { font-size: 13px; color: #616472; margin-bottom: 10px; text-transform: uppercase; letter-spacing: 1px; }
        
        /* 個人資料區 */
        .my-profile { display: flex; align-items: center; gap: 10px; padding: 8px; background: #1c1d24; border-radius: 10px; margin-bottom: 16px; cursor: pointer; border: 1px dashed #353844; }
        .my-profile:hover { border-color: #ff9f0a; }
        .avatar-img { width: 32px; height: 32px; border-radius: 50%; object-fit: cover; background: #2e313c; display: flex; justify-content: center; align-items: center; font-size: 18px; }

        .channel-list, .member-list { list-style: none; margin-bottom: 16px; }
        .channel-item, .member-item { padding: 10px; border-radius: 8px; font-size: 14px; cursor: pointer; color: #a5a9b8; display: flex; align-items: center; justify-content: space-between; margin-bottom: 4px; }
        .channel-item.active, .channel-item:hover { background: #21232b; color: #fff; }
        .member-info { display: flex; align-items: center; gap: 8px; }
        .dot { width: 8px; height: 8px; border-radius: 50%; background: #444; }
        .dot.online { background: #34c759; box-shadow: 0 0 6px #34c759; }

        .chat-main { flex: 1; display: flex; flex-direction: column; background: #0d0e12; }
        .chat-header { height: 50px; border-bottom: 1px solid #21232b; display: flex; align-items: center; justify-content: space-between; padding: 0 16px; font-size: 15px; font-weight: 600; }
        .chat-messages { flex: 1; padding: 16px; overflow-y: auto; display: flex; flex-direction: column; gap: 12px; }
        .msg-bubble { max-width: 80%; padding: 10px 14px; border-radius: 12px; background: #1c1d24; font-size: 14px; line-height: 1.4; align-self: flex-start; word-break: break-word; }
        .msg-bubble.me { align-self: flex-end; background: #007aff; }
        .msg-bubble.highlight { border: 2px solid #ff9f0a; background: #3a2d13; }
        .msg-meta { font-size: 11px; color: rgba(255,255,255,0.6); margin-bottom: 4px; display: flex; align-items: center; gap: 6px; }
        
        .chat-input-area { padding: 12px; border-top: 1px solid #21232b; display: flex; gap: 8px; background: #14151a; }
        .chat-input { flex: 1; background: #1c1d24; border: 1px solid #21232b; border-radius: 20px; padding: 10px 16px; color: #fff; outline: none; font-size: 14px; }
        .send-btn { background: #ff9f0a; border: none; border-radius: 50%; width: 38px; height: 38px; color: #fff; cursor: pointer; font-weight: bold; }

        /* 防窺全黑遮罩 */
        .lock-mask { position: fixed; inset: 0; background: #000; z-index: 999; display: none; flex-direction: column; justify-content: center; align-items: center; }
        .btn-danger { background: #ff3b30; color: #fff; padding: 6px 10px; border: none; border-radius: 6px; font-size: 12px; cursor: pointer; }
    </style>
</head>
<body>

    <!-- 1. 計算機外殼 -->
    <div class="calculator" id="calculatorApp">
        <div class="top-icons">
            <button class="secret-trigger" id="secretBtn">x</button>
        </div>

        <div class="algebra-panel" id="algebraPanel">
            <h4>📐 一元二次方程式求解器</h4>
            <div style="font-size:12px; color:#a5a9b8; margin-bottom:8px;">
                <input type="number" id="algA" class="algebra-input" value="1"> x² + 
                <input type="number" id="algB" class="algebra-input" value="-1"> x + 
                <input type="number" id="algC" class="algebra-input" value="-2"> = 0
                <button onclick="solveAlgebra()" style="background:#ff9f0a; border:none; color:#fff; padding:2px 8px; border-radius:4px; margin-left:6px;">求解</button>
            </div>
            <div id="algebraAns" style="font-family:monospace; font-weight:bold; color:#34c759; font-size:13px;">解: x₁ = 2.00, x₂ = -1.00</div>
        </div>

        <div class="screen">
            <div class="history" id="history"></div>
            <div class="current" id="current">0</div>
        </div>

        <div class="keypad">
            <button class="btn func" onclick="clearCalc()">C</button>
            <button class="btn func" onclick="backspace()">⌫</button>
            <button class="btn func" onclick="appendPercent()">%</button>
            <button class="btn operator" onclick="appendOperator('÷')">÷</button>

            <button class="btn" onclick="appendNumber('7')">7</button>
            <button class="btn" onclick="appendNumber('8')">8</button>
            <button class="btn" onclick="appendNumber('9')">9</button>
            <button class="btn operator" onclick="appendOperator('×')">×</button>

            <button class="btn" onclick="appendNumber('4')">4</button>
            <button class="btn" onclick="appendNumber('5')">5</button>
            <button class="btn" onclick="appendNumber('6')">6</button>
            <button class="btn operator" onclick="appendOperator('－')">－</button>

            <button class="btn" onclick="appendNumber('1')">1</button>
            <button class="btn" onclick="appendNumber('2')">2</button>
            <button class="btn" onclick="appendNumber('3')">3</button>
            <button class="btn operator" onclick="appendOperator('＋')">＋</button>

            <button class="btn func" onclick="toggleParentheses()">( )</button>
            <button class="btn" onclick="appendNumber('0')">0</button>
            <button class="btn" onclick="appendDecimal()">.</button>
            <button class="btn operator" onclick="calculate()">＝</button>
        </div>

        <!-- 兩階段驗證 Modal -->
        <div class="modal-overlay" id="authModal">
            <div class="modal-box" id="stage1Box">
                <h3>校園自主學習專案</h3>
                <p>進階代數功能僅限授課專案測試使用，請輸入指導老師分發的課程驗證碼：</p>
                <input type="password" class="modal-input" id="courseCodeInput" placeholder="請輸入課程驗證碼">
                <div class="modal-btn-group">
                    <button class="modal-btn cancel" onclick="closeAuthModal()">取消</button>
                    <button class="modal-btn confirm" onclick="verifyCourseCode()">下一步</button>
                </div>
            </div>

            <div class="modal-box" id="stage2Box" style="display: none;">
                <h3>自主學習系統登入</h3>
                <p>請輸入您的專案學號與個人驗證密碼：</p>
                <input type="text" class="modal-input" id="usernameInput" placeholder="請輸入學號 / 帳號">
                <input type="password" class="modal-input" id="userPasswordInput" placeholder="請輸入個人密碼">
                <div class="modal-btn-group">
                    <button class="modal-btn cancel" onclick="backToStage1()">上一步</button>
                    <button class="modal-btn confirm" onclick="finalLogin()">進入系統</button>
                </div>
            </div>
        </div>
    </div>

    <!-- 2. 秘密通訊大廳 -->
    <div class="chat-app" id="chatApp">
        <div class="sidebar">
            <h2>個人設定</h2>
            <div class="my-profile" onclick="triggerAvatarUpload()">
                <div id="myAvatarBox" class="avatar-img">👤</div>
                <div>
                    <div id="myNickname" style="font-size:13px; font-weight:600;">使用者</div>
                    <div style="font-size:10px; color:#ff9f0a;">📷 點擊更換頭像</div>
                </div>
            </div>
            <!-- 隱藏的檔案上傳輸入框 -->
            <input type="file" id="avatarInput" accept="image/*" style="display:none" onchange="uploadCustomAvatar(event)">

            <h2>頻道選單</h2>
            <ul class="channel-list" id="channelList"></ul>
            
            <h2>成員動態</h2>
            <ul class="member-list" id="memberList"></ul>
            
            <div style="margin-top:auto;">
                <button class="btn-danger" style="width:100%; padding:10px;" onclick="nuclearDestruct()">⚠️ 一鍵全網銷毀</button>
            </div>
        </div>

        <div class="chat-main">
            <div class="chat-header">
                <span id="currentChannelTitle">頻道聊天室</span>
                <button class="btn-danger" onclick="toggleFreezeCurrentTarget()">🚨 觸發凍結</button>
            </div>
            <div class="chat-messages" id="chatMessages"></div>
            <div class="chat-input-area">
                <input type="text" class="chat-input" id="msgInput" placeholder="發送訊息... (支援 @[標註:user] @[加密:pwd] @[限時:秒])">
                <button class="send-btn" onclick="sendMessage()">➤</button>
            </div>
        </div>
    </div>

    <!-- 3. 鎖屏遮罩 -->
    <div class="lock-mask" id="lockMask">
        <h3 style="margin-bottom:12px;">系統已鎖定</h3>
        <input type="password" class="modal-input" id="unlockCodeInput" style="max-width:200px;" placeholder="輸入短暗號解鎖">
        <button class="modal-btn confirm" style="max-width:200px;" onclick="unlockScreen()">解鎖</button>
    </div>

    <script>
        // ================= ⚠️ 請修改此處的 Supabase 金鑰 =================
        const SUPABASE_URL = "https://vypcadthtduafammtlwz.supabase.co/rest/v1/";
        const SUPABASE_ANON_KEY = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InZ5cGNhZHRodGR1YWZhbW10bHd6Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3ODg0Mzc1NzIsImV4cCI6MjEwNDAxMzU3Mn0.AYL9fbOfD7i4cIXgYQZs4JWHkQF7tm1X-K_uwQ0NGoI";
        const COURSE_CODE = "PLAYMATH"; 
        // =================================================================

        const supabase = supabase.createClient(SUPABASE_URL, SUPABASE_ANON_KEY);

        let currentUser = null;
        let activeChannel = { type: 'group', target: 'group_1234', title: '👥 1234 核心大群' };
        let allUsers = [];

        // --- 計算機邏輯 ---
        let expression = '0', isNewCalc = false;
        function updateDisplay() { document.getElementById('current').innerText = expression; }
        function appendNumber(num) { expression = (expression === '0' || isNewCalc) ? num : expression + num; isNewCalc = false; updateDisplay(); }
        function appendOperator(op) { expression += op; isNewCalc = false; updateDisplay(); }
        function clearCalc() { expression = '0'; updateDisplay(); }
        function backspace() { expression = expression.length > 1 ? expression.slice(0,-1) : '0'; updateDisplay(); }
        function calculate() {
            try {
                let expr = expression.replace(/＋/g,'+').replace(/－/g,'-').replace(/×/g,'*').replace(/÷/g,'/');
                expression = String(eval(expr)); isNewCalc = true;
            } catch(e) { expression = '錯誤'; }
            updateDisplay();
        }

        function solveAlgebra() {
            let a = parseFloat(document.getElementById('algA').value), b = parseFloat(document.getElementById('algB').value), c = parseFloat(document.getElementById('algC').value);
            let d = b*b - 4*a*c;
            if (d < 0) document.getElementById('algebraAns').innerText = "無實數解";
            else {
                let x1 = (-b + Math.sqrt(d))/(2*a), x2 = (-b - Math.sqrt(d))/(2*a);
                document.getElementById('algebraAns').innerText = `解: x₁ = ${x1.toFixed(2)}, x₂ = ${x2.toFixed(2)}`;
            }
        }

        // --- 登入邏輯 ---
        document.getElementById('secretBtn').addEventListener('click', () => { document.getElementById('authModal').style.display = 'flex'; });
        function closeAuthModal() { document.getElementById('authModal').style.display = 'none'; }

        function verifyCourseCode() {
            const input = document.getElementById('courseCodeInput').value.trim();
            if (input.endsWith('-fake')) {
                closeAuthModal();
                document.getElementById('algebraPanel').style.display = 'block';
            } else if (input === COURSE_CODE) {
                document.getElementById('stage1Box').style.display = 'none';
                document.getElementById('stage2Box').style.display = 'block';
            } else { alert("課程驗證碼錯誤"); }
        }

        function backToStage1() {
            document.getElementById('stage2Box').style.display = 'none';
            document.getElementById('stage1Box').style.display = 'block';
        }

        async function finalLogin() {
            const un = document.getElementById('usernameInput').value.trim();
            const pwd = document.getElementById('userPasswordInput').value.trim();

            if (pwd.endsWith('-fake')) {
                closeAuthModal();
                document.getElementById('algebraPanel').style.display = 'block';
                return;
            }

            const { data: user, error } = await supabase.from('users').select('*').eq('username', un).eq('password', pwd).single();
            if (error || !user) { alert("帳號或密碼不正確"); return; }
            if (user.security_status === 'compromised') { alert("⚠️ 該帳號處於風險凍結狀態！"); return; }

            currentUser = user;
            closeAuthModal();
            document.getElementById('calculatorApp').style.display = 'none';
            document.getElementById('chatApp').style.display = 'flex';

            updateProfileUI();
            initChatSystem();
        }

        // --- 頭像上傳與渲染 ---
        function triggerAvatarUpload() {
            document.getElementById('avatarInput').click();
        }

        function getAvatarHtml(u) {
            if (u.avatar_url) {
                return `<img src="${u.avatar_url}" style="width:24px; height:24px; border-radius:50%; object-fit:cover; vertical-align:middle;">`;
            }
            return u.avatar_emoji || '👤';
        }

        function updateProfileUI() {
            document.getElementById('myNickname').innerText = currentUser.nickname || currentUser.username;
            const box = document.getElementById('myAvatarBox');
            if (currentUser.avatar_url) {
                box.innerHTML = `<img src="${currentUser.avatar_url}" style="width:100%; height:100%; border-radius:50%; object-fit:cover;">`;
            } else {
                box.innerText = currentUser.avatar_emoji || '👤';
            }
        }

        function uploadCustomAvatar(event) {
            const file = event.target.files[0];
            if (!file) return;

            const reader = new FileReader();
            reader.onload = function(e) {
                const img = new Image();
                img.onload = function() {
                    // 自動壓縮圖片尺寸 (80x80)
                    const canvas = document.createElement('canvas');
                    canvas.width = 80; canvas.height = 80;
                    const ctx = canvas.getContext('2d');
                    ctx.drawImage(img, 0, 0, 80, 80);
                    const base64Img = canvas.toDataURL('image/jpeg', 0.8);

                    // 存入 Supabase
                    supabase.from('users').update({ avatar_url: base64Img }).eq('username', currentUser.username)
                    .then(() => {
                        currentUser.avatar_url = base64Img;
                        updateProfileUI();
                        fetchAllUsers();
                        alert("頭像已更新完成！");
                    });
                };
                img.src = e.target.result;
            };
            reader.readAsDataURL(file);
        }

        // --- 聊天室邏輯 ---
        async function initChatSystem() {
            await fetchAllUsers();
            renderChannels();
            setInterval(async () => {
                await supabase.from('users').update({ last_seen: new Date() }).eq('username', currentUser.username);
                await fetchAllUsers();
                loadMessages();
            }, 4000);
        }

        async function fetchAllUsers() {
            const { data } = await supabase.from('users').select('*');
            allUsers = data || [];
            renderMemberList();
        }

        function renderMemberList() {
            const memberList = document.getElementById('memberList');
            memberList.innerHTML = '';
            const now = new Date();
            allUsers.forEach(u => {
                if (currentUser.username === 'user5' && u.username !== 'user1' && u.username !== 'user5') return;
                const isOnline = (now - new Date(u.last_seen)) < 25000;
                memberList.innerHTML += `<li class="member-item"><div class="member-info">${getAvatarHtml(u)} <span>${u.nickname}</span></div><span class="dot ${isOnline ? 'online':''}"></span></li>`;
            });
        }

        function renderChannels() {
            const channelList = document.getElementById('channelList');
            channelList.innerHTML = '';
            let channels = [];
            if (currentUser.username === 'user1') {
                channels = [
                    { type: 'group', target: 'group_1234', title: '👥 1234 核心大群' },
                    { type: 'private', target: 'user2', title: '💬 組員 A' },
                    { type: 'private', target: 'user3', title: '💬 組員 B' },
                    { type: 'private', target: 'user4', title: '💬 組員 C' },
                    { type: 'private', target: 'user5', title: '💬 組員 D (絕對隔離)' }
                ];
            } else if (['user2', 'user3', 'user4'].includes(currentUser.username)) {
                channels = [{ type: 'group', target: 'group_1234', title: '👥 1234 核心大群' }];
                ['user1', 'user2', 'user3', 'user4'].forEach(un => {
                    if (un !== currentUser.username) {
                        const targetUser = allUsers.find(u => u.username === un);
                        channels.push({ type: 'private', target: un, title: `💬 ${targetUser ? targetUser.nickname : un}` });
                    }
                });
            } else if (currentUser.username === 'user5') {
                channels = [{ type: 'private', target: 'user1', title: '💬 組長 (單線頻道)' }];
            }

            channels.forEach(ch => {
                const li = document.createElement('li');
                li.className = `channel-item ${activeChannel.target === ch.target ? 'active':''}`;
                li.innerText = ch.title;
                li.onclick = () => { activeChannel = ch; document.getElementById('currentChannelTitle').innerText = ch.title; renderChannels(); loadMessages(); };
                channelList.appendChild(li);
            });
        }

        async function loadMessages() {
            let query = supabase.from('messages').select('*').order('created_at', { ascending: true });
            if (activeChannel.type === 'group') {
                query = query.eq('target_id', 'group_1234');
            } else {
                query = query.or(`and(sender.eq.${currentUser.username},target_id.eq.${activeChannel.target}),and(sender.eq.${activeChannel.target},target_id.eq.${currentUser.username})`);
            }
            const { data: msgs } = await query;
            renderMessages(msgs || []);
        }

        function renderMessages(msgs) {
            const container = document.getElementById('chatMessages');
            container.innerHTML = '';
            msgs.forEach(m => {
                let content = m.content;
                let isMeMentioned = false;
                content = content.replace(/@\[標註:(\w+)\]/g, (match, un) => {
                    const u = allUsers.find(x => x.username === un);
                    if (un === currentUser.username) isMeMentioned = true;
                    return `<span style="color:#ff9f0a; font-weight:bold;">@${u ? u.nickname : un}</span>`;
                });

                if (content.includes('@[加密:')) {
                    content = content.replace(/@\[加密:(.+?)\]\s*(.+)/, (m, pwd, text) => {
                        return `<div id="enc_${m.id}">🔒 加密訊息 <button onclick="decryptMsg('${pwd}', '${text}', 'enc_${m.id}')" style="padding:2px 6px;">解密</button></div>`;
                    });
                }

                const isMe = m.sender === currentUser.username;
                const senderObj = allUsers.find(u => u.username === m.sender);
                const avatarIcon = senderObj ? getAvatarHtml(senderObj) : '👤';
                
                const bubble = document.createElement('div');
                bubble.className = `msg-bubble ${isMe ? 'me':''} ${isMeMentioned ? 'highlight':''}`;
                bubble.innerHTML = `<div class="msg-meta">${avatarIcon} <span>${senderObj ? senderObj.nickname : m.sender}</span></div><div>${content}</div>`;
                container.appendChild(bubble);
            });
            container.scrollTop = container.scrollHeight;
        }

        function decryptMsg(pwd, text, elId) {
            const userPwd = prompt("請輸入加密金鑰：");
            if (userPwd === pwd) {
                try {
                    const bytes = CryptoJS.AES.decrypt(text, pwd);
                    document.getElementById(elId).innerHTML = `🔓 ${bytes.toString(CryptoJS.enc.Utf8)}`;
                } catch(e) { alert("解密失敗"); }
            } else { alert("金鑰不正確"); }
        }

        async function sendMessage() {
            const input = document.getElementById('msgInput');
            let txt = input.value.trim();
            if (!txt) return;

            if (txt.startsWith('@[加密:')) {
                txt = txt.replace(/@\[加密:(.+?)\]\s*(.+)/, (m, pwd, text) => {
                    return `@[加密:${pwd}] ${CryptoJS.AES.encrypt(text, pwd).toString()}`;
                });
            }

            await supabase.from('messages').insert({
                sender: currentUser.username,
                channel_type: activeChannel.type,
                target_id: activeChannel.target,
                content: txt
            });
            input.value = '';
            loadMessages();
        }

        async function nuclearDestruct() {
            if (confirm("⚠️ 確定啟動全網銷毀？訊息將永久物理抹除！")) {
                await supabase.from('messages').delete().neq('id', 0);
                loadMessages();
            }
        }

        // --- 防護與遮罩 ---
        document.addEventListener('contextmenu', e => e.preventDefault());
        document.addEventListener('copy', e => e.preventDefault());
        document.addEventListener('keydown', e => {
            if (e.key === 'F12' || (e.ctrlKey && e.shiftKey && ['I','J','C'].includes(e.key)) || e.key === 'PrintScreen') {
                e.preventDefault(); location.reload();
            }
        });

        document.addEventListener('visibilitychange', () => {
            if (document.hidden && currentUser) {
                document.getElementById('lockMask').style.display = 'flex';
            }
        });

        function unlockScreen() {
            const code = document.getElementById('unlockCodeInput').value.trim();
            if (code === '7788' || (currentUser && code === currentUser.password)) {
                document.getElementById('lockMask').style.display = 'none';
                document.getElementById('unlockCodeInput').value = '';
            } else { alert("暗號錯誤"); }
        }
    </script>
</body>
</html>
