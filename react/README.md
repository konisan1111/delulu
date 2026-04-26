<div align="center">
  <img src="https://i.ibb.co/S4QYX9Ck/delulu-logo.png" alt="Delulu Logo" width="500"/>
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
  </p>
</div>

# 📽️ Videók tanulásra:
Kérlek, legalább nézzetek bele néhányba, mert nagyon sok infót elmondanak bennük, és hasznosak lesznek a vizsgán!
(a CSS Flexboxot, TypeScriptet, ES6-ot mindenképpen nézzétek meg!!!)

CSS Flexbox Course: https://www.youtube.com/watch?v=wsTv9y931o8

JavaScript Crash Course: https://www.youtube.com/watch?v=W6NZfCO5SIk

ES6-os szabvány (ez igen csak kell typescripthez): https://www.youtube.com/watch?v=WZQc7RUAg18

React with Typescript: https://www.youtube.com/watch?v=TPACABQTHvM

TypeScript Crash Course: https://www.youtube.com/watch?v=ZvZ7gvcmPmI

Axios: https://www.youtube.com/watch?v=12l6lkW6JhE

Fetch API: https://www.youtube.com/watch?v=zR5FoKMAJp4

# 📚 Gyakorló feladatok:

Desserts - JSON importálás, és komponensek mapelésére jó feladat!

https://www.frontendmentor.io/challenges/product-list-with-cart-5MmqLVAp_d

Pokedex Template - Gyakorlati vizsga feladat. EZT NAGYON NÉZZÉTEK ÁT! Konkrétan ugyan ez!!!

https://github.com/Mechwart-NT/pokedex-template

# 🧪 Táblázat még év elejéről:
![Táblázat Képe](https://i.ibb.co/Wv0f0V40/image.png)

# 🤔 Hogyan kezdj el egy projektet?
Remélem számodra már egyértelmű az hogy Node.js-t használtunk végig.

Ha szeretnél egy projektet létrehozni, akkor a következőt írd be: `npm create vite@latest`
> Szükséges a vite package, viszont ha ez nem volt telepítve akkor alapból megkérdezi, hogy telepítse-e ami nekünk nyilván kell.

Az `npm` a Node Package Manager.

Válaszd ki, hogy `React`-ot használsz, illetve `TypeScript`-et kódoláshoz.

Miután készen vagy, futtasd élőben a projektet az `npm run dev` parancs használatával!


# 💻 Frontend React Feladat:
Reactban egy Frontend feladatot kell megoldanod, egy megkezdett projektben. Az alábbiakat kell elvégezned:

- 🔴 (4 pont) Importálj az asp.NET feladatban létrehozott backend endpointon egy json objektumot Fetchel, vagy Axios-al.
- 🟡 (2 pont) Custom hook, és state kezelés.
- 🔵 (9 pont) Hozz létre egy komponenst egyedül, és adj csillagos értékelést.
- 🟢 (? pont) Flexbox CSS elrendezés, és grid.

**Nagyon fontos, a backendnek nem muszáj jól működnie!**

Összesen **3 biztosítás** van a feladatban! Amennyiben nem megy az asp.NET backend, nincsen baj, mert van egy JSON fájl ugyan azokkal az adatokkal amit nem az endpointról kell megkapnod, csak simán behívod a React projektedben! 

Ha valamiért ez sem menne, vagy egy egész dummy JSON block eleve a kódban. 

Ami még szintén fontos, az az, hogy: az asp.NET feladatában nem neked kell megcsinálnod azt az endpointot amin a JSON érkezik a React-ba, tehát teljesen hülye biztos. Az már eleve benne lesz.

### 🔴 (FETCH API) JSON importálás és olvasás.
Használhatsz FETCH API-t, ami egy régebbi megoldás, és nem manuális. Nem támogatott annyira széles körben.
```

import React, { useState, useEffect } from 'react';

const DataFetcher = () => {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetch('IDE JÖN AZ ENDPOINT!!!')
      .then((response) => response.json())
      .then((json) => setData(json));
  }, []);

  return (
    <div>
      <ul>
        {data.slice(0, 5).map((item) => (
          <li key={item.id}>{item.title}</li>
        ))}
      </ul>
    </div>
  );
};

export default DataFetcher;
```

### 🔴 (AXIOS) JSON importálás és olvasás.
Ha automatizált beolvasást akarsz akkor telepítsd az AXIOS-t. A FETCH-el ellentétben, ezt egy `npm package`-ként kell telepítened. Nagyobb a támogatottsága.

Így telepítsd fel a projektbe: `npm install axios`
```
import React, { useState, useEffect } from 'react';
import axios from 'axios';

const DataFetcher = () => {
  const [data, setData] = useState([]);

  useEffect(() => {
    axios.get('IDE JÖN AZ ENDPOINT!!!')
      .then((response) => {
        setData(response.data);
      })
      .catch((error) => {
        console.error('Hiba történt:', error);
      });
  }, []);

  return (
    <div>
      <ul>
        {data.slice(0, 5).map((item) => (
          <li key={item.id}>{item.title}</li>
        ))}
      </ul>
    </div>
  );
};

export default DataFetcher;
```