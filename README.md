<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>چت خصوصی | پی‌وی</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        body {
            background-color: #fafafa;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        }
        
        .instagram-header {
            background: #ffffff;
            border-bottom: 1px solid #dbdbdb;
            height: 60px;
        }
        
        .chat-container {
            background: #fafafa;
            height: calc(100vh - 120px);
        }
        
        .message-bubble {
            max-width: 70%;
            padding: 12px 16px;
            margin: 4px 0;
            border-radius: 22px;
            position: relative;
            animation: fadeIn 0.3s ease;
        }
        
        .message-sent {
            background: #3797f0;
            color: white;
            margin-left: auto;
            margin-right: 16px;
            border-bottom-right-radius: 6px;
        }
        
        .message-received {
            background: #ffffff;
            color: #262626;
            margin-right: auto;
            margin-left: 16px;
            border: 1px solid #efefef;
            border-bottom-left-radius: 6px;
        }
        
        .message-time {
            font-size: 10px;
            opacity: 0.7;
            margin-top: 4px;
        }
        
        .typing-indicator {
            display: inline-flex;
            align-items: center;
            background: #ffffff;
            border: 1px solid #efefef;
            padding: 12px 16px;
            border-radius: 22px;
            border-bottom-left-radius: 6px;
            margin-right: auto;
            margin-left: 16px;
        }
        
        .typing-dot {
            height: 6px;
            width: 6px;
            border-radius: 50%;
            background-color: #8e8e8e;
            margin: 0 2px;
            animation: typing 1.4s infinite ease-in-out;
        }
        
        .typing-dot:nth-child(1) { animation-delay: -0.32s; }
        .typing-dot:nth-child(2) { animation-delay: -0.16s; }
        
        @keyframes typing {
            0%, 80%, 100% { transform: scale(0.8); opacity: 0.5; }
            40% { transform: scale(1); opacity: 1; }
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .input-container {
            background: #ffffff;
            border-top: 1px solid #efefef;
            height: 60px;
        }
        
        .message-input {
            background: #fafafa;
            border: 1px solid #dbdbdb;
            border-radius: 22px;
            padding: 12px 16px;
            outline: none;
        }
        
        .message-input:focus {
            border-color: #a8a8a8;
        }
        
        .send-button {
            color: #3797f0;
            font-weight: 600;
            display: none;
        }
        
        .send-button.active {
            display: block;
        }
        
        .action-button {
            color: #262626;
            padding: 8px;
        }
        
        .plus-button {
            background: #3797f0;
            color: white;
            width: 28px;
            height: 28px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 14px;
        }
        
        .story-ring {
            padding: 2px;
            background: linear-gradient(45deg, #feda75, #fa7e1e, #d62976, #962fbf, #4f5bd5);
            border-radius: 50%;
        }
        
        .profile-pic {
            border-radius: 50%;
            border: 2px solid white;
            object-fit: cover;
        }
        
        .status-dot {
            width: 12px;
            height: 12px;
            background: #42b883;
            border: 2px solid white;
            border-radius: 50%;
            position: absolute;
            bottom: 0;
            right: 0;
        }
        
        /* پنجره نمایش عکس تمام صفحه */
        .fullscreen-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.9);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            animation: fadeInOverlay 0.3s ease;
        }
        
        .fullscreen-image {
            max-width: 90%;
            max-height: 90%;
            border-radius: 10px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            animation: zoomIn 0.5s ease;
        }
        
        .countdown-timer {
            position: absolute;
            top: 20px;
            right: 20px;
            background: rgba(255, 255, 255, 0.2);
            color: white;
            padding: 10px 15px;
            border-radius: 20px;
            font-size: 16px;
            font-weight: bold;
            backdrop-filter: blur(10px);
        }
        
        .close-button {
            position: absolute;
            top: 20px;
            left: 20px;
            background: rgba(255, 255, 255, 0.2);
            color: white;
            border: none;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            font-size: 20px;
            cursor: pointer;
            display: flex;
            justify-content: center;
            align-items: center;
            backdrop-filter: blur(10px);
            transition: all 0.3s ease;
        }
        
        .close-button:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: scale(1.1);
        }
        
        @keyframes fadeInOverlay {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        @keyframes zoomIn {
            from { transform: scale(0.8); opacity: 0; }
            to { transform: scale(1); opacity: 1; }
        }
        
        /* Scrollbar styling */
        #chat-content::-webkit-scrollbar {
            width: 4px;
        }
        
        #chat-content::-webkit-scrollbar-track {
            background: transparent;
        }
        
        #chat-content::-webkit-scrollbar-thumb {
            background: #dbdbdb;
            border-radius: 2px;
        }
    </style>
