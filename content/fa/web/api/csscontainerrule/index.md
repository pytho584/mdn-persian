---
title: CSSContainerRule
slug: Web/API/CSSContainerRule
page-type: web-api-interface
browser-compat: api.CSSContainerRule
---

{{ APIRef("CSSOM") }}

رابطهٔ **`CSSContainerRule`** یک قانون CSS {{cssxref("@container")}} را نمایش میدهد.

{{InheritanceDiagram}}

## ویژگیهای نمونه

_ویژگیها را از اجداد خود {{domxref("CSSConditionRule")}}، {{domxref("CSSGroupingRule")}} و {{domxref("CSSRule")}} به ارث میبرد._

- {{domxref("CSSContainerRule.conditions")}} {{ReadOnlyInline}}
  - : یک آرایه از اشیاء را برمیگرداند که هر کدام یک شرط کانتینر را در یک قانون {{cssxref("@container")}} مشخص میکنند.
    این اشیاء دارای یک ویژگی رشتهای `name` و یک ویژگی رشتهای `query` هستند که هر کدام ممکن است در صورت تعریفنشدن، رشتهٔ خالی باشند.
    `name` نام یک کانتینر را نشان میدهد و `query` مجموعهٔ آزمونهای ویژگی را نشان میدهد که باید برای اعمال آن شرط خاص درست باشند.
- {{domxref("CSSContainerRule.containerName")}} {{ReadOnlyInline}}
  - : یک رشته را برمیگرداند که نام شرط کانتینر یک {{cssxref("@container")}} را نشان میدهد، زمانی که فقط یک شرط وجود داشته باشد.
    اگر چند شرط کانتینر وجود داشته باشد، یا اگر فقط یک شرط وجود داشته باشد که نامی را مشخص نکند، این رشته خالی است.
- {{domxref("CSSContainerRule.containerQuery")}} {{ReadOnlyInline}}
  - : یک رشته را برمیگرداند که کوئری کانتینر را برای شرط کانتینر یک {{cssxref("@container")}} نشان میدهد، زمانی که فقط یک شرط وجود داشته باشد.
    این مجموعهٔ آزمونهای ویژگی را نشان میدهد که برای اعمال شرط باید همگی درست باشند.
    اگر چند شرط کانتینر وجود داشته باشد، یا اگر فقط یک شرط وجود داشته باشد که کوئری را مشخص نکند، این رشته خالی است.

## روشهای نمونه

_روش خاصی ندارد؛ روشها را از اجداد خود {{domxref("CSSConditionRule")}}، {{domxref("CSSGroupingRule")}} و {{domxref("CSSRule")}} به ارث میبرد._

## توضیحات

یک شیء `CSSContainerRule` یک قانون {{cssxref("@container")}} را نمایش میدهد.

یک قانون `@container` یک یا چند _شرط کانتینر_ را تعریف میکند که با کاما از هم جدا شدهاند.
هر شرط کانتینر شامل یک «نام» و/یا یک «کوئری» است، جایی که «نام» نام کانتینری را که شرط به آن اعمال میشود نشان میدهد و «کوئری» یک یا چند بررسی ویژگی را که بهصورت منطقی ترکیب شدهاند بر روی ویژگیهای یک کانتینر مشخص میکند.
اگر هر یک از شرایط کانتینر با یک کانتینر مطابقت داشته باشد، استایلهای مشخصشده اعمال میشوند.

