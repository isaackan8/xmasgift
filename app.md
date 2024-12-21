<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>刮刮樂遊戲</title>
</head>
<body>
    <!-- 這<!DOCTYPE html>
<html>
<head>
    <title>100個喜歡珍珠刮刮樂</title>
    <div style="text-align: center; font-size: 1.5em; color: #ff0000; margin-top: 20px; font-weight: bold; text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);">
    Merry Christmas 🎄
</div>
    <style>
        body {
            display: flex;
            flex-direction: column;
            align-items: center;
            background: #2b2b2b;
            font-family: Arial, sans-serif;
            color: white;
            cursor: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10" fill="%23ffd700" stroke="%23b8860b" stroke-width="2"/><text x="12" y="16" font-size="12" text-anchor="middle" fill="%23b8860b">$</text></svg>') 12 12, auto;
        }
        .grid {
            display: grid;
            grid-template-columns: repeat(10, 1fr);
            gap: 5px;
            max-width: 800px;
            margin: 20px;
            background: #1a1a1a;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 0 30px rgba(255,215,0,0.2);
        }
        .number {
            width: 60px;
            height: 60px;
            background: linear-gradient(45deg, #c0c0c0, #808080);
            border: 2px solid #ffd700;
            border-radius: 5px;
            font-size: 20px;
            color: white;
            cursor: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10" fill="%23ffd700" stroke="%23b8860b" stroke-width="2"/><text x="12" y="16" font-size="12" text-anchor="middle" fill="%23b8860b">$</text></svg>') 12 12, pointer;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        .number::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 200%;
            height: 100%;
            background: linear-gradient(
                90deg,
                rgba(255,255,255,0) 0%,
                rgba(255,255,255,0.2) 50%,
                rgba(255,255,255,0) 100%
            );
            transition: 0.5s;
        }
        .number:hover::before {
            left: 100%;
        }
        .number.scratched {
            background: linear-gradient(45deg, #ffd700, #ffa500);
            transform: scale(0.95);
        }
        .message {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: rgba(255,215,0,0.9);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(255,215,0,0.5);
            display: none;
            z-index: 100;
            color: black;
            font-size: 18px;
            text-align: center;
            min-width: 200px;
            cursor: default;
        }
        h1 {
            color: #ffd700;
            text-shadow: 0 0 10px rgba(255,215,0,0.5);
            margin: 30px 0;
            cursor: default;
        }
    </style>
</head>
<body>
    <h1>100個喜歡珍珠刮刮樂</h1>
    <div class="grid" id="numberGrid"></div>
    <div class="message" id="message"></div>

    <script>
        const messages = [
            "我超愛珍珠奶茶！",
            "珍珠好好吃喔！",
            "沒有珍珠的奶茶不完整！",
            "珍珠是我的快樂泉源！",
            "今天也要喝珍奶！",
            "珍珠Q彈有嚼勁！",
            "珍珠是我的生命！",
            "沒有珍珠我會生氣！",
            "珍珠是我的維他命！",
            "珍珠使我快樂！"
        ];

        // 建立一個映射來存儲每個號碼對應的訊息
        const numberMessages = {};

        function shuffleMessages() {
            // 複製訊息陣列並重複10次以達到100個訊息
            let allMessages = [];
            for(let i = 0; i < 10; i++) {
                allMessages = allMessages.concat([...messages]);
            }
            
            // 打亂訊息順序
            for(let i = allMessages.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [allMessages[i], allMessages[j]] = [allMessages[j], allMessages[i]];
            }
            
            // 為每個號碼分配一個訊息
            for(let i = 1; i <= 100; i++) {
                numberMessages[i] = allMessages[i-1];
            }
        }

        function createGrid() {
            const grid = document.getElementById('numberGrid');
            for (let i = 1; i <= 100; i++) {
                const button = document.createElement('button');
                button.className = 'number';
                button.textContent = i;
                button.onclick = () => scratchNumber(button, i);
                grid.appendChild(button);
            }
        }

        function scratchNumber(button, number) {
            button.classList.add('scratched');
            const message = document.getElementById('message');
            message.textContent = numberMessages[number];
            message.style.display = 'block';
            
            setTimeout(() => {
                message.style.display = 'none';
            }, 1500);
        }

        // 初始化時打亂訊息
        shuffleMessages();
        createGrid();
    </script>
</body>
</html>
<!-- 1. 增加刮開動畫效果 -->
<style>
.number {
    transition: all 0.3s;
    position: relative;
    overflow: hidden;
}

.scratched {
    transform: scale(0.9);
    background: #f0f0f0 !important;
}

.number:before {
    content: "";
    position: absolute;
    top: 0;
    left: -100%;
    width: 200%;
    height: 100%;
    background: rgba(255,255,255,0.3);
    transform: skewX(-20deg);
    transition: 0.5s;
}

.scratched:before {
    left: 100%;
}
</style>

<script>
// 2. 增加音效
function playSound() {
    const audio = new Audio('https://www.soundjay.com/misc/sounds/scratch-1.mp3');
    audio.play();
}

// 3. 增加計數器功能
let scratchedCount = 0;
function updateCounter() {
    scratchedCount++;
    const counter = document.createElement('div');
    counter.textContent = `已刮開: ${scratchedCount}/100`;
    document.body.appendChild(counter);
}

</script>
<style>
.progress-bar {
    position: fixed;
    bottom: 20px;
    left: 50%;
    transform: translateX(-50%);
    width: 80%;
    max-width: 600px;
    height: 30px;
    background: rgba(26, 26, 26, 0.8);
    border-radius: 15px;
    border: 2px solid #ffd700;
    overflow: hidden;
    box-shadow: 0 0 20px rgba(255, 215, 0, 0.2);
}

.progress-fill {
    height: 100%;
    width: 0%;
    background: linear-gradient(45deg, #ffd700, #ffa500);
    transition: width 0.3s ease;
}

.progress-text {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: white;
    font-weight: bold;
    text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
}
</style>

<script>
// 更新計數器功能
const progressBar = document.createElement('div');
progressBar.className = 'progress-bar';
progressBar.innerHTML = `
    <div class="progress-fill"></div>
    <div class="progress-text">已刮開: 0/100</div>
`;
document.body.appendChild(progressBar);

// 修改原本的 scratchNumber 函數來整合進度條
const originalScratchNumber = window.scratchNumber;
window.scratchNumber = function(button, number) {
    if (!button.classList.contains('scratched')) {
        originalScratchNumber(button, number);
        updateCounter();
    }
}

function updateCounter() {
    scratchedCount++;
    const progressFill = document.querySelector('.progress-fill');
    const progressText = document.querySelector('.progress-text');
    const percentage = (scratchedCount / 100) * 100;
    
    progressFill.style.width = `${percentage}%`;
    progressText.textContent = `已刮開: ${scratchedCount}/100`;
}
</script>
<style>
.scratch-title {
    text-align: center;
    font-size: 2.5em;
    color: #ffd700;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
    margin: 20px 0;
    font-weight: bold;
}

.scratch-subtitle {
    text-align: center;
    font-size: 1.2em;
    color: #ffa500;
    margin-bottom: 30px;
}
</style>

<div class="scratch-title">高達100次中獎機會</div>
<div class="scratch-subtitle">刮開方格，看看您能中多少獎!</div>
<script>
// 調整訊息顯示時間為原本的1.5倍
const originalShowMessage = window.showMessage;
window.showMessage = function(message, isWin = false) {
    const messageDiv = document.createElement('div');
    messageDiv.className = 'message';
    messageDiv.textContent = message;
    if (isWin) {
        messageDiv.classList.add('win');
    }
    document.body.appendChild(messageDiv);
    
    // 延長顯示時間至1.5秒 (原本是1秒)
    setTimeout(() => {
        messageDiv.remove();
    }, 1500);
}
</script>
<script>
// 監聽刮開次數的變化
function checkCompletion() {
    if (scratchedCount === 100) {
        // 創建煙花效果
        createFireworks();
        // 顯示恭喜訊息
        showCongratulations();
    }
}

// 在原有的updateCounter函數中添加檢查
const originalUpdateCounter = updateCounter;
updateCounter = function() {
    originalUpdateCounter();
    checkCompletion();
}

// 創建煙花效果
function createFireworks() {
    for (let i = 0; i < 10; i++) {
        setTimeout(() => {
            const firework = document.createElement('div');
            firework.className = 'firework';
            firework.style.left = Math.random() * window.innerWidth + 'px';
            firework.style.top = Math.random() * window.innerHeight + 'px';
            document.body.appendChild(firework);
            
            setTimeout(() => {
                firework.remove();
            }, 1000);
        }, i * 300);
    }
}

// 顯示恭喜訊息
function showCongratulations() {
    const congrats = document.createElement('div');
    congrats.className = 'congratulations';
    congrats.innerHTML = '🎉 恭喜得到PEARL🎉';
    document.body.appendChild(congrats);
    
    setTimeout(() => {
        congrats.remove();
    }, 5000);
}
</script>

<style>
.firework {
    position: fixed;
    width: 10px;
    height: 10px;
    border-radius: 50%;
    background: radial-gradient(circle, #ffd700, #ff6b6b);
    animation: explode 1s ease-out forwards;
    pointer-events: none;
}

.congratulations {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: rgba(0, 0, 0, 0.8);
    color: #ffd700;
    padding: 20px 40px;
    border-radius: 10px;
    font-size: 24px;
    z-index: 1000;
    animation: bounce 0.5s ease infinite alternate;
}

@keyframes explode {
    0% {
        transform: scale(1);
        opacity: 1;
    }
    100% {
        transform: scale(20);
        opacity: 0;
    }
}

@keyframes bounce {
    from {
        transform: translate(-50%, -50%) scale(1);
    }
    to {
        transform: translate(-50%, -50%) scale(1.1);
    }
}
</style>
</body>
</html>
