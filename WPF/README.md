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

A projekthez kapni fogsz egy .sql fájlt amit egy adatbázisra kell átformáznod. Olyan mint egy recept. Nyisd meg, vagy töltsd le a DB Browser-t SQLite-hoz.

https://sqlitebrowser.org/dl/

Majd ezt követően nyisd meg és importáld be a .sql fájlt.
Utána `File > Save Database as...` és .db fájlként mentsd el a `\Debug\.NET Verzió\` könyvtárba a projekteden belül, így látni fogja a kódod.

# 💻 Megoldások a gyakorló feladathoz:
Két fájlt kell írni a feladat során, magát a kódot, és az xaml fájlt. Egyik a program, másik a UI.

### 🟪 MainWindow.xaml.cs
```
using System.Windows;
using System.Windows.Controls;
using System.Data.SQLite;

namespace TourGUI
{
    public partial class MainWindow : Window
    {
        List<Versenyzo> versenyzok = new List<Versenyzo>();
        string connectionString = "Data Source=tour.sql;Version=3;";

        public MainWindow()
        {
            InitializeComponent();
            AdatokBetoltese();
            dgVersenyzok.ItemsSource = versenyzok;
            dgVersenyzok.SelectedIndex = 0;
        }

        private void AdatokBetoltese()
        {
            using (var conn = new SQLiteConnection(connectionString))
            {
                conn.Open();
                var command = new SQLiteCommand("SELECT v.id, v.nev, v.nemzetiseg, c.csapatNev FROM versenyzo v JOIN csapat c ON v.csapatId = c.id", conn);

                using (var reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        versenyzok.Add(new Versenyzo
                        {
                            Id = reader.GetInt32(0),
                            Nev = reader.GetString(1),
                            Nemzetiseg = reader.GetString(2),
                            CsapatNev = reader.GetString(3)
                        });
                    }
                }
            }
        }

        private void dgVersenyzok_SelectionChanged(object sender, SelectionChangedEventArgs e)
        {
            if (dgVersenyzok.SelectedItem is Versenyzo valasztott)
            {
                using (var conn = new SQLiteConnection(connectionString))
                {
                    conn.Open();
                    var command = new SQLiteCommand("SELECT ido FROM eredmeny WHERE versenyzoId = @id AND szakasz = 5", conn);
                    command.Parameters.AddWithValue("@id", valasztott.Id);

                    var result = command.ExecuteScalar();

                    if (result != null)
                    {
                        tbSzakaszEredmeny.Text = $"5. szakasz eredménye: {result}";
                    }
                    else
                    {
                        tbSzakaszEredmeny.Text = "5. szakasz eredménye: Nincs adat";
                    }
                }
            }
        }

        private void btnCsapatok_Click(object sender, RoutedEventArgs e)
        {
            lbCsapatok.Items.Clear();
            var csoportositott = versenyzok.GroupBy(v => v.CsapatNev)
                                          .Select(g => $"{g.Key}: {g.Count()}");
            foreach (var sor in csoportositott)
            {
                lbCsapatok.Items.Add(sor);
            }
        }

        private void btnMagyarok_Click(object sender, RoutedEventArgs e)
        {
            int magyarokSzama = versenyzok.Count(v => v.Nemzetiseg == "HUN");
            MessageBox.Show($"Magyar versenyzők száma: {magyarokSzama}");
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
        Title="MainWindow" Height="450" Width="800">
    <Grid>
        <DataGrid Name="dgVersenyzok" Margin="10,10,400,50" SelectionMode="Single" SelectionChanged="dgVersenyzok_SelectionChanged" AutoGenerateColumns="False">
            <DataGrid.Columns>
                <DataGridTextColumn Header="Id" Binding="{Binding Id}" Width="30" />
                <DataGridTextColumn Header="Név" Binding="{Binding Nev}" Width="*" />
                <DataGridTextColumn Header="Csapat" Binding="{Binding CsapatNev}" Width="*" />
                <DataGridTextColumn Header="Nemzetiség" Binding="{Binding Nemzetiseg}" Width="80" />
            </DataGrid.Columns>
        </DataGrid>

        <StackPanel Margin="420,10,10,10">
            <TextBlock Name="tbSzakaszEredmeny" Text="5. szakasz eredménye:" FontSize="16" Margin="0,0,0,20" />
            <Button Content="Csapatonkénti versenyzők száma" Click="btnCsapatok_Click" Margin="0,0,0,5" />
            <ListBox Name="lbCsapatok" Height="150" Margin="0,0,0,20" />
            <Button Content="Magyar versenyzők száma" Click="btnMagyarok_Click" />
        </StackPanel>
    </Grid>
</Window>

```

### ✂️ XAML Template:

```
<Grid>


    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="*" />
        <ColumnDefinition Width="300" />
    </Grid.ColumnDefinitions>


    <DataGrid
        Grid.Column="0"
        Name="dgVersenyzok"
        AutoGenerateColumns="True"
        SelectionMode="Single"
    />


    <StackPanel
        Grid.Column="1"
            >


        <TextBlock Name="asd" Text="5. szakasz eredménye"/>


        <Button
            Content="Csapatonként versenyzők száma"
            />


        <ListBox Height="100" Margin="0,0,0,5">
            <ListBoxItem Content="Első random adat"/>
            <ListBoxItem Content="Második random adat"/>
            <ListBoxItem Content="Szuper fontos infó"/>
            <ListBoxItem Content="Ez is egy sor"/>
        </ListBox>


        <Button 
            Content="Magyar versenyzők száma"
            />

            
    </StackPanel>
</Grid>
```