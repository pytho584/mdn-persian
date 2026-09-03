---
title: Using the Payment Request API
slug: Web/API/Payment_Request_API/Using_the_Payment_Request_API
page-type: guide
---

{{DefaultAPISidebar("Payment Request API")}}

[Payment Request API](/en-US/docs/Web/API/Payment_Request_API) یک روش مبتنی بر مرورگر برای اتصال کاربران و سیستم‌ها و پلتفرم‌های پرداخت ترجیحی آن‌ها به فروشندگانی است که می‌خواهند برای کالاها و خدمات هزینه پرداخت کنند، فراهم می‌کند. این مقاله راهنمایی برای استفاده از [Payment Request API](/en-US/docs/Web/API/Payment_Request_API) با مثال‌ها و بهترین روش‌های پیشنهادی است.

## اصول اولیه پرداخت

این بخش اصول اولیه استفاده از Payment Request API برای انجام پرداخت را شرح می‌دهد.

> [!NOTE]
> قطعه کدهای این بخش از [دموی تشخیص پشتیبانی از ویژگی](https://github.com/mdn/dom-examples/blob/main/payment-request/feature-detect-support.html) ما گرفته شده است.

### ایجاد یک شیء درخواست پرداخت جدید

یک درخواست پرداخت همیشه با ایجاد یک شیء جدید {{domxref("PaymentRequest")}} آغاز می‌شود - با استفاده از سازنده {{domxref("PaymentRequest.PaymentRequest", "PaymentRequest()")}}. این سازنده دو پارامتر اجباری و یک پارامتر اختیاری می‌گیرد:

- `methodData` - یک شیء حاوی اطلاعات مربوط به ارائه‌دهنده پرداخت، مانند اینکه چه روش‌های پرداختی پشتیبانی می‌شوند و غیره.
- `details` - یک شیء حاوی اطلاعات مربوط به پرداخت خاص، مانند مبلغ کل پرداخت، مالیات، هزینه حمل و نقل و غیره.
- `options` (اختیاری) - یک شیء حاوی گزینه‌های اضافی مرتبط با پرداخت.

بنابراین برای مثال، می‌توانید یک نمونه جدید از `PaymentRequest` به شکل زیر ایجاد کنید:

```js
const request = new PaymentRequest(
  buildSupportedPaymentMethodData(),
  buildShoppingCartDetails(),
);
```

توابع فراخوانی شده در داخل سازنده، پارامترهای شیء مورد نیاز را برمی‌گردانند:

```js
function buildSupportedPaymentMethodData() {
  // Example supported payment methods:
  return [{ supportedMethods: "https://example.com/pay" }];
}

function buildShoppingCartDetails() {
  // Hardcoded for demo purposes:
  return {
    id: "order-123",
    displayItems: [
      {
        label: "Example item",
        amount: { currency: "USD", value: "1.00" },
      },
    ],
    total: {
      label: "Total",
      amount: { currency: "USD", value: "1.00" },
    },
  };
}
```

### شروع فرآیند پرداخت

پس از ایجاد شیء `PaymentRequest`، متد {{domxref("PaymentRequest.show()")}} را روی آن فراخوانی می‌کنید تا درخواست پرداخت آغاز شود. این متد یک promise برمی‌گرداند که در صورت موفقیت‌آمیز بودن پرداخت، با یک شیء {{domxref("PaymentResponse")}} fulfilled می‌شود:

```js
request.show().then((paymentResponse) => {
  // Here we would process the payment. For this demo, simulate immediate success:
  paymentResponse.complete("success").then(() => {
    // For demo purposes:
    introPanel.style.display = "none";
    successPanel.style.display = "block";
  });
});
```

این شیء به توسعه‌دهنده دسترسی به جزئیاتی را می‌دهد که می‌تواند برای تکمیل مراحل منطقی مورد نیاز پس از اتمام پرداخت استفاده کند، مانند یک آدرس ایمیل برای تماس با مشتری، یک آدرس حمل و نقل برای ارسال کالا و غیره. در کد بالا، می‌بینید که ما متد {{domxref("PaymentResponse.complete()")}} را برای علامت‌دادن به پایان تعامل فراخوانی کرده‌ایم - از این برای انجام مراحل پایانی، مانند به‌روزرسانی رابط کاربری برای اطلاع‌رسانی به کاربر مبنی بر تکمیل تراکنش، استفاده می‌کنید.

### سایر متدهای مفید درخواست پرداخت

چند متد مفید دیگر درخواست پرداخت وجود دارد که ارزش دانستن دارند.

از {{domxref("PaymentRequest.canMakePayment()")}} می‌توان برای بررسی اینکه آیا شیء `PaymentRequest` قادر به انجام پرداخت است قبل از شروع فرآیند پرداخت استفاده کرد. این متد یک promise برمی‌گرداند که با یک مقدار boolean نشان‌دهنده توانایی یا عدم توانایی fulfilled می‌شود، به عنوان مثال:

```js
// Dummy payment request to check whether payment can be made
new PaymentRequest(buildSupportedPaymentMethodData(), {
  total: { label: "Stub", amount: { currency: "USD", value: "0.01" } },
})
  .canMakePayment()
  .then((result) => {
    if (result) {
      // Real payment request
      const request = new PaymentRequest(
        buildSupportedPaymentMethodData(),
        checkoutObject,
      );
      request.show().then((paymentResponse) => {
        // Here we would process the payment.
        paymentResponse.complete("success").then(() => {
          // Finish handling payment
        });
      });
    }
  });
```

از {{domxref("PaymentRequest.abort()")}} می‌توان در صورت نیاز برای لغو درخواست پرداخت استفاده کرد.

## تشخیص در دسترس بودن Payment Request API

می‌توانید با بررسی اینکه مرورگر کاربر از {{domxref("PaymentRequest")}} پشتیبانی می‌کند، یعنی `if (window.PaymentRequest)`، به طور مؤثر پشتیبانی از Payment Request API را تشخیص دهید.

در قطعه کد زیر، یک صفحه فروشنده این بررسی را انجام می‌دهد و اگر `true` برگرداند، دکمه تسویه حساب را به‌روز می‌کند تا به جای فرم‌های وب قدیمی از `PaymentRequest` استفاده کند.

```js
const checkoutButton = document.getElementById("checkout-button");
if (window.PaymentRequest) {
  let request = new PaymentRequest(
    buildSupportedPaymentMethodNames(),
    buildShoppingCartDetails(),
  );
  checkoutButton.addEventListener("click", () => {
    request
      .show()
      .then((paymentResponse) => {
        // Handle successful payment
      })
      .catch((error) => {
        // Handle cancelled or failed payment. For example, redirect to
        // the legacy web form checkout:
        window.location.href = "/legacy-web-form-checkout";
      });

    // Every click on the checkout button should use a new instance of
    // PaymentRequest object, because PaymentRequest.show() can be
    // called only once per instance.
    request = new PaymentRequest(
      buildSupportedPaymentMethodNames(),
      buildShoppingCartDetails(),
    );
  });
}
```

> [!NOTE]
> برای کد کامل به [دموی تشخیص پشتیبانی از ویژگی](https://mdn.github.io/dom-examples/payment-request/feature-detect-support.html) ما مراجعه کنید.

## بررسی اینکه آیا کاربران می‌توانند پرداخت انجام دهند

بررسی اینکه آیا کاربران می‌توانند پرداخت انجام دهند همیشه مفید است. در اینجا چند تکنیک مرتبط آورده شده است.

### سفارشی‌سازی دکمه پرداخت

یک تکنیک مفید که می‌توان به کار برد، سفارشی‌سازی دکمه درخواست پرداخت بسته به اینکه کاربران می‌توانند پرداخت انجام دهند یا خیر است.

در قطعه کد زیر دقیقاً این کار را انجام می‌دهیم - بسته به اینکه کاربر می‌تواند یک پرداخت سریع انجام دهد یا نیاز به افزودن اعتبار پرداخت دارد، عنوان دکمه تسویه حساب بین "Fast Checkout with W3C" و "Setup W3C Checkout" تغییر می‌کند. در هر دو حالت، دکمه تسویه حساب {{domxref("PaymentRequest.show()")}} را فراخوانی می‌کند.

```js
const checkoutButton = document.getElementById("checkout-button");
checkoutButton.innerText = "Loading…";
if (window.PaymentRequest) {
  const request = new PaymentRequest(
    buildSupportedPaymentMethodNames(),
    buildShoppingCartDetails(),
  );
  request
    .canMakePayment()
    .then((canMakeAFastPayment) => {
      checkoutButton.textContent = canMakeAFastPayment
        ? "Fast Checkout with W3C"
        : "Setup W3C Checkout";
    })
    .catch((error) => {
      // The user may have turned off the querying functionality in their
      // privacy settings. The website does not know whether they can make
      // a fast payment, so pick a generic title.
      checkoutButton.textContent = "Checkout with W3C";
    });
}
```

> [!NOTE]
> برای کد کامل به [دموی سفارشی‌سازی دکمه پرداخت](https://mdn.github.io/dom-examples/payment-request/customize-button-can-make-payment.html) ما مراجعه کنید.

### بررسی قبل از مشخص شدن قیمت‌ها

اگر فرآیند تسویه حساب نیاز دارد بداند که آیا {{domxref("PaymentRequest.canMakePayment()")}} حتی قبل از مشخص شدن همه اقلام و قیمت‌های آن‌ها `true` برمی‌گرداند، می‌توانید `PaymentRequest` را با داده‌های ساختگی نمونه‌سازی کرده و `.canMakePayment()` را از پیش پرس‌وجو کنید. اگر `.canMakePayment()` را چندین بار فراخوانی می‌کنید، به خاطر داشته باشید که اولین پارامتر سازنده `PaymentRequest` باید شامل همان نام‌ها و داده‌های روش باشد.

```js
// The page has loaded. Should the page use PaymentRequest?
// If PaymentRequest fails, should the page fallback to manual
// web form checkout?
const supportedPaymentMethods = [/* supported methods */];

let shouldCallPaymentRequest = true;
let fallbackToLegacyOnPaymentRequestFailure = false;
new PaymentRequest(supportedPaymentMethods, {
  total: { label: "Stub", amount: { currency: "USD", value: "0.01" } },
})
  .canMakePayment()
  .then((result) => {
    shouldCallPaymentRequest = result;
  })
  .catch((error) => {
    console.error(error);

    // The user may have turned off query ability in their privacy settings.
    // Let's use PaymentRequest by default and fallback to legacy
    // web form based checkout.
    shouldCallPaymentRequest = true;
    fallbackToLegacyOnPaymentRequestFailure = true;
  });

// User has clicked on the checkout button. We know
// what's in the cart, but we don't have a `Checkout` object.
function onCheckoutButtonClicked(lineItems) {
  callServerToRetrieveCheckoutDetails(lineItems);
}

// The server has constructed the `Checkout` object. Now we know
// all of the prices and shipping options.
function onServerCheckoutDetailsRetrieved(checkoutObject) {
  if (shouldCallPaymentRequest) {
    const request = new PaymentRequest(supportedPaymentMethods, checkoutObject);
    request
      .show()
      .then((paymentResponse) => {
        // Post the results to the server and call `paymentResponse.complete()`.
      })
      .catch((error) => {
        console.error(error);
        if (fallbackToLegacyOnPaymentRequestFailure) {
          window.location.href = "/legacy-web-form-checkout";
        } else {
          showCheckoutErrorToUser();
        }
      });
  } else {
    window.location.href = "/legacy-web-form-checkout";
  }
}
```

> [!NOTE]
> برای کد کامل به [دموی بررسی توانایی کاربر برای پرداخت قبل از مشخص شدن قیمت‌ها](https://mdn.github.io/dom-examples/payment-request/check-user-can-make-payment.html) ما مراجعه کنید.

## توصیه یک برنامه پرداخت زمانی که کاربر برنامه‌ای ندارد

اگر در این صفحه فروشنده، ارائه‌دهنده پرداخت دموی BobBucks را برای پرداخت انتخاب کنید، سعی می‌کند `PaymentRequest.show()` را فراخوانی کند، در حالی که `NotSupportedError` {{domxref("DOMException")}} را رهگیری می‌کند. اگر این روش پرداخت پشتیبانی نشود، به صفحه ثبت‌نام BobBucks هدایت می‌شود.

کد به شکل زیر است:

```js
checkoutButton.addEventListener("click", () => {
  const request = new PaymentRequest(
    buildSupportedPaymentMethodData(),
    buildShoppingCartDetails(),
  );
  request
    .show()
    .then((paymentResponse) => {
      // Here we would process the payment. For this demo, simulate immediate success:
      paymentResponse.complete("success").then(() => {
        // For demo purposes:
        introPanel.style.display = "none";
        successPanel.style.display = "block";
      });
    })
    .catch((error) => {
      if (error.name === "NotSupportedError") {
        window.location.href = "https://bobbucks.dev/#download";
      } else {
        // Other kinds of errors; cancelled or failed payment. For demo purposes:
        introPanel.style.display = "none";
        legacyPanel.style.display = "block";
      }
    });
});
```

> [!NOTE]
> برای کد کامل به [دموی توصیه یک برنامه پرداخت زمانی که کاربر برنامه‌ای ندارد](https://mdn.github.io/dom-examples/payment-request/recommend-payment-app.html) ما مراجعه کنید.

## نمایش رابط کاربری اضافی پس از پرداخت‌های موفق

اگر فروشنده تمایل به جمع‌آوری اطلاعات اضافی که بخشی از API نیست (مانند دستورالعمل‌های تحویل اضافی) داشته باشد، می‌تواند پس از تسویه حساب، صفحه‌ای با فیلدهای `<input type="text">` اضافی نمایش دهد.

```js
request
  .show()
  .then((paymentResponse) => paymentResponse.complete("success"))
  .then(() => {
    // Process payment here.
    // Close the UI:
    // Request additional shipping address details.
    const additionalDetailsContainer = document.getElementById(
      "additional-details-container",
    );
    additionalDetailsContainer.style.display = "block";
    window.scrollTo(additionalDetailsContainer.getBoundingClientRect().x, 0);
  })
  .catch((error) => {
    // Handle error.
  });
```

> [!NOTE]
> برای کد کامل به [دموی نمایش رابط کاربری اضافی پس از پرداخت موفق](https://mdn.github.io/dom-examples/payment-request/show-additional-ui-after-payment.html) ما مراجعه کنید.

## پیش‌مجوزدهی تراکنش‌ها

برخی موارد استفاده (مانند پرداخت سوخت در پمپ بنزین) شامل پیش‌مجوزدهی پرداخت است. یکی از راه‌های انجام این کار از طریق یک Payment Handler مبتنی بر وب است (به {{domxref("Web-based Payment Handler API", "", "", "nocode")}} مراجعه کنید). در زمان نگارش این مقاله، آن مشخصات شامل یک رویداد `canmakepayment` است که یک Payment Handler مبتنی بر وب می‌تواند از آن برای برگرداندن وضعیت مجوز استفاده کند.

کد فروشنده به شکل زیر خواهد بود:

```js
const paymentRequest = new PaymentRequest(
  [{ supportedMethods: "https://example.com/preauth" }],
  details,
);

// Send `CanMakePayment` event to the payment handler.
paymentRequest
  .canMakePayment()
  .then((res) => {
    if (res) {
      // The payment handler has pre-authorized a transaction
      // with some static amount, e.g., USD $1.00.
    } else {
      // Pre-authorization failed or payment handler not installed.
    }
  })
  .catch((err) => {
    // Unexpected error occurred.
  });
```

Payment handler مبتنی بر وب شامل کد زیر خواهد بود:

```js
self.addEventListener("canmakepayment", (evt) => {
  // Pre-authorize here.
  const preAuthSuccess = true;
  evt.respondWith(preAuthSuccess);
});
```

این Payment handler باید در یک service worker در محدوده `https://example.com/preauth` قرار داشته باشد.

> [!NOTE]
> برای کد کامل به [دموی پیش‌مجوزدهی تراکنش‌ها](https://mdn.github.io/dom-examples/payment-request/pre-authorize-transaction.html) ما مراجعه کنید.

## همچنین ببینید

- [نمونه‌های Google PaymentRequest](https://googlechrome.github.io/samples/paymentrequest/)