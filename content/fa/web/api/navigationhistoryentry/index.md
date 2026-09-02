---
title: NavigationHistoryEntry
slug: Web/API/NavigationHistoryEntry
page-type: web-api-interface
browser-compat: api.NavigationHistoryEntry
---

{{APIRef("Navigation API")}}

رابط **`NavigationHistoryEntry`** از {{domxref("Navigation API", "Navigation API", "", "nocode")}} نشان‌دهندهٔ یک ورودی از تاریخچهٔ پیمایش است.

این اشیاء معمولاً از طریق ویژگی {{domxref("Navigation.currentEntry")}} و متد {{domxref("Navigation.entries()")}} قابل دسترسی هستند.

Navigation API تنها ورودی‌های تاریخچه‌ای را در معرض دید قرار می‌دهد که در زمینهٔ مرور فعلی ایجاد شده‌اند و مبدأ (origin) یکسانی با صفحهٔ فعلی دارند (به عنوان مثال، نه پیمایش‌های داخل {{htmlelement("iframe")}}های تعبیه‌شده، و نه پیمایش‌های بین‌مبدأ). این کار یک فهرست دقیق از تمام ورودی‌های قبلی تاریخچه را فقط برای برنامهٔ شما فراهم می‌کند. این باعث می‌شود که پیمایش در تاریخچه نسبت به {{domxref("History API", "History API", "", "nocode")}} قدیمی بسیار کمتر شکننده باشد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه (Instance properties)

ویژگی‌هایی را از والد خود، {{DOMxRef("EventTarget")}}، به ارث می‌برد.

- {{domxref("NavigationHistoryEntry.id", "id")}} {{ReadOnlyInline}}
  - : مقدار `id` ورودی تاریخچه را بازمی‌گرداند. این یک مقدار یکتا و تولیدشده توسط عامل کاربر (UA) است که همیشه نمایندهٔ یک ورودی خاص از تاریخچه می‌باشد و برای مرتبط‌سازی آن با یک منبع خارجی مانند حافظهٔ نهان ذخیره‌سازی مفید است.
- {{domxref("NavigationHistoryEntry.index", "index")}} {{ReadOnlyInline}}
  - : شاخص (index) ورودی تاریخچه را در فهرست ورودی‌های تاریخچه (یعنی فهرست بازگردانده‌شده توسط {{domxref("Navigation.entries()")}}) بازمی‌گرداند، یا اگر ورودی در فهرست وجود نداشته باشد، `1-` را برمی‌گرداند.
- {{domxref("NavigationHistoryEntry.key", "key")}} {{ReadOnlyInline}}
  - : مقدار `key` ورودی تاریخچه را بازمی‌گرداند. این یک مقدار یکتا و تولیدشده توسط عامل کاربر است که نشان‌دهندهٔ جایگاه (slot) ورودی تاریخچه در فهرست ورودی‌ها است، نه خود ورودی. از آن برای پیمایش به آن جایگاه خاص از طریق {{domxref("Navigation.traverseTo()")}} استفاده می‌شود. `key` توسط ورودی‌های دیگری که جایگزین آن ورودی در فهرست می‌شوند، دوباره استفاده خواهد شد (یعنی اگر {{domxref("NavigateEvent.navigationType")}} برابر با `replace` باشد).
- {{domxref("NavigationHistoryEntry.sameDocument", "sameDocument")}} {{ReadOnlyInline}}
  - : اگر این ورودی تاریخچه برای همان `document` (سند) فعلی باشد، `true` و در غیر این صورت `false` بازمی‌گرداند.
- {{domxref("NavigationHistoryEntry.url", "url")}} {{ReadOnlyInline}}
  - : نشانی اینترنتی مطلق این ورودی تاریخچه را بازمی‌گرداند. اگر ورودی مربوط به سندی متفاوت از سند فعلی باشد (مانند اینکه ویژگی `sameDocument` برابر `false` باشد) و آن سند با هدر {{httpheader("Referrer-Policy")}} تنظیم‌شده به `no-referrer` یا `origin` دریافت شده باشد، این ویژگی `null` را برمی‌گرداند.

## روش‌های نمونه (Instance methods)

متدهایی را از والد خود، {{DOMxRef("EventTarget")}}، به ارث می‌برد.

- {{domxref("NavigationHistoryEntry.getState", "getState()")}}
  - : یک کپی (clone) از حالت (state) موجود مرتبط با این ورودی تاریخچه را بازمی‌گرداند.

## رویدادها (Events)

- {{domxref("NavigationHistoryEntry/dispose_event", "dispose")}}
  - : هنگامی که ورودی دیگر بخشی از فهرست ورودی‌های تاریخچه نیست، فعال می‌شود.

## مثال‌ها

```js
function initHomeBtn() {
  // Get the key of the first loaded entry
  // so the user can always go back to this view.
  const { key } = navigation.currentEntry;
  backToHomeButton.onclick = () => {
    navigation.traverseTo(key);
  };
}
// Intercept navigate events, such as link clicks, and
// replace them with single-page navigations
navigation.addEventListener("navigate", (event) => {
  event.intercept({
    async handler() {
      // Navigate to a different view,
      // but the "home" button will always work.
    },
  });
});
```

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید (See also)

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)
- [Navigation API live demo](https://mdn.github.io/dom-examples/navigation-api/) ([view demo source](https://github.com/mdn/dom-examples/tree/main/navigation-api))