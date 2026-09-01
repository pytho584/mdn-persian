---
title: "HTMLFencedFrameElement: config property"
short-title: config
slug: Web/API/HTMLFencedFrameElement/config
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HTMLFencedFrameElement.config
---

{{SeeCompatTable}}{{APIRef("Fenced Frame API")}}

خاصیت **`config`** در {{domxref("HTMLFencedFrameElement")}} حاوی یک شیء {{domxref("FencedFrameConfig")}} است که نشان‌دهندهٔ مسیریابی یک {{htmlelement("fencedframe")}} می‌باشد؛ یعنی محتوایی که در آن نمایش داده خواهد شد. یک `FencedFrameConfig` از منابعی مانند [Protected Audience API](https://privacysandbox.google.com/private-advertising/protected-audience) بازگردانده می‌شود.

## مقدار

مقدار `config` در ابتدا `null` است.

زمانی که مقدار آن به یک نمونه شیء {{domxref("FencedFrameConfig")}} تنظیم شود، خصوصیات داخلی `FencedFrameConfig` (برای مثال `mappedURL`) تعیین می‌کنند که چه چیزی درون `<fencedframe>` مرتبط بارگذاری شود. علاوه بر این:

- نوع مسیریابی `"replace"` خواهد بود (به {{domxref("NavigateEvent.navigationType")}} مراجعه کنید)، به این معنی که ورودی فعلی تاریخچه با ورودی جدید جایگزین می‌شود، به‌جای اینکه یک ورودی جدید به آن اضافه شود.
- سیاست ارجاع‌دهنده ({{httpheader("Referrer-Policy")}}) مسیریابی روی `"no-referrer"` تنظیم می‌شود.

## مثال‌ها

برای تنظیم محتوایی که در یک `<fencedframe>` نمایش داده می‌شود، یک API استفاده‌کننده (مانند [Protected Audience](https://privacysandbox.google.com/private-advertising/protected-audience) یا [Shared Storage](https://privacysandbox.google.com/private-advertising/shared-storage)) یک شیء {{domxref("FencedFrameConfig")}} تولید می‌کند که سپس به عنوان مقدار خاصیت `config` آن `<fencedframe>` تنظیم می‌شود.

مثال زیر یک `FencedFrameConfig` را از یک حراجی تبلیغات API Protected Audience دریافت می‌کند که سپس برای نمایش تبلیغ برنده در یک `<fencedframe>` استفاده می‌شود:

```js
const frameConfig = await navigator.runAdAuction({
  // … پیکربندی حراجی
  resolveToConfig: true,
});

const frame = document.createElement("fencedframe");
frame.config = frameConfig;
```

> **توجه:** برای دریافت یک شیء `FencedFrameConfig`، باید `resolveToConfig: true` را در فراخوانی `runAdAuction()` ارسال کرد. اگر تنظیم نشود، {{jsxref("Promise")}} حاصل به یک URN تبدیل می‌شود که فقط در یک {{htmlelement("iframe")}} قابل استفاده است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [Fenced frames](https://privacysandbox.google.com/private-advertising/fenced-frame) در privacysandbox.google.com
- [The Privacy Sandbox](https://privacysandbox.google.com/) در privacysandbox.google.com