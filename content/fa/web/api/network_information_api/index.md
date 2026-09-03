---
title: "Network Information API"
---

---
title: Network Information API
slug: Web/API/Network_Information_API
page-type: web-api-overview
browser-compat: api.NetworkInformation
spec-urls: https://wicg.github.io/netinfo/
---

{{DefaultAPISidebar("Network Information API")}} {{AvailableInWorkers}}

**Network Information API** اطلاعاتی دربارهٔ نوع کلی اتصال سیستم (مثلاً «wifi»، «cellular» و غیره) فراهم می‌کند. از این اطلاعات می‌توان برای انتخاب محتوای با کیفیت بالا یا کیفیت پایین بر اساس اتصال کاربر استفاده کرد.

این رابط از یک شیء {{domxref("NetworkInformation")}} تشکیل شده است که نمونه‌ای از آن توسط خاصیت {{domxref("Navigator.connection")}} یا خاصیت {{domxref("WorkerNavigator.connection")}} بازگردانده می‌شود.

## رابط‌ها

- {{domxref("NetworkInformation")}}
  - : اطلاعاتی دربارهٔ اتصالی که دستگاه برای برقراری ارتباط با شبکه استفاده می‌کند فراهم می‌کند و به اسکریپت‌ها امکان می‌دهد تا در صورت تغییر نوع اتصال مطلع شوند. رابط `NetworkInformation` قابل نمونه‌سازی نیست. در عوض از طریق رابط {{domxref("Navigator")}} یا رابط {{domxref("WorkerNavigator")}} قابل دسترسی است.

### توسعه‌های مربوط به رابط‌های دیگر

- {{domxref("Navigator.connection")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("NetworkInformation")}} شامل اطلاعات مربوط به اتصال شبکهٔ یک دستگاه را بازمی‌گرداند.
- {{domxref("WorkerNavigator.connection")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("NetworkInformation")}} شامل اطلاعات مربوط به اتصال شبکهٔ یک دستگاه را فراهم می‌کند.

## مثال‌ها

### تشخیص تغییرات اتصال

این مثال تغییرات اتصال کاربر را زیر نظر می‌گیرد.

```js
let type = navigator.connection.effectiveType;

function updateConnectionStatus() {
  console.log(
    `Connection type changed from ${type} to ${navigator.connection.effectiveType}`,
  );
  type = navigator.connection.effectiveType;
}

navigator.connection.addEventListener("change", updateConnectionStatus);
```

### پیش‌بارگذاری منابع حجیم

شیء connection برای تصمیم‌گیری دربارهٔ اینکه آیا منابعی که پهنای باند یا حافظهٔ زیادی مصرف می‌کنند پیش‌بارگذاری شوند یا نه مفید است. این مثال باید بلافاصله پس از بارگذاری صفحه فراخوانی شود تا نوع اتصالی را بررسی کند که شاید پیش‌بارگذاری ویدیو در آن مطلوب نباشد. اگر اتصال cellular یافت شود، پرچم `preloadVideo` روی `false` تنظیم می‌شود. برای سادگی و وضوح، این مثال فقط یک نوع اتصال را آزمایش می‌کند. در کاربرد واقعی، احتمالاً از دستور switch یا روش دیگری برای بررسی همهٔ مقادیر ممکن {{domxref("NetworkInformation.type")}} استفاده می‌شود. صرف‌نظر از مقدار `type`، می‌توانید تخمینی از سرعت اتصال را از طریق خاصیت {{domxref("NetworkInformation.effectiveType")}} به دست آورید.

```js
let preloadVideo = true;
const connection = navigator.connection;
if (connection) {
  if (connection.effectiveType === "slow-2g") {
    preloadVideo = false;
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [رویدادهای آنلاین و آفلاین](/en-US/docs/Web/API/Navigator/onLine)