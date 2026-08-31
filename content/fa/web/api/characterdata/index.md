---
title: CharacterData
slug: Web/API/CharacterData
page-type: web-api-interface
browser-compat: api.CharacterData
---

{{APIRef("DOM")}}

اینترفیس انتزاعی **`CharacterData`** یک شیء {{domxref("Node")}} را نشان می‌دهد که حاوی نویسه‌ها (کاراکترها) است. این یک اینترفیس انتزاعی است؛ به این معنی که هیچ شیئی از نوع `CharacterData` وجود ندارد: این اینترفیس توسط اینترفیس‌های دیگری مانند {{domxref("Text")}}، {{domxref("Comment")}}، {{domxref("CDATASection")}} یا {{domxref("ProcessingInstruction")}} پیاده‌سازی می‌شود که انتزاعی نیستند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این اینترفیس همچنین ویژگی‌های والدهای خود، {{domxref("Node")}} و {{domxref("EventTarget")}} را به ارث می‌برد._

- {{domxref("CharacterData.data")}}
  - : یک رشته که دادهٔ متنی موجود در این شیء را نشان می‌دهد.
- {{domxref("CharacterData.length")}} {{ReadOnlyInline}}
  - : یک عدد برمی‌گرداند که اندازهٔ رشتهٔ موجود در شیء را نشان می‌دهد.
- {{domxref("CharacterData.nextElementSibling")}} {{ReadOnlyInline}}
  - : اولین {{domxref("Element")}} را برمی‌گرداند که _بعد از_ این گره قرار دارد و هم‌خواهر (sibling) آن است.
- {{domxref("CharacterData.previousElementSibling")}} {{ReadOnlyInline}}
  - : اولین {{domxref("Element")}} را برمی‌گرداند که _قبل از_ این گره قرار دارد و هم‌خواهر (sibling) آن است.

## روش‌های نمونه

_این اینترفیس همچنین متدهای والدهای خود، {{domxref("Node")}} و {{domxref("EventTarget")}} را به ارث می‌برد._

- {{domxref("CharacterData.after()")}}
  - : مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها را در فهرست فرزندان والدِ `CharacterData`، درست بعد از خودِ شیء `CharacterData` درج می‌کند.
- {{domxref("CharacterData.appendData()")}}
  - : رشتهٔ داده‌شده را به رشتهٔ `CharacterData.data` اضافه می‌کند؛ وقتی این متد برمی‌گردد، `data` شامل رشتهٔ الحاق‌شده است.
- {{domxref("CharacterData.before()")}}
  - : مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها را در فهرست فرزندان والدِ `CharacterData`، درست قبل از خودِ شیء `CharacterData` درج می‌کند.
- {{domxref("CharacterData.deleteData()")}}
  - : تعداد مشخصی از نویسه‌ها را از رشتهٔ `CharacterData.data`، با شروع از آفست مشخص‌شده، حذف می‌کند؛ وقتی این متد برمی‌گردد، `data` شامل رشتهٔ کوتاه‌شده است.
- {{domxref("CharacterData.insertData()")}}
  - : نویسه‌های مشخص‌شده را در آفست مشخص، در رشتهٔ `CharacterData.data` درج می‌کند؛ وقتی این متد برمی‌گردد، `data` شامل رشتهٔ تغییر‌یافته است.
- {{domxref("CharacterData.remove()")}}
  - : شیء را از فهرست فرزندان والدش حذف می‌کند.
- {{domxref("CharacterData.replaceData()")}}
  - : تعداد مشخصی از نویسه‌ها را، با شروع از آفست مشخص، با رشتهٔ مشخص‌شده جایگزین می‌کند؛ وقتی این متد برمی‌گردد، `data` شامل رشتهٔ تغییر‌یافته است.
- {{DOMxRef("CharacterData.replaceWith()")}}
  - : نویسه‌های موجود در فهرست فرزندان والدش را با مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها جایگزین می‌کند.
- {{domxref("CharacterData.substringData()")}}
  - : رشته‌ای شامل بخشی از `CharacterData.data` را با طول مشخص‌شده و شروع از آفست مشخص برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [صفحهٔ نمای کلی DOM](/en-US/docs/Web/API/Document_Object_Model).
- اینترفیس‌های انضمامی که آن را پیاده‌سازی می‌کنند: {{domxref("Text")}}، {{domxref("CDATASection")}}، {{domxref("ProcessingInstruction")}} و {{domxref("Comment")}}.