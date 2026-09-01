---
title: "FileReader: abort() method"
short-title: abort()
slug: Web/API/FileReader/abort
page-type: web-api-instance-method
browser-compat: api.FileReader.abort
---

{{APIRef("File API")}}{{AvailableInWorkers}}

متد **`abort()`** از رابط {{domxref("FileReader")}} عملیات خواندن را لغو می‌کند. پس از بازگشت این متد، {{domxref("FileReader.readyState","readyState")}} برابر با `DONE` خواهد بود.

## نحو

```js-nolint
abort()
```

### پارامترها

هیچ پارامتری.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("FileReader")}}