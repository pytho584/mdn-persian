---
title: "Event: explicitOriginalTarget property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Event/explicitOriginalTarget"
---

---
title: "Event: explicitOriginalTarget property"
short-title: explicitOriginalTarget
slug: Web/API/Event/explicitOriginalTarget
page-type: web-api-instance-property
status:
  - non-standard
browser-compat: api.Event.explicitOriginalTarget
---

{{APIRef("DOM")}}{{Non-standard_Header}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`explicitOriginalTarget`** از رابط {{domxref("Event")}}، هدف اصلیِ غیرمستعار (non-anonymous) رویداد را برمی‌گرداند.

اگر رویداد به دلایلی غیر از عبور از مرز ناشناس (anonymous boundary) تغییر هدف داده شده باشد (retargeted)، این ویژگی به هدفِ قبل از تغییر هدف اشاره می‌کند.

برای مثال، رویدادهای ماوس وقتی روی گره‌های متنی رخ می‌دهند به گرهٔ والدشان تغییر هدف می‌دهند (به [باگ فایرفاکس 185889](https://bugzil.la/185889) مراجعه کنید). در آن حالت، [`currentTarget`](/en-US/docs/Web/API/Event/currentTarget) والد را نشان می‌دهد، در حالی که این ویژگی گرهٔ متنی را نشان می‌دهد.

این ویژگی همچنین با [`originalTarget`](/en-US/docs/Web/API/Event/originalTarget) تفاوت دارد، زیرا هرگز حاوی محتوای ناشناس (anonymous content) نخواهد بود.

## مقدار

شیء {{domxref("EventTarget")}} را برمی‌گرداند، یا اگر وجود نداشته باشد `null` برمی‌گرداند.

## مثال

می‌توان از این ویژگی همراه با `<command>` استفاده کرد تا جزئیات رویدادِ شیء اصلیِ صداکنندهٔ فرمان به دست آید.

```js
function myCommand(ev) {
  alert(ev.explicitOriginalTarget.nodeName); // 'menuitem' را برمی‌گرداند
}
```

```xml
<xul:command id="my-cmd-anAction" oncommand="myCommand(event);"/>

<xul:menulist>
  <xul:menupopup>
    <xul:menuitem label="Get my element name!" command="my-cmd-anAction"/>
  </xul:menupopup>
</menulist>
```

## مشخصات

_این یک ویژگی مخصوصِ موزیلا است و بخشی از هیچ مشخصات فعلی نیست. در مسیر استاندارد شدن نیز قرار ندارد._

## سازگاری مرورگر

{{Compat}}