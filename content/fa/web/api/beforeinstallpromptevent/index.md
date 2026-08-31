---
title: "BeforeInstallPromptEvent"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BeforeInstallPromptEvent"
translated_by: "n8n + AI"
---

---
title: BeforeInstallPromptEvent
slug: Web/API/BeforeInstallPromptEvent
page-type: web-api-interface
status:
  - experimental
  - non-standard
browser-compat: api.BeforeInstallPromptEvent
---

{{APIRef}}{{SeeCompatTable}}{{Non-standard_header}}

**`BeforeInstallPromptEvent`** رابط رویداد {{domxref("Window.beforeinstallprompt_event", "beforeinstallprompt")}} است که روی شیء {{domxref("Window")}} پرتاب میشود، پیش از اینکه از کاربر خواسته شود یک وبسایت را به صفحه اصلی در موبایل «نصب» کند.

این رابط از رابط {{domxref("Event")}} ارث میبرد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("BeforeInstallPromptEvent.BeforeInstallPromptEvent","BeforeInstallPromptEvent()")}}{{Non-standard_Inline}} {{Experimental_Inline}}
  - : یک شیء جدید `BeforeInstallPromptEvent` میسازد.

## ویژگیهای نمونه

_ویژگیها را از والد خود، {{domxref("Event")}}، به ارث میبرد._

- {{domxref("BeforeInstallPromptEvent.platforms")}} {{ReadOnlyInline}}{{Non-standard_Inline}} {{Experimental_Inline}}
  - : آرایهای از رشتهها را برمیگرداند که شامل پلتفرمهایی است که رویداد روی آنها ارسال شده است. این برای عاملهای کاربری فراهم شده است که میخواهند انتخابی از نسخهها را به کاربر ارائه دهند، مانند «web» یا «play» که به کاربر امکان انتخاب بین نسخه وب یا نسخه اندروید را میدهد.
- {{domxref("BeforeInstallPromptEvent.userChoice")}} {{ReadOnlyInline}}{{Non-standard_Inline}} {{Experimental_Inline}}
  - : یک {{jsxref("Promise")}} برمیگرداند که به شیئی که انتخاب کاربر را هنگام اعلان نصب برنامه توصیف میکند، حل میشود.

## متدهای نمونه

- {{domxref("BeforeInstallPromptEvent.prompt()")}}{{Non-standard_Inline}} {{Experimental_Inline}}
  - : یک اعلان را نشان میدهد که از کاربر میپرسد آیا میخواهد برنامه را نصب کند. این متد یک {{jsxref("Promise")}} برمیگرداند که به شیئی که انتخاب کاربر را هنگام اعلان نصب برنامه توصیف میکند، حل میشود.

## مثالها

در مثال زیر، یک برنامه دکمه نصب خود را دارد که `id` آن `"install"` است. در ابتدا دکمه پنهان است.

```html
<button id="install" hidden>Install</button>
```

هندلر `beforeinstallprompt`:

- رویداد را لغو میکند، که از نمایش رابط کاربری نصب خود مرورگر در برخی پلتفرمها جلوگیری میکند.
- شیء `BeforeInstallPromptEvent` را به یک متغیر اختصاص میدهد تا بعداً مورد استفاده قرار گیرد.
- دکمه نصب برنامه را نمایان میکند.

```js
let installPrompt = null;
const installButton = document.querySelector("#install");

window.addEventListener("beforeinstallprompt", (event) => {
  event.preventDefault();
  installPrompt = event;
  installButton.removeAttribute("hidden");
});
```

هنگامی که دکمه نصب برنامه کلیک میشود:

- متد {{domxref("BeforeInstallPromptEvent.prompt()", "prompt()")}} شیء رویداد ذخیرهشده را برای راهاندازی اعلان نصب فراخوانی میکند.
- با پاک کردن متغیر `installPrompt` و پنهان کردن دوباره خودش، حالت خود را بازنشانی میکند.

```js
installButton.addEventListener("click", async () => {
  if (!installPrompt) {
    return;
  }
  const result = await installPrompt.prompt();
  console.log(`Install prompt was: ${result.outcome}`);
  installPrompt = null;
  installButton.setAttribute("hidden", "");
});
```

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Making PWAs installable](/en-US/docs/Web/Progressive_web_apps/Guides/Making_PWAs_installable)
- [How to provide your own in-app install experience](https://web.dev/articles/customize-install) در web.dev (2021)