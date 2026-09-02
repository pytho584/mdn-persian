---
title: "Location: port property"
short-title: port
slug: Web/API/Location/port
page-type: web-api-instance-property
browser-compat: api.Location.port
---

{{ApiRef("Location")}}

ویژگی **`port`** از رابط {{domxref("Location")}} رشتهای است که شمارهٔ پورتِ URL را دربردارد. اگر پورت، مقدار پیشفرضِ پروتکل باشد (`80` برای `ws:` و `http:`، `443` برای `wss:` و `https:`، و `21` برای `ftp:`)، این ویژگی شامل یک رشتهٔ خالی (`""`) است.

این ویژگی را میتوان برای تغییر پورتِ URL مقداردهی کرد. اگر URL هیچ {{domxref("Location.host", "host")}} نداشته باشد یا طرح (scheme) آن `file:` باشد، مقداردهی این ویژگی هیچ اثری ندارد. این ویژگی همچنین شماره‌های پورت نامعتبر را بی‌سروصدا نادیده می‌گیرد.

برای اطلاعات بیشتر، به {{domxref("URL.port")}} مراجعه کنید.

## مقدار

یک رشته (string).

## مثال‌ها

```js
// Assume current page is at https://developer.mozilla.org/en-US/docs/Location/port
const result = location.port; // Returns:''
```

```js
// Assume another page is at https://developer.mozilla.org:8888/en-US/docs/Location/port
const result = location.port; // Returns:'8888'
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}