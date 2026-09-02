---
title: "MediaSource: setLiveSeekableRange() method"
short-title: setLiveSeekableRange()
slug: Web/API/MediaSource/setLiveSeekableRange
page-type: web-api-instance-method
browser-compat: api.MediaSource.setLiveSeekableRange
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}

متد **`setLiveSeekableRange()`** از رابط {{domxref("MediaSource")}} محدوده‌ای را تنظیم می‌کند که کاربر می‌تواند در عنصر رسانه در آن جستجو کند.

## نحو

```js-nolint
setLiveSeekableRange(start, end)
```

### پارامترها

- `start`
  - : شروع محدوده قابل جستجو برای تنظیم بر حسب ثانیه که از ابتدای منبع اندازه‌گیری می‌شود. اگر مدت منبع رسانه بینهایت مثبت باشد، شیء {{domxref("TimeRanges")}} بازگشتی توسط ویژگی {{domxref("HTMLMediaElement.seekable")}} دارای یک زمان‌نمای شروع کمتر یا مساوی با این مقدار خواهد بود.
- `end`
  - : پایان محدوده قابل جستجو برای تنظیم بر حسب ثانیه که از ابتدای منبع اندازه‌گیری می‌شود. اگر مدت منبع رسانه بینهایت مثبت باشد، شیء {{domxref("TimeRanges")}} بازگشتی توسط ویژگی {{domxref("HTMLMediaElement.seekable")}} دارای یک زمان‌نمای پایان نه کمتر از این مقدار خواهد بود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
// TBD
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}