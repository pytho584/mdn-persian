---
title: "InputDeviceCapabilities API"
---

---
title: InputDeviceCapabilities API
slug: Web/API/InputDeviceCapabilities_API
page-type: web-api-overview
status:
  - experimental
browser-compat: api.InputDeviceCapabilities
---

{{DefaultAPISidebar("Input Device Capabilities API")}}{{SeeCompatTable}}

API InputDeviceCapabilities جزئیات مربوط به منابع زیربنایی رویدادهای ورودی را فراهم می‌کند. این API سعی می‌کند رفتار دستگاه را توصیف کند، نه اینکه چیستی آن را مشخص کند. برای مثال، نسخه اول این API نشان می‌دهد که آیا یک دستگاه رویدادهای لمسی را تولید می‌کند یا خیر، نه اینکه آیا یک صفحه لمسی است.

## مفاهیم و کاربرد قابلیت‌های دستگاه ورودی

از آنجایی که رویدادهای DOM ورودی دستگاه را انتزاع می‌کنند، هیچ راهی برای فهمیدن اینکه کدام دستگاه یا نوع دستگاهی یک رویداد را ایجاد کرده است، فراهم نمی‌کنند. این می‌تواند منجر به مواردی شود که یک عمل واحد چندین کنترل‌کننده رویداد را فعال کند. برای مقابله با این مسئله، توسعه‌دهندگان فرضیاتی می‌کنند و از روش‌های اکتشافی (heuristics) برای نرمال‌سازی رفتار در صفحات وب استفاده می‌کنند.

API InputDeviceCapabilities این مشکل را با انتزاع قابلیت‌های دستگاه‌های ورودی حل می‌کند. به عنوان مثال، فرض کنید یک صفحه وب داریم که هم رویداد `touchstart` و هم رویداد `mousedown` را پیاده‌سازی می‌کند. می‌توانیم فرض کنیم که اگر رویداد touchstart فعال شود، دستگاه کاربر دارای رابط لمسی است. اما وقتی رویداد mousedown فعال می‌شود چطور؟ مفید خواهد بود که بدانیم آیا رویداد `touchstart` نیز فعال شده است تا از انجام دوباره همان عمل جلوگیری کنیم. این کار را می‌توانیم با بررسی ویژگی `sourceCapabilities` از {{domxref("UIEvent")}} انجام دهیم.

```js
myButton.addEventListener("mousedown", (e) => {
  // Touch event case handled above, don't change the style again on tap.
  if (!e.sourceCapabilities.firesTouchEvents) myButton.classList.add("pressed");
});
```

## اینترفیس‌ها

- {{domxref("InputDeviceCapabilities")}} {{Experimental_Inline}}
  - : اطلاعات منطقی درباره یک دستگاه ورودی فراهم می‌کند.

## افزونه‌ها به سایر اینترفیس‌ها

- {{domxref("UIEvent.sourceCapabilities")}} {{Experimental_Inline}} {{ReadOnlyInline}}
  - : یک نمونه از اینترفیس `InputDeviceCapabilities` را برمی‌گرداند که اطلاعاتی درباره دستگاه فیزیکی مسئول تولید یک رویداد لمسی فراهم می‌کند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}