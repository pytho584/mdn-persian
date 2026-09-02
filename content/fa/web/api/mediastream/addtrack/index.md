---
title: "MediaStream: addTrack() method"
short-title: addTrack()
slug: Web/API/MediaStream/addTrack
page-type: web-api-instance-method
browser-compat: api.MediaStream.addTrack
---

{{APIRef("Media Capture and Streams")}}

متد **`addTrack()`** از رابط {{domxref("MediaStream")}} یک رد (track) جدید به جریان (stream) اضافه می‌کند. این رد به عنوان یک پارامتر از نوع {{domxref("MediaStreamTrack")}} مشخص می‌شود.

> [!NOTE]
> اگر رد مشخص‌شده از قبل در مجموعه ردهای جریان وجود داشته باشد، این متد هیچ تأثیری ندارد.

## نحو (Syntax)

```js-nolint
addTrack(track)
```

### پارامترها

- `track`
  - : یک {{domxref("MediaStreamTrack")}} که باید به جریان اضافه شود.

### مقدار بازگشتی

هیچ مقداری ({{jsxref("undefined")}}).

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("MediaStream")}}، رابطی که این متد به آن تعلق دارد.