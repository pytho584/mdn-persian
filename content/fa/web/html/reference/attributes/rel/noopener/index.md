---
title: "rel=\"noopener\" HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/rel/noopener"
translated_by: "n8n + AI"
---

کلیدواژهٔ **`noopener`** برای `rel` attribute در عناصر `<a>`، `<area>` و `<form>` به مرورگر می‌گوید هنگام پیمایش به مقصد، به بافتار مرور جدید دسترسی به سندِ مبدأ ندهد؛ یعنی `{{DOMxRef("Window.opener")}}` را روی پنجرهٔ بازشده تنظیم نکند (و مقدار آن `null` بماند).

این موضوع به‌ویژه هنگام باز کردن لینک‌های غیرقابل اعتماد مفید است؛ چون تضمین می‌کند که آن لینک‌ها از طریق `{{DOMxRef("Window.opener")}}` نتوانند سند مبدأ را دستکاری کنند (برای جزئیات بیشتر به [About rel=noopener](https://mathiasbynens.github.io/rel-noopener/) مراجعه کنید). در عین حال هدر HTTP `Referer` هنوز ارسال می‌شود، مگر اینکه `noreferrer` هم استفاده شود.

توجه داشته باشید که وقتی `noopener` استفاده می‌شود، نام‌های target غیرخالی به‌جز `_top`، `_self` و `_parent` همگی از نظر تعیین باز شدن پنجره یا تب جدید، مانند `_blank` رفتار می‌کنند.

> **نکته:** تنظیم `target="_blank"` روی عناصر `<a>`، `<area>` و `<form>` به‌طور ضمنی همان رفتار `rel="noopener"` را ایجاد می‌کند و `window.opener` را تنظیم نمی‌کند.