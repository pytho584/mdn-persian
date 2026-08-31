---
title: "CSSContainerRule: containerName property"
short-title: containerName
slug: Web/API/CSSContainerRule/containerName
page-type: web-api-instance-property
browser-compat: api.CSSContainerRule.containerName
---

{{ APIRef("CSSOM") }}

ویژگی فقط‌خواندنی **`containerName`** در رابط {{domxref("CSSContainerRule")}} نام شرط کانتینر را برای یک قانون کانتینر نشان می‌دهد که فقط یک شرط کانتینر تعریف کرده است. اگر چندین شرط کانتینر وجود داشته باشد، مقدار آن رشتهٔ خالی خواهد بود.

## مقدار

رشته‌ای شامل نام شرط کانتینر تعریف‌شده در یک قانون کانتینر، اما فقط در صورتی که آن قانون فقط یک شرط کانتینر داشته باشد.

اگر نامی تعریف نشده باشد، یا اگر قانون چندین شرط کانتینر تعریف کند، مقدار آن رشتهٔ خالی (`""`) است.

## توضیحات

این ویژگی بخش نامِ شرط کانتینر را در یک at-rule مربوط به {{cssxref("@container")}} که فقط یک شرط کانتینر دارد منعکس می‌کند.

برای مثال، مقدار `containerName` برای {{cssxref("@container")}} زیر برابر با `sidebar` است:

```css
@container sidebar (width >= 700px) {
  /* Styles */
}
```

> [!NOTE]
> مقدار `containerName` توسط {{domxref("CSSContainerRule.conditions")}} جایگزین شده است و باید در مرورگرهای پشتیبان استفاده شود. مرورگرهایی که از `conditions` پشتیبانی نمی‌کنند نمی‌توانند تعریف‌های `@container` با چندین شرط کانتینر را تجزیه کنند.

## مثال‌ها

### استفادهٔ پایه

