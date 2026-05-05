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

# 📽️ Videó tanulásra:
Nagyon őszinte leszek veletek, a WPF egy hulladék, és alig van valami uptodate tutorial róla. Miután kisétáltatok a vizsgáról, nyugodtan felejtsétek el ezt az egészet, minél gyorsabban.

WPF XAML Tutorial: https://www.youtube.com/watch?v=Z0a0QYNlKig

## 🟪 WPF Application Feladat

Ebben a feladatban be kell olvasni egy .sql fájlt a projektbe, annak az adatait be kell listázni, majd meg kell jeleníteni DataGridben, és ListBoxban, illetve egy pop-up ablakban.

- Projekt létrehozása:
  > Az alkalmazás alapstruktúrája megfelelően el lett készítve.

- Adatmodell kezelése:
  > Az adatok szerkezetét leíró osztályfájl (Entity/Model) helyesen szerepel a projektben.

- Megjelenítő vezérlő:
  > A táblázatos adatmegjelenítő (DataGrid) szakszerűen el lett helyezve a felhasználói felületen.

- Adatbetöltés:
  > Az alkalmazás indulásakor vagy esemény hatására az adatok sikeresen betöltődnek a táblázatba.

- Részletek megjelenítése:
  > Rendelkezésre áll egy szöveges mező (Label vagy TextBlock) az adatok részletezéséhez.

- Eseményvezérelt tartalom:
  > A táblázat egy elemének kiválasztásakor a kapcsolódó információk automatikusan megjelennek a kijelzőn.

- Funkcionális vezérlők:
  > A kért műveletekhez (pl. szűrés, exportálás) tartozó gomb és listás megjelenítő (ListBox) létezik.

- Logikai feldolgozás:
  > A gombra kattintva a program elvégzi a számításokat vagy műveleteket, és az eredményt a listába írja.

- Specifikus lekérdezés:
  > Egy dedikált gomb szolgál a meghatározott feltétel szerinti (pl. statisztikai) adatlekérés indítására.

- Eredmény közlése:
  > A számított érték vagy a szűrt darabszám helyesen megjelenik a felhasználó számára a kattintás után.

# 📚 Gyakorló feladat:

Ofő erre is csinált egy feladatot, ennek a megoldás is itt lesz a repo-ban, lentebb.

https://onedrive.live.com/?redeem=aHR0cHM6Ly8xZHJ2Lm1zL2YvYy8zZjI1ZTA3Y2ZjMDljODUyL0VpWUV5eE9NZkN0TXFmR192aVZzckpBQnRIT2hrUXotMmp1TWs0a0x6UF9MOHc_ZT1NWVpLMjQ&id=3F25E07CFC09C852!s769db521c82d49ecbc408767cb7f9934&cid=3F25E07CFC09C852&sb=name&sd=1

# 🤔 Hogyan kezdj el egy projektet?
Ugyan úgy kell mint egy C# Console Appot, viszont itt a WPF-et választjuk ki. Semmi más belállítás nem szükséges utána. 

