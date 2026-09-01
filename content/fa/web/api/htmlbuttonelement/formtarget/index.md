---
title: "HTMLButtonElement: formTarget property"
---

---
title: "HTMLButtonElement: formTarget property"
short-title: formTarget
slug: Web/API/HTMLButtonElement/formTarget
page-type: web-api-instance-property
browser-compat: api.HTMLButtonElement.formTarget
---

{{APIRef("HTML DOM")}}

ویژگی **`formTarget`** از رابط {{domxref("HTMLButtonElement")}} مشخص می‌کند که پاسخ فرم ارسال‌شده ({{HtmlElement("form")}}) در کدام تب، پنجره، یا iframe نمایش داده شود. این ویژگی، مقدار ویژگی [`formtarget`](/en-US/docs/Web/HTML/Reference/Elements/button#formtarget) عنصر {{HTMLElement("button")}} را منعکس می‌کند.

اگر فرم از طریق این دکمه ارسال شود، این مقدار، ویژگی {{domxref("HTMLFormElement.target", "target")}} رابط {{domxref("HTMLFormElement")}} را نادیده می‌گیرد. این ویژگی قابل خواندن و تنظیم است. اگر تنظیم نشده باشد، مقدار آن رشتهٔ خالی (`""`) است.

## مقدار

یک رشته.

## نمونه‌ها

```js
btnEl.formTarget = "_self";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLButtonElement.formAction")}}
- {{domxref("HTMLButtonElement.formEnctype")}}
- {{domxref("HTMLButtonElement.formNoValidate")}}
- {{domxref("HTMLButtonElement.formMethod")}}
- {{domxref("HTMLFormElement.target")}}
- [ارسال داده‌های فرم](/en-US/docs/Learn_web_development/Extensions/Forms/Sending_and_retrieving_form_data)