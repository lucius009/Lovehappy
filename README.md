

<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>💖 Открой моё сердце</title>

<style>
body{
margin:0;
font-family:Arial;
background:linear-gradient(135deg,#ff9a9e,#fad0c4);
overflow-x:hidden;
text-align:center;
}

.card{
max-width:780px;
margin:30px auto;
background:white;
padding:25px;
border-radius:20px;
box-shadow:0 10px 30px rgba(0,0,0,0.2);
animation:popIn 1s ease;
}

@keyframes popIn{
from{transform:scale(0.85);opacity:0;}
to{transform:scale(1);opacity:1;}
}

button{
padding:10px 15px;
border:none;
border-radius:12px;
background:#ffb6c1;
cursor:pointer;
transition:0.3s;
}

button:hover{
transform:scale(1.08);
box-shadow:0 5px 15px rgba(0,0,0,0.2);
}

.link{
background:#fff0f5;
padding:14px;
margin:10px 0;
border-radius:12px;
cursor:pointer;
font-weight:bold;
transition:0.3s;
animation:fadeUp 0.6s ease;
}

.link:hover{
transform:scale(1.03);
background:#ffe4ec;
}

@keyframes fadeUp{
from{opacity:0;transform:translateY(10px);}
to{opacity:1;transform:translateY(0);}
}

.text{
display:none;
margin-top:10px;
padding:14px;
background:#fffafc;
border-radius:12px;
text-align:left;
line-height:1.6;
white-space:pre-wrap;
animation:fade 0.6s ease;
}

@keyframes fade{
from{opacity:0;transform:translateY(-10px);}
to{opacity:1;transform:translateY(0);}
}

/* сердечки */
.heart{
position:fixed;
top:-10px;
font-size:18px;
color:white;
animation:fall 4s linear;
}

@keyframes fall{
to{transform:translateY(110vh);}
}

/* блёстки */
.spark{
position:fixed;
width:6px;
height:6px;
background:white;
border-radius:50%;
animation:spark 2s linear forwards;
}

@keyframes spark{
to{transform:translateY(-100px) scale(0);opacity:0;}
}

.hidden{display:none;}

#secret{
display:none;
margin-top:20px;
padding:18px;
background:#fff0f8;
border-radius:15px;
text-align:left;
animation:fade 1s ease;
line-height:1.6;
}

</style>
</head>

<body>

<div class="card">

<h1>💖 Открой моё сердце</h1>

<button onclick="start()">Начать 💌</button>

<div id="list" style="display:none;">

<div class="link" onclick="toggle(1)">❤️ 1. Почему именно ты<div id="t1" class="text"></div></div>
<div class="link" onclick="toggle(2)">❤️ 2. Что я люблю в тебе<div id="t2" class="text"></div></div>
<div class="link" onclick="toggle(3)">❤️ 3. Наше знакомство<div id="t3" class="text"></div></div>
<div class="link" onclick="toggle(4)">❤️ 4. Воспоминание<div id="t4" class="text"></div></div>
<div class="link" onclick="toggle(5)">❤️ 5. Спасибо тебе<div id="t5" class="text"></div></div>
<div class="link" onclick="toggle(6)">❤️ 6. Как ты изменил мою жизнь<div id="t6" class="text"></div></div>
<div class="link" onclick="toggle(7)">❤️ 7. Восхищение<div id="t7" class="text"></div></div>
<div class="link" onclick="toggle(8)">❤️ 8. Тайна<div id="t8" class="text"></div></div>
<div class="link" onclick="toggle(9)">❤️ 9. Мечта<div id="t9" class="text"></div></div>
<div class="link" onclick="toggle(10)">❤️ 10. Финал<div id="t10" class="text"></div></div>

</div>

<div id="secret"></div>

<button id="giftBtn" class="hidden" onclick="gift()">🎁 Финальный подарок</button>

</div>

<script>

let step=1;

