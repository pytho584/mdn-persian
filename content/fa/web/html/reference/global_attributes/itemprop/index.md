---
title: "itemprop HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/itemprop"
translated_by: "n8n + AI"
---

**`itemprop`** یک attribute سراسری است که برای افزودن property به یک item استفاده می‌شود. هر HTML element می‌تواند دارای attribute به نام `itemprop` باشد؛ یک `itemprop` از یک جفت نام-مقدار (name-value pair) تشکیل می‌شود. به هر جفت نام-مقدار یک **property** گفته می‌شود و مجموعه‌ای از یک یا چند property، یک **item** را می‌سازد. مقادیر property یا یک رشته (string) هستند یا یک URL و می‌توانند به عناصر بسیار متنوعی متصل شوند، از جمله `audio`، `embed`، `iframe`، `img`، `link`، `object`، `source`، `track` و `video`.

## مثال‌ها

مثال زیر، کد منبع مجموعه‌ای از عناصر را نشان می‌دهد که با attribute های `itemprop` علامت‌گذاری شده‌اند و به دنبال آن جدولی نمایش‌دهندهٔ داده‌های ساخت‌یافتهٔ حاصل آمده است.

### HTML

```html
<div itemscope itemtype="http://schema.org/Movie">
  <h1 itemprop="name">Avatar</h1>
  <span>
    Director:
    <span itemprop="director">James Cameron</span>
    (born August 16, 1954)
  </span>
  <span itemprop="genre">Science fiction</span>
  <a href="../movies/avatar-theatrical-trailer.html" itemprop="trailer">
    Trailer
  </a>
</div>
```

### داده‌های ساخت‌یافته

<table class="standard-table">
  <tbody>
    <tr>
      <td rowspan="2"> </td>
      <th colspan="2"><strong>آیتم</strong></th>
    </tr>
    <tr>
      <th><strong>نام itemprop</strong></th>
      <th><strong>مقدار itemprop</strong></th>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>name</td>
      <td>Avatar</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>director</td>
      <td>James Cameron</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>genre</td>
      <td>Science fiction</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>trailer</td>
      <td>../movies/avatar-theatrical-trailer.html</td>
    </tr>
  </tbody>
</table>

## Properties

property ها مقادیری دارند که یا رشته هستند یا URL. وقتی مقدار یک رشته، URL باشد، با استفاده از عنصر `a` و attribute «href» آن، عنصر `img` و attribute «src» آن، یا سایر عناصری که به منابع خارجی لینک می‌دهند یا آن‌ها را جاسازی می‌کنند، بیان می‌شود.

### سه property با مقادیر رشته‌ای

```html
<div itemscope>
  <p>My name is <span itemprop="name">Neil</span>.</p>
  <p>My band is called <span itemprop="band">Four Parts Water</span>.</p>
  <p>I am <span itemprop="nationality">British</span>.</p>
</div>
```

### یک property به نام «image» که مقدار آن URL است

```html
<div itemscope>
  <img itemprop="image" src="google-logo.png" alt="Google" />
</div>
```

وقتی یک مقدار رشته‌ای برای انسان به‌راحتی قابل خواندن و درک نیست (مثلاً رشته‌ای طولانی از اعداد و حروف)، می‌توان آن را با attribute «value» عنصر `data` نمایش داد؛ به این ترتیب که نسخهٔ قابل‌فهم برای انسان در محتوای element قرار می‌گیرد (که بخشی از داده‌های ساخت‌یافته نیست — به مثال زیر مراجعه کنید).

### یک item با property که مقدار آن شناسهٔ محصول (product ID) است

این شناسه برای انسان مناسب نیست، بنابراین به جای آن از نام محصول استفاده شده است.

```html
<h1 itemscope>
  <data itemprop="product-id" value="9678AOU879">The Instigator 2000</data>
</h1>
```

برای داده‌های عددی، می‌توان از عنصر `meter` و attribute «value» آن استفاده کرد.

### یک عنصر meter

