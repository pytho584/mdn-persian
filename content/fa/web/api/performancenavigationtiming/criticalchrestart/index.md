---
title: "PerformanceNavigationTiming: criticalCHRestart property"
short-title: criticalCHRestart
slug: Web/API/PerformanceNavigationTiming/criticalCHRestart
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceNavigationTiming.criticalCHRestart
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

یک وب‌سایت می‌تواند با درج یک [Client Hint](/en-US/docs/Web/HTTP/Guides/Client_hints) خاص در هدر پاسخ HTTP {{HTTPHeader("Critical-CH")}} (به همراه هدر درخواست HTTP {{HTTPHeader("Accept-CH")}} که برای همه Client Hint‌ها، چه بحرانی و چه غیربحرانی، لازم است) نشان دهد که آن Client Hint برای صفحه بحرانی است. این کار باعث راه‌اندازی مجدد اتصال (connection restart) می‌شود اگر آن hint که در هدر پاسخ `Critical-CH` فهرست شده می‌توانست در درخواست HTTP اولیه فرستاده شود اما فرستاده نشده بود. اگر مرورگر از آن Client Hint پشتیبانی نکند، نادیده گرفته می‌شود و راه‌اندازی مجدد اتصال رخ نمی‌دهد.

خاصیت فقط خواندنی **`criticalCHRestart`** زمان وقوع راه‌اندازی مجدد اتصال را نشان می‌دهد.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}} که تعداد میلی‌ثانیه‌های سپری‌شده از {{domxref("PerformanceEntry.startTime")}} تا زمان وقوع راه‌اندازی مجدد اتصال را بر حسب میلی‌ثانیه نشان می‌دهد.

اگر مقدار `0` باشد، اتصال راه‌اندازی مجدد نشده است.

## مثال‌ها

### تشخیص صفحاتی که راه‌اندازی مجدد اتصال داشته‌اند

کد جاوااسکریپت زیر می‌تواند برای بررسی اینکه آیا اتصال راه‌اندازی مجدد شده است استفاده شود:

```js
const restartTime =
  performance?.getEntriesByType?.("navigation")[0]?.criticalCHRestart;
if (restartTime > 0) {
  console.log("زمان وقوع راه‌اندازی مجدد اتصال:", restartTime);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Client hints](/en-US/docs/Web/HTTP/Guides/Client_hints)
- [User-Agent Client Hints API](/en-US/docs/Web/API/User-Agent_Client_Hints_API)
- [بهبود حریم خصوصی کاربر و تجربه توسعه‌دهنده با User-Agent Client Hints](https://developer.chrome.com/docs/privacy-security/user-agent-client-hints) (developer.chrome.com)
- {{HTTPHeader("Accept-CH")}}
- {{HTTPHeader("Critical-CH")}}