</head>
<body class="flex flex-col h-screen">
    <!-- هدر اینستاگرام -->
    <div class="instagram-header flex items-center justify-between px-4 fixed top-0 left-0 right-0 z-10">
        <div class="flex items-center gap-3">
            <button class="action-button">
                <i class="fas fa-arrow-left text-lg"></i>
            </button>
            <div class="flex items-center gap-2">
                <div class="relative">
                    <div class="story-ring">
                        <img src="https://cdn.imgurl.ir/uploads/55910_IMG_20251012_150450_324.jpg" alt="آوا" class="profile-pic w-10 h-10">
                    </div>
                    <div class="status-dot"></div>
                </div>
                <div>
                    <div class="font-semibold text-sm">آوا</div>
                    <div class="text-xs text-gray-500">آنلاین</div>
                </div>
            </div>
        </div>
        <div class="flex items-center gap-4">
            <button class="action-button">
                <i class="fas fa-video text-lg"></i>
            </button>
            <button class="action-button">
                <i class="fas fa-phone-alt text-lg"></i>
            </button>
            <button class="action-button">
                <i class="fas fa-info-circle text-lg"></i>
            </button>
        </div>
    </div>
    
    <!-- محتوای چت -->
    <div class="chat-container flex-1 overflow-y-auto pt-16 pb-20" id="chat-content">
        <!-- تاریخ -->
        <div class="text-center my-6">
            <span class="text-xs text-gray-500 bg-white px-3 py-1 rounded-full border border-efefef">امروز</span>
        </div>
        
        <!-- پیام اولیه -->
        <div class="message-bubble message-received">
            <div class="text-sm">سلام! چطوری؟ 😊</div>
            <div class="message-time text-left">۱۰:۳۰</div>
        </div>
    </div>
    
    <!-- نوار پایین برای ارسال پیام -->
    <div class="input-container flex items-center justify-between px-4 fixed bottom-0 left-0 right-0 z-10">
        <div class="flex items-center gap-3 flex-1">
            <button class="plus-button">
                <i class="fas fa-plus"></i>
            </button>
            <div class="flex-1">
                <input type="text" id="message-input" class="message-input w-full text-sm" placeholder="پیام...">
            </div>
        </div>
        <div class="flex items-center gap-4 mr-2">
            <button class="action-button text-gray-400">
                <i class="fas fa-microphone text-xl"></i>
            </button>
            <button class="action-button text-gray-400">
                <i class="far fa-image text-xl"></i>
            </button>
            <button class="action-button text-gray-400">
                <i class="far fa-sticky-note text-xl"></i>
            </button>
            <button id="send-button" class="send-button text-sm font-semibold">
                ارسال
            </button>
        </div>
    </div>

    <!-- پنجره نمایش عکس تمام صفحه -->
    <div class="fullscreen-overlay" id="image-overlay">
        <button class="close-button" id="close-overlay">
            <i class="fas fa-times"></i>
        </button>
        <div class="countdown-timer" id="countdown">۱۰</div>
        <img src="https://cdn.imgurl.ir/uploads/q89930_images.jpeg" alt="عکس ویژه" class="fullscreen-image" id="fullscreen-image">
    </div>

    <script>
        const chatContent = document.getElementById("chat-content");
        const messageInput = document.getElementById("message-input");
        const sendButton = document.getElementById("send-button");
        const imageOverlay = document.getElementById("image-overlay");
        const closeOverlay = document.getElementById("close-overlay");
        const fullscreenImage = document.getElementById("fullscreen-image");
        const countdownElement = document.getElementById("countdown");
        
        let countdownTimer;
        let currentCountdown = 10;
        
        // متن context پیش‌فرض برای هوش مصنوعی - با فرمت صحیح
        const systemContext = `تو آوا هستی، یک دختر ۱۳ ساله که رشته تجربی میخونی و دوست داری در آینده روانشناس بشی. 
        همیشه با لحن خودمانی و صمیمی صحبت میکنی، مثل یه دوست همسن.
        فقط به سوالات کاربر جواب بده و در مورد اطلاعات شخصیت خودت صحبت نکن مگر اینکه کاربر مستقیم در موردش بپرسه.
        از کلمات عامیانه و دوستانه استفاده کن و emoji زیاد بذار.`;
        
        // فعال/غیرفعال کردن دکمه ارسال بر اساس محتوای پیام
        messageInput.addEventListener('input', function() {
            if (this.value.trim() === '') {
                sendButton.classList.remove('active');
            } else {
                sendButton.classList.add('active');
            }
        });
        
        // ارسال پیام جدید
        sendButton.addEventListener('click', sendMessage);
        messageInput.addEventListener('keypress', function(e) {
            if (e.key === 'Enter' && !e.shiftKey) {
                e.preventDefault();
                sendMessage();
            }
        });
        
        // بستن پنجره عکس
        closeOverlay.addEventListener('click', closeImageOverlay);
        
        // بستن با کلید ESC
        document.addEventListener('keydown', function(e) {
            if (e.key === 'Escape') {
                closeImageOverlay();
            }
        });
        
        function sendMessage() {
            const message = messageInput.value.trim();
            if (!message) return;
            
            // ایجاد المان پیام جدید
            const messageElement = document.createElement('div');
            messageElement.className = 'message-bubble message-sent';
            
            const now = new Date();
            const timeString = `${now.getHours().toString().padStart(2, '0')}:${now.getMinutes().toString().padStart(2, '0')}`;
            
            messageElement.innerHTML = `
                <div class="text-sm">${message}</div>
                <div class="message-time text-right">${timeString}</div>
            `;
            
            // اضافه کردن پیام به چت
            chatContent.appendChild(messageElement);
            
            // پاک کردن فیلد ورودی
            messageInput.value = '';
            sendButton.classList.remove('active');
            
            // اسکرول به پایین
            chatContent.scrollTop = chatContent.scrollHeight;
            
            // بررسی اگر کاربر "کوچولو" نوشته باشد
            if (message.toLowerCase().includes('کوچولو')) {
                showImageOverlay();
            } else {
                // اتصال به هوش مصنوعی و دریافت پاسخ
                getAIResponse(message);
            }
        }
        
        function showImageOverlay() {
            imageOverlay.style.display = 'flex';
            currentCountdown = 10;
            countdownElement.textContent = currentCountdown;
            
            // شروع تایمر شمارش معکوس
            countdownTimer = setInterval(() => {
                currentCountdown--;
                countdownElement.textContent = currentCountdown;
                
                if (currentCountdown <= 0) {
                    closeImageOverlay();
                }
            }, 1000);
        }
        
        function closeImageOverlay() {
            imageOverlay.style.display = 'none';
            clearInterval(countdownTimer);
        }
        
        async function getAIResponse(userMessage) {
            // نمایش نشانگر تایپ
            const typingElement = document.createElement('div');
            typingElement.className = 'typing-indicator';
            typingElement.innerHTML = `
                <div class="typing-dot"></div>
                <div class="typing-dot"></div>
                <div class="typing-dot"></div>
            `;
            chatContent.appendChild(typingElement);
            chatContent.scrollTop = chatContent.scrollHeight;
            
            try {
                // ساخت prompt نهایی با فرمت صحیح
                const finalPrompt = `${systemContext}

                کاربر: ${userMessage}
                
                آوا:`;
                
                const response = await fetch("https://backend.buildpicoapps.com/aero/run/llm-api?pk=v1-Z0FBQUFBQm5IZkJDMlNyYUVUTjIyZVN3UWFNX3BFTU85SWpCM2NUMUk3T2dxejhLSzBhNWNMMXNzZlp3c09BSTR6YW1Sc1BmdGNTVk1GY0liT1RoWDZZX1lNZlZ0Z1dqd3c9PQ==", {
                    method: "POST",
                    headers: { "Content-Type": "application/json" },
                    body: JSON.stringify({ prompt: finalPrompt })
                });

                // حذف نشانگر تایپ
                chatContent.removeChild(typingElement);
                
                if (!response.ok) {
                    throw new Error('خطا در ارتباط با سرور');
                }
                
                const data = await response.json();
                let botResponse = data.status === "success" ? data.text : "اوه! یه مشکلی پیش اومده، دوباره بپرس داش!";
                
                // پاکسازی پاسخ - حذف هرگونه اشاره به context
                botResponse = botResponse.replace(/آوا هستی|۱۳ ساله|رشته تجربی|روانشناس|آینده.*روانشناس/g, '');
                
                // ایجاد المان پاسخ
                const replyElement = document.createElement('div');
                replyElement.className = 'message-bubble message-received';
                
                const now = new Date();
                const timeString = `${now.getHours().toString().padStart(2, '0')}:${now.getMinutes().toString().padStart(2, '0')}`;
                
                replyElement.innerHTML = `
                    <div class="text-sm">${botResponse}</div>
                    <div class="message-time text-left">${timeString}</div>
                `;
                
                // اضافه کردن پاسخ به چت
                chatContent.appendChild(replyElement);
                
                // اسکرول به پایین
                chatContent.scrollTop = chatContent.scrollHeight;
                
            } catch (error) {
                console.error('Error:', error);
                // حذف نشانگر تایپ
                chatContent.removeChild(typingElement);
                
                // نمایش پیام خطا
                const errorElement = document.createElement('div');
                errorElement.className = 'message-bubble message-received';
                
                const now = new Date();
                const timeString = `${now.getHours().toString().padStart(2, '0')}:${now.getMinutes().toString().padStart(2, '0')}`;
                
                errorElement.innerHTML = `
                    <div class="text-sm">اوه! نت قطع شده، دوباره تلاش کن رفیق! 😅</div>
                    <div class="message-time text-left">${timeString}</div>
                `;
                
                chatContent.appendChild(errorElement);
                chatContent.scrollTop = chatContent.scrollHeight;
            }
        }
        
        // اسکرول به پایین هنگام بارگذاری صفحه
        window.addEventListener('load', function() {
            chatContent.scrollTop = chatContent.scrollHeight;
        });

        // مدیریت خطا در لود عکس
        document.querySelector('.profile-pic').addEventListener('error', function() {
            this.src = 'https://i.pravatar.cc/40?img=5';
        });
        
        // مدیریت خطا در لود عکس تمام صفحه
        fullscreenImage.addEventListener('error', function() {
            this.src = 'https://cdn.imgurl.ir/uploads/55910_IMG_20251012_150450_324.jpg';
        });
    </script>
</body>
</html>