به همین ترتیب، برای داده‌های مربوط به تاریخ و زمان می‌توان از عنصر `time` و attribute آن یعنی `datetime` استفاده کرد.

### آیتمی با یک property به نام «birthday» که مقدارش یک تاریخ است

```html
<div itemscope>
  I was born on
  <time itemprop="birthday" datetime="1984-05-10">May 10th 1984</time>.
</div>
```

Propertyها می‌توانند گروه‌هایی از جفت‌های نام-مقدار نیز باشند؛ با قرار دادن attribute ای به نام `itemscope` روی عنصری که property را تعریف می‌کند. هر مقدار یا یک رشته است یا یک گروه از جفت‌های نام-مقدار (یعنی یک آیتم).

### یک آیتم بیرونی که یک شخص را نشان می‌دهد و یک آیتم داخلی که یک گروه موسیقی را نشان می‌دهد

```html
<div itemscope>
  <p>Name: <span itemprop="name">Amanda</span></p>
  <p>
    Band:
    <span itemprop="band" itemscope>
      <span itemprop="name">Jazz Band</span>
      (<span itemprop="size">12</span> players)
    </span>
  </p>
</div>
```

آیتم بیرونی بالا دو property دارد: «name» و «band». مقدار «name» برابر «Amanda» است و «band» خودش یک آیتم مستقل با دو property به نام‌های «name» و «size» است. نام گروه «Jazz Band» و اندازه آن «12» است. آیتم بیرونی در این مثال یک آیتم سطح بالای microdata است. به آیتم‌هایی که جزئی از آیتم‌های دیگر نیستند، آیتم‌های سطح بالای microdata می‌گویند.

### جدا کردن همه‌ی propertyها از آیتم‌هایشان

این مثال همان نتیجهٔ مثال قبلی را دارد، اما همهٔ propertyها از آیتم‌هایشان جدا شده‌اند.

```html
<div itemscope id="amanda" itemref="a b"></div>
<p id="a">Name: <span itemprop="name">Amanda</span></p>
<div id="b" itemprop="band" itemscope itemref="c"></div>
<div id="c">
  <p>Band: <span itemprop="name">Jazz Band</span></p>
  <p>Size: <span itemprop="size">12</span> players</p>
</div>
```

این کار همان نتیجهٔ مثال قبلی را می‌دهد. آیتم اول دو property دارد: «name» با مقدار «Amanda» و «band» که مقدارش آیتم دیگری است. آن آیتم دوم دو property دیگر دارد: «name» با مقدار «Jazz Band» و «size» با مقدار «12».

یک آیتم می‌تواند چندین property با نام یکسان و مقادیر متفاوت داشته باشد.

### بستنی با دو طعم

```html
<div itemscope>
  <p>Flavors in my favorite ice cream:</p>
  <ul>
    <li itemprop="flavor">Lemon sorbet</li>
    <li itemprop="flavor">Apricot sorbet</li>
  </ul>
</div>
```

این کار آیتمی با دو property ایجاد می‌کند که هر دو نام «flavor» دارند و مقادیرشان «Lemon sorbet» و «Apricot sorbet» است.

یک عنصر می‌تواند هنگام معرفی یک property، چند property را هم‌زمان معرفی کند تا وقتی برخی از propertyها مقدار یکسانی دارند، از تکرار جلوگیری شود.

### آیتمی با دو property به نام‌های «favorite-color» و «favorite-fruit» که هر دو مقدار «orange» دارند

```html
<div itemscope>
  <span
    itemprop="favorite-color
    favorite-fruit"
    >orange
  </span>
</div>
```

> [!NOTE]
> هیچ ارتباطی بین microdata و محتوای سندی که microdata در آن نشانه‌گذاری شده است وجود ندارد.

### داده‌های ساختاریافتهٔ یکسان با دو روش نشانه‌گذاری متفاوت

هیچ تفاوت معنایی بین دو مثال زیر وجود ندارد.

```html
<figure>
  <img src="castle.jpeg" />
  <figcaption>
    <span itemscope><span itemprop="name">The Castle</span></span> (1986)
  </figcaption>
</figure>
```

