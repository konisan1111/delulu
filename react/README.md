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

# Frontend React Feladat:
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
Ez az első lehetőséged amivel importálhatod a JSON-t. Kicsit klasszikusabb, és bonyibb de nem sokkal.

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
Az AXIOS egy modernebb megoldás a JSON importálásra, de kb majdnem ugyan az mind a kettő.
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