---
title: "HTMLAnchorElement: port property"
short-title: port
slug: Web/API/HTMLAnchorElement/port
page-type: web-api-instance-property
browser-compat: api.HTMLAnchorElement.port
---

{{ApiRef("HTML DOM")}}

ویژگی **`port`** از رابط {{domxref("HTMLAnchorElement")}} یک رشته است که شامل شماره پورتِ `href` عنصر `<a>` می‌شود. اگر پورت، مقدار پیش‌فرضِ پروتکل باشد (`80` برای `ws:` و `http:`، `443` برای `wss:` و `https:`، و `21` برای `ftp:`)، این ویژگی یک رشتهٔ خالی (`""`) را در بر می‌گیرد.

این ویژگی را می‌توان برای تغییر پورت URL تنظیم کرد. اگر URL میزبان ({{domxref("HTMLAnchorElement.host", "host")}}) نداشته باشد یا طرح (scheme) آن `file:` باشد، تنظیم این ویژگی هیچ تأثیری نخواهد داشت. همچنین شماره پورت‌های نامعتبر را بی‌صدا نادیده می‌گیرد.

برای اطلاعات بیشتر به {{domxref("URL.port")}} مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

### دریافت پورت از یک پیوند anchor

```js
// An <a id="myAnchor" href="https://developer.mozilla.org:443/en-US/docs/HTMLAnchorElement"> element is in the document
const anchor = document.getElementByID("myAnchor");
anchor.port; // returns ''
```

```js
// Another <a id="myAnchor" href="https://developer.mozilla.org:8888/en-US/docs/HTMLAnchorElement"> element is in the document
const anchor = document.getElementByID("myAnchor");
anchor.port; // Returns:'8888'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("HTMLAnchorElement")}} که این ویژگی به آن تعلق دارد.