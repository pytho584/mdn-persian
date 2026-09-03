---
title: PresentationConnectionList
slug: Web/API/PresentationConnectionList
page-type: web-api-interface
status:
  - experimental
browser-compat: api.PresentationConnectionList
---

{{securecontext_header}}{{SeeCompatTable}}{{APIRef("Presentation API")}}

`PresentationConnectionList` مجموعهای از اتصالهای ارائهٔ ورودی (incoming presentation connections) است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref('PresentationConnectionList.connections')}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : مجموعهٔ اتصال‌های خاتمه‌نیافته از نوع {{DOMxRef("PresentationConnection")}} موجود در [مجموعهٔ کنترل‌کننده‌های ارائه](https://www.w3.org/TR/presentation-api/#dfn-set-of-presentation-controllers) را برمی‌گرداند.

## رویدادها

- {{domxref('PresentationConnectionList/connectionavailable_event', "connectionavailable")}} {{Experimental_Inline}}
  - هرگاه یک [اتصال ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-connection) جدید در دسترس قرار گیرد، این رویداد صادر می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
