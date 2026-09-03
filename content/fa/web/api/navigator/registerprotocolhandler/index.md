---
title: "Navigator: registerProtocolHandler() method"
short-title: registerProtocolHandler()
slug: Web/API/Navigator/registerProtocolHandler
page-type: web-api-instance-method
browser-compat: api.Navigator.registerProtocolHandler
---

{{APIRef("HTML DOM")}}{{securecontext_header}}

متد **{{domxref("Navigator")}}** به نام **`registerProtocolHandler()`** به وب‌سایت‌ها این امکان را می‌دهد که توانایی خود را برای باز کردن یا مدیریت طرح‌های خاص URL (که پروتکل نیز نامیده می‌شوند) ثبت کنند.

برای مثال، این API به وب‌سایت‌های ایمیل مبتنی بر وب اجازه می‌دهد URLهای `mailto:` را باز کنند و به وب‌سایت‌های VoIP اجازه می‌دهد URLهای `tel:` را باز کنند.

برای ثبت یک کنترل‌کنندهٔ پروتکل، یک وب‌سایت `registerProtocolHandler()` را فراخوانی می‌کند و پروتکل موردنظر برای ثبت و یک قالب URL را به‌عنوان ورودی به آن پاس می‌دهد.

وقتی کاربر پیوندی را فعال می‌کند که از پروتکلِ ثبت‌شده استفاده می‌کند، مرورگر [`href`](/en-US/docs/Web/HTML/Reference/Elements/a#href) همان پیوندِ فعال‌شده را درون قالب URL که هنگام ثبت کنترل‌کننده ارائه شده بود جایگذاری می‌کند و صفحهٔ فعلی را به URL حاصل هدایت می‌کند.

ممکن است مرورگر هنگام ثبت پروتکل یا هنگام فعال کردن پیوند توسط کاربر، از کاربر بپرسد که آیا می‌خواهد به صفحه اجازه داده شود آن پروتکل را مدیریت کند.

## سینتکس

```js-nolint
registerProtocolHandler(scheme, url)
```

### پارامترها

- `scheme`
  - : رشته‌ای شامل طرح (scheme) پروتکلی که سایت می‌خواهد مدیریت کند.

    این طرح می‌تواند سفارشی باشد، که در این صورت نام طرح باید:
    - با `web+` شروع شود
    - پس از پیشوند `web+` حداقل یک حرف داشته باشد
    - فقط شامل حروف کوچک {{Glossary("ASCII")}} باشد.

    در غیر این صورت، طرح باید یکی از موارد زیر باشد:
    - `bitcoin`
    - `ftp`
    - `ftps`
    - `geo`
    - `im`
    - `irc`
    - `ircs`
    - `magnet`
    - `mailto`
    - `matrix`
    - `mms`
    - `news`
    - `nntp`
    - `openpgp4fpr`
    - `sftp`
    - `sip`
    - `sms`
    - `smsto`
    - `ssh`
    - `tel`
    - `urn`
    - `webcal`
    - `wtai`
    - `xmpp`

    <!-- This must match: https://html.spec.whatwg.org/multipage/system-state.html#safelisted-scheme -->

- `url`
  - : رشته‌ای شامل URL کنترل‌کننده. این URL باید شامل `%s` به‌عنوان یک جاینگهدار (placeholder) باشد که با [نسخهٔ کدگذاری (escape) شده](/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURIComponent) URLِ موردنظر جایگزین خواهد شد.

    URL کنترل‌کننده باید از طرح `https` استفاده کند و {{glossary("origin")}} آن باید با خاستگاه صفحهٔ وبی که در حال ثبت کنترل‌کننده است یکسان باشد.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `SecurityError` {{domxref("DOMException")}}
  - : عامل کاربر (user agent) ثبت را مسدود کرده است. این وضعیت ممکن است در این موارد رخ دهد:
    - طرح (پروتکل) ثبت‌شده نامعتبر باشد؛ مانند طرحی که خود مرورگر مدیریت می‌کند (`https:`، `about:` و غیره).
    - {{Glossary("origin")}} در URL کنترل‌کننده با خاستگاه صفحهٔ فراخوانندهٔ این API یکسان نباشد.
    - طرح URLِ کنترل‌کننده `https` نباشد.

- `SyntaxError` {{domxref("DOMException")}}
  - : جاینگهدار `%s` در URL کنترل‌کننده وجود ندارد.

## مثال‌ها

### ثبت یک کنترل‌کننده برای پروتکل mailto

بسیار رایج است که صفحات وب برای پیوند به منابع از پروتکل‌هایی غیر از `https` استفاده کنند. یک نمونهٔ آن پروتکل `mailto:` است. نویسندگان وب می‌توانند هر وقت بخواهند راهی آسان برای ارسال مستقیم ایمیل از صفحهٔ وب در اختیار کاربران بگذارند، از پیوند `mailto` استفاده کنند:

```html
<a href="mailto:webmaster@example.com">Web Master</a>
```

با فعال شدن پیوند، مرورگر باید برنامهٔ پیش‌فرض رومیزی برای مدیریت ایمیل را اجرا کند. می‌توانید این را به‌عنوان یک کنترل‌کنندهٔ پروتکلِ _مبتنی بر دسکتاپ_ در نظر بگیرید.

کنترل‌کننده‌های پروتکل مبتنی بر وب به برنامه‌های تحت وب نیز اجازه می‌دهند در این فرایند مشارکت کنند. یک برنامهٔ ایمیل تحت وب در `mail.example.org` می‌تواند با کدی مانند زیر برای مدیریت پیوندهای `mailto` ثبت شود:

```js
navigator.registerProtocolHandler("mailto", "https://mail.example.org/?to=%s");
```

پس از این کار، وقتی کاربر روی یک پیوند `mailto` در هر وب‌سایتی کلیک کند، مرورگر (شاید پس از جلب تأیید کاربر) به `https://mail.example.org/?to=mailto:webmaster@example.com` هدایت می‌شود. این صفحه می‌تواند پارامتر URL را تجزیه کند تا آدرس را استخراج کند و از آن برای ساخت یک ایمیل استفاده کند.

### ثبت یک کنترل‌کننده برای یک پروتکل سفارشی

در این مثال، یک صفحه با کدی مانند زیر، کنترل‌کننده‌ای برای پروتکل `web+burger` ثبت می‌کند:

```js
navigator.registerProtocolHandler(
  "web+burger",
  "https://burgers.example.org/?burger=%s",
);
```

سپس، کاربر از صفحه‌ای بازدید می‌کند که پیوندی مانند زیر دارد:

```html
<a href="web+burger:cheeseburger">cheeseburger</a>
```

اگر کاربر پیوند `web+burger` را فعال کند، مرورگر (شاید پس از جلب تأیید کاربر) به `https://burgers.example.org/?burger=web+burger:cheeseburger` هدایت می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}