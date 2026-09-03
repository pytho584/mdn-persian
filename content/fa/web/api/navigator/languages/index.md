```
---
title: "Navigator: languages property"
---

---
title: "Navigator: languages property"
short-title: languages
slug: Web/API/Navigator/languages
page-type: web-api-instance-property
browser-compat: api.Navigator.languages
---

{{APIRef("HTML DOM")}}

ویژگی فقط‑خواندنی **`languages`** از رابط {{domxref("Navigator")}} یک آرایه از رشته‌ها را برمی‌گرداند که زبان‌های ترجیحی کاربر را نشان می‌دهد. هر زبان با استفاده از یک {{glossary("BCP 47 language tag")}} (برچسب زبان BCP 47) توصیف می‌شود. در آرایه بازگشتی، آن‌ها به ترتیب اولویت مرتب شده‌اند و زبان با بیشترین اولویت در ابتدا قرار دارد.

مقدار {{domxref("Navigator.language","navigator.language")}} اولین عنصر آرایه بازگشتی است.

هنگامی که مقدار آن تغییر می‌کند، یعنی با تغییر زبان‌های ترجیحی کاربر، یک رویداد {{domxref("Window.languagechange_event", "languagechange")}} روی شیء {{domxref("Window")}} شلیک می‌شود.

هدر HTTP {{HTTPHeader("Accept-Language")}} در هر درخواست HTTP از مرورگر کاربر معمولاً همان مکان‌ها (locale) را که در ویژگی `navigator.languages` وجود دارد، با مقادیر `q` (کیفیت) کاهش‌یافته فهرست می‌کند. برخی مرورگرها (Chrome و Safari) برچسب‌های بازگشتی فقط‑زبان را در `Accept-Language` اضافه می‌کنند — برای مثال، `en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7` وقتی `navigator.languages` برابر با `["en-US", "zh-CN"]` است. به دلایل حفظ حریم خصوصی (کاهش {{Glossary("fingerprinting")}})، ممکن است هر دو `Accept-Language` و `navigator.languages` فهرست کامل ترجیحات کاربر را شامل نشوند، مانند Safari (همیشه) و حالت ناشناس Chrome، که در آن‌ها فقط یک زبان فهرست می‌شود.

## مقدار

یک آرایه از رشته‌ها.

## نمونه‌ها

### فهرست کردن محتویات navigator.language و navigator.languages

```js
navigator.language; // "en-US"
navigator.languages; // ["en-US", "zh-CN", "ja-JP"]
```

### استفاده از سازنده‌های Intl برای قالب‌بندی مختص زبان، با بازگشت

آرایه شناسه‌های زبان موجود در `navigator.languages` می‌تواند مستقیماً به سازنده‌های {{jsxref("Intl")}} ارسال شود تا انتخاب بازگشتی مبتنی بر اولویت مکان‌ها پیاده‌سازی شود، به‌طوری‌که اولین ورودی در فهرست که با یک مکان پشتیبانی‌شده توسط `Intl` مطابقت دارد، استفاده می‌شود:

```js
const date = new Date("2012-05-24");

const formattedDate = new Intl.DateTimeFormat(navigator.languages).format(date);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("navigator.language")}}
- {{domxref("navigator")}}
- رویداد {{domxref("Window.languagechange_event", "languagechange")}}
- {{jsxref("Intl")}}
```