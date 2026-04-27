<div align="center">
  <img src="https://i.ibb.co/8gVnLPFz/output-onlinegiftools.gif" alt="Delulu Logo" width="500"/>
  <p>
    <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" />
    <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white" />
    <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" />
    <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" />
    <br>
    <img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" />
    <img src="https://img.shields.io/badge/WPF-512BD4?style=for-the-badge&logo=dotnet&logoColor=white" />
    <img src="https://img.shields.io/badge/C%23_Console-239120?style=for-the-badge&logo=c-sharp&logoColor=white" />
    <img src="https://img.shields.io/badge/asp.NET-512BD4?style=for-the-badge&logo=dotnet&logoColor=white" />
    <br>
    <img src="https://komarev.com/ghpvc/?username=konisan1111&repo=delulu&style=for-the-badge&color=blue" />
    <img src="https://img.shields.io/github/stars/konisan1111/delulu?style=for-the-badge&color=gold" />
  </p>
</div>

### 🌐 Weboldalak

https://stackoverflow.com/questions

https://www.w3schools.com/

https://www.w3schools.com/js/

https://www.w3schools.com/css/css3_flexbox.asp

https://www.w3schools.com/REACT/default.asp

### 🎥 Videók

CSS Flexbox Course: https://www.youtube.com/watch?v=wsTv9y931o8

JavaScript Crash Course: https://www.youtube.com/watch?v=W6NZfCO5SIk

ES6-os szabvány (ez igen csak kell typescripthez): https://www.youtube.com/watch?v=WZQc7RUAg18

React with Typescript: https://www.youtube.com/watch?v=TPACABQTHvM

TypeScript Crash Course: https://www.youtube.com/watch?v=ZvZ7gvcmPmI

Axios: https://www.youtube.com/watch?v=12l6lkW6JhE

Fetch API: https://www.youtube.com/watch?v=zR5FoKMAJp4

Ofő megoldása a gyakorló feladatnak: https://www.youtube.com/watch?v=UGfHMuNLkAU

C# Crash Course: https://www.youtube.com/watch?v=gfkTfcpWqAY

CSV beolvasás és feldolgozás: https://www.youtube.com/watch?v=W2Oj5OdWnBo

# 🔵 Mi az a React?

A React (vagy React.js) egy nyílt forráskódú, JavaScript-alapú programozási könyvtár, amelyet elsősorban felhasználói felületek (UI) építésére használnak. A Meta (korábban Facebook) fejlesztette ki, és mára az egyik legnépszerűbb eszközzé vált a modern webfejlesztésben.

Íme a legfontosabb jellemzői közérthetően:

- Komponens-alapú felépítés
A React lényege, hogy a weboldalt nem egyetlen óriási fájlként kezeli, hanem apró, újrafelhasználható egységekre, úgynevezett komponensekre bontja. Például egy gomb, egy keresősáv vagy egy profilkártya mind különálló komponens lehet, amelyeket aztán legószerűen összeillesztve épül fel a teljes alkalmazás.

- Deklaratív szemlélet
A Reactnél nem azt kell megmondanod a böngészőnek lépésről lépésre, hogyan változtassa meg az oldalt (imperatív mód), hanem azt írod le, hogyan kellene kinéznie a felületnek egy adott állapotban. Ha az adatok megváltoznak, a React automatikusan frissíti a felületet.

- Virtual DOM (Virtuális DOM)
A weboldalak frissítése hagyományosan lassú folyamat. A React ezt egy "Virtuális DOM" használatával gyorsítja fel:

  - Készít egy másolatot az oldal szerkezetéről a memóriában.

  - Amikor változás történik, először ezen a másolaton végzi el a módosítást.

  - Kiszámolja a leggyorsabb utat a változtatások átvezetéséhez, és csak azt a részt frissíti a valódi böngészőben, ami ténylegesen megváltozott.

- Egyirányú adatfolyam
Az adatok fentről lefelé (a szülő komponenstől a gyerek felé) áramlanak. Ez átláthatóbbá és könnyebben tesztelhetővé teszi a kódot, mivel pontosan tudni lehet, mi honnan érkezik.

