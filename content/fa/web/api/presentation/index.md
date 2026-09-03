---
title: Presentation
slug: Web/API/Presentation
page-type: web-api-interface
status:
  - experimental
browser-compat: api.Presentation
---

{{SeeCompatTable}}{{securecontext_header}}{{APIRef("Presentation API")}}

در این بافت، **`Presentation`** را می‌توان به‌عنوان یکی از دو عامل کاربرِ ممکن تعریف کرد: _عامل کاربر کنترل‌کننده_ و _عامل کاربر دریافت‌کننده_.

در بافت مرورِ کنترل‌کننده، رابط `Presentation` سازوکاری برای نادیده‌گرفتن رفتار پیش‌فرض مرورگر در هنگام شروع ارائه روی صفحه‌نمایش خارجی فراهم می‌کند. در بافت مرورِ دریافت‌کننده نیز رابط `Presentation` دسترسی به اتصال‌های ارائهٔ موجود را فراهم می‌کند.

## ویژگی‌های نمونه

- {{DOMxRef("Presentation.defaultRequest")}} {{Experimental_Inline}}
  - : در یک [عامل کاربر کنترل‌کننده](https://www.w3.org/TR/presentation-api/#dfn-controlling-user-agent)، ویژگی `defaultRequest` _باید_ در صورت وجود، [درخواست ارائهٔ پیش‌فرض](https://www.w3.org/TR/presentation-api/#dfn-default-presentation-request) را برگرداند و در غیر این صورت `null` را برگرداند. در یک [بافت مرور دریافت‌کننده](https://www.w3.org/TR/presentation-api/#dfn-receiving-browsing-context)، این ویژگی _باید_ مقدار `null` را برگرداند.
- {{DOMxRef("Presentation.receiver")}} {{Experimental_Inline}}
  - : در یک [عامل کاربر دریافت‌کننده](https://www.w3.org/TR/presentation-api/#dfn-receiving-user-agent)، ویژگی `receiver` _باید_ نمونهٔ {{DOMxRef("PresentationReceiver")}} مرتبط با [بافت مرور دریافت‌کننده](https://www.w3.org/TR/presentation-api/#dfn-receiving-browsing-context) را برگرداند؛ این نمونه هنگام ایجاد [بافت مرور دریافت‌کننده](https://www.w3.org/TR/presentation-api/#dfn-receiving-browsing-context) توسط [عامل کاربر دریافت‌کننده](https://www.w3.org/TR/presentation-api/#dfn-receiving-user-agent) ساخته شده است.

## متدهای نمونه

هیچ.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}