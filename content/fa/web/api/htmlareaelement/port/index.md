---
title: "HTMLAreaElement: port property"
short-title: port
slug: Web/API/HTMLAreaElement/port
page-type: web-api-instance-property
browser-compat: api.HTMLAreaElement.port
---

{{ApiRef("HTML DOM")}}

ویژگی **`port`** در رابط {{domxref("HTMLAreaElement")}} یک رشته (string) است که شماره پورت `href` عنصر `<area>` را شامل می‌شود. اگر پورت، پورت پیش‌فرض پروتکل باشد (`80` برای `ws:` و `http:`، `443` برای `wss:` و `https:` و `21` برای `ftp:`)، این ویژگی شامل یک رشته خالی، `""` است.

این ویژگی قابل تنظیم است تا پورت URL تغییر کند. اگر URL دارای {{domxref("HTMLAnchorElement.host", "host")}} نباشد یا طرح (scheme) آن `file:` باشد، تنظیم این ویژگی هیچ اثری ندارد. همچنین شماره پورت‌های نامعتبر را بی‌صدا نادیده می‌گیرد.

برای اطلاعات بیشتر به {{domxref("URL.port")}} مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

### دریافت پورت از یک پیوند area

```js
// یک عنصر <area id="myArea" href="https://developer.mozilla.org:443/en-US/docs/HTMLAreaElement"> در سند وجود دارد
const area = document.getElementByID("myArea");
area.port; // ‏'‎'‎' را برمی‌گرداند
```

```js
// یک عنصر <area id="myArea" href="https://developer.mozilla.org:8888/en-US/docs/HTMLAreaElement"> دیگر در سند وجود دارد
const area = document.getElementByID("myArea");
area.port; // ‏'8888' را برمی‌گرداند
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("HTMLAreaElement")}} که این ویژگی به آن تعلق دارد.