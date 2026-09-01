---
title: "HTMLMediaElement: playbackRate property"
short-title: playbackRate
slug: Web/API/HTMLMediaElement/playbackRate
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.playbackRate
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLMediaElement.playbackRate`** نرخ پخش رسانه را تنظیم می‌کند. از این ویژگی برای پیاده‌سازی کنترل‌های کاربر برای جلو بردن سریع، آهسته‌کردن حرکت و موارد مشابه استفاده می‌شود. نرخ پخش عادی در این مقدار ضرب می‌شود تا نرخ فعلی به دست آید؛ بنابراین مقدار `1.0` به معنای سرعت عادی است.

مقدار منفی برای `playbackRate` نشان می‌دهد که رسانه باید به صورت معکوس پخش شود، اما پشتیبانی از این ویژگی هنوز فراگیر نیست. (برای جزئیات به [سازگاری مرورگر](#browser_compatibility) مراجعه کنید.)

وقتی سرعت پخش سریع یا آهسته از محدودهٔ مفید خارج شود، صدا قطع می‌شود (برای مثال، در Gecko صدا در خارج از بازهٔ `0.25` تا `4.0` قطع می‌شود).

زیروبمی صدا به طور پیش‌فرض تصحیح می‌شود. می‌توانید تصحیح زیروبمی را با استفاده از ویژگی {{domxref("HTMLMediaElement.preservesPitch")}} غیرفعال کنید.

## مقدار

یک [`double`](https://en.wikipedia.org/wiki/Double-precision_floating-point_format). مقدار `1.0` به معنای «سرعت عادی» است؛ مقادیر کمتر از `1.0` رسانه را آهسته‌تر از حالت عادی پخش می‌کنند و مقادیر بیشتر باعث پخش سریع‌تر می‌شوند. (**پیش‌فرض:** `1.0`)

## مثال‌ها

```js
const obj = document.createElement("video");
console.log(obj.playbackRate); // Expected Output: 1
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLMediaElement")}}: رابطی که برای تعریف ویژگی `HTMLMediaElement.playbackRate` استفاده می‌شود
- گزارش‌های باگ مرورگر برای پشتیبانی از `playbackRate` منفی در [Firefox](https://bugzil.la/1468019) و [Blink](https://crbug.com/40410591) (کروم و غیره)
- مسئلهٔ Web Hypertext Application Technology Working Group (WHATWG) برای [الزام پشتیبانی از `playbackRate` منفی](https://github.com/whatwg/html/issues/3754)
