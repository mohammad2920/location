<!DOCTYPE html>  
<html>  
<head>  
<meta charset="UTF-8">  
<title>Valentine Spin Wheel 💘</title>  
  
<link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css"/>  
  
<style>  
body{  
    font-family:Arial;  
    text-align:center;  
    background:#ffe6f0;  
}  
#wheel{  
    margin:30px auto;  
    width:300px;  
    height:300px;  
    border-radius:50%;  
    border:8px solid #ff4d88;  
    display:flex;  
    align-items:center;  
    justify-content:center;  
    font-size:28px;  
    background:white;  
}  
button{  
    padding:15px;  
    font-size:18px;  
    border:none;  
    border-radius:10px;  
    background:#ff4d88;  
    color:white;  
    cursor:pointer;  
}  
#map{  
    height:400px;  
    width:90%;  
    margin:auto;  
    border-radius:15px;  
    margin-top:20px;  
    display:none;  
}  
</style>  
</head>  
  
<body>  
  
<h1>🎡 Spin The Valentine Wheel 🎡</h1>  
<p>Where are we going for our date??</p>  
  
<div id="wheel">❓</div>  
  
<button onclick="spinWheel()">💘 Spin The Wheel 💘</button>  
  
<h2 id="result"></h2>  
  
<div id="map"></div>  
  
<script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>  
  
<script>  
  
var places = [  
"macdo 🍟",  
"burger king 👑",  
"Plume ☕",  
"yaso’s house 🏠",  
"Chops 🍖"  
];  
  
var map;  
var mapCreated = false;  
  
function spinWheel(){  
  
    var wheel = document.getElementById("wheel");  
    var result = document.getElementById("result");  
  
    var spins = 0;  
  
    var interval = setInterval(function(){  
  
        var randomIndex = Math.floor(Math.random()*places.length);  
        wheel.innerText = places[randomIndex];  
        spins++;  
  
        if(spins>15){  
            clearInterval(interval);  
  
            wheel.innerText = "Chops 🍖";  
            result.innerText = "🎉 Surprise! We're going to CHOPS!";  
  
            setTimeout(showMap,1200);  
        }  
  
    },150);  
}  
  
function showMap(){  
  
    document.getElementById("map").style.display="block";  
  
    
    var lat = 33.9000879;  
    var lng = 35.4987426;  
  
    if(!mapCreated){  
        map = L.map('map').setView([lat,lng],16);  
  
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',{  
            attribution:'Map data © OpenStreetMap'  
        }).addTo(map);  
  
        L.marker([lat,lng]).addTo(map)  
        .bindPopup("💘 Our Date at CHOPS!")  
        .openPopup();  
  
        mapCreated = true;  
    }  
}  
  
</script>  
  
</body>  
</html>  
