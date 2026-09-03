---
title: "Navigator: buildID property"
short-title: buildID
slug: Web/API/Navigator/buildID
page-type: web-api-instance-property
status:
  - non-standard
browser-compat: api.Navigator.buildID
---

{{ApiRef("HTML DOM")}}{{Non-standard_Header}}

شناسه ساخت مرورگر را بازمی‌گرداند. در مرورگرهای مدرن، این ویژگی به‌عنوان اقدامی برای حفظ حریم خصوصی، یک برچسب زمانی ثابت را برمی‌گرداند؛ برای مثال، در فایرفاکس ۶۴ به بعد مقدار `20181001000000` را بازمی‌گرداند.

## مقدار

یک رشته است که شناسه ساخت برنامه را نشان می‌دهد. شناسه ساخت به شکل `YYYYMMDDHHMMSS` است.

## مثال‌ها

```js
console.log(navigator.buildID);
```

## مشخصات

بخشی از هیچ استاندارد عمومی نیست.

## سازگاری مرورگرها

{{Compat}}