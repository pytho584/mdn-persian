---
title: NamedNodeMap
slug: Web/API/NamedNodeMap
page-type: web-api-interface
browser-compat: api.NamedNodeMap
---

{{APIRef("DOM")}}

رابط **`NamedNodeMap`** مجموعه‌ای از اشیاء {{domxref("Attr")}} را نمایش می‌دهد. اشیاء درون یک `NamedNodeMap` بر خلاف {{domxref("NodeList")}} ترتیب خاصی ندارند، اگرچه می‌توان با استفاده از یک ایندکس (مانند آرایه) به آن‌ها دسترسی داشت.

یک شیء `NamedNodeMap` _زنده_ است و بنابراین اگر تغییراتی در محتوای آن به صورت داخلی یا خارجی ایجاد شود، به طور خودکار به‌روزرسانی می‌شود.

> [!NOTE]
> اگرچه این رابط `NamedNodeMap` نامیده می‌شود، اما با اشیاء {{domxref("Node")}} سروکار ندارد، بلکه با اشیاء {{domxref("Attr")}} کار می‌کند که یک کلاس تخصصی از اشیاء {{domxref("Node")}} هستند.

## ویژگی‌های نمونه

_این رابط هیچ ویژگیای را به ارث نمی‌برد._

- {{domxref("NamedNodeMap.length")}} {{ReadOnlyInline}}
  - : تعداد اشیاء موجود در نقشه را بازمی‌گرداند.

## روش‌های نمونه

_این رابط هیچ روشی را به ارث نمی‌برد._

- {{domxref("NamedNodeMap.getNamedItem()")}}
  - : یک {{domxref("Attr")}} متناظر با نام داده شده را بازمی‌گرداند.
- {{domxref("NamedNodeMap.setNamedItem()")}}
  - : {{domxref("Attr")}} شناسایی‌شده در نقشه توسط نام داده شده را جایگزین می‌کند یا اضافه می‌نماید.
- {{domxref("NamedNodeMap.removeNamedItem()")}}
  - : {{domxref("Attr")}} شناسایی‌شده توسط نقشه داده شده را حذف می‌کند.
- {{domxref("NamedNodeMap.item()")}}
  - : {{domxref("Attr")}} را در ایندکس داده شده بازمی‌گرداند، یا اگر ایندکس بزرگتر یا مساوی تعداد گره‌ها باشد `null` را برمی‌گرداند.
- {{domxref("NamedNodeMap.getNamedItemNS()")}}
  - : یک {{domxref("Attr")}} شناسایی‌شده توسط یک فضای نام و نام محلی مرتبط را بازمی‌گرداند.
- {{domxref("NamedNodeMap.setNamedItemNS()")}}
  - : {{domxref("Attr")}} شناسایی‌شده در نقشه توسط فضای نام و نام محلی مرتبط داده شده را جایگزین می‌کند یا اضافه می‌نماید.
- {{domxref("NamedNodeMap.removeNamedItemNS()")}}
  - : {{domxref("Attr")}} شناسایی‌شده توسط فضای نام و نام محلی مرتبط داده شده را حذف می‌کند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.attributes")}}