<!DOCTYPE html>
<html lang="fa">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>چت باکس پیشرفته</title>
    <style>
        body {
            background-color: #121212;
            color: #ffffff;
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
        }
        .chat-box {
            width: 100%;
            max-width: 600px;
            height: 400px;
            border: 1px solid #333;
            padding: 10px;
            overflow-y: auto;
            background-color: #222;
            border-radius: 5px;
        }
        #user-input {
            width: 75%;
            padding: 10px;
            margin-top: 10px;
            border: 1px solid #555;
            background-color: #222;
            color: #fff;
            border-radius: 5px;
        }
        button {
            padding: 10px;
            margin-left: 10px;
            border: none;
            background-color: #6200ea;
            color: #ffffff;
            cursor: pointer;
            border-radius: 5px;
        }
        button:hover {
            background-color: #3700b3;
        }
        .message {
            background-color: #333;
            padding: 8px;
            margin: 5px 0;
            border-radius: 5px;
            width: fit-content;
            max-width: 80%;
        }
        .ai-message {
            background-color: #0057e7;
            text-align: left;
        }
        .developer {
            margin-top: 20px;
            font-size: 14px;
            color: #bbb;
        }
        .file-upload {
            margin-top: 15px;
        }
        .language-select {
            margin-top: 10px;
            color: #fff;
        }
    </style>
</head>
<body>

    <div class="chat-box" id="chat-box">
        <!-- پیام‌ها در اینجا نمایش داده می‌شوند -->
    </div>

    <input type="text" id="user-input" placeholder="پیام خود را وارد کنید...">
    <button onclick="sendMessage()">ارسال</button>

    <div class="file-upload">
        <input type="file" id="file-input" accept="image/*,video/*">
        <button onclick="processFile()">پردازش فایل</button>
    </div>

    <select class="language-select" id="language-select" onchange="changeLanguage()">
        <option value="fa">فارسی</option>
        <option value="en">English</option>
        <option value="de">Deutsch</option>
        <option value="it">Italiano</option>
        <option value="zh">中文</option>
        <option value="hi">हिन्दी</option>
    </select>

    <p class="developer">امضا: تیارا صالحی</p>

    <script>
        function sendMessage() {
            const input = document.getElementById('user-input');
            const chatBox = document.getElementById('chat-box');

            if (input.value.trim()) {
                // پیام کاربر
                const userMessage = document.createElement('div');
                userMessage.classList.add('message');
                userMessage.textContent = input.value;
                chatBox.appendChild(userMessage);

                // پاسخ هوش مصنوعی
                setTimeout(() => {
                    const aiMessage = document.createElement('div');
                    aiMessage.classList.add('message', 'ai-message');
                    aiMessage.textContent = "پاسخ هوش مصنوعی: " + generateAIResponse(input.value);
                    chatBox.appendChild(aiMessage);
                    chatBox.scrollTop = chatBox.scrollHeight; // اسکرول به پایین
                }, 1000);

                input.value = ''; // پاک کردن ورودی پس از ارسال
            }
        }

        function generateAIResponse(userText) {
            const responses = {
                "fa": ["سلام! چطور می‌توانم کمکتان کنم؟", "جالب است! بیشتر توضیح دهید.", "به نظر موضوع مهمی می‌آید."],
                "en": ["Hello! How can I assist you?", "Interesting! Please elaborate.", "That seems important."],
                "de": ["Hallo! Wie kann ich Ihnen helfen?", "Interessant! Erzählen Sie mir mehr.", "Das scheint wichtig zu sein."],
                "it": ["Ciao! Come posso aiutarti?", "Interessante! Raccontami di più.", "Sembra importante."],
                "zh": ["你好！我怎么帮你？", "有趣！请详细说明。", "这似乎很重要。"],
                "hi": ["नमस्ते! मैं आपकी कैसे मदद कर सकता हूँ?", "दिलचस्प! कृपया और समझाएं।", "यह महत्वपूर्ण लगता है।"]
            };
            const lang = document.getElementById("language-select").value;
            return responses[lang][Math.floor(Math.random() * responses[lang].length)];
        }

        function processFile() {
            const fileInput = document.getElementById("file-input");
            if (fileInput.files.length > 0) {
                const file = fileInput.files[0];
                alert("فایل " + file.name + " پردازش شد! (این ویژگی به هوش مصنوعی نیاز دارد)");
            } else {
                alert("لطفاً یک فایل انتخاب کنید!");
            }
        }

        function changeLanguage() {
            const lang = document.getElementById("language-select").value;
            alert("زبان به " + document.getElementById("language-select").selectedOptions[0].text + " تغییر یافت!");
        }
    </script>

</body>
</html># SalehiChatBotAI
