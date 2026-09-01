```yaml
---
title: "HTMLCollection: item() method"
short-title: item()
slug: Web/API/HTMLCollection/item
page-type: web-api-instance-method
browser-compat: api.HTMLCollection.item
---

{{APIRef("HTML DOM")}}

متد `item()` از {{domxref("HTMLCollection")}}، عنصری را که در موقعیت (ایندکس) مشخص‌شده در مجموعه قرار دارد، برمی‌گرداند.

> [!NOTE]
> از آنجا که محتویات یک `HTMLCollection` زنده (live) هستند، تغییرات در DOM زمینه‌ای می‌تواند باعث تغییر موقعیت عناصر منفرد در مجموعه شود؛ بنابراین مقدار ایندکس برای یک عنصر خاص لزوماً ثابت نخواهد ماند.

## نحو (Syntax)

```js-nolint
item(index)
```

### پارامترها

- `index`
  - : موقعیت {{domxref("Element")}}ای که باید برگردانده شود. عناصر در یک `HTMLCollection` به همان ترتیبی ظاهر می‌شوند که در منبع سند (source) آمده‌اند.

### مقدار بازگشتی

{{domxref("Element")}} در ایندکس مشخص‌شده، یا اگر `index` کمتر از صفر یا بزرگ‌تر یا مساوی خصوصیت `length` باشد، `null` برگردانده می‌شود.

## نکات استفاده

متد `item()` یک عنصر شماره‌دار را از یک `HTMLCollection` برمی‌گرداند. در جاوااسکریپت، ساده‌تر است که `HTMLCollection` را مانند یک آرایه در نظر بگیرید و با نماد آرایه به آن ایندکس بدهید. به [مثال‌ها](#examples) در زیر مراجعه کنید.

## مثال‌ها

```js
const images = document.images; // این یک HTMLCollection است
const img0 = images.item(0); // می‌توانید از متد item() به این صورت استفاده کنید
const img1 = images[1]; // اما این نماد ساده‌تر و رایج‌تر است
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("NodeList.item()")}}
```