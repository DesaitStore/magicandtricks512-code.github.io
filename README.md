# magicandtricks512-code.github.io
html
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fortnite Shop — Магазин В-баксов и кодов</title>
    <style>
        :root {
            --primary-color: #f7eb0a;
            --secondary-color: #2b0057;
            --dark-color: #120024;
            --text-light: #ffffff;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--dark-color);
            color: var(--text-light);
            margin: 0;
            padding: 0;
        }

        header {
            background-color: var(--secondary-color);
            padding: 20px;
            text-align: center;
            border-bottom: 4px solid var(--primary-color);
        }

        header h1 {
            margin: 0;
            font-size: 2.5rem;
            text-transform: uppercase;
            color: var(--primary-color);
            text-shadow: 2px 2px 0px #000;
        }

        .container {
            max-width: 1200px;
            margin: 30px auto;
            padding: 0 20px;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
        }

        .card {
            background-color: var(--secondary-color);
            border-radius: 8px;
            overflow: hidden;
            border: 2px solid transparent;
            transition: transform 0.2s, border-color 0.2s;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .card:hover {
            transform: translateY(-5px);
            border-color: var(--primary-color);
        }

        .card-img {
            width: 100%;
            height: 200px;
            background: #3a0075 linear-gradient(45deg, #3a0075, #120024);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 1.2rem;
        }

        .card-content {
            padding: 20px;
            text-align: center;
        }

        .card-title {
            font-size: 1.4rem;
            margin: 0 0 10px 0;
        }

        .card-price {
            font-size: 1.6rem;
            color: var(--primary-color);
            font-weight: bold;
            margin-bottom: 15px;
        }

        .btn {
            background-color: var(--primary-color);
            color: #000;
            border: none;
            padding: 10px 20px;
            font-size: 1rem;
            font-weight: bold;
            border-radius: 4px;
            cursor: pointer;
            text-transform: uppercase;
            width: 100%;
            transition: background 0.2s;
        }

        .btn:hover {
            background-color: #fff200;
        }

        /* Модальное окно */
        .modal {
            display: none;
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background-color: rgba(0,0,0,0.8);
            align-items: center;
            justify-content: center;
        }

        .modal-content {
            background-color: var(--secondary-color);
            padding: 30px;
            border-radius: 8px;
            max-width: 400px;
            width: 100%;
            border: 2px solid var(--primary-color);
        }

        .modal h2 { margin-top: 0; color: var(--primary-color); }

        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            margin-bottom: 5px;
        }

        .form-group input {
            width: 100%;
            padding: 10px;
            box-sizing: border-box;
            border-radius: 4px;
            border: 1px solid #fff;
            background: #fff;
            color: #000;
        }

        .close-btn {
            background: none;
            border: none;
            color: #fff;
            float: right;
            font-size: 1.5rem;
            cursor: pointer;
        }
    </style>
</head>
<body>

<header>
    <h1>Fortnite Items Shop</h1>
</header>

<div class="container">
    <div class="grid">
        <!-- Товар 1 -->
        <div class="card">
            <div class="card-img">📦 1,000 V-Bucks</div>
            <div class="card-content">
                <h3 class="card-title">1 000 В-баксов</h3>
                <div class="card-price">699 ₽</div>
                <button class="btn" onclick="openOrder('1 000 В-баксов', '699 ₽')">Купить</button>
            </div>
        </div>

        <!-- Товар 2 -->
        <div class="card">
            <div class="card-img">📦 2,800 V-Bucks</div>
            <div class="card-content">
                <h3 class="card-title">2 800 В-баксов</h3>
                <div class="card-price">1 699 ₽</div>
                <button class="btn" onclick="openOrder('2 800 В-баксов', '1 699 ₽')">Купить</button>
            </div>
        </div>

        <!-- Товар 3 -->
        <div class="card">
            <div class="card-img">📦 5,000 V-Bucks</div>
            <div class="card-content">
                <h3 class="card-title">5 000 В-баксов</h3>
                <div class="card-price">2 699 ₽</div>
                <button class="btn" onclick="openOrder('5 000 В-баксов', '2 699 ₽')">Купить</button>
            </div>
        </div>

        <!-- Товар 4 -->
        <div class="card">
            <div class="card-img">🔑 Экипировка (Код)</div>
            <div class="card-content">
                <h3 class="card-title">Случайный Neo Versa Набор</h3>
                <div class="card-price">990 ₽</div>
                <button class="btn" onclick="openOrder('Набор Neo Versa', '990 ₽')">Купить</button>
            </div>
        </div>
    </div>
</div>

<!-- Модальное окно заказа -->
<div id="orderModal" class="modal">
    <div class="modal-content">
        <button class="close-btn" onclick="closeOrder()">&times;</button>
        <h2 id="modalTitle">Оформление заказа</h2>
        <p>Товар: <strong id="modalItemName"></strong> на сумму <strong id="modalItemPrice"></strong></p>
        
        <form id="orderForm" onsubmit="submitOrder(event)">
            <div class="form-group">
                <label for="email">Ваш Email для связи:</label>
                <input type="email" id="email" required placeholder="example@mail.ru">
            </div>
            <div class="form-group">
                <label for="epicName">Никнейм Epic Games (если нужен донат):</label>
                <input type="text" id="epicName" placeholder="Введи ник">
            </div>
            <button type="submit" class="btn">Перейти к оплате</button>
        </form>
    </div>
</div>

<script>
    let currentItem = '';
    let currentPrice = '';

    function openOrder(name, price) {
        currentItem = name;
        currentPrice = price;
        document.getElementById('modalItemName').innerText = name;
        document.getElementById('modalItemPrice').innerText = price;
        document.getElementById('orderModal').style.display = 'flex';
    }

    function closeOrder() {
        document.getElementById('orderModal').style.display = 'none';
    }

    function submitOrder(event) {
        event.preventDefault();
        const email = document.getElementById('email').value;
        const epicName = document.getElementById('epicName').value;
        
        alert(`Заказ оформлен!\nТовар: ${currentItem}\nEmail: ${email}\nEpic: ${epicName}.\n(Здесь настраивается перенаправление на платежную систему)`);
        closeOrder();
    }
</script>

</body>
</html>
