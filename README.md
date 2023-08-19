# HTML, CSS

1. Яке зі значень CSS атрибута "position" застосовується для відображення елемента в певному місці на екрані й дає змогу елементу не змінювати свого положення під час прокручування веб-сторінки.

    **fixed**

2. Як розмістити на сторінці 2 елементи <div> так, щоб вони розташовувалися на сторінці в такий спосіб, не використовуючи при цьому властивість CSS position:

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

3. В абзаці, що динамічно розтягується по ширині, є словосполучення "добрий вечір". При цьому, словосполучення має завжди бути на одному рядку. Яким чином ми можемо уникнути непотрібного нам перенесення одного зі слів на наступний рядок?

```html
<p>добрий&nbsp;вечір</p>
```
або
```html
<p>
    <span style="white-space: nowrap;">добрий вечір</span>
</p>
```

4. Схематично зобразіть чим відрізняються CSS атрибути margin і padding

![схематичне зображення](https://i.imgur.com/pJjRqrb.png)

5. Напишіть HTML код для відображення таблиці:

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

6. Напишіть HTML код для відображення напису C2H5OH:

```html
<body>
    <p>C<sub>2</sub>H<sub>5</sub>OH</p>
</body>
```