مثال زیر یک قانون {{cssxref("@container")}} با یک شرط کانتینر واحد تعریف می‌کند و ویژگی‌های {{domxref("CSSContainerRule")}} مرتبط را نمایش می‌دهد. CSS این مثال بسیار شبیه به مثال [ایجاد زمینه‌های کانتینر نام‌دار](/en-US/docs/Web/CSS/Reference/At-rules/@container#creating_named_container_contexts) در مستندات `@container` است.

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

ابتدا HTML مربوط به یک `card` را تعریف می‌کنیم که در یک `post` قرار دارد. این‌ها با دو عنصر تودرتوی {{htmlelement("div")}} نمایش داده می‌شوند.

```html
<div class="post">
  <div class="card">
    <h2>Card title</h2>
    <p>Card content</p>
  </div>
</div>
```

#### CSS

در CSS عنصر کانتینر، نوع کانتینر به همراه یک نام مشخص شده است. کارت یک اندازه قلم پیش‌فرض دارد که اگر `width` آن بزرگ‌تر یا مساوی `700px` باشد، برای `@container` با نام `sidebar` بازنویسی می‌شود.

```html
<style id="example-styles">
  .post {
    container-type: inline-size;
    container-name: sidebar;
  }

  /* Default heading styles for the card title */
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

#### JavaScript

کد زیر عنصر {{domxref("HTMLStyleElement")}} مرتبط با مثال را با استفاده از `id` آن دریافت می‌کند و سپس با ویژگی `sheet` آن، {{domxref("StyleSheet")}} را به دست می‌آورد. از روی `StyleSheet` مجموعه‌ی `cssRules` اضافه‌شده به برگه را دریافت می‌کنیم. از آنجا که `@container` را به عنوان سومین قانون بالا اضافه کرده‌ایم، می‌توانیم با استفاده از سومین ورودی (ایندکس "2") در `cssRules` به `CSSContainerRule` مرتبط دسترسی پیدا کنیم.

```js
const exampleStylesheet = document.getElementById("example-styles").sheet;
const exampleRules = exampleStylesheet.cssRules;
const containerRule = exampleRules[2]; // a CSSContainerRule representing the container rule.
```

سپس از `containerRule` برای ثبت نام اولین شرط کانتینر استفاده می‌کنیم. اگر مرورگر از `CSSContainerRule.conditions` پشتیبانی کند، نام و کوئری را نیز از آن نمایش می‌دهیم.

```js
log(`CSSContainerRule.containerName: "${containerRule.containerName}"`);

if ("conditions" in CSSContainerRule.prototype) {
  log("CSSContainerRule.conditions:");
  containerRule.conditions.forEach((item) => {
    const jsonString = JSON.stringify(item);
    log(`  ${jsonString}`);
  });
}
```

#### نتیجه

خروجی مثال در زیر نشان داده شده است. بخش ثبت‌شده نام تنها شرط کانتینر را با استفاده از `containerName` فهرست می‌کند. همچنین نام و کوئری را با استفاده از ویژگی `conditions` در صورت پشتیبانی نمایش می‌دهد.

{{EmbedLiveSample("Basic usage","100%","300px")}}

توجه کنید که متن داخل `<div>` کارت با رسیدن `width` کانتینر به `700px` دو برابر می‌شود و با کاهش `width` به زیر `700px` دوباره نصف می‌شود.

### چندین شرط کانتینر

مثال زیر تقریباً دقیقاً مشابه مثال قبلی است، با این تفاوت که CSS چندین شرط کانتینر را مشخص می‌کند.

توجه داشته باشید که HTML را پنهان کرده‌ایم چون همانند مثال قبلی است.

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
    <h2>Card title</h2>
    <p>Card content</p>
  </div>
</div>
```

#### CSS

کارت یک اندازه قلم پیش‌فرض دارد که اگر `width` مربوط به `@container` با نام `sidebar` بزرگ‌تر از `700px` باشد، یا اگر کانتینر نام `other-name` را داشته باشد، بازنویسی می‌شود. توجه کنید که این شرط صرفاً برای نشان دادن اثر چند شرط کانتینر ساخته شده است (و رفتار مثال را تغییر نمی‌دهد).

```html
<style id="example-styles">
  .post {
    container-type: inline-size;
    container-name: sidebar;
  }

  /* Default heading styles for the card title */
  .card h2 {
    font-size: 1em;
  }

  @container sidebar (width >= 700px), other-name {
    .card {
      font-size: 2em;
    }
  }
</style>
```

#### JavaScript

کد زیر عنصر {{domxref("HTMLStyleElement")}} مرتبط با مثال را با استفاده از `id` آن دریافت می‌کند و سپس با ویژگی `sheet` آن، {{domxref("StyleSheet")}} را به دست می‌آورد. از روی `StyleSheet` مجموعه‌ی `cssRules` اضافه‌شده به برگه را دریافت می‌کنیم. از آنجا که `@container` را به عنوان سومین قانون بالا اضافه کرده‌ایم، می‌توانیم با استفاده از سومین ورودی (ایندکس "2") در `cssRules` به `CSSContainerRule` مرتبط دسترسی پیدا کنیم.

```js
const exampleStylesheet = document.getElementById("example-styles").sheet;
const exampleRules = exampleStylesheet.cssRules;
const containerRule = exampleRules[2]; // a CSSContainerRule representing the container rule.
```

کد کمی با حالت قبلی متفاوت است، زیرا اگر مرورگر از چند شرط کانتینر پشتیبانی نکند، `containerRule` برابر با `undefined` خواهد بود. بنابراین مقدار `containerName` را فقط در صورتی ثبت می‌کنیم که مرورگر از چند شرط کانتینر پشتیبانی کند — این مقدار رشتهٔ خالی خواهد بود.

```js
if (!containerRule) {
  // Browser doesn't support multiple container conditions
  log(
    "No CSSContainerRule was created. This browser doesn't support @container with multiple conditions.",
  );
} else {
  log(`CSSContainerRule.containerName: "${containerRule.containerName}"`);
}

if ("conditions" in CSSContainerRule.prototype) {
  log("CSSContainerRule.conditions:");
  containerRule.conditions.forEach((item) => {
    const jsonString = JSON.stringify(item);
    log(`  ${jsonString}`);
  });
}
```

برای اطلاعات و مثال‌های بیشتر به [آزمون ویژگی](/en-US/docs/Web/API/CSSContainerRule#feature_testing) در مستندات `CSSContainerRule` مراجعه کنید.

#### نتیجه

خروجی مثال در زیر نشان داده شده است. توجه کنید که اگر مرورگر از چند شرط کانتینر پشتیبانی نکند، قانون اصلاً وجود ندارد. اگر پشتیبانی کند، مقدار `containerName` رشتهٔ خالی است.

{{EmbedLiveSample("Multiple container conditions","100%","250px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی کوتاه‌نویس CSS {{cssxref("container")}}
- [ماژول محصورسازی CSS](/en-US/docs/Web/CSS/Guides/Containment)
- [Container queries](/en-US/docs/Web/CSS/Guides/Containment/Container_queries)
- [استفاده از کوئری‌های اندازه و سبک کانتینر](/en-US/docs/Web/CSS/Guides/Containment/Container_size_and_style_queries)