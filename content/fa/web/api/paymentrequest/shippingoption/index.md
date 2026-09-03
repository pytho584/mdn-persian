---
title: "PaymentRequest: shippingOption property"
short-title: shippingOption
slug: Web/API/PaymentRequest/shippingOption
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.PaymentRequest.shippingOption
---

{{APIRef("Payment Request API")}}{{SecureContext_Header}}{{Deprecated_Header}}{{Non-standard_Header}}

ویژگی فقط‌خواندنی **`shippingOption`** در رابط {{domxref('PaymentRequest')}} یا شناسه یک گزینه حمل‌ونقل انتخاب‌شده را برمی‌گرداند، یا `null` (اگر هیچ گزینه حمل‌ونقلی برای انتخاب تنظیم نشده باشد)، یا گزینه حمل‌ونقلی که توسط کاربر انتخاب شده است. زمانی که هیچ گزینه حمل‌ونقلی با وضعیت «selected» ارائه نشود، این ویژگی به‌صورت اولیه `null` است.

این ویژگی فقط زمانی مقداردهی می‌شود که سازنده با پرچم `requestShipping` برابر با `true` فراخوانی شود. اگر `requestShipping` برابر با `false` باشد (یا وجود نداشته باشد)، `shippingOption` مقدار `null` برمی‌گرداند، حتی اگر توسعه‌دهنده یک گزینه حمل‌ونقل انتخاب‌شده ارائه کند.

## مقدار

یک شیء یا `null`.

## مثال‌ها

در مثال زیر، رویدادهای {{domxref('PaymentRequest.shippingaddresschange_event', 'shippingaddresschange')}} و {{domxref('PaymentRequest.shippingoptionchange_event', 'shippingoptionchange')}} ارسال می‌شوند. در هر رویداد، متد `updateWith()` فراخوانی می‌شود؛ یکی با استفاده از یک promise و دیگری با استفاده از یک شیء ساده جاوااسکریپت. این به‌روزرسانی هم‌زمان و غیرهم‌زمان برگه پرداخت را نشان می‌دهد.

```js
const request = new PaymentRequest(methodData, details, options);
// Async update to details
request.onshippingaddresschange = (ev) => {
  ev.updateWith(checkShipping(request));
};
// Sync update to the total
request.onshippingoptionchange = (ev) => {
  const shippingOption = shippingOptions.find(
    (option) => option.id === request.id,
  );
  const newTotal = {
    currency: "USD",
    label: "Total due",
    value: calculateNewTotal(shippingOption),
  };
  ev.updateWith({ ...details, total: newTotal });
};
async function checkShipping(request) {
  try {
    const json = request.shippingAddress.toJSON();

    await ensureCanShipTo(json);
    const { shippingOptions, total } = await calculateShipping(json);

    return { ...details, shippingOptions, total };
  } catch (err) {
    return { ...details, error: `Sorry! we can't ship to your address.` };
  }
}
```

## سازگاری مرورگر

{{Compat}}