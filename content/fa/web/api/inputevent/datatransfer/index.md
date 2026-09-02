---
title: "InputEvent: dataTransfer property"
short-title: dataTransfer
slug: Web/API/InputEvent/dataTransfer
page-type: web-api-instance-property
browser-compat: api.InputEvent.dataTransfer
---

{{APIRef("UI Events")}}

ویژگی فقط‌خواندنی **`dataTransfer`** از رابط {{domxref("InputEvent")}} یک شیء {{domxref("DataTransfer")}} برمی‌گرداند که حاوی اطلاعاتی درباره متن غنی (rich text) یا متن ساده‌ای است که به محتوای قابل ویرایش اضافه یا از آن حذف می‌شود.

## مقدار

یک شیء {{domxref("DataTransfer")}} یا `null`. مشخصات (spec) یک [بررسی کلی](https://w3c.github.io/input-events/#overview) از مقدار آن در موارد مختلف دارد.

## مثال‌ها

در مثال ساده زیر، ما یک شنونده رویداد روی رویداد [input](/en-US/docs/Web/API/Element/input_event) تنظیم کرده‌ایم تا زمانی که هر محتوایی در عنصر {{htmlelement("p")}} با ویژگی `contenteditable` جای‌گذاری (paste) شود، کد HTML آن از طریق متد [`InputEvent.dataTransfer.getData()`](/en-US/docs/Web/API/DataTransfer/getData) دریافت شود و در پاراگراف زیر ورودی گزارش شود.

برای دیدن اثرات، سعی کنید برخی از محتوای ارائه شده را کپی و جای‌گذاری کنید.

```html
<p><span style="font-weight: bold; color: blue">Whoa, bold blue text!</span></p>
<p>
  <span style="font-style: italic; color: red">Exciting: italic red text!</span>
</p>
<p>Boring normal text ;-(</p>

<hr />

<p contenteditable="true">
  Go on, try pasting some content into this editable paragraph and see what
  happens!
</p>

<p class="result"></p>
```

```js
const editable = document.querySelector("p[contenteditable]");
const result = document.querySelector(".result");

editable.addEventListener("input", (e) => {
  result.textContent = e.dataTransfer.getData("text/html");
});
```

{{EmbedLiveSample('Examples', '100%', 250)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}