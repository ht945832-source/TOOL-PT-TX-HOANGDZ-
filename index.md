




         <!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>AD HOANGDZ - ELITE SYSTEM V2</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --neon: #00f2ff;
            --primary: #6366f1;
            --danger: #ff4757;
            --bg: #030712;
            --glass: rgba(15, 23, 42, 0.98);
        }

        * { 
            margin: 0; padding: 0; box-sizing: border-box; 
            font-family: 'Inter', sans-serif;
            touch-action: manipulation;
            -webkit-user-select: none;
        }

        body {
            background: var(--bg);
            color: #fff;
            height: 100vh;
            width: 100vw;
            overflow: hidden;
            position: fixed;
        }

        #bg-canvas {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            pointer-events: none; z-index: 0;
        }
        .icon-p {
            position: absolute; color: var(--neon); opacity: 0.15;
            will-change: transform; animation: fall linear infinite;
        }
        @keyframes fall {
            from { transform: translateY(-10vh) rotate(0deg); }
            to { transform: translateY(110vh) rotate(360deg); }
        }

        .page {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            display: none; padding: 30px 20px 100px; overflow-y: auto; z-index: 10;
        }
        .page.active { display: block; }
        .container { max-width: 600px; margin: 0 auto; }

        .brand-header { text-align: center; margin-bottom: 20px; }
        .brand-name { font-size: 2.8rem; font-weight: 900; color: var(--neon); text-shadow: 0 0 20px rgba(0,242,255,0.4); }
        
        .glass-card {
            background: var(--glass);
            border: 1px solid rgba(255,255,255,0.08);
            border-radius: 30px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.6);
        }

        .input-box {
            width: 100%; padding: 18px; background: #000; border: 2px solid #1e293b;
            border-radius: 20px; color: #fff; font-size: 1.1rem; text-align: center;
            font-family: monospace; margin-bottom: 15px; outline: none; transition: 0.3s;
        }
        .input-box:focus { border-color: var(--neon); box-shadow: 0 0 15px rgba(0,242,255,0.2); }

        .btn-act {
            width: 100%; padding: 18px; background: var(--neon); color: #000;
            border: none; border-radius: 20px; font-weight: 900; font-size: 1.1rem; cursor: pointer;
            text-transform: uppercase; box-shadow: 0 0 20px rgba(0,242,255,0.3);
        }

        .res-display { display: none; margin-top: 25px; text-align: center; animation: fadeInUp 0.5s; }
        @keyframes fadeInUp { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } }

        .grid-stats { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-bottom: 15px; }
        .stat-card { background: rgba(255,255,255,0.03); padding: 15px; border-radius: 15px; border: 1px solid rgba(255,255,255,0.05); }
        .val-num { font-size: 1.6rem; font-weight: 900; display: block; margin-top: 5px; color: #fff; }

        .verdict-box {
            padding: 20px; border-radius: 25px;
            background: rgba(255, 255, 255, 0.02); border: 1px solid rgba(255, 255, 255, 0.1);
        }
        .big-res { font-size: 4rem; font-weight: 900; line-height: 1; margin-bottom: 10px; }

        .detail-list { text-align: left; font-size: 0.85rem; margin-top: 15px; color: #94a3b8; }
        .detail-item { display: flex; justify-content: space-between; margin-bottom: 5px; padding: 4px 0; border-bottom: 1px solid rgba(255,255,255,0.05); }

        .nav-dock {
            position: fixed; bottom: 25px; left: 50%; transform: translateX(-50%);
            display: flex; background: rgba(15, 23, 42, 0.95); backdrop-filter: blur(20px);
            padding: 8px; border-radius: 50px; border: 1px solid rgba(255,255,255,0.1); z-index: 1000;
        }
        .nav-btn {
            padding: 12px 25px; border: none; background: none; color: #64748b;
            font-weight: 800; cursor: pointer; border-radius: 40px; transition: 0.4s;
        }
        .nav-btn.active { background: var(--neon); color: #000; }

        .hist-item {
            display: flex; justify-content: space-between; padding: 12px;
            background: rgba(255,255,255,0.02); border-radius: 12px; margin-bottom: 8px;
            border-left: 4px solid var(--neon); font-size: 0.9rem;
        }
    </style>
</head>
<body oncontextmenu="return false;">

    <div id="bg-canvas"></div>

    <nav class="nav-dock">
        <button class="nav-btn active" id="btn-home" onclick="showTab('home')">NHÀ</button>
        <button class="nav-btn" id="btn-tool" onclick="showTab('tool')">TOOL VIP</button>
    </nav>

    <!-- TRANG CHỦ -->
    <div id="page-home" class="page active">
        <div class="container">
            <div class="brand-header">
                <div class="brand-name">AD HOANGDZ</div>
                <p style="color: var(--primary); font-weight: 800; font-size: 0.8rem;">ALGORITHM V2 - ENTROPY ENGINE</p>
            </div>
            <div class="glass-card">
                <p style="color: var(--neon); font-weight: 800; margin-bottom: 10px;">🚀 CÔNG NGHỆ MỚI:</p>
                <p style="font-size: 0.9rem; line-height: 1.6; color: #cbd5e1;">
                    Hệ thống đã nâng cấp thuật toán <b>MD5 Entropy & Bit Analysis</b>. 
                    Dữ liệu được bóc tách qua 4 lớp phương pháp (Binary, Hex-Sum, Entropy, Last-Char) để đưa ra dự đoán chính xác nhất.
                </p>
            </div>
        </div>
    </div>

    <!-- TRANG TOOL -->
    <div id="page-tool" class="page">
        <div class="container">
            <div class="brand-header">
                <h2 style="font-weight: 900; letter-spacing: 2px;">BẢNG PHÂN TÍCH <span style="color: var(--neon);">PRO</span></h2>
            </div>

            <div class="glass-card">
                <input type="text" id="md5-input" class="input-box" placeholder="Dán mã MD5 (32 ký tự)..." maxlength="32">
                <button class="btn-act" onclick="runAnalysis()">PHÂN TÍCH HỆ THỐNG</button>

                <div id="result-view" class="res-display">
                    <div class="grid-stats">
                        <div class="stat-card">
                            <small style="color:var(--neon); font-weight:800;">BIT RATE (TÀI)</small>
                            <b id="bit-rate" class="val-num">0%</b>
                        </div>
                        <div class="stat-card">
                            <small style="color:var(--primary); font-weight:800;">ENTROPY</small>
                            <b id="entropy-val" class="val-num">0</b>
                        </div>
                    </div>

                    <div class="verdict-box">
                        <div class="big-res" id="final-res">---</div>
                        <div id="final-signal" style="font-weight: 800; font-size: 1.1rem;">-- --</div>
                        <div id="confidence" style="font-size: 0.9rem; color: #94a3b8; margin-top: 5px;">Độ tin cậy: 0%</div>
                    </div>

                    <div class="detail-list">
                        <div class="detail-item"><span>Phương pháp Binary (Bit > 64)</span> <b id="m1">--</b></div>
                        <div class="detail-item"><span>Phương pháp Entropy (> 3.5)</span> <b id="m2">--</b></div>
                        <div class="detail-item"><span>Phương pháp Hex-Sum (Even)</span> <b id="m3">--</b></div>
                        <div class="detail-item"><span>Phương pháp Last-Char (Dec)</span> <b id="m4">--</b></div>
                    </div>
                </div>
            </div>

            <div class="glass-card">
                <h4 style="margin-bottom: 15px; color: var(--neon);"><i class="fas fa-history"></i> LỊCH SỬ PHIÊN</h4>
                <div id="history-box"></div>
            </div>
        </div>
    </div>

    <script>
        // Hiệu ứng icon rơi (giữ nguyên phong cách cũ)
        const icons = ['fa-bolt', 'fa-code', 'fa-microchip', 'fa-shield-virus'];
        function spawn() {
            const container = document.getElementById('bg-canvas');
            for(let i=0; i<20; i++) {
                setTimeout(() => {
                    const icon = document.createElement('i');
                    icon.className = `fas ${icons[Math.floor(Math.random()*icons.length)]} icon-p`;
                    icon.style.left = Math.random() * 100 + 'vw';
                    icon.style.animationDuration = (Math.random() * 3 + 4) + 's';
                    icon.style.fontSize = (Math.random() * 10 + 12) + 'px';
                    container.appendChild(icon);
                    icon.addEventListener('animationend', () => icon.remove());
                }, i * 300);
            }
        }
        spawn(); setInterval(spawn, 8000);

        function showTab(tab) {
            document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
            document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
            document.getElementById('page-' + tab).classList.add('active');
            document.getElementById('btn-' + tab).classList.add('active');
        }

        // --- THUẬT TOÁN NÂNG CẤP ---
        
        function calculateEntropy(str) {
            const freq = {};
            for (let char of str) freq[char] = (freq[char] || 0) + 1;
            let entropy = 0;
            const len = str.length;
            for (let char in freq) {
                const p = freq[char] / len;
                entropy -= p * Math.log2(p);
            }
            return entropy;
        }

        function runAnalysis() {
            const input = document.getElementById('md5-input').value.trim().toLowerCase();
            if(input.length !== 32) {
                alert("Vui lòng nhập đúng mã MD5 32 ký tự!");
                return;
            }

            // 1. Chuyển sang Binary & Đếm Bit 1
            let binaryStr = "";
            let hexSum = 0;
            for(let char of input) {
                const val = parseInt(char, 16);
                binaryStr += val.toString(2).padStart(4, '0');
                hexSum += val;
            }
            const bit1Count = (binaryStr.match(/1/g) || []).length;
            const bitRate = ((bit1Count / 128) * 100).toFixed(1);

            // 2. Tính Entropy
            const entropy = calculateEntropy(input);

            // 3. Logic 4 phương pháp
            const m1 = bit1Count > 64 ? "TÀI" : "XỈU"; // Binary
            const m2 = entropy > 3.5 ? "TÀI" : "XỈU";  // Entropy
            const m3 = hexSum % 2 === 0 ? "TÀI" : "XỈU"; // Hex Sum
            const m4 = parseInt(input[31], 16) % 2 === 0 ? "TÀI" : "XỈU"; // Last Char

            const votes = [m1, m2, m3, m4];
            const taiVotes = votes.filter(v => v === "TÀI").length;
            const finalResult = taiVotes >= 2 ? "TÀI" : "XỈU";
            const confidence = 65 + (taiVotes === 4 || taiVotes === 0 ? 25 : (taiVotes === 3 || taiVotes === 1 ? 15 : 5));

            // Hiển thị UI
            document.getElementById('result-view').style.display = 'block';
            document.getElementById('bit-rate').innerText = bitRate + "%";
            document.getElementById('entropy-val').innerText = entropy.toFixed(3);
            
            const rTxt = document.getElementById('final-res');
            rTxt.innerText = finalResult;
            rTxt.style.color = finalResult === "TÀI" ? "var(--neon)" : "var(--danger)";

            const sTxt = document.getElementById('final-signal');
            if(confidence >= 85) { sTxt.innerText = "TÍN HIỆU CỰC MẠNH"; sTxt.style.color = "#00ff88"; }
            else if(confidence >= 75) { sTxt.innerText = "TÍN HIỆU TỐT"; sTxt.style.color = "#fbbf24"; }
            else { sTxt.innerText = "TÍN HIỆU YẾU"; sTxt.style.color = "#94a3b8"; }

            document.getElementById('confidence').innerText = `Độ tin cậy: ${confidence}%`;

            // Chi tiết phương pháp
            const setMethodUI = (id, res) => {
                const el = document.getElementById(id);
                el.innerText = res;
                el.style.color = res === "TÀI" ? "var(--neon)" : "var(--danger)";
            };
            setMethodUI('m1', m1);
            setMethodUI('m2', m2);
            setMethodUI('m3', m3);
            setMethodUI('m4', m4);

            // Lịch sử
            const hBox = document.getElementById('history-box');
            const item = document.createElement('div');
            item.className = 'hist-item';
            item.innerHTML = `<span>#${input.slice(-6)}</span> <b style="color:${finalResult === 'TÀI' ? 'var(--neon)' : 'var(--danger)'}">${finalResult}</b> <small>${confidence}%</small>`;
            hBox.prepend(item);
            if(hBox.children.length > 5) hBox.lastChild.remove();
        }
    </script>
</body>
</html>
