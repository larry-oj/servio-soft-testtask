# Table of Contents

1. [HTML, CSS](#html-css)
2. [C#, Asp.NET](#c-aspnet)
3. [MS SQL](#ms-sql)
4. [LINQ](#linq)

# HTML, CSS

#### 1. Яке зі значень CSS атрибута "position" застосовується для відображення елемента в певному місці на екрані й дає змогу елементу не змінювати свого положення під час прокручування веб-сторінки.

**fixed**

#### 2. Як розмістити на сторінці 2 елементи <div> так, щоб вони розташовувалися на сторінці в такий спосіб, не використовуючи при цьому властивість CSS position:

```html
<div class="container">
    <div>1</div>
    <div>2</div>
</div>

<style>
    .container {
        display: flex;
    }
    
    div {
        flex: 1;
    }
</style>
```

#### 3. В абзаці, що динамічно розтягується по ширині, є словосполучення "добрий вечір". При цьому, словосполучення має завжди бути на одному рядку. Яким чином ми можемо уникнути непотрібного нам перенесення одного зі слів на наступний рядок?

```html
<p>добрий&nbsp;вечір</p>
```
або
```html
<p>
    <span style="white-space: nowrap;">добрий вечір</span>
</p>
```

#### 4. Схематично зобразіть чим відрізняються CSS атрибути margin і padding

![схематичне зображення](https://i.imgur.com/pJjRqrb.png)

#### 5. Напишіть HTML код для відображення таблиці:

```html
<body>
    <style>
        table {
            width: 100%;
        }
        td {
            border: 1px solid black;
            padding: 10px;
        }
        .text-center {
            text-align: center;
        }
        .text-end {
            text-align: end;
        }
    </style>
    <table>
        <tr>
            <td>a</td>
            <td>b</td>
            <td class="text-center" rowspan="3">d</td>
        </tr>
        <tr>
            <td class="text-center" colspan="2">c</td>
        </tr>
        <tr class="text-end">
            <td>e</td>
            <td>f</td>
        </tr>
    </table>
</body>
```

#### 6. Напишіть HTML код для відображення напису C2H5OH:

```html
<body>
    <p>C<sub>2</sub>H<sub>5</sub>OH</p>
</body>
```

# C#, Asp.NET

#### 7. Яка подія відбудеться раніше під час опрацювання сторінки .aspx на стороні сервера: Page_Load чи Button_Click?

    **Page_Load** - відбувається при завантаженні сторінки

#### 8. Напишіть рядок оголошення функції в класі, яку можна викликати без оголошення екземпляра об'єкта класу?

```csharp
public class MyClass
{
    public static void StaticFunction()
    {
        // ...
    }
}
```

#### 9. Чому не компілюється наступний код?

```csharp
public static void Sample_Function(int i)
{
    this.ID = i.ToString();
}
```

`Sample_Function` - статичний метод, і як наслідок **не прив'язаний до екземпляру класу**, `this.` - звертається до **екземпляру класу**

#### 10. Яке значення змінної i буде після виконання наступного коду?

```csharp
int i = 0;
while ((i > 10) && (i < 100))
{
    i++;
}
for (var j = 0; j < 4; j++) 
    i += j;
```

i = 6

#### 11. Який із прикладів коду, наведених нижче, є кращим? Відповідь обґрунтуйте.

```csharp
var s = "";
for (int i = 0; i < 100000; i++)
{
    s += i;
}
```

```csharp
var sb = new StringBuilder();
or (int i = 0; i < 100000; i++)
{
    sb.Append(i);
}
var s = sb.ToString();
```

За умовою, у нас відбувається 100000 операцій. За великих обсягів даних, другий приклад коду, що використовує `StringBuilder`, є кращим. 

`Append` "під копотом" додає до кінця рядка символи, в той час як оператор `+=` створює кожен раз новий рядок. Це надає наступні переваги:
- Економія пам'яті
- Скорочення часу виконання

#### 12. Яке значення змінної i буде після виконання наступного коду:

```csharp
uint k = 5;
object j = k;
long i = (uint) j;
```

i = 5

# MS SQL

#### 13. Як у MSSQL можна дізнатися ID запису, що додався в результаті виконання команди INSERT?

1. Використовуючи `SCOPE_IDENTITY()`:

```sql
SELECT SCOPE_IDENTITY();
```

2. Використовуючи `@@IDENTITY`

```sql
SELECT @@IDENTITY;
```

3. Використовуючи `OUTPUT` всередині операції `INSERT`:

```sql
INSERT INTO SampleTable (Data1, Data2)
OUTPUT INSERTED.ID AS InsertedID
VALUES ('Text1', 'Text2');
```

#### 14. Є 2 таблиці: таблиця гостей (Guests) і таблиця компаній (Companies), від яких ці гості приїхали.

| CompanyID | CompanyName    |
|-----------|----------------|
| 1         | ExpertSolution |
| 2         | ServioSoft     |
| 3         | Apple          |

| GuestID | CompanyID | Name              |
|---------|-----------|-------------------|
| 1       | 1         | Іван Василів      |
| 2       | 1         | Петро Симонович   |
| 3       | 2         | Василь Пупкін     |
| 4       | 3         | Сергій Іванов     |
| 5       | 2         | Роман Пушко       |
| 6       | 1         | Станіслав Мотужко |
| 7       | NULL      | Рустам Алекжі     |

1. **Зобразіть результат виконання запиту:**
```sql
Select G.Name, C.CompanyName
From Guests as G
Left Join Companies as C on G.CompanyID = C.CompanyID;
```

| Name              | CompanyName    |
|-------------------|----------------|
| Іван Василів      | ExpertSolution |
| Петро Симонович   | ExpertSolution |
| Василь Пупкін     | ServioSoft     |
| Сергій Іванов     | Apple          |
| Роман Пушко       | ServioSoft     |
| Станіслав Мотужко | ExpertSolution |
| Рустам Алекжі     | NULL           |

```sql
Select G.Name, C.CompanyName
Join Guests G on G.CompanyID = C.CompanyID
From Companies C
```

Запит має непрвильну структуру, виправлений запит та результат:
```sql
SELECT G.Name, C.CompanyName
FROM Guests G
JOIN Companies C ON G.CompanyID = C.CompanyID;
```

| Name              | CompanyName    |
|-------------------|----------------|
| Іван Василів      | ExpertSolution |
| Петро Симонович   | ExpertSolution |
| Василь Пупкін     | ServioSoft     |
| Сергій Іванов     | Apple          |
| Роман Пушко       | ServioSoft     |
| Станіслав Мотужко | ExpertSolution |

2. **Напишіть запит, який би виводив такі записи:**

- Усіх гостей, які живуть від компанії ExpertSolution

```sql
SELECT G.*
FROM Guests G
JOIN Companies C ON G.CompanyID = C.CompanyID
WHERE C.CompanyName = 'ExpertSolution';
```
- Усі компанії із зазначенням кількості людей, які живуть від них, відсортованих за зменшенням кількості гостей

```sql
SELECT C.CompanyName, COUNT(G.GuestID) AS NumberOfGuests
FROM Companies C
LEFT JOIN Guests G ON C.CompanyID = G.CompanyID
GROUP BY C.CompanyName
ORDER BY NumberOfGuests DESC;
```

- По одному (будь-якому) гостю від кожної компанії, із запиту виводити тільки назву компанії, прізвище та перша літера імені гостя.

```sql
SELECT 
    C.CompanyName,
    LEFT(G.Name, 1) AS FirstNameInitial,
    G.Name AS GuestLastName
FROM (
    SELECT 
        G.CompanyID,
        MIN(G.GuestID) AS MinGuestID
    FROM Guests G
    GROUP BY G.CompanyID
) AS MinGuests
JOIN Guests G ON MinGuests.MinGuestID = G.GuestID
JOIN Companies C ON G.CompanyID = C.CompanyID;
```

# LINQ

#### 15. На основі бази даних в Entity Framework сформовано такі класи:

```csharp
public class Guest
{
    public int GuestID;
    public int CompanyID;
    public Company Company;
    public string Name;
}

public class Company
{
    public int CompanyID;
    public string CompanyName;
    public TrackableCollection<Guest> Guests;
}
```
**Є 2 функції, які повертають колекції відповідних таблиць:**

```csharp
public IQueryable<Guest> GetGuests();
public IQueryable<Company> GetCompanies();
```

**Є кілька DTO класів для виведення інформації користувачеві**

```csharp
public class GuestDTO1
{
    public int GuestID;
    public string Name;
    public string CompanyName;
}

public class CompanyDTO2
{
    public int CompanyID;
    public string CompanyName;
    public int GuestCount;
}

public class CompanyDTO3
{
    public int CompanyID;
    public string CompanyName;
    public string GuestNames;
}
```

**Напишіть LINQ запит, використовуючи "лямбда" вирази, що повертають такі
записи:**

1. **Усіх гостей, які живуть від компанії ExpertSolution**

```csharp
var guests = GetGuests()
    .Where(g => g.Company.CompanyName == "ExpertSolution")
    .Select(g => new GuestDTO1
    {
        GuestID = g.GuestID,
        Name = g.Name,
        CompanyName = g.Company.CompanyName
    })
    .ToList();
```

2. **Усі компанії із зазначенням кількості людей, які живуть від них, відсортованих за зменшенням кількості гостей.**

```csharp
var companies = GetCompanies()
    .GroupJoin(
        GetGuests(),
        c => c.CompanyID,
        g => g.CompanyID,
        (company, guests) => new CompanyDTO2
        {
            CompanyID = company.CompanyID,
            CompanyName = company.CompanyName,
            GuestCount = guests.Count()
        })
    .OrderByDescending(c => c.GuestCount);
```

3. **Усі компанії, для яких є гості з прізвищем, що закінчується на "ко". У результат вивести список таких компаній, без даних гостя.**

```csharp
var targetCompanies = GetCompanies()
    .Where(c => c.Guests.Any(g => g.Name.EndsWith("ко")))
    .Select(c => new CompanyDTO2
    {
        CompanyID = c.CompanyID,
        CompanyName = c.CompanyName
    })
    .ToList();
```

4. **Усі компанії та гостей, які проживають від них. У результаті має виводитися назва компанії, список імен гостей через кому. Для виведення результату використовувати клас CompanyDTO3**

```csharp
var result = GetCompanies()
    .Select(c => new CompanyDTO3
    {
        CompanyID = c.CompanyID,
        CompanyName = c.CompanyName,
        GuestNames = string.Join(", ", GetGuests()
            .Where(g => g.CompanyID == c.CompanyID)
            .Select(g => g.Name))
    })
    .ToList();
```

# JS, jQuery

#### 16. Який знак використовується для використання аліасу jQuery?

**$**

#### 17. Який код слід виконати для виставлення червоного фону всім параграфам?

```js
$("p").css("background-color", "red");
```

#### 18. Перед вами селектор: $("div.intro"). Які елементи він вибере?

**Всі div з класами="intro"**

#### 19. Яка jQuery функція використовується для запобігання запуску коду до тих пір, поки весь документ не буде завантажено?

```js
$(document).ready()
```

#### 20. Який jQuery код зробить усі елементи div висотою 100 пікселів?

```js
$("div").height(100)
```