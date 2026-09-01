---
title: "Document: lastModified property"
short-title: lastModified
slug: Web/API/Document/lastModified
page-type: web-api-instance-property
browser-compat: api.Document.lastModified
---

{{APIRef("DOM")}}

ویژگی **`lastModified`** از رابط {{domxref("Document")}}، رشتهای شامل تاریخ و زمان محلی آخرین تغییری که روی سند فعلی انجام شده است را برمیگرداند.

## مقدار

یک رشته.

## مثالها

### استفاده ساده

این مثال مقدار `lastModified` را در یک پنجره هشدار نشان میدهد.

```js
alert(document.lastModified);
// returns: Tuesday, December 16, 2017 11:09:42
```

### تبدیل lastModified به یک شیء Date

این مثال `lastModified` را به یک شیء {{jsxref("Date")}} تبدیل میکند.

```js
let oLastModif = new Date(document.lastModified);
```

### تبدیل lastModified به میلیثانیه

این مثال `lastModified` را به تعداد میلیثانیههای سپریشده از ۱ ژانویه ۱۹۷۰، ساعت ۰۰:۰۰:۰۰ به وقت محلی تبدیل میکند.

```js
let nLastModif = Date.parse(document.lastModified);
```

## نکات

توجه داشته باشید که `lastModified` بهصورت یک رشته است و بهسادگی نمیتوان از آن برای مقایسه تاریخ تغییر اسناد استفاده کرد. در ادامه نمونهای از یک روش احتمالی برای نمایش پیام هشدار هنگام تغییر صفحه آورده شده است (همچنین ببینید: [JavaScript cookies API](/en-US/docs/Web/API/Document/cookie)):

```js
// Match 'timestamp' in 'last_modif=timestamp'
// e.g. '1687964614822' in 'last_modif=1687964614822'
const pattern = /last_modif\s*=\s*([^;]*)/;

if (
  Date.parse(document.lastModified) >
  (parseFloat(document.cookie.match(pattern)?.[1]) || 0)
) {
  document.cookie = `last_modif=${Date.now()}; expires=Fri, 31 Dec 9999 23:59:59 GMT; path=${
    location.pathname
  }`;
  alert("This page has changed!");
}
```

…همان مثال، اما با رد شدن از اولین بازدید:

```js
const pattern = /last_modif\s*=\s*([^;]*)/;

const lastVisit = parseFloat(document.cookie.replace(pattern, "$1"));
const lastModif = Date.parse(document.lastModified);

if (Number.isNaN(lastVisit) || lastModif > lastVisit) {
  document.cookie = `last_modif=${Date.now()}; expires=Fri, 31 Dec 9999 23:59:59 GMT; path=${
    location.pathname
  }`;

  if (isFinite(lastVisit)) {
    alert("This page has been changed!");
  }
}
```

اگر میخواهید بدانید که آیا یک صفحه _خارجی_ تغییر کرده است، میتوانید با استفاده از API {{domxref("Window/fetch", "fetch()")}} یک درخواست {{HTTPMethod("HEAD")}} ارسال کنید و هدر پاسخ {{HTTPHeader("Last-Modified")}} را بررسی کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}