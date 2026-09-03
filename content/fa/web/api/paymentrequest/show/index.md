---
title: "PaymentRequest: show() method"
---

---
title: "PaymentRequest: show() method"
short-title: show()
slug: Web/API/PaymentRequest/show
page-type: web-api-instance-method
browser-compat: api.PaymentRequest.show
---

{{securecontext_header}}{{APIRef("Payment Request API")}}

متد **`show()`** در رابط {{domxref('PaymentRequest')}} به عامل کاربر (user agent) دستور می‌دهد تا فرایند نمایش و مدیریت رابط کاربری درخواست پرداخت را برای کاربر آغاز کند.

در هر لحظه، تنها یک درخواست پرداخت می‌تواند در حال رسیدگی باشد، آن هم در تمام اسناد. به محض فراخوانی متد `show()` یک `PaymentRequest`، هر فراخوانی دیگری از `show()` با خطای `AbortError` رد می‌شود، تا زمانی که Promise بازگشتی به پایان برسد؛ یا با یک {{domxref("PaymentResponse")}} که نتایج درخواست پرداخت را نشان می‌دهد تکمیل شود، یا با یک خطا رد شود.

> [!NOTE]
> در عمل، علیرغم اینکه مشخصات (specification) می‌گوید این کار امکان‌پذیر نیست، برخی مرورگرها از جمله Firefox از چند درخواست پرداخت فعال به طور همزمان پشتیبانی می‌کنند.

اگر معماری شما لزوماً تمام داده‌ها را در لحظهٔ نمونه‌سازی رابط پرداخت با فراخوانی `show()` آماده ندارد، پارامتر `detailsPromise` را مشخص کنید و یک {{jsxref("Promise")}} ارائه دهید که به محض آماده شدن داده‌ها تکمیل شود. اگر این پارامتر ارائه شود، `show()` اجازه نمی‌دهد کاربر با رابط پرداخت تعامل کند تا زمانی که Promise تکمیل شود، تا داده‌ها پیش از درگیر شدن کاربر با فرایند پرداخت به‌روزرسانی شوند.

پردازش نتیجه و در صورت لزوم فراخوانی {{domxref("PaymentResponse.retry()")}} برای تلاش مجدد یک پرداخت ناموفق، بسته به نیاز شما می‌تواند به صورت ناهمزمان (asynchronous) یا همزمان (synchronous) انجام شود. برای بهترین تجربهٔ کاربری، راه‌حل‌های ناهمزمان معمولاً بهترین گزینه هستند. بیشتر مثال‌ها در MDN و جاهای دیگر از [`async`](/en-US/docs/Web/JavaScript/Reference/Statements/async_function)/[`await`](/en-US/docs/Web/JavaScript/Reference/Operators/await) برای انتظار ناهمزمان در حین اعتبارسنجی نتایج و موارد مشابه استفاده می‌کنند.

## نحو

```js-nolint
show()
show(details)
```

### پارامترها

