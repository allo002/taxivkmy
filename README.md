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