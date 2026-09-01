---
title: "HTMLMediaElement: defaultPlaybackRate property"
---

---
title: "HTMLMediaElement: defaultPlaybackRate property"
short-title: defaultPlaybackRate
slug: Web/API/HTMLMediaElement/defaultPlaybackRate
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.defaultPlaybackRate
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLMediaElement.defaultPlaybackRate`** نرخ پخش پیش‌فرض رسانه را مشخص می‌کند.

## مقدار

یک عدد اعشاری (double). مقدار `1.0` به معنای «سرعت عادی» است؛ مقادیر کمتر از `1.0` باعث پخش کندتر رسانه و مقادیر بیشتر باعث پخش سریع‌تر آن می‌شوند.

### استثناها

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر مقدار مشخص‌شده پشتیبانی نشود، این خطا پرتاب می‌شود.

## مثال‌ها

```js
const obj = document.createElement("video");
console.log(obj.defaultPlaybackRate); // 1
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLMediaElement")}}: اینترفیسی که برای تعریف ویژگی `HTMLMediaElement.defaultPlaybackRate` استفاده می‌شود.