- `details` {{optional_inline}}
  - : یک شیء یا یک {{jsxref("Promise")}} که به یک شیء resolve می‌شود. اگر معماری شما ایجاب می‌کند که جزئیات درخواست پرداخت بین نمونه‌سازی رابط پرداخت و شروع تعامل کاربر با آن به‌روزرسانی شوند، این پارامتر را ارائه دهید. شیء باید اطلاعات به‌روزرسانی‌شده را شامل شود:
    - `displayItems` {{optional_inline}}
      - : آرایه‌ای از اشیاء که هر یک یک آیتم ردیفی (line item) از درخواست پرداخت را توصیف می‌کند. این‌ها نشان‌دهندهٔ آیتم‌های ردیفی در یک رسید یا فاکتور هستند که هر یک دارای ویژگی‌های زیر هستند:
        - `amount`
          - : شیئی که مقدار پولی آیتم را توصیف می‌کند. این شیء شامل فیلدهای زیر است:
            - `currency`
              - : رشته‌ای حاوی یک شناسهٔ ارز معتبر سه‌حرفی [ISO 4217](https://www.iso.org/iso-4217-currency-codes.html) ([ISO 4217](https://en.wikipedia.org/wiki/ISO_4217)) که ارز مورد استفاده برای `value` پرداخت را نشان می‌دهد.
            - `value`
              - : رشته‌ای حاوی یک مقدار اعشاری معتبر که مبلغ ارز تشکیل‌دهندهٔ مقدار پرداخت را نشان می‌دهد. این رشته تنها می‌تواند یک «-» اختیاری در ابتدا برای نشان دادن مقدار منفی داشته باشد، سپس یک یا چند رقم از 0 تا 9، و یک اعشار اختیاری («.»، بدون توجه به locale) که حداقل یک رقم دیگر دنبال شود. هیچ فاصلهٔ خالی مجاز نیست.
        - `label`
          - : رشته‌ای که یک نام یا توضیح قابل خواندن برای انسان از آیتم یا خدمتی که هزینهٔ آن دریافت می‌شود را مشخص می‌کند. بسته به طراحی رابط، ممکن است این مقدار توسط {{Glossary("user agent")}} به کاربر نمایش داده شود.
        - `pending`
          - : یک مقدار بولی که اگر `amount` مشخص‌شده هنوز نهایی نشده باشد، `true` است. این می‌تواند برای نمایش مواردی مانند هزینه‌های حمل‌ونقل یا مالیات که به انتخاب آدرس حمل‌ونقل، گزینهٔ حمل‌ونقل و موارد مشابه وابسته هستند استفاده شود. عامل کاربر ممکن است این اطلاعات را نمایش دهد اما الزامی ندارد.

    - `error` {{optional_inline}} {{deprecated_inline}} {{non-standard_inline}}
      - : رشته‌ای که یک پیام خطا برای نمایش به کاربر مشخص می‌کند. هنگام فراخوانی {{domxref("PaymentRequestUpdateEvent.updateWith", "updateWith()")}}، گنجاندن `error` در داده‌های به‌روزرسانی‌شده باعث می‌شود {{Glossary("user agent")}} متن را به عنوان یک پیام خطای عمومی نمایش دهد. برای خطاهای خاص فیلد آدرس، از فیلد `shippingAddressErrors` استفاده کنید.

    - `modifiers` {{optional_inline}}
      - : آرایه‌ای از اشیاء که هر یک یک اصلاح‌کننده (modifier) برای شناسه‌های روش پرداخت خاص را توصیف می‌کند، هر یک با ویژگی‌های زیر:
        - `supportedMethods`
          - : رشته‌ای که شناسهٔ روش پرداخت را نشان می‌دهد. شناسهٔ روش پرداخت فقط در صورتی اعمال می‌شود که کاربر این روش پرداخت را انتخاب کند.
        - `total` {{optional_inline}}
          - : شیئی که اگر کاربر این روش پرداخت را انتخاب کند، ویژگی `total` پارامتر `detailsPromise` را بازنویسی می‌کند. این ویژگی همان ورودی ویژگی `total` پارامتر `detailsPromise` را می‌پذیرد.
        - `additionalDisplayItems` {{optional_inline}}
          - : یک {{jsxref("Array")}} از اشیاء که آیتم‌های نمایشی اضافی ارائه می‌دهند که اگر کاربر این روش پرداخت را انتخاب کند، به ویژگی `displayItems` پارامتر `detailsPromise` اضافه می‌شوند. این ویژگی معمولاً برای افزودن یک آیتم ردیفی تخفیف یا هزینهٔ اضافی استفاده می‌شود که دلیل مبلغ کل متفاوت برای روش پرداخت انتخابی را نشان می‌دهد و ممکن است توسط عامل کاربر نمایش داده شود. این ویژگی همان ورودی ویژگی `displayItems` پارامتر `detailsPromise` را می‌پذیرد.
        - `data` {{optional_inline}}
          - : یک شیء قابل سریال‌سازی که اطلاعات اختیاری مورد نیاز روش‌های پرداخت پشتیبانی‌شده را فراهم می‌کند.

        برای مثال، می‌توانید از یکی برای تنظیم مبلغ کل پرداخت بر اساس روش پرداخت انتخابی استفاده کنید («۵٪ تخفیف نقدی!»).

    - `shippingAddressErrors` {{optional_inline}} {{deprecated_inline}} {{non-standard_inline}}
      - : شیئی که برای هر ویژگی از آدرس حمل‌ونقل که نتوانسته اعتبارسنجی شود، یک پیام خطا شامل می‌شود.
    - `shippingOptions` {{optional_inline}} {{deprecated_inline}} {{non-standard_inline}}
      - : آرایه‌ای از اشیاء که هر یک یک گزینهٔ حمل‌ونقل موجود را که کاربر می‌تواند از بین آن‌ها انتخاب کند توصیف می‌کند.
    - `total` {{optional_inline}}
      - : شیئی با همان ویژگی‌های اشیاء موجود در `displayItems` که مبلغ کل به‌روزرسانی‌شده‌ای برای پرداخت ارائه می‌دهد. مطمئن شوید که این مقدار با مجموع تمام آیتم‌های موجود در `displayItems` برابر است. _این مقدار به طور خودکار محاسبه نمی‌شود_. هر زمان که مبلغ کل تغییر کرد، باید این مقدار را خودتان به‌روزرسانی کنید. این به شما انعطاف می‌دهد که با مواردی مانند مالیات، تخفیف‌ها و سایر تنظیمات مبلغ کل شارژ شده به روش دلخواه برخورد کنید.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که در نهایت با یک {{domxref("PaymentResponse")}} resolve می‌شود. این Promise زمانی resolve می‌شود که کاربر درخواست پرداخت را بپذیرد (مثلاً با کلیک بر دکمهٔ «پرداخت» در برگهٔ پرداخت مرورگر).

### استثناها

استثناها پرتاب نمی‌شوند، اما زمانی که {{jsxref("Promise")}} رد می‌شود (reject) بازگردانده می‌شوند.

- `AbortError` {{domxref("DOMException")}}
  - : اگر {{Glossary("user agent")}} از قبل در حال نمایش برگهٔ پرداخت باشد بازگردانده می‌شود. تنها یک برگهٔ پرداخت ممکن است در هر زمان _در تمام اسناد بارگذاری‌شده توسط عامل کاربر_ قابل مشاهده باشد.

    همچنین اگر کاربر درخواست پرداخت را لغو کند، Promise با `AbortError` رد می‌شود.

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر همان پرداخت قبلاً برای این درخواست نمایش داده شده باشد بازگردانده می‌شود (وضعیت آن `interactive` است چون در حال نمایش است).
- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر عامل کاربر از روش‌های پرداخت مشخص‌شده در زمان فراخوانی سازندهٔ {{domxref("PaymentRequest.PaymentRequest","PaymentRequest")}} پشتیبانی نکند بازگردانده می‌شود.
- `SecurityError` {{domxref("DOMException")}}
  - : اگر فراخوانی `show()` در پاسخ به یک اقدام کاربر مانند رویداد {{domxref("Element/click_event", "click")}} یا {{domxref("Element/keyup_event", "keyup")}} نباشد بازگردانده می‌شود. دلایل دیگری که ممکن است `SecurityError` پرتاب شود به صلاحدید عامل کاربر است و ممکن است شامل موقعیت‌هایی مانند فراخوانی‌های بیش از حد `show()` در مدت کوتاه یا فراخوانی `show()` در حالی که درخواست‌های پرداخت توسط کنترل‌های والدین مسدود شده‌اند باشد.

## امنیت

[فعال‌سازی گذرای کاربر (Transient user activation)](/en-US/docs/Web/Security/Defenses/User_activation) لازم است. کاربر باید با صفحه یا یک عنصر رابط کاربری تعامل کند تا این ویژگی کار کند.

## نکات استفاده

رایج‌ترین الگوهای استفاده از `show()` شامل نحو [`async`](/en-US/docs/Web/JavaScript/Reference/Statements/async_function)/[`await`](/en-US/docs/Web/JavaScript/Reference/Operators/await) یا استفاده از `show().then().catch()` برای مدیریت پاسخ و هرگونه رد شدن احتمالی است. این‌ها به این شکل هستند:

### نحو async/await

استفاده از `await` برای انتظار برای تکمیل یک Promise، نوشتن کد رسیدگی به پرداخت‌ها را به‌طور خاص تمیز و خوانا می‌کند:

```js
async function processPayment() {
  try {
    const payRequest = new PaymentRequest(methodData, details, options);

    payRequest.onshippingaddresschange = (ev) =>
      ev.updateWith(checkAddress(payRequest));
    payRequest.onshippingoptionchange = (ev) =>
      ev.updateWith(checkShipping(payRequest));

    const response = await payRequest.show();
    await validateResponse(response);
  } catch (err) {
    /* handle the error; AbortError usually means a user cancellation */
  }
}
```

در این کد، متدهای `checkAddress()` و `checkShipping()`، به ترتیب، تغییرات آدرس حمل‌ونقل و گزینهٔ حمل‌ونقل را بررسی می‌کنند و در پاسخ یک شیء یا یک Promise برای بازگرداندن یک شیء ارائه می‌دهند؛ این شیء شامل فیلدهای موجود در {{domxref("PaymentResponse")}} است که تغییر کرده‌اند یا باید تغییر کنند.

متد `validateResponse()` در زیر، به محض بازگشت `show()` فراخوانی می‌شود تا `response` بازگشتی را بررسی کند و یا پرداخت را ارسال کند یا آن را به عنوان ناموفق رد کند:

```js
async function validateResponse(response) {
  try {
    if (await checkAllValues(response)) {
      await response.complete("success");
    } else {
      await response.complete("fail");
    }
  } catch (err) {
    await response.complete("fail");
  }
}
```

در اینجا، یک تابع سفارشی به نام `checkAllValues()` هر مقدار در `response` را بررسی می‌کند و مطمئن می‌شود که معتبر هستند؛ اگر همهٔ فیلدها معتبر باشند `true` و اگر هر یک نامعتبر باشند `false` برمی‌گرداند. اگر و فقط اگر همهٔ فیلدها معتبر باشند، متد {{domxref("PaymentResponse.complete", "complete()")}} بر روی پاسخ با رشتهٔ `"success"` فراخوانی می‌شود که نشان می‌دهد همه‌چیز معتبر است و پرداخت می‌تواند بر این اساس تکمیل شود.

اگر هر یک از فیلدها مقادیر غیرقابل قبولی داشته باشند، یا اگر استثنایی توسط کد قبلی پرتاب شود، `complete()` با رشتهٔ `"fail"` فراخوانی می‌شود که نشان می‌دهد فرایند پرداخت کامل شده و ناموفق بوده است.

به جای شکست فوری، می‌توانید {{domxref("PaymentResponse.retry", "retry()")}} را بر روی شیء پاسخ فراخوانی کنید تا از عامل کاربر بخواهید دوباره تلاش کند پرداخت را پردازش کند؛ این کار معمولاً فقط باید پس از انجام اصلاحات لازم توسط کاربر در سفارش انجام شود.

شروع فرایند پرداخت، در نهایت، به سادگی فراخوانی متد `processPayment()` است.

### نحو then/catch

همچنین می‌توانید از رویکرد مبتنی بر Promise قدیمی‌تر برای کار با پرداخت‌ها استفاده کنید، با استفاده از توابع {{jsxref("Promise.then", "then()")}} و {{jsxref("Promise.catch", "catch()")}} بر روی Promise بازگشتی از `show()`:

```js
function processPayment() {
  const payRequest = new PaymentRequest(methodData, details, options);

  payRequest.onshippingaddresschange = (ev) =>
    ev.updateWith(checkAddress(payRequest));
  payRequest.onshippingoptionchange = (ev) =>
    ev.updateWith(checkShipping(payRequest));

  payRequest
    .show()
    .then((response) => validateResponse(response))
    .catch((err) => handleError(err));
}
```

این به طور عملکردی معادل متد `processPayment()` با استفاده از نحو `await` است.

```js
function validateResponse(response) {
  checkAllValues(response)
    .then((response) => response.complete("success"))
    .catch((response) => response.complete("fail"));
}
```

حتی می‌توانید `checkAllValues()` را به عنوان یک تابع همزمان داشته باشید، اگرچه این ممکن است پیامدهای عملکردی داشته باشد که نمی‌خواهید با آن‌ها دست و پنجه نرم کنید:

```js
function validateResponse(response) {
  if (checkAllValues(response)) {
    response.complete("success");
  } else {
    response.complete("fail");
  }
}
```

اگر به اطلاعات بیشتری دربارهٔ کار با Promiseها نیاز دارید، مقالهٔ [استفاده از promises](/en-US/docs/Web/JavaScript/Guide/Using_promises) را ببینید.

## مثال‌ها

در مثال زیر، یک شیء `PaymentRequest` قبل از فراخوانی متد `show()` نمونه‌سازی می‌شود. این متد فرایند داخلی عامل کاربر برای دریافت اطلاعات پرداخت از کاربر را آغاز می‌کند. متد `show()` یک {{jsxref('Promise')}} برمی‌گرداند که وقتی تعامل کاربر کامل شود به یک شیء {{domxref("PaymentResponse")}} resolve می‌شود. توسعه‌دهنده