```html
<span itemscope><meta itemprop="name" content="The Castle" /></span>
<figure>
  <img src="castle.jpeg" />
  <figcaption>The Castle (1986)</figcaption>
</figure>
```

## نام‌ها و مقادیر

یک **property** مجموعه‌ای نامرتب از tokenهای یکتا است که به حروف بزرگ و کوچک حساس هستند و جفت‌های name-value را نشان می‌دهند. مقدار property باید حداقل یک token داشته باشد. در مثال زیر، هر خانه از داده یک token است.

### مثال‌هایی از نام‌ها

<table class="standard-table">
  <thead>
    <tr>
      <th rowspan="2" scope="col"> </th>
      <th colspan="2" scope="col">Item</th>
    </tr>
    <tr>
      <th scope="col">itemprop <strong>name</strong></th>
      <th scope="col">itemprop <strong>value</strong></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>itemprop</th>
      <td>country</td>
      <td>Ireland</td>
    </tr>
    <tr>
      <th>itemprop</th>
      <td>Option</td>
      <td>2</td>
    </tr>
    <tr>
      <th>itemprop</th>
      <td>https://www.flickr.com/photos/nlireland/6992065114/</td>
      <td>Ring of Kerry</td>
    </tr>
    <tr>
      <th>itemprop</th>
      <td>img</td>
      <td>https://www.flickr.com/photos/nlireland/6992065114/</td>
    </tr>
    <tr>
      <th>itemprop</th>
      <td>website</td>
      <td>flickr</td>
    </tr>
    <tr>
      <th>itemprop</th>
      <td>(token)</td>
      <td>(token)</td>
    </tr>
  </tbody>
</table>

**Tokenها** یا string هستند یا URL. اگر یک item یک URL باشد، به آن **typed item** می‌گویند. در غیر این صورت، یک string است. stringها نمی‌توانند شامل نقطه یا دونقطه باشند (به زیر مراجعه کنید).

1. اگر item از نوع typed باشد، باید یکی از موارد زیر باشد:
   1. یک نام property تعریف‌شده، یا
   2. یک URL معتبر که به تعریف واژگان اشاره می‌کند، یا
   3. یک URL معتبر که به‌عنوان نام property اختصاصی برای item استفاده می‌شود (یعنی خاصیتی که در یک مشخصات عمومی تعریف نشده است)، یا

2. اگر item از نوع typed نباشد، باید:
   1. یک string باشد که شامل هیچ کاراکتر `.` (U+002E FULL STOP) و هیچ کاراکتر `:` (U+003A COLON) نباشد و به‌عنوان نام property اختصاصی برای item استفاده شود (دوباره، خاصیتی که در یک مشخصات عمومی تعریف نشده است).

> [!NOTE]
> قواعد بالا استفاده از کاراکتر «:» را در مقادیر غیر-URL منع می‌کند، زیرا در غیر این صورت نمی‌توان آن‌ها را از URLها تشخیص داد. مقادیری که دارای کاراکتر «.» هستند برای توسعه‌های آینده رزرو شده‌اند. کاراکترهای فاصله هم مجاز نیستند، زیرا در غیر این صورت مقادیر به‌صورت چند token تجزیه می‌شوند.

## مقدار

مقدار property برای یک جفت name-value طبق اولین مورد سازگار در فهرست زیر تعیین می‌شود:

- اگر element دارای attribute به نام `itemscope` باشد
  - مقدار، **item** ساخته‌شده توسط element است.

- اگر element یک `meta` باشد
  - مقدار، مقدار attribute با نام `content` است.

- اگر element از نوع `audio`، `embed`، `iframe`، `img`، `source`، `track` یا `video` باشد
  - مقدار، رشته URL نهایی است که از تجزیه مقدار attribute با نام `src` عنصر نسبت به node document عنصر (بخشی از [Microdata DOM API](/en-US/docs/Web/HTML/Guides/Microdata)) در زمان تنظیم attribute به دست می‌آید.

