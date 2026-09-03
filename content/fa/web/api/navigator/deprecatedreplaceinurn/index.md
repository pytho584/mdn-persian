---
title: "Navigator: deprecatedReplaceInURN() method"
short-title: deprecatedReplaceInURN()
slug: Web/API/Navigator/deprecatedReplaceInURN
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.Navigator.deprecatedReplaceInURN
---

{{APIRef("Fenced Frame API")}}{{seecompattable}}

متد **`deprecatedReplaceInURN()`** در رابط {{domxref("Navigator")}} رشته‌های مشخص‌شده را درون URL نگاشت‌شده‌ای جایگزین می‌کند که متناظر با یک URN ناشفاف (opaque URN) یا ویژگی داخلی `url` از یک `FencedFrameConfig` است.

یک `FencedFrameConfig` یا URN ناشفاف از منبعی مانند متد `runAdAuction()` در [Protected Audience API](https://privacysandbox.google.com/private-advertising/protected-audience) بازگردانده می‌شود و سپس به عنوان مقدار {{domxref("HTMLFencedFrameElement.config")}} تنظیم می‌شود. URL محتوای مرتبط با آن `FencedFrameConfig` یا URN ناشفاف توسط مرورگر به‌صورت داخلی به آن نگاشت می‌شود و از طریق جاوااسکریپت قابل دسترسی نیست.

با این حال، ممکن است بخواهید بخش‌هایی از آن URL داخلی را جایگزین کنید. این کار رویکردی رایج برای انتقال داده‌های زمان اجرا (runtime data) به کریتیوهای تبلیغاتی (ad creatives) برای استفاده در رندر است. تابع `deprecatedReplaceInURN()` به عنوان یک اقدام موقت در دسترس قرار گرفته است تا این جایگزینی را برای URLهای fenced frame ممکن کند و به ارائه‌دهندگان فناوری تبلیغات (ad tech) کمک کند تا پیاده‌سازی‌های موجود خود را به APIهای [privacy sandbox](https://privacysandbox.google.com/) منتقل کنند.

## سینتکس

```js-nolint
deprecatedReplaceInURN(UrnOrConfig, replacements)
```

### پارامترها

- `UrnOrConfig`
  - : یک شیء `FencedFrameConfig` یا یک URN ناشفاف که می‌خواهید بخش‌هایی از URL داخلی متناظر با آن را جایگزین کنید.
- `replacements`
  - : یک شیء شامل یک یا چند ویژگی که بیانگر جایگزینی‌هایی است که می‌خواهید در URL داخلی انجام دهید. کلید هر ویژگی یک زیربخش از URL است که می‌خواهید جایگزین شود و مقدار هر ویژگی رشته‌ای است که با آن جایگزین می‌شود. توجه داشته باشید که:
    - زیربخش‌های URL که باید جایگزین شوند باید در یکی از قالب‌های زیر باشند:
      - `${string}`
      - `%%string%%`
    - اگر یک زیربخش URL در قالب صحیح باشد، اما آن زیربخش در URL یافت نشود، پرامیسی بازگشتی همچنان fulfilled می‌شود (یعنی با موفقیت تکمیل می‌شود)، اما هیچ جایگزینی صورت نمی‌گیرد.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با مقدار {{jsxref("undefined")}} تکمیل می‌شود.

### استثناها

- `TypeError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود:
    - `UrnOrConfig` یک شیء معتبر `FencedFrameConfig` یا URN ناشفاف نباشد.
    - هر یک از کلیدهای جایگزینی مشخص‌شده با قالب‌های مجاز مطابقت نداشته باشند.

## مثال‌ها

از فراخوانی زیر می‌توان برای بازگرداندن یک URN ناشفاف استفاده کرد:

```js
const exampleURN = await navigator.runAdAuction({
  ...auctionConfig,
  resolveToConfig: false,
});
```

سپس می‌توانید زیربخش‌های URL را با استفاده از یک فراخوانی `deprecatedReplaceInURN()` مانند زیر جایگزین کنید:

```js
await navigator.deprecatedReplaceInURN(exampleURN, {
  "${foo}": "1",
  "${bar}": "2",
  "%%baz%%": "3",
});
```

اگر URL داخلی مرتبط با URN در ابتدا به این صورت باشد:

```http
https://example.com/a=${foo}&b=${bar}&c=%%baz%%
```

پس از جایگزینی، به این صورت خواهد بود:

```http
https://example.com/a=1&b=2&c=3
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Fenced Frame API](/en-US/docs/Web/API/Fenced_frame_API)