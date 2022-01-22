<template>
<div id="productspage">
  <br>
  <br>
  <br>
  <br>
  <br>
  <div class="container">
      <br>
      <center>
 <v-text-field 
                hide-details 
                label="Filled" 
                placeholder="Search" 
                filled 
                rounded 
                dense 
                single-line 
                append-icon="mdi-magnify" 
                >
            </v-text-field>
      </center>
</div>

<div class="small-container">
  <div class="row row-2">
    <h2>Featured by top sellers</h2>
    <select>
      <option value="">Default Shorting</option>
      <option value="">Short by price</option>
      <option value="">Short by popularity</option>
      <option value="">Short by rating</option>
      <option value="">Short by sale</option>
    </select>
  </div>
  <div class="row">
    <div class="col-4">
      <img src="https://www.hemswell-antiques.com/uploads/media/news/0001/69/thumb_68212_news_wide.jpeg" alt="" />
      <h4>test product</h4>
      <div class="rating">
        <i class="fas fa-star"></i>
        <i class="fas fa-star"></i>
        <i class="fas fa-star"></i>
        <i class="fas fa-star"></i>
        <i class="far fa-star"></i>
      </div>
      <p>£500.00</p>
    </div>

    <div class="col-4">
      <img src="data:image/jpeg;base64,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" alt="" />
      <h4>test product</h4>
      <div class="rating">
        <i class="fas fa-star"></i>
        <i class="fas fa-star"></i>
        <i class="fas fa-star"></i>
        <i class="far fa-star"></i>
        <i class="far fa-star"></i>
      </div>
      <p>£500.00</p>
    </div>

    <div class="col-4">
      <img src="https://assets.rebelmouse.io/eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpbWFnZSI6Imh0dHBzOi8vYXNzZXRzLnJibC5tcy8yNDU1MTM5NC9vcmlnaW4uanBnIiwiZXhwaXJlc19hdCI6MTY0MDkwNDA5NX0.Qr8yaRHj_V1vEdYdRBIOysHxnwzd16guzqxwSzyhhFg/img.jpg?width=1245&quality=85&coordinates=0%2C0%2C0%2C0&height=700" alt="" />
     <h4>test product</h4>
      <div class="rating">
        <i class="fas fa-star"></i>
        <i class="fas fa-star"></i>
        <i class="fas fa-star"></i>
        <i class="far fa-star"></i>
        <i class="far fa-star"></i>
      </div>
      <p>£500.00</p>
    </div>

    <div class="col-4">
      <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTr6pm-n51aOHj5_TZWdO5grAeMw5O_gW8jFQ&usqp=CAU" alt="" />
    <h4>test product</h4>
      <div class="rating">
        <i class="fas fa-star"></i>
        <i class="fas fa-star"></i>
        <i class="fas fa-star"></i>
        <i class="far fa-star"></i>
        <i class="far fa-star"></i>
      </div>
      <p>£500.00</p>
    </div>
  </div>

 
  


  <div class="page-btn">
    <span>1</span>
    <span>2</span>
    <span>3</span>
    <span>4</span>
    <span>&#8594;</span>
  </div>
</div>

<!-- Footer -->
<div class="footer">
  <div class="container">
    <div class="row">
      <div class="footer-col-1">
        <h3>Download Our App</h3>
        <p>Download App for Android and iso mobile phone.</p>
        <div class="app-logo">
          <img src="https://i.ibb.co/KbPTYYQ/play-store.png" alt="" />
          <img src="https://i.ibb.co/hVM4X2p/app-store.png" alt="" />
        </div>
      </div>

      <div class="footer-col-2">
        <img src="https://i.ibb.co/j3FNGj7/logo-white.png" alt="" />
        <p>
          Our Purpose Is To Sustainably Make the Pleasure and Benefits of
          Sports Accessible to the Many.
        </p>
      </div>

      <div class="footer-col-3">
        <h3>Useful Links</h3>
        <ul>
          <li>Coupons</li>
          <li>Blog Post</li>
          <li>Return Policy</li>
          <li>Join Affiliate</li>
        </ul>
      </div>

      <div class="footer-col-4">
        <h3>Follow us</h3>
        <ul>
          <li>Facebook</li>
          <li>Twitter</li>
          <li>Instagram</li>
          <li>YouTube</li>
        </ul>
      </div>
    </div>
    <hr />
    <p class="copyright">Copyright &copy; 2021 - Red Store</p>
  </div>
</div>


    </div>
</template>

<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
import VueCookies from 'vue-cookies'

