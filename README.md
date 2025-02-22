<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bundle & Save</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #333333;
            color: white;
            margin: 0;
            padding: 0;
        }

        .bundle-container {
            background-color: #444444;
            width: 350px;
            margin: 50px auto;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        h2 {
            text-align: center;
            font-size: 24px;
            margin-bottom: 20px;
            color: white;
            background-color: #FFB6C1;
            padding: 10px;
            border-radius: 8px;
        }

        .bundle-option {
            display: flex;
            flex-direction: column;
            padding: 15px;
            margin-bottom: 20px;
            background-color: #555555;
            border-radius: 6px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            transition: background-color 0.3s ease;
        }

        .bundle-option:hover {
            background-color: #666666;
        }

        .bundle-option input[type="radio"] {
            accent-color: #FFB6C1;
            margin-bottom: 10px;
            cursor: pointer;
        }

        .bundle-option label {
            font-size: 18px;
            font-weight: bold;
            color: white;
        }

        .bundle-option label span {
            font-size: 14px;
            color: #FFB6C1;
            float: right;
        }

        .blinking {
            color: #f39c12;
            font-weight: bold;
            animation: blink 1s infinite;
        }

        @keyframes blink {
            0% { opacity: 1; }
            50% { opacity: 0; }
            100% { opacity: 1; }
        }

        .size-color-select {
            display: flex;
            gap: 10px;
            margin-top: 10px;
        }

        .size-color-select select {
            padding: 8px;
            font-size: 14px;
            border-radius: 4px;
            border: 1px solid #FFB6C1;
            outline: none;
            transition: border-color 0.3s;
            background-color: #333333;
            color: white;
        }

        .size-color-select select:focus {
            border-color: #FF69B4;
        }

        .shipping-total {
            margin-top: 20px;
            text-align: right;
            font-size: 16px;
            color: white;
        }

        .shipping-total p {
            margin: 5px 0;
        }

        .add-to-cart {
            background-color: #FFB6C1;
            color: white;
            border: none;
            padding: 12px;
            width: 100%;
            font-size: 16px;
            font-weight: bold;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .add-to-cart:hover {
            background-color: #FF69B4;
        }
    </style>
</head>
<body>

<div class="bundle-container">
    <h2>Bundle & Save</h2>

    <div class="bundle-option">
        <input type="radio" id="1-pair" name="bundle" value="1" checked>
        <label for="1-pair">1 Pair $195.00 <span>50% OFF</span></label>
        <div class="size-color-select">
            <label for="size-1">Size:</label>
            <select id="size-1">
                <option value="S">S</option>
                <option value="M">M</option>
                <option value="XL">XL</option>
            </select>
            <label for="color-1">Color:</label>
            <select id="color-1">
                <option value="black">Black</option>
                <option value="yellow">Yellow</option>
                <option value="brown">Brown</option>
            </select>
        </div>
    </div>

    <div class="bundle-option">
        <input type="radio" id="2-pair" name="bundle" value="2">
        <label for="2-pair">
            <span class="blinking">Most Popular</span><br>
            2 Pair $345.00 <span>40% OFF</span>
        </label>
        <div class="size-color-select">
            <label for="size-2">Size:</label>
            <select id="size-2">
                <option value="S">S</option>
                <option value="M">M</option>
                <option value="XL">XL</option>
            </select>
            <label for="color-2">Color:</label>
            <select id="color-2">
                <option value="black">Black</option>
                <option value="yellow">Yellow</option>
                <option value="brown">Brown</option>
            </select>
        </div>
    </div>

    <div class="bundle-option">
        <input type="radio" id="3-pair" name="bundle" value="3">
        <label for="3-pair">3 Pair $528.00 <span>60% OFF</span></label>
        <div class="size-color-select">
            <label for="size-3">Size:</label>
            <select id="size-3">
                <option value="S">S</option>
                <option value="M">M</option>
                <option value="XL">XL</option>
            </select>
            <label for="color-3">Color:</label>
            <select id="color-3">
                <option value="black">Black</option>
                <option value="yellow">Yellow</option>
                <option value="brown">Brown</option>
            </select>
        </div>
    </div>

    <div class="shipping-total">
        <p>Free 2 Day Shipping</p>
        <p>Total: $<span id="total-price">195.00</span></p>
    </div>
    <button class="add-to-cart">+ Add to Cart</button>
</div>

<script>
    const bundleOptions = document.querySelectorAll('input[name="bundle"]');
    const totalPriceElement = document.querySelector('#total-price');

    const prices = {
        "1": 195.00,
        "2": 345.00,
        "3": 528.00
    };
    const discounts = {
        "1": 0.5,
        "2": 0.4,
        "3": 0.6
    };

    bundleOptions.forEach(option => {
        option.addEventListener('change', () => {
            const selectedValue = option.value;
            const discountedPrice = prices[selectedValue] * (1 - discounts[selectedValue]);
            totalPriceElement.textContent = discountedPrice.toFixed(2);
        });
    });
</script>

</body>
</html>
