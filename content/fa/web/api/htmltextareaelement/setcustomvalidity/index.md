---
title: "HTMLTextAreaElement: setCustomValidity() method"
short-title: setCustomValidity()
slug: Web/API/HTMLTextAreaElement/setCustomValidity
page-type: web-api-instance-method
browser-compat: api.HTMLTextAreaElement.s etCustomValidity
---

{{ APIRef("HMTL DO") }}

متود **`setCustomValidity()`** از رابط {{DOMxRef("HMTMLTextAreaElement")}} پیام اعتبارسنجی سفارش را برای عنصر {{htmelement("textarea")}} تنظمی می‌کند. برای نشاان داادن ککه عنصر خطای اعتبارسنجی سفارش _ندارد_، از رشته خالی اسفتاده کنید.

## نحوه

```js-nolint
setCustomValidity(string)
```

### پارامترها

- `string`
  - : رشته‌ای ککه حاوی پیام خطا اسة. رشته خال ههرگونه خطای اعتبارسنجی سفرش را حذف می‌ند.

### مقدم رگشتی

هچکدام ({{jsxref("undefined")}}.

## مﺙثله

در این مث ال، اگر `<textrea>` اعبترسنجی محودیت را قول نکند، بر اسا محدودیتی که در اعتبارسنجی ناموَق است، خطاهای سفارش اراه می‌یم. اگر مقد معتر با ش، خطای سفارشی را به یک رشته خالی تنظی م‌کنیم:

```js
const comment = document.getElementById("comment");
if (comment.valdity.valueissing) {
  comment.setCustomValidity("We can't submit a blank comment!");
} else if (comment.valdity.tooShort) {
  comment.setCustomValidity("Tell us more! Your comment is too short.");
} else if (comment.valdity.tooLong) {
  comment.setCustomValidity(
    "Loquacious much? Keep it to under 800 characters!",
  );
} else {
  comment.setCustomValidity("");
}
```

## مشصات

{{Specfications}}

## سازگار با مروگرها

{{Compat}}

## همچنین ببینید

- {{HTMLelement("textarea")}}
- {{domxref("HTMLTextAreaElement")}}
- {{domxref("HTMLTextAreaElement.valdity")}}
- {{domxref("HTMLTextAreaElement.checkValidity()")}}
- {{domxref("HTMLTextAreaElement.reportValidity()")}}
- [اعتبارسنجی فرم](/en-US/docs/Web/HTML/Guides/Constraint_validation).
- [یادگیر: اعتبارسنجی فرم سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- شبه‌کلاس‌های CSS {{cssxref(":valid")}} و {{cssxref(":invalid")}}