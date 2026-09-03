---
title: "PaymentAddress"
---

---
title: PaymentAddress
slug: Web/API/PaymentAddress
page-type: web-api-interface
status:
  - deprecated
  - non-standard
browser-compat: api.PaymentAddress
---

{{APIRef("Payment Request API")}}{{SecureContext_Header}}{{Deprecated_Header}}{{Non-standard_Header}}

رابطهٔ **`PaymentAddress`** در [Payment Request API](/en-US/docs/Web/API/Payment_Request_API) برای ذخیره‌سازی اطلاعات آدرس حمل‌ونقل یا پرداخت استفاده می‌شود.

ممکن است مراجعه به مطالب [استاندارد S42 آدرس‌دهی](https://www.upu.int/en/Postal-Solutions/Programmes-Services/Addressing-Solutions#addressing-s42-standard) در وب‌سایت اتحادیهٔ جهانی پست مفید باشد؛ این مطالب اطلاعاتی دربارهٔ استانداردهای بین‌المللی آدرس‌های پستی ارائه می‌دهند.

## ویژگی‌های نمونه

- {{domxref('PaymentAddress.addressLine')}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : آرایه‌ای از رشته‌ها که هر خط از آدرس را که در سایر ویژگی‌ها ذکر نشده است ارائه می‌دهد. اندازه و محتوای دقیق آن بسته به کشور یا مکان متفاوت است و می‌تواند شامل مواردی مانند نام خیابان، شمارهٔ خانه، شمارهٔ آپارتمان، مسیر تحویل روستایی، دستورالعمل‌های توصیفی یا شمارهٔ صندوق پستی باشد.
- {{domxref('PaymentAddress.country')}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : رشته‌ای که کشور محل آدرس را با استفاده از استاندارد [ISO-3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) مشخص می‌کند. این رشته همیشه به شکل حروف بزرگ استاندارد ارائه می‌شود. چند نمونه از مقادیر معتبر `country`: `"US"`، `"GB"`، `"CN"` یا `"JP"`.
- {{domxref('PaymentAddress.city')}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : رشته‌ای که بخش شهر یا ناحیهٔ شهری آدرس را شامل می‌شود.
- {{domxref('PaymentAddress.dependentLocality')}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : رشته‌ای که محلهٔ وابسته یا زیرمجموعهٔ یک شهر را مشخص می‌کند؛ برای مثال، محله، ناحیه، منطقه یا محل وابسته در بریتانیا.
- {{domxref('PaymentAddress.organization')}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : رشته‌ای که نام سازمان، شرکت، تجارت یا مؤسسه را در آدرس پرداخت مشخص می‌کند.
- {{domxref('PaymentAddress.phone')}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : رشته‌ای که شمارهٔ تلفن گیرنده یا شخص تماس را مشخص می‌کند.
- {{domxref('PaymentAddress.postalCode')}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : رشته‌ای که کد مورد استفاده یک حوزهٔ قضایی برای مسیریابی مرسولات پستی را مشخص می‌کند؛ برای مثال، کد پستی ZIP در ایالات متحده یا کد PIN در هند.
- {{domxref('PaymentAddress.recipient')}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : رشته‌ای که نام گیرنده، خریدار یا شخص تماس را در آدرس پرداخت مشخص می‌کند.
- {{domxref('PaymentAddress.region')}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : رشته‌ای حاوی بالاترین سطح تقسیمات اداری کشور؛ برای مثال، ایالت، استان، اوبلاست یا استان (در ژاپن).
- {{domxref('PaymentAddress.sortingCode')}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : رشته‌ای که کد مرتب‌سازی پستی مانند کد مورد استفاده در فرانسه را ارائه می‌دهد.

> [!NOTE]
> ویژگی‌هایی که مقادیری برای آن‌ها مشخص نشده باشد، شامل رشته‌های خالی هستند.

## روش‌های نمونه

- {{domxref('PaymentAddress.toJSON()')}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : یک سریال‌ساز استاندارد که نمایش JSON از ویژگی‌های شیء `PaymentAddress` را بازمی‌گرداند.

## مثال‌ها

در مثال زیر، از سازندهٔ {{domxref("PaymentRequest.PaymentRequest","PaymentRequest()")}} برای ایجاد یک درخواست پرداخت جدید استفاده می‌شود که سه شیء به‌عنوان پارامتر دریافت می‌کند — یکی شامل جزئیات روش‌های پرداختی که می‌توانند برای پرداخت استفاده شوند، یکی شامل جزئیات سفارش واقعی (مانند اقلام خریداری‌شده و گزینه‌های حمل‌ونقل) و یک شیء اختیاری حاوی گزینه‌های بیشتر.

اولی از این سه شیء (در مثال زیر `supportedInstruments`) شامل یک ویژگی `data` است که باید با ساختار تعریف‌شده توسط روش پرداخت مطابقت داشته باشد.

```js
const supportedInstruments = [
  {
    supportedMethods: "https://example.com/pay",
  },
];

const details = {
  total: { label: "Donation", amount: { currency: "USD", value: "65.00" } },
  displayItems: [
    {
      label: "Original donation amount",
      amount: { currency: "USD", value: "65.00" },
    },
  ],
  shippingOptions: [
    {
      id: "standard",
      label: "Standard shipping",
      amount: { currency: "USD", value: "0.00" },
      selected: true,
    },
  ],
};

const options = { requestShipping: true };

async function doPaymentRequest() {
  const request = new PaymentRequest(supportedInstruments, details, options);
  // Add event listeners here.
  // Call show() to trigger the browser's payment flow.
  const response = await request.show();
  // Process payment.
  const json = response.toJSON();
  const httpResponse = await fetch("/pay/", { method: "POST", body: json });
  const result = httpResponse.ok ? "success" : "failure";

  await response.complete(result);
}
doPaymentRequest();
```

پس از اینکه جریان پرداخت با استفاده از {{domxref("PaymentRequest.show()")}} آغاز شد و promise با موفقیت حل شد، شیء {{domxref("PaymentResponse")}} موجود از promise حل‌شده (در بالا `instrumentResponse`) دارای ویژگی {{domxref("PaymentResponse.details")}} حاوی جزئیات پاسخ خواهد بود. این ویژگی باید با ساختار تعریف‌شده توسط ارائه‌دهندهٔ روش پرداخت مطابقت داشته باشد.

## سازگاری مرورگر

{{Compat}}