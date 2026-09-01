---
title: "FetchEvent: resultingClientId property"
short-title: resultingClientId
slug: Web/API/FetchEvent/resultingClientId
page-type: web-api-instance-property
browser-compat: api.FetchEvent.resultingClientId
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

ویژگی فقطخواندنی **`resultingClientId`** در رابط {{domxref("FetchEvent")}}، مقدار {{domxref("Client.id", "id")}} از {{domxref("Client", "client")}} است که در حین پیمایش صفحه، جایگزین کلاینت قبلی می‌شود.

برای مثال، هنگام پیمایش از صفحه A به صفحه B، `resultingClientId` شناسه کلاینتی است که با صفحه B مرتبط است.

اگر درخواست fetch یک درخواست زیرمنبع باشد یا [`destination`](/en-US/docs/Web/API/Request/destination) درخواست `report` باشد، `resultingClientId` یک رشته خالی خواهد بود.

## Value

یک رشته.

## Examples

```js
self.addEventListener("fetch", (event) => {
  console.log(event.resultingClientId);
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Using Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- [Service workers basic code example](https://github.com/mdn/dom-examples/tree/main/service-worker/simple-service-worker)
- [Using web workers](/en-US/docs/Web/API/Web_Workers_API/Using_web_workers)