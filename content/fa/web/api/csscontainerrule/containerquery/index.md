---
title: "CSSContainerRule: containerQuery property"
short-title: containerQuery
slug: Web/API/CSSContainerRule/containerQuery
page-type: web-api-instance-property
browser-compat: api.CSSContainerRule.containerQuery
---

{{ APIRef("CSSOM") }}

خاصیت فقط-خواندنی **`containerQuery`** از رابط {{domxref("CSSContainerRule")}}، بخش پرس‌وجو (query) از شرط ظرف (container condition) را برای یک قانون ظرف (container rule) که تنها یک شرط ظرف تعریف می‌کند، نمایش می‌دهد. اگر چندین شرط ظرف وجود داشته باشد، مقدار این خاصیت برابر با رشته خالی خواهد بود.

## مقدار

یک رشته که شامل بخش پرس‌وجوی شرط ظرف تعریف‌شده در یک قانون ظرف است، اما تنها در صورتی که آن قانون فقط یک شرط ظرف داشته باشد. توجه داشته باشید که مقدار ممکن است با رشته اصلی یکسان نباشد، زیرا ممکن است نرمال‌سازی‌هایی مانند حذف فاصله‌های خالی انجام شود. اگر هیچ پرس‌وجویی تعریف نشده باشد، یا اگر قانون چندین شرط ظرف تعریف کند، این مقدار برابر با رشته خالی (`""`) است.

## توضیحات

این خاصیت مقدار بخش پرس‌وجوی شرط ظرف را در یک at-rule {{cssxref("@container")}} متناظر که فقط یک شرط ظرف دارد، منعکس می‌کند. برای مثال، مقدار `containerQuery` برای {{cssxref("@container")}} زیر برابر با `(width >= 700px)` است:

```css
@container sidebar (width >= 700px) {
  /* Styles */
}
```

> [!NOTE]
> مقدار `containerQuery` توسط {{domxref("CSSContainerRule.conditions")}} جایگزین شده است که باید در مرورگرهای پشتیبانی‌کننده استفاده شود. مرورگرهایی که از `conditions` پشتیبانی نمی‌کنند، نمی‌توانند تعاریف `@container` با چندین شرط ظرف را تجزیه کنند.

## مثال‌ها

### استفاده پایه

