```markdown
---
title: "CloseEvent: reason property"
short-title: reason
slug: Web/API/CloseEvent/reason
page-type: web-api-instance-property
browser-compat: api.CloseEvent.reason
---

{{APIRef("Websockets API")}}{{AvailableInWorkers}}

ویژگی فقط‑خواندنی **`reason`** از رابط {{domxref("CloseEvent")}}، [دلیل بسته شدن اتصال WebSocket](https://www.rfc-editor.org/info/rfc6455/#section-7.1.6) را که سرور برای بستن اتصال ارائه داده است، برمی‌گرداند. این مقدار یک توضیح متنی مختصر و قابل‌فهم برای انسان در مورد علت بسته شدن اتصال است.

## مقدار

یک رشته (string).

## مثال‌ها

مثال زیر مقدار `reason` را در کنسول چاپ می‌کند.

```js
WebSocket.onclose = (event) => {
  console.log(event.reason);
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [RFC 6455](https://www.rfc-editor.org/info/rfc6455/) (مشخصات پروتکل WebSocket)
```