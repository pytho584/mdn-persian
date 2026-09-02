---
title: "NavigationHistoryEntry: key property"
short-title: key
slug: Web/API/NavigationHistoryEntry/key
page-type: web-api-instance-property
browser-compat: api.NavigationHistoryEntry.key
---

{{APIRef("Navigation API")}}

ویژگی فقط خواندنی **`key`** از رابط {{domxref("NavigationHistoryEntry")}}، کلید (key) ورودی تاریخچه را برمی‌گرداند، یا یک رشته خالی اگر سند فعلی کاملاً فعال نباشد. این یک مقدار منحصربه‌فرد است که توسط عامل کاربر (UA) تولید شده و نشان‌دهنده جایگاه (slot) آن ورودی در لیست ورودی‌ها است. از این کلید برای پیمایش به آن جایگاه خاص از طریق {{domxref("Navigation.traverseTo()")}} استفاده می‌شود. `key` توسط سایر ورودی‌هایی که جایگزین آن ورودی در لیست می‌شوند (یعنی اگر {{domxref("NavigateEvent.navigationType")}} برابر `replace` باشد) مجدداً استفاده خواهد شد.

این ویژگی با {{domxref("NavigationHistoryEntry.id", "id")}} یک ورودی تاریخچه متفاوت است. `id` یک مقدار منحصربه‌فرد است که توسط عامل کاربر تولید شده و همیشه نمایانگر یک ورودی تاریخچه خاص است، نه جایگاه آن در لیست ورودی‌ها. این برای ارتباط دادن آن با یک منبع خارجی مانند حافظه نهان (storage cache) مفید است.

## مقدار

یک رشته که `key` آبجکت {{domxref("NavigationHistoryEntry")}} را نشان می‌دهد.

## مثال‌ها

### استفاده پایه

```js
const current = navigation.currentEntry;
console.log(current.key);
```

### راه‌اندازی یک دکمه خانه

```js
function initHomeBtn() {
  // کلید اولین ورودی بارگذاری‌شده را می‌گیریم
  // تا کاربر همیشه بتواند به این نما بازگردد.
  const { key } = navigation.currentEntry;
  backToHomeButton.onclick = () => {
    navigation.traverseTo(key);
  };
}
// رویدادهای navigate (مانند کلیک روی پیوندها) را رهگیری کرده و
// آنها را با پیمایش‌های تک‌صفحه‌ای جایگزین می‌کنیم
navigation.addEventListener("navigate", (event) => {
  event.intercept({
    async handler() {
      // به یک نمای متفاوت پیمایش می‌کنیم،
      // اما دکمه "خانه" همیشه کار خواهد کرد.
    },
  });
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کلاینت: Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح Navigation API](https://github.com/WICG/navigation-api/blob/main/README.md)