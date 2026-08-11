---
title: "Shorthand properties"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Cascade/Shorthand_properties"
translated_by: "n8n + AI"
---

**ویژگی‌های خلاصه‌نویس (Shorthand Properties)**  
ویژگی‌های خلاصه‌نویس (Shorthand Properties) ویژگی‌های CSS هستند که به شما اجازه می‌دهند مقادیر چندین ویژگی دیگر CSS را در یک اعلان تنظیم کنید. با استفاده از یک shorthand، می‌توانید شیوه‌نامه‌های مختصرتر (و اغلب خواناتر) بنویسید و در زمان و انرژی صرفه‌جویی کنید.

مشخصات CSS ویژگی‌های خلاصه‌نویس را برای گروه‌بندی تعریف ویژگی‌های رایجی که روی یک موضوع مشترک کار می‌کنند، تعریف می‌کند. برای مثال، ویژگی `background` یک shorthand است که می‌تواند مقادیر `background-color`، `background-image`، `background-repeat` و `background-position` را تعریف کند.

## موارد خاص (Edge Cases)

هنگام استفاده از ویژگی‌های خلاصه‌نویس، چند مورد خاص را باید در نظر داشته باشید.

### حذف ویژگی‌ها (Omitting properties)

مقداری که مشخص نشود، به مقدار پیش‌فرض تعریف‌شده توسط shorthand تنظیم می‌شود که ممکن است با مقدار اولیه (initial value) property متفاوت باشد. این یعنی مقادیر قبلی را **بازنویسی (override)** می‌کند. برای مثال:

```css
p {
  background-color: red;
  background: url("images/bg.gif") no-repeat left top;
}
```

در اینجا رنگ پس‌زمینه `red` نخواهد بود، بلکه به مقدار پیش‌فرض `background-color` یعنی `transparent` تنظیم می‌شود.

فقط مقادیر ویژگی‌های تکی می‌توانند ارث‌بری (inherit) شوند. از آنجایی که مقادیر缺失 با مقدار اولیه خود جایگزین می‌شوند، امکان ارث‌بری ویژگی‌های تکی با حذف آن‌ها وجود ندارد. کلمه کلیدی `inherit` را می‌توان به یک property اعمال کرد، اما فقط به صورت کلی، نه به عنوان کلمه کلیدی برای یک مقدار خاص. یعنی تنها راه برای ارث‌بری یک مقدار خاص، استفاده از property طولانی (longhand) با کلمه کلیدی `inherit` است.

### ترتیب ویژگی‌ها (Ordering properties)

ویژگی‌های خلاصه‌نویس سعی می‌کنند ترتیب خاصی را برای مقادیر ویژگی‌هایی که جایگزین می‌کنند، تحمیل نکنند. این موضوع زمانی که این ویژگی‌ها از مقادیری با انواع مختلف استفاده می‌کنند، خوب کار می‌کند (چون ترتیب اهمیتی ندارد)، اما زمانی که چندین ویژگی می‌توانند مقادیر یکسان داشته باشند، به این راحتی عمل نمی‌کند.

دو مورد مهم در اینجا عبارتند از:

- ویژگی‌های مربوط به **کناره‌های جعبه (sides of the box)**، مانند `border-style`، `margin` یا `padding`
- ویژگی‌های مربوط به **گوشه‌های جعبه (corners of the box)**، مانند `border-radius`

#### کناره‌های جعبه

Shorthandهایی که ویژگی‌های مربوط به کناره‌های جعبه را مدیریت می‌کنند، مانند `border-style`، `margin` یا `padding`، همیشه از یک سینتکس 1 تا 4 مقداری ثابت برای نمایش آن کناره‌ها استفاده می‌کنند:

- **سینتکس ۱ مقداری:** `border-width: 1em` — یک مقدار نشان‌دهندهٔ همهٔ کناره‌ها است: ![Box edges with one-value syntax](border1.png)

- **سینتکس ۲ مقداری:** `border-width: 1em 2em` — مقدار اول نشان‌دهندهٔ کناره‌های بالا و پایین، و مقدار دوم نشان‌دهندهٔ کناره‌های چپ و راست است: ![Box edges with two-value syntax](border2.png)

- **سینتکس ۳ مقداری:** `border-width: 1em 2em 3em` — مقدار اول نشان‌دهندهٔ کنارهٔ بالا، مقدار دوم نشان‌دهندهٔ کناره‌های چپ و راست، و مقدار سوم نشان‌دهندهٔ کنارهٔ پایین است: ![Box edges with three-value syntax](border3.png)

