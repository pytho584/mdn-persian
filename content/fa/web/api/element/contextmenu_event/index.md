---
title: "Element: contextmenu event"
short-title: contextmenu
slug: Web/API/Element/contextmenu_event
page-type: web-api-event
browser-compat: api.Element.contextmenu_event
---

{{APIRef("Pointer Events")}}

رویداد **`contextmenu`** زمانی فعال می‌شود که کاربر تلاش کند یک منوی زمینه (context menu) را باز کند. این رویداد معمولاً با کلیک روی دکمه راست ماوس یا با فشار دادن کلید منوی زمینه (context menu key) ایجاد می‌شود.

در حالت دوم، منوی زمینه در پایین سمت چپ عنصر دارای فوکوس نمایش داده می‌شود، مگر اینکه عنصر یک درخت (tree) باشد، که در این صورت منوی زمینه در پایین سمت چپ ردیف جاری نمایش داده می‌شود.

هر رویداد کلیک راست که غیرفعال نشده باشد (با فراخوانی متد {{domxref("Event.preventDefault", "preventDefault()")}} رویداد کلیک)، باعث می‌شود یک رویداد `contextmenu` در عنصر هدف فعال شود.

> [!NOTE]
> یک استثنا در Firefox: اگر کاربر در حین کلیک راست، کلید <kbd>Shift</kbd> را نگه دارد، منوی زمینه بدون فعال شدن رویداد `contextmenu` نمایش داده می‌شود.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("contextmenu", (event) => { })

oncontextmenu = (event) => { }
```

## نوع رویداد

یک {{domxref("PointerEvent")}}. از {{domxref("MouseEvent")}} به ارث برده شده است.

{{InheritanceDiagram("PointerEvent")}}

> [!NOTE]
> در نسخه‌های قدیمی‌تر مشخصات، نوع رویداد برای این رویداد یک {{domxref("MouseEvent")}} بود. برای اطلاعات بیشتر به [سازگاری مرورگر](#browser_compatibility) مراجعه کنید.

## مثال‌ها

### لغو رویداد `contextmenu`

در این مثال، عملکرد پیش‌فرض رویداد `contextmenu` با استفاده از `preventDefault()` در هنگام فعال شدن رویداد `contextmenu` در پاراگراف اول لغو می‌شود. در نتیجه، پاراگراف اول هنگام کلیک راست هیچ کاری انجام نمی‌دهد، در حالی که پاراگراف دوم منوی زمینه استاندارد ارائه شده توسط مرورگر شما را نمایش می‌دهد.

> [!NOTE]
> در Firefox، اگر در حین کلیک راست کلید <kbd>Shift</kbd> را نگه دارید، منوی زمینه بدون فعال شدن رویداد `contextmenu` نمایش داده می‌شود. بنابراین، لغو رویداد مانع از نمایش منوی زمینه نمی‌شود.

#### HTML

```html
<p id="noContextMenu">منوی زمینه در این پاراگراف غیرفعال شده است.</p>
<p>اما در این یکی غیرفعال نشده است.</p>
```

#### JavaScript

```js
const noContext = document.getElementById("noContextMenu");

noContext.addEventListener("contextmenu", (e) => {
  e.preventDefault();
});
```

#### نتیجه

{{EmbedLiveSample("Canceling the contextmenu event")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [یادگیری: مقدمه‌ای بر رویدادها](/en-US/docs/Learn_web_development/Core/Scripting/Events)
- {{domxref("Element/auxclick_event", "auxclick")}}
- {{domxref("Element/click_event", "click")}}
- {{domxref("Element/dblclick_event", "dblclick")}}
- {{domxref("Element/mousedown_event", "mousedown")}}
- {{domxref("Element/mouseup_event", "mouseup")}}
- {{domxref("Element/pointerdown_event", "pointerdown")}}
- {{domxref("Element/pointerup_event", "pointerup")}}