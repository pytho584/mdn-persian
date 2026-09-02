---
title: MediaStreamEvent
slug: Web/API/MediaStreamEvent
page-type: web-api-interface
status:
  - deprecated
  - non-standard
browser-compat: api.MediaStreamEvent
---

{{APIRef("WebRTC")}}{{Deprecated_Header}}{{Non-standard_Header}}

رابطِ **`MediaStreamEvent`** نشان‌دهنده رویدادهایی است که در رابطه با یک {{domxref("MediaStream")}} رخ می‌دهند. دو رویداد از این نوع می‌توانند ایجاد شوند: {{domxref("RTCPeerConnection.addstream_event", "addstream")}} و {{domxref("RTCPeerConnection.removestream_event", "removestream")}}.

## ویژگی‌های نمونه

یک `MediaStreamEvent` از آن‌جا که یک {{domxref("Event")}} است، این ویژگی‌ها را نیز پیاده‌سازی می‌کند.

- {{domxref("MediaStreamEvent.stream")}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : شامل {{domxref("MediaStream")}} مرتبط با این رویداد است.

## سازنده‌ها

- {{domxref("MediaStreamEvent.MediaStreamEvent()", "MediaStreamEvent()")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : یک نمونه `MediaStreamEvent` جدید بازمی‌گرداند. این سازنده دو پارامتر می‌پذیرد: اولی رشته‌ای است که نوع رویداد را مشخص می‌کند و دومی یک dictionary شامل {{domxref("MediaStream")}}ی است که به آن اشاره دارد.

## روش‌های نمونه

یک `MediaStreamEvent` از آن‌جا که یک {{domxref("Event")}} است، این ویژگی‌ها را نیز پیاده‌سازی می‌کند. هیچ روش اختصاصی برای `MediaStreamEvent` وجود ندارد.

## مثال‌ها

```js
pc.onaddstream = (ev) => {
  alert(`A stream (id: '${ev.stream.id}') has been added to this connection.`);
};
```

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [WebRTC](/en-US/docs/Web/API/WebRTC_API)
- هدف معمول آن: {{domxref("RTCPeerConnection")}}.