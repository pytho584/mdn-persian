---
title: "Event: cancelBubble property"
short-title: cancelBubble
slug: Web/API/Event/cancelBubble
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.Event.cancelBubble
---

{{APIRef("DOM")}}{{Deprecated_Header}}{{AvailableInWorkers}}

ویژگی **`cancelBubble`** از رابط {{domxref("Event")}} منسوخ شده است. به‌جای آن از {{domxref("Event.stopPropagation()")}} استفاده کنید. تنظیم مقدار آن به `true` قبل از بازگشت از یک هندلر رویداد، از انتشار رویداد جلوگیری می‌کند. در پیاده‌سازی‌های جدیدتر، تنظیم آن به `false` هیچ اثری ندارد. برای جزئیات به [سازگاری مرورگر](#browser_compatibility) مراجعه کنید.

## مقدار

یک مقدار بولی. مقدار `true` به این معناست که رویداد نباید بیشتر منتشر شود.

## مثال

```js
elem.onclick = (event) => {
  // Do cool things here
  event.cancelBubble = true;
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}