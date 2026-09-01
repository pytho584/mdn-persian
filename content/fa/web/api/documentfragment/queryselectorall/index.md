---
title: "DocumentFragment: querySelectorAll() method"
short-title: querySelectorAll()
slug: Web/API/DocumentFragment/querySelectorAll
page-type: web-api-instance-method
browser-compat: api.DocumentFragment.querySelectorAll
---

{{ApiRef("DOM")}}

متد **`DocumentFragment.querySelectorAll()`** یک {{domxref("NodeList")}} از عناصر داخل {{domxref("DocumentFragment")}} را برمی‌گرداند (با استفاده از پیمایش پیش‌ترتیب عمق-اول گره‌های سند) که با گروه مشخص‌شده از انتخاب‌گرها مطابقت دارند.

اگر انتخاب‌گرهای مشخص‌شده در پارامتر نامعتبر باشند، یک {{domxref("DOMException")}} با مقدار `SYNTAX_ERR` صادر می‌شود.

## Syntax

```js-nolint
querySelectorAll(selectors)
```

### Parameters

- `selectors`
  - : یک رشته شامل یک یا چند انتخاب‌گر CSS که با کاما از هم جدا شده‌اند.

### Return value

یک {{domxref("NodeList")}} غیرزنده که شامل یک {{domxref("Element")}} برای هر عنصری است که حداقل با یکی از انتخاب‌گرهای مشخص‌شده مطابقت دارد، یا یک {{domxref("NodeList")}} خالی در صورت عدم تطابق.

## Examples

این مثال لیستی از همه عناصر `div` داخل `DocumentFragment` را برمی‌گرداند که دارای کلاس `note` یا `alert` هستند:

```js
const matches = documentFrag.querySelectorAll("div.note, div.alert");
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("DocumentFragment")}} — رابطی که این متد به آن تعلق دارد.