---
title: "ClipboardEvent: clipboardData property"
short-title: clipboardData
slug: Web/API/ClipboardEvent/clipboardData
page-type: web-api-instance-property
browser-compat: api.ClipboardEvent.clipboardData
---

{{APIRef("Clipboard API")}}

ویژگی **`clipboardData`** از رابط {{domxref("ClipboardEvent")}} یک شیء {{domxref("DataTransfer")}} را نگه می‌دارد که می‌توان از آن برای موارد زیر استفاده کرد:

- مشخص کردن داده‌هایی که باید در رویدادهای {{domxref("Element/cut_event", "cut")}} (برش) و {{domxref("Element/copy_event", "copy")}} (کپی) در کلیپ‌بورد قرار گیرند، معمولاً با فراخوانی {{domxref("DataTransfer.setData", "setData(format, data)")}};
- به دست آوردن داده‌هایی که باید در رویداد {{domxref("Element/paste_event", "paste")}} (چسباندن) جای‌گذاری شوند، معمولاً با فراخوانی {{domxref("DataTransfer.getData", "getData(format)")}}.

برای اطلاعات بیشتر، مستندات رویدادهای {{domxref("Element/cut_event", "cut")}}، {{domxref("Element/copy_event", "copy")}} و {{domxref("Element/paste_event", "paste")}} را ببینید.

## مقدار

یک شیء {{domxref("DataTransfer")}}.

این ویژگی وقتی رویداد با استفاده از سازنده (constructor) ایجاد شود می‌تواند `null` باشد. اما وقتی رویداد توسط مرورگر ارسال شود، هرگز `null` نیست.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- رویدادهای مرتبط با کپی: {{domxref("Element/copy_event", "copy")}}، {{domxref("Element/cut_event", "cut")}}، {{domxref("Element/paste_event", "paste")}}
- رابط {{domxref("ClipboardEvent")}} که این ویژگی به آن تعلق دارد.
- [Clipboard API](/en-US/docs/Web/API/Clipboard_API)