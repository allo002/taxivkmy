# taxivkmy
Taxi in one click - VK Mini App
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🚖 OneTap Taxi</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        
        .app-container {
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            width: 100%;
            max-width: 400px;
            overflow: hidden;
            animation: fadeIn 0.5s ease;
        }
        
        .header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 30px 20px;
            text-align: center;
        }
        
        .header h1 {
            font-size: 28px;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }
        
        .header p {
            opacity: 0.9;
            font-size: 16px;
        }
        
        .content {
            padding: 30px 20px;
        }
        
        .step {
            display: flex;
            align-items: center;
            margin-bottom: 25px;
            padding: 15px;
            background: #f8f9fa;
            border-radius: 12px;
            border-left: 4px solid #667eea;
        }
        
        .step-number {
            background: #667eea;
            color: white;
            width: 32px;
            height: 32px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            margin-right: 15px;
            flex-shrink: 0;
        }
        
        .step-text {
            flex: 1;
        }
        
        .step-text h3 {
            color: #333;
            margin-bottom: 5px;
            font-size: 16px;
        }
        
        .step-text p {
            color: #666;
            font-size: 14px;
            line-height: 1.4;
        }
        
        .buttons {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin-top: 30px;
        }
        
        .btn {
            padding: 16px 24px;
            border: none;
            border-radius: 12px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }
        
        .btn-primary {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
        }
        
        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(102, 126, 234, 0.4);
        }
        
        .btn-secondary {
            background: #f0f2f5;
            color: #667eea;
            border: 2px solid #e0e2e5;
        }
        
        .footer {
            text-align: center;
            padding: 20px;
            color: #888;
            font-size: 14px;
            border-top: 1px solid #eee;
        }
        
        .vk-badge {
            background: #4a76a8;
            color: white;
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 12px;
            display: inline-block;
            margin-top: 10px;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        @media (max-width: 480px) {
            .app-container {
                border-radius: 15px;
            }
            
            .header {
                padding: 25px 15px;
            }
            
            .header h1 {
                font-size: 24px;
            }
        }
    </style>
</head>
<body>
    <div class="app-container" id="app">
        <div class="header">
            <h1>🚖 OneTap Taxi</h1>
            <p>Такси в один клик через VK</p>
            <div class="vk-badge">VK Mini App</div>
        </div>
        
        <div class="content">
            <div class="step">
                <div class="step-number">1</div>
                <div class="step-text">
                    <h3>Авторизуйтесь через VK</h3>
                    <p>Войдите через ваш VK аккаунт для быстрого доступа</p>
                </div>
            </div>
            
            <div class="step">
                <div class="step-number">2</div>
                <div class="step-text">
                    <h3>Сохраните адреса</h3>
                    <p>Укажите домашний и рабочий адрес один раз</p>
                </div>
            </div>
            
            <div class="step">
                <div class="step-number">3</div>
                <div class="step-text">
                    <h3>Вызывайте такси одной кнопкой</h3>
                    <p>Больше не нужно каждый раз вводить адреса</p>
                </div>
            </div>
            
            <div class="buttons">
                <button class="btn btn-primary" id="openVK">
                    <span>🚀 Открыть в VK</span>
                </button>
                <button class="btn btn-secondary" id="showInstructions">
                    <span>📖 Инструкция по настройке</span>
                </button>
            </div>
        </div>
        
        <div class="footer">
            <p>Домен: <strong id="domain">allo002.github.io/onetaptaxi-vk</strong></p>
            <p style="margin-top: 5px; font-size: 12px;">
                Статус: <span id="status">✅ Готово к работе в VK</span>
            </p>
        </div>
    </div>

    <script>
        // Элементы DOM
        const openVKBtn = document.getElementById('openVK');
        const instructionsBtn = document.getElementById('showInstructions');
        const domainElement = document.getElementById('domain');
        const statusElement = document.getElementById('status');
        
        // Текущий домен
        domainElement.textContent = window.location.hostname + window.location.pathname;
        
        // Проверяем, открыто ли в VK
        const isVK = navigator.userAgent.includes('VK');
        
        // Обновляем интерфейс если в VK
        if (isVK) {
            document.querySelector('h1').innerHTML = '🚖 Добро пожаловать!';
            document.querySelector('.header p').textContent = 'OneTap Taxi готов к работе';
            openVKBtn.innerHTML = '<span>🎯 Начать пользоваться</span>';
            statusElement.textContent = '✅ Работает в VK';
            statusElement.style.color = '#4CAF50';
            
            // Добавляем функциональность для VK
            openVKBtn.addEventListener('click', function() {
                showMessage('Демо-режим: Такси будет вызвано через 5-7 минут', 'success');
            });
        } else {
            // Режим вне VK
            openVKBtn.addEventListener('click', function() {
                const instructions = `
ДЛЯ РАБОТЫ В VK:

1. СОЗДАЙТЕ ПРИЛОЖЕНИЕ:
   • vk.com/editapp?act=create
   • Тип: Standalone
   • Название: OneTap Taxi

2. НАСТРОЙТЕ ДОМЕН:
   • Базовый адрес: ${window.location.origin}
   • Адрес сайта: ${window.location.origin}

3. ПОЛУЧИТЕ ID ПРИЛОЖЕНИЯ
4. ОТКРОЙТЕ: vk.com/app/ВАШ_ID
                `;
                alert(instructions);
            });
        }
        
        // Кнопка инструкции
        instructionsBtn.addEventListener('click', function() {
            const steps = `
🛠 ПОШАГОВАЯ НАСТРОЙКА:

ШАГ 1: VK ПРИЛОЖЕНИЕ
1. Откройте: vk.com/editapp?act=create
2. Заполните:
   - Название: OneTap Taxi
   - Тип: Standalone
   - Категория: Утилиты
   - Платформы: ✅ Мини-приложения
3. Сохраните → запомните ID приложения

ШАГ 2: НАСТРОЙКА ДОМЕНА
1. В настройках приложения:
   - Базовый адрес: ${window.location.origin}
   - Адрес сайта: ${window.location.origin}
2. Сохраните

ШАГ 3: ПРОВЕРКА
1. Откройте: vk.com/app/ВАШ_ID
2. Приложение должно работать!

ТЕКУЩИЙ ДОМЕН: ${window.location.origin}
            `;
            alert(steps);
        });
        
        // Функция показа сообщений
        function showMessage(text, type = 'info') {
            const message = document.createElement('div');
            message.textContent = text;
            message.style.cssText = `
                position: fixed;
                top: 20px;
                left: 50%;
                transform: translateX(-50%);
                background: ${type === 'success' ? '#4CAF50' : '#2196F3'};
                color: white;
                padding: 12px 24px;
                border-radius: 8px;
                z-index: 1000;
                animation: slideDown 0.3s ease;
                max-width: 90%;
                text-align: center;
            `;
            
            document.body.appendChild(message);
            
            setTimeout(() => {
                message.style.animation = 'slideUp 0.3s ease';
                setTimeout(() => message.remove(), 300);
            }, 3000);
        }
        
        // Добавляем стили анимаций
        const style = document.createElement('style');
        style.textContent = `
            @keyframes slideDown {
                from { transform: translate(-50%, -100%); opacity: 0; }
                to { transform: translate(-50%, 0); opacity: 1; }
            }
            @keyframes slideUp {
                from { transform: translate(-50%, 0); opacity: 1; }
                to { transform: translate(-50%, -100%); opacity: 0; }
            }
        `;
        document.head.appendChild(style);
        
        // Логи
        console.log('OneTap Taxi App loaded');
        console.log('Domain:', window.location.hostname);
        console.log('Is VK:', isVK);
    </script>
</body>
</html>