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

# 📽️ Videók tanulásra:

Ofő megoldása a gyakorló feladatnak: https://www.youtube.com/watch?v=UGfHMuNLkAU

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

# 📚 Az én megoldásom a gyakorló feladatnak. Kommentes kód.
```
// Szia! ^^ Megmutatom neked, hogy hogyan kell értelmezni ezt a kódot!
// Először is, ne aggódj, van kód bőven meg komment, de egyáltalán nem olyan nehéz mint amilyennek kinéz.

// A Namespace-nek mindig egyeznie kell a fájlnévvel, vagy hibás lesz az egész!
using System.Text;

namespace Tour {

    // A Program class-ban futtatjuk le a feladokat.
    class Program {
        static void Main(string[] args) {
            // Mivel vannak ékezetek az applikációnkban, és alapból nem jelennek meg, megadjuk hogy UTF-8-as legyen az encoding.
            Console.OutputEncoding = Encoding.UTF8;

            // Csinálnunk kell egy listát a már létező adatmezőnk mintájára.
            List<Versenyzo> versenyzok = new List<Versenyzo>();

            // Készítsük el az adatok beolvására a foreach-et.
            // Kell egy string változó a soroknak, ez lesz a line, majd csak beolvassok a sorait a fájlnak. Ezeken megyünk végig.
            foreach (string line in File.ReadLines("tour.csv")) {
                // NAGYON FONTOS!!! --->>> A Debug mappába tegyétek a tour.csv fájlt, mert onnan tudja ilyen formában kiolvassni a Visual Studio.
                
                // Mivel a legelső sor a fejléc, az nekünk nyilván nem kell, így kihagyjuk.
                if (line.StartsWith("szakasz")) continue;
                // Most pedig, csináljuk egy listát a sorok feldarabolására.
                string[] parts = line.Split(";");
                versenyzok.Add(new Versenyzo(
                    // Mivel már a konstruktorban megadtuk hogy mik fognak kelleni, szépen a feldarabolt részeket a listából csak
                    // betesszük ide.
                    // Nagyon fontos! Ugye a legelső adat a szakasz, szóval azt itt is int-re kell alakítani!
                    int.Parse(parts[0]),
                    parts[1],
                    parts[2],
                    parts[3],
                    parts[4]
                ));
            }

            // FELADATOK --------------------------------->>>

            // 4. Feladat

            // Meg kell jelenítenünk hogy mennyi versenyző van az ötödik szakaszban.
            // A legjobb megoldás ha lambda kifejezéseket használunk a megoldásoknál.
            // Így néz ki: (x => x)
            // Itt megszámoljuk azokat az indexeket, tehát versenyzőket, akiknek az indexüknek a szakasza 5.
            int fifthRoundCount = versenyzok.Count(index => index.szakasz == 5);
            Console.WriteLine($"4. Feladat: 5-ös szakasz versenyzői: {fifthRoundCount} fő");

            // 5. Feladat

            // Ki kell számolnunk az átlagos időt (az összes versenyzőből), majd ki kell írni hogy hány fő volt felette az 5. szakaszban.
            // Először is kiválasztjuk azokat a versenyzőket akik az 5. szakaszban vannak.
            // Azért használunk var-t változónak, hogy a .NET eldöntse magának hogy milyen változó lesz belőle, tehát limbózik előtte.
            var fifthRoundComps = versenyzok.Where(index => index.szakasz == 5).ToList();
            // Számolunk egy átlag időt az összes versenyzőből.
            double averageTimeForAll = fifthRoundComps.Average(index => index.returnTime(index.ido));
            // Megszámoljuk azokat a versenyzőket akik az 5. szakaszban vannak és az átlag felett teljesítettek.
            int overAverageComps = fifthRoundComps.Count(index => index.returnTime(index.ido) > averageTimeForAll);
            Console.WriteLine($"5. Feladat: Átlag felett: {overAverageComps} fő");

            // 6. Feladat

            // Na ez egy picikét bonyi lesz, de ne aggódj, elmagyarázom mi micsoda.
            // Szóval, ismét egy var-t hozunk létre, hogy a .NET eldöntse milyen változó lesz belőle.
            // Elkezdjük lebontani, szűrni hogy mit is akarunk.
            // Először is, csoportba rendezzük a csapatokat a legelső Lambda kifejezéssel.
            var averageForTeams = versenyzok.GroupBy(index => index.csapat)
                                            // Utána kiválasztjuk az összes versenyzőt és számolunk nekik egy átlagot az idejükből.
                                            // Fontos, hogy én itt egy külön gyűjteményt csináltam, amiből lehívhatóak csapatok neve, és az átlagos idejük.
                                            .Select(selectIndex => new { nev = selectIndex.Key, atlag = selectIndex.Average(timeIndex => timeIndex.returnTime(timeIndex.ido)) })
                                            // Itt pedig csak névsorrendbe rendezzük az egészet.
                                            .OrderBy(x => x.nev);

            // Itt írjuk ki az átlagos időt csapatonként.
            Console.WriteLine("6. Feladat: Csapatonkénti átlagos idő:");
            foreach (var average in averageForTeams) {
                // Itt az average a csapat, majd annak lekérjük a nevét és az átlagát a már korábban létrehozott új gyűjteményből.
                Console.WriteLine($"{average.nev} : {average.atlag}");
            }

            // 7. Feladat
            // Itt csak lekérjük hogy az adott versenyző kapott-e külön díjat. Meg kell hívni a változónkat az idővel, és nemzetiséggel.
            Console.WriteLine($"7. feladat: Kitüntetett versenyzők: {versenyzok.Count(index => index.returnAward(index.nemzetiseg, index.ido))} ");

            // 8. Feladat
            // Csinálunk egy var-t és elrendezzük benne az idő alapján a leggyorsabbakat, majd ebből vesszük a legelső 10-et.
            var top10SelectedComp = fifthRoundComps.OrderBy(index => index.returnTime(index.ido)).Take(10);
            // Itt végigmegyünk a listán, és kiírjuk őket.
            foreach (var index in top10SelectedComp) {
                Console.WriteLine($"{index.nev}, {index.ido}");
            }
        }
    }

    // Ezt a class-t az adatmezőkre használjuk fel! (Propsokra, properties)
    class Versenyzo {

        // A .csv fájlunkban a legelső sorában van a fejléc, és ott megvan adva, hogy melyik adat micsoda.
        // A feladat azt mondja, hogy a változók ezeket a neveket vegyék fel.

        // Mivel a szakasz mindig egy szám lesz, ezért int-nek deklaráljuk.
        public int szakasz { get; set; }
        public string ido { get; set; }
        public string nev { get; set; }
        public string nemzetiseg { get; set; }
        public string csapat { get; set; }

        // Miután deklaráltál mindent is, jelöld ki az egészet, és csinálj egy konstruktort.
        public Versenyzo(int szakasz, string ido, string nev, string nemzetiseg, string csapat)
        {
            this.szakasz = szakasz;
            this.ido = ido;
            this.nev = nev;
            this.nemzetiseg = nemzetiseg;
            this.csapat = csapat;
        }
        // ^^^ Készíteni fogunk egy listát a beolvasott adatoknak, és ez szabja meg a formázását. ^^^

        // A feladat kéri, hogy csináljunk egy funckiót amivel a már megadott képlet alapján átszámoljuk az időt full másodpercbe.
        // Mivel a nyers idővel fogunk átalakítást végezni, igényelni kell a zárójelek között azt.
        public int returnTime(string time) {
            // Pofon egyszerű ez a rész; csinálunk egy parts listát, majd szépen beledaraboljuk az órát | percet | másodpercet.
            string[] parts = time.Split(":");
            // És most jöhet a képletünk ide! Mivel stringként dolgoztunk idáig, ezért int-re kell fordítani a már kész számokat!
            // Óra * 3600 + Perc * 60 + Másodperc
            return int.Parse(parts[0]) * 3600 + int.Parse(parts[1]) * 60 + int.Parse(parts[2]);
        }
        // Kell nekünk egy olyan boolean ami kidobja, hogy az illető Amerikai-e illetve hogy 3 óra alatt teljesített-e.
        public bool returnAward(string competitor, string time)
        {
            // Ezzel ellentétben az idő egy string lesz a formája miatt, ezt szépen splitelni kell.
            return (competitor == "USA" && returnTime(time) < 10800);
            // Arra figyeljetek hogy másodpercben számítunk mindent, ez a leggyorsabb, szóval használhatjuk a már meglévő funkciónkat.
            // Még valami, a három óra az ugye --->>> 60 * 60 * 3. Az ilyenekre kérlek nagyon de nagyon figyeljetek oda!
        }
    }

}
```
# ✂️ Komment nélküli változat. Shortcut
```
using System.Text;

namespace Tour {

    class Program {
        static void Main(string[] args) {
            Console.OutputEncoding = Encoding.UTF8;

            List<Versenyzo> versenyzok = new List<Versenyzo>();
            foreach (string line in File.ReadLines("tour.csv")) {                
                if (line.StartsWith("szakasz")) continue;
                string[] parts = line.Split(";");
                versenyzok.Add(new Versenyzo(

                    int.Parse(parts[0]),
                    parts[1],
                    parts[2],
                    parts[3],
                    parts[4]
                ));
            }

            int fifthRoundCount = versenyzok.Count(index => index.szakasz == 5);
            Console.WriteLine($"4. Feladat: 5-ös szakasz versenyzői: {fifthRoundCount} fő");

            var fifthRoundComps = versenyzok.Where(index => index.szakasz == 5).ToList();
            double averageTimeForAll = fifthRoundComps.Average(index => index.returnTime(index.ido));
            int overAverageComps = fifthRoundComps.Count(index => index.returnTime(index.ido) > averageTimeForAll);
            Console.WriteLine($"5. Feladat: Átlag felett: {overAverageComps} fő");

            var averageForTeams = versenyzok.GroupBy(index => index.csapat)
                                            .Select(selectIndex => new { nev = selectIndex.Key, atlag = selectIndex.Average(timeIndex => timeIndex.returnTime(timeIndex.ido)) })
                                            .OrderBy(x => x.nev);

            Console.WriteLine("6. Feladat: Csapatonkénti átlagos idő:");
            foreach (var average in averageForTeams) {
                Console.WriteLine($"{average.nev} : {average.atlag}");
            }

            Console.WriteLine($"7. feladat: Kitüntetett versenyzők: {versenyzok.Count(index => index.returnAward(index.nemzetiseg, index.ido))} ");

            var top10SelectedComp = fifthRoundComps.OrderBy(index => index.returnTime(index.ido)).Take(10);
            foreach (var index in top10SelectedComp) {
                Console.WriteLine($"{index.nev}, {index.ido}");
            }
        }
    }

    class Versenyzo {
        public int szakasz { get; set; }
        public string ido { get; set; }
        public string nev { get; set; }
        public string nemzetiseg { get; set; }
        public string csapat { get; set; }

        public Versenyzo(int szakasz, string ido, string nev, string nemzetiseg, string csapat)
        {
            this.szakasz = szakasz;
            this.ido = ido;
            this.nev = nev;
            this.nemzetiseg = nemzetiseg;
            this.csapat = csapat;
        }

        public int returnTime(string time) {
            string[] parts = time.Split(":");
            return int.Parse(parts[0]) * 3600 + int.Parse(parts[1]) * 60 + int.Parse(parts[2]);
        }
        public bool returnAward(string competitor, string time)
        {
            return (competitor == "USA" && returnTime(time) < 10800);
        }
    }

}
```
