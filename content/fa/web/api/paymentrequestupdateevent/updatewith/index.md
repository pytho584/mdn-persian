---
title: "PaymentRequestUpdateEvent: updateWith() method"
short-title: updateWith()
slug: Web/API/PaymentRequestUpdateEvent/updateWith
page-type: web-api-instance-method
browser-compat: api.PaymentRequestUpdateEvent.updateWith
---

{{APIRef("Payment Request API")}}{{securecontext_header}}

متد **`updateWith()`** از رابط {{domxref("PaymentRequestUpdateEvent")}}، جزئیات یک {{domxref("PaymentRequest")}} موجود را به‌روزرسانی می‌کند.

## سینتکس

```js-nolint
updateWith(details)
```

### پارامترها

- `details`
  - : یک شیء یا یک {{jsxref("Promise")}} که به یک شیء resolve می‌شود و تغییرات اعمال‌شده به درخواست پرداخت را مشخص می‌کند:
    - `displayItems` {{optional_inline}}
      - : آرایه‌ای از اشیاء که هر کدام یک آیتم ردیف (line item) برای درخواست پرداخت را توصیف می‌کند. این اشیاء بیانگر ردیف‌های یک رسید یا فاکتور هستند و هر کدام ویژگی‌های زیر را دارند:
        - `amount`
          - : شیئی که ارزش پولی آیتم را توصیف می‌کند. این شیء شامل فیلدهای زیر است:
            - `currency`
              - : رشته‌ای حاوی شناسهٔ ارز معتبر سه‌حرفی [ISO 4217](https://www.iso.org/iso-4217-currency-codes.html) (استاندارد [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217)) که ارز مورد استفاده برای `value` پرداخت را نشان می‌دهد.
            - `value`
              - : رشته‌ای حاوی مقدار اعشاری معتبر که مقدار پول تشکیل‌دهندهٔ مبلغ پرداخت را نشان می‌دهد. این رشته فقط می‌تواند شامل یک «-» اختیاری در ابتدا برای نشان دادن مقدار منفی، سپس یک یا چند رقم از 0 تا 9، و یک نقطهٔ اعشار اختیاری (".", بدون توجه به locale) باشد که پس از آن حداقل یک رقم دیگر بیاید. هیچ فاصلهٔ خالی (whitespace) مجاز نیست.
        - `label`
          - : رشته‌ای که نام یا توضیح قابل‌خواندن برای انسان از آیتم یا خدمتی که برای آن هزینه دریافت می‌شود را مشخص می‌کند. این مقدار ممکن است بسته به طراحی رابط توسط {{Glossary("user agent")}} به کاربر نمایش داده شود.
        - `pending`
          - : یک مقدار بولی که اگر `amount` مشخص‌شده هنوز نهایی نشده باشد، `true` است. می‌توان از آن برای نمایش مواردی مانند هزینهٔ حمل یا مالیات استفاده کرد که به انتخاب آدرس حمل، گزینهٔ حمل و مانند آن بستگی دارند. {{Glossary("user agent")}} ممکن است این اطلاعات را نمایش دهد، اما الزامی به این کار ندارد.

    - `error` {{optional_inline}} {{deprecated_inline}} {{non-standard_inline}}
      - : رشته‌ای که پیام خطایی را برای نمایش به کاربر مشخص می‌کند. هنگام فراخوانی `updateWith()`، گنجاندن `error` در داده‌های به‌روزشده باعث می‌شود {{Glossary("user agent")}} متن را به‌عنوان یک پیام خطای عمومی نمایش دهد. برای خطاهای مربوط به فیلد خاصی از آدرس، از فیلد `shippingAddressErrors` استفاده کنید.

    - `modifiers` {{optional_inline}}
      - : یک {{jsxref("Array")}} از اشیاء `PaymentDetailsModifier` که ویژگی‌های آن‌ها در {{domxref("PaymentRequestEvent.modifiers")}} توضیح داده شده است.

        مثلاً می‌توانید از آن برای تنظیم مبلغ کل پرداخت بر اساس روش پرداخت انتخاب‌شده استفاده کنید («۵٪ تخفیف نقدی!»).

    - `shippingAddressErrors` {{optional_inline}} {{deprecated_inline}} {{non-standard_inline}}
      - : شیئی که برای هر ویژگی از آدرس حمل که نتوانسته اعتبارسنجی شود، یک پیام خطا در بر می‌گیرد.
    - `shippingOptions` {{optional_inline}} {{deprecated_inline}} {{non-standard_inline}}
      - : آرایه‌ای از اشیاء که هر کدام یکی از گزینه‌های حمل موجود را که کاربر می‌تواند از بین آن‌ها انتخاب کند، توصیف می‌کند.
    - `total` {{optional_inline}}
      - : شیئی با همان ویژگی‌های اشیاء موجود در `displayItems` که مبلغ کل به‌روزشدهٔ پرداخت را فراهم می‌کند. مطمئن شوید که این مقدار با مجموع همهٔ آیتم‌های `displayItems` برابر است. _این مقدار به‌صورت خودکار محاسبه نمی‌شود_. هر زمان که مبلغ کل قابل‌پرداخت تغییر کند، باید این مقدار را خودتان به‌روزرسانی کنید. این امر به شما امکان می‌دهد برای مدیریت مواردی مانند مالیات، تخفیف‌ها و سایر تعدیل‌های قیمت کل انعطاف‌پذیری داشته باشید.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}