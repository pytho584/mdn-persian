---
title: "HTMLTextAreaElement: wrap property"
---

---
title: "HTMLTextAreaElement: wrap property"
short-title: wrap
slug: Web/API/HTMLTextAreaElement/wrap
page-type: web-api-instance-property
browser-compat: api.HTMLTextAreaElement.wrap
---

{{ APIRef("HTML DOM") }}

ویژگی **`wrap`** در رابط {{DOMxRef("HTMLTextAreaElement")}} نشاندهندهٔ نحوهٔ خط‌شکنی مقدار برای ارسال فرم است. این ویژگی، صفت [`wrap`](/en-US/docs/Web/HTML/Reference/Elements/textarea#wrap) عنصر `<textarea>` را منعکس می‌کند. توجه داشته باشید که مقدار `"hard"` فقط زمانی تأثیر می‌گذارد که صفت {{domxref("HTMLTextAreaElement.cols", "cols")}} نیز تنظیم شده باشد.

## مقدار

برای مقادیر ممکن به [`wrap`](/en-US/docs/Web/HTML/Reference/Elements/textarea#wrap) مراجعه کنید. مقدار پیش‌فرض `"soft"` است.

## مثال‌ها

```js
const textareaElement = document.getElementById("comment");
const oldWrap = textArea.wrap;
textArea.wrap = "hard"; // Add line breaks (CR+LF) during form submission
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{HTMLElement("textarea")}}
- {{DOMXref("HTMLTextAreaElement.cols")}}