- **سینتکس ۴ مقداری:** `border-width: 1em 2em 3em 4em` — چهار مقدار به ترتیب نشان‌دهندهٔ کناره‌های بالا، راست، پایین و چپ هستند؛ همیشه به همین ترتیب، یعنی در جهت عقربه‌های ساعت از بالا شروع می‌شود: ![Box edges with four-value syntax](border4.png) حروف اول کلمات Top-Right-Bottom-Left با ترتیب حروف بی‌صدا در کلمهٔ «trouble» (TRBL) مطابقت دارد. همچنین می‌توانید آن را به عنوان ترتیب حرکت عقربه‌های ساعت به خاطر بسپارید: `1em` در موقعیت ساعت ۱۲، سپس `2em` در ساعت ۳، سپس `3em` در ساعت ۶، و `4em` در ساعت ۹.

#### گوشه‌های جعبه

به طور مشابه، shorthandهایی که ویژگی‌های مربوط به گوشه‌های جعبه را مدیریت می‌کنند، مانند `border-radius`، همیشه از یک سینتکس 1 تا 4 مقداری ثابت برای نمایش آن گوشه‌ها استفاده می‌کنند:

- **نحو یک‌مقداری:** `border-radius: 1em` — یک مقدار نشان‌دهندهٔ همهٔ گوشه‌هاست: ![گوشه‌های جعبه با نحو یک‌مقداری](corner1.png)

- **نحو دو-مقداری:** `border-radius: 1em 2em` — مقدار اول نشان‌دهندهٔ گوشه‌های بالا-چپ و پایین-راست و مقدار دوم نشان‌دهندهٔ گوشه‌های بالا-راست و پایین-چپ است: ![گوشه‌های جعبه با نحو دو-مقداری](corner2.png)

- **نحو سه-مقداری:** `border-radius: 1em 2em 3em` — مقدار اول نشان‌دهندهٔ گوشهٔ بالا-چپ، مقدار دوم نشان‌دهندهٔ گوشه‌های بالا-راست و پایین-چپ و مقدار سوم نشان‌دهندهٔ گوشهٔ پایین-راست است: ![گوشه‌های جعبه با نحو سه-مقداری](corner3.png)

- **نحو چهار-مقداری:** `border-radius: 1em 2em 3em 4em` — چهار مقدار به ترتیب نشان‌دهندهٔ گوشه‌های بالا-چپ، بالا-راست، پایین-راست و پایین-چپ هستند؛ همیشه به همین ترتیب، یعنی در جهت عقربه‌های ساعت از بالا-چپ شروع می‌شود: ![گوشه‌های جعبه با نحو چهار-مقداری](corner4.png)

## ویژگی‌های background

به یک background با ویژگی‌های زیر توجه کنید:

```css
background-color: black;
background-image: url("images/bg.gif");
background-repeat: no-repeat;
background-position: left top;
```

این چهار اعلان را می‌توان به یک اعلان کوتاه کرد:

```css
background: black url("images/bg.gif") no-repeat left top;
```

(فرم shorthand در واقع معادل ویژگی‌های بلند بالا به اضافهٔ `background-attachment: scroll` و در CSS3 چند ویژگی دیگر است.)

برای اطلاعات بیشتر، از جمله ویژگی‌های CSS3، به مستندات background مراجعه کنید.

## ویژگی‌های font

اعلان‌های زیر را در نظر بگیرید:

```css
font-style: italic;
font-weight: bold;
font-size: 0.8em;
line-height: 1.2;
font-family: "Arial", sans-serif;
```

این پنج عبارت را می‌توان به صورت زیر کوتاه کرد:

```css
font:
  italic bold 0.8em/1.2 "Arial",
  sans-serif;
```

این اعلان shorthand در واقع معادل اعلان‌های بلند بالا به اضافهٔ `font-variant: normal`، `font-size-adjust: none` و `font-stretch: normal` است.

## ویژگی‌های border

در مورد borderها، می‌توان width، color و style را در یک اعلان خلاصه کرد. برای مثال، CSS زیر را در نظر بگیرید:

```css
border-width: 1px;
border-style: solid;
border-color: black;
```

می‌توان آن را به صورت زیر ساده کرد:

```css
border: 1px solid black;
```

## ویژگی‌های margin و padding

نسخه‌های shorthand مقادیر margin و padding به طور مشابه کار می‌کنند؛ ویژگی margin اجازه می‌دهد مقادیر را با یک، دو، سه یا چهار مقدار مشخص کنید. اعلان‌های CSS زیر را در نظر بگیرید:

```css
margin-top: 10px;
margin-right: 5px;
margin-bottom: 10px;
margin-left: 5px;
```

آن‌ها معادل اعلان زیر با استفاده از shorthand چهارمقداری هستند. توجه کنید که مقادیر به ترتیب جهت عقربه‌های ساعت، از بالا شروع می‌شوند: top، right، bottom و سپس left (TRBL، حروف بی‌صدا در کلمه trouble).

