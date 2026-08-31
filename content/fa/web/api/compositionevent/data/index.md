---
title: "CompositionEvent: data property"
short-title: data
slug: Web/API/CompositionEvent/data
page-type: web-api-instance-property
browser-compat: api.CompositionEvent.data
---

{{APIRef("UI Events")}}

ویژگی فقط‑خواندنی **`data`** از رابط {{domxref("CompositionEvent")}} نویسه‌هایی را که توسط روش ورودی (input method) ایجادکنندهٔ رویداد تولید شده‌اند، بازمی‌گرداند. ماهیت دقیق این مقدار بسته به نوع رویدادی که شیء `CompositionEvent` را ایجاد کرده، متفاوت است.

## مقدار

یک رشته (string) که داده‌های رویداد را نمایش می‌دهد:

- برای رویدادهای `compositionstart`، این رشته همان متنی است که در حال حاضر انتخاب شده و قرار است با رشته‌ای که در حال ترکیب (compose) شدن است جایگزین شود. این مقدار حتی اگر محتوا دامنهٔ انتخاب را تغییر دهد، ثابت می‌ماند؛ در عوض، رشته‌ای را نشان می‌دهد که در زمان شروع ترکیب انتخاب شده بود.
- برای `compositionupdate`، این رشته، رشته‌ای است که در حال حاضر و در حین ویرایش وجود دارد.
- برای رویدادهای `compositionend`، این رشته، رشته‌ای است که به ویرایشگر نهایی (commit) شده است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CompositionEvent")}}