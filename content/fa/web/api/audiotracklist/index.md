---
title: "AudioTrackList"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioTrackList"
translated_by: "n8n + AI"
---

---
title: AudioTrackList
slug: Web/API/AudioTrackList
page-type: web-api-interface
browser-compat: api.AudioTrackList
---

{{APIRef("HTML DOM")}}

رابط **`AudioTrackList`** برای نمایش فهرستی از آهنگ‌های صوتی موجود در یک عنصر رسانه HTML مشخص استفاده می‌شود، که هر آهنگ توسط یک شیء جداگانه {{domxref("AudioTrack")}} در فهرست نمایش داده می‌شود.

یک نمونه از این شیء را با {{domxref('HTMLMediaElement.audioTracks')}} دریافت کنید. آهنگ‌های جداگانه را می‌توان با استفاده از نحو آرایه‌ای (array syntax) به دست آورد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌هایی را از رابط والد خود، {{domxref("EventTarget")}}، به ارث می‌برد._

- {{domxref("AudioTrackList.length", "length")}} {{ReadOnlyInline}}
  - : تعداد آهنگ‌های موجود در فهرست.

## روش‌های نمونه

_این رابط همچنین روش‌هایی را از رابط والد خود، {{domxref("EventTarget")}}، به ارث می‌برد._

- {{domxref("AudioTrackList.getTrackById", "getTrackById()")}}
  - : {{domxref("AudioTrack")}} موجود در `AudioTrackList` را که {{domxref("AudioTrack.id", "id")}} آن با رشته مشخص شده مطابقت دارد، برمی‌گرداند. اگر هیچ موردی یافت نشود، `null` برگردانده می‌شود.

## رویدادها

- [`addtrack`](/en-US/docs/Web/API/AudioTrackList/addtrack_event)
  - : زمانی که یک آهنگ صوتی جدید به عنصر رسانه اضافه می‌شود، فعال می‌گردد.
- [`change`](/en-US/docs/Web/API/AudioTrackList/change_event)
  - : زمانی که یک آهنگ فعال یا غیرفعال می‌شود، فعال می‌گردد.
- [`removetrack`](/en-US/docs/Web/API/AudioTrackList/removetrack_event)
  - : زمانی که یک آهنگ صوتی جدید از عنصر رسانه حذف می‌شود، فعال می‌گردد.

## نکات استفاده

علاوه بر امکان دسترسی مستقیم به آهنگ‌های صوتی موجود در یک عنصر رسانه، `AudioTrackList` به شما اجازه می‌دهد تا مدیریت‌کننده‌های رویداد را بر روی رویدادهای {{domxref("AudioTrackList/addtrack_event", "addtrack")}} و {{domxref("AudioTrackList/removetrack_event", "removetrack")}} تنظیم کنید، تا بتوانید زمانی که آهنگ‌هایی به جریان عنصر رسانه اضافه یا از آن حذف می‌شوند، تشخیص دهید. برای جزئیات و مثال‌ها به رویدادهای {{domxref("AudioTrackList/addtrack_event", "addtrack")}} و {{domxref("AudioTrackList/removetrack_event", "removetrack")}} مراجعه کنید.

## مثال‌ها

### دریافت فهرست آهنگ‌های صوتی یک عنصر رسانه

برای دریافت `AudioTrackList` یک عنصر رسانه، از ویژگی {{domxref("HTMLMediaElement.audioTracks", "audioTracks")}} آن استفاده کنید.

```js
const audioTracks = document.querySelector("video").audioTracks;
```

### نظارت بر تغییرات تعداد آهنگ‌ها

در این مثال، ما یک برنامه داریم که اطلاعاتی در مورد تعداد کانال‌های موجود نمایش می‌دهد. برای به‌روز نگه داشتن آن، مدیریت‌کننده‌هایی برای رویدادهای {{domxref("AudioTrackList/addtrack_event", "addtrack")}} و {{domxref("AudioTrackList/removetrack_event", "removetrack")}} تنظیم شده‌است.

```js
audioTracks.onaddtrack = updateTrackCount;
audioTracks.onremovetrack = updateTrackCount;

function updateTrackCount(event) {
  trackCount = audioTracks.length;
  drawTrackCountIndicator(trackCount);
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}