---
title: "Presentation: receiver property"
short-title: receiver
slug: Web/API/Presentation/receiver
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Presentation.receiver
---

{{APIRef("Presentation")}}{{SeeCompatTable}}{{SecureContext_Header}}

ویژگی **فقط‑خواندنی** {{domxref("Presentation")}} با نام `receiver` که تنها در زمینه‌های مرورگری در دسترس است که در **حال دریافت یک ارائه** هستند، شیء {{domxref("PresentationReceiver")}} را برمی‌گرداند. این شیء برای دسترسی و ارتباط با زمینه‌ای از مرورگر که ارائه را کنترل می‌کند، قابل استفاده است. این ویژگی وقتی از خارج از زمینه‌ای که در حال دریافت ارائه است، فراخوانی شود، همیشه `null` است.

## مقدار

اگر کد در زمینه‌ای اجرا شود که در حال دریافت یک ارائه است، مقدار بازگشتی یک {{domxref("PresentationReceiver")}} خواهد بود که می‌توان از آن برای ارتباط با زمینه‌ای که منبع ارائه است استفاده کرد.

اگر زمینه‌ی فعلی در حال دریافت ارائه نباشد، `receiver` برابر با `null` است.

## مثال‌ها

### تشخیص اینکه آیا زمینه در حال دریافت ارائه است یا نه

به راحتی می‌توانید تشخیص دهید که آیا زمینه دریافت‌کننده‌ی یک ارائه است یا نه، با بررسی مقدار `navigator.presentation.receiver`. اگر این مقدار غیر از `null` باشد، زمینه واقعاً در حال دریافت یک ارائه است. اگر `null` باشد، هیچ ارائه‌ی ورودی‌ای وجود ندارد.

```js
footer.textContent = navigator.presentation.receiver
  ? "Receiving presentation"
  : "(idle)";
```

### دسترسی به لیست اتصال‌ها

این مثال از `receiver` برای دسترسی به لیست اتصال‌های ورودی و ساخت و نمایش لیستی از رشته‌های شناسه‌ی آن اتصال‌ها استفاده می‌کند.

```js
const listElem = document.getElementById("connection-view");

navigator.presentation.receiver.connectionList.then((connections) => {
  connections.forEach((connection) => {
    listElem.appendChild(document.createElement("li")).textContent =
      connection.id;
  });
});
```

پس از دسترسی به عنصر لیست خروجی در متغیر `connectionView`، از `navigator.presentation.receiver` برای دریافت یک ارجاع به شیء {{domxref("PresentationReceiver")}} مربوط به این زمینه استفاده می‌شود، و از {{domxref("PresentationReceiver.connectionList", "connectionList")}} آن برای دریافت یک {{jsxref("Promise")}} استفاده می‌شود که وقتی لیست در دسترس باشد فراخوانی می‌شود.

مدیر وعده (handler) یک آرایه از اتصال‌های ورودی را به عنوان پارامتر ورودی خود دریافت می‌کند. با استفاده از {{jsxref("Array.forEach", "forEach()")}} روی آن‌ها پیمایش می‌کنیم و برای هر اتصال یک آیتم جدید به عنصر لیست `connectionView` اضافه می‌کنیم.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- Presentation API
- {{domxref("Presentation")}}
- {{domxref("PresentationReceiver")}}