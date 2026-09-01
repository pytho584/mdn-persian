---
title: "Building and updating the DOM tree"
---

---
title: Building and updating the DOM tree
slug: Web/API/Document_Object_Model/Building_and_updating_the_DOM_tree
page-type: guide
---

{{DefaultAPISidebar("DOM")}}

این مقاله مروری است بر برخی از متدهای قدرتمند و بنیادی DOM سطح ۱ و نحوهٔ استفاده از آن‌ها در جاوااسکریپت. یاد می‌گیرید که چگونه عناصر HTML را به‌صورت پویا ایجاد کنید، به آن‌ها دسترسی پیدا کنید و کنترل‌شان کنید، و آن‌ها را حذف کنید. متدهای DOM که در اینجا معرفی می‌شوند مختص HTML نیستند؛ بلکه برای XML نیز کاربرد دارند. نمونه‌های ارائه‌شده در این مقاله در هر مرورگر مدرنی به‌درستی کار می‌کنند.

> [!NOTE]
> متدهای DOM ارائه‌شده در اینجا بخشی از مشخصات سطح ۱ مدل شیء سند (هسته) هستند. DOM سطح ۱ شامل متدهایی برای دسترسی عمومی به سند و دستکاری آن (DOM 1 Core) و همچنین متدهای مخصوص اسناد HTML (DOM 1 HTML) است.

## ایجاد پویای یک جدول HTML

### مثال

در این مثال، با کلیک روی یک دکمه، یک جدول جدید به صفحه اضافه می‌کنیم.

#### HTML

```html
<input type="button" value="Generate a table" />
```

#### JavaScript

```js
function generateTable() {
  // creates a <table> element and a <tbody> element
  const tbl = document.createElement("table");
  const tblBody = document.createElement("tbody");

  // creating all cells
  for (let i = 0; i < 2; i++) {
    // creates a table row
    const row = document.createElement("tr");

    for (let j = 0; j < 2; j++) {
      // Create a <td> element and a text node, make the text
      // node the contents of the <td>, and put the <td> at
      // the end of the table row
      const cell = document.createElement("td");
      const cellText = document.createTextNode(`cell in row ${i}, column ${j}`);
      cell.appendChild(cellText);
      row.appendChild(cell);
    }

    // add the row to the end of the table body
    tblBody.appendChild(row);
  }

  // put the <tbody> in the <table>
  tbl.appendChild(tblBody);
  // appends <table> into <body>
  document.body.appendChild(tbl);
  // sets the border attribute of tbl to '2'
  tbl.setAttribute("border", "2");
}

document
  .querySelector("input[type='button']")
  .addEventListener("click", generateTable);
```

```css hidden
table {
  margin: 1rem auto;
}

td {
  padding: 0.5rem;
}
```

#### نتیجه

{{ EmbedLiveSample('Example') }}

### توضیح

به ترتیبی که عناصر و گره متنی را ایجاد کردیم توجه کنید:

1. ابتدا عنصر `<table>` را ایجاد کردیم.
2. سپس عنصر `<tbody>` را که فرزند عنصر `<table>` است ایجاد کردیم.
3. سپس با استفاده از یک حلقه، عناصر `<tr>` را که فرزندان عنصر `<tbody>` هستند ایجاد کردیم.
4. برای هر عنصر `<tr>`، با استفاده از یک حلقه، عناصر `<td>` را که فرزندان عناصر `<tr>` هستند ایجاد کردیم.
5. سپس برای هر عنصر `<td>`، گره متنی حاوی متن خانهٔ جدول را ایجاد کردیم.

پس از ایجاد عناصر `<table>`، `<tbody>`، `<tr>`، `<td>` و سپس گره متنی، هر شیء را به ترتیب معکوس به والد خود اضافه می‌کنیم:

1. ابتدا هر گره متنی را با استفاده از

   ```js
   cell.appendChild(cellText);
   ```

   به عنصر والد `<td>` متصل می‌کنیم.

2. سپس هر عنصر `<td>` را با استفاده از

   ```js
   row.appendChild(cell);
   ```

   به عنصر والد `<tr>` متصل می‌کنیم.

3. سپس هر عنصر `<tr>` را با استفاده از

   ```js
   tblBody.appendChild(row);
   ```

   به عنصر والد `<tbody>` متصل می‌کنیم.

4. سپس عنصر `<tbody>` را با استفاده از

   ```js
   tbl.appendChild(tblBody);
   ```

   به عنصر والد `<table>` متصل می‌کنیم.

5. سپس عنصر `<table>` را با استفاده از

   ```js
   document.body.appendChild(tbl);
   ```

   به عنصر والد `<body>` متصل می‌کنیم.

