# Table of Contents

1. [HTML, CSS](#html-css)
2. [C#, Asp.NET](#c-aspnet)

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