```css
margin: 10px 5px 10px 5px;
```

قوانین shorthand برای margin با یک، دو، سه و چهار مقدار به این صورت است:

- وقتی **یک** مقدار مشخص شود، آن مقدار برای **هر چهار طرف** یکسان اعمال می‌شود.
- وقتی **دو** مقدار مشخص شود، مقدار اول برای **بالا و پایین** و مقدار دوم برای **چپ و راست** اعمال می‌شود.
- وقتی **سه** مقدار مشخص شود، مقدار اول برای **بالا**، مقدار دوم برای **چپ و راست** و مقدار سوم برای **پایین** اعمال می‌شود.
- وقتی **چهار** مقدار مشخص شود، مقادیر به ترتیب برای **بالا**، **راست**، **پایین** و **چپ** (در جهت عقربه‌های ساعت) اعمال می‌شوند.

## ویژگی‌های position

در مورد position، می‌توان نسخه‌های shorthand برای top، right، bottom و left را در یک اعلان خلاصه کرد. برای مثال، CSS زیر را در نظر بگیرید:

```css
top: 0;
right: 20px;
bottom: 0;
left: 20px;
```

می‌توان آن را به صورت زیر ساده کرد:

```css
inset: 0 20px 0 20px;
```

درست مانند margin و padding، مقادیر inset به ترتیب جهت عقربه‌های ساعت مرتب می‌شوند: top، right، bottom و بعد left (TRBL).

## ویژگی shorthand عمومی

CSS یک ویژگی میانبر (shorthand property) عمومی به نام `all` ارائه می‌دهد که مقدار خود را به تمام ویژگی‌های سند اعمال می‌کند. هدف آن تغییر مدل ارث‌بری (inheritance) ویژگی‌ها است.

برای اطلاعات بیشتر درباره نحوه کار ارث‌بری در CSS، به [مدیریت تعارض‌ها](/en-US/docs/Learn_web_development/Core/Styling_basics/Handling_conflicts) یا [آشنایی با آبشار CSS](/en-US/docs/Web/CSS/Guides/Cascade/Introduction) مراجعه کنید.

## Shorthand properties

- all
- animation
- animation-range
- background
- border
- border-block
- border-block-end
- border-block-start
- border-bottom
- border-color
- border-image
- border-inline
- border-inline-end
- border-inline-start
- border-left
- border-radius
- border-right
- border-style
- border-top
- border-width
- column-rule
- columns
- contain-intrinsic-size
- container
- flex
- flex-flow
- font
- font-synthesis
- font-variant
- gap
- grid
- grid-area
- grid-column
- grid-row
- grid-template
- inset
- inset-block
- inset-inline
- list-style
- margin
- margin-block
- margin-inline
- mask
- mask-border
- offset
- outline
- overflow
- overscroll-behavior
- padding
- padding-block
- padding-inline
- place-content
- place-items
- place-self
- position-try
- scroll-margin
- scroll-margin-block
- scroll-margin-inline
- scroll-padding
- scroll-padding-block
- scroll-padding-inline
- scroll-timeline
- text-box
- text-decoration
- text-emphasis
- text-wrap
- transition
- view-timeline
- -webkit-text-stroke
- -webkit-border-before
- -webkit-mask-box-image

## See also

- [ماژول آبشار و ارث‌بری CSS](/en-US/docs/Web/CSS/Guides/Cascade)
- [مقدمه‌ای بر نحو CSS: اعلان‌ها، مجموعه‌قوانین و دستورات](/en-US/docs/Web/CSS/Guides/Syntax/Introduction)
- [At-rules](/en-US/docs/Web/CSS/Guides/Syntax/At-rules)
- [ویژگی (Specificity)](/en-US/docs/Web/CSS/Guides/Cascade/Specificity)
- [ارث‌بری (Inheritance)](/en-US/docs/Web/CSS/Guides/Cascade/Inheritance)
- [آشنایی با آبشار CSS](/en-US/docs/Web/CSS/Guides/Cascade/Introduction)
- [یادگیری: مدیریت تعارض‌ها](/en-US/docs/Learn_web_development/Core/Styling_basics/Handling_conflicts)
- [یادگیری: لایه‌های آبشار](/en-US/docs/Learn_web_development/Core/Styling_basics/Cascade_layers)
- [مدل‌های قالب‌بندی بصری](/en-US/docs/Web/CSS/Guides/Display/Visual_formatting_model)
- مقادیر: [initial](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#initial_value), [computed](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#computed_value), [used](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#used_value) و [actual](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#actual_value)
- [نحو تعریف مقدار](/en-US/docs/Web/CSS/Guides/Values_and_units/Value_definition_syntax)