این تکنیک را به خاطر بسپارید. در برنامه‌نویسی برای W3C DOM بارها به آن نیاز خواهید داشت. ابتدا عناصر را از بالا به پایین ایجاد می‌کنید؛ سپس فرزندان را از پایین به بالا به والدهایشان متصل می‌کنید.

در زیر، مارکاپ HTML تولیدشده توسط کد جاوااسکریپت آمده است:

```html
<table border="2">
  <tbody>
    <tr>
      <td>cell is row 0 column 0</td>
      <td>cell is row 0 column 1</td>
    </tr>
    <tr>
      <td>cell is row 1 column 0</td>
      <td>cell is row 1 column 1</td>
    </tr>
  </tbody>
</table>
```

درخت شیء DOM تولیدشده توسط کد برای عنصر `<table>` و عناصر فرزند آن به این صورت است:

![نحوهٔ تولید درخت شیء DOM از عنصر اصلی و فرزندان آن](sample1-tabledom.jpg)

می‌توانید این جدول و عناصر فرزند داخلی آن را فقط با چند متد DOM ایجاد کنید. به یاد داشته باشید که مدل درختی ساختارهایی را که قصد ساختن‌شان را دارید در نظر بگیرید؛ این کار نوشتن کد لازم را آسان‌تر می‌کند. در درخت `<table>` شکل ۱، عنصر `<table>` یک فرزند دارد: عنصر `<tbody>`. `<tbody>` دو فرزند دارد. هر فرزند `<tbody>` (یعنی `<tr>`) دو فرزند (`<td>`) دارد. در نهایت، هر `<td>` یک فرزند دارد: یک گره متنی.

## تنظیم رنگ پس‌زمینهٔ یک پاراگراف

### مثال

در این مثال، با کلیک روی یک دکمه، رنگ پس‌زمینهٔ یک پاراگراف را تغییر می‌دهیم.

#### HTML

```html
<body>
  <input type="button" value="Set paragraph background color" />
  <p>hi</p>
  <p>hello</p>
</body>
```

#### JavaScript

```js
function setBackground() {
  // now, get all the p elements in the document
  const paragraphs = document.getElementsByTagName("p");

  // get the second paragraph from the list
  const secondParagraph = paragraphs[1];

  // set the inline style
  secondParagraph.style.background = "red";
}

document.querySelector("input").addEventListener("click", setBackground);
```

#### نتیجه

{{ EmbedLiveSample('Example_2') }}

### توضیح

`getElementsByTagName(tagNameValue)` یک متد است که در هر {{domxref("Element")}} یا عنصر ریشهٔ {{domxref("Document")}} در DOM در دسترس است. هنگام فراخوانی، آرایه‌ای شامل همهٔ نوادگان آن عنصر که با نام تگ مطابقت دارند بازمی‌گرداند. اولین عنصر فهرست در موقعیت `[0]` آرایه قرار دارد.

مراحل زیر را انجام داده‌ایم:

1. ابتدا همهٔ عناصر `p` سند را دریافت می‌کنیم:

   ```js
   const paragraphs = document.getElementsByTagName("p");
   ```

2. سپس دومین عنصر پاراگراف را از فهرست عناصر `p` می‌گیریم:

   ```js
   const secondParagraph = paragraphs[1];
   ```

   ![یک عنصر پاراگراف به‌عنوان یک خواهر/برادر جدید به یک پاراگراف موجود در درخت DOM اضافه شده است](sample2a2.jpg)

3. در نهایت، رنگ پس‌زمینه را با استفاده از ویژگی {{domxref("HTMLElement.style", "style")}} شیء {{domxref("HTMLParagraphElement", "paragraph")}} قرمز می‌کنیم:

   ```js
   secondParagraph.style.background = "red";
   ```

### ایجاد گره‌های متنی با document.createTextNode("..")

برای فراخوانی متد `createTextNode` و ایجاد گره متنی خود، از شیء document استفاده کنید. فقط کافی است محتوای متنی را ارسال کنید. مقدار بازگشتی یک شیء است که گره متنی را نمایش می‌دهد.

```js
myTextNode = document.createTextNode("world");
```

این یعنی گرهی از نوع `TEXT_NODE` (یک قطعه متن) ایجاد کرده‌اید که دادهٔ متنی آن `"world"` است و `myTextNode` ارجاع شما به این شیء گره است. برای درج این متن در صفحهٔ HTML خود، باید این گره متنی را فرزند یک گرهٔ دیگر کنید.

### درج عناصر با appendChild(..)

