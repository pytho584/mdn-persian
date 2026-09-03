---
title: "PreferenceObject"
source: "https://developer.mozilla.org/en-US/docs/Web/API/PreferenceObject"

---
title: PreferenceObject
slug: Web/API/PreferenceObject
page-type: web-api-interface
status:
  - experimental
browser-compat: api.PreferenceObject
spec-urls: https://drafts.csswg.org/mediaqueries-5/#preference-object-interface
---

{{APIRef("User Preferences API")}}{{SeeCompatTable}}{{SecureContext_Header}}

رابط **`PreferenceObject`** در [User Preferences API](/en-US/docs/Web/API/User_Preferences_API) ویژگی‌ها و روش‌هایی برای خواندن و تغییر ترجیحات کاربر ارائه می‌دهد.

برای دسترسی به اشیاء `PreferenceObject` که نمایانگر هر ترجیح موجود هستند، از {{domxref("PreferenceManager")}} سند (از طریق {{domxref("Navigator.preferences")}}) استفاده کنید.

رابط `PreferenceManager` از {{domxref("EventTarget")}} ارث‌بری می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("PreferenceObject.override")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : مقدار جایگزین در صورت تنظیم شدن، در غیر این صورت `null`.
- {{domxref("PreferenceObject.value")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : مقدار جایگزین در صورت تنظیم شدن، در غیر این صورت مقدار پیش‌فرض کاربر عامل (UA).
- {{domxref("PreferenceObject.validValues")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : مقادیر معتبر برای مقدار جایگزین.

## روش‌های نمونه

- {{domxref("PreferenceObject.clearOverride()")}} {{Experimental_Inline}}
  - : هر مقدار جایگزین قبلی را به `null` بازنشانی می‌کند و رویداد {{domxref("PreferenceObject.change_event", "change")}} را فعال می‌کند.
- {{domxref("PreferenceObject.requestOverride()")}} {{Experimental_Inline}}
  - : درخواست جایگزینی برای ترجیح می‌دهد و در صورت موفقیت رویداد {{domxref("PreferenceObject.change_event", "change")}} را فعال می‌کند.

## رویدادها

- {{domxref("PreferenceObject.change_event", "change")}} {{Experimental_Inline}}
  - : زمانی که مقدار جایگزین تنظیم یا بازنشانی می‌شود فعال می‌گردد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}