---
title: "ElementInternals: ariaBrailleRoleDescription property"
short-title: ariaBrailleRoleDescription
slug: Web/API/ElementInternals/ariaBrailleRoleDescription
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaBrailleRoleDescription
---

{{APIRef("Web Components")}}

ویژگی **`ariaBrailleRoleDescription`** از رابط {{domxref("ElementInternals")}} مقدار ویژگی [`aria-brailleroledescription`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-brailleroledescription) را منعکس می‌کند، که توصیف نقش بریل ARIA عنصر را تعریف می‌کند.

از این ویژگی می‌توان برای ارائه‌ی نسخه‌ی کوتاه‌شده‌ی مقدار [`aria-roledescription`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-roledescription) استفاده کرد. این ویژگی تنها زمانی باید استفاده شود که `aria-roledescription` وجود داشته باشد و در موارد نادری که مقدار آن برای بریل بیش از حد طولانی است. ویژگی [`aria-brailleroledescription`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-brailleroledescription) اطلاعات بیشتری در مورد زمان تنظیم این ویژگی ارائه می‌دهد.

## مقدار

یک رشته (string) که قرار است به بریل تبدیل شود.

## مثال‌ها

فرض کنید یک عنصر اسلاید سفارشی داریم:

```js
class CustomSlide extends HTMLElement {
  constructor() {
    super();
    this._internals = this.attachInternals();
    this._internals.role = "slide";
  }

  // …
}

customElements.define("custom-slide", CustomSlide);
```

ما می‌توانیم مقدار `aria-brailleroledescription` عنصر سفارشی را بازیابی و تنظیم کنیم:

```js
const customEl = document.querySelector("custom-slide");
log(customEl.ariaBrailleRoleDescription);
customEl.ariaBrailleRoleDescription = "sd";
log(customEl.ariaBrailleRoleDescription);
```

### نتیجه

{{EmbedLiveSample("Getting and setting ariaBrailleRoleDescription")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

### همچنین ببینید

- [نقش‌های ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles)
