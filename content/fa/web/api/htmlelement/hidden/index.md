---
title: "HTMLElement: hidden property"
short-title: hidden
slug: Web/API/HTMLElement/hidden
page-type: web-api-instance-property
browser-compat: api.HTMLElement.hidden
---

{{ APIRef("HTML DOM") }}

خصوصیت **`hidden`** در {{domxref("HTMLElement")}} منعکس‌کنندهٔ مقدار ویژگی [`hidden`](/en-US/docs/Web/HTML/Reference/Global_attributes/hidden) آن عنصر است.

## مقدار

این خصوصیت می‌تواند یکی از سه مقدار زیر را داشته باشد:

- `true`
  - : عنصر پنهان است.
- `false`
  - : عنصر پنهان نیست. این مقدار پیش‌فرض برای ویژگی است.
- `"until-found"`
  - : عنصر «پنهان تا زمان یافتن» است؛ یعنی پنهان است، اما اگر از طریق جستجو در صفحه یافت شود یا با پیمایش به بخشی از صفحه (fragment navigation) به آن دسترسی پیدا شود، نمایان می‌گردد.

برای جزئیات کاربرد این ویژگی، به صفحهٔ ویژگی HTML [`hidden`](/en-US/docs/Web/HTML/Reference/Global_attributes/hidden) که این خصوصیت منعکس‌کنندهٔ آن است مراجعه کنید.

## مثال‌ها

در این مثال، یک بلوک پنهان برای نگهداری پیام «متشکریم» استفاده شده است که پس از موافقت کاربر با یک درخواست غیرمعمول نمایش داده می‌شود.

### HTML

کد HTML شامل دو پنل است: یک پنل خوش‌آمدگویی که از کاربران می‌خواهد موافقت کنند که فوق‌العاده باشند، و یک پنل پیگیری که در ابتدا پنهان است.

```html
<div id="welcome" class="panel">
  <h1>Welcome to my website!</h1>
  <p>By clicking "OK" you agree to be awesome today!</p>
  <button class="button" id="okButton">OK</button>
</div>

<div id="awesome" class="panel" hidden>
  <h1>Thanks!</h1>
  <p>Thanks for agreeing to be awesome today!</p>
</div>
```

### CSS

محتوا با استفاده از CSS زیر استایل‌بندی شده است.

```css
.panel {
  font:
    16px "Open Sans",
    "Helvetica",
    "Arial",
    sans-serif;
  border: 1px solid #2222dd;
  padding: 12px;
  width: 500px;
  text-align: center;
}

.button {
  font:
    22px "Open Sans",
    "Helvetica",
    "Arial",
    sans-serif;
  padding: 5px 36px;
}

h1 {
  margin-top: 0;
  font-size: 175%;
}
```

### JavaScript

کد JavaScript یک شنوندهٔ رویداد (event listener) به دکمهٔ «OK» اضافه می‌کند که پنل «خوش‌آمدگویی» را پنهان کرده و پنل «فوق‌العاده» را نمایش می‌دهد:

```js
document.getElementById("okButton").addEventListener("click", () => {
  document.getElementById("welcome").hidden = true;
  document.getElementById("awesome").hidden = false;
});
```

### نتیجه

{{ EmbedLiveSample('Examples', 560, 200) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی [hidden](/en-US/docs/Web/HTML/Reference/Global_attributes/hidden)
- {{cssxref("display")}}