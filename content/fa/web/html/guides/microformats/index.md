---
title: "Using microformats in HTML"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Microformats"
translated_by: "n8n + AI"
---

# استفاده از میکروفرمت‌ها در HTML

[_Microformats_](https://microformats.org/wiki/Main_Page) استانداردهایی هستند که برای جاسازی معنا (semantics) و داده‌های ساختیافته در HTML به کار می‌روند. این استانداردها یک API در اختیار برنامه‌های وب اجتماعی، موتورهای جستجو، جمع‌آوری‌کننده‌های محتوا (aggregators) و سایر ابزارها قرار می‌دهند. این الگوهای کوچک HTML برای نشانه‌گذاری موجودیت‌هایی مانند افراد، سازمان‌ها، رویدادها و مکان‌ها استفاده می‌شوند؛ از اطلاعات پایه گرفته تا اطلاعات تخصصی.

- برای ایجاد یک شیء میکروفرمت، از نام کلاس‌های `h-*` در ویژگی `class` استفاده می‌شود.
- برای افزودن یک ویژگی (property) به شیء، نام کلاس‌های `p-*`، `u-*`، `dt-*` و `e-*` روی یکی از فرزندان (descendants) آن شیء به کار می‌رود.

میکروفرمت‌ها از واژگان پشتیبان (supporting vocabularies) برای توصیف اشیاء و از جفت‌های نام-مقدار برای تعیین مقادیر ویژگی‌ها استفاده می‌کنند. ویژگی‌ها در ویژگی‌های `class` قرار می‌گیرند که می‌توان به هر المان HTML اضافه کرد، و مقادیر داده‌ها از محتوای المان‌های HTML و ویژگی‌های معنایی آنها استخراج می‌شوند.

میکروفرمت‌های نسخه ۲ (گاهی mf2 نامیده می‌شود) نسخه‌ای به‌روز از میکروفرمت‌ها است که روشی برای نشانه‌گذاری نحو (syntax) و واژگان ساختاریافته HTML ارائه می‌دهد؛ روشی ساده‌تر از رویکردهای قبلی مانند RDFa و microdata که نیاز به یادگیری ویژگی‌های جدید داشتند.

برای میکروفرمت‌های نسخه ۲، [کتابخانه‌های متن‌باز تحلیل‌گر (parser) برای بیشتر زبان‌ها](https://microformats.org/wiki/microformats2#Parsers) وجود دارد.

## نحوه کار میکروفرمت‌ها

نویسنده یک صفحه وب می‌تواند میکروفرمت‌ها را به HTML خود اضافه کند. برای مثال اگر بخواهد خودش را معرفی کند، می‌تواند از یک [h-card](https://microformats.org/wiki/h-card) مانند زیر استفاده کند:

### مثال HTML

```html
<a class="h-card" href="https://alice.example.com">Alice Blogger</a>
```

وقتی یک تحلیل‌گر با این داده مواجه می‌شود، متوجه می‌شود که این صفحه شامل یک «کارت» (card) است که یک شخص یا سازمان به نام `Alice Blogger` و با آدرس `https://alice.example.com/` را توصیف می‌کند. تحلیل‌گر این داده را از طریق APIهایی در دسترس قرار می‌دهد که برای کاربردهای مختلف قابل استفاده هستند. مثلاً یک برنامه می‌تواند صفحه را برای یافتن یک h-card اسکن کند و از آن به عنوان اطلاعات پروفایل شخصی که در یک سرویس ثبت‌نام کرده استفاده کند.

همانطور که در این مثال می‌بینید، برخی الگوهای نشانه‌گذاری فقط به یک نام کلاس ریشه (microformat root class name) نیاز دارند تا تحلیل‌گر بتواند ویژگی‌های عمومی مانند `name`، `url` و `photo` را پیدا کند.

## موارد استفاده از میکروفرمت‌ها

میکروفرمت‌ها کاربردهای زیادی دارند. اول از همه، [استاندارد Webmention](https://webmention.net/draft/) از میکروفرمت‌ها برای ارسال پیام‌ها و نظرات از یک سایت به سایت دیگر استفاده می‌کند. مشخصات Webmention ویژگی‌های خاصی را تعریف می‌کند که سایت‌ها می‌توانند منتشر و مصرف کنند تا یک روش غنی و تعامل‌پذیر برای انتشار پیام و نظر ایجاد شود. میکروفرمت‌ها را می‌توان همراه با Webmention به کار برد تا واکنش‌های اجتماعی مثل لایک، بازنشر (repost) و بوک‌مارک از یک سایت به سایت دیگر ارسال شود.

میکروفرمت‌ها همچنین اشتراک‌گذاری آسان محتوا بین سایت‌ها (syndication) را ممکن می‌کنند. یک جمع‌آوری‌کننده (aggregator) می‌تواند صفحه‌ای که میکروفرمت‌ها در آن منتشر شده را تحلیل کند تا اطلاعاتی مانند عنوان پست، متن پست و نویسنده آن را پیدا کند. سپس این جمع‌آوری‌کننده می‌تواند از اطلاعات معنایی جمع‌آوری‌شده برای نمایش یک نتیجه در سایت خود استفاده کند. به عنوان مثال، خبرخوان‌ها و انجمن‌های بحث می‌توانند ارسال محتوا را تسهیل کنند و از میکروفرمت‌ها برای استخراج دقیق محتوای مرتبط از یک صفحه بهره ببرند. علاوه بر این، یک وب‌سایت می‌تواند از میکروفرمت‌ها برای ارسال درخواست‌های ساختاریافته به اشخاص ثالث (مثل شبکه‌های اجتماعی) جهت انتشار محتوا استفاده کند.

همه موتورهای جستجوی اصلی از خواندن و تفسیر میکروفرمت‌ها پشتیبانی می‌کنند. موتورهای جستجو از دسترسی مستقیم به این داده‌های ساختاریافته سود زیادی می‌برند، زیرا به آنها امکان می‌دهد اطلاعات موجود در صفحات وب را درک کنند. با این اطلاعات، موتورهای جستجو می‌توانند نتایج مرتبط‌تری به کاربران ارائه دهند. برخی موتورهای جستجو ممکن است بر اساس داده‌های میکروفرمت‌ها، قطعات ویژه‌ای مانند امتیاز ستاره‌ای (star ratings) را در نتایج جستجو نمایش دهند.

علاوه بر اینکه میکروفرمت‌ها (microformats) ماشین‌خوان هستند، به‌گونه‌ای طراحی شده‌اند که انسان‌ها هم به‌راحتی بتوانند آن‌ها را بخوانند. این رویکرد درک و نگهداری داده‌های میکروفرمت را برای افراد ساده می‌کند.

## پیشوندهای میکروفرمت

همهٔ میکروفرمت‌ها از یک ریشه (root) و مجموعه‌ای از propertyها تشکیل شده‌اند. همهٔ propertyها اختیاری هستند و می‌توانند چندمقداره باشند؛ برنامه‌هایی که به یک مقدار واحد نیاز دارند می‌توانند از اولین نمونهٔ یک property استفاده کنند. داده‌های سلسله‌مراتبی با میکروفرمت‌های تو در تو نمایش داده می‌شوند که معمولاً خودشان به‌عنوان مقدار property عمل می‌کنند.

همهٔ نام کلاس‌های میکروفرمت از پیشوندها استفاده می‌کنند. پیشوندها از نظر syntax مستقل از vocabularies هستند که به‌طور جداگانه توسعه داده می‌شوند.

- **«h-\*» برای نام کلاس‌های ریشه**، مانند «h-card»، «h-entry»، «h-feed» و بسیاری دیگر. این کلاس‌های ریشه‌ی سطح بالا معمولاً یک نوع و vocabularies متناظر مورد انتظار از propertyها را نشان می‌دهند. برای مثال:
  - [h-card](https://microformats.org/wiki/h-card) یک شخص یا سازمان را توصیف می‌کند.
  - [h-entry](https://microformats.org/wiki/h-entry) محتوای آنلاین دوره‌ای یا دارای تاریخ مانند پست وبلاگ را توصیف می‌کند.
  - [h-feed](https://microformats.org/wiki/h-feed) یک جریان یا فید از پست‌ها را توصیف می‌کند.
  - می‌توانید بسیاری [vocabularies دیگر را در ویکی microformats2](https://microformats.org/wiki/microformats2#v2_vocabularies) پیدا کنید.

- **«p-\*» برای propertyهای متنی ساده**، مانند «p-name»، «p-summary»
  - پردازش عام متن ساده؛ به‌طور کلی متن element. در برخی elementهای HTML ابتدا از attributeهای خاص استفاده کنید، مانند img/alt، abbr/title.

- **«u-\*» برای propertyهای URL**، مانند «u-url»، «u-photo»، «u-logo»
  - پردازش ویژه: attributeهای element مانند a/href، img/src، object/data و غیره نسبت به محتوای element اولویت دارند.

- **«dt-\*» برای propertyهای datetime**، مانند «dt-start»، «dt-end»، «dt-bday»
  - پردازش ویژه: attribute دیتاتایم در element تایم، [value-class-pattern](https://microformats.org/wiki/value-class-pattern) و پردازش جداگانهٔ مقدار تاریخ و زمان برای خوانایی بهتر.

- **«e-\*» برای propertyهای درخت element** که در آن کل سلسله‌مراتب عناصر درون‌بر، مقدار property است، مانند «e-content». پیشوند «e-» را می‌توان به صورت یادآوری با «element tree» (درخت المان)، «embedded markup» (مارکاپ جاسازی‌شده) یا «encapsulated markup» (مارکاپ محصور) به خاطر سپرد.

## چند مثال از میکروفرمت‌ها

### h-card

میکروفرمت [h-card](https://microformats.org/wiki/h-card) یک شخص یا سازمان را نمایش می‌دهد.

مقدار هر property در HTML با استفاده از attribute کلاس (class) تعریف می‌شود؛ هر element می‌تواند این attribute را داشته باشد.

#### مثال h-card

```html
<p class="h-card">
  <img class="u-photo" src="https://example.org/photo.png" alt="" />
  <a class="p-name u-url" href="https://example.org">Joe Bloggs</a>
  <a class="u-email" href="mailto:jbloggs@example.com">jbloggs@example.com</a>,
  <span class="p-street-address">17 Austerstræti</span>
  <span class="p-locality">Reykjavík</span>
  <span class="p-country-name">Iceland</span>
</p>
```

| Property               | Description                                                    |
| ---------------------- | -------------------------------------------------------------- |
| **`p-name`**           | نام کامل/فرمت‌شده شخص یا سازمان.                               |
| **`u-email`**          | آدرس ایمیل                                                      |
| **`u-photo`**          | عکسی از شخص یا سازمان                                           |
| **`u-url`**            | صفحه اصلی یا URL دیگری که نمایانگر شخص یا سازمان است             |
| **`u-uid`**            | شناسه یکتای جهانی، ترجیحاً URL متعارف                           |
| **`p-street-address`** | شماره خیابان + نام                                              |
| **`p-locality`**       | شهر/شهرک/روستا                                                  |
| **`p-country-name`**   | نام کشور                                                        |

#### مثال h-card تو در تو

```html
<div class="h-card">
  <a class="p-name u-url" href="https://blog.lizardwrangler.com/">
    Mitchell Baker
  </a>
  (<a class="p-org h-card" href="https://mozilla.org/">Mozilla Foundation</a>)
</div>
```

JSON تجزیه‌شده:

```json
{
  "items": [
    {
      "type": ["h-card"],
      "properties": {
        "name": ["Mitchell Baker"],
        "url": ["https://blog.lizardwrangler.com/"],
        "org": [
          {
            "value": "Mozilla Foundation",
            "type": ["h-card"],
            "properties": {
              "name": ["Mozilla Foundation"],
              "url": ["https://mozilla.org/"]
            }
          }
        ]
      }
    }
  ]
}
```

در این مثال، یک h-card هم برای شخص و هم برای سازمانی که او نمایندگی می‌کند تعریف شده است. وابستگی شخص به سازمان مرتبط را با استفاده از ویژگی `p-org` مشخص می‌کنیم.

توجه: h-card تو در تو، دقیقاً مثل هر h-card دیگری که فقط class ریشه دارد و روی یک `<a href>` قرار می‌گیرد، ویژگی‌های `name` و `url` را به‌صورت ضمنی دریافت می‌کند.

### h-entry

ریزفرمت [h-entry](https://microformats.org/wiki/h-entry) محتوای دوره‌ای یا تاریخ‌دار را در وب نمایش می‌دهد. h-entry اغلب برای محتوایی استفاده می‌شود که قصد انتشار آن‌ها در جاهای دیگر را دارید؛ مثل پست‌های وبلاگ و یادداشت‌های کوتاه.

مثال h-entry به‌عنوان یک پست وبلاگ:

```html
<article class="h-entry">
  <h1 class="p-name">Microformats are amazing</h1>
  <p>
    Published by
    <a class="p-author h-card" href="https://example.com">W. Developer</a> on
    <time class="dt-published" datetime="2013-06-13 12:00:00">
      13<sup>th</sup> June 2013
    </time>
  </p>

  <p class="p-summary">In which I extoll the virtues of using microformats.</p>

  <div class="e-content">
    <p>Blah blah blah</p>
  </div>
</article>
```

#### ویژگی‌ها

| ویژگی             | توضیحات                                        |
| ----------------- | ---------------------------------------------- |
| **`p-name`**      | نام/عنوان نوشته                                |
| **`p-author`**    | نویسندهٔ نوشته؛ به‌صورت اختیاری با h-card تو در تو |
| **`dt-published`**| زمان انتشار نوشته                              |
| **`p-summary`**   | خلاصهٔ کوتاه نوشته                             |
| **`e-content`**   | محتوای کامل نوشته                              |

#### مثال تجزیه‌شدهٔ h-entry برای پاسخ

```html
<div class="h-entry">
  <p>
    <span class="p-author h-card">
      <a href="https://quickthoughts.jgregorymcverry.com/profile/jgmac1106">
        <img
          class="u-photo"
          alt="Greg McVerry"
          src="https://quickthoughts.jgregorymcverry.com/file/2d6c9cfed7ac8e849f492b5bc7e6a630/thumb.jpg" />
      </a>
      <a
        class="p-name u-url"
        href="https://quickthoughts.jgregorymcverry.com/profile/jgmac1106">
        Greg McVerry
      </a>
    </span>
    Replied to
    <a
      class="u-in-reply-to"
      href="https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Microformats">
      a post on <strong>developer.mozilla.org</strong>
    </a>
    :
  </p>
  <p class="p-name e-content">
    Hey thanks for making this microformats resource
  </p>
  <p>
    <a href="https://quickthoughts.jgregorymcverry.com/profile/jgmac1106">
      Greg McVerry
    </a>
    published this
    <a
      class="u-url url"
      href="https://quickthoughts.jgregorymcverry.com/2019/05/31/hey-thanks-for-making-this-microformats-resource">
      <time class="dt-published" datetime="2019-05-31T14:19:09+0000">
        31 May 2019
      </time>
    </a>
  </p>
</div>
```

```json
{
  "items": [
    {
      "type": ["h-entry"],
      "properties": {
        "in-reply-to": [
          "https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Microformats"
        ],
        "name": ["Hey thanks for making this microformats resource"],
        "url": [
          "https://quickthoughts.jgregorymcverry.com/2019/05/31/hey-thanks-for-making-this-microformats-resource"
        ],
        "published": ["2019-05-31T14:19:09+0000"],
        "content": [
          {
            "html": "Hey thanks for making this microformats resource",
            "value": "Hey thanks for making this microformats resource",
            "lang": "en"
          }
        ],
        "author": [
          {
            "type": ["h-card"],
            "properties": {
              "name": ["Greg McVerry"],
              "photo": [
                "https://quickthoughts.jgregorymcverry.com/file/2d6c9cfed7ac8e849f492b5bc7e6a630/thumb.jpg"
              ],
              "url": [
                "https://quickthoughts.jgregorymcverry.com/profile/jgmac1106"
              ]
            },
            "lang": "en",
            "value": "Greg McVerry"
          }
        ]
      },
      "lang": "en"
    }
  ]
}
```

### h-feed

[h-feed](https://microformats.org/wiki/h-feed) یک جریان یا فید از پست‌های [h-entry](https://microformats.org/wiki/h-entry) است؛ مانند پست‌های کامل در صفحهٔ اصلی یا صفحات آرشیو، یا خلاصه‌ها و فهرست‌های کوتاه دیگری از پست‌ها.

#### مثال h-feed

```html
<div class="h-feed">
  <h1 class="p-name">Microformats Blogs</h1>
  <article class="h-entry">
    <h2 class="p-name">Microformats are amazing</h2>
    <p>
      Published by
      <a class="p-author h-card" href="https://example.com">W. Developer</a> on
      <time class="dt-published" datetime="2013-06-13 12:00:00">
        13<sup>th</sup> June 2013
      </time>
    </p>
    <p class="p-summary">
      In which I extoll the virtues of using microformats.
    </p>
    <div class="e-content"><p>Blah blah blah</p></div>
  </article>
</div>
```

#### ویژگی‌ها

| ویژگی | توضیحات |
| -------------- | ---------------------------------------------- |
| **`p-name`**   | نام فید |
| **`p-author`** | نویسندهٔ فید؛ به‌صورت اختیاری می‌تواند شامل h-card باشد |

#### فرزندان

<table class="standard-table">
  <tbody>
    <tr>
      <td><strong>h-entry تودرتو</strong></td>
      <td></td>
    </tr>
    <tr>
      <td>اشیایی که آیتم‌های فید را نمایش می‌دهند</td>
      <td></td>
    </tr>
  </tbody>
</table>

### h-event

`h-event` برای رویدادهای وب استفاده می‌شود. این کلاس معمولاً هم در فهرست رویدادها و هم در صفحه‌های مربوط به یک رویداد خاص به کار می‌رود.

```html
<div class="h-event">
  <h1 class="p-name">Microformats Meetup</h1>
  <p>
    From
    <time class="dt-start" datetime="2013-06-30 12:00">
      30<sup>th</sup> June 2013, 12:00
    </time>
    to <time class="dt-end" datetime="2013-06-30 18:00">18:00</time> at
    <span class="p-location">Some bar in SF</span>
  </p>
  <p class="p-summary">
    Get together and discuss all things microformats-related.
  </p>
</div>
```

#### ویژگی‌ها

| ویژگی | توضیحات |
| ---------------- | ------------------------------------------------------- |
| **`p-name`**     | نام رویداد (یا عنوان) |
| **`p-summary`**  | خلاصه‌ای کوتاه از رویداد |
| **`dt-start`**   | تاریخ و زمان شروع رویداد |
| **`dt-end`**     | تاریخ و زمان پایان رویداد |
| **`p-location`** | محل برگزاری رویداد؛ به‌صورت اختیاری می‌تواند h-card تعبیه‌شده باشد |

#### مثال تجزیه‌شدهٔ h-event

```markdown
```html
<div class="h-event">
  <h2 class="p-name">IndieWeb Summit</h2>
  <time class="dt-start" datetime="2019-06-29T09:00:00-07:00">
    June 29, 2019 at 9:00am (-0700)
  </time>
  <br />through
  <time class="dt-end" datetime="2019-06-30T18:00:00-07:00">
    June 30, 2019 at 6:00pm (-0700)
  </time>
  <br />
  <div class="p-location h-card">
    <div>
      <span class="p-name">Mozilla</span>
    </div>
    <div>
      <span class="p-street-address">1120 NW Couch St</span>,
      <span class="p-locality">Portland</span>,
      <span class="p-region">Oregon</span>,
      <span class="p-country">US</span>
    </div>
    <data class="p-latitude" value="45.52345"></data>
    <data class="p-longitude" value="-122.682677"></data>
  </div>
  <div class="e-content">Come join us</div>
  <div>
    <span class="p-author h-card">
      <a class="u-url p-name" href="https://aaronparecki.com">Aaron Parecki</a>
    </span>
    Published this
    <a href="https://aaronparecki.com/2019/06/29/1/" class="u-url">event </a>on
    <time class="dt published" datetime="2019-05-25T18:00:00-07:00">
      May 5th, 2019
    </time>
  </div>
</div>
```

```json
{
  "items": [
    {
      "type": ["h-event"],
      "properties": {
        "name": ["IndieWeb Summit"],
        "url": ["https://aaronparecki.com/2019/06/29/1/"],
        "author": [
          {
            "type": ["h-card"],
            "properties": {
              "name": ["Aaron Parecki"],
              "url": ["https://aaronparecki.com"]
            },
            "lang": "en",
            "value": "Aaron Parecki"
          }
        ],
        "start": ["2019-06-29T09:00:00-07:00"],
        "end": ["2019-06-30T18:00:00-07:00"],
        "published": ["2019-05-25T18:00:00-07:00"],
        "content": [
          {
            "html": "Come join us",
            "value": "Come join us",
            "lang": "en"
          }
        ],
        "location": [
          {
            "type": ["h-card"],
            "properties": {
              "name": ["Mozilla"],
              "p-street-address": ["1120 NW Couch St"],
              "locality": ["Portland"],
              "region": ["Oregon"],
              "country": ["US"],
              "latitude": ["45.52345"],
              "longitude": ["-122.682677"]
            },
            "lang": "en",
            "value": "Mozilla"
          }
        ]
      },
      "lang": "en"
    }
  ]
}
```

## مثال‌هایی از ویژگی `rel` در Microformats

برخی از microformatsها با استفاده از ویژگی مخصوص `rel=` به یک صفحه اعمال می‌شوند. این microformatsها رابطه بین سند فعلی و سند مرتبط را توصیف می‌کنند. برای مشاهده فهرست کامل آن‌ها، به [ویژگی rel](https://microformats.org/wiki/rel-values) در ویکی microformats مراجعه کنید.

### rel=author

این ویژگی (attribute) مشخص می‌کند که سند مرتبط، نویسنده صفحه فعلی را معرفی می‌کند.

```html
<a rel="author" href="https://jamesg.blog">James Gallagher</a>
```

### rel=license

این ویژگی مشخص می‌کند که سند مرتبط شامل مجوز (license) انتشار صفحه فعلی است.

```html
<a rel="license" href="https://mit-license.org/">MIT License</a>
```

### rel=nofollow

این ویژگی مشخص می‌کند که سند مرتبط نباید توسط الگوریتم‌های رتبه‌بندی موتورهای جستجو که ممکن است از صفحه فعلی سرچشمه بگیرند، وزنی دریافت کند. این کار مفید است، زیرا از وزن‌دهی بیش از حد الگوریتم‌های گراف لینک به یک صفحه پس از مشاهده یک لینک به سند جلوگیری می‌کند.

```html
<a rel="nofollow" href="https://jamesg.blog">James Gallagher</a>
```

## سازگاری مرورگر

این قابلیت در همه مرورگرهایی که از ویژگی `class` و DOM API آن پشتیبانی می‌کنند، در دسترس است.

## همچنین ببینید
```

- [class attribute](/en-US/docs/Web/HTML/Reference/Global_attributes/class)
- [Microformat](https://en.wikipedia.org/wiki/Microformat) در ویکی‌پدیا
- [وب‌سایت رسمی Microformats](https://microformats.org/wiki/Main_Page)
- [پشتیبانی موتورهای جستجو](https://microformats.org/wiki/search_engines) در وب‌سایت رسمی Microformats
- [Microformats در IndieWebCamp](https://indieweb.org/microformats)