- Hol használják?
Bár eredetileg webes felületekre készült, a React Native segítségével ma már mobilalkalmazások (iOS, Android) fejlesztésére is használják ugyanazt a logikát. Olyan óriások használják, mint a Facebook, az Instagram, a Netflix, az Airbnb vagy az Uber.

# 🟣 Mi az a C# Console Application?
A C# Console Application egy olyan számítógépes program, amely egy szöveges felületen (úgynevezett konzolon vagy terminálon) fut. Nem rendelkezik grafikus ablakokkal, gombokkal vagy egérrel kattintható elemekkel; a kommunikáció tisztán szöveges formában történik.

Íme a legfontosabb jellemzői:

- Hogyan működik?
A program és a felhasználó közötti interakció két fő csatornán zajlik:

Bemenet (Input): A felhasználó gépel valamit a billentyűzeten, majd leüti az Entert.

Kimenet (Output): A program szöveges üzeneteket ír ki a képernyőre.

- Mire használják?
Bár a mai világban a legtöbb felhasználó a grafikus (GUI) vagy webes felületeket szokta meg, a konzolos alkalmazások még mindig rendkívül fontosak:

  - Tanulás: A kezdő programozók itt sajátítják el a nyelv alapjait (változók, ciklusok, feltételek), mert nem vonja el a figyelmet a bonyolult ablakkezelés.

  - Rendszereszközök: Automatizálási szkriptek, adatfeldolgozó szoftverek és szerveroldali alkalmazások gyakran így futnak.

  - Backend fejlesztés: Sok komplex rendszer "motorja" valójában egy konzolos környezetben futó kód.

- Egy egyszerű példa

```
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Szia! Hogy hívnak?");
        string nev = Console.ReadLine(); // Beolvassa a nevet
        Console.WriteLine("Üdvözöllek, " + nev + "!");
    }
}
```

- Hol futtatható?
A modern .NET keretrendszernek köszönhetően a C# konzolos alkalmazások platformfüggetlenek. Ez azt jelenti, hogy ugyanaz a kód elfut:

  - Windows-on (Command Prompt vagy PowerShell)

  - Linux-on (Bash/Terminal)

  - macOS-en

# 🟣 Mi az a WPF Application?
A WPF (Windows Presentation Foundation) a Microsoft egyik grafikus alrendszere asztali alkalmazások fejlesztéséhez, amely a .NET keretrendszer része.

Tömören az alábbi pontokban foglalható össze a lényege:

