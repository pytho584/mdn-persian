---
title: "PreferenceObject: change event"
short-title: change
slug: Web/API/PreferenceObject/change_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.PreferenceObject.change_event
spec-urls: https://drafts.csswg.org/mediaqueries-5/#onchange-attribute
---

{{APIRef("User Preferences API")}}{{SeeCompatTable}}{{SecureContext_Header}}

رویداد **`change`** از رابط {{domxref("PreferenceObject")}} زمانی صادر می‌شود که مقدار {{domxref("PreferenceObject.override", "override")}} در یک `PreferenceObject` تغییر کند. این اتفاق می‌تواند در نتیجه فراخوانی متدهای {{domxref("PreferenceObject.requestOverride", "requestOverride")}} یا {{domxref("PreferenceObject.clearOverride", "clearOverride")}} رخ دهد.

## Syntax

از نام این رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler) تنظیم نمایید.

```js-nolint
addEventListener("change", (event) => { })

onchange = (event) => { }
```

## Event type

یک رویداد عمومی از نوع {{domxref("Event")}}.

## Examples

### Basic usage

قطعه‌کد زیر، هر بار که طرح رنگ موردعلاقه کاربر تغییر کند، مقدار جدید را در کنسول ثبت می‌کند.

```js
navigator.preferences.colorScheme.addEventListener("change", (event) => {
  console.log(navigator.preferences.colorScheme.value);
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}