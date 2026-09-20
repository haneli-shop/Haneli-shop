<!doctype html>
<html lang="fa" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>هانلی</title>

<style>
body{
font-family:Tahoma,Arial;
margin:0;
background:#fff7fa;
color:#333
}

header{
background:#d81b60;
color:#fff;
text-align:center;
padding:20px
}

.logo{
font-size:30px;
font-weight:bold
}

button{
padding:10px 14px;
border:0;
border-radius:10px;
cursor:pointer;
font-family:inherit
}

nav{
margin-top:15px;
display:flex;
gap:8px;
justify-content:center;
flex-wrap:wrap
}

nav button{
color:#d81b60
}

.wrap{
max-width:1000px;
margin:auto;
padding:20px
}

.search,input,textarea{
width:100%;
box-sizing:border-box;
padding:12px;
border:1px solid #ddd;
border-radius:10px;
margin:7px 0;
font-family:inherit
}

.cats{
display:flex;
gap:7px;
flex-wrap:wrap;
margin:15px 0
}

.cats button{
background:#f8d5e1;
color:#9b1749
}

.cats .on,
.main{
background:#d81b60;
color:#fff
}

.grid{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(210px,1fr));
gap:15px
}

.card,
.section{
background:#fff;
padding:18px;
border-radius:15px;
box-shadow:0 3px 12px #0001
}

.pic{
height:120px;
background:#fde0e9;
border-radius:12px;
display:flex;
align-items:center;
justify-content:center;
font-size:50px
}

.price{
color:#d81b60;
font-weight:bold;
margin:10px 0
}

.main{
width:100%
}

.section{
display:none;
margin-top:20px
}

.section.show{
display:block
}

.tabs{
display:flex;
gap:7px
}

.tabs button{
flex:1;
background:#f8d5e1;
color:#9b1749
}

.tabs .on{
background:#d81b60;
color:#fff
}

.form{
display:none
}

.form.show{
display:block
}

.msg{
padding:10px;
border-radius:9px;
margin:10px 0;
background:#e8f5e9
}

.cartrow{
padding:14px 0;
border-bottom:1px solid #eee
}

.qty{
display:flex;
gap:6px;
align-items:center;
margin-top:8px;
flex-wrap:wrap
}

.qty button{
background:#f8d5e1
}

.qty .delete{
background:#ffe5e5;
color:#b00020
}

.cart-actions{
display:flex;
gap:8px;
margin:15px 0;
flex-wrap:wrap
}

.clear-cart{
background:#ffe5e5;
color:#b00020
}

.empty{
padding:20px;
text-align:center;
background:#fff7fa;
border-radius:10px;
color:#777
}

.total{
font-size:20px;
font-weight:bold;
color:#d81b60;
text-align:center;
margin:18px
}

.pay{
background:#fff0f5;
padding:14px;
border-radius:10px;
line-height:2;
margin:15px 0
}

.close{
float:left;
background:#eee
}
</style>
</head>

<body>

<header>

<div class="logo">🌸 هانلی</div>

<div>فروشگاه لوازم آرایشی</div>

<nav>

<button onclick="openAccount()">
👤 ثبت‌نام / ورود
</button>

<button onclick="openCart()">
🛒 سبد خرید (<span id="count">0</span>)
</button>

</nav>

</header>


<main class="wrap">

<input
id="search"
class="search"
placeholder="🔎 جستجوی محصول"
>

<div class="cats">

<button class="on" onclick="setCat('همه',this)">
همه
</button>

<button onclick="setCat('لب',this)">
لب
</button>

<button onclick="setCat('چشم',this)">
چشم
</button>

<button onclick="setCat('پوست',this)">
پوست
</button>

</div>


<div id="products" class="grid"></div>


<!-- حساب کاربری -->

<section id="account" class="section">

<button class="close" onclick="closeAll()">
✕
</button>

<h2>👤 حساب کاربری</h2>

<div id="msg"></div>

<div id="auth">

<div class="tabs">

<button id="rt"
class="on"
onclick="tab('reg')">
ثبت‌نام
</button>

<button id="lt"
onclick="tab('login')">
ورود
</button>

</div>


<div id="reg" class="form show">

<input
id="name"
placeholder="نام و نام خانوادگی"
>

<input
id="phone"
placeholder="شماره موبایل"
>

<input
id="pass"
type="password"
placeholder="رمز عبور"
>

<input
id="pass2"
type="password"
placeholder="تکرار رمز عبور"
>

<button
class="main"
onclick="registerUser()"
>
ثبت‌نام
</button>

</div>


<div id="login" class="form">

<input
id="lphone"
placeholder="شماره موبایل"
>

<input
id="lpass"
type="password"
placeholder="رمز عبور"
>

<button
class="main"
onclick="loginUser()"
>
ورود
</button>

</div>

</div>


<div id="user" style="display:none"></div>

</section>



<!-- سبد خرید -->

<section id="cart" class="section">

