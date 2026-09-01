---
title: "Event: returnValue property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Event/returnValue"
---

---
title: "Event: returnValue property"
short-title: returnValue
slug: Web/API/Event/returnValue
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.Event.returnValue
---

{{APIRef("DOM")}}{{Deprecated_Header}}{{AvailableInWorkers}}

ویژگی **`returnValue`** از {{domxref("Event")}}، نشان می‌دهد که آیا اقدام پیش‌فرض برای این رویداد جلوگیری شده است یا خیر.

این ویژگی به طور پیش‌فرض `true` است و امکان انجام اقدام پیش‌فرض را فراهم می‌کند. تنظیم این ویژگی به `false` از اقدام پیش‌فرض جلوگیری می‌کند.

> [!NOTE]
> اگرچه `returnValue` در استاندارد DOM گنجانده شده است، اما عمدتاً برای پشتیبانی از کدهای موجود ارائه شده است. به جای این ویژگی قدیمی، از {{DOMxRef("Event.preventDefault", "preventDefault()")}} و {{domxref("Event.defaultPrevented", "defaultPrevented")}} استفاده کنید.

## مقدار

یک مقدار بولی است که اگر رویداد لغو نشده باشد `true` است؛ در غیر این صورت، اگر رویداد لغو شده یا اقدام پیش‌فرض جلوگیری شده باشد، مقدار `false` خواهد بود.

مقدار `returnValue` برعکس مقداری است که توسط {{domxref("Event.defaultPrevented", "defaultPrevented")}} بازگردانده می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLDialogElement.returnValue")}}: مقدار بازگشتی برای {{HTMLElement("dialog")}}.