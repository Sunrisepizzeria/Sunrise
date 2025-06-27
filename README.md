<!DOCTYPE html>
<html lang="fi">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Sunrise Pizzeria</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            background: #fff8f0;
            color: #333;
        }
        h1 {
            color: #e74c3c;
            text-align: center;
        }
        .address, .contact {
            text-align: center;
            margin-bottom: 20px;
            font-weight: bold;
        }
        .pizza-list {
            margin-bottom: 20px;
        }
        .pizza-item {
            background: #fdecea;
            padding: 10px;
            margin: 8px 0;
            border-radius: 5px;
            font-size: 18px;
        }
        form {
            max-width: 400px;
            margin: auto;
            background: #f9f3f1;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 8px rgba(0,0,0,0.1);
        }
        label {
            display: block;
            margin-top: 12px;
        }
        select, input[type="number"], input[type="text"], input[type="tel"] {
            width: 100%;
            padding: 8px;
            margin-top: 5px;
            border-radius: 4px;
            border: 1px solid #ccc;
            box-sizing: border-box;
        }
        button {
            background-color: #e74c3c;
            color: white;
            border: none;
            padding: 12px;
            width: 100%;
            margin-top: 20px;
            font-size: 18px;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #c0392b;
        }
        footer {
            text-align: center;
            margin-top: 30px;
            font-size: 14px;
            color: #999;
        }
    </style>
</head>
<body>
    <h1>Sunrise Pizzeria</h1>
    <div class="address">Sammonaukio 1, 48600 Kotka</div>
    <div class="contact">Puhelin: +358404140424 | WhatsApp: +358404140424</div>

    <div class="pizza-list">
        <div class="pizza-item">Margherita - 7€</div>
        <div class="pizza-item">Kana - 8.5€</div>
        <div class="pizza-item">Kasvis - 8€</div>
        <div class="pizza-item">Pepperoni - 9€</div>
    </div>

    <h2 style="text-align:center;">Tilaa nyt</h2>
    <form id="orderForm" onsubmit="sendOrder(event)">
        <label for="pizza">Valitse pizzatyyppi:</label>
        <select id="pizza" required>
            <option value="">-- Valitse --</option>
            <option value="Margherita">Margherita</option>
            <option value="Kana">Kana</option>
            <option value="Kasvis">Kasvis</option>
            <option value="Pepperoni">Pepperoni</option>
        </select>

        <label for="quantity">Määrä:</label>
        <input type="number" id="quantity" min="1" value="1" required />

        <label for="name">Nimi:</label>
        <input type="text" id="name" required />

        <label for="phone">Puhelinnumero:</label>
        <input type="tel" id="phone" required />

        <button type="submit">Lähetä tilaus WhatsAppissa</button>
    </form>

    <script>
        function sendOrder(event) {
            event.preventDefault();
            const pizza = document.getElementById('pizza').value;
            const quantity = document.getElementById('quantity').value;
            const name = document.getElementById('name').value.trim();
            const phone = document.getElementById('phone').value.trim();

            if (!pizza || !quantity || !name || !phone) {
                alert('Täytä kaikki kentät.');
                return;
            }

            const message =
                `Pizza-tilaus Sunrise Pizzeriasta:\\n` +
                `Tyyppi: ${pizza}\\n` +
                `Määrä: ${quantity}\\n` +
                `Nimi: ${name}\\n` +
                `Puhelinnumero: ${phone}`;

            const whatsappNumber = '358404140424';
            const whatsappURL = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(message)}`;
            window.open(whatsappURL, '_blank');
        }
    </script>

    <footer>
        © 2025 Sunrise Pizzeria - Kaikki oikeudet pidätetään
    </footer>
</body>
</html>
