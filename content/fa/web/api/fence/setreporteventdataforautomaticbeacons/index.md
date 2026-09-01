---
title: "Fence: setReportEventDataForAutomaticBeacons() method"
---

---
title: "Fence: setReportEventDataForAutomaticBeacons() method"
short-title: setReportEventDataForAutomaticBeacons()
slug: Web/API/Fence/setReportEventDataForAutomaticBeacons
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.Fence.setReportEventDataForAutomaticBeacons
---

{{SeeCompatTable}}{{APIRef("Fenced Frame API")}}

متد **`setReportEventDataForAutomaticBeacons()`** از رابط {{domxref("Fence")}} داده‌های رویدادی را مشخص می‌کند که هنگام انجام یک پیمایش (navigation) درون یک {{htmlelement("fencedframe")}} ارسال می‌شود. این داده‌ها از طریق یک [beacon](/en-US/docs/Web/API/Beacon_API) خودکار به یک یا چند URL مشخص که از طریق متد {{domxref("InterestGroupReportingScriptRunnerGlobalScope.registerAdBeacon", "registerAdBeacon()")}} از [Protected Audience API](https://privacysandbox.google.com/private-advertising/protected-audience) ثبت شده‌اند ارسال می‌شوند؛ هدف از این کار جمع‌آوری داده‌های گزارش‌دهی برای نتایج حراج آگهی (ad auction) است.

> [!NOTE]
> {{domxref("Fence.reportEvent", "reportEvent()")}} نیز ارسال داده گزارش مشابهی را فراهم می‌کند، با این تفاوت که در آن حالت، ارسال داده از طریق فراخوانی صریح متد انجام می‌شود، نه از طریق یک پیمایش.

## سینتکس

```js-nolint
setReportEventDataForAutomaticBeacons(event)
```

### پارامترها

- `event`
  - : یک شیء (object) که داده‌های مورد نظر برای ارسال را نشان می‌دهد. ویژگی‌های ممکن به شرح زیر هستند:
    - `eventType`
      - : یک رشته (string) که نوع رویداد در حال گزارش‌دهی را نشان می‌دهد. مقادیر موجود عبارتند از:
        - `reserved.top_navigation_start`: رویدادی که هنگام شروع یک پیمایش سطح بالا (top-level navigation) شلیک می‌شود.
        - `reserved.top_navigation_commit`: رویدادی که هنگام تکمیل یک پیمایش سطح بالا (top-level navigation) شلیک می‌شود.
    - `eventData`
      - : یک رشته (string) که داده‌های مورد نظر برای ارسال را نشان می‌دهد.
    - `destination`
      - : یک آرایه (array) شامل یک یا چند مقدار شمارشی (enumerated) که انواع مقصد را نشان می‌دهد. این‌ها طرف‌های درگیر هستند که داده‌ها را در URLهای ثبت‌شده‌ی خود دریافت می‌کنند (یعنی از طریق {{domxref("InterestGroupReportingScriptRunnerGlobalScope.registerAdBeacon", "registerAdBeacon()")}}). مقادیر ممکن عبارتند از:
        - `"buyer"`: پیشنهاددهنده (bidder) در حراج آگهی.
        - `"seller"`: فروشنده سطح بالایی که حراج آگهی را اجرا می‌کند.
        - `"component-seller"`: فروشنده یک حراج جزء (component auction) در یک حراج چندسطحی (multi-level auction).
        - `"direct-seller"`: فروشنده‌ای که مستقیماً حراجی را که خریدار در آن پیشنهاد داده بود اجرا کرده است. اگر آگهی در یک حراج تکسطحی (single-level auction) بود، مقدار استفاده‌شده `"seller"` خواهد بود و اگر آگهی در یک حراج چندسطحی بود، مقدار استفاده‌شده `"component-seller"` خواهد بود.
        - `"shared-storage-select-url"`: یک مکان ذخیره‌سازی در [Shared Storage API](https://privacysandbox.google.com/private-advertising/shared-storage)، همان‌طور که در فراخوانی متد {{domxref("WindowSharedStorage.selectURL", "Window.sharedStorage.selectURL()")}} تعریف شده است.
    - `once` {{optional_inline}}
      - : یک مقدار بولی (boolean). اگر روی `true` تنظیم شود، beacon خودکار فقط برای رویداد بعدی ارسال می‌شود و تا زمانی که `setReportEventDataForAutomaticBeacons()` دوباره فراخوانی شود، beaconها برای رویدادهای بعدی ارسال نخواهند شد. برای مثال، وقتی با یک هندلر `click` استفاده شود، می‌توان از آن برای ارسال داده‌های beacon فقط برای پیمایش‌های سطح بالای مشخص استفاده کرد، نه برای تمام پیمایش‌های سطح بالا. این ویژگی به‌طور پیش‌فرض روی `false` است.

### مقدار بازگشتی

هیچ (`Undefined`).

## مثال‌ها

```js
window.fence.setReportEventDataForAutomaticBeacons({
  eventType: "reserved.top_navigation_start",
  eventData: "an example string",
  destination: ["seller", "buyer"],
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [Fenced frames](https://privacysandbox.google.com/private-advertising/fenced-frame) در privacysandbox.google.com
- [The Privacy Sandbox](https://privacysandbox.google.com/) در privacysandbox.google.com