---
title: "Element: prefix property"
short-title: prefix
slug: Web/API/Element/prefix
page-type: web-api-instance-property
browser-compat: api.Element.prefix
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`Element.prefix`** پیشوند فضای نام عنصر مشخص‌شده را برمی‌گرداند، یا اگر پیشوندی تعیین نشده باشد، مقدار `null` را برمی‌گرداند.

## مقدار

یک رشته.

## مثال‌ها

کد زیر رشته «x» را در کنسول ثبت می‌کند.

```xml
<x:div onclick="console.log(this.prefix)"/>
```

## یادداشت‌ها

این ویژگی فقط زمانی کار می‌کند که از تجزیه‌کننده‌ای استفاده شود که به فضای نام آگاه باشد؛ یعنی وقتی سند با یک نوع MIME مبتنی بر XML ارائه شود. این ویژگی برای اسناد HTML کار نخواهد کرد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.namespaceURI")}}
- {{domxref("Element.localName")}}
- {{domxref("Attr.prefix")}}