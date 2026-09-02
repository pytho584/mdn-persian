---
title: "ImageTrackList"
---

---
title: ImageTrackList
slug: Web/API/ImageTrackList
page-type: web-api-interface
browser-compat: api.ImageTrackList
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

رابطهٔ **`ImageTrackList`** متعلق به {{domxref('WebCodecs API','','','true')}}، فهرستی از trackهای تصویر را نمایش می‌دهد.

## ویژگی‌های وهله

- {{domxref("ImageTrackList.ready")}} {{ReadOnlyInline}}
  - : یک {{jsxref("Promise")}} بازمی‌گرداند که پس از پر شدن `ImageTrackList` با {{domxref("ImageTrack","tracks")}}، resolve می‌شود.
- {{domxref("ImageTrackList.length")}} {{ReadOnlyInline}}
  - : یک عدد صحیح بازمی‌گرداند که طول `ImageTrackList` را نشان می‌دهد.
- {{domxref("ImageTrackList.selectedIndex")}} {{ReadOnlyInline}}
  - : یک عدد صحیح بازمی‌گرداند که ایندکسِ `selectedTrack` را نشان می‌دهد.
- {{domxref("ImageTrackList.selectedTrack")}} {{ReadOnlyInline}}
  - : {{domxref("ImageTrack")}} انتخاب‌شده را بازمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}