- اگر element از نوع `a`، `area` یا `link` باشد
  - مقدار، رشته URL نهایی است که از تجزیه مقدار attribute با نام `href` عنصر نسبت به node document عنصر در زمان تنظیم attribute به دست می‌آید.

- اگر element یک `object` باشد
  - مقدار، رشته URL نهایی است که از تجزیه مقدار attribute با نام `data` عنصر نسبت به node document عنصر در زمان تنظیم attribute به دست می‌آید.

- اگر element یک `data` باشد
  - مقدار، مقدار attribute با نام `value` است.

- اگر element یک `meter` باشد
  - مقدار، مقدار attribute با نام `value` است.

- اگر element یک `time` باشد
  - مقدار، مقدار `datetime` است.

در غیر این صورت

- مقدار برابر با `_textContent_` عنصر است.

اگر مقدار یک ویژگی از نوع `URL` باشد، باید آن ویژگی را با یک عنصر URL property (ویژگی URL) مشخص کرد. عناصر URL property عبارتند از: `a`، `area`، `audio`، `embed`، `iframe`، `img`، `link`، `object`، `source`، `track` و `video`.

### ترتیب نام‌ها

نام‌ها نسبت به یکدیگر ترتیب مشخصی ندارند، اما اگر یک نام چندین مقدار داشته باشد، آن مقادیر دارای ترتیب نسبی هستند.

در مثال زیر، ویژگی «a» مقادیر «1» و «2» را _به همین ترتیب_ دارد، اما این که ویژگی «a» قبل از ویژگی «b» بیاید یا نه، اهمیتی ندارد.

```html
<div itemscope>
  <p itemprop="a">1</p>
  <p itemprop="a">2</p>
  <p itemprop="b">test</p>
</div>
```

چند مثال معادل دیگر:

```html
<div itemscope>
  <p itemprop="b">test</p>
  <p itemprop="a">1</p>
  <p itemprop="a">2</p>
</div>
```

```html
<div itemscope>
  <p itemprop="a">1</p>
  <p itemprop="b">test</p>
  <p itemprop="a">2</p>
</div>
```

```html
<div id="x">
  <p itemprop="a">1</p>
</div>
<div itemscope itemref="x">
  <p itemprop="b">test</p>
  <p itemprop="a">2</p>
</div>
```

### نمایش داده‌های ساختاریافته برای یک کتاب

این مثال از ویژگی‌های microdata برای نمایش داده‌های ساختاریافته زیر استفاده می‌کند:

<table class="standard-table">
  <tbody>
    <tr>
      <td rowspan="4">itemscope</td>
      <td>itemtype: itemid</td>
      <td colspan="2">https://schema.org/Book: urn:isbn:0-374-22848-5</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>title</td>
      <td>Owls of the Eastern Ice</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>author</td>
      <td>Jonathan C Slaght</td>
    </tr>
    <tr>
      <td>itemprop</td>
      <td>datePublished</td>
      <td>2020-08-04</td>
    </tr>
  </tbody>
</table>

#### HTML

```html
<dl
  itemscope
  itemtype="https://schema.org/Book"
  itemid="urn:isbn:0-374-22848-5<">
  <dt>Title</dt>
  <dd itemprop="title">Owls of the Eastern Ice</dd>
  <dt>Author</dt>
  <dd itemprop="author">Jonathan C Slaght</dd>
  <dt>Publication date</dt>
  <dd>
    <time itemprop="datePublished" datetime="2020-08-04">August 4 2020</time>
  </dd>
</dl>
```

#### نتیجه

## مشخصات

## همچنین ببینید

- [سایر ویژگی‌های سراسری متفاوت](/en-US/docs/Web/HTML/Reference/Global_attributes)
- سایر ویژگی‌های سراسری مرتبط با microdata:
  - [`itemid`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemid)
  - [`itemref`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemref)
  - [`itemscope`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemscope)
  - [`itemtype`](/en-US/docs/Web/HTML/Reference/Global_attributes/itemtype)