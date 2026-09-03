```markdown
---
title: "NetworkInformation"
---

---
title: NetworkInformation
slug: Web/API/NetworkInformation
page-type: web-api-interface
browser-compat: api.NetworkInformation
---

{{APIRef("Network Information API")}} {{AvailableInWorkers}}

رابط کاربری **`NetworkInformation`** از [Network Information API](/en-US/docs/Web/API/Network_Information_API) اطلاعاتی درباره اتصالی که دستگاه برای برقراری ارتباط با شبکه از آن استفاده می‌کند فراهم می‌کند و همچنین مکانیزمی را برای اسکریپت‌ها فراهم می‌کند تا در صورت تغییر نوع اتصال، مطلع شوند.
رابط کاربری `NetworkInformation` را نمی‌توان مستقیماً نمونه‌سازی کرد. در عوض، از طریق ویژگی `connection` در رابط کاربری {{domxref("Navigator")}} یا رابط کاربری {{domxref("WorkerNavigator")}} قابل دسترسی است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

این رابط کاربری همچنین ویژگی‌های والد خود، {{domxref("EventTarget")}} را به ارث می‌برد.

- {{domxref("NetworkInformation.downlink")}} {{ReadOnlyInline}}
  - : برآورد پهنای باند مؤثر را بر حسب مگابیت بر ثانیه برمی‌گرداند که به نزدیک‌ترین مضرب ۲۵ کیلوبیت در ثانیه گرد شده است.
- {{domxref("NetworkInformation.downlinkMax")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : حداکثر سرعت دانلود را بر حسب مگابیت بر ثانیه (Mbps) برای فناوری اتصال زیرین برمی‌گرداند.
- {{domxref("NetworkInformation.effectiveType")}} {{ReadOnlyInline}}
  - : نوع مؤثر اتصال را برمی‌گرداند که یکی از مقادیر 'slow-2g'، '2g'، '3g' یا '4g' است. این مقدار با استفاده از ترکیبی از زمان رفت‌وبرگشت (round-trip time) مشاهده‌شده اخیر و مقادیر downlink تعیین می‌شود.
- {{domxref("NetworkInformation.rtt")}} {{ReadOnlyInline}}
  - : برآورد زمان رفت‌وبرگشت مؤثر اتصال فعلی را برمی‌گرداند که به نزدیک‌ترین مضرب ۲۵ میلی‌ثانیه گرد شده است.
- {{domxref("NetworkInformation.saveData")}} {{ReadOnlyInline}}
  - : در صورتی که کاربر گزینه کاهش مصرف داده را در عامل کاربر (user agent) فعال کرده باشد، `true` برمی‌گرداند.
- {{domxref("NetworkInformation.type")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : نوع اتصالی که دستگاه برای برقراری ارتباط با شبکه استفاده می‌کند را برمی‌گرداند. این مقدار یکی از موارد زیر خواهد بود:
    - `bluetooth` (بلوتوث)
    - `cellular` (سلولی)
    - `ethernet` (اترنت)
    - `none` (هیچ)
    - `wifi` (وای‌فای)
    - `wimax` (وایمکس)
    - `other` (سایر)
    - `unknown` (ناشناخته)

## روش‌های نمونه

این رابط کاربری همچنین روش‌های والد خود، {{domxref("EventTarget")}} را به ارث می‌برد.

## رویدادها

- {{domxref("NetworkInformation.change_event", "change")}}
  - : رویدادی که هنگام تغییر اطلاعات اتصال رخ می‌دهد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [رویدادهای آنلاین و آفلاین](/en-US/docs/Web/API/Navigator/onLine)
```