- A felület és a logika szétválasztása
A WPF egyik legnagyobb újítása a XAML (egy XML-alapú nyelv) használata. Ez lehetővé teszi, hogy a felhasználói felületet (UI) külön fájlban tervezzük meg, míg a működtető logika (C# vagy VB.NET) egy másik fájlba kerül. Ez megkönnyíti a fejlesztők és a grafikusok közös munkáját.

- Hardveres gyorsítás
A korábbi technológiákkal (pl. Windows Forms) ellentétben a WPF a DirectX-re épül. Ez azt jelenti, hogy a grafika megjelenítéséhez a videókártyát (GPU) használja a processzor helyett, így sokkal simább animációkat és komplexebb látványvilágot tesz lehetővé.

- Vektoros megjelenítés
A WPF nem pixelekkel, hanem vektorokkal dolgozik. Ennek köszönhetően az alkalmazások tetszőlegesen átméretezhetők minőségromlás nélkül, és kiválóan alkalmazkodnak a különböző felbontású monitorokhoz (High DPI támogatás).

- Adatkötés (Data Binding)
Ez a WPF "szuperereje". Lehetővé teszi, hogy az adatok (pl. egy adatbázis tartalma) és a megjelenítő elemek (pl. egy szövegmező) között élő kapcsolat legyen. Ha az adat változik, a felület automatikusan frissül, és fordítva. Erre épül a népszerű MVVM (Model-View-ViewModel) tervezési minta is.

- Rugalmas testreszabhatóság
Minden vezérlő (gombok, listák stb.) teljesen átalakítható. Egy gomb belsejébe akár videót, képet vagy bonyolult alakzatokat is tehetsz anélkül, hogy az alapvető viselkedése megváltozna.

# 🟪 Mi az a Web API?


A Web API a Visual Studio környezetben (elsősorban az ASP.NET Core keretrendszeren belül) egy olyan technológia, amellyel HTTP-alapú szolgáltatásokat építhetsz.

Míg egy hagyományos weboldal HTML-t küld a böngészőnek, a Web API jellemzően adatokat (leggyakrabban JSON formátumban) szolgáltat más alkalmazások számára.

Tömören a lényeg:

- Mire jó?
Ez a „híd” a szerver és a kliensek között. Egyetlen Web API-t kiszolgálhat:

  - Egy mobilalkalmazást (iOS/Android).

  - Egy modern webes frontendet (React, Angular, Vue).

  - Más szervereket vagy asztali alkalmazásokat.

- Hogyan működik? (REST elv)
A Web API a szabványos HTTP metódusokat használja a műveletekhez:

`GET`: Adatok lekérése (pl. terméklista).

`POST`: Új adat létrehozása (pl. regisztráció).

`PUT`: Meglévő adat módosítása.

`DELETE`: Adat törlése.

- Főbb jellemzői Visual Studio-ban
  - Kontrollerek (Controllers): Olyan osztályok, amelyek kezelik a beérkező kéréseket és válaszolnak rájuk.

  - Routing: Meghatározza, hogy melyik URL (pl. /api/users/5) melyik kódrészletet futtassa le.

  - JSON sorosítás: A C# objektumaidat a keretrendszer automatikusan olvasható JSON szöveggé alakítja, és fordítva.

  - Swagger/OpenAPI: A Visual Studio alapból tartalmazza ezt az eszközt, ami egy automatikus dokumentációt és tesztfelületet generál az API-dhoz, így böngészőből is kipróbálhatod a végpontokat.

- Hol találod?
Amikor új projektet indítasz Visual Studio-ban, az "ASP.NET Core Web API" sablont kell választanod. Ez előkészíti neked a szükséges könyvtárakat és egy példa kontrollert (gyakran egy időjárás-előrejelzőt), hogy azonnal el tudd kezdeni a fejlesztést.

# 🟨 Az ECMAScript (ES): 
Az ECMAScript (gyakran csak ES) nem egy konkrét programozási nyelv, hanem egy szabvány, amely meghatározza, hogyan kell működnie a parancsfájlnyelveknek (scripting languages).

Gondolj rá úgy, mint egy receptkönyvre vagy egy tervrajzra: a szabvány leírja a szabályokat, a programozási nyelvek pedig megvalósítják azokat.

- Kapcsolata a JavaScripttel
A legfontosabb tudnivaló: a JavaScript az ECMAScript legnépszerűbb megvalósítása.

Az ECMAScript a specifikáció (a papír, amire leírták a szabályokat).

> A JavaScript a nyelv, amit ténylegesen használsz a böngészőben vagy Node.js alatt.

- Miért volt rá szükség?
A 90-es években a böngészőháborúk idején a Netscape (JavaScript) és a Microsoft (JScript) saját verziókat készített. Hogy a weboldalak mindenhol ugyanúgy fussanak, szükség volt egy központi szabványra. Ezt a feladatot az Ecma International nevű szervezet vállalta el – innen az elnevezés.

- Verziók, amikkel találkozni fogsz
A szabványt folyamatosan frissítik. A legfontosabb mérföldkövek:

ES5 (2009): A "régi" JavaScript, amit minden böngésző alapból értett.

ES6 / ES2015: Ez volt a legnagyobb robbanás. Rengeteg modern funkciót hozott (pl. let, const, nyíl függvények, osztályok). Azóta évente adnak ki kisebb frissítéseket (ES2016, ES2017 stb.).

- Miért fontos ez fejlesztőként?
Amikor azt hallod, hogy egy funkció "ES6-os", az azt jelenti, hogy az egy modernebb megoldás. Mivel a régebbi böngészők (mint az Internet Explorer) nem ismerik az újabb ECMAScript szabványokat, a fejlesztők gyakran használnak olyan eszközöket (pl. Babel), amik az új kódot visszaalakítják régebbi, "emészthetőbb" szabványra.