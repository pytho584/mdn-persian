---
title: "BeforeInstallPromptEvent: BeforeInstallPromptEvent() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BeforeInstallPromptEvent/BeforeInstallPromptEvent"
translated_by: "n8n + AI"
---

---
title: "BeforeInstallPromptEvent: BeforeInstallPromptEvent() constructor"
short-title: BeforeInstallPromptEvent()
slug: Web/API/BeforeInstallPromptEvent/BeforeInstallPromptEvent
page-type: web-api-constructor
status:
  - experimental
  - non-standard
browser-compat: api.BeforeInstallPromptEvent.BeforeInstallPromptEvent
---

{{APIRef}}{{SeeCompatTable}}{{Non-standard_header}}

سازنده **`BeforeInstallPromptEvent()`** یک شیء جدید {{domxref("BeforeInstallPromptEvent")}} ایجاد می‌کند.

## Syntax

```js-nolint
new BeforeInstallPromptEvent(type)
new BeforeInstallPromptEvent(type, eventInitDict)
```

### پارامترها

- `type`
  - : یک رشته با نام رویداد، که روی `beforeinstallprompt` تنظیم شده است.
- `eventInitDict` {{optional_inline}}
  - : یک شیء با یک ویژگی اختیاری به نام `platforms` که آرایه‌ای از رشته‌ها است و پلتفرم‌هایی را که رویداد روی آن‌ها ارسال می‌شود، فهرست می‌کند.

## Specifications

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [قابل نصب کردن PWAs](/en-US/docs/Web/Progressive_web_apps/Guides/Making_PWAs_installable)
- [چگونه تجربه نصب درون برنامه‌ای خود را ارائه دهید](https://web.dev/articles/customize-install) در web.dev (2021)