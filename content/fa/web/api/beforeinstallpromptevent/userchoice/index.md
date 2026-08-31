---
title: "BeforeInstallPromptEvent: userChoice property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BeforeInstallPromptEvent/userChoice"
translated_by: "n8n + AI"
---

---
title: "BeforeInstallPromptEvent: userChoice property"
short-title: userChoice
slug: Web/API/BeforeInstallPromptEvent/userChoice
page-type: web-api-instance-property
status:
  - experimental
  - non-standard
browser-compat: api.BeforeInstallPromptEvent.userChoice
---

{{APIRef}}{{SeeCompatTable}}{{Non-standard_header}}

ویژگی **`userChoice`** از رابط {{domxref("BeforeInstallPromptEvent")}} انتخابی را که کاربر هنگام درخواست نصب برنامه انجام داده است، نشان می‌دهد.

## مقدار

یک {{jsxref("Promise")}} که به یک شیء شامل دو ویژگی تبدیل می‌شود:

- `outcome` {{experimental_inline}} {{non-standard_inline}}
  - : رشته‌ای که نشان می‌دهد کاربر نصب برنامه را انتخاب کرده است یا نه. باید یکی از مقادیر زیر باشد:
    - `"accepted"`: کاربر برنامه را نصب کرد.
    - `"dismissed"`: کاربر برنامه را نصب نکرد.

- `platform` {{experimental_inline}} {{non-standard_inline}}
  - : اگر کاربر نصب برنامه را انتخاب کرده باشد، این یک رشته است که نام پلتفرم انتخابی را مشخص می‌کند و یکی از مقادیر ویژگی {{domxref("BeforeInstallPromptEvent.platforms")}} است. اگر کاربر انتخاب کرده باشد برنامه را نصب نکند، این یک رشته خالی است.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [قابل نصب کردن PWAها](/en-US/docs/Web/Progressive_web_apps/Guides/Making_PWAs_installable)
- [چگونه تجربه نصب درون‌برنامه‌ای خود را ارائه دهید](https://web.dev/articles/customize-install) در web.dev (2021)