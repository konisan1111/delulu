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
Így néz ki a klasszikus "Helló Világ!" program C# nyelven:

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