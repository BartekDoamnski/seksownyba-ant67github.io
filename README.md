<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>STYXXX SHOP</title>
    
<style>
body {
background: #000;
color: white;}
h2 { 
text-align: left;
}
button {
background: white;
color: black;
border: 1px solid #ccc;
padding: 12px 24px;
cursor: pointer;
}
#przycisk2 {
position: relative;
top: -45px;
}
.btn1 {
background: white;
color: black;
border: 1px solid #ccc;
padding: 12px 24px;
position: relative; 
top: -30px;        
} 
#koszyk {
margin-top: 20px;
border-top: 2px solid white;
padding-top: 10px;
}
#przycisk4 {
position: relative;
top: -35px;
}
</style>
<marquee><img src="https://styxxx.pl/cdn/shop/files/logo_stx.svg?v=1749645331&width=500"></marquee>
<hr></hr>
<!--Etui-->
<img src="https://styxxx.pl/cdn/shop/files/JOY_CASE_-_1.webp?v=1754992595&width=600" width="400" height="470" alt="Etui" style="margin-top: 30px;">
<h2 style="position: absolute; left: 65px; top: 60px;">Etui na telefon JOY [CASE]</h2>
<h2 style="position: absolute; left: 280px; top: 570px;"><b>49zł</b></h2>
<div style="text-align: left;">
<button onclick="dodajDoKoszyka(1)">DODAJ DO KOSZYKA</button>
</div>

<!--Album Deluxe-->
<h2 style="position: absolute; right: 65px; top: 60px;">RETO - STYXXX DELUXE</h2>
<img src="https://styxxx.pl/cdn/shop/files/STX_DELUXE_wisior-800x1066.webp?v=1754991290&width=600" 
width="400" height="470" alt="Album" 
style="float: right; margin-top: -520px;">
<h2 style="position: absolute; left: 750px; top: 570px;"><b>199zł</b></h2>
<div style="text-align: right;">
<button id="przycisk2" onclick="dodajDoKoszyka(2)">DODAJ DO KOSZYKA</button></div>

<!--Album -->
<img src="https://styxxx.pl/cdn/shop/files/STX_STANDARD_sjb_2-800x1066.webp?v=1749814362&width=600" width="400" height="470" alt="Etui">
<h2 style="position: absolute; left: 65px; top: 620px;">RETO - STYXXX CD</h2>
<h2 style="position: absolute; left: 280px; top: 1130px;"><b>59zł</b></h2>
<div style="text-align: left;">
<button onclick="dodajDoKoszyka(3)">DODAJ DO KOSZYKA</button> 
</div>

<!-- Czapka -->
<h2 style="position: absolute; right: 65px; top: 620px;">CAP STX 4EVER</h2>
<img src="https://styxxx.pl/cdn/shop/files/cap_3-800x1067-nobckgr.webp?v=1752902300&width=600" 
width="400" height="470" alt="Czapka" 
style="float: right; margin-top: -510px;">
<h2 style="position: absolute; left: 750px; top: 1130px;"><b>69zł</b></h2>
<div style="text-align: right;">
<button id="przycisk4" onclick="dodajDoKoszyka(4)">DODAJ DO KOSZYKA</button></div>

<!-- Koszyk -->
<h3>Koszyk</h3>
<div id="koszyk">Koszyk jest pusty</div>
<button id="przycisk1" onclick="zatwierdzZamowienie()">Zatwierdź zamówienie</button>

<script>
// Produkty
const produkty = [
{ id: 1, nazwa: "Etui JOY [CASE]", cena: 49 },
{ id: 2, nazwa: "RETO - STYXXX DELUXE", cena: 199 },
{ id: 3, nazwa: "RETO - STYXXX CD", cena: 59 },
{ id: 4, nazwa: "CAP STX 4EVER", cena: 69 } ];

// Koszyk
let koszyk = [];

// Dodawanie do koszyka
function dodajDoKoszyka(idProduktu) {
const produkt = produkty.find(p => p.id === idProduktu);
const wKoszyku = koszyk.find(p => p.id === idProduktu);
if (wKoszyku) {
wKoszyku.ilosc += 1;
} else { koszyk.push({ id: produkt.id, nazwa: produkt.nazwa, cena: produkt.cena, ilosc: 1 });}
wyswietlKoszyk();}

// Usuwanie z koszyka
function usunZKoszyka(idProduktu) {
koszyk = koszyk.filter(p => p.id !== idProduktu);
wyswietlKoszyk();}

// Obliczanie sumy
function obliczSume() {
return koszyk.reduce((suma, p) => suma + p.cena * p.ilosc, 0);}

// Wyświetlanie koszyka
function wyswietlKoszyk() {
const div = document.getElementById('koszyk');
if (koszyk.length === 0) {
div.innerHTML = 'Koszyk jest pusty';
return;}
let html = "";
koszyk.forEach(p => {
html += `<p>${p.nazwa} x ${p.ilosc} - ${p.cena * p.ilosc} zł 
<button onclick="usunZKoszyka(${p.id})">Usuń</button></p>`; });
html += `<p><strong>Łącznie: ${obliczSume()} zł</strong></p>`;
div.innerHTML = html;}

// Zatwierdzanie zamówienia
function zatwierdzZamowienie() {
if (koszyk.length === 0) {
alert("Koszyk jest pusty!");
return;}
let podsumowanie = "Twoje zamówienie:\n";
koszyk.forEach(p => {
podsumowanie += `${p.nazwa} x ${p.ilosc} - ${p.cena * p.ilosc} zł\n`; });
podsumowanie += `Łącznie: ${obliczSume()} zł`;
alert(podsumowanie);
koszyk = [];
wyswietlKoszyk();}
wyswietlKoszyk();
</script> 
</body>
</html>
