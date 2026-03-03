<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Unit 6: Education - Smart World 7 (Full Test)</title>
    <link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@400;600;800&family=Nunito:wght@400;700;900&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.5.1/dist/confetti.browser.min.js"></script>
    <style>
        :root {
            --primary: #8854C0;
            --secondary: #FDCB6E;
            --success: #00D26A;
            --error: #FF4757;
            --info: #00C9A7;
            --bg-gradient: linear-gradient(-45deg, #8854C0, #00C9A7, #FDCB6E, #FF7675);
        }

        * { box-sizing: border-box; }

        @keyframes gradientBG {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        @keyframes floatPattern {
            0% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(5deg); }
            100% { transform: translateY(0) rotate(0deg); }
        }

        body {
            font-family: 'Nunito', sans-serif;
            margin: 0;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            background: var(--bg-gradient);
            background-size: 400% 400%;
            animation: gradientBG 15s ease infinite;
            position: relative;
            padding: 20px;
            color: #2d3436;
        }

        /* SVG Pattern Lơ lửng */
        body::before {
            content: "";
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background-image: 
                url("data:image/svg+xml,%3Csvg width='80' height='80' viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M50 10 L60 40 L90 50 L60 60 L50 90 L40 60 L10 50 L40 40 Z' fill='%23ffffff' fill-opacity='0.15'/%3E%3Ccircle cx='20' cy='20' r='5' fill='%23ffffff' fill-opacity='0.1'/%3E%3Ccircle cx='80' cy='80' r='8' fill='%23ffffff' fill-opacity='0.1'/%3E%3C/svg%3E"),
                url("data:image/svg+xml,%3Csvg width='120' height='120' viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Ctext x='10' y='30' font-size='20' fill='%23ffffff' fill-opacity='0.1' font-family='sans-serif'%3E🍋%3C/text%3E%3Ctext x='70' y='80' font-size='25' fill='%23ffffff' fill-opacity='0.1' font-family='sans-serif'%3E🐱%3C/text%3E%3C/svg%3E");
            z-index: -1;
            animation: floatPattern 8s ease-in-out infinite;
            pointer-events: none;
        }

        .header {
            text-align: center;
            color: white;
            text-shadow: 2px 2px 0px rgba(0,0,0,0.2);
            margin-bottom: 30px;
        }

        .header h3 { margin: 0; font-size: 1.2rem; font-weight: 700; background: rgba(0,0,0,0.2); display: inline-block; padding: 5px 15px; border-radius: 20px;}
        .header h1 { font-size: 3rem; margin: 10px 0; font-weight: 900; letter-spacing: 2px;}

        .container {
            width: 100%;
            max-width: 900px;
            background: rgba(255, 255, 255, 0.98);
            border-radius: 30px;
            padding: 40px;
            box-shadow: 0 20px 50px rgba(0,0,0,0.2);
            margin-bottom: 80px;
        }

        .section-title {
            color: white;
            background: var(--primary);
            padding: 10px 20px;
            border-radius: 15px;
            margin: 40px -20px 20px -20px;
            text-transform: uppercase;
            font-weight: 900;
            box-shadow: 0 5px 0 #6c4298;
            text-align: center;
        }

        .passage-box {
            background: #fdf6e3;
            border: 3px dashed var(--secondary);
            padding: 20px;
            border-radius: 15px;
            margin-bottom: 25px;
            font-size: 1.1rem;
            line-height: 1.8;
            font-family: 'Quicksand', sans-serif;
            font-weight: 600;
        }

        .question-card {
            background: white;
            border: 3px solid #f1f2f6;
            border-radius: 20px;
            padding: 25px;
            margin-bottom: 30px;
            position: relative;
            transition: all 0.3s;
        }

        .question-card:hover { border-color: var(--info); }

        .question-text {
            font-size: 1.25rem;
            font-weight: 800;
            margin-bottom: 20px;
            color: #2d3436;
            line-height: 1.5;
        }

        u { color: #e84393; text-decoration: underline; font-weight: 900; }

        /* Nút trắc nghiệm */
        .options-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
        }

        .option-btn {
            background: white;
            border: 3px solid #dfe4ea;
            border-bottom-width: 6px;
            border-radius: 15px;
            padding: 15px;
            font-family: 'Nunito', sans-serif;
            font-weight: 700;
            font-size: 1.1rem;
            color: #2f3542;
            cursor: pointer;
            transition: all 0.15s ease;
            text-align: left;
            display: flex;
            align-items: center;
        }

        .option-btn:hover {
            transform: translateY(-3px);
            border-color: var(--info);
            background: #f0fbf9;
        }

        .option-btn:active {
            transform: translateY(3px);
            border-bottom-width: 3px;
        }

        .option-btn.correct {
            background-color: var(--success) !important;
            border-color: #00a854 !important;
            color: white;
            box-shadow: 0 5px 0 #00a854;
        }

        .option-btn.wrong {
            background-color: var(--error) !important;
            border-color: #d63031 !important;
            color: white;
            animation: shake 0.4s;
            box-shadow: 0 5px 0 #d63031;
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-10px); }
            75% { transform: translateX(10px); }
        }

        /* Input cho Tự luận / Điền từ */
        .input-group {
            display: flex;
            gap: 10px;
            margin-top: 10px;
        }

        .text-input {
            flex: 1;
            padding: 15px;
            font-size: 1.1rem;
            font-family: 'Quicksand', sans-serif;
            font-weight: 700;
            border: 3px solid #dfe4ea;
            border-radius: 15px;
            outline: none;
            transition: border-color 0.2s;
        }

        .text-input:focus { border-color: var(--primary); }

        .check-btn {
            padding: 15px 25px;
            background: var(--info);
            color: white;
            border: none;
            border-radius: 15px;
            font-size: 1.1rem;
            font-weight: 800;
            cursor: pointer;
            border-bottom: 5px solid #00997f;
            transition: all 0.1s;
        }
        .check-btn:active { transform: translateY(5px); border-bottom-width: 0; }

        .gap-input {
            display: inline-block;
            min-width: 120px;
            border-bottom: 3px dashed var(--primary);
            color: var(--primary);
            font-weight: 800;
            cursor: pointer;
            text-align: center;
            padding: 0 10px;
            background: rgba(136, 84, 192, 0.1);
            border-radius: 5px;
            transition: all 0.2s;
        }
        .gap-input:hover { background: rgba(136, 84, 192, 0.2); transform: scale(1.05); }
        .gap-input.done-correct { background: var(--success); color: white; border-bottom: none; }
        .gap-input.done-wrong { background: var(--error); color: white; border-bottom: none; }

        /* Giải thích siêu chi tiết */
        .explanation {
            display: none;
            margin-top: 20px;
            padding: 20px;
            background: #f8f9fa;
            border-left: 6px solid var(--primary);
            border-radius: 12px;
            font-size: 1.05rem;
            color: #2d3436;
            line-height: 1.6;
            animation: fadeIn 0.5s ease;
        }

        .explanation h4 { margin: 0 0 10px 0; color: var(--primary); font-size: 1.2rem; display: flex; align-items: center; gap: 5px;}
        
        @keyframes fadeIn { from { opacity: 0; transform: translateY(-10px); } to { opacity: 1; transform: translateY(0); } }

        /* UI Chấm điểm */
        .score-box {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: white;
            padding: 15px 30px;
            border-radius: 50px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.3);
            font-weight: 900;
            font-size: 1.2rem;
            color: var(--primary);
            z-index: 1000;
            display: flex;
            align-items: center;
            gap: 15px;
            border: 3px solid #f1f2f6;
        }
        .score-correct { color: var(--success); }
        .score-wrong { color: var(--error); }

        .submit-btn {
            display: block;
            width: 100%;
            padding: 20px;
            background: linear-gradient(to right, #00D26A, #00C9A7);
            color: white;
            border: none;
            border-radius: 20px;
            font-size: 1.5rem;
            font-weight: 900;
            cursor: pointer;
            margin-top: 50px;
            box-shadow: 0 10px 0 #009950;
            transition: all 0.1s;
        }
        .submit-btn:active { transform: translateY(10px); box-shadow: 0 0 0 #009950; }

        /* Hình ảnh CSS cho Q15, Q16 */
        .css-sign {
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            width: 200px;
            height: 200px;
            margin: 0 auto 20px auto;
            border-radius: 20px;
            border: 5px solid #2d3436;
            background: white;
            text-align: center;
            padding: 10px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
        }
        .sign-15-icon { font-size: 4rem; background: #0984e3; color: white; width: 100px; height: 100px; border-radius: 50%; display: flex; align-items: center; justify-content: center; margin-bottom: 10px;}
        .sign-15-text { font-weight: 900; font-size: 1.1rem; }
        
        .css-sign-16 {
            background: linear-gradient(to bottom right, #74b9ff, #0984e3);
            flex-direction: row;
            width: 100%; max-width: 350px; padding: 20px; gap: 15px;
        }
        .sign-16-pencil { font-size: 4rem; animation: floatPattern 3s infinite;}
        .sign-16-bubble { background: white; padding: 15px; border-radius: 15px; font-weight: 900; position: relative;}
        .sign-16-bubble::before { content: ''; position: absolute; left: -10px; top: 50%; transform: translateY(-50%); border-width: 10px 10px 10px 0; border-style: solid; border-color: transparent white transparent transparent; }

        @media (max-width: 768px) {
            .options-grid { grid-template-columns: 1fr; }
            .header h1 { font-size: 2rem; }
        }
    </style>
</head>
<body>

    <div class="header">
        <h3>Giáo viên tạo: Ms Mai An ULIS</h3>
        <h1>UNIT 6: EDUCATION</h1>
        <p style="font-size: 1.2rem; font-weight: 700;">i-LEARN SMART WORLD 7 - THE ULTIMATE TEST</p>
    </div>

    <div class="container" id="quiz-container">
        </div>

    <div class="score-box">
        <span class="score-correct">Đúng: <span id="score-correct">0</span></span>
        <span>|</span>
        <span class="score-wrong">Sai: <span id="score-wrong">0</span></span>
    </div>

    <script>
        // Web Audio API
        const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
        function playSound(type) {
            if(audioCtx.state === 'suspended') audioCtx.resume();
            const osc = audioCtx.createOscillator();
            const gain = audioCtx.createGain();
            osc.connect(gain);
            gain.connect(audioCtx.destination);
            
            if (type === 'correct') {
                osc.type = 'sine';
                osc.frequency.setValueAtTime(523.25, audioCtx.currentTime); // C5
                osc.frequency.exponentialRampToValueAtTime(880, audioCtx.currentTime + 0.15);
                gain.gain.setValueAtTime(0.3, audioCtx.currentTime);
                gain.gain.exponentialRampToValueAtTime(0.01, audioCtx.currentTime + 0.3);
                osc.start(); osc.stop(audioCtx.currentTime + 0.3);
            } else {
                osc.type = 'sawtooth';
                osc.frequency.setValueAtTime(150, audioCtx.currentTime);
                osc.frequency.linearRampToValueAtTime(80, audioCtx.currentTime + 0.3);
                gain.gain.setValueAtTime(0.3, audioCtx.currentTime);
                gain.gain.exponentialRampToValueAtTime(0.01, audioCtx.currentTime + 0.3);
                osc.start(); osc.stop(audioCtx.currentTime + 0.3);
            }
        }

        function triggerConfetti() {
            confetti({ particleCount: 150, spread: 80, origin: { y: 0.6 }, colors: ['#8854C0', '#FDCB6E', '#00D26A', '#FF4757'] });
        }

        // DỮ LIỆU CÂU HỎI SIÊU CHI TIẾT
        const db = [
            { type: 'title', title: 'I. PRONUNCIATION & STRESS' },
            { 
                id: 1, type: 'mcq', 
                q: "1. Choose the word whose underlined part is pronounced differently.",
                options: [
                    { text: "b<u>e</u>fore", correct: false },
                    { text: "r<u>e</u>port", correct: false },
                    { text: "d<u>e</u>lighted", correct: false },
                    { text: "unif<u>o</u>rm", correct: true }
                ],
                exp: "1. Dịch câu hỏi: Chọn từ có phần gạch chân phát âm khác.<br>2. Phân tích 4 đáp án:<br>A. before /bɪˈfɔːr/ (âm /ɪ/)<br>B. report /rɪˈpɔːrt/ (âm /ɪ/)<br>C. delighted /dɪˈlaɪtɪd/ (âm /ɪ/)<br>D. uniform /ˈjuːnɪfɔːrm/ (âm /ɔː/ hoặc không có /ɪ/ ở âm tương ứng).<br>*(Ghi chú: Đề gốc bị lỗi font, giáo viên đã chuẩn hóa thành kiểm tra âm /ɪ/)*<br>3. Chọn D vì là âm khác biệt."
            },
            { 
                id: 2, type: 'mcq', 
                q: "2. Choose the word whose underlined part is pronounced differently.",
                options: [
                    { text: "excit<u>ed</u>", correct: true },
                    { text: "annoy<u>ed</u>", correct: false },
                    { text: "surpris<u>ed</u>", correct: false },
                    { text: "pleas<u>ed</u>", correct: false }
                ],
                exp: "1. Dịch: Chọn từ có đuôi -ed phát âm khác.<br>2. Phân tích:<br>A. excited /ɪkˈsaɪtɪd/ (âm /ɪd/ vì kết thúc bằng t).<br>B. annoyed /əˈnɔɪd/ (âm /d/).<br>C. surprised /səˈpraɪzd/ (âm /d/).<br>D. pleased /pliːzd/ (âm /d/).<br>3. Chọn A. Các đáp án B, C, D đều phát âm là /d/."
            },
            { 
                id: 3, type: 'mcq', 
                q: "3. Choose the word that has a different stressed syllable.",
                options: [
                    { text: "classmate", correct: false },
                    { text: "finish", correct: false },
                    { text: "homework", correct: false },
                    { text: "abroad", correct: true }
                ],
                exp: "1. Dịch: Chọn từ có trọng âm khác.<br>2. Phân tích:<br>A. 'classmate (nhấn âm 1).<br>B. 'finish (nhấn âm 1).<br>C. 'homework (nhấn âm 1).<br>D. a'broad (nhấn âm 2).<br>3. Chọn D vì trọng âm rơi vào âm tiết 2, còn lại âm 1."
            },
            { 
                id: 4, type: 'mcq', 
                q: "4. Choose the word that has a different stressed syllable.",
                options: [
                    { text: "difficult", correct: false },
                    { text: "however", correct: true },
                    { text: "positive", correct: false },
                    { text: "chemistry", correct: false }
                ],
                exp: "1. Phân tích 4 đáp án:<br>A. 'difficult (nhấn âm 1).<br>B. how'ever (nhấn âm 2).<br>C. 'positive (nhấn âm 1).<br>D. 'chemistry (nhấn âm 1).<br>2. Chọn B. 'however' nhấn âm 2, ba từ còn lại nhấn âm 1."
            },
            
            { type: 'title', title: 'II. VOCABULARY AND GRAMMAR' },
            { 
                id: 5, type: 'mcq', 
                q: "5. Sammy studied really hard, so she _______ all of her tests.",
                options: [
                    { text: "passed", correct: true },
                    { text: "failed", correct: false },
                    { text: "got", correct: false },
                    { text: "did", correct: false }
                ],
                exp: "1. Dịch: Sammy học rất chăm chỉ, vì vậy cô ấy đã ___ tất cả bài kiểm tra.<br>2. Nghĩa các từ:<br>A. passed (v): thi đậu/vượt qua.<br>B. failed (v): thi trượt.<br>C. got (v): lấy/có được.<br>D. did (v): làm.<br>3. Tại sao chọn A? Vì vế trước là 'studied really hard' (học chăm chỉ) nên kết quả phải là thi đậu (passed). Loại B vì sai ngữ cảnh, C và D không tạo thành cụm từ hợp lý trong ngữ cảnh này."
            },
            { 
                id: 6, type: 'mcq', 
                q: "6. Student A: How's the course going? - Student B: I'm _______ enjoying it.",
                options: [
                    { text: "very", correct: false },
                    { text: "much", correct: false },
                    { text: "really", correct: true },
                    { text: "a lot", correct: false }
                ],
                exp: "1. Dịch: A: Khóa học thế nào rồi? B: Tôi ___ thích nó.<br>2. Phân tích ngữ pháp: Động từ 'enjoying' (đang thích) cần một trạng từ bổ nghĩa đứng trước.<br>3. Chọn C. 'really' (thực sự) được dùng trước động từ để nhấn mạnh (I'm really enjoying it).<br>4. Tại sao sai: 'very' không đứng trực tiếp trước động từ; 'much' thường dùng trong câu phủ định/nghi vấn hoặc sau động từ; 'a lot' phải đứng ở cuối câu (enjoying it a lot)."
            },
            { 
                id: 7, type: 'mcq', 
                q: "7. Ivy was so _______ because she failed two tests last semester.",
                options: [
                    { text: "pleased", correct: false },
                    { text: "delighted", correct: false },
                    { text: "relaxed", correct: false },
                    { text: "upset", correct: true }
                ],
                exp: "1. Dịch: Ivy đã rất ___ vì cô ấy thi trượt 2 bài kiểm tra học kỳ trước.<br>2. Nghĩa 4 đáp án: A. pleased (hài lòng); B. delighted (vui mừng); C. relaxed (thư giãn); D. upset (buồn bã/thất vọng).<br>3. Chọn D. 'failed two tests' (trượt 2 bài kiểm tra) là nguyên nhân tiêu cực, nên cảm xúc phải là 'upset' (buồn). Loại A, B, C vì mang nghĩa tích cực."
            },
            { 
                id: 8, type: 'mcq', 
                q: "8. We _______ buy lunch in the canteen. There's a shop next to the school and it sells sandwiches and other snacks.",
                options: [
                    { text: "have to", correct: false },
                    { text: "don't have to", correct: true },
                    { text: "mustn't", correct: false },
                    { text: "should", correct: false }
                ],
                exp: "1. Dịch: Chúng ta ___ mua bữa trưa ở căng-tin. Có một cửa hàng cạnh trường bán bánh mì kẹp và đồ ăn vặt.<br>2. Phân tích cấu trúc: A. have to (phải làm); B. don't have to (không cần phải); C. mustn't (cấm); D. should (nên).<br>3. Chọn B. Vì đã có cửa hàng bán đồ ăn bên ngoài (sự lựa chọn khác) nên việc mua ở căng tin là 'không bắt buộc/không cần thiết' (don't have to)."
            },
            { 
                id: 9, type: 'mcq', 
                q: "9. The teacher asked us to choose a book from the list, read it at home and then write a _______ about it.",
                options: [
                    { text: "project", correct: false },
                    { text: "presentation", correct: false },
                    { text: "report", correct: true },
                    { text: "revision", correct: false }
                ],
                exp: "1. Dịch: Giáo viên yêu cầu chúng tôi chọn 1 quyển sách, đọc ở nhà và sau đó viết một ___ về nó.<br>2. Nghĩa 4 đáp án: A. project (dự án); B. presentation (bài thuyết trình); C. report (bài báo cáo); D. revision (sự ôn tập).<br>3. Chọn C. Viết về một cuốn sách đã đọc thì gọi là 'book report' (báo cáo sách). 'write a report' là collocation (cụm từ cố định) chuẩn."
            },
            { 
                id: 10, type: 'mcq', 
                q: "10. Our math teacher, Mr. Thomas is funny and friendly, but he gives us too much _______ to do after school.",
                options: [
                    { text: "homework", correct: true },
                    { text: "exams", correct: false },
                    { text: "essays", correct: false },
                    { text: "tests", correct: false }
                ],
                exp: "1. Dịch: Thầy dạy Toán Thomas rất vui tính, nhưng thầy cho chúng tôi quá nhiều ___ để làm sau giờ học.<br>2. Phân tích: 'too much' (quá nhiều) chỉ đi với danh từ KHÔNG đếm được.<br>3. Chọn A. 'homework' là danh từ không đếm được. Các đáp án B (exams), C (essays), D (tests) đều là danh từ đếm được số nhiều (nếu dùng phải đi với 'too many')."
            },
            { 
                id: 11, type: 'mcq', 
                q: "11. Nick got 100% on his physics test. His twin brother, Adam, _______ had to retake the test.",
                options: [
                    { text: "although", correct: false },
                    { text: "but", correct: false },
                    { text: "so", correct: false },
                    { text: "however", correct: true }
                ],
                exp: "1. Dịch: Nick đạt 100% bài kiểm tra vật lý. _____, anh sinh đôi Adam lại phải thi lại.<br>2. Phân tích: Hai vế câu mang nghĩa đối lập. Vị trí từ cần điền đứng sau dấu phẩy (,) và trước dấu phẩy hoặc ở giữa câu để bổ nghĩa.<br>3. Chọn D. 'However' (Tuy nhiên) có thể đứng sau chủ ngữ (Adam, however, had to...). 'Although', 'but', 'so' không đứng độc lập giữa các thành phần câu theo cách này."
            },
            { 
                id: 12, type: 'mcq', 
                q: "12. I'm really _______ with Nick. We have an important biology project, but he doesn't do his part.",
                options: [
                    { text: "hopeful", correct: false },
                    { text: "annoyed", correct: true },
                    { text: "pleased", correct: false },
                    { text: "excited", correct: false }
                ],
                exp: "1. Dịch: Tôi thực sự ___ với Nick. Chúng tôi có một dự án sinh học quan trọng, nhưng cậu ấy không làm phần của mình.<br>2. Phân tích nghĩa: Việc Nick lười biếng sẽ gây ra cảm giác khó chịu.<br>3. Chọn B. 'annoyed' (bực mình/khó chịu). A, C, D đều là cảm xúc tích cực, sai ngữ cảnh."
            },
            { 
                id: 13, type: 'mcq', 
                q: "13. Yesterday, I wrote a(n) _______ about the benefits of studying overseas, and the teacher said it was good.",
                options: [
                    { text: "homework", correct: false },
                    { text: "test", correct: false },
                    { text: "essay", correct: true },
                    { text: "paper", correct: false }
                ],
                exp: "1. Dịch: Hôm qua, tôi đã viết một ___ về lợi ích của việc du học, và giáo viên khen nó hay.<br>2. Phân tích: Cụm từ 'wrote a/an...' (viết một...).<br>3. Chọn C. 'essay' (bài luận). Phù hợp với mạo từ 'an' (an essay). 'homework' không đếm được (không dùng an), 'test' không hợp nghĩa viết tự luận."
            },
            { 
                id: 14, type: 'mcq', 
                q: "14. Student A: I'm going to the movies this evening. Do you want to join me? - Student B: _______ I have too much homework to do.",
                options: [
                    { text: "Sure, I can.", correct: false },
                    { text: "Thanks, but I don't think I can.", correct: true },
                    { text: "Of course, I will.", correct: false },
                    { text: "Thanks, but sorry, I'm not.", correct: false }
                ],
                exp: "1. Dịch: A: Tối nay tớ đi xem phim. Cậu đi cùng không? B: ____ Tớ có quá nhiều bài tập phải làm.<br>2. Phân tích: Người B từ chối vì bận bài tập.<br>3. Chọn B. 'Cảm ơn, nhưng tớ không nghĩ là tớ đi được' (Từ chối lịch sự). A và C là đồng ý (sai). D dùng sai ngữ pháp (I'm not không khớp với do you want)."
            },
            { 
                id: 15, type: 'mcq', 
                q: `15. Read the notice and choose the correct statement.
                    <div class="css-sign">
                        <div class="sign-15-icon">🧤</div>
                        <div class="sign-15-text">WEAR<br>HAND PROTECTION</div>
                    </div>`,
                options: [
                    { text: "A. You have to wear gloves when you enter this place.", correct: true },
                    { text: "B. You don't have to wear gloves in this place.", correct: false },
                    { text: "C. It's a good idea to wear gloves in this place.", correct: false },
                    { text: "D. You need to bring gloves to this area.", correct: false }
                ],
                exp: "1. Dịch biển báo: 'Hãy mặc đồ bảo hộ tay' (Bắt buộc).<br>2. Phân tích: Đây là biển báo an toàn lao động mang tính bắt buộc.<br>3. Chọn A. 'You have to...' (Bạn BẮT BUỘC phải đeo găng tay...). B là không cần, C là gợi ý (không đủ mạnh), D chỉ nói mang theo chứ không nói phải đeo."
            },
            { 
                id: 16, type: 'mcq', 
                q: `16. What does this sign mean?
                    <div class="css-sign css-sign-16">
                        <div class="sign-16-pencil">✏️</div>
                        <div class="sign-16-bubble">QUIET PLEASE<br>EXAMS IN PROGRESS</div>
                    </div>`,
                options: [
                    { text: "A. You don't have to talk in this area.", correct: false },
                    { text: "B. You have to keep silent in this area.", correct: true },
                    { text: "C. You have to take the exam in this area.", correct: false },
                    { text: "D. You don't have to make any noise during the exam.", correct: false }
                ],
                exp: "1. Dịch biển báo: 'Vui lòng giữ im lặng. Đang trong giờ thi'.<br>2. Phân tích: Biển yêu cầu không được làm ồn.<br>3. Chọn B. 'You have to keep silent...' (Bạn phải giữ im lặng). A sai vì 'don't have to' nghĩa là 'không cần thiết phải làm' (nhưng làm cũng được), ở đây là cấm nói chuyện."
            },

            { type: 'title', title: 'III. WORD FORMATION' },
            {
                id: 17, type: 'fill',
                q: "17. I was so ________ because I got an A plus on my English test. (SURPRISE)",
                answer: "surprised",
                exp: "1. Dịch: Tôi đã rất ___ vì tôi được điểm A+ môn tiếng Anh.<br>2. Ngữ pháp: Tính từ đuôi -ed (surprised) dùng để miêu tả CẢM XÚC của con người (bị tác động bởi ngoại cảnh).<br>3. Đáp án: <b>surprised</b> (ngạc nhiên, theo hướng vui vẻ)."
            },
            {
                id: 18, type: 'fill',
                q: "18. In my English class, we have to give ________ about various topics. (PRESENT)",
                answer: "presentations",
                exp: "1. Dịch: Trong lớp tiếng Anh, chúng tôi phải thực hiện các bài ___ về nhiều chủ đề.<br>2. Ngữ pháp: Sau động từ 'give' cần một danh từ. 'give a presentation' (thuyết trình). Vì 'various topics' (nhiều chủ đề) nên danh từ phải ở dạng số nhiều.<br>3. Đáp án: <b>presentations</b>."
            },
            {
                id: 19, type: 'fill',
                q: "19. Philip was really ________ when he got a D on his math test. He studied very hard for it. (DISAPPOINT)",
                answer: "disappointed",
                exp: "1. Dịch: Philip thực sự ___ khi bị điểm D môn Toán. Cậu ấy đã học rất chăm.<br>2. Ngữ pháp: Tương tự câu 17, miêu tả cảm xúc con người dùng tính từ đuôi -ed.<br>3. Đáp án: <b>disappointed</b> (thất vọng)."
            },
            {
                id: 20, type: 'fill',
                q: "20. Studying abroad puts you into an unfamiliar situation, so you will become more ________. (DEPEND)",
                answer: "independent",
                exp: "1. Dịch: Du học đặt bạn vào một hoàn cảnh lạ lẫm, vì vậy bạn sẽ trở nên ___ hơn.<br>2. Ngữ pháp/Ngữ nghĩa: Ở một mình nơi đất khách thì phải 'tự lập'. Tiền tố 'in-' thêm vào 'dependent' (phụ thuộc) tạo ra từ trái nghĩa.<br>3. Đáp án: <b>independent</b> (tự lập / độc lập)."
            },
            {
                id: 21, type: 'fill',
                q: "21. Studying overseas also gives you the opportunity to make friends with people from ________ backgrounds. (DIFFER)",
                answer: "different",
                exp: "1. Dịch: Du học cho bạn cơ hội kết bạn với những người từ các hoàn cảnh ___.<br>2. Ngữ pháp: Đứng trước danh từ 'backgrounds' cần một tính từ để bổ nghĩa. Tính từ của 'differ' là 'different'.<br>3. Đáp án: <b>different</b> (khác biệt / đa dạng)."
            },
            {
                id: 22, type: 'fill',
                q: "22. When I first came to the USA, I was ________ and lonely because I couldn't understand what other people said. (SCARY)",
                answer: "scared",
                exp: "1. Dịch: Khi mới đến Mỹ, tôi đã rất ___ và cô đơn vì không hiểu người khác nói gì.<br>2. Ngữ pháp: Tả cảm giác sợ hãi của bản thân (con người) phải dùng 'scared'. ('Scary' dùng để miêu tả bản chất của 1 vật/sự việc gây sợ hãi, ví dụ: a scary movie).<br>3. Đáp án: <b>scared</b> (cảm thấy sợ hãi)."
            },

            { type: 'title', title: 'IV. LISTENING (Simulated as Gap Fill)' },
            {
                id: 999, type: 'passage',
                content: "<b>Transcript:</b> Hey, it's Tom! My trip was amazing, although I really missed my friends and family back home. The thing that surprised me most was how welcoming everyone was. Alex was pleased to hear I didn't have trouble making friends. I thought the local food was really delicious because it tasted hot and spicy, but honestly, I found it hard to take a test in a foreign language."
            },
            {
                id: 23, type: 'inline-gap',
                q: "Tom's trip was amazing, although he (23) {gap} his friends and family.",
                options: ["missed", "called", "forgot"], answer: "missed",
                exp: "Dựa vào đoạn script: '...although I really missed my friends...'. Chọn 'missed' (nhớ)."
            },
            {
                id: 24, type: 'inline-gap',
                q: "The thing that (24) {gap} him was how welcoming everyone was.",
                options: ["annoyed", "surprised", "scared"], answer: "surprised",
                exp: "Dựa vào đoạn script: 'The thing that surprised me most...'. Chọn 'surprised' (làm ngạc nhiên)."
            },
            {
                id: 25, type: 'inline-gap',
                q: "His friend Alex was (25) {gap} to hear Tom didn't have trouble making friends.",
                options: ["upset", "angry", "pleased"], answer: "pleased",
                exp: "Dựa vào đoạn script: 'Alex was pleased to hear...'. Chọn 'pleased' (vui mừng/hài lòng)."
            },
            {
                id: 26, type: 'inline-gap',
                q: "Tom thought the food was (26) {gap} delicious because it tasted hot and spicy...",
                options: ["very", "really", "a bit"], answer: "really",
                exp: "Dựa vào đoạn script: 'thought the local food was really delicious'. Chọn 'really'."
            },
            {
                id: 27, type: 'inline-gap',
                q: "...and he found it hard to take a (27) {gap} in a foreign language.",
                options: ["test", "trip", "class"], answer: "test",
                exp: "Dựa vào đoạn script: 'hard to take a test in a foreign language'. Chọn 'test' (bài kiểm tra)."
            },

            { type: 'title', title: 'V. READING' },
            {
                id: 998, type: 'passage',
                content: "Studying abroad is becoming popular for many students looking to learn more about other languages and countries. Sometimes, students (33) ________ work with an online exchange organization to make travel arrangements and make sure they have a wonderful and safe experience while away. Studying abroad is also a (34) ________ way to meet new friends, visit new places, and experience different things. Students are (35) ________ to learn about new opportunities and meet people from other cultures. (36) ________ learning in a foreign country can be difficult, they are pleased when they (37) ________ their first test, complete their first project, or meet amazing new people."
            },
            {
                id: 33, type: 'mcq',
                q: "33. Choose the best word:",
                options: [{text:"have", correct:false}, {text:"have to", correct:true}, {text:"to have", correct:false}, {text:"has to", correct:false}],
                exp: "1. Phân tích: Động từ chính phía sau là 'work' (V nguyên thể). 'Students' là số nhiều.<br>2. Chọn B. 'have to' + V-inf (phải làm gì). Câu dịch: 'Đôi khi, học sinh phải làm việc với một tổ chức trao đổi...'"
            },
            {
                id: 34, type: 'mcq',
                q: "34. Choose the best word:",
                options: [{text:"great", correct:true}, {text:"terrible", correct:false}, {text:"pleased", correct:false}, {text:"surprised", correct:false}],
                exp: "1. Ngữ cảnh: Đoạn văn đang nói về lợi ích tích cực của du học ('meet new friends', 'visit new places').<br>2. Chọn A. 'a great way' (một cách tuyệt vời). 'terrible' là tồi tệ (sai nghĩa). 'pleased/surprised' dùng tả người, không tả 'way'."
            },
            {
                id: 35, type: 'mcq',
                q: "35. Choose the best word:",
                options: [{text:"upset", correct:false}, {text:"disappointed", correct:false}, {text:"annoyed", correct:false}, {text:"delighted", correct:true}],
                exp: "1. Ngữ cảnh: Học sinh được học cơ hội mới, gặp người mới -> Cảm xúc phải tích cực.<br>2. Chọn D. 'delighted' (vui mừng). A, B, C đều mang nghĩa tiêu cực (buồn bực, thất vọng)."
            },
            {
                id: 36, type: 'mcq',
                q: "36. Choose the best word:",
                options: [{text:"Because", correct:false}, {text:"Although", correct:true}, {text:"However", correct:false}, {text:"So", correct:false}],
                exp: "1. Dịch 2 vế: '___ việc học ở nước ngoài có thể khó khăn, họ vẫn hài lòng khi...'<br>2. Phân tích: Hai vế đối lập nhau (Khó khăn >< Hài lòng).<br>3. Chọn B. 'Although' (Mặc dù). 'However' không đứng đầu câu nối 2 vế bằng dấu phẩy theo cách này."
            },
            {
                id: 37, type: 'mcq',
                q: "37. Choose the best word:",
                options: [{text:"present", correct:false}, {text:"fail", correct:false}, {text:"pass", correct:true}, {text:"make", correct:false}],
                exp: "1. Cụm từ đi với 'their first test' (bài kiểm tra đầu tiên) trong ngữ cảnh họ đang 'pleased' (vui).<br>2. Chọn C. 'pass' (thi đỗ/vượt qua). Không thể chọn 'fail' (trượt) vì họ đang vui."
            },

            {
                id: 997, type: 'passage',
                content: "When Sophie was a little girl, she dreamed about visiting another country. One day, while looking on the internet, she was surprised to learn about a way to travel and study abroad. First, Sophie would have to decide which country to visit. She would also need to learn a foreign language to take tests and write essays. Sophie quickly knew it would take a lot of work to make her dreams come true, so she began working with her parents on making plans. Sophie was so excited about her future that she spent an entire summer working with her dad to save money. She also took French lessons because she always dreamed about traveling to Paris. The following summer, Sophie was accepted into an exchange program and spent a year traveling and studying abroad."
            },
            {
                id: 38, type: 'mcq',
                q: "38. Sophie made her dreams of traveling abroad come true by working hard.",
                options: [{text:"True", correct:true}, {text:"False", correct:false}, {text:"Not Given", correct:false}],
                exp: "Dẫn chứng: 'Sophie quickly knew it would take a lot of work to make her dreams come true... she spent an entire summer working...'. -> True."
            },
            {
                id: 39, type: 'mcq',
                q: "39. Sophie didn't have to learn a foreign language.",
                options: [{text:"True", correct:false}, {text:"False", correct:true}, {text:"Not Given", correct:false}],
                exp: "Dịch: Sophie không cần học ngoại ngữ.<br>Dẫn chứng trong bài: 'She would also need to learn a foreign language... She also took French lessons'. (Cô ấy CÓ học) -> False."
            },
            {
                id: 40, type: 'mcq',
                q: "40. Sophie planned to take a train to Paris.",
                options: [{text:"True", correct:false}, {text:"False", correct:false}, {text:"Not Given", correct:true}],
                exp: "Dẫn chứng: Bài viết chỉ đề cập 'she always dreamed about traveling to Paris'. KHÔNG CÓ thông tin nào nhắc đến việc đi bằng tàu hỏa (take a train). -> Not Given."
            },
            {
                id: 41, type: 'mcq',
                q: "41. Sophie worked with her dad to save money.",
                options: [{text:"True", correct:true}, {text:"False", correct:false}, {text:"Not Given", correct:false}],
                exp: "Dẫn chứng: 'she spent an entire summer working with her dad to save money.' -> Trùng khớp 100% -> True."
            },
            {
                id: 42, type: 'mcq',
                q: "42. Sophie spent one whole summer studying abroad.",
                options: [{text:"True", correct:false}, {text:"False", correct:true}, {text:"Not Given", correct:false}],
                exp: "Dịch: Sophie dành nguyên 1 mùa hè để du học.<br>Dẫn chứng: 'spent an entire summer working... The following summer, Sophie was accepted... and spent a year traveling and studying'. (Dành 1 mùa hè để LÀM VIỆC kiếm tiền, sau đó đi du học 1 NĂM). -> False."
            },

            { type: 'title', title: 'VI. WRITING (Sentence Transformation)' },
            {
                id: 43, type: 'fill',
                q: "43. Anna's mother is from China, but she can't speak Chinese. (HOWEVER)<br>→ Anna's mother is from China; ...................................",
                answer: "however, she can't speak Chinese.",
                exp: "1. Cấu trúc: Clause 1, but Clause 2 = Clause 1; however, Clause 2. (Tuy nhiên).<br>2. Lưu ý dấu câu: Trước however là dấu chấm phẩy (;), sau however là dấu phẩy (,).<br>3. Đáp án: <b>however, she can't speak Chinese.</b>"
            },
            {
                id: 44, type: 'fill',
                q: "44. Luke wants to study overseas, but he is afraid of living alone.<br>→ Although ...................................",
                answer: "Luke wants to study overseas, he is afraid of living alone.",
                exp: "1. Cấu trúc: Mặc dù (Although) + S + V, S + V. Khi dùng Although ở đầu câu, bỏ 'but' ở giữa câu.<br>2. Đáp án: <b>Luke wants to study overseas, he is afraid of living alone.</b>"
            },
            {
                id: 45, type: 'fill',
                q: "45. According to the rules, it's necessary for students to hand in their assignments on time.<br>→ Students ...................................",
                answer: "have to hand in their assignments on time.",
                exp: "1. Cấu trúc: It is necessary for sb to do sth (Cần thiết phải làm gì) = sb + have to / has to + V.<br>2. 'Students' là số nhiều -> dùng 'have to'.<br>3. Đáp án: <b>have to hand in their assignments on time.</b>"
            },
            {
                id: 46, type: 'fill',
                q: "46. It isn't necessary for Cathy to buy new textbooks because she can borrow them from the library.<br>→ Cathy ...................................",
                answer: "doesn't have to buy new textbooks because she can borrow them from the library.",
                exp: "1. Cấu trúc: It isn't necessary for sb to do sth (Không cần thiết phải làm gì) = sb + don't/doesn't have to + V.<br>2. Cathy là số ít -> doesn't have to.<br>3. Đáp án: <b>doesn't have to buy new textbooks...</b>"
            },
            {
                id: 47, type: 'fill',
                q: "47. I / have / be / school / 8:50 / because / first lesson / start / 9:00.<br>→ ...................................",
                answer: "I have to be at school at 8:50 because my first lesson starts at 9:00.",
                exp: "1. Ngữ pháp: 'have to be' (phải có mặt); giới từ 'at' + địa điểm/thời gian; 'lesson' số ít nên 'starts' thêm 's'.<br>2. Đáp án: <b>I have to be at school at 8:50 because my first lesson starts at 9:00.</b>"
            },
            {
                id: 48, type: 'fill',
                q: "48. Although / Ann / not like / sports / she / have / play / basketball / P.E. lessons.<br>→ ...................................",
                answer: "Although Ann doesn't like sports, she has to play basketball in P.E. lessons.",
                exp: "1. Ngữ pháp: Ann (số ít) -> doesn't like; she (số ít) -> has to play; 'in' P.E lessons (trong tiết thể dục). Nhớ có dấu phẩy ngăn cách 2 vế.<br>2. Đáp án: <b>Although Ann doesn't like sports, she has to play basketball in P.E. lessons.</b>"
            },
            {
                id: 49, type: 'fill',
                q: "49. I / pass / all / exams / so / parents / be / so / delighted.<br>→ ...................................",
                answer: "I passed all my exams, so my parents were so delighted.",
                exp: "1. Ngữ cảnh: Sự việc đã xảy ra nên chia Quá khứ đơn (passed, were). Thêm tính từ sở hữu 'my' cho tự nhiên.<br>2. Đáp án: <b>I passed all my exams, so my parents were so delighted.</b> (Dùng hiện tại I pass... so my parents are... cũng được chấp nhận)."
            },
            {
                id: 50, type: 'fill',
                q: "50. Tom / play / computer games / right now / although / he / have / important test / tomorrow morning.<br>→ ...................................",
                answer: "Tom is playing computer games right now although he has an important test tomorrow morning.",
                exp: "1. Ngữ pháp: 'right now' -> Hiện tại tiếp diễn (is playing). 'he' -> has. 'important test' cần mạo từ 'an'.<br>2. Đáp án: <b>Tom is playing computer games right now although he has an important test tomorrow morning.</b>"
            }
        ];

        let totalCorrect = 0;
        let totalWrong = 0;

        // Shuffle function cho trắc nghiệm
        function shuffleArray(array) {
            for (let i = array.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [array[i], array[j]] = [array[j], array[i]];
            }
        }

        function cleanString(str) {
            return str.toLowerCase().replace(/[^a-z0-9]/g, '');
        }

        // Render toàn bộ UI
        function renderQuiz() {
            const container = document.getElementById('quiz-container');
            let html = '';

            db.forEach((item, index) => {
                if (item.type === 'title') {
                    html += `<div class="section-title">${item.title}</div>`;
                } else if (item.type === 'passage') {
                    html += `<div class="passage-box">${item.content}</div>`;
                } else if (item.type === 'mcq') {
                    // Clone để không ảnh hưởng db gốc
                    let opts = [...item.options];
                    shuffleArray(opts);
                    
                    html += `
                        <div class="question-card" id="card-${item.id}">
                            <div class="question-text">${item.q}</div>
                            <div class="options-grid">
                                ${opts.map((opt, i) => `
                                    <button class="option-btn" onclick="checkMCQ(this, ${opt.correct}, ${item.id})">
                                        <b>${['A','B','C','D'][i]}.</b>&nbsp; ${opt.text}
                                    </button>
                                `).join('')}
                            </div>
                            <div class="explanation" id="exp-${item.id}">
                                <h4>💡 GIẢI THÍCH CHI TIẾT:</h4>
                                ${item.exp}
                            </div>
                        </div>
                    `;
                } else if (item.type === 'fill') {
                    html += `
                        <div class="question-card" id="card-${item.id}">
                            <div class="question-text">${item.q}</div>
                            <div class="input-group">
                                <input type="text" class="text-input" id="input-${item.id}" placeholder="Nhập câu trả lời của bạn...">
                                <button class="check-btn" onclick="checkFill(${item.id}, '${item.answer.replace(/'/g, "\\'")}')">KIỂM TRA</button>
                            </div>
                            <div class="explanation" id="exp-${item.id}">
                                <h4>💡 GIẢI THÍCH CHI TIẾT:</h4>
                                ${item.exp}
                            </div>
                        </div>
                    `;
                } else if (item.type === 'inline-gap') {
                    // Dùng cho bài Gap Fill (giả lập popup)
                    let textParts = item.q.split('{gap}');
                    html += `
                        <div class="question-card" id="card-${item.id}">
                            <div class="question-text" style="display:inline-block; margin-bottom:0;">
                                ${textParts[0]}
                                <span class="gap-input" id="gap-${item.id}" onclick="showGapPopup(${item.id}, '${item.options.join('|')}', '${item.answer}')">[ Chọn từ ]</span>
                                ${textParts[1]}
                            </div>
                            <div class="explanation" id="exp-${item.id}">
                                <h4>💡 GIẢI THÍCH CHI TIẾT:</h4>
                                ${item.exp}
                            </div>
                        </div>
                    `;
                }
            });

            html += `<button class="submit-btn" onclick="finishTest()">NỘP BÀI TỔNG KẾT</button>`;
            container.innerHTML = html;
        }

        // Logic chấm MCQs
        window.checkMCQ = function(btn, isCorrect, id) {
            const card = document.getElementById(`card-${id}`);
            if (card.classList.contains('answered')) return;
            card.classList.add('answered');

            const btns = card.querySelectorAll('.option-btn');
            const exp = document.getElementById(`exp-${id}`);

            if (isCorrect) {
                btn.classList.add('correct');
                playSound('correct');
                triggerConfetti();
                totalCorrect++;
            } else {
                btn.classList.add('wrong');
                playSound('wrong');
                totalWrong++;
                // Hiện đáp án đúng
                btns.forEach(b => {
                    // Cần tìm nút chứa correct option thực sự dựa vào hàm onclick truyền vào
                    if(b.getAttribute('onclick').includes('true')) b.classList.add('correct');
                });
            }
            updateScore();
            exp.style.display = 'block';
        };

        // Logic chấm Tự luận
        window.checkFill = function(id, correctAns) {
            const card = document.getElementById(`card-${id}`);
            if (card.classList.contains('answered')) return;
            
            const input = document.getElementById(`input-${id}`);
            const userVal = input.value.trim();
            if (!userVal) { alert("Vui lòng nhập đáp án!"); return; }

            card.classList.add('answered');
            input.disabled = true;

            const isCorrect = cleanString(userVal) === cleanString(correctAns);

            if (isCorrect) {
                input.style.borderColor = "var(--success)";
                input.style.backgroundColor = "#e8f8f5";
                input.style.color = "var(--success)";
                playSound('correct');
                triggerConfetti();
                totalCorrect++;
            } else {
                input.style.borderColor = "var(--error)";
                input.style.backgroundColor = "#fdeded";
                input.style.color = "var(--error)";
                playSound('wrong');
                totalWrong++;
            }
            updateScore();
            document.getElementById(`exp-${id}`).style.display = 'block';
        };

        // Logic chấm Gap Fill (Popup)
        window.showGapPopup = function(id, optsStr, correctAns) {
            const el = document.getElementById(`gap-${id}`);
            if (el.classList.contains('done-correct') || el.classList.contains('done-wrong')) return;

            const opts = optsStr.split('|');
            let msg = `Chọn 1 đáp án cho câu ${id}:\n`;
            opts.forEach((o, i) => msg += `${i+1}. ${o}\n`);
            
            const choice = prompt(msg);
            if (!choice) return;

            const isCorrect = cleanString(choice) === cleanString(correctAns);
            el.innerText = choice;

            if (isCorrect) {
                el.classList.add('done-correct');
                playSound('correct');
                triggerConfetti();
                totalCorrect++;
            } else {
                alert(`Rất tiếc! Đáp án đúng là: ${correctAns}`);
                el.innerText = correctAns;
                el.classList.add('done-wrong');
                playSound('wrong');
                totalWrong++;
            }
            updateScore();
            document.getElementById(`exp-${id}`).style.display = 'block';
        };

        function updateScore() {
            document.getElementById('score-correct').innerText = totalCorrect;
            document.getElementById('score-wrong').innerText = totalWrong;
        }

        window.finishTest = function() {
            const total = 45; // Có 45 câu hỏi thực tế trong data
            const percent = Math.round((totalCorrect / total) * 100);
            let msg = percent >= 80 ? "BẠN THẬT XUẤT SẮC! THIÊN TÀI LÀ ĐÂY! 🎉" : "HÃY CỐ GẮNG ÔN TẬP LẠI NHÉ! 💪";
            
            alert(`TỔNG KẾT BÀI THI\n\nSố câu ĐÚNG: ${totalCorrect}/${total}\nSố câu SAI: ${totalWrong}\nTỉ lệ: ${percent}%\n\n${msg}`);
            if(percent >= 80) triggerConfetti();
        };

        // Khởi tạo
        window.onload = renderQuiz;
    </script>
</body>
</html>
