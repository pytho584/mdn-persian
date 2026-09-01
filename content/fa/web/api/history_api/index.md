---
title: "History API"
---

---
title: History API
slug: Web/API/History_API
page-type: web-api-overview
browser-compat: api.History
---

{{DefaultAPISidebar("History API")}}

**History API** از طریق شیء سراسری {{DOMxRef("Window.history","history")}} به تاریخچه نشست مرورگر (که نباید با [تاریخچه WebExtensions](/en-US/docs/Mozilla/Add-ons/WebExtensions/API/history) اشتباه گرفته شود) دسترسی فراهم می‌کند. این API متدها و ویژگی‌های مفیدی را در اختیار شما قرار می‌دهد که با آن‌ها می‌توانید در تاریخچه کاربر به عقب و جلو حرکت کنید و محتویات پشته تاریخچه را دستکاری نمایید.

> [!NOTE]
> این API فقط در رشته اصلی ({{domxref("Window")}}) در دسترس است. در زمینه‌های {{domxref("Worker")}} یا {{domxref("Worklet")}} قابل دسترسی نیست.

## مفهوم و کاربرد

حرکت به عقب و جلو در تاریخچه کاربر با استفاده از متدهای {{DOMxRef("History.back","back()")}}، {{DOMxRef("History.forward","forward()")}} و {{DOMxRef("History.go","go()")}} انجام می‌شود.

### حرکت به جلو و عقب

برای حرکت به عقب در تاریخچه:

```js
history.back();
```

این عمل دقیقاً معادل کلیک کردن کاربر بر دکمه <kbd><strong>Back</strong></kbd> (بازگشت) در نوار ابزار مرورگر است.

به همین ترتیب، می‌توانید به جلو حرکت کنید (همان‌طور که اگر کاربر دکمه <kbd><strong>Forward</strong></kbd> (رفتن به جلو) را کلیک کرده باشد)، به این صورت:

```js
history.forward();
```

### رفتن به نقطه‌ای خاص در تاریخچه

می‌توانید از متد {{DOMxRef("History.go","go()")}} برای بارگذاری صفحه‌ای خاص از تاریخچه نشست استفاده کنید که با موقعیت نسبی آن نسبت به صفحه جاری مشخص می‌شود. (موقعیت نسبی صفحه جاری `0` است.)

برای حرکت به عقب به اندازه یک صفحه (معادل فراخوانی {{DOMxRef("History.back","back()")}}):

```js
history.go(-1);
```

برای حرکت به جلو به اندازه یک صفحه، درست مانند فراخوانی {{DOMxRef("History.forward","forward()")}}:

```js
history.go(1);
```

به همین ترتیب، می‌توانید با ارسال `2` دو صفحه به جلو حرکت کنید، و همین‌طور الی آخر.

کاربرد دیگر متد `go()` تازه‌سازی صفحه جاری است؛ یا با ارسال `0`، یا با فراخوانی آن بدون آرگومان:

```js
// The following statements
// both have the effect of
// refreshing the page
history.go(0);
history.go();
```

برای تعیین تعداد صفحات موجود در پشته تاریخچه، می‌توانید به مقدار ویژگی `length` نگاه کنید:

```js
const numberOfEntries = history.length;
```

## رابط‌ها

- {{domxref("History")}}
  - : دستکاری _تاریخچه نشست_ مرورگر (یعنی صفحاتی که در تب یا فریمی که صفحه جاری در آن بارگذاری شده است، بازدید شده‌اند) را امکان‌پذیر می‌کند.
- {{domxref("PopStateEvent")}}
  - : رابط مربوط به رویداد {{domxref("Window.popstate_event", "popstate")}}.

## مثال‌ها

مثال زیر یک شنونده برای رویداد {{domxref("Window.popstate_event", "popstate")}} اختصاص می‌دهد. سپس برخی از متدهای شیء `history` را برای افزودن، جایگزینی و جابه‌جایی در تاریخچه مرورگر تب جاری نشان می‌دهد.

```js
window.addEventListener("popstate", (event) => {
  alert(
    `location: ${document.location}, state: ${JSON.stringify(event.state)}`,
  );
});

history.pushState({ page: 1 }, "title 1", "?page=1");
history.pushState({ page: 2 }, "title 2", "?page=2");
history.replaceState({ page: 3 }, "title 3", "?page=3");
history.back(); // alerts "location: http://example.com/example.html?page=1, state: {"page":1}"
history.back(); // alerts "location: http://example.com/example.html, state: null"
history.go(2); // alerts "location: http://example.com/example.html?page=3, state: {"page":3}"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- شیء سراسری {{domxref("window.history", "history")}}
- رویداد {{domxref("Window/popstate_event", "popstate")}}