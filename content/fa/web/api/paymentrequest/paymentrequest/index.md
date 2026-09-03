---
title: "PaymentRequest: PaymentRequest() constructor"
short-title: PaymentRequest()
slug: Web/API/PaymentRequest/PaymentRequest
page-type: web-api-constructor
browser-compat: api.PaymentRequest.PaymentRequest
---

{{securecontext_header}}{{APIRef("Payment Request API")}}

سازندهٔ **`PaymentRequest()`** یک شیء {{domxref("PaymentRequest")}} جدید می‌سازد که برای مدیریت فرایند تولید، اعتبارسنجی و ارسال یک درخواست پرداخت استفاده می‌شود.

## نحو (Syntax)

```js-nolint
new PaymentRequest(methodData, details)
new PaymentRequest(methodData, details, options)
```

### پارامترها

- `methodData`
  - : شامل آرایه‌ای از شناسه‌های روش‌های پرداختی است که وب‌سایت فروشنده می‌پذیرد و همچنین هر دادهٔ مرتبط با آن روش‌های پرداخت. هر آیتم در این آرایه شامل فیلدهای زیر است:
    - `supportedMethods`
      - : رشته‌ای حاوی [شناسهٔ روش پرداخت](/en-US/docs/Web/API/Payment_Request_API/Concepts#payment_method_identifiers). این مقدار یا یک URL است یا یکی از [شناسه‌های استاندارد روش پرداخت](/en-US/docs/Web/API/Payment_Request_API/Concepts#standardized_payment_method_identifiers). مقدار و ساختار فیلد `data` بسته به مقدار فیلد `supportedMethods` متفاوت خواهد بود.

    - `data`
      - : یک شیء قابل تبدیل به JSON که اطلاعات اختیاری مورد نیاز روش‌های پرداخت پشتیبانی‌شده را فراهم می‌کند. این داده باید با نوع مورد انتظار پردازندهٔ پرداخت که توسط `supportedMethods` مشخص شده است مطابقت داشته باشد. توسعه‌دهندگان باید برای اطلاع از شکل مورد انتظار شیء داده، با کنترل‌کنندهٔ روش‌های پرداخت مشورت کنند. اگر `supportedMethods` برابر با `secure-payment-confirmation` باشد، `data` باید با دیکشنری {{domxref("SecurePaymentConfirmationRequest")}} مطابقت داشته باشد.

- `details`
  - : اطلاعاتی دربارهٔ تراکنش درخواستی فراهم می‌کند. این پارامتر شامل فیلدهای زیر است:
    - `total`
      - : مبلغ کل درخواست پرداخت.
    - `id` {{optional_inline}}
      - : یک شناسهٔ آزاد برای این درخواست پرداخت. اگر مقداری ارائه نشود، مرورگر یکی می‌سازد.
    - `displayItems`
      - : آرایه‌ای از آیتم‌های خطی (line items) اختیاری برای درخواست پرداخت که عامل کاربر ممکن است نمایش دهد، مانند جزئیات محصول، مالیات و حمل‌ونقل.
    - `shippingOptions`
      - : گزینه‌های حمل‌ونقلی که کاربر می‌تواند از میان آن‌ها انتخاب کند. اگر این دنباله خالی باشد، نشان می‌دهد که فروشنده نمی‌تواند به آدرس حمل‌ونقل فعلی ارسال کند. گزینهٔ پیش‌فرض حمل‌ونقل ممکن است در این دنباله مشخص شده باشد.
    - `modifiers`
      - : تغییردهنده‌هایی برای روش‌های پرداخت خاص؛ مثلاً تنظیم مبلغ کل بر اساس روش پرداخت. این پارامتر شامل فیلدهای زیر است:
        - `additionalDisplayItems`
          - : آرایه‌ای از آیتم‌ها که به ویژگی `details.displayItems`追加 می‌شود. این ویژگی معمولاً برای افزودن یک آیتم خطی تخفیف یا هزینهٔ اضافه استفاده می‌شود که مبلغ متفاوت را در `details.modifiers.total` نشان می‌دهد.
        - `data`
          - : یک شیء قابل تبدیل به JSON که اطلاعات اختیاری مورد نیاز روش‌های پرداخت پشتیبانی‌شده را فراهم می‌کند.
        - `total`
          - : مبلغ کل برای درخواست پرداخت که مقدار `details.total` را لغو می‌کند. این معمولاً زمانی استفاده می‌شود که `details.modifiers.additionalItems` یک تخفیف یا یک خرید به درخواست اضافه می‌کند.

- `options` {{optional_inline}}
  - : به شما امکان می‌دهد گزینه‌هایی را تنظیم کنید که رفتار عامل کاربر را کنترل می‌کنند. این پارامتر شامل فیلدهای زیر است:
    - `requestPayerName`
      - : یک مقدار بولی که نشان می‌دهد آیا عامل کاربر باید نام پرداخت‌کننده را جمع‌آوری کرده و همراه با درخواست پرداخت ارسال کند. مقدار پیش‌فرض `false` است.
    - `requestPayerEmail`
      - : یک مقدار بولی که نشان می‌دهد آیا عامل کاربر باید آدرس ایمیل پرداخت‌کننده را جمع‌آوری کرده و همراه با درخواست پرداخت ارسال کند. مقدار پیش‌فرض `false` است.
    - `requestPayerPhone`
      - : یک مقدار بولی که نشان می‌دهد آیا عامل کاربر باید شماره تلفن پرداخت‌کننده را جمع‌آوری کرده و همراه با درخواست پرداخت ارسال کند. مقدار پیش‌فرض `false` است.
    - `requestShipping`
      - : یک مقدار بولی که نشان می‌دهد آیا عامل کاربر باید آدرس حمل‌ونقل پرداخت‌کننده را جمع‌آوری کرده و همراه با درخواست پرداخت ارسال کند. اگر این نوع را روی `true` تنظیم کنید، باید یک `shippingType` مناسب انتخاب کنید. مقدار پیش‌فرض `false` است.
    - `shippingType`
      - : به شما امکان می‌دهد مشخص کنید که رابط کاربری چگونه به حمل‌ونقل اشاره می‌کند، زمانی که کلمهٔ «shipping» برای مورد استفادهٔ شما مناسب نیست. برای مثال، در کشورهای انگلیسی‌زبان می‌گویید «pizza delivery» نه «pizza shipping». مقادیر معتبر عبارت‌اند از `"shipping"`، `"delivery"` و `"pickup"`. علامت‌های نقل‌قول باید گنجانده شوند. مقدار پیش‌فرض `"shipping"` است.

### مقدار بازگشتی

یک شیء {{domxref("PaymentRequest")}} جدید که مطابق با پارامترهای ورودی پیکربندی شده است.

### استثناها (Exceptions)

- `SecurityError` {{domxref("DOMException")}}
  - : استفاده از این ویژگی توسط [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) مسدود شده است.

## مثال‌ها

مثال زیر حداقل قابلیت را نشان می‌دهد و در عوض تمرکز خود را بر نمایش زمینهٔ کامل instantiate کردن یک شیء `PaymentRequest` می‌گذارد.

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

try {
  const request = new PaymentRequest(supportedInstruments, details, options);
  // Add event listeners here.
  // Call show() to trigger the browser's payment flow.
  request
    .show()
    .then((instrumentResponse) => {
      // Do something with the response from the UI.
    })
    .catch((err) => {
      // Do something with the error from request.show().
    });
} catch (e) {
  // Catch any other errors.
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}