مثال زیر یک قانون {{cssxref("@container")}} با یک شرط ظرف واحد تعریف می‌کند و ویژگی‌های {{domxref("CSSContainerRule")}} مرتبط را نمایش می‌دهد. CSS بسیار شبیه به مثال «[ایجاد بافت‌های ظرف نام‌گذاری‌شده](/en-US/docs/Web/CSS/Reference/At-rules/@container#creating_named_container_contexts)» در مستندات `@container` است.

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

ابتدا، HTML مربوط به یک `card` (کارت) که درون یک `post` (پست) قرار دارد را تعریف می‌کنیم. این دو عنصر توسط دو عنصر {{htmlelement("div")}} تو در تو نمایش داده می‌شوند.

```html
<div class="post">
  <div class="card">
    <h2>Card title</h2>
    <p>Card content</p>
  </div>
</div>
```

#### CSS

CSS عنصر ظرف، نوع ظرف را به همراه یک نام مشخص می‌کند. کارت دارای یک اندازه قلم پیش‌فرض است که برای `@container` به نام `sidebar` در صورتی که عرض آن بزرگ‌تر یا برابر با `700px` باشد، بازنویسی می‌شود.

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

کد زیر، {{domxref("HTMLStyleElement")}} مرتبط با مثال را با استفاده از `id` آن بازیابی می‌کند و سپس از خاصیت `sheet` آن برای به‌دست‌آوردن {{domxref("StyleSheet")}} استفاده می‌کند. از `StyleSheet` مجموعه قوانین `cssRules` اضافه‌شده به برگه را دریافت می‌کنیم. از آنجایی که `@container` را به عنوان سومین قانون اضافه کرده‌ایم، می‌توانیم با استفاده از سومین ورودی (ایندکس "2") در `cssRules` به `CSSContainerRule` مرتبط دسترسی پیدا کنیم.

```js
const exampleStylesheet = document.getElementById("example-styles").sheet;
const exampleRules = exampleStylesheet.cssRules;
const containerRule = exampleRules[2]; // a CSSContainerRule representing the container rule.
```

سپس از `containerRule` برای ثبت پرس‌وجوی شرط ظرف استفاده می‌کنیم. اگر `CSSContainerRule.conditions` در مرورگر پشتیبانی شود، نام و پرس‌وجو را نیز از آن نمایش می‌دهیم.

```js
log(`CSSContainerRule.containerQuery: "${containerRule.containerQuery}"`);

if ("conditions" in CSSContainerRule.prototype) {
  log("CSSContainerRule.conditions:");
  containerRule.conditions.forEach((item) => {
    const jsonString = JSON.stringify(item);
    log(`  ${jsonString}`);
  });
}
```

#### نتایج

خروجی مثال در زیر نمایش داده شده است. بخش گزارش، پرس‌وجوی تنها شرط ظرف را با استفاده از `containerQuery` فهرست می‌کند. همچنین در صورت پشتیبانی، نام و پرس‌وجو را با استفاده از خاصیت `conditions` نمایش می‌دهد.

{{EmbedLiveSample("Basic usage","100%","320px")}}

متن موجود در `<div>` کارت باید با رسیدن عرض صفحه به `700px` دو برابر شود و با کاهش به زیر `700px` دوباره نصف شود.

### چندین شرط ظرف

مثال زیر تقریباً دقیقاً مشابه مثال قبلی است، با این تفاوت که CSS چندین شرط ظرف را مشخص می‌کند.

توجه داشته باشید که HTML را پنهان کرده‌ایم زیرا همانند مثال قبلی است.

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

کارت دارای یک اندازه قلم پیش‌فرض است که برای `@container` به نام `sidebar` در صورتی که عرض آن بزرگ‌تر یا برابر با `700px` باشد یا اگر ظرف نام `other-name` را داشته باشد، بازنویسی می‌شود. توجه داشته باشید که این شرط برای نشان دادن تأثیر چندین شرط ساخته شده است (بر رفتار مثال تأثیری ندارد).

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

کد زیر، {{domxref("HTMLStyleElement")}} مرتبط با مثال را با استفاده از `id` آن بازیابی می‌کند و سپس از خاصیت `sheet` آن برای به‌دست‌آوردن {{domxref("StyleSheet")}} استفاده می‌کند. از `StyleSheet` مجموعه قوانین `cssRules` اضافه‌شده به برگه را دریافت می‌کنیم. از آنجایی که `@container` را به عنوان سومین قانون اضافه کرده‌ایم، می‌توانیم با استفاده از سومین ورودی (ایندکس "2") در `cssRules` به `CSSContainerRule` مرتبط دسترسی پیدا کنیم.

```js
const exampleStylesheet = document.getElementById("example-styles").sheet;
const exampleRules = exampleStylesheet.cssRules;
const containerRule = exampleRules[2]; // a CSSContainerRule representing the container rule.
```

کد کمی با حالت قبلی تفاوت دارد، زیرا اگر چندین شرط ظرف توسط مرورگر پشتیبانی نشود، `containerRule` برابر با `undefined` خواهد بود. بنابراین فقط در صورتی که مرورگر از چندین شرط ظرف پشتیبانی کند، مقدار `containerQuery` را ثبت می‌کنیم – که در این صورت برابر با رشته خالی خواهد بود.

```js
if (!containerRule) {
  // Browser doesn't support multiple container conditions
  log(
    "No CSSContainerRule was created. This browser doesn't support @container with multiple conditions.",
  );
} else {
  log(`CSSContainerRule.containerQuery: "${containerRule.containerQuery}"`);
}

if ("conditions" in CSSContainerRule.prototype) {
  log("CSSContainerRule.conditions:");
  containerRule.conditions.forEach((item) => {
    const jsonString = JSON.stringify(item);
    log(`  ${jsonString}`);
  });
}
```

برای اطلاعات/مثال‌های بیشتر به [آزمون ویژگی](/en-US/docs/Web/API/CSSContainerRule#feature_testing) در `CSSContainerRule` مراجعه کنید.

#### نتایج

خروجی مثال در زیر نمایش داده شده است. توجه داشته باشید که اگر مرورگر از چندین شرط ظرف پشتیبانی نکند، قانون اصلاً وجود ندارد. در صورت پشتیبانی، مقدار `containerQuery` برابر با رشته خالی است.

{{EmbedLiveSample("Multiple container conditions","100%","250px")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی خلاصه‌نویس CSS {{cssxref("container")}}
- [ماژول محصورسازی CSS](/en-US/docs/Web/CSS/Guides/Containment)
- [پرس‌وجوهای ظرف (Container queries)](/en-US/docs/Web/CSS/Guides/Containment/Container_queries)
- [استفاده از پرس‌وجوهای اندازه و سبک ظرف](/en-US/docs/Web/CSS/Guides/Containment/Container_size_and_style_queries)