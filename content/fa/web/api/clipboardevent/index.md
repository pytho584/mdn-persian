```markdown
---
title: ClipboardEvent
slug: Web/API/ClipboardEvent
page-type: web-api-interface
browser-compat: api.ClipboardEvent
---

{{APIRef("Clipboard API")}}

رابط **`ClipboardEvent`** از [Clipboard API](/en-US/docs/Web/API/Clipboard_API) رویدادهایی را نشان می‌دهد که اطلاعات مربوط به تغییرات در کلیپ‌بورد (clipboard) را ارائه می‌کنند؛ یعنی رویدادهای {{domxref("Element/cut_event", "cut")}} (برش)، {{domxref("Element/copy_event", "copy")}} (کپی) و {{domxref("Element/paste_event", "paste")}} (چسباندن).

{{InheritanceDiagram}}

## سازنده (Constructor)

- {{domxref("ClipboardEvent.ClipboardEvent", "ClipboardEvent()")}}
  - : یک رویداد `ClipboardEvent` با پارامترهای داده شده ایجاد می‌کند.

## خصوصیات نمونه (Instance properties)

_همچنین خصوصیات والد خود {{domxref("Event")}} را به ارث می‌برد._

- {{domxref("ClipboardEvent.clipboardData")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("DataTransfer")}} که شامل داده‌های تحت تأثیر عملیات {{domxref("Element/cut_event", "cut")}}، {{domxref("Element/copy_event", "copy")}} یا {{domxref("Element/paste_event", "paste")}} است که توسط کاربر آغاز شده، همراه با نوع MIME آن.

## روش‌های نمونه (Instance methods)

_روش خاصی ندارد؛ روش‌های والد خود {{domxref("Event")}} را به ارث می‌برد._

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط با کپی: {{domxref("Element/copy_event", "copy")}}، {{domxref("Element/cut_event", "cut")}}، {{domxref("Element/paste_event", "paste")}}
- {{domxref("ClipboardChangeEvent")}}
- [Clipboard API](/en-US/docs/Web/API/Clipboard_API)
- [مقاله پشتیبانی از تصویر برای Async Clipboard](https://web.dev/articles/async-clipboard)
```