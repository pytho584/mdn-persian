---
title: "PresentationConnection: state property"
short-title: state
slug: Web/API/PresentationConnection/state
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PresentationConnection.state
---

{{APIRef("Presentation API")}}{{SeeCompatTable}}{{SecureContext_Header}}

ویژگی **`state`** وضعیت فعلی [اتصال ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-connection) را منعکس می‌کند. بسته به [`PresentationConnectionState`](https://www.w3.org/TR/presentation-api/#idl-def-presentationconnectionstate) فعلی، ویژگی `state` می‌تواند یکی از مقادیر زیر را داشته باشد.

- **`connecting`**: عامل کاربر در حال تلاش برای [برقراری اتصال ارائه](https://www.w3.org/TR/presentation-api/#dfn-establish-a-presentation-connection) با [زمینه مرور مقصد](https://www.w3.org/TR/presentation-api/#dfn-destination-browsing-context) است. این حالت اولیه هنگام ایجاد یک شیء [`PresentationConnection`](https://www.w3.org/TR/presentation-api/#idl-def-presentationconnection) است.
- **`connected`**: [اتصال ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-connection) برقرار شده و ارتباط ممکن است.
- **`closed`**: [اتصال ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-connection) بسته شده است یا نتوانسته باز شود. اتصال ممکن است با فراخوانی [`reconnect()`](https://www.w3.org/TR/presentation-api/#dom-presentationrequest-reconnect) دوباره باز شود. در این حالت هیچ ارتباطی ممکن نیست.
- **`terminated`**: [زمینه مرور دریافت‌کننده](https://www.w3.org/TR/presentation-api/#dfn-receiving-browsing-context) خاتمه یافته است. هر [اتصال ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-connection) به آن [ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation) نیز خاتمه یافته و قابل بازگشایی نیست. هیچ ارتباطی ممکن نیست.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}