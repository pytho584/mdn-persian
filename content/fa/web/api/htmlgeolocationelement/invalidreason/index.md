---
title: "HTMLGeolocationElement: invalidReason property"
short-title: invalidReason
slug: Web/API/HTMLGeolocationElement/invalidReason
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HTMLGeolocationElement.invalidReason
---

{{APIRef("Navigation API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`invalidReason`** در رابط {{domxref("HTMLGeolocationElement")}}، یک مقدار شمارشی برمی‌گرداند که نشان می‌دهد چرا عنصر مرتبط {{htmlelement("geolocation")}} نامعتبر است (مسدود شده)، در صورتی که چنین باشد.

هنگامی که یک [مسدودکننده](/en-US/docs/Web/HTML/Reference/Elements/geolocation#geolocation_blocking) بر روی یک عنصر `<geolocation>` فعال باشد، آن عنصر نامعتبر است؛ یعنی از کار کردن بازمانده است، خواه به‌صورت موقت یا دائمی، بسته به دلیل.

می‌توانید خاصیت {{domxref("HTMLGeolocationElement.isValid")}} را بررسی کنید تا ببینید آیا عنصر `<geolocation>` معتبر است یا خیر.

## مقدار

رشته خالی (`""`) اگر عنصر مسدودکننده فعالی نداشته باشد، یا یکی از مقادیر زیر (به ترتیب اولویت):

- `illegal_subframe`
  - : عنصر `<geolocation>` داخل یک عنصر {{htmlelement("fencedframe")}} قرار گرفته است.

    مسدودکننده دائمی.

- `unsuccessful_registration`
  - : بیش از سه عنصر `<geolocation>` در همان سند درج شده است.

    مسدودکننده موقت.

- `recently_attached`
  - : عنصر `<geolocation>` به‌تازگی به DOM متصل شده است.

    مسدودکننده در حال انقضا.

- `intersection_changed`
  - : عنصر `<geolocation>` در حال جابه‌جایی است.

    مسدودکننده در حال انقضا.

- `intersection_out_of_viewport_or_clipped`
  - : عنصر `<geolocation>` در خارج یا به‌صورت جزئی در داخل نمای دید (viewport) رندر شده است.

    مسدودکننده موقت.

- `intersection_occluded_or_distorted`
  - : عنصر `<geolocation>` کاملاً در داخل نمای دید رندر شده است، اما به نحوی پوشیده شده یا تحریف شده است، مثلاً پشت محتوای دیگر قرار دارد.

    مسدودکننده موقت.

- `style_invalid`
  - : سبک‌های محدودکننده‌ای روی عنصر `<geolocation>` اعمال شده است (به [محدودیت‌های سبک‌دهی](/en-US/docs/Web/HTML/Reference/Elements/geolocation#styling_restrictions) مراجعه کنید).

    مسدودکننده موقت.

این دلایل نامعتبری به ترتیب اولویت، از بالاترین به پایین‌ترین فهرست شده‌اند.
اگر چند مسدودکننده فعال باشند، مقدار `invalidReason` برگشتی، مقداری خواهد بود که بالاترین اولویت مسدودکننده فعال را نشان می‌دهد.

همچنین توجه کنید که توضیحات بالا شامل یک «نوع مسدودکننده» برای هر دلیل نامعتبری است که یکی از موارد زیر است:

- دائمی
  - : عنصر `<geolocation>` به‌طور دائمی نامعتبر است تا زمانی که توسعه‌دهنده کد را به‌روزرسانی کند تا مسدودکننده رخ ندهد.
- موقت
  - : عنصر `<geolocation>` نامعتبر است تا زمانی که شرط مسدودکننده دیگر رخ ندهد. پس از آن، مسدودکننده موقت به یک مسدودکننده در حال انقضا تبدیل می‌شود.
- در حال انقضا
  - : عنصر `<geolocation>` برای مدت کوتاهی نامعتبر است و پس از آن دوباره معتبر می‌شود.

## مثال‌ها

### استفاده پایه

```html
<geolocation></geolocation>
```

```js
const geo = document.querySelector("geolocation");
console.log(geo.invalidReason);
// ""، به شرطی که عنصر `<geolocation>` به نحوی مسدود نشده باشد
```

### بررسی دلایل نامعتبری

در این مثال، یک کنترل فرم برای اعمال سبک‌های مختلف روی عنصر `<geolocation>` فراهم می‌کنیم که آن را نامعتبر می‌کند. وقتی هر مجموعه سبک اعمال می‌شود، `invalidReason` ارائه‌شده توسط مرورگر را گزارش می‌کنیم.

#### HTML

با قرار دادن یک عنصر `<geolocation>` و یک عنصر {{htmlelement("div")}} شروع می‌کنیم که بعداً اجازه می‌دهیم روی عنصر `<geolocation>` رندر شود.

```html
<geolocation>
  مرورگر شما از عنصر <code>&lt;geolocation&gt;</code> پشتیبانی نمی‌کند.
</geolocation>
<div id="cover">عنصر پوشاننده</div>
```

سپس یک عنصر {{htmlelement("p")}} قرار می‌دهیم که `invalidReason` تولیدشده توسط هر مجموعه سبک را در آن چاپ می‌کنیم.

```html
<p id="reason"></p>
```

در نهایت، یک عنصر {{htmlelement("select")}} قرار می‌دهیم تا کاربر بتواند افکت‌های سبک‌دهی مختلفی را انتخاب کند که عنصر `<geolocation>` را نامعتبر می‌کنند.

```html
<form>
  <label for="invalidate"
    >راهی برای نامعتبر کردن عنصر
    <code>&lt;geolocation&gt;</code> انتخاب کنید:</label
  >
  <select id="invalidate">
    <option value="">هیچ‌کدام</option>
    <option value="move-behind">انتقال به پشت عنصر</option>
    <option value="move-out">انتقال به خارج از نمای دید</option>
    <option value="bad-contrast">کنتراست نامناسب</option>
  </select>
</form>
```

#### CSS

در سبک‌ها، ابتدا به عنصر `<geolocation>` یک {{cssxref("position")}} با مقدار `relative` می‌دهیم تا قابل مکان‌دهی باشد و یک {{cssxref("z-index")}} با مقدار `1`.

```css hidden
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin-left: 50px;
}

geolocation {
  font-size: small;
}

#cover {
  width: 200px;
  height: 50px;
  color: white;
  background-color: darkblue;
  padding: 10px;
}
```

```css
geolocation {
  position: relative;
  z-index: 1;
}
```

سپس، `#cover` خود را که یک `<div>` است با `position: absolute` استایل می‌دهیم و از {{glossary("inset properties")}} برای قرار دادن آن در سمت راست عنصر `<geolocation>` استفاده می‌کنیم. همچنین به آن مقدار `z-index` برابر `2` می‌دهیم تا اگر `<div>` ما در همان ناحیه عنصر `<geolocation>` قرار گیرد، `<div>` در بالا قرار گیرد.

```css
#cover {
  position: absolute;
  top: 72px;
  left: 250px;
  z-index: 2;
}
```

حالا سه کلاس استایل تعریف می‌کنیم که وقتی کاربر گزینه‌های مختلف `<select>` را انتخاب می‌کند، روی عنصر `<geolocation>` اعمال می‌شوند. `.move-behind` آن را پشت `<div>` با شناسه `#cover` منتقل می‌کند، `.move-out` آن را از صفحه خارج می‌کند، و `.bad-contrast` به آن [کنتراست رنگی](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable/Color_contrast) نامناسبی می‌دهد. هر سه این سبک‌ها باعث می‌شوند عنصر `<geolocation>` نامعتبر شود.

```css
.move-behind {
  left: 150px;
}

.move-out {
  right: 250px;
}

.bad-contrast {
  background-color: red;
  color: orange;
}
```

#### JavaScript

در اسکریپت، ابتدا ارجاع‌هایی به عناصر `<geolocation>`، `<div>`، `<p>` و `<select>` می‌گیریم.

```js
const geo = document.querySelector("geolocation");
const coverElem = document.querySelector("#cover");
const reasonElem = document.querySelector("#reason");
const selectElem = document.querySelector("select");
```

سپس، یک شنونده رویداد `input` به عنصر `<select>` اضافه می‌کنیم. وقتی مقدار جدیدی انتخاب شود، یک ویژگی `class` روی عنصر `<geolocation>` برابر با مقدار انتخاب‌شده تنظیم می‌کنیم که یکی از کلاس‌های نامعتبرکننده را اعمال می‌کند. پس از یک تأخیر ۴ ثانیه‌ای، `class` را دوباره به `""` تنظیم می‌کنیم تا عنصر `<geolocation>` به حالت معتبر خود بازگردد.

```js
selectElem.addEventListener("input", () => {
  geo.className = selectElem.value;
  setTimeout(() => {
    geo.className = "";
  }, 4000);
});
```

در نهایت، کدی برای گزارش تغییرات وضعیت اعتبار که هنگام انتخاب مقادیر مختلف رخ می‌دهند اضافه می‌کنیم. با تنظیم متن `<p>` شروع می‌کنیم تا `invalidReason` فعال هنگام بارگذاری اولیه صفحه را شامل شود. سپس یک شنونده رویداد {{domxref("HTMLGeolocationElement.validationstatuschange_event", "validationstatuschange")}} به عنصر `<geolocation>` اضافه می‌کنیم. هر زمان که وضعیت اعتبار تغییر کند، بررسی می‌کنیم که آیا عنصر `<geolocation>` با استفاده از {{domxref("HTMLGeolocationElement.isValid")}} معتبر است یا خیر، و اگر معتبر بود، پیامی تأییدی در متن `<p>` چاپ می‌کنیم. اگر عنصر `<geolocation>` نامعتبر باشد، `invalidReason` را در متن `<p>` چاپ می‌کنیم.

```js
reasonElem.textContent = `دلیل نامعتبری: ${geo.invalidReason}`;

geo.addEventListener("validationstatuschange", () => {
  if (geo.isValid) {
    reasonElem.textContent = `<geolocation> معتبر است`;
  } else {
    reasonElem.textContent = `دلیل نامعتبری: ${geo.invalidReason}`;
  }
});
```

#### نتیجه

این کد را [به‌صورت زنده اجرا کنید](https://mdn.github.io/dom-examples/geolocation-element/exploring-invalid-reasons/) (همچنین [کد منبع کامل](https://github.com/mdn/dom-examples/tree/main/geolocation-element/exploring-invalid-reasons) را ببینید). گزینه‌های مختلف نامعتبرسازی را امتحان کنید تا ببینید در هر مورد کدام دلایل نامعتبری گزارش می‌شوند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر {{htmlelement("geolocation")}}