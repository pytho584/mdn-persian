---
title: "console: groupCollapsed() static method"
short-title: groupCollapsed()
slug: Web/API/console/groupCollapsed_static
page-type: web-api-static-method
browser-compat: api.console.groupCollapsed_static
---

{{APIRef("Console API")}} {{AvailableInWorkers}}

متد ایستای **`console.groupCollapsed()`** یک گروه درون‌خطی جدید در کنسول ایجاد می‌کند. با این حال، برخلاف {{domxref("console/group_static", "console.group()")}}، گروه جدید به صورت جمع‌شده ایجاد می‌شود. کاربر برای باز کردن آن و مشاهدهٔ ورودی‌های ایجاد شده در گروه، باید از دکمهٔ باز شدن (disclosure button) کنار آن استفاده کند.

برای بازگشت به گروه والد، از {{domxref("console/groupEnd_static", "console.groupEnd()")}} استفاده کنید.

برای جزئیات و مثال‌ها، بخش [استفاده از گروه‌ها در کنسول](/en-US/docs/Web/API/console#using_groups_in_the_console) را در مستندات {{domxref("console")}} ببینید.

## Syntax

```js-nolint
console.groupCollapsed()
console.groupCollapsed(label)
```

### Parameters

- `label` {{Optional_Inline}}
  - : برچسبی برای گروه.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("console/group_static", "console.group()")}}
- {{domxref("console/groupEnd_static", "console.groupEnd()")}}
- [مستندات Microsoft Edge برای `console.groupCollapsed()`](https://learn.microsoft.com/en-us/microsoft-edge/devtools/console/api#groupcollapsed)
- [مستندات Node.js برای `console.groupCollapsed()`](https://nodejs.org/docs/latest/api/console.html#consolegroupcollapsed)
- [مستندات Google Chrome برای `console.groupCollapsed()`](https://developer.chrome.com/docs/devtools/console/api/#groupcollapsed)