Vue.use(VueAxios, axios);
Vue.use(VueCookies);
export default ({
  name: 'ProductsPage',
  data() {
    return {
      //
    }
  },
  beforeMount(){
    //check if the token from cookie is valid else redirect to login page
    this.axios.get('https://localhost:44316/api/users/AuthenticateUser',{
      headers: {
        Authorization: 'bearer ' + this.$cookies.get('jwt')
      }
    }).then(response => {
      if(response.status == 200){
            console.log("Authenticated");
           console.warn(response.data);
      }
    }).catch(error => {
            console.warn(error);
            location.href = 'http://localhost:8080/pagenotfound';

    });
  }
})
</script>
<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Poppins", sans-serif;
}

.navbar {
  display: flex;
  align-items: center;
  padding: 20px;
}

nav {
  flex: 1;
  text-align: right;
}

nav ul {
  display: inline-block;
  list-style-type: none;
}

nav ul li {
  display: inline-block;
  margin-right: 20px;
}

a {
  text-decoration: none;
  color: #555;
}

p {
  color: #555;
}

.container {
  max-width: 1300px;
  margin: auto;
  padding-left: 25px;
  padding-right: 25px;
}

.row {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  justify-content: space-around;
}

.col-2 {
  flex-basis: 50%;
  min-width: 300px;
}

.col-2 img {
  max-width: 100%;
  padding: 50px 0;
}

.col-2 h1 {
  font-size: 50px;
  line-height: 60px;
  margin: 25px 0;
}

.btn {
  display: inline-block;
  background: #ff523b;
  color: #ffffff;
  padding: 8px 30px;
  margin: 30px 0;
  border-radius: 30px;
  transition: background 0.5s;
}

.btn:hover {
  background: #563434;
}