<button class="close" onclick="closeAll()">
✕
</button>

<h2>🛒 سبد خرید</h2>

<div id="items"></div>


<div class="cart-actions">

<button
class="clear-cart"
onclick="clearCart()"
>
🧹 خالی کردن سبد
</button>

</div>


<div
id="total"
class="total"
></div>


<div
id="checkout"
style="display:none"
>

<input
id="cname"
placeholder="نام و نام خانوادگی"
>

<input
id="cphone"
placeholder="شماره موبایل"
>

<textarea
id="address"
placeholder="آدرس کامل"
></textarea>


<div class="pay">

💳 کارت به کارت

<br>

شماره کارت:

<b>
6219 8619 8303 3399
</b>

<br>

به نام:

<b>
هانیه کریمی خانقاه
</b>

<br>

🚚 هزینه ارسال بر عهده خریدار است و هنگام تحویل پرداخت می‌شود.

</div>


<input
id="receipt"
type="file"
accept="image/*"
>

<br>
<br>

<button
class="main"
onclick="order()"
>
📱 ثبت سفارش در واتساپ
</button>

</div>

</section>

</main>


<footer
style="text-align:center;padding:30px"
>
🌸 هانلی
</footer>



<script>

var products=[

{
id:1,
n:'رژ لب مات هانلی',
p:249000,
c:'لب',
i:'💄'
},

{
id:2,
n:'ریمل حجم‌دهنده',
p:319000,
c:'چشم',
i:'👁️'
},

{
id:3,
n:'کرم مرطوب‌کننده',
p:289000,
c:'پوست',
i:'🧴'
},

{
id:4,
n:'پالت سایه چشم',
p:459000,
c:'چشم',
i:'🎨'
},

{
id:5,
n:'بالم لب',
p:159000,
c:'لب',
i:'💋'
},

{
id:6,
n:'سرم مراقبت پوست',
p:529000,
c:'پوست',
i:'✨'
}

];


var cat='همه';

var cart=[];


try{

cart=JSON.parse(
localStorage.getItem('haneliCart') || '[]'
);

}catch(e){

cart=[];

}



function money(n){

return Number(n).toLocaleString('fa-IR')
+
' تومان';

}



function save(){

localStorage.setItem(
'haneliCart',
JSON.stringify(cart)
);

}



function render(){

var q=document
.getElementById('search')
.value
.toLowerCase()
.trim();


var box=document
.getElementById('products');

box.innerHTML='';


products
.filter(function(p){

return(

(cat==='همه'||p.c===cat)

&&

p.n.toLowerCase()
.indexOf(q)>-1

);

})
.forEach(function(p){

box.innerHTML+=

'<article class="card">'+

'<div class="pic">'+
p.i+
'</div>'+

'<h3>'+
p.n+
'</h3>'+

'<div>'+
'دسته: '+
p.c+
'</div>'+

'<div class="price">'+
money(p.p)+
'</div>'+

'<button class="main" onclick="add('+p.id+')">'+
'➕ افزودن به سبد'+
'</button>'+

'</article>';

});

}



function setCat(x,b){

cat=x;


document
.querySelectorAll('.cats button')
.forEach(function(a){

a.classList.remove('on');

});


b.classList.add('on');

render();

}



function add(id){

var x=cart.find(function(a){

return a.id===id;

});


if(x){

x.q++;

}else{

cart.push({

id:id,
q:1

});

}


save();

draw();


alert(
'محصول به سبد خرید اضافه شد 🌸'
);

}



function plus(id){

var x=cart.find(function(a){

return a.id===id;

});


if(x){

x.q++;

}


save();

draw();

}



function minus(id){

var x=cart.find(function(a){

return a.id===id;

});


if(!x){

return;

}


if(x.q>1){

x.q--;

}else{

removeItem(id);

return;

}


save();

draw();

}



function removeItem(id){

cart=cart.filter(function(a){

return a.id!==id;

});


save();

draw();

}



function clearCart(){

if(!cart.length){

return;

}


if(
confirm(
'آیا مطمئن هستید که می‌خواهید کل سبد خرید خالی شود؟'
)
){

cart=[];

save();

draw();

}

}



function draw(){

var box=document
.getElementById('items');


var total=0;

var count=0;


box.innerHTML='';


cart.forEach(function(x){

var p=products.find(function(a){

return a.id===x.id;

});


if(!p){

return;

}


total+=p.p*x.q;

count+=x.q;


box.innerHTML+=

'<div class="cartrow">'+

'<b>'+
p.n+
'</b>'+

'<br>'+

money(p.p)+


'<div class="qty">'+


'<button onclick="minus('+p.id+')">'+
'−'+
'</button>'+


'<b>'+
x.q+
'</b>'+


'<button onclick="plus('+p.id+')">'+
'+'+
'</button>'+


'<button class="delete" onclick="removeItem('+p.id+')">'+
'🗑️ حذف'+
'</button>'+
