---
title: "AudioTrackList: getTrackById() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioTrackList/getTrackById"
translated_by: "n8n + AI"
---

---
title: "AudioTrackList: getTrackById() method"
short-title: getTrackById()
slug: Web/API/AudioTrackList/getTrackById
page-type: web-api-instance-method
browser-compat: api.AudioTrackList.getTrackById
---

{{APIRef("HTML DOM")}}

متود **`getTrackById()`** متعلق به {{domxref("AudioTrackList")}} اولین شیء {{domxref("AudioTrack")}} را از فهرست trackهایی برمیگرداند که {{domxref("AudioTrack.id", "id")}} آنها با رشته مشخصشده مطابقت دارد.
این امکان را به شما میدهد تا اگر رشته شناسه (ID) یک track مشخص را میدانید، آن را پیدا کنید.

## Syntax

```js-nolint
getTrackById(id)
```

### Parameters

- `id`
  - : یک رشته که شناسه track مورد نظر برای یافتن در فهرست trackها را نشان میدهد.

### Return value

یک شیء {{domxref("AudioTrack")}} که اولین track یافتشده در `AudioTrackList` را نشان میدهد که `id` آن با رشته مشخصشده مطابقت دارد. اگر هیچ موردی مطابقت نداشته باشد، این متود مقدار `null` را برمیگرداند.

trackها به ترتیب طبیعی خود جستجو میشوند؛ یعنی به ترتیبی که توسط خود منبع رسانهای تعریف شده است، یا اگر منبع ترتیبی را تعریف نکرده باشد، به ترتیب نسبی که trackها توسط منبع رسانهای اعلام شدهاند.

## Examples

این مثال یک بازی فرضی را پیشنهاد میدهد که در آن از فیلمها به عنوان صحنههای سینمایی یا قطعات کلیدی دیگر در بازی استفاده میشود. هر فیلم یک track صوتی برای هر شخصیت دارد، همچنین یکی برای موسیقی، جلوههای صوتی و غیره. این تابع به بازی اجازه میدهد تا صدای یک شخصیت خاص را غیرفعال کند تا عملکرد فیلم بر اساس رویدادهای درون بازی تنظیم شود؛ اگر دیالوگ شخصیت مرتبط نباشد، حذف میشود. بدیهی است که برای کارکردن این کار به طراحی گرافیکی هوشمندانهای نیاز است، اما این یک بازی فرضی است.

```js
function disableCharacter(videoElem, characterName) {
  videoElem.audioTracks.getTrackById(characterName).enabled = false;
}
```

این تابع کوتاه {{domxref("AudioTrackList")}} حاوی trackهای صوتی ویدیو را با استفاده از {{domxref("HTMLMediaElement.audioTracks")}} دریافت میکند، سپس `getTrackById()` را روی آن با مشخص کردن نام شخصیت فراخوانی میکند. سپس صدای track حاصل با تنظیم علامت {{domxref("AudioTrack.enabled", "enabled")}} آن روی `false` غیرفعال میشود.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}