> [!NOTE]
> پشتیبانی از چند شرط کانتینر با کلید `conditions` در جدول [سازگاری مرورگر](#browser_compatibility) نشان داده شده است (نسخههای قبلی مشخصات فقط یک شرط کانتینر را مجاز میدانستند).
> این موضوع بر نحوهٔ استفاده از `CSSContainerRule` و `@container` تأثیر میگذارد.

یک مثال ساختگی شامل سه شرط در زیر نشان داده شده است.
این مثال با یک کانتینر به نام `main-content` مطابقت خواهد داشت اگر عرض آن بین `600px` و `800px` باشد، با هر کانتینری که ارتفاع آن بیشتر از `800px` باشد، یا با هر کانتینری به نام `other-content`.

```css
@container main-content (width > 600px) and (width < 800px), (height > 800px), other-content {
  /* اعمال استایل‌ها */
}
```

در مرورگرهای پشتیبان، ویژگی `CSSContainerRule.conditions` یک `@container` را بهصورت آرایهای از اشیاء نشان میدهد که هر کدام یک شرط کانتینر را تعریف میکنند.
اشیاء دارای ویژگیهای `name` و `query` هستند که ممکن است رشتهٔ خالی (`""`) باشند.
ویژگی `conditions` برای مثال `@container` بالا به این شکل خواهد بود:

```js
[
  { name: "main-content", query: "(width > 600px) and (width < 800px)" },
  { name: "", query: "(height > 800px)" },
  { name: "other-content", query: "" },
];
```

ویژگیهای `containerName` و `containerQuery` پیش از پشتیبانی از قوانین کانتینر با چند شرط کانتینر وجود داشتهاند.
برای یک قانون کانتینر با _یک شرط کانتینر_، این ویژگیها شامل نام و کوئری آن شرط هستند (که با ویژگیهای `name` و `query` شیء در آرایهٔ `conditions` مطابقت دارند).
برای یک قانون کانتینر با چند شرط، هر دو به رشتهٔ خالی تنظیم میشوند.

توجه داشته باشید که مرورگرهایی که از ویژگی `conditions` پشتیبانی نمیکنند فقط قوانین کانتینر با یک شرط کانتینر را مجاز میدانند.
یک `@container` با چند شرط کانتینر تجزیه نخواهد شد و هیچ `CSSContainerRule` متناظری ایجاد نخواهد شد.

همچنین میتوانید متن کل شرط را با استفاده از {{domxref("CSSConditionRule.conditionText")}} دریافت کنید.

## مثالها

### آزمایش ویژگی

آزمایش ویژگی میتواند پیچیده باشد، زیرا ممکن است لازم باشد مواردی را مدیریت کنید که `CSSContainerRule` یا `CSSContainerRule.conditions` پشتیبانی نمیشوند، و همچنین مورد خاصی که `conditions` پشتیبانی نمیشود اما چند شرط کانتینر در CSS مشخص شده است.

این کد نشان میدهد که چگونه میتوانید این کار را انجام دهید، با فرض اینکه قبلاً `containerRule` را به دست آوردهاید، یک نمونهٔ `CSSContainerRule` که با یک قانون {{cssxref("@container")}} تعریفشده در CSS صفحه مطابقت دارد (مثال بعدی نشان میدهد که چگونه ممکن است `containerRule` را دریافت کنید).

```js
if (typeof CSSContainerRule === "undefined") {
  // مرورگر از CSSContainerRule (اصلاً) پشتیبانی نمی‌کند
  log("CSSContainerRule در این مرورگر پشتیبانی نمی‌شود.");
} else if (!containerRule) {
  // مرورگر از چند شرط کانتینر پشتیبانی نمی‌کند
  log(
    "هیچ CSSContainerRule ایجاد نشد — ممکن است @container با چند شرط تجزیه نشود.",
  );
} else if ("conditions" in CSSContainerRule.prototype) {
  log("CSSContainerRule.conditions پشتیبانی می‌شود.");
  log("CSSContainerRule.conditions:");
  containerRule.conditions.forEach((item) => {
    const jsonString = JSON.stringify(item);
    log(`  ${jsonString}`);
  });
  log(`CSSContainerRule.conditionText: "${containerRule.conditionText}"`);
} else {
  // @container وجود دارد اما پیش از مشخصات چند شرطی است
  log("CSSContainerRule.conditions پشتیبانی نمی‌شود");
  log(`CSSContainerRule.containerName: "${containerRule.containerName}"`);
  log(`CSSContainerRule.containerQuery: "${containerRule.containerQuery}"`);
  log(`CSSContainerRule.conditionText: "${containerRule.conditionText}"`);
}
```

توجه داشته باشید که اگر تعریف شده باشد، ترجیح میدهیم از اطلاعات موجود در `CSSContainerRule.conditions` بهجای `containerName` و `containerQuery` استفاده کنیم.

### شرط کانتینر بدون نام

مثال زیر یک قانون {{cssxref("@container")}} را تعریف میکند که یک شرط کانتینر بدون نام دارد و ویژگیهای `CSSContainerRule` مرتبط را نمایش میدهد.
CSS همانند مثال `@container` [تنظیم استایلها بر اساس اندازهٔ کانتینر](/en-US/docs/Web/CSS/Reference/At-rules/@container#setting_styles_based_on_a_containers_size) است.

توجه داشته باشید که کد ثبت نتایج ما چندان مرتبط نیست، بنابراین پنهان شده است.

```html hidden
<pre id="log"></pre>
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```css hidden
#log {
  height: 100px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

#### HTML

ابتدا HTML را برای یک `card` که درون یک `post` قرار دارد تعریف میکنیم.
این دو با دو عنصر تودرتوی {{htmlelement("div")}} نمایش داده میشوند.

```html
<div class="post">
  <div class="card">
    <h2>عنوان کارت</h2>
    <p>محتوای کارت</p>
  </div>
</div>
```

#### CSS

CSS این مثال در زیر نشان داده شده است.
CSS ابتدا {{cssxref("container-type")}} را برای عنصر کانتینر (`post`) مشخص میکند.
سپس قانون `@container` یک `width`، `background-color` و `font-size` جدید را به کارت اعمال میکند اگر عرض کمتر از `650px` باشد.

```html
<style id="example-styles">
  /* یک زمینهٔ کانتینر بر اساس اندازهٔ درونی */
  .post {
    container-type: inline-size;
  }

  /* اعمال استایل‌ها اگر کانتینر باریک‌تر از 650px باشد */
  @container (width < 650px) {
    .card {
      width: 50%;
      background-color: gray;
      font-size: 1em;
    }
  }
</style>
```

> [!NOTE]
> استایلهای این مثالها در یک عنصر HTML درونخطی {{htmlelement("style")}} با یک `id` تعریف شدهاند تا پیدا کردن برگهٔ سبک صحیح برای کد آسان باشد.
> همچنین میتوانید برگهٔ سبک صحیح را برای هر مثال با استفاده از ایندکس بر اساس تعداد برگههای سبک موجود در سند، یعنی `length` ویژگی `styleSheets` (مثلاً `document.styleSheets[document.styleSheets.length-1]`) پیدا کنید، اما این کار تعیین برگهٔ صحیح برای هر مثال را پیچیدهتر میکند.

#### JavaScript

کد زیر عنصر {{domxref("HTMLStyleElement")}} مرتبط با مثال را با استفاده از `id` آن دریافت میکند و سپس از ویژگی `sheet` آن برای دریافت {{domxref("StyleSheet")}} استفاده میکند.
از `StyleSheet` مجموعهٔ `cssRules` اضافهشده به برگه را دریافت میکنیم.
از آنجایی که `@container` را بهعنوان قانون دوم در بالا اضافه کردیم، میتوانیم به `CSSContainerRule` مرتبط با استفاده از ورودی دوم، با ایندکس "1" در `cssRules` دسترسی پیدا کنیم.

```js
const exampleStylesheet = document.getElementById("example-styles").sheet;
const exampleRules = exampleStylesheet.cssRules;
const containerRule = exampleRules[1]; // یک CSSContainerRule که قانون کانتینر را نشان می‌دهد.
```

در ادامه، از کد آزمایش ویژگی خود از مثال قبلی برای یافتن و ثبت اطلاعاتی که میخواهیم نمایش دهیم استفاده میکنیم.

```js
if (typeof CSSContainerRule === "undefined") {
  // مرورگر از CSSContainerRule (اصلاً) پشتیبانی نمی‌کند
  log("CSSContainerRule در این مرورگر پشتیبانی نمی‌شود.");
} else if (!containerRule) {
  // مرورگر از چند شرط کانتینر پشتیبانی نمی‌کند
  log(
    "هیچ CSSContainerRule ایجاد نشد. این مرورگر از @container با چند شرط پشتیبانی نمی‌کند.",
  );
} else if ("conditions" in CSSContainerRule.prototype) {
  log("CSSContainerRule.conditions پشتیبانی می‌شود.");
  log("CSSContainerRule.conditions:");
  containerRule.conditions.forEach((item) => {
    const jsonString = JSON.stringify(item);
    log(`  ${jsonString}`);
  });
  log(`CSSContainerRule.conditionText: "${containerRule.conditionText}"`);
} else {
  // @container وجود دارد اما پیش از مشخصات چند شرطی است
  log("CSSContainerRule.conditions پشتیبانی نمی‌شود");
  log(`CSSContainerRule.containerName: "${containerRule.containerName}"`);
  log(`CSSContainerRule.containerQuery: "${containerRule.containerQuery}"`);
  log(`CSSContainerRule.conditionText: "${containerRule.conditionText}"`);
}
```

#### نتایج

خروجی مثال در زیر نشان داده شده است.
این خروجی شرط را با استفاده از ویژگی `conditions` در صورت پشتیبانی، یا با `containerName`/`containerQuery` در صورت عدم پشتیبانی فهرست میکند.

{{EmbedLiveSample("شرط کانتینر بدون نام","100%","300px")}}

توجه داشته باشید که `background-color` کارت باید زمانی که عرض کانتینر کوچکتر یا بزرگتر از `650px` میشود تغییر کند.

### شرط کانتینر نامدار

مثال زیر یک قانون {{cssxref("@container")}} را تعریف میکند که شامل یک نام و یک کوئری است و ویژگیهای `CSSContainerRule` مرتبط را نمایش میدهد.

CSS بسیار شبیه به مثال `@container` [ایجاد زمینههای کانتینر نامدار](/en-US/docs/Web/CSS/Reference/At-rules/@container#creating_named_container_contexts) است.
توجه داشته باشید که HTML، کد ثبت و کد بررسی ویژگی را پنهان کردهایم، زیرا آنها مانند مثال قبلی هستند.

```html hidden
<pre id="log"></pre>
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```css hidden
#log {
  height: 100px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

```html hidden
<div class="post">
  <div class="card">
    <h2>عنوان کارت</h2>
    <p>محتوای کارت</p>
  </div>
</div>
```

#### CSS

در این مثال، {{cssxref("@container")}} یک نام کانتینر، یعنی `sidebar`، و همچنین نوع کانتینر را مشخص میکند.
کارت یک اندازهٔ فونت پیشفرض دارد که وقتی در یک `@container` به نام `sidebar` قرار میگیرد و عرض آن بزرگتر یا مساوی `700px` است، بازنویسی میشود.

```html
<style id="example-styles">
  .post {
    container-type: inline-size;
    container-name: sidebar;
  }

  /* استایل‌های پیش‌فرض عنوان برای عنوان کارت */
  .card h2 {
    font-size: 1em;
  }

  @container sidebar (width >= 700px) {
    .card {
      font-size: 2em;
    }
  }
</style>
```

```js hidden
const exampleStylesheet = document.getElementById("example-styles").sheet;
const exampleRules = exampleStylesheet.cssRules;
const containerRule = exampleRules[2]; // یک CSSContainerRule که قانون کانتینر را نشان می‌دهد.

if (typeof CSSContainerRule === "undefined") {
  // مرورگر از CSSContainerRule (اصلاً) پشتیبانی نمی‌کند
  log("CSSContainerRule در این مرورگر پشتیبانی نمی‌شود.");
} else if (!containerRule) {
  // مرورگر از چند شرط کانتینر پشتیبانی نمی‌کند
  log(
    "هیچ CSSContainerRule ایجاد نشد. این مرورگر از @container با چند شرط پشتیبانی نمی‌کند.",
  );
} else if ("conditions" in CSSContainerRule.prototype) {
  log("CSSContainerRule.conditions پشتیبانی می‌شود.");
  log("CSSContainerRule.conditions:");
  containerRule.conditions.forEach((item) => {
    const jsonString = JSON.stringify(item);
    log(`  ${jsonString}`);
  });
  log(`CSSContainerRule.conditionText: "${containerRule.conditionText}"`);
} else {
  // @container وجود دارد اما پیش از مشخصات چند شرطی است
  log("CSSContainerRule.conditions پشتیبانی نمی‌شود");
  log(`CSSContainerRule.containerName: "${containerRule.containerName}"`);
  log(`CSSContainerRule.containerQuery: "${containerRule.containerQuery}"`);
  log(`CSSContainerRule.conditionText: "${containerRule.conditionText}"`);
}
```

#### نتایج

خروجی مثال در زیر نشان داده شده است.
این خروجی شرط را با استفاده از ویژگی `conditions` در صورت پشتیبانی، یا با `containerName`/`containerQuery` در صورت عدم پشتیبانی فهرست میکند.
`conditionText` نیز ثبت میشود و ترکیب این دو رشته را نشان میدهد.

{{EmbedLiveSample("شرط کانتینر نامدار","100%","300px")}}

متن درون `<div>` کارت باید با رسیدن عرض صفحه به `700px` دو برابر شود و با کاهش دوباره به زیر `700px` نصف شود.

### چند شرط کانتینر

مثال زیر یک قانون {{cssxref("@container")}} را تعریف میکند که شامل چند شرط کانتینر است