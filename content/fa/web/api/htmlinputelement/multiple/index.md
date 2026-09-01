---
title: "HTMLInputElement: multiple property"
short-title: multiple
slug: Web/API/HTMLInputElement/multiple
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.multiple
---

{{ APIRef("HTML DOM") }}

خاصیت **`HTMLInputElement.multiple`** نشان می‌دهد که آیا یک input می‌تواند بیش از یک مقدار داشته باشد. Firefox در حال حاضر فقط برای `<input type="file">` از ویژگی `multiple` پشتیبانی می‌کند.

## مقدار

یک مقدار بولین (boolean).

## مثال‌ها

```html
<input id="my-file-input" type="file" multiple />
```

```js
let fileInput = document.getElementById("my-file-input");

if (fileInput.multiple) {
  // Loop fileInput.files
  for (const file of fileInput.files) {
    // Perform action on one file
  }
  // Only one file available
} else {
  let [file] = fileInput.files;
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [FileList](/en-US/docs/Web/API/FileList)
- [Bug 523771](https://bugzil.la/523771) - پشتیبانی از `<input type=file multiple>`