![Image](https://i.ibb.co/HfNjNpvn/image.png)

# ✅ A megoldás felépítése:

Mivel egy katasztrófa a WPF, még magamnak is vezetni kell hogy milyen lépésekben kell megoldanom.

És igen, minden második mondatban szidni fogom XDDD

Szerencsére van egy `Dapper` nevű package amivel nagyon szépen le lehetett faragni a 82 soros kódból, így már csak 42. Végig megyek az egészen mi micsoda, és miért van.

### 📌 Az összes usage telepítése:

Azért hogy ne legyen egy spagetti az egész, importálni kell a `Dapper`-t.
`using Dapper;`

SQLitehoz pedig `using System.Data.SQLite;` kell használni.

Mivel nincsenek alapból telepítve ezek a nuGet Packagek, jobb kattintás után feldobja lehetőségnek a VS, hogy telepítsd őket. 

### 📌 SQLite adatbázis létrehozása:
Nos a feladatban kapni fogunk egy .sql fájlt, de ezt szerencsésebb, sőt a feladatban egy leírás el is mondja, hogy át kell alakítanunk .db-re.

A .sql fájl olyan mint egy recept. 
Nyisd meg, vagy töltsd le a DB Browser-t SQLite-hoz először is.

https://sqlitebrowser.org/dl/

Majd ezt követően nyisd meg és importáld be a .sql fájlt.
Utána `File > Save Database as...` és .db fájlként mentsd el a `\Debug\.NET Verzió\` könyvtárba a projekteden belül, így látni fogja a kódod.

### 📌 Rekordok olvasása az adatbázisból:
Az első legfontosabb dolog, hogy csinálni kell egy listát az olvasott adatoknak, illetve egy connection stringet az adatbázishoz.

```
List<Versenyzo> versenyzok = new List<Versenyzo>();
string connectionString = "Data Source=tour.db;Version=3;";
```

Itt a 'versenyzok' lista a már megadott `Versenyzo.cs` fájlban megadott adatmező alapján készül.

Nagyon fontos, hogy ha még nem tetted be a fájlok közé, akkor a Solution Explorerben nyomj egy jobb clicket, és `Add > Existing Item`. Válaszd ki a .cs fájlt, és már bent is van!


Szupi! Most jöhet a lényeg;

```
void AdatokBetoltese() {
    using var conn = new SQLiteConnection(connectionString);
    versenyzok = conn.Query<Versenyzo>(
        "SELECT v.id, v.nev, v.nemzetiseg, c.csapatNev FROM versenyzo v JOIN csapat c ON v.csapatId = c.id"
    ).ToList();
}
```

Ez a void felel azért hogy az adatok be legyenek töltve. Ha kérdezed mi az a void; ezek kód blokkok amelyek nem returnölnek semmit sem, vagy bármilyen értéket, csak lefuttatja azt a kódot amit beleírsz.

```
void AdatokBetoltese() {}
```

A conn változó maga a kapcsolódási string lesz, ez kell ahhoz hogy tudja a program, milyen fájlal kell kommunikálni.

```
using var conn = new SQLiteConnection(connectionString);
```

Végül jön az utolsó sorunk. A versenyzok Listát már definiáltuk, viszont most belerakjuk az értékeket is. A `conn.Query<Versenyzo>().toList();`-ben a conn mint mutattam a connection string, viszont a Query a legfontosabb része. Automatikusan, helyettünk mappeli az adatokat és propertyket készít. Nagyon egyszerűen, mindent elvégez helyetted hogy a `<Versenyzo>` adatmező alapján a Listába legyenek rendezve a dolgok.

Viszont az nem mindegy hogy milyen adatok, így a zárójelek közé be kell tenni azt az SQL parancsot amivel az összes szükséges rekordod kitudjuk venni
`SELECT v.id, v.nev, v.nemzetiseg, c.csapatNev FROM versenyzo v JOIN csapat c ON v.csapatId = c.id`

A v és a c csak rövidítések. Megmondjuk hogy `SELECT` azaz válasszuk ki a `v` tehát versenyzo táblából az id-t, nevet, nemzetiséget, és csapat nevet. A `FROM` mondja meg a sql parancsnak hogy a versenyzo az `v`. Még hozzácsatoljuk a csapatokat, és készen is vagyunk.

Csináltam egy ábrát arra hogy értelmezhetőbb legyen az SQL parancs.

![Ábra](https://i.ibb.co/MmbDP5B/sql-abra.png)

```
versenyzok = conn.Query<Versenyzo>(
        "SELECT v.id, v.nev, v.nemzetiseg, c.csapatNev FROM versenyzo v JOIN csapat c ON v.csapatId = c.id"
    ).ToList();
```

Végül csak listává kell alakítani az egészet a `.toList()`-el.

### 📌 Az 5. szakasz ideje, kijelölés után:

![Ábra](https://i.ibb.co/vCR729fz/selection-Changed.png)

A `void selectionChanged` sorral kezdődik minden, ami egy eseménykezelő. Ez akkor fut le, amikor a táblázatban (vagyis a DataGridben) a felhasználó rákattint egy sorra, vagyis megváltozik a kijelölés.

A következő rész az `if (compDisplay.SelectedItem is Versenyzo v)`. 
Itt a program megnézi, hogy amit éppen kije löltek a felületen, az tényleg egy Versenyzo típusú objektum-e. Ha igen, akkor elnevezi v-nek, így a kapun belül már tudunk hivatkozni az adataira, például a `v.Id`-ra, ami az adatbázisbeli azonosítója.

A `using var conn` sor létrehozza a kapcsolatot az adatbázissal. A using azért jó, mert amint lefut a kódblokk, automatikusan lezárja a kapcsolatot, így nem marad nyitva feleslegesen az adatbázis fájl.

A `var ido = conn.ExecuteScalar(...)` a Dapper része. Az ExecuteScalar akkor kell, ha pontosan egyetlen értéket várunk vissza az adatbázisból, nálunk ez a versenyző időeredménye. 

A string jelzi, hogy szövegként kérjük vissza az adatot.  A SQL parancsban a `WHERE versenyzoId = @Id` résznél a `@Id` egy biztonsági helyörző. A Dapper a parancs végén lévő new `{ v.Id }` részből veszi ki az adatot, és biztonságosan behelyettesíti a `@Id` helyére.
Ezzel véded a programodat a hibáktól.

Végül a `resultsText.Text` sor frissíti a felületet. A dollár jeles megoldással beillesztjük a szövegbe az eredményt. A két kérdőjel `(??)` pedig egy rövidítés: azt jelenti, hogy ha az adatbázis nem adott vissza semmit (null lett az érték), akkor írja ki helyette azt, hogy Nincs adat. Csak hogy hülye biztos legyen.

```
void selectionChanged(object sender, SelectionChangedEventArgs e) {
    if (compDisplay.SelectedItem is Versenyzo v){
        using var conn = new SQLiteConnection(connectionString);
        var ido = conn.ExecuteScalar<string>("SELECT ido FROM eredmeny WHERE versenyzoId = @Id AND szakasz = 5", new { v.Id });
        resultsText.Text = $"5. szakasz eredménye: {ido ?? "Nincs adat"}";
    }
}
```

### 📌 A Két gomb kezelése:
Végül van két gombunk amelyek megmutatják a versenyzők számát, és a Magyar versenyzők számát is. A C# Console App-os megoldásomat is megnézheted, mert ugyan ilyen Lambda kifejezéseket használtam a megoldáshoz, így magától értetődő hogy mi mit csinál itt.

```
void compsCount(object sender, RoutedEventArgs e) {
    teamList.ItemsSource = versenyzok.GroupBy(v => v.CsapatNev)
                                     .Select(g => $"{g.Key}: {g.Count()}");
}

void hunCompsCount(object sender, RoutedEventArgs e) {
    MessageBox.Show($"Magyar versenyzők száma: {versenyzok.Count(v => v.Nemzetiseg == "HUN")}");
}
```

### 📌 A void-ok futtatása:
Hogy minden lefusson, el kell indítani azokat a voidokat amelyek pl. az adatokat olvassák be.

```
public MainWindow() {
    InitializeComponent();
    AdatokBetoltese();
    compDisplay.ItemsSource = versenyzok;
    compDisplay.SelectedIndex = 0;
}
```

Készen is vagyunk. Ezt követően a WPF Appunk készen is van!
(ami egy katasztrófa 😭👉👈, de amúgy fr, lowkey nem találtam olyan tutorialt ami nem 5 évvel ezelőtti lett volna, senki sem használja már ezt xddd. Magyar oktatás khm.)


# 💻 Megoldások a gyakorló feladathoz:
Két fájlt kell írni a feladat során, magát a kódot, és az xaml fájlt. Egyik a program, másik a UI.

### 🟪 MainWindow.xaml.cs
```
using System.Windows;
using System.Windows.Controls;
using System.Data.SQLite;
using Dapper;

namespace TourGUI {
    public partial class MainWindow : Window {
        List<Versenyzo> versenyzok = new List<Versenyzo>();
        string connectionString = "Data Source=tour.sql;Version=3;";

        public MainWindow() {
            InitializeComponent();
            AdatokBetoltese();
            compDisplay.ItemsSource = versenyzok;
            compDisplay.SelectedIndex = 0;
        }

        void AdatokBetoltese() {
            using var conn = new SQLiteConnection(connectionString);
            versenyzok = conn.Query<Versenyzo>(
                "SELECT v.id, v.nev, v.nemzetiseg, c.csapatNev FROM versenyzo v JOIN csapat c ON v.csapatId = c.id"
            ).ToList();
        }

        void selectionChanged(object sender, SelectionChangedEventArgs e) {
            if (compDisplay.SelectedItem is Versenyzo v){
                using var conn = new SQLiteConnection(connectionString);
                var ido = conn.ExecuteScalar<string>("SELECT ido FROM eredmeny WHERE versenyzoId = @Id AND szakasz = 5", new { v.Id });
                resultsText.Text = $"5. szakasz eredménye: {ido ?? "Nincs adat"}";
            }
        }

        void compsCount(object sender, RoutedEventArgs e) {
            teamList.ItemsSource = versenyzok.GroupBy(v => v.CsapatNev)
                                             .Select(g => $"{g.Key}: {g.Count()}");
        }

        void hunCompsCount(object sender, RoutedEventArgs e) {
            MessageBox.Show($"Magyar versenyzők száma: {versenyzok.Count(v => v.Nemzetiseg == "HUN")}");
        }
    }
}
```

### 🔵 MainWindow.xaml:
```
<Window x:Class="TourGUI.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:TourGUI"
        mc:Ignorable="d"
        Title="MainWindow"
        Height="450" 
        Width="800"
        >

    <Grid>

        <Grid.ColumnDefinitions>

            <ColumnDefinition 
                Width="*"
                />

            <ColumnDefinition 
                Width="300"
                />

        </Grid.ColumnDefinitions>

        <DataGrid 
            Grid.Column="0"
            Name="compDisplay"
            SelectionMode="Single"
            SelectionChanged="selectionChanged"
            AutoGenerateColumns="True"
            />

        <StackPanel
            Grid.Column="1"
            >
            <TextBlock
                Name="resultsText"
                Text="5. szakasz eredménye:"
                FontSize="16"
                />

            <Button
                Content="Csapatonkénti versenyzők száma"
                Click="compsCount"
                />

            <ListBox
                Name="teamList"
                Height="150"
                />

            <Button
                Content="Magyar versenyzők száma"
                Click="hunCompsCount"
                />

        </StackPanel>
    </Grid>
</Window>
```

### ✂️ XAML Template:

Csak másold ki ezt a templatet, és írd be a saját változóidat a helyükre.
Tök jól tud jönni, rengeteg időt megspórolsz vele.
```
<Window x:Class="TourGUI.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:TourGUI"
        mc:Ignorable="d"
        Title="EZT ITT ÍRD ÁT A PROJEKT NEVÉRE!!!! <<<--------------"
        Height="450" 
        Width="800"
        >

    <Grid>

        <Grid.ColumnDefinitions>

            <ColumnDefinition 
                Width="*"
                />

            <ColumnDefinition 
                Width="300"
                />

        </Grid.ColumnDefinitions>

        <DataGrid 
            Grid.Column="0"
            Name="?????????"
            SelectionMode="Single"
            SelectionChanged="?????????"
            AutoGenerateColumns="True"
            />

        <StackPanel
            Grid.Column="1"
            >
            <TextBlock
                Name="?????????"
                Text="?????????"
                FontSize="?????????"
                />

            <Button
                Content="?????????"
                Click="?????????"
                />

            <ListBox
                Name="?????????"
                Height="150"
                />

            <Button
                Content="?????????"
                Click="?????????"
                />

        </StackPanel>
    </Grid>
</Window>
```