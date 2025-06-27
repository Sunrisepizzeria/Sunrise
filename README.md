<!DOCTYPE html>
<html>
<head>
    <title>بيتزا كشك</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <style>
        body { font-family: Arial, sans-serif; margin: 20px; }
        h1 { color: #e74c3c; }
        .pizza-list { margin-bottom: 20px; }
        .pizza-item { margin-bottom: 10px; }
        label { display: block; margin-top: 10px; }
        input, select, textarea { width: 100%; padding: 8px; margin-top: 5px; }
        button { background-color: #e74c3c; color: white; border: none; padding: 10px; width: 100%; margin-top: 20px; font-size: 16px; }
    </style>
</head>
<body>
    <h1>بيتزا كشك</h1>

    <div class="pizza-list">
        <div class="pizza-item">مارغريتا - 3000 ع.د</div>
        <div class="pizza-item">دجاج - 4000 ع.د</div>
        <div class="pizza-item">خضار - 3500 ع.د</div>
        <div class="pizza-item">بيبروني - 4500 ع.د</div>
    </div>

    <h2>اطلب الآن</h2>
    <form id="orderForm" onsubmit="sendOrder(event)">
        <label for="pizza">اختر نوع البيتزا:</label>
        <select id="pizza" required>
            <option value="">-- اختر --</option>
            <option value="مارغريتا">مارغريتا</option>
            <option value="دجاج">دجاج</option>
            <option value="خضار">خضار</option>
            <option value="بيبروني">بيبروني</option>
        </select>

        <label for="quantity">الكمية:</label>
        <input type="number" id="quantity" min="1" value="1" required>

        <label for="name">الاسم:</label>
        <input type="text" id="name" required>

        <label for="phone">رقم الهاتف:</label>
        <input type="tel" id="phone" required>

        <button type="submit">إرسال الطلب</button>
    </form>

    <script>
        function sendOrder(event) {
            event.preventDefault();
            const pizza = document.getElementById('pizza').value;
            const quantity = document.getElementById('quantity').value;
            const name = document.getElementById('name').value;
            const phone = document.getElementById('phone').value;

            const message = `طلب بيتزا:\nالنوع: ${pizza}\nالكمية: ${quantity}\nالاسم: ${name}\nرقم الهاتف: ${phone}`;

            // فتح واتساب مع رسالة الطلب جاهزة للإرسال
            const whatsappURL = `https://wa.me/رقمك_هنا?text=${encodeURIComponent(message)}`;
            window.open(whatsappURL, '_blank');
        }
    </script>
</body>
</html>
