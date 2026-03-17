# Ex02 Commercial Website
## Date:

## AIM
To create a commercial website using CSS Flexbox.

## ALGORITHM
### STEP 1
Create an HTML file (index.html)

### STEP 2
Create a CSS file (style.css)

### STEP 3
Include a navigation bar with links to different sections.

### STEP 4
Add structured sections for Homepage, Products / Services, About Us, Contact Details and User Account.

### STEP 5
Include social media links at the footer with copyright information.

### STEP 6
Define global styles for fonts, colors, and layout.

### STEP 7
Style the header, navigation bar, and sections.

### STEP 8
Use Flexbox for layout design.

### STEP 9
Add hover effects and transitions for interactivity.

### STEP 10
Add Images and Media.

### STEP 11
Use optimized images for a professional look.

### STEP 12
Open the HTML file in a browser to check layout and functionality.

### STEP 13
Fix styling issues and refine content placement.

### STEP 14
Deploy the website.

### STEP 15
Upload to GitHub Pages for free hosting.

## PROGRAM
LOGIN.HTML
```
<!DOCTYPE html>
<html>
<head>
<title>Login</title>

<style>
body{
font-family:Arial;
background:#f3f3f3;
display:flex;
justify-content:center;
align-items:center;
height:100vh;
}

.login-box{
background:white;
padding:30px;
border-radius:5px;
text-align:center;
}

input{
width:200px;
padding:10px;
margin:10px;
}

button{
padding:10px 20px;
background:#febd69;
border:none;
cursor:pointer;
}
</style>
</head>

<body>

<div class="login-box">

<h2>Login</h2>

<input type="text" id="email" placeholder="Email"><br>
<input type="password" id="password" placeholder="Password"><br>

<button onclick="login()">Login</button>

<p id="msg"></p>

</div>

<script>
function login(){
let email=document.getElementById("email").value
let password=document.getElementById("password").value

if(email=="" || password==""){
document.getElementById("msg").innerHTML="Enter Email and Password"
}else{
window.location.href="products.html"
}
}
</script>

</body>
</html>
```
PRODUCT.HTML
```
<!DOCTYPE html>
<html>
<head>
<title>shoplex</title>

<style>

body{
font-family:Arial;
margin:0;
background:#f3f3f3;
}

/* Navbar */

.navbar{
background:#131921;
color:white;
padding:15px;
display:flex;
justify-content:space-between;
}

.navbar a{
color:white;
margin-left:15px;
text-decoration:none;
cursor:pointer;
}

/* Login Box */

.login-box{
background:white;
padding:30px;
width:300px;
margin:50px auto;
text-align:center;
border-radius:5px;
}

/* Products */

.products{
display:grid;
grid-template-columns:repeat(3,1fr);
gap:20px;
padding:20px;
display:none; /* hidden until login */
}

.product{
background:white;
padding:20px;
text-align:center;
border-radius:5px;
}

.product img{
width:180px;
height:180px;
object-fit:cover;
}

button{
background:#ffd814;
border:none;
padding:10px;
cursor:pointer;
margin-top:10px;
}

</style>

</head>

<body>

<!-- Navbar -->

<div class="navbar">
<h2>SHOPLEX</h2>

<div>
<a onclick="showLogin()">Login</a>
<a href="cart.html">Cart 🛒</a>
<a href="contact.html">Contact</a>
<a onclick="logout()">Logout</a>
</div>
</div>

<!-- Login Section -->

<div class="login-box" id="loginBox">

<h2>Login</h2>

<input type="text" id="email" placeholder="Email"><br>
<input type="password" id="password" placeholder="Password"><br>

<button onclick="login()">Login</button>

<p id="msg"></p>

</div>

<!-- Products Section -->

<div class="products" id="productSection">

<div class="product">
<img src="https://images.unsplash.com/photo-1505740420928-5e560c06d30e">
<h3>Headphones</h3>
<p>$50</p>
<button onclick="add('Headphones',50)">Add to Cart</button>
</div>

<div class="product">
<img src="https://images.unsplash.com/photo-1517336714731-489689fd1ca8">
<h3>Laptop</h3>
<p>$900</p>
<button onclick="add('Laptop',900)">Add to Cart</button>
</div>

<div class="product">
<img src="https://m.media-amazon.com/images/I/71UD0DCIVSL._AC_UF1000,1000_QL80_.jpg">
<h3>Camera</h3>
<p>$300</p>
<button onclick="add('Camera',300)">Add to Cart</button>
</div>

<div class="product">
<img src="https://images.unsplash.com/photo-1511707171634-5f897ff02aa9">
<h3>Smartphone</h3>
<p>$600</p>
<button onclick="add('Smartphone',600)">Add to Cart</button>
</div>

<div class="product">
<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS5Eg9OwKfsgmNx5RtcPq5X7Fn9Tl3La4Kfsw&s">
<h3>Speaker</h3>
<p>$80</p>
<button onclick="add('Speaker',80)">Add to Cart</button>
</div>

<div class="product">
<img src="https://store.storeimages.cdn-apple.com/1/as-images.apple.com/is/MXCK3?wid=4000&hei=4000&fmt=jpeg&qlt=90&.v=1730320444782">
<h3>Keyboard</h3>
<p>$40</p>
<button onclick="add('Keyboard',40)">Add to Cart</button>
</div>

</div>

<!-- JavaScript -->

<script>

// Show login manually
function showLogin(){
document.getElementById("loginBox").style.display="block"
document.getElementById("productSection").style.display="none"
}

// Login function
function login(){

let email=document.getElementById("email").value
let password=document.getElementById("password").value

if(email=="" || password==""){
document.getElementById("msg").innerHTML="Enter Email and Password"
}
else{
localStorage.setItem("loggedIn","true")

document.getElementById("loginBox").style.display="none"
document.getElementById("productSection").style.display="grid"
}

}

// Auto check login on page load
if(localStorage.getItem("loggedIn") === "true"){
document.getElementById("loginBox").style.display="none"
document.getElementById("productSection").style.display="grid"
}

// Logout
function logout(){
localStorage.removeItem("loggedIn")
location.reload()
}

// Add to Cart
function add(name, price){

let cart = JSON.parse(localStorage.getItem("cart")) || []

cart.push({name:name, price:price})

localStorage.setItem("cart", JSON.stringify(cart))

alert(name + " added to cart")

}

</script>

</body>
</html>
```
CONTACT.HTML
```
<!DOCTYPE html>
<html>
<head>
<title>Contact Us</title>

<style>

body{
font-family:Arial;
background:#f3f3f3;
text-align:center;
padding:30px;
}

.contact-box{
background:white;
padding:30px;
width:350px;
margin:auto;
border-radius:5px;
}

input,textarea{
width:90%;
padding:10px;
margin:10px;
}

button{
padding:10px 20px;
background:#febd69;
border:none;
cursor:pointer;
}

.info{
background:white;
padding:20px;
margin:20px auto;
width:350px;
border-radius:5px;
text-align:left;
}

h3{
color:#131921;
}

</style>

</head>

<body>

<!-- Contact Form -->

<div class="contact-box">

<h2>Contact Us</h2>

<input type="text" placeholder="Your Name">
<input type="email" placeholder="Email">
<textarea placeholder="Your Message"></textarea>

<button onclick="send()">Send</button>

<p id="msg"></p>

</div>

<!-- Helpline Info -->

<div class="info">

<h3>📞 Helpline Number</h3>
<p>+91 98765 43210</p>

</div>

<!-- Refund Steps -->

<div class="info">

<h3>🔄 Refund Process</h3>

<p>1. Go to Products page</p>
<p>2. Open your Cart</p>
<p>3. Click "Remove" on the product</p>
<p>4. Contact support using this page</p>
<p>5. Refund will be processed in 3-5 days</p>

</div>

<script>

function send(){
document.getElementById("msg").innerHTML="Message Sent Successfully"
}

</script>

</body>
</html>
```

## OUTPUT
![alt text](<Screenshot 2026-03-17 232645.png>)
![alt text](<Screenshot 2026-03-17 232657.png>)
![alt text](<Screenshot 2026-03-17 233115.png>)

## RESULT
The program for creating commercial website using CSS Flexbox is executed successfully.
