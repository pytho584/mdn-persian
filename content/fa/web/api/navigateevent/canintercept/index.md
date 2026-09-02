---
title: "NavigateEvent: canIntercept property"
short-title: canIntercept
slug: Web/API/NavigateEvent/canIntercept
page-type: web-api-instance-property
browser-compat: api.NavigateEvent.canIntercept
---

{{APIRef("Navigation API")}}

خاصیت فقطخواندنی **`canIntercept`** از رابط {{domxref("NavigateEvent")}}، اگر ناوبری قابل رهگیری باشد و بتوان URL آن را بازنویسی کرد، مقدار `true` و در غیر این صورت مقدار `false` را برمی‌گرداند.

در مورد اینکه چه زمانی می‌توان یک ناوبری را رهگیری کرد، چند قاعده وجود دارد. برای مثال:

- نمی‌توانید ناوبری‌های cross-origin را رهگیری کنید.
- می‌توانید URLهای `http` یا `https` را رهگیری کنید اگر تنها بخش‌های `path`، `query` و `fragment` در URL جدید با URL فعلی تفاوت داشته باشند.
- می‌توانید URLهای `file` را رهگیری کنید اگر تنها بخش‌های `query` و `fragment` نشانی جدید نسبت به نشانی فعلی متفاوت باشند.
- برای سایر انواع URL، اگر فقط بخش `fragment` متفاوت باشد، می‌توانید ناوبری را رهگیری کنید.

برای توضیحات بیشتر دربارهٔ [زمانی که می‌توان URL یک Document را بازنویسی کرد](https://html.spec.whatwg.org/multipage/nav-history-apis.html#can-have-its-url-rewritten)، از جمله جدول نمونه‌ها، به مشخصات مراجعه کنید.

## مقدار

یک مقدار بولی — اگر ناوبری قابل رهگیری باشد `true` است، در غیر این صورت `false` است.

## مثال‌ها

```js
navigation.addEventListener("navigate", (event) => {
  // Some navigations, e.g. cross-origin navigations, we
  // cannot intercept. Let the browser handle those normally.
  if (!event.canIntercept) {
    return;
  }

  // Don't intercept fragment navigations or downloads.
  if (event.hashChange || event.downloadRequest !== null) {
    return;
  }

  event.intercept({
    handler() {
      if (event.formData) {
        processFormDataAndUpdateUI(event.formData, event.signal);
      } else {
        doSinglePageAppNav(event.destination, event.signal);
      }
    },
  });
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)
