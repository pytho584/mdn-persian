---
title: DOMParser
slug: Web/API/DOMParser
page-type: web-api-interface
browser-compat: api.DOMParser
---

{{APIRef("DOM")}}

رابط **`DOMParser`** امکان تجزیه کد منبع {{Glossary("XML")}} یا {{Glossary("HTML")}} از یک رشته به یک {{domxref("Document")}} در DOM را فراهم می‌کند.

شما می‌توانید عملیات معکوس — تبدیل یک درخت DOM به کد منبع XML یا HTML — را با استفاده از رابط {{domxref("XMLSerializer")}} انجام دهید.

در مورد یک سند HTML، می‌توانید با تنظیم مقدار ویژگی‌های {{domxref("Element.innerHTML")}} و {{domxref("Element.outerHTML", "outerHTML")}}، بخش‌هایی از DOM را با درخت‌های DOM جدیدی که از HTML ساخته شده‌اند جایگزین کنید. همچنین می‌توان این ویژگی‌ها را برای دریافت قطعه‌های HTML متناظر با زیردرخت DOM مربوطه خواند.

توجه داشته باشید که {{domxref("XMLHttpRequest")}} می‌تواند XML و HTML را مستقیماً از یک منبع قابل آدرس‌دهی با URL تجزیه کند و یک `Document` را در ویژگی {{domxref("XMLHttpRequest.response", "response")}} خود بازگرداند.

> [!NOTE]
> آگاه باشید که [عناصر سطح-بلوک](/en-US/docs/Glossary/Block-level_content) مانند `<p>` به‌طور خودکار بسته می‌شوند اگر عنصر سطح-بلوک دیگری داخل آن‌ها تودرتو شده باشد؛ بنابراین آن عنصر داخلی قبل از تگ بسته شدن `</p>` تجزیه می‌شود.

## سازنده

- {{domxref("DOMParser.DOMParser","DOMParser()")}}
  - : یک شیء جدید `DOMParser` می‌سازد.

## متدهای نمونه

- {{domxref("DOMParser.parseFromString()")}}
  - : یک نمونه از {{domxref("TrustedHTML")}} یا یک رشته را به‌عنوان HTML یا XML تجزیه کرده و یک {{domxref("Document")}} بازمی‌گرداند.

## مثال‌ها

مستندات مربوط به {{domxref("DOMParser.parseFromString()")}}، که تنها متد این رابط است، شامل مثال‌هایی برای تجزیه رشته‌های XML، SVG و HTML است.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## جستارهای وابسته

- [تجزیه و سریال‌سازی XML](/en-US/docs/Web/XML/Guides/Parsing_and_serializing_XML)
- {{domxref("XMLHttpRequest")}}
- {{domxref("XMLSerializer")}}
- {{jsxref("JSON.parse()")}} - معادل آن برای اسناد {{jsxref("JSON")}}.