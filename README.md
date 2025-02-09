# menu.html
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>قائمة المطعم</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            direction: rtl;
            background-color: #f8f8f8;
        }
        .menu {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            margin-top: 20px;
        }
        .item {
            background: white;
            padding: 15px;
            margin: 10px;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            width: 200px;
        }
        button {
            background-color: #28a745;
            color: white;
            border: none;
            padding: 8px;
            cursor: pointer;
        }
        button:hover {
            background-color: #218838;
        }
        .cart {
            margin-top: 20px;
            padding: 20px;
            background: white;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            display: inline-block;
            min-width: 250px;
        }
    </style>
</head>
<body>

    <h1>قائمة الطعام</h1>

    <div class="menu" id="menu">
        <div class="item" data-name="بيتزا" data-price="30">
            <h3>بيتزا</h3>
            <p>السعر: 30 ريال</p>
            <button onclick="addToCart('بيتزا', 30)">إضافة إلى السلة</button>
        </div>
        <div class="item" data-name="برجر" data-price="25">
            <h3>برجر</h3>
            <p>السعر: 25 ريال</p>
            <button onclick="addToCart('برجر', 25)">إضافة إلى السلة</button>
        </div>
        <div class="item" data-name="برياني" data-price="40">
            <h3>برياني</h3>
            <p>السعر: 40 ريال</p>
            <button onclick="addToCart('برياني', 40)">إضافة إلى السلة</button>
        </div>
    </div>

    <div class="cart" id="cart">
        <h2>سلة المشتريات</h2>
        <ul id="cart-items"></ul>
        <p>الإجمالي: <span id="total">0</span> ريال</p>
    </div>

    <script>
        let cart = [];
        let total = 0;

        function addToCart(name, price) {
            cart.push({ name, price });
            total += price;
            updateCart();
        }

        function updateCart() {
            let cartList = document.getElementById("cart-items");
            cartList.innerHTML = "";
            cart.forEach(item => {
                let li = document.createElement("li");
                li.textContent = `${item.name} - ${item.price} ريال`;
                cartList.appendChild(li);
            });
            document.getElementById("total").textContent = total;
        }
    </script>

</body>
</html>
