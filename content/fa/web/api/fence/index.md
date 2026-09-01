---
title: Fence
slug: Web/API/Fence
page-type: web-api-interface
status:
  - experimental
browser-compat: api.Fence
---

{{SeeCompatTable}}{{APIRef("Fenced Frame API")}}

رابط **`Fence`** از {{domxref("Fenced Frame API", "Fenced Frame API", "", "nocode")}} شامل چندین تابع مرتبط با عملکرد {{htmlelement("fencedframe")}} است.

اشیاء `Fence` از طریق ویژگی {{domxref("Window.fence")}} قابل دسترسی هستند، اما فقط برای اسنادی که درون {{htmlelement("fencedframe")}}ها (بارگذاری شده از طریق {{domxref("FencedFrameConfig")}}ها) یا {{htmlelement("iframe")}}ها (بارگذاری شده از طریق URNهای مبهم) جاسازی شده‌اند، در دسترس هستند.

> [!NOTE]
> برای توضیحاتی درباره `FencedFrameConfig`ها و URNهای مبهم، به [چگونه `<fencedframe>`ها کار می‌کنند؟](/en-US/docs/Web/API/Fenced_frame_API#how_do_fencedframes_work) مراجعه کنید.

{{InheritanceDiagram}}

## روش‌های نمونه

- {{domxref("Fence.getNestedConfigs", "getNestedConfigs()")}} {{Experimental_Inline}}
  - : آرایه‌ای از `FencedFrameConfig`های بارگذاری شده در `<fencedframe>`های جاسازی شده درون `<fencedframe>` جاری را برمی‌گرداند.
- {{domxref("Fence.reportEvent", "reportEvent()")}} {{Experimental_Inline}}
  - : ارسال داده‌های گزارش را از طریق یک [beacon](/en-US/docs/Web/API/Beacon_API) به یک یا چند URL خاص که از طریق متد {{domxref("InterestGroupReportingScriptRunnerGlobalScope.registerAdBeacon", "registerAdBeacon()")}} از [Protected Audience API](https://privacysandbox.google.com/private-advertising/protected-audience) ثبت شده‌اند، به منظور جمع‌آوری نتایج حراج تبلیغات، راه‌اندازی می‌کند.
- {{domxref("Fence.setReportEventDataForAutomaticBeacons", "setReportEventDataForAutomaticBeacons()")}} {{Experimental_Inline}}
  - : داده‌های رویدادی را مشخص می‌کند که هنگام یک پیمایش درون `<fencedframe>` ارسال خواهد شد. این داده‌ها از طریق یک beacon خودکار به یک یا چند URL خاص که از طریق متد {{domxref("InterestGroupReportingScriptRunnerGlobalScope.registerAdBeacon", "registerAdBeacon()")}} از [Protected Audience API](https://privacysandbox.google.com/private-advertising/protected-audience) ثبت شده‌اند، به منظور جمع‌آوری داده‌های گزارش برای نتایج حراج تبلیغات، ارسال می‌شوند.

## مثال‌ها

```js
window.fence.reportEvent({
  eventType: "click",
  eventData: JSON.stringify({ clickX: "123", clickY: "456" }),
  destination: ["buyer", "seller"],
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [قاب‌های حصاردار (Fenced frames)](https://privacysandbox.google.com/private-advertising/fenced-frame) در privacysandbox.google.com
- [پلتفرم Privacy Sandbox](https://privacysandbox.google.com/) در privacysandbox.google.com