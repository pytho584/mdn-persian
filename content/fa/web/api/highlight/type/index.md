---
title: "Highlight: type property"
short-title: type
slug: Web/API/Highlight/type
page-type: web-api-instance-property
browser-compat: api.Highlight.type
---

{{APIRef("CSS Custom Highlight API")}}

ویژگی `type` از رابط {{domxref("Highlight")}} یک {{jsxref("String")}} شمارشی است که برای تعیین معنای هایلایت به کار می‌رود. این امکان به فناوری‌های کمکی مانند صفحه‌خوان‌ها اجازه می‌دهد تا این معنا را هنگام ارائهٔ هایلایت به کاربران لحاظ کنند.

به‌طور پیش‌فرض، نوع یک شیء هایلایت روی `highlight` تنظیم شده است؛ اما می‌توانید آن را به `spelling-error` یا `grammar-error` تغییر دهید.

## مقدار

مقادیر ممکن برای مقدار شمارشی `type` عبارت‌اند از:

- `highlight`
  - : این نوع پیش‌فرض هایلایت است و معنای خاصی ندارد.
- `spelling-error`
  - : زمانی از این نوع استفاده کنید که هایلایت برای برجسته‌کردن محتوایی به کار می‌رود که املای آن اشتباه است.
- `grammar-error`
  - : زمانی از این نوع استفاده کنید که هایلایت برای برجسته‌کردن محتوایی به کار می‌رود که از نظر دستوری نادرست است.

## مثال‌ها

```js
const spellErrorRange = new Range();
spellErrorRange.setStart(textNode, 10);
spellErrorRange.setEnd(textNode, 20);

const spellErrorsHighlight = new Highlight(spellErrorRange);

spellErrorsHighlight.type = "spelling-error";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("css_custom_highlight_api", "The CSS Custom Highlight API", "", "nocode")}}
- ماژول [CSS custom highlight API](/en-US/docs/Web/CSS/Guides/Custom_highlight_API)
- [CSS Custom Highlight API: The Future of Highlighting Text Ranges on the Web](https://css-tricks.com/css-custom-highlight-api-early-look/)