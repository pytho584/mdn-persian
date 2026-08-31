---
title: "CSSContainerRule: conditions property"
short-title: conditions
slug: Web/API/CSSContainerRule/conditions
page-type: web-api-instance-property
browser-compat: api.CSSContainerRule.conditions
---

{{ APIRef("CSSOM") }}

ویژگی فقط‌خواندنی **`conditions`** از رابط {{domxref("CSSContainerRule")}}، قانون at-rule مرتبطِ {{cssxref("@container")}} را به‌صورت آرایه‌ای از اشیاء نمایش می‌دهد که هر شیء نمایانگر یک شرط ظرف (container condition) است.

## مقدار

آرایه‌ای از اشیاء که هر شیء به شکل زیر است:

```js
({ name: "<container-name>", query: "<container-query>" });
```

یا `name` یا `query` ممکن است رشتهٔ خالی باشد، اما هر دو نه.

## توضیحات

ویژگی **`conditions`**، قانون at-rule مرتبطِ {{cssxref("@container")}} را به‌صورت آرایه‌ای از اشیاء نمایش می‌دهد.

هر شیء یک شرط ظرف را به‌صورت یک ویژگی رشته‌ای `name` و یک ویژگی رشته‌ای `query` نشان می‌دهد؛ هرکدام اگر تعریف نشده باشند می‌توانند رشتهٔ خالی باشند. `name` نام ظرف را نشان می‌دهد و رشتهٔ `query` مجموعهٔ آزمون‌های ویژگی را نشان می‌دهد که باید درست باشند تا آن شرط ظرفِ خاص برقرار شود.

برای مثال، با توجه به {{cssxref("@container")}} زیر:

```css
@container sidebar (width >= 700px), (height >= 400px) {
  /* Styles */
}
```

مقدار `conditions` آرایه‌ای مانند زیر خواهد بود:

```js
[
  { name: "sidebar", query: "(width >= 700px)" },
  { name: "", query: "(height >= 400px)" },
];
```

## مثال‌ها

همچنین [مثال‌ها](/en-US/docs/Web/API/CSSContainerRule#examples) را در `CSSContainerRule` ببینید.

### استفادهٔ پایه

این مثال نشان می‌دهد که چگونه چند شرط ظرف در ویژگی `conditions` نمایش داده می‌شوند.

توجه داشته باشید که کد ثبت (logging) را پنهان کرده‌ایم، زیرا مرتبط نیست.

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

ابتدا HTML یک `card` را که درون یک `post` قرار دارد تعریف می‌کنیم. این‌ها با دو عنصر تودرتوی {{htmlelement("div")}} نمایش داده می‌شوند.

```html
<div class="post">
  <div class="card">
    <h2>Card title</h2>
    <p>Card content</p>
  </div>
</div>
```

#### CSS

CSS عنصر ظرف، نوع ظرف را مشخص می‌کند و همچنین ممکن است یک نام را مشخص کند. کارت یک اندازهٔ فونت پیش‌فرض دارد که وقتی درون یک `@container` با نام `sidebar` قرار گیرد و عرض آن بزرگ‌تر یا مساوی `700px` باشد، یا وقتی درون ظرفی به نام `other-name` باشد، بازنویسی می‌شود. توجه داشته باشید که این شرط صرفاً برای نشان دادن نحوهٔ نمایش چند شرط ساخته شده است (`other-name` در واقع هیچ کاری انجام نمی‌دهد).

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

#### جاوااسکریپت

کد زیر، {{domxref("HTMLStyleElement")}} مرتبط با مثال را با استفاده از `id` آن دریافت می‌کند و سپس از ویژگی `sheet` آن برای به‌دست آوردن {{domxref("StyleSheet")}} استفاده می‌کند. از روی `StyleSheet`، مجموعهٔ `cssRules` اضافه‌شده به برگهٔ سبک را دریافت می‌کنیم. از آنجایی که `@container` را به‌عنوان سومین قانون در بالا اضافه کردیم، می‌توانیم به `CSSContainerRule` مرتبط از طریق سومین ورودی (ایندکس «2») در `cssRules` دسترسی پیدا کنیم.

```js
const exampleStylesheet = document.getElementById("example-styles").sheet;
const exampleRules = exampleStylesheet.cssRules;
const containerRule = exampleRules[2]; // a CSSContainerRule representing the container rule.
```

سپس از `containerRule` استفاده می‌کنیم تا مقدار ویژگی `conditions` را ثبت کنیم.

```js
if ("conditions" in CSSContainerRule.prototype) {
  log("CSSContainerRule.conditions:");
  containerRule.conditions.forEach((item) => {
    const jsonString = JSON.stringify(item);
    log(`  ${jsonString}`);
  });
} else {
  log("CSSContainerRule.conditions is not supported.");
}
```

> [!NOTE]
> در مرورگرهایی که از `conditions` پشتیبانی نمی‌کنند، ممکن است بتوانید از {{domxref("CSSContainerRule.containerName")}} و {{domxref("CSSContainerRule.containerQuery")}} استفاده کنید، به شرطی که `@container` فقط یک شرط ظرف را مشخص کند. برای اطلاعات بیشتر، به مثال [تست ویژگی](/en-US/docs/Web/API/CSSContainerRule#feature_testing) در `CSSContainerRule` مراجعه کنید.

#### نتایج

خروجی مثال در زیر نمایش داده شده است.

{{EmbedLiveSample("Basic usage","100%","300px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی کوتاه‌نویس (shorthand) {{cssxref("container")}} در CSS
- [پیمانهٔ محصورسازی CSS](/en-US/docs/Web/CSS/Guides/Containment)
- [پرس‌وجوهای ظرف](/en-US/docs/Web/CSS/Guides/Containment/Container_queries)
- [استفاده از پرس‌وجوهای اندازه و سبک ظرف](/en-US/docs/Web/CSS/Guides/Containment/Container_size_and_style_queries)