بنابراین، با فراخوانی `secondParagraph.appendChild(node_element)`، این عنصر را به فرزند جدیدی از دومین عنصر `<p>` تبدیل می‌کنید.

```js
secondParagraph.appendChild(myTextNode);
```

پس از آزمایش این نمونه، توجه کنید که کلمات hello و world کنار هم هستند: helloworld. بنابراین از نظر بصری، وقتی صفحهٔ HTML را می‌بینید، به نظر می‌رسد دو گره متنی hello و world یک گره واحد هستند؛ اما به یاد داشته باشید که در مدل سند، دو گره وجود دارد. گرهٔ دوم، گرهٔ جدیدی از نوع `TEXT_NODE` است و دومین فرزند تگ دوم `<p>` است. شکل زیر شیء Text Node تازه‌ایجادشده را در داخل درخت سند نشان می‌دهد.

![گره‌های متنی در یک عنصر پاراگراف به‌عنوان خواهر/برادرهایی مجزا در درخت DOM](sample2b2.jpg)

> [!NOTE]
> استفاده از `createTextNode()` و `appendChild()` روش ساده‌ای برای گنجاندن فاصلهٔ سفید بین کلمات _hello_ و _world_ است. نکتهٔ مهم دیگر این است که متد `appendChild` فرزند را بعد از آخرین فرزند اضافه می‌کند، دقیقاً مانند اینکه کلمهٔ _world_ بعد از کلمهٔ _hello_ اضافه شده است. بنابراین اگر می‌خواهید یک گره متنی بین _hello_ و _world_ اضافه کنید، به‌جای `appendChild` باید از `insertBefore` استفاده کنید.

### ایجاد عناصر جدید با شیء document و متد createElement(..)

با `createElement` می‌توانید عناصر HTML جدید یا هر عنصر دیگری که می‌خواهید ایجاد کنید. برای مثال، اگر بخواهید یک عنصر `<p>` جدید به‌عنوان فرزند عنصر `<body>` بسازید، می‌توانید از `myBody` مثال قبلی استفاده کنید و یک گرهٔ عنصر جدید به آن اضافه کنید. برای ایجاد یک گره، `document.createElement("tagname")` را فراخوانی کنید. برای مثال:

```js
myNewPTagNode = document.createElement("p");
myBody.appendChild(myNewPTagNode);
```

![نحوهٔ افزودن یک گرهٔ عنصر جدید به شیء گرهٔ متنی در داخل درخت سند](sample2c.jpg)

### حذف گره‌ها با متد removeChild(..)

گره‌ها قابل حذف هستند. کد زیر گرهٔ متنی `myTextNode` (شامل کلمهٔ «world») را از دومین عنصر `<p>` یعنی `secondParagraph` حذف می‌کند.

```js
secondParagraph.removeChild(myTextNode);
```

گرهٔ متنی `myTextNode` (شامل کلمهٔ «world») همچنان وجود دارد. کد زیر، `myTextNode` را به عنصر `<p>` تازه‌ایجادشده یعنی `myNewPTagNode` متصل می‌کند.

```js
myNewPTagNode.appendChild(myTextNode);
```

وضعیت نهایی درخت شیء تغییر یافته به این شکل است:

![ایجاد و افزودن یک عنصر گره جدید به ساختار متنی درخت شیء](sample2d.jpg)

## ایجاد پویای یک جدول

شکل زیر ساختار درخت شیء جدول را برای جدول ایجادشده در نمونه نشان می‌دهد.

### مرور ساختار جدول HTML

![ساختار درخت شیء جدول HTML پس از افزودن گره‌های عنصر جدید](sample1-tabledom.jpg)

### ایجاد گره‌های عنصر و درج آن‌ها در درخت سند

مراحل اصلی ایجاد جدول عبارت‌اند از:

- دریافت شیء body (اولین آیتم شیء document).
- ایجاد همهٔ عناصر.
- در نهایت، هر فرزند را مطابق ساختار جدول (مانند شکل بالا) به والدش اضافه کنید.

> [!NOTE]
> در انتهای اسکریپت، یک خط کد جدید وجود دارد. ویژگی `border` جدول با استفاده از یک متد DOM دیگر به نام `setAttribute()` تنظیم شده است. `setAttribute()` دو آرگومان دارد: نام ویژگی و مقدار ویژگی. می‌توانید با استفاده از متد `setAttribute` هر ویژگی‌ای را روی هر عنصری تنظیم کنید.

