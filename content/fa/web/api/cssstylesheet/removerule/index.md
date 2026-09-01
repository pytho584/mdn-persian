---
title: "CSSStyleSheet: removeRule() method"
short-title: removeRule()
slug: Web/API/CSSStyleSheet/removeRule
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.CSSStyleSheet.removeRule
---

{{APIRef("CSSOM")}}{{deprecated_header}}

متد منسوخ‌شدهٔ {{domxref("CSSStyleSheet")}} با نام **`removeRule()`** یک قانون (rule) را از شیءِ استایل‌شیت حذف می‌کند. این متد از نظر عملکردی با متد استاندارد و ارجح {{domxref("CSSStyleSheet.deleteRule", "deleteRule()")}} یکسان است.

> [!NOTE]
> این یک _متد قدیمی_ است که با متد استاندارد {{domxref("CSSStyleSheet.deleteRule", "deleteRule()")}} جایگزین شده است. بهتر است به‌جای آن از همین متد استفاده کنید.

## سینتکس

```js-nolint
removeRule(index)
```

### پارامترها

- `index`
  - شاخصی در {{domxref("CSSRuleList")}} استایل‌شیت که مشخص می‌کند کدام قانون حذف شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

این مثال اولین قانون را از استایل‌شیت `myStyles` حذف می‌کند.

```js
myStyles.removeRule(0);
```

می‌توانید به‌سادگی این کد را برای استفاده از متد استاندارد `deleteRule()` بازنویسی کنید:

```js
myStyles.deleteRule(0);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [CSS Object Model](/en-US/docs/Web/API/CSS_Object_Model)
- [استفاده از اطلاعات استایل‌دهی پویا](/en-US/docs/Web/API/CSS_Object_Model/Using_dynamic_styling_information)
- {{domxref("CSSStyleSheet.insertRule", "insertRule()")}}