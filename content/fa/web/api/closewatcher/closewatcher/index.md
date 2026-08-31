---
title: "CloseWatcher: CloseWatcher() constructor"
short-title: CloseWatcher()
slug: Web/API/CloseWatcher/CloseWatcher
page-type: web-api-constructor
browser-compat: api.CloseWatcher.CloseWatcher
---

{{APIRef("HTML DOM")}}

سازندهٔ **`CloseWatcher()`** یک شیء جدید از نوع {{domxref("CloseWatcher")}} می‌سازد.

شما می‌توانید نمونه‌های `CloseWatcher` را بدون [فعالیت کاربر](/en-US/docs/Web/Security/Defenses/User_activation) ایجاد کنید، و این می‌تواند برای پیاده‌سازی مواردی مانند گفتگوهای وقفه به دلیل عدم فعالیت نشست مفید باشد. با این حال، اگر بیش از یک `CloseWatcher` بدون فعالیت کاربر ایجاد کنید، نمونهٔ تازه‌ساخته‌شده با نمونهٔ قبلی گروه‌بندی می‌شود، بنابراین یک درخواست بستن، هر دوی آن‌ها را می‌بندد. این بدان معناست که مهم است متدهای {{domxref("CloseWatcher.destroy()", "destroy()")}}، {{domxref("CloseWatcher.close()", "close()")}} و {{domxref("CloseWatcher.requestClose()", "requestClose()")}} را به‌درستی فراخوانی کنید.

## Syntax

```js-nolint
new CloseWatcher()
new CloseWatcher(options)
```

### Parameters

- `options` {{optional_inline}}
  - : شیئی است که ویژگی‌های زیر را دارد:
    - `signal`
      - : یک {{domxref("AbortSignal")}}. اگر این مورد ارائه شود، ناظر (watcher) می‌تواند (مشابه فراخوانی {{domxref("CloseWatcher.destroy()")}}) با فراخوانی {{domxref("AbortController.abort()")}} روی {{domxref("AbortController")}} متناظر از بین برود.

### Return value

یک شیء جدید از نوع {{domxref("CloseWatcher")}}.

## Examples

### ایجاد نمونه‌های جدید `CloseWatcher`

یک `CloseWatcher` جدید ایجاد کنید.

```js
const watcher = new CloseWatcher();
```

یک `CloseWatcher` جدید با یک {{domxref("AbortSignal")}} ایجاد کنید که از بین بردن ناظر را کنترل می‌کند.

```js
const controller = new AbortController();
const signalWatcher = new CloseWatcher({ signal: controller.signal });
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}