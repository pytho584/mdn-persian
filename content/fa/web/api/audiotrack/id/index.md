---
title: "AudioTrack: id property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioTrack/id"
translated_by: "n8n + AI"
short-title: id
slug: Web/API/AudioTrack/id
page-type: web-api-instance-property
browser-compat: api.AudioTrack.id
---

{{APIRef("HTML DOM")}}

ویژگی **`id`** شامل یک رشته است که به طور منحصربه‌فرد ردیف نمایش داده شده توسط **{{domxref("AudioTrack")}}** را شناسایی می‌کند.

این ID می‌تواند با متد {{domxref("AudioTrackList.getTrackById()")}} برای یافتن یک ردیف خاص در رسانه مرتبط با یک عنصر رسانه استفاده شود. همچنین می‌توان از ID ردیف به عنوان بخشی از یک URL که ردیف خاص را بارگذاری می‌کند استفاده کرد (اگر رسانه از قطعات رسانه پشتیبانی کند).

## مقدار

یک رشته که ردیف را شناسایی می‌کند، مناسب برای استفاده هنگام فراخوانی {{domxref("AudioTrackList.getTrackById", "getTrackById()")}} در یک {{domxref("AudioTrackList")}} مانند آنچه توسط ویژگی {{domxref("HTMLMediaElement.audioTracks", "audioTracks")}} یک عنصر رسانه مشخص شده است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}