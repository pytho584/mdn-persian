---
title: "PerformanceNavigation: type property"
short-title: type
slug: Web/API/PerformanceNavigation/type
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.PerformanceNavigation.type
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

خاصیت فقط‌خواندنی قدیمی
**`PerformanceNavigation.type`**
یک `unsigned short` برمی‌گرداند که شامل یک ثابت توصیف‌کننده نحوه ناوبری به این صفحه است.

> [!WARNING]
> این رابط و خاصیت آن در [مشخصات سطح ۲ زمان‌بندی ناوبری](https://w3c.github.io/navigation-timing/#obsolete) منسوخ اعلام شده است.
> لطفاً به‌جای آن از رابط {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

## مقدار

یک `unsigned short`.

مقادیر ممکن عبارتند از:

<table class="no-markdown">
  <thead>
    <tr>
      <th scope="col">مقدار</th>
      <th scope="col">نام ثابت</th>
      <th scope="col">معنی</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>0</code></td>
      <td><code>TYPE_NAVIGATE</code></td>
      <td>
        صفحه از طریق دنبال کردن یک پیوند، نشانک، ارسال فرم، اسکریپت یا تایپ URL در نوار آدرس باز شده است.
      </td>
    </tr>
    <tr>
      <td><code>1</code></td>
      <td><code>TYPE_RELOAD</code></td>
      <td>
        صفحه با کلیک روی دکمه بارگذاری مجدد یا از طریق روش {{domxref("Location.reload()")}} باز شده است.
      </td>
    </tr>
    <tr>
      <td><code>2</code></td>
      <td><code>TYPE_BACK_FORWARD</code></td>
      <td>صفحه با ناوبری به داخل تاریخچه باز شده است.</td>
    </tr>
    <tr>
      <td><code>255</code></td>
      <td><code>TYPE_RESERVED</code></td>
      <td>هر روش دیگری.</td>
    </tr>
  </tbody>
</table>

> [!NOTE]
> در گذشته، توسعه‌دهندگان برای دریافت نشانه‌ای از نرخ برخورد حافظه نهان عقب/جلو ({{glossary("bfcache")}})، مقدار `"TYPE_BACK_FORWARD"` را بررسی می‌کردند. اما این کار دلایل مسدود شدن bfcache یا داده دیگری ارائه نمی‌داد. برای پایش bfcache از این پس باید از خاصیت {{domxref("PerformanceNavigationTiming.notRestoredReasons")}} استفاده شود. اطلاعات بیشتر در [پایش دلایل مسدود شدن bfcache](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons) موجود است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("PerformanceNavigation")}} که این خاصیت به آن تعلق دارد.