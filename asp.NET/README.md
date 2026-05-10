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

# 📦 Packagek

- Microsoft.EntityFrameworkCore.Display
- Microsoft.EntityFrameworkCore.Sqlite
  
# ✂️ Code Templatek

### ✂️ DTO Template:
```
public record ItemListDto(int Id, string Name);
 
public record ItemCreateDto(string Name);

public record ItemDetailDto(int Id, string Name, string Description, List<string> SubItems);

```

### ✂️ Controller Template:
```
[ApiController]
[Route("api/[controller]")]
public class ItemsController : ControllerBase
{
    private readonly MyDbContext _context;
 
    public ItemsController(MyDbContext context)
    {
        _context = context;
    }
}
```

### ✂️ SQLite Database Config:
```
using Microsoft.EntityFrameworkCore;
 
var builder = WebApplication.CreateBuilder(args);
 
builder.Services.AddDbContext<MyDbContext>(opt =>
    opt.UseSqlite("Data Source=mydatabase.db"));
 
var app = builder.Build();
app.Run();
```

### ✂️ DbContext Template, teszt adatokkal:
```
using Microsoft.EntityFrameworkCore;
 
public class MyDbContext : DbContext
{
    public MyDbContext(DbContextOptions<MyDbContext> options) : base(options) { }
 
    public DbSet<Owner> Owners => Set<Owner>();
    public DbSet<Pet> Pets => Set<Pet>();
 
    protected override void OnModelCreating(ModelBuilder modelBuilder)
    {
        modelBuilder.Entity<Owner>()
            .Property(o => o.FirstName)
            .IsRequired()
            .HasMaxLength(60);
 
        modelBuilder.Entity<Pet>()
            .HasOne(p => p.Owner)
            .WithMany(o => o.Pets)
            .HasForeignKey(p => p.OwnerId);
    }
}
```

### ✂️ Modell Template:
```
namespace PetClinicApi.Models;
 
public class Owner
{
    public int Id { get; set; }
    public required string FirstName { get; set; }
    public required string LastName { get; set; }
    public string? Phone { get; set; }
    public string? Email { get; set; }
    // Navigációs property
    public List<Pet> Pets { get; set; } = new();
}
```

### ✂️ GET, POST, PUT, DELETE Template egy Controllerben:
```
[ApiController]
[Route("api/[controller]")]
public class ItemsController : ControllerBase
{
    private readonly YourDbContext _db;
    public ItemsController(YourDbContext db) => _db = db;
 
    // --- GET (Olvasás - Összes) ---
    [HttpGet]
    public async Task<ActionResult<List<ItemDto>>> GetAll()
    {
        var items = await _db.Items
            [cite_start].OrderBy(i => i.Name) // Alapértelmezett sorrend 
            .Select(i => new ItemDto(i.Id, i.Name)) 
            .ToListAsync();
 
        return Ok(items); // 200 OK + az adatok
    }
 
    // --- GET (Olvasás - Egy konkrét darab) ---
    [HttpGet("{id}")]
    public async Task<ActionResult<ItemDto>> GetById(int id)
    {
        var item = await _db.Items.FindAsync(id);
 
        if (item == null) return NotFound(); // 404, ha nincs ilyen ID
 
        return Ok(new ItemDto(item.Id, item.Name));
    }
 
    // --- POST (Létrehozás) ---
    [HttpPost]
    public async Task<ActionResult<ItemDto>> Create(ItemCreateDto dto)
    {
        var newItem = new Item { Name = dto.Name };
 
        _db.Items.Add(newItem);
        await _db.SaveChangesAsync();
 
        var result = new ItemDto(newItem.Id, newItem.Name);
 
        // 201 Created + visszairányítás a GetById-re
        return CreatedAtAction(nameof(GetById), new { id = newItem.Id }, result);
    }
 
    // --- PUT (Módosítás) ---
    [HttpPut("{id}")]
    public async Task<IActionResult> Update(int id, ItemCreateDto dto)
    {
        var item = await _db.Items.FindAsync(id);
 
        if (item == null) return NotFound();
 
        item.Name = dto.Name; // Mezők frissítése
 
        await _db.SaveChangesAsync();
 
        return NoContent(); // 204: Sikerült, nincs visszatérő adat
    }
 
    // --- DELETE (Törlés) ---
    [HttpDelete("{id}")]
    public async Task<IActionResult> Delete(int id)
    {
        var item = await _db.Items.FindAsync(id);
 
        if (item == null) return NotFound();
 
        _db.Items.Remove(item);
        await _db.SaveChangesAsync();
 
        return NoContent(); // 204: Sikeres törlés
    }
}
```