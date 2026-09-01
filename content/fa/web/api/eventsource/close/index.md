---
title: "EventSource: close() method"
short-title: close()
slug: Web/API/EventSource/close
page-type: web-api-instance-method
browser-compat: api.EventSource.close
---

{{APIRef("Server Sent Events")}}{{AvailableInWorkers}}

متد **`close()`** در رابط {{domxref("EventSource")}} اگر اتصالی برقرار شده باشد، آن را می‌بندد و ویژگی {{domxref("EventSource.readyState")}} را روی `2` (بسته) قرار می‌دهد.

> [!NOTE]
> اگر اتصال از قبل بسته شده باشد، این متد هیچ کاری انجام نمی‌دهد.

## سینتکس

```js-nolint
close()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
const button = document.querySelector("button");
const evtSource = new EventSource("sse.php");

button.onclick = () => {
  console.log("Connection closed");
  evtSource.close();
};
```

> [!NOTE]
> می‌توانید مثال کامل این کار را در GitHub ببینید — به [Simple SSE demo using PHP](https://github.com/mdn/dom-examples/tree/main/server-sent-events) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("EventSource")}}