.header {
  background: radial-gradient(#fff, #ffd6d6);
}

.header .row {
  margin-top: 70px;
}

.categories {
  margin: 70px 0;
}

.col-3 {
  flex-basis: 30%;
  min-width: 250px;
  margin-bottom: 30px;
}

.col-3 img {
  width: 100%;
}

.small-container {
  max-width: 1080px;
  margin: auto;
  padding-left: 25px;
  padding-right: 25px;
}

.col-4 {
  flex-basis: 25%;
  padding: 10px;
  min-width: 200px;
  margin-bottom: 50px;
  transition: transform 0.5s;
}

.col-4 img {
  width: 100%;
}

.title {
  text-align: center;
  margin: 0 auto 80px;
  position: relative;
  line-height: 60px;
  color: #555;
}
.title::after {
  content: "";
  background: #ff523b;
  width: 80px;
  height: 5px;
  border-radius: 5px;
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translate(-50%);
}

h4 {
  color: #555;
  font-weight: normal;
}

.col-4 p {
  font-size: 14px;
}

.rating .fas {
  color: #ff523b;
}

.rating .far {
  color: #ff523b;
}

.col-4:hover {
  transform: translateY(-5px);
}

/* Offer */

.offer {
  background: radial-gradient(#fff, #ffd6d6);
  margin-top: 80px;
  padding: 30px 0;
}

.col-2 .offer-img {
  padding: 50px;
}

small {
  color: #555;
}

/* testimonial */

.testimonial {
  padding-top: 100px;
}

.testimonial .col-3 {
  text-align: center;
  padding: 40px 20px;
  box-shadow: 0 0 20px 0px rgba(0, 0, 0, 0.1);
  cursor: pointer;
  transition: transform 0.5s;
}

.testimonial .col-3 img {
  width: 100px;
  margin-top: 20px;
  border-radius: 50%;
}

.testimonial .col-3:hover {
  transform: translateY(-10px);
}

.fa-quote-left {
  font-size: 34px;
  color: #ff523b;
}

.col-3 p {
  font-size: 14px;
  margin: 12px 0;
  color: #777777;
}

.testimonial .col-3 h3 {
  font-weight: 600;
  color: #555;
  font-size: 16px;
}

.brands {
  margin: 100px auto;
}

.col-5 {
  width: 160px;
}

.col-5 img {
  width: 100%;
  cursor: pointer;
  filter: grayscale(100%);
}

.col-5 img:hover {
  width: 100%;
  cursor: pointer;
  filter: grayscale(0);
}

/* footer */

.footer {
  background: #000;
  color: #8a8a8a;
  font-size: 14px;
  padding: 60px 0 20px;
}

.footer p {
  color: #8a8a8a;
}

.footer h3 {
  color: #ffffff;
  margin-bottom: 20px;
}

.footer-col-1,
.footer-col-2,
.footer-col-3,
.footer-col-4 {
  min-width: 250px;
  margin-bottom: 20px;
}

.footer-col-1 {
  flex-basis: 30%;
}

.footer-col-2 {
  flex: 1;
  text-align: center;
}

.footer-col-2 img {
  width: 180px;
  margin-bottom: 20px;
}

.footer-col-3,
.footer-col-4 {
  flex-basis: 12%;
  text-align: center;
}

ul {
  list-style-type: none;
}

.app-logo {
  margin-top: 20px;
}
.app-logo img {
  width: 140px;
}

.footer hr {
  border: none;
  background: #b5b5b5;
  height: 1px;
  margin: 20px 0;
}

.copyright {
  text-align: center;
}

.menu-icon {
  width: 28px;
  margin-left: 20px;
  display: none;
}

/* media query for menu */

@media only screen and (max-width: 800px) {
  nav ul {
    position: absolute;
    top: 70px;
    left: 0;
    background: #333;
    width: 100%;
    overflow: hidden;
    transition: max-height 0.5s;
  }
  nav ul li {
    display: block;
    margin-right: 50px;
    margin-top: 10px;
    margin-bottom: 10px;
  }

  nav ul li a {
    color: #fff;
  }
  .menu-icon {
    display: block;
    cursor: pointer;
  }
}

/* all products page */

.row-2 {
  justify-content: space-between;
  margin: 100px auto 50px;
}

select {
  border: 1px solid #ff523b;
  padding: 5px;
}

select:focus {
  outline: none;
}

.page-btn {
  margin: 0 auto 80px;
}

.page-btn span {
  display: inline-block;
  border: 1px solid #ff523b;
  margin-left: 10px;
  width: 40px;
  height: 40px;
  text-align: center;
  line-height: 40px;
  cursor: pointer;
}

.page-btn span:hover {
  background: #ff523b;
  color: #ffffff;
}

/* single product details */

.single-product {
  margin-top: 80px;
}

.single-product .col-2 img {
  padding: 0;
}

.single-product .col-2 {
  padding: 20px;
}

.single-product h4 {
  margin: 20px 0;
  font-size: 22px;
  font-weight: bold;
}

.single-product select {
  display: block;
  padding: 10px;
  margin-top: 20px;
}

.single-product input {
  width: 50px;
  height: 40px;
  padding-left: 10px;
  font-size: 20px;
  margin-right: 10px;
  border: 1px solid #ff523b;
}

input:focus {
  outline: none;
}

.single-product .fas {
  color: #ff523b;
  margin-left: 10px;
}

.small-img-row {
  display: flex;
  justify-content: space-between;
}

.small-img-col {
  flex-basis: 24%;
  cursor: pointer;
}

/* cart items */

.cart-page {
  margin: 90px auto;
}

table {
  width: 100%;
  border-collapse: collapse;
}

.cart-info {
  display: flex;
  flex-wrap: wrap;
}

th {
  text-align: left;
  padding: 5px;
  color: #ffffff;
  background: #ff523b;
  font-weight: normal;
}
td {
  padding: 10px 5px;
}

td input {
  width: 40px;
  height: 30px;
  padding: 5px;
}

td a {
  color: #ff523b;
  font-size: 12px;
}

td img {
  width: 80px;
  height: 80px;
  margin-right: 10px;
}

.total-price {
  display: flex;
  justify-content: flex-end;
}

.total-price table {
  border-top: 3px solid #ff523b;
  width: 100%;
  max-width: 400px;
}

td:last-child {
  text-align: right;
}

th:last-child {
  text-align: right;
}
/* account page */
.account-page {
  padding: 50px 0;
  background: radial-gradient(#fff, #ffd6d6);
}

.form-container {
  background: #ffffff;
  width: 300px;
  height: 400px;
  position: relative;
  text-align: center;
  padding: 20px 0;
  margin: auto;
  box-shadow: 0 0 20px 0px rgba(0, 0, 0, 0.1);
  overflow: hidden;
}

.form-container span {
  font-weight: bold;
  padding: 0 10px;
  color: #555555;
  cursor: pointer;
  width: 100px;
  display: inline-block;
}

.form-btn {
  display: inline-block;
}

.form-container form {
  max-width: 300px;
  padding: 0 20px;
  position: absolute;
  top: 130px;
  transition: transform 1s;
}

form input {
  width: 100%;
  height: 30px;
  margin: 10px 0;
  padding: 0 10px;
  border: 1px solid #ccc;
}

form .btn {
  width: 100%;
  border: none;
  cursor: pointer;
  margin: 10px 0;
}

form .btn:focus {
  outline: none;
}

#LoginForm {
  left: -300px;
}

#RegForm {
  left: 0;
}

form a {
  font-size: 12px;
}

#Indicator {
  width: 100px;
  border: none;
  background: #ff523b;
  height: 3px;
  margin-top: 8px;
  transform: translateX(100px);
  transition: transform 1s;
}

/* media query for less than 600 screen size */

@media only screen and (max-width: 600px) {
  .row {
    text-align: center;
  }
  .col-2,
  .col-3,
  .col-4 {
    flex-basis: 100%;
  }

  .single-product .row {
    text-align: left;
  }

  .single-product .col-2 {
    padding: 20px 0;
  }
  .single-product h1 {
    font-size: 26px;
    line-height: 32px;
  }
  .cart-info p {
    display: none;
  }
}


</style>
