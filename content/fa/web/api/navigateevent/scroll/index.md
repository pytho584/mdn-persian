---
title: "NavigateEvent: scroll() method"
---

{{APIRef("Navigation API")}}

متد **`scroll()`** از رابط {{domxref("NavigateEvent")}} را میتوان برای راهاندازی دستی رفتار پیمایش مرورگر که در پاسخ به ناوبری رخ میدهد، فراخوانی کرد، اگر بخواهید این کار قبل از تکمیل پردازش ناوبری انجام شود.

## نحو

```js-nolint
scroll()
```

### پارامترها

هیچ.

### مقدار برگشتی

هیچ (`undefined`).

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("Document")}} فعلی هنوز فعال نشده باشد، یا اگر ناوبری لغو شده باشد، پرتاب میشود.
- `SecurityError` {{domxref("DOMException")}}
  - : اگر رویداد توسط یک فراخوانی {{domxref("EventTarget.dispatchEvent", "dispatchEvent()")}} ارسال شده باشد، نه توسط عامل کاربر، پرتاب میشود.

## مثالها

### مدیریت پیمایش با استفاده از `scroll()`

در این مثال از رهگیری یک ناوبری، تابع `handler()` ابتدا محتوای یک مقاله را واکشی و رندر میکند، اما سپس محتوای ثانویه را بعد از آن واکشی و رندر میکند. منطقی است که به محض در دسترس بودن محتوای اصلی مقاله، صفحه به آن اسکرول شود تا کاربر بتواند با آن تعامل کند، به جای اینکه منتظر رندر شدن محتوای ثانویه نیز بمانیم. برای رسیدن به این هدف، یک فراخوانی `scroll()` بین این دو اضافه کردهایم.

```js
navigation.addEventListener("navigate", (event) => {
  if (shouldNotIntercept(navigateEvent)) {
    return;
  }
  const url = new URL(event.destination.url);

  if (url.pathname.startsWith("/articles/")) {
    event.intercept({
      async handler() {
        const articleContent = await getArticleContent(url.pathname);
        renderArticlePage(articleContent);

        event.scroll();

        const secondaryContent = await getSecondaryContent(url.pathname);
        addSecondaryContent(secondaryContent);
      },
    });
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)