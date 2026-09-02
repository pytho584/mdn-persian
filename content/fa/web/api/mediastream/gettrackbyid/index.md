---
title: "MediaStream: getTrackById() method"
short-title: getTrackById()
slug: Web/API/MediaStream/getTrackById
page-type: web-api-instance-method
browser-compat: api.MediaStream.getTrackById
---

{{APIRef("Media Capture and Streams")}}

متد **`getTrackById()`** در رابط {{domxref("MediaStream")}}، یک شیء {{domxref("MediaStreamTrack")}} را برمی‌گرداند که نمایانگر ردی با شناسه (ID) مشخص‌شده است. اگر ردی با این شناسه وجود نداشته باشد، این متد مقدار `null` را برمی‌گرداند.

## Syntax

```js-nolint
getTrackById(id)
```

### Parameters

- `id`
  - : یک رشته که ردی را که باید بازگردانده شود مشخص می‌کند.

### Return value

اگر ردی یافت شود که {{domxref("MediaStreamTrack.id")}} آن با رشته `id` specified مطابقت داشته باشد، آن شیء {{domxref("MediaStreamTrack")}} بازگردانده می‌شود. در غیر این صورت، مقدار بازگشتی `null` است.

## Examples

این مثال یک ردی تفسیر (commentary) را روی یک ویدیو فعال می‌کند، بدین صورت که سطح صدای ردی اصلی صوتی را به ۵۰٪ کاهش می‌دهد و سپس ردی تفسیر را فعال می‌کند.

مثال فرض می‌کند که شناسه‌های هر دو ردی مشخص هستند (مثلاً از یک فراخوانی قبلی به {{domxref("MediaStreamTrack.id")}}). در یک برنامه واقعی، ممکن است این شناسه‌ها را هنگام دریافت اولیه جریان (stream) ذخیره کنید، زیرا آن‌ها به‌صورت تصادفی در مرورگر تولید می‌شوند.

```js
const primaryAudioTrack = stream.getTrackById(
  "69f8520f-d94e-43f0-8a7c-77b1774f3b8f",
);
const commentaryTrack = stream.getTrackById(
  "b5410643-2549-491e-b0f7-f08a4ebe54b8",
);

primaryAudioTrack.applyConstraints({ volume: 0.5 });
commentaryTrack.enabled = true;
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("MediaStream")}}
- {{domxref("MediaStreamTrack.id")}}