/* 💖 ДЛИННЫЕ ТЕКСТЫ */
const texts={

1:`

Иногда я думаю о том, как странно и красиво складывается жизнь.

Среди миллионов людей ты стал тем самым человеком, который оказался мне ближе всех. Это не про случайность - это про ощущение.

Рядом с тобой я чувствую спокойствие, тепло и уверенность. Мне не нужно притворяться или играть роль. Я могу быть собой, и ты принимаешь меня таким, какой я есть.`,

2:`

Я люблю в тебе гораздо больше, чем можно объяснить словами.

Я люблю твою улыбку - она делает мир вокруг мягче.  
Я люблю твой голос - он остаётся в голове и сердце.  
Я люблю твою заботу, даже если ты сам этого не замечаешь.

Но больше всего я люблю твою настоящесть. Ты не пытаешься быть кем-то другим.`,

3:`

Я до сих пор помню момент, когда мы впервые пересеклись.

Тогда это казалось обычным событием, но со временем стало понятно, что это начало чего-то очень важного.

Каждое сообщение, каждый разговор - всё это незаметно сближало нас.`,

4:`

Самые ценные воспоминания - это не большие события.

Это обычные моменты: разговоры, смех, тишина, ожидание сообщений.

И именно они с тобой стали для меня самыми тёплыми.`,

5:`

Спасибо тебе за всё, что ты даже не считаешь чем-то особенным.

За поддержку, за внимание, за присутствие в моей жизни.

Иногда ты даже не понимаешь, насколько сильно влияешь на меня.`,

6:`

С тобой моя жизнь стала другой.

Она стала спокойнее, теплее и светлее.

Я стал чаще улыбаться и меньше переживать. Ты изменил мой мир просто тем, что ты есть.`,

7:`

Я восхищаюсь тобой.

Твоей силой, твоим характером, твоей добротой и тем, как ты справляешься с жизнью.

Ты вдохновляешь меня.`,

8:`

Есть одна вещь, которую ты, возможно, не замечаешь.

Иногда я просто думаю о тебе - и улыбаюсь.

И это происходит чаще, чем ты думаешь.`,

9:`

Моя мечта очень простая.

Больше времени вместе, больше разговоров, больше обычных моментов.

И самое главное - чтобы ты был рядом всегда.`,

10:`

Если сказать честно…

Ты стал для меня самым важным человеком.

И я люлюкаюююю тебя.`
};

/* открыть */
function toggle(id){

if(id!==step) return;

let el=document.getElementById("t"+id);

if(el.style.display==="block") return;

el.style.display="block";
el.innerText=texts[id];

step++;

sparkles();

if(step>10){
showSecret();
}
}

/* старт */
function start(){
document.getElementById("list").style.display="block";
burst();
}

/* 💖 СЕКРЕТНЫЙ ФИНАЛ (ДЛИННЫЙ) */
function showSecret(){

let s=document.getElementById("secret");
s.style.display="block";

s.innerHTML=`
<h2>🔐 Секретный финал</h2>

<p>
💖 Если ты читаешь это - значит ты прошёл весь путь до конца.<br><br>

Я хочу сказать тебе самое главное, что иногда сложно выразить словами.<br><br>

Ты стал для меня не просто важным человеком.<br>
Ты стал частью моей жизни, моих мыслей и моего сердца.<br><br>

С тобой всё ощущается иначе - спокойнее, теплее, глубже.<br>
Ты можешь даже не замечать этого, но ты влияешь на меня каждый день.<br><br>

Иногда я думаю о том, как бы всё было без тебя… и понимаю, что это было бы совсем другое, более пустое пространство внутри меня.<br><br>

Я благодарен судьбе за то, что ты появился в моей жизни.<br>
И если бы мне дали возможность выбрать снова - я бы снова выбрала тебя.<br><br>

Потому что ты -- мой человек.<br>
Мин да эйигин олус күүскэ таптыыбын 💖
</p>
`;

document.getElementById("giftBtn").classList.remove("hidden");
}

/* подарок */
function gift(){
alert("💖 Финальный подарок открыт");
alert("Дай титю💕");
}

/* сердечки */
function hearts(){
let h=document.createElement("div");
h.innerHTML="❤";
h.classList.add("heart");
h.style.left=Math.random()*100+"vw";
h.style.animationDuration=(2+Math.random()*3)+"s";
document.body.appendChild(h);
setTimeout(()=>h.remove(),4000);
}
setInterval(hearts,250);

/* блёстки */
function sparkles(){
for(let i=0;i<10;i++){
let s=document.createElement("div");
s.classList.add("spark");
s.style.left=Math.random()*100+"vw";
s.style.top=(window.innerHeight-100)+"px";
document.body.appendChild(s);
setTimeout(()=>s.remove(),2000);
}
}

function burst(){
sparkles();
}

</script>

</body>
</html>
