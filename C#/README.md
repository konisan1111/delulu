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
C# Crash Course: https://www.youtube.com/watch?v=gfkTfcpWqAY

CSV beolvasás és feldolgozás: https://www.youtube.com/watch?v=W2Oj5OdWnBo

# 📚 Gyakorló feladatok:

Ofő feltett egy gyakorló feladatot ami hasonló lesz a vizsgán lévő feladathoz:

https://onedrive.live.com/?redeem=aHR0cHM6Ly8xZHJ2Lm1zL2YvYy8zZjI1ZTA3Y2ZjMDljODUyL0VpWUV5eE9NZkN0TXFmR192aVZzckpBQnRIT2hrUXotMmp1TWs0a0x6UF9MOHc%5FZT1NWVpLMjQ&id=3F25E07CFC09C852%21s769db521c82d49ecbc408767cb7f9934&cid=3F25E07CFC09C852&sb=name&sd=1

# 🤔 Hogyan kezdj el egy projektet?
Először is, legyen Visual Studio Community 2026-od. Már csak azért is mert szerintem sokkal tisztább lett a felület, és valamiért nem érződik annyira hulladéknak amilyen valójában az összes Visual Studio.

Ezt követően hozd létre a projektet így:
![GIF](https://i.ibb.co/jvL96405/2026-04-2617-35-22online-video-cutter-com-ezgif-com-crop-1.gif)

NE használj top-level statementet! Nem ajánlott, de ha annyira akarod, akkor go ahead 😶‍🌫️

# 🟣 C# Console Application Feladat:
Egy olyan console appot kell csinálnod ami beolvas egy CSV fájlt (Comma-Separated Value) és annak az adatait kezeled; műveleteket végzel el velük.
- 🔴 Projekt és Osztály létrehozása
> Egy új konzolos alkalmazás indítása, majd egy külön osztály (class) készítése az adatok tárolására publikus tulajdonságokkal.
- 🟠 Konstruktor
> Az osztályon belül egy olyan metódus írása, amely a beolvasott fájl egy sorát feldolgozza és értékül adja a tulajdonságoknak.
- 🟡 Fájlbeolvasás
> A megadott (gyakran CSV) forrásfájl megnyitása megfelelő kódolással, és a sorok betöltése egy listába vagy tömbbe.
- 🟢 Mértékegység-átváltás
> Gyakran kell egy plusz függvény az osztályba, ami például időt (óra:perc:másodperc) vált át összes másodpercre vagy távolságot számol át.
- 🔵 Statisztika és Szűrés
> Alapvető algoritmusok használata, mint például a megszámlálás (hány ilyen elem van?), az összegzés és átlagszámítás.
- 🟣 Keresés és Szélsőérték
> A legkisebb vagy legnagyobb érték (minimum/maximum) megkeresése, illetve az első olyan elem azonosítása, ami megfelel egy feltételnek.
- 🔴 Csoportosítás
> Az adatok rendszerezése valamilyen szempont (például csapat, város vagy kategória) szerint, és az ezekhez tartozó statisztikák kiírása.

### 🟡 Fájlbeolvasás
Na hát most erre van két megoldás legalább, de több is.

A tutorial videóban szépen manuálisan dolgozzuk fel az adatokat, viszont lehet egy nuGet packaget is használni hozzá.

#### Manuális megoldás: 
Hosszú és fárasztó, ez legyen neked a B terv.

```
using System;
using System.IO;

namespace CsvParserApp
{
    class Program
    {
        static void Main(string[] args)
        {
            string filePath = "adatok.csv";

            if (File.Exists(filePath))
            {
                string[] lines = File.ReadAllLines(filePath);

                foreach (string line in lines)
                {
                    string[] columns = line.Split(';');
                    
                    foreach (string col in columns)
                    {
                        Console.Write($"{col}\t");
                    }
                    Console.WriteLine();
                }
            }
            else
            {
                Console.WriteLine("A fájl nem található!");
            }
        }
    }
}
```

#### NuGet-es CsvHelper: 
Jóval rövidebb és, jah, szerintem te is látod.
```
using System;
using System.IO;

namespace CsvParserApp
{
    class Program
    {
        static void Main(string[] args)
        {
            string filePath = "adatok.csv";

            using (var reader = new StreamReader(filePath))
            {
                while (!reader.EndOfStream)
                {
                    string line = reader.ReadLine();
                    if (line != null)
                    {
                        string[] values = line.Split(';');
                        Console.WriteLine(string.Join(" | ", values));
                    }
                }
            }
        }
    }
}
```

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
C# Crash Course: https://www.youtube.com/watch?v=gfkTfcpWqAY

CSV beolvasás és feldolgozás: https://www.youtube.com/watch?v=W2Oj5OdWnBo

# 📚 Gyakorló feladatok:

Ofő feltett egy gyakorló feladatot ami hasonló lesz a vizsgán lévő feladathoz:

https://onedrive.live.com/?redeem=aHR0cHM6Ly8xZHJ2Lm1zL2YvYy8zZjI1ZTA3Y2ZjMDljODUyL0VpWUV5eE9NZkN0TXFmR192aVZzckpBQnRIT2hrUXotMmp1TWs0a0x6UF9MOHc%5FZT1NWVpLMjQ&id=3F25E07CFC09C852%21s769db521c82d49ecbc408767cb7f9934&cid=3F25E07CFC09C852&sb=name&sd=1

# 🤔 Hogyan kezdj el egy projektet?
Először is, legyen Visual Studio Community 2026-od. Már csak azért is mert szerintem sokkal tisztább lett a felület, és valamiért nem érződik annyira hulladéknak amilyen valójában az összes Visual Studio.

Ezt követően hozd létre a projektet így:
![GIF](https://i.ibb.co/jvL96405/2026-04-2617-35-22online-video-cutter-com-ezgif-com-crop-1.gif)

NE használj top-level statementet! Nem ajánlott, de ha annyira akarod, akkor go ahead 😶‍🌫️

# 🟣 C# Console Application Feladat:
Egy olyan console appot kell csinálnod ami beolvas egy CSV fájlt (Comma-Separated Value) és annak az adatait kezeled; műveleteket végzel el velük.
- 🔴 Projekt és Osztály létrehozása
> Egy új konzolos alkalmazás indítása, majd egy külön osztály (class) készítése az adatok tárolására publikus tulajdonságokkal.
- 🟠 Konstruktor
> Az osztályon belül egy olyan metódus írása, amely a beolvasott fájl egy sorát feldolgozza és értékül adja a tulajdonságoknak.
- 🟡 Fájlbeolvasás
> A megadott (gyakran CSV) forrásfájl megnyitása megfelelő kódolással, és a sorok betöltése egy listába vagy tömbbe.
- 🟢 Mértékegység-átváltás
> Gyakran kell egy plusz függvény az osztályba, ami például időt (óra:perc:másodperc) vált át összes másodpercre vagy távolságot számol át.
- 🔵 Statisztika és Szűrés
> Alapvető algoritmusok használata, mint például a megszámlálás (hány ilyen elem van?), az összegzés és átlagszámítás.
- 🟣 Keresés és Szélsőérték
> A legkisebb vagy legnagyobb érték (minimum/maximum) megkeresése, illetve az első olyan elem azonosítása, ami megfelel egy feltételnek.
- 🔴 Csoportosítás
> Az adatok rendszerezése valamilyen szempont (például csapat, város vagy kategória) szerint, és az ezekhez tartozó statisztikák kiírása.

### 🟡 Fájlbeolvasás
Na hát most erre van két megoldás legalább, de több is.

A tutorial videóban szépen manuálisan dolgozzuk fel az adatokat, viszont lehet egy nuGet packaget is használni hozzá.

#### Manuális megoldás: 
Hosszú és fárasztó, ez legyen neked a B terv.

```
using System;
using System.IO;

namespace CsvParserApp
{
    class Program
    {
        static void Main(string[] args)
        {
            string filePath = "adatok.csv";

            if (File.Exists(filePath))
            {
                string[] lines = File.ReadAllLines(filePath);

                foreach (string line in lines)
                {
                    string[] columns = line.Split(';');
                    
                    foreach (string col in columns)
                    {
                        Console.Write($"{col}\t");
                    }
                    Console.WriteLine();
                }
            }
            else
            {
                Console.WriteLine("A fájl nem található!");
            }
        }
    }
}
```

#### NuGet-es CsvHelper: 
Jóval rövidebb és, jah, szerintem te is látod.
```
using System;
using System.IO;

namespace CsvParserApp
{
    class Program
    {
        static void Main(string[] args)
        {
            string filePath = "adatok.csv";

            using (var reader = new StreamReader(filePath))
            {
                while (!reader.EndOfStream)
                {
                    string line = reader.ReadLine();
                    if (line != null)
                    {
                        string[] values = line.Split(';');
                        Console.WriteLine(string.Join(" | ", values));
                    }
                }
            }
        }
    }
}
```