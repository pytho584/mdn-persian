---
title: "BeforeInstallPromptEvent: prompt() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BeforeInstallPromptEvent/prompt"
translated_by: "n8n + AI"
---

---
title: "BeforeInstallPromptEvent: prompt() method"
short-title: prompt()
slug: Web/API/BeforeInstallPromptEvent/prompt
page-type: web-api-instance-method
status:
  - experimental
  - non-standard
browser-compat: api.BeforeInstallPromptEvent.prompt
---

{{APIRef}}{{SeeCompatTable}}{{Non-standard_header}}

روش **`prompt()`** از رابط {{domxref("BeforeInstallPromptEvent")}} به توسعه‌دهنده اجازه می‌دهد تا اعلان نصب را در زمان مورد نظر خود نمایش دهد. معمولاً این روش در کنترل‌کننده رویداد برای رابط کاربری نصب سفارشی برنامه فراخوانی می‌شود.

این روش باید در کنترل‌کننده رویداد برای یک اقدام کاربر (مانند کلیک دکمه) فراخوانی شود و فقط یک بار در یک نمونه `BeforeInstallPromptEvent` خاص قابل فراخوانی است.

## Syntax

```js-nolint
prompt()
```

### Parameters

هیچکدام.

### Return value

یک {{jsxref("Promise")}} که به یک شیء حاوی ویژگی‌های زیر تبدیل می‌شود:

- `outcome` {{experimental_inline}} {{non-standard_inline}}
  - : یک رشته که نشان می‌دهد کاربر انتخاب کرده است برنامه را نصب کند یا خیر. باید یکی از مقادیر زیر باشد:
    - `"accepted"`: کاربر برنامه را نصب کرد.
    - `"dismissed"`: کاربر برنامه را نصب نکرد.

- `platform` {{experimental_inline}} {{non-standard_inline}}
  - : اگر کاربر انتخاب کند برنامه را نصب کند، این یک رشته است که نام پلتفرم انتخاب‌شده را مشخص می‌کند که یکی از مقادیر ویژگی {{domxref("BeforeInstallPromptEvent.platforms")}} است. اگر کاربر انتخاب کند برنامه را نصب نکند، این یک رشته خالی است.

## Examples

به [مثال برای رابط `BeforeInstallPromptEvent`](/en-US/docs/Web/API/BeforeInstallPromptEvent#examples) مراجعه کنید.

## Browser compatibility

{{Compat}}

## See also

- [قابل نصب کردن PWAها](/en-US/docs/Web/Progressive_web_apps/Guides/Making_PWAs_installable)
- [چگونه تجربه نصب درون‌برنامه‌ای خود را ارائه دهید](https://web.dev/articles/customize-install) در web.dev (2021)