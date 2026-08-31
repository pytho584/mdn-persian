---
title: "AudioDecoder"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioDecoder"
translated_by: "n8n + AI"
---

---
title: AudioDecoder
slug: Web/API/AudioDecoder
page-type: web-api-interface
browser-compat: api.AudioDecoder
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

رابط **`AudioDecoder`** از {{domxref('WebCodecs API','','',' ')}} تکه‌های صوتی را رمزگشایی می‌کند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("AudioDecoder.AudioDecoder", "AudioDecoder()")}}
  - : یک شیء `AudioDecoder` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{DOMxRef("EventTarget")}}، به ارث می‌برد._

- {{domxref("AudioDecoder.decodeQueueSize")}} {{ReadOnlyInline}}
  - : یک عدد صحیح که تعداد درخواست‌های صف رمزگشایی را نشان می‌دهد.
- {{domxref("AudioDecoder.state")}} {{ReadOnlyInline}}
  - : وضعیت کدک پایه و اینکه آیا برای رمزگشایی پیکربندی شده است را نشان می‌دهد.

### رویدادها

- {{domxref("AudioDecoder.dequeue_event", "dequeue")}}
  - : برای نشان دادن کاهش در {{domxref("AudioDecoder.decodeQueueSize")}} رخ می‌دهد.

## متدهای ایستا

- {{domxref("AudioDecoder/isConfigSupported_static", "AudioDecoder.isConfigSupported()")}}
  - : یک وعده (Promise) برمی‌گرداند که نشان می‌دهد آیا `AudioDecoderConfig` ارائه‌شده پشتیبانی می‌شود یا خیر.

## متدهای نمونه

_متدها را از والد خود، {{DOMxRef("EventTarget")}}، به ارث می‌برد._

- {{domxref("AudioDecoder.configure()")}}
  - : یک پیام کنترلی را در صف قرار می‌دهد تا رمزگشای صوتی برای رمزگشایی تکه‌ها پیکربندی شود.
- {{domxref("AudioDecoder.decode()")}}
  - : یک پیام کنترلی را در صف قرار می‌دهد تا یک تکه صوتی معین را رمزگشایی کند.
- {{domxref("AudioDecoder.flush()")}}
  - : یک وعده (Promise) برمی‌گرداند که پس از اتمام تمام پیام‌های در انتظار در صف حل می‌شود.
- {{domxref("AudioDecoder.reset()")}}
  - : همه وضعیت‌ها از جمله پیکربندی، پیام‌های کنترلی در صف پیام‌های کنترلی، و همه فراخوان‌های در انتظار را بازنشانی می‌کند.
- {{domxref("AudioDecoder.close()")}}
  - : تمام کارهای در انتظار را پایان داده و منابع سیستم را آزاد می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}