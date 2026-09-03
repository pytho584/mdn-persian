---
title: "PerformanceNavigationTiming: type property"
short-title: type
slug: Web/API/PerformanceNavigationTiming/type
page-type: web-api-instance-property
browser-compat: api.PerformanceNavigationTiming.type
---

{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`type`** نوع پیمایش (navigation) را برمی‌گرداند.

می‌توانید از این ویژگی برای دسته‌بندی داده‌های زمان‌بندی پیمایش خود استفاده کنید؛ زیرا هر یک از این نوع‌ها ویژگی‌های عملکردی متفاوتی دارند. کاربرانی که بین صفحه‌ها رفت‌وبرگشت می‌کنند ممکن است سایت را سریع‌تر از کاربرانی تجربه کنند که برای نخستین بار پیمایش را انجام می‌دهند یا فرمی را ارسال می‌کنند و مانند آن.

برای مثال، اگر سایت شما به‌طور مکرر محتوای جدید ارائه می‌دهد، شاید بخواهید آن محتوا را با استفاده از [Fetch](/en-US/docs/Web/API/Fetch_API) یا روشی مشابه تازه کنید و کاری کنید که کاربران مجبور نباشند همیشه کل صفحه را دوباره بارگذاری کنند. نوع `"reload"` می‌تواند به شما کمک کند صفحه‌هایی را بیابید که مکرراً بارگذاری مجدد می‌شوند.

## مقدار

ویژگی `type` می‌تواند مقادیر زیر را داشته باشد:

- `"navigate"`
  - پیمایشی که با کلیک روی یک پیوند، وارد کردن URL در نوار آدرس مرورگر، ارسال فرم، یا راه‌اندازی از طریق یک عملیات اسکریپتی آغاز می‌شود؛ به‌جز انواع `reload` و `back_forward` که در ادامه فهرست شده‌اند.
- `"reload"`
  - پیمایش از طریق عملیات بارگذاری مجدد مرورگر، {{domxref("location.reload()")}} یا یک دستور pragma از نوع Refresh مانند `<meta http-equiv="refresh" content="300">` انجام می‌شود.
- `"back_forward"`
  - پیمایش از طریق عملیات جابه‌جایی در تاریخچه مرورگر انجام می‌شود.

## مثال‌ها

### ثبت پیمایش‌های بارگذاری مجدد

ویژگی `type` را می‌توان برای بررسی این‌که آیا پیمایش از نوع `reload` بوده است استفاده کرد. برای مثال، می‌توانید این ورودی‌های `reload` را در یک endpoint سمت سرور جمع‌آوری کنید تا مشخص کنید کدام صفحه‌های سایت شما بیشترین بارگذاری مجدد را دارند، یا همه نوع‌های پیمایش را جمع‌آوری کرده و تعیین کنید چه درصدی از کاربران به عقب و جلو می‌روند.

مثال زیر از {{domxref("PerformanceObserver")}} استفاده می‌کند که هنگام ثبت هر ورودی عملکردی جدید از نوع `navigation` در جدول زمانی عملکرد مرورگر، اعلانی ارسال می‌کند. از گزینه `buffered` برای دسترسی به ورودی‌های پیش از ایجاد observer استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    if (entry.type === "reload") {
      console.log(`${entry.name} was reloaded!`);
      console.log(entry);
    }
  });
});

observer.observe({ type: "navigation", buffered: true });
```

مثال زیر از {{domxref("Performance.getEntriesByType()")}} استفاده می‌کند که فقط ورودی‌های عملکردی `navigation` موجود در جدول زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const entries = performance.getEntriesByType("navigation");
entries.forEach((entry) => {
  if (entry.type === "reload") {
    console.log(`${entry.name} was reloaded!`);
    console.log(entry);
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}