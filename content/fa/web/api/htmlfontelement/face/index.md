---
title: "HTMLFontElement: face property"
short-title: face
slug: Web/API/HTMLFontElement/face
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLFontElement.face
---

{{deprecated_header}}{{ APIRef("HTML DOM") }}

خاصیت منسوخ‌شدهٔ **`HTMLFontElement.face`** یک رشته است که ویژگی HTML [`face`](/en-US/docs/Web/HTML/Reference/Elements/font#face) را بازتاب می‌دهد و شامل یک فهرست جدا شده با کاما از یک یا چند نام قلم است.

متن سند، در سبک پیش‌فرض، با اولین قلمی که مرورگر کلاینت از آن پشتیبانی می‌کند نمایش داده می‌شود. اگر هیچ‌یک از قلم‌های فهرست‌شده روی سیستم محلی نصب نباشند، مرورگر معمولاً از قلم متناسب یا ثابت‌پهنای همان سیستم استفاده می‌کند.

قالب این رشته باید یکی از میکرو نحوهای HTML زیر را دنبال کند:

| میکرو نحو (Microsyntax)                              | توضیحات                                                         | مثال‌ها           |
| ---------------------------------------------------- | --------------------------------------------------------------- | ----------------- |
| فهرست یک یا چند نام خانواده‌قلم معتبر                 | _فهرستی از نام‌های قلم که باید در سیستم محلی موجود باشند_       | `courier,verdana` |

## مقدار

یک رشته.

## مثال‌ها

```js
// فرض می‌کنیم یک عنصر <font id="f"> در HTML وجود دارد

const f = document.getElementById("f");
f.face = "arial";
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- رابط {{domxref("HTMLFontElement")}} که این خاصیت به آن تعلق دارد.