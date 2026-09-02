---
title: Navigation
slug: Web/API/Navigation
page-type: web-api-interface
browser-compat: api.Navigation
---

{{APIRef("Navigation API")}}

رابطه‌ی **`Navigation`** در {{domxref("Navigation API", "Navigation API", "", "nocode")}} امکان کنترل تمام کنش‌های ناوبری برای `window` فعلی را در یک مکان متمرکز فراهم می‌کند؛ از جمله شروع ناوبری‌ها به صورت برنامه‌نویسی‌شده، بررسی ورودی‌های تاریخچه‌ی ناوبری و مدیریت ناوبری‌ها هنگام وقوع آن‌ها.

این رابط از طریق ویژگی {{domxref("Window.navigation")}} در دسترس است.

Navigation API تنها ورودی‌های تاریخچه‌ای را در معرض قرار می‌دهد که در بستر مرور (browsing context) فعلی ایجاد شده‌اند و همان مبدأ (origin) صفحه‌ی فعلی را دارند (مثلاً نه ناوبری‌های داخل {{htmlelement("iframe")}}های توکار و نه ناوبری‌های بین‌مبدأ)؛ بنابراین فهرست دقیقی از تمام ورودی‌های قبلی تاریخچه را فقط برای برنامه‌ی شما فراهم می‌کند. این امر پیمایش در تاریخچه را در مقایسه با {{domxref("History API", "History API", "", "nocode")}} قدیمی به مراتب کم‌شکننده‌تر می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌های والد خود، {{DOMxRef("EventTarget")}} را به ارث می‌برد._

- {{domxref("Navigation.activation", "activation")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("NavigationActivation")}} برمی‌گرداند که حاوی اطلاعاتی درباره‌ی آخرین ناوبری بین‌اسنادی (cross-document) است که این Document را «فعال» کرده است.
- {{domxref("Navigation.canGoBack", "canGoBack")}} {{ReadOnlyInline}}
  - : اگر امکان حرکت به عقب در تاریخچه‌ی ناوبری وجود داشته باشد (یعنی {{domxref("Navigation.currentEntry", "currentEntry")}} اولین ورودی فهرست تاریخچه نباشد) `true` برمی‌گرداند و در غیر این صورت `false`.
- {{domxref("Navigation.canGoForward", "canGoForward")}} {{ReadOnlyInline}}
  - : اگر امکان حرکت به جلو در تاریخچه‌ی ناوبری وجود داشته باشد (یعنی {{domxref("Navigation.currentEntry", "currentEntry")}} آخرین ورودی فهرست تاریخچه نباشد) `true` برمی‌گرداند و در غیر این صورت `false`.
- {{domxref("Navigation.currentEntry", "currentEntry")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("NavigationHistoryEntry")}} برمی‌گرداند که مکان فعلی کاربر را نشان می‌دهد؛ یعنی جایی که کاربر در حال حاضر به آن ناوبری شده است.
- {{domxref("Navigation.transition", "transition")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("NavigationTransition")}} برمی‌گرداند که وضعیت یک ناوبری در حال انجام را نشان می‌دهد و می‌توان از آن برای پیگیری ناوبری استفاده کرد. اگر در حال حاضر ناوبری در جریان نباشد `null` برمی‌گرداند.

## روش‌های نمونه

_روش‌های والد خود، {{DOMxRef("EventTarget")}} را به ارث می‌برد._

- {{domxref("Navigation.back", "back()")}}
  - : با یک ورودی در تاریخچه‌ی ناوبری به عقب می‌رود.
- {{domxref("Navigation.entries", "entries()")}}
  - : آرایه‌ای از اشیاء {{domxref("NavigationHistoryEntry")}} برمی‌گرداند که تمام ورودی‌های موجود تاریخچه را نشان می‌دهد.
- {{domxref("Navigation.forward", "forward()")}}
  - : با یک ورودی در تاریخچه‌ی ناوبری به جلو می‌رود.
- {{domxref("Navigation.navigate", "navigate()")}}
  - : به یک URL مشخص ناوبری می‌کند و هر state ارائه‌شده را در فهرست ورودی‌های تاریخچه به‌روزرسانی می‌کند.
- {{domxref("Navigation.reload", "reload()")}}
  - : URL فعلی را بارگذاری مجدد می‌کند و هر state ارائه‌شده را در فهرست ورودی‌های تاریخچه به‌روزرسانی می‌کند.
- {{domxref("Navigation.traverseTo", "traverseTo()")}}
  - : به یک {{domxref("NavigationHistoryEntry")}} مشخص که با {{domxref("NavigationHistoryEntry.key", "key")}} شناسایی شده است ناوبری می‌کند.
- {{domxref("Navigation.updateCurrentEntry", "updateCurrentEntry()")}}
  - : state ویژگی {{domxref("Navigation.currentEntry","currentEntry")}} را به‌روزرسانی می‌کند؛ در مواردی استفاده می‌شود که تغییر state مستقل از ناوبری یا بارگذاری مجدد باشد.

## رویدادها

_رویدادهای والد خود، {{DOMxRef("EventTarget")}} را به ارث می‌برد._

- {{domxref("Navigation/currententrychange_event", "currententrychange")}}
  - : زمانی که {{domxref("Navigation.currentEntry")}} تغییر کرده باشد، پرتاب می‌شود.
- {{domxref("Navigation/navigate_event", "navigate")}}
  - : زمانی که [هر نوع ناوبری](https://github.com/WICG/navigation-api#appendix-types-of-navigations) آغاز شود، پرتاب می‌شود و به شما امکان می‌دهد در صورت نیاز آن را رهگیری (intercept) کنید.
- {{domxref("Navigation/navigateerror_event", "navigateerror")}}
  - : زمانی که یک ناوبری با شکست مواجه شود، پرتاب می‌شود.
- {{domxref("Navigation/navigatesuccess_event", "navigatesuccess")}}
  - : زمانی که یک ناوبری موفق به پایان برسد، پرتاب می‌شود.

## نمونه‌ها

### حرکت به جلو و عقب در تاریخچه

```js
async function backHandler() {
  if (navigation.canGoBack) {
    await navigation.back().finished;
    // Handle any required clean-up after
    // navigation has finished
  } else {
    displayBanner("You are on the first page");
  }
}

async function forwardHandler() {
  if (navigation.canGoForward) {
    await navigation.forward().finished;
    // Handle any required clean-up after
    // navigation has finished
  } else {
    displayBanner("You are on the last page");
  }
}
```

### پیمایش به یک ورودی مشخص در تاریخچه

```js
// On JS startup, get the key of the first loaded page
// so the user can always go back there.
const { key } = navigation.currentEntry;
backToHomeButton.onclick = () => navigation.traverseTo(key);

// Navigate away, but the button will always work.
await navigation.navigate("/another_url").finished;
```

### ناوبری و به‌روزرسانی state

```js
navigation.navigate(url, { state: newState });
```

یا

```js
navigation.reload({ state: newState });
```

یا اگر state مستقل از ناوبری یا بارگذاری مجدد باشد:

```js
navigation.updateCurrentEntry({ state: newState });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کلاینت: Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح‌دهنده‌ی Navigation API](https://github.com/WICG/navigation-api/blob/main/README.md)
- [دموی زنده‌ی Navigation API](https://mdn.github.io/dom-examples/navigation-api/) ([مشاهده‌ی سورس دمو](https://github.com/mdn/dom-examples/tree/main/navigation-api))