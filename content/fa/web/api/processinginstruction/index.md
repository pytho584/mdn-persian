---
title: ProcessingInstruction
slug: Web/API/ProcessingInstruction
page-type: web-api-interface
browser-compat: api.ProcessingInstruction
---

{{APIRef("DOM")}}

رابط **`ProcessingInstruction`** یک [دستور پردازش](https://www.w3.org/TR/xml/#sec-pi) را نمایش می‌دهد؛ یعنی یک {{domxref("Node")}} که دستوری را برای یک برنامهٔ خاص در خود جای می‌دهد، اما هر برنامهٔ دیگری که آن دستور را نمی‌شناسد می‌تواند آن را نادیده بگیرد.

> [!WARNING]
> گره‌های `ProcessingInstruction` فقط در اسناد XML پشتیبانی می‌شوند، نه در اسناد HTML. در اسناد HTML، یک دستور پردازش به‌عنوان یک دیدگاه در نظر گرفته می‌شود و به‌صورت یک شیء {{domxref("Comment")}} در درخت نمایش داده می‌شود.

یک دستور پردازش ممکن است با [اعلامیهٔ XML](/en-US/docs/Web/XML/Guides/XML_introduction#xml_declaration) تفاوت داشته باشد.

> [!NOTE]
> دستورهای پردازش تعریف‌شده توسط کاربر نمی‌توانند با `"xml"` شروع شوند، زیرا نام‌های هدفِ دستور پردازش که با پیشوند `xml` شروع می‌شوند، طبق مشخصات XML برای کاربردهای استاندارد خاصی رزرو شده‌اند (برای نمونه، `<?xml-stylesheet ?>` را ببینید).

برای مثال:

```html
<?xml version="1.0"?>
```

یک دستور پردازش است که `target` آن `xml` است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌های رابط‌های والد خود، یعنی {{domxref("CharacterData")}}، {{domxref("Node")}} و {{domxref("EventTarget")}} را به ارث می‌برد._

- {{domxref("ProcessingInstruction.sheet")}} {{ReadOnlyInline}}
  - : در صورت وجود، شیء {{domxref("StyleSheet")}} مرتبط را برمی‌گرداند؛ در غیر این صورت `null` را برمی‌گرداند.

- {{domxref("ProcessingInstruction.target")}} {{ReadOnlyInline}}
  - : نامی که برنامه‌ای را که دستور برای آن در نظر گرفته شده است شناسایی می‌کند.

## متدهای نمونه

_این رابط متد خاصی ندارد، اما متدهای رابط‌های والد خود، یعنی {{domxref("CharacterData")}}، {{domxref("Node")}} و {{domxref("EventTarget")}} را به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [document.createProcessingInstruction()](/en-US/docs/Web/API/Document/createProcessingInstruction)
- [API DOM](/en-US/docs/Web/API/Document_Object_Model)