```js
// get the reference for the body
const myBody = document.getElementsByTagName("body")[0];

// creates <table> and <tbody> elements
const myTable = document.createElement("table");
const myTableBody = document.createElement("tbody");

// creating all cells
for (let j = 0; j < 3; j++) {
  // creates a <tr> element
  const myCurrentRow = document.createElement("tr");

  for (let i = 0; i < 4; i++) {
    // creates a <td> element
    const myCurrentCell = document.createElement("td");
    // creates a Text Node
    const currentText = document.createTextNode(
      `cell is row ${j}, column ${i}`,
    );
    // appends the Text Node we created into the cell <td>
    myCurrentCell.appendChild(currentText);
    // appends the cell <td> into the row <tr>
    myCurrentRow.appendChild(myCurrentCell);
  }
  // appends the row <tr> into <tbody>
  myTableBody.appendChild(myCurrentRow);
}

// appends <tbody> into <table>
myTable.appendChild(myTableBody);
// appends <table> into <body>
myBody.appendChild(myTable);
// sets the border attribute of myTable to 2;
myTable.setAttribute("border", "2");
```

## دستکاری جدول با DOM و CSS

### دریافت یک گره متنی از جدول

این مثال دو ویژگی DOM جدید را معرفی می‌کند. ابتدا از ویژگی `childNodes` برای دریافت فهرست گره‌های فرزند myCell استفاده می‌کند. فهرست `childNodes` همهٔ گره‌های فرزند را بدون توجه به نام یا نوع آن‌ها در بر می‌گیرد. مانند `getElementsByTagName()`، این فهرست، فهرستی از گره‌ها را بازمی‌گرداند.

تفاوت‌ها این است که (الف) `getElementsByTagName()` فقط عناصری با نام تگ مشخص‌شده را بازمی‌گرداند؛ و (ب) `childNodes` همهٔ نوادگان را در هر سطحی شامل می‌شود، نه فقط فرزندان مستقیم را.

پس از دریافت فهرست بازگشتی، از متد `[x]` برای بازیابی آیتم فرزند موردنظر استفاده کنید. این مثال، گره متنی دومین خانه در دومین ردیف جدول را در `myCellText` ذخیره می‌کند.

سپس، برای نمایش نتایج در این مثال، یک گرهٔ متنی جدید ایجاد می‌کند که محتوای آن دادهٔ `myCellText` است و آن را به‌عنوان فرزند عنصر `<body>` اضافه می‌کند.

> [!NOTE]
> اگر شیء شما یک گرهٔ متنی است، می‌توانید از ویژگی data استفاده کنید و محتوای متنی گره را دریافت کنید.

```js
const myBody = document.getElementsByTagName("body")[0];
const myTable = myBody.getElementsByTagName("table")[0];
const myTableBody = myTable.getElementsByTagName("tbody")[0];
const myRow = myTableBody.getElementsByTagName("tr")[1];
const myCell = myRow.getElementsByTagName("td")[1];

// first item element of the childNodes list of myCell
const myCellText = myCell.childNodes[0];

// content of currentText is the data content of myCellText
const currentText = document.createTextNode(myCellText.data);
myBody.appendChild(currentText);
```

### دریافت مقدار یک ویژگی

در انتهای نمونه۱، فراخوانی `setAttribute` روی شیء `myTable` انجام شده است. از این فراخوانی برای تنظیم ویژگی border جدول استفاده شده بود. برای دریافت مقدار ویژگی، از متد `getAttribute` استفاده کنید:

```js
myTable.getAttribute("border");
```

### پنهان کردن یک ستون با تغییر ویژگی‌های style

وقتی شیء را در متغیر جاوااسکریپت خود داشته باشید، می‌توانید ویژگی‌های `style` را مستقیماً تنظیم کنید. کد زیر یک نسخهٔ اصلاح‌شده است که در آن هر خانه از ستون دوم پنهان شده و هر خانه از ستون اول به رنگ پس‌زمینهٔ قرمز تغییر یافته است. توجه کنید که ویژگی `style` مستقیماً تنظیم شده است.

```js
const myBody = document.getElementsByTagName("body")[0];
const myTable = document.createElement("table");
const myTableBody = document.createElement("tbody");

for (let row = 0; row < 2; row++) {
  const myCurrentRow = document.createElement("tr");
  for (let col = 0; col < 2; col++) {
    const myCurrentCell = document.createElement("td");
    const currentText = document.createTextNode(`cell is: ${row}${col}`);
    myCurrentCell.appendChild(currentText);
    myCurrentRow.appendChild(myCurrentCell);
    // set the cell background color
    // if the column is 0. If the column is 1 hide the cell
    if (col === 0) {
      myCurrentCell.style.background = "red";
    } else {
      myCurrentCell.style.display = "none";
    }
  }
  myTableBody.appendChild(myCurrentRow);
}
myTable.appendChild(myTableBody);
myBody.appendChild(myTable);
```