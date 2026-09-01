---
title: "HTMLMediaElement: canPlayType() method"
---

---
title: "HTMLMediaElement: canPlayType() method"
short-title: canPlayType()
slug: Web/API/HTMLMediaElement/canPlayType
page-type: web-api-instance-method
browser-compat: api.HTMLMediaElement.canPlayType
---

{{APIRef("HTML DOM")}}

متد **`canPlayType()`** از {{domxref("HTMLMediaElement")}} گزارش می‌دهد که چقدر احتمال دارد مرورگر فعلی بتواند رسانه‌ای با [نوع MIME](/en-US/docs/Web/HTTP/Guides/MIME_types) مشخص‌شده را پخش کند.

## Syntax

```js-nolint
canPlayType(type)
```

### Parameters

- `type`
  - : رشته‌ای که [نوع MIME](/en-US/docs/Web/HTTP/Guides/MIME_types) رسانه و (به‌صورت اختیاری) یک [`codecs` parameter](/en-US/docs/Web/Media/Guides/Formats/codecs_parameter) شامل فهرستی از کدک‌های پشتیبانی‌شده را که با کاما جدا شده‌اند، مشخص می‌کند.

### Return value

رشته‌ای که نشان می‌دهد چقدر احتمال دارد رسانه قابل پخش باشد.
این رشته یکی از مقادیر زیر خواهد بود:

- `""` (رشته خالی)
  - : رسانه روی دستگاه فعلی قابل پخش نیست.
- `probably`
  - : رسانه به احتمال زیاد روی این دستگاه قابل پخش است.
- `maybe`
  - : اطلاعات کافی برای تعیین اینکه رسانه قابل پخش است یا نه وجود ندارد (تا زمانی که پخش واقعاً امتحان نشود).

## Examples

```js
let obj = document.createElement("video");
console.log(obj.canPlayType("video/mp4")); // "maybe"
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("HTMLMediaElement")}}: رابطی که برای تعریف متد `HTMLMediaElement.canPlayType()` استفاده می‌شود
- {{domxref("MediaCapabilities")}}
- [رسیدگی به مشکلات پشتیبانی رسانه در محتوای وب](/en-US/docs/Web/Media/Guides/Formats/Support_issues)
- [راهنمای نوع رسانه و فرمت](/en-US/docs/Web/Media/Guides/Formats)
- [کدک‌ها در انواع رایج رسانه](/en-US/docs/Web/Media/Guides/Formats/codecs_parameter)