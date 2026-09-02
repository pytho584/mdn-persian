---
title: "HTMLTextAreaElement: select() method"
---

---
title: "HTMLTextAreaElement: select() method"
short-title: select()
slug: Web/API/HTMLTextAreaElement/select
page-type: web-api-instance-method
browser-compat: api.HTMLTextAreaElement.select
---

{{APIRef("HTML DOM")}}

متد **`select()`** از رابط {{domxref("HTMLTextAreaElement")}} کل محتوای عنصر {{htmlelement("textarea")}} را انتخاب می‌کند. علاوه بر این، رویداد {{domxref("HTMLTextAreaElement.select_event", "select")}} صادر می‌شود. متد `select()` هیچ پارامتری نمی‌پذیرد و مقداری بازنمی‌گرداند.

## نحو

```js-nolint
select()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
const textarea = document.getElementById("text-box");
textarea.select();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("textarea")}}
- رویداد {{domxref("HTMLTextAreaElement/select_event", "select")}}
- {{domxref("EventTarget.addEventListener", "addEventListener()")}}
- شبه‌عنصر CSS {{cssxref("::selection")}}