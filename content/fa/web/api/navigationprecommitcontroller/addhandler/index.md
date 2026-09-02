```markdown
---
title: "NavigationPrecommitController: addHandler() method"
short-title: addHandler()
slug: Web/API/NavigationPrecommitController/addHandler
page-type: web-api-instance-method
browser-compat: api.NavigationPrecommitController.addHandler
---

{{APIRef("Navigation API")}}

متد **`addHandler()`** از رابط {{domxref("NavigationPrecommitController")}} به شما امکان می‌دهد تا یک تابع بازگشتی (handler) را به صورت پویا در کد precommit اضافه کنید، که سپس پس از commit شدن ناوبری اجرا خواهد شد.

این زمانی مفید است که جریان کار ناوبری به اطلاعاتی وابسته باشد که تا زمانی که کد precommit شروع به اجرا نشده است، مشخص نیست. اگر precommit و handler (پس از commit) مستقل از هم باشند، می‌توان handler را در آرگومان [`options.handler`](/en-US/docs/Web/API/NavigateEvent/intercept#handler) که به {{domxref("NavigateEvent.intercept()")}} ارسال می‌شود، مشخص کرد.

## Syntax

```js-nolint
addHandler(handler);
```

### Parameters

- `handler`
  - : یک تابع بازگشتی که رفتار مدیریت ناوبری پس از commit را تعریف می‌کند؛ این تابع یک promise برمی‌گرداند.

    تابع بازگشتی handler به گونه‌ای فراخوانی می‌شود که گویی به متد `NavigateEvent.intercept()` ارسال شده است، و پس از به‌روزرسانی ویژگی {{domxref("Navigation.currentEntry", "currentEntry")}} اجرا خواهد شد.

### Return value

None (`undefined`).

### Exceptions

- `InvalidStateError` {{domxref("DOMException")}}
  - : در صورتی که:
    - {{domxref("NavigateEvent")}} مبدأ قطع (intercept) نشده باشد یا لغو شده باشد.
    - {{domxref("Document")}} به طور کامل فعال نباشد.
- `SecurityError` {{domxref("DOMException")}}
  - : در صورتی که ویژگی {{domxref("Event/isTrusted","isTrusted")}} رویداد `false` باشد.

## Examples

برای مثال‌های بیشتر به {{domxref("NavigationPrecommitController")}} مراجعه کنید.

### Basic usage

این مثال یک پیاده‌سازی `precommitHandler` را نشان می‌دهد که داده‌های یک صفحه را واکشی (fetch) می‌کند و از `addHandler()` برای افزودن handlerهای مختلف بر اساس نوع صفحه استفاده می‌کند (پیاده‌سازی‌های `fetchConfig`، `setupVideoPlayer()` و `setupArticleView()` ارائه نشده است).

```js
navigation.addEventListener("navigate", (event) => {
  event.intercept({
    async precommitHandler(controller) {
      const pageData = await fetchConfig();
      if (pageData.type === "video") {
        controller.addHandler(() => setupVideoPlayer());
      } else {
        controller.addHandler(() => setupArticleView());
      }
    },
  });
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
```