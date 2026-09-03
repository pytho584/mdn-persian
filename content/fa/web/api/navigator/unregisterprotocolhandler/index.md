---
title: "Navigator: unregisterProtocolHandler() method"
short-title: unregisterProtocolHandler()
slug: Web/API/Navigator/unregisterProtocolHandler
page-type: web-api-instance-method
browser-compat: api.Navigator.unregisterProtocolHandler
---

{{APIRef("HTML DOM")}}{{securecontext_header}}

متد **`unregisterProtocolHandler()`** از {{domxref("Navigator")}}، یک مدیریت‌کنندهٔ پروتکل (protocol handler) را برای یک [طرح (scheme)](#permitted_schemes) مشخص از URL حذف می‌کند.

این متد معکوس **`registerProtocolHandler()`** است.

## Syntax

```js-nolint
unregisterProtocolHandler(scheme, url)
```

### پارامترها

- `scheme`
  - : یک رشته شامل [طرح مجاز](#permitted_schemes) در مدیریت‌کنندهٔ پروتکلی که قرار است لغو ثبت شود.
    برای مثال، می‌توانید با ارسال طرح `"sms"`، مدیریت‌کنندهٔ لینک‌های پیام متنی SMS را لغو ثبت کنید.
- `url`
  - : یک رشته شامل URL مدیریت‌کننده.
    **این URL باید با همان چیزی که برای ثبت مدیریت‌کننده استفاده شده است مطابقت داشته باشد (مثلاً باید شامل `%s` باشد)**.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `SecurityError` {{domxref("DOMException")}}
  - : عامل کاربر (user agent) لغو ثبت را مسدود کرد.
    این حالت ممکن است رخ دهد اگر:
    - طرح (پروتکل) نامعتبر باشد، مانند طرحی که خود مرورگر مدیریت می‌کند (`https:`، `about:` و غیره).
    - {{Glossary("origin", "مبدأ")}} URL مدیریت‌کننده با مبدأ صفحه‌ای که این API را فراخوانی می‌کند مطابقت نداشته باشد.
    - مرورگر ایجاب کند که این تابع از یک بافت امن (secure context) فراخوانی شود.
    - مرورگر ایجاب کند که URL مدیریت‌کننده از طریق HTTPS باشد.
- `SyntaxError` {{domxref("DOMException")}}
  - : جایگاه `%s` در URL مدیریت‌کننده وجود ندارد.

## طرح‌های مجاز

به دلایل امنیتی، `unregisterProtocolHandler()` طرح‌هایی را که می‌توان لغو ثبت کرد محدود می‌کند.

یک **طرح سفارشی** تا زمانی قابل لغو ثبت است که:

- نام طرح سفارشی با `web+` شروع شود.
- نام طرح سفارشی حداقل ۱ حرف بعد از پیشوند `web+` داشته باشد.
- نام طرح سفارشی فقط شامل حروف ASCII کوچک (a-z) باشد.

برای مثال، `web+burger` همان‌طور که در [مثال](#examples) زیر نشان داده شده است.

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

## مثال‌ها

اگر سایت شما `burgers.example.com` است و یک طرح `web+burger:` دارید، می‌توانید مدیریت‌کنندهٔ آن را به این صورت لغو ثبت کنید:

```js
navigator.unregisterProtocolHandler(
  "web+burger",
  "https://burgers.example.com/?burger=%s",
);
```

این اسکریپت باید از همان مبدأ URL مدیریت‌کننده اجرا شود (یعنی هر صفحه‌ای در `https://burgers.example.com`)، و URL مدیریت‌کننده باید `http` یا `https` باشد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}