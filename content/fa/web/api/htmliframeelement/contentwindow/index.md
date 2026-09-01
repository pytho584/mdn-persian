---
title: "HTMLIFrameElement: contentWindow property"
short-title: contentWindow
slug: Web/API/HTMLIFrameElement/contentWindow
page-type: web-api-instance-property
browser-compat: api.HTMLIFrameElement.contentWindow
---

{{APIRef("HTML DOM")}}

ویژگی **`contentWindow`**، شیء [Window](/en-US/docs/Web/API/Window) مربوط به یک [HTMLIFrameElement](/en-US/docs/Web/API/HTMLIFrameElement) را برمی‌گرداند.

این ویژگی فقط‌خواندنی است.

## مقدار

یک شیء [Window](/en-US/docs/Web/API/Window).

## توضیحات

دسترسی به {{domxref("Window")}} که توسط `contentWindow` برگردانده می‌شود، تابع قوانین [خط‌مشی همان‌مبدأ](/en-US/docs/Web/Security/Defenses/Same-origin_policy) است؛ به این معنی که اگر iframe با والد خود هم‌مبدأ باشد، والد می‌تواند به سند iframe و DOM داخلی آن دسترسی داشته باشد و اگر ناهم‌مبدأ باشند، دسترسی بسیار محدودی به ویژگی‌های پنجره خواهد داشت. برای جزئیات به [«دسترسی به API اسکریپت در حالت ناهم‌مبدأ»](/en-US/docs/Web/Security/Defenses/Same-origin_policy#cross-origin_script_api_access) مراجعه کنید.

صفحات همچنین می‌توانند از این ویژگی برای یافتن اینکه کدام iframe پیامی را با استفاده از {{domxref("Window.postMessage()")}} ارسال کرده است استفاده کنند؛ بدین صورت که این ویژگی را با ویژگی {{domxref("MessageEvent.source", "source")}} رویداد پیام مقایسه می‌کنند.

## مثال‌ها

### دسترسی به سند یک iframe

این مثال ویژگی `style` بدنهٔ سند را تغییر می‌دهد.

توجه داشته باشید که این کار تنها زمانی کار می‌کند که پنجرهٔ iframe با والد خود هم‌مبدأ باشد؛ در غیر این صورت تلاش برای دسترسی به `contentWindow.document` یک استثنا پرتاب می‌کند.

```js
const iframe = document.querySelector("iframe").contentWindow;

iframe.document.querySelector("body").style.backgroundColor = "blue";
// این کار اولین iframe در سند را آبی می‌کند.
```

### نگاشت فرستندگان پیام به iframeها

این مثال می‌تواند در صفحه‌ای اجرا شود که چندین iframe را میزبانی می‌کند و هر یک از آن‌ها می‌توانند با استفاده از {{domxref("Window.postMessage()")}} برای آن پیام ارسال کنند. وقتی صفحه پیامی دریافت می‌کند، می‌خواهد بداند کدام iframe حاوی پنجره‌ای است که پیام را ارسال کرده است.

برای این کار، صفحه هنگام دریافت پیام، ابتدا بررسی می‌کند که پیام از مبدأ مورد انتظار آمده باشد و سپس با مقایسهٔ ویژگی {{domxref("MessageEvent.source", "source")}} رویداد پیام با ویژگی `contentWindow` هر iframe، iframe مبدأ پیام را پیدا می‌کند.

```js
const expectedOrigin = "https://example.org";

const iframes = Array.from(document.querySelectorAll("iframe"));

window.addEventListener("message", (e) => {
  if (e.origin !== expectedOrigin) return;

  const sourceIframe = iframes.find(
    (iframe) => iframe.contentWindow === e.source,
  );

  console.log(sourceIframe);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}