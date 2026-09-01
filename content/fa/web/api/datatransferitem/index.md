---
title: "DataTransferItem"
---

---
title: DataTransferItem
slug: Web/API/DataTransferItem
page-type: web-api-interface
browser-compat: api.DataTransferItem
---

{{APIRef("HTML Drag and Drop API")}}

شیء **`DataTransferItem`** نمایانگر یک آیتم داده‌ای کشیدن است. در طول یک _عملیات کشیدن_، هر {{domxref("DragEvent")}} دارای ویژگی {{domxref("DragEvent.dataTransfer","dataTransfer")}} است که شامل یک {{domxref("DataTransferItemList","فهرست")}} از آیتم‌های داده‌ای کشیدن می‌شود. هر آیتم در این فهرست یک شیء `DataTransferItem` است.

`DataTransferItem` در ابتدا برای [HTML Drag and Drop API](/en-US/docs/Web/API/HTML_Drag_and_Drop_API) طراحی شده بود و همچنان در بخش HTML drag-and-drop تعریف می‌شود، اما اکنون توسط APIهای دیگری مانند {{domxref("ClipboardEvent.clipboardData")}} و {{domxref("InputEvent.dataTransfer")}} نیز استفاده می‌شود. مستندات `DataTransferItem` در درجه اول کاربرد آن را در عملیات کشیدن و رها کردن توضیح می‌دهد و برای کاربرد `DataTransferItem` در آن بافتارها باید به مستندات سایر APIها مراجعه کنید.

این رابط سازنده ندارد.

## ویژگی‌های نمونه

- {{domxref("DataTransferItem.kind")}} {{ReadOnlyInline}}
  - : _نوع_ آیتم داده‌ای کشیدن، `string` یا `file`.
- {{domxref("DataTransferItem.type")}} {{ReadOnlyInline}}
  - : نوع آیتم داده‌ای کشیدن، معمولاً یک نوع MIME.

## روش‌های نمونه

- {{domxref("DataTransferItem.getAsFile()")}}
  - : شیء {{domxref("File")}} مرتبط با آیتم داده‌ای کشیدن را برمی‌گرداند (یا در صورتی که آیتم کشیدن یک فایل نباشد، `null`).
- {{domxref("DataTransferItem.getAsFileSystemHandle()")}} {{Experimental_Inline}}
  - : یک {{jsxref('Promise')}} برمی‌گرداند که اگر آیتم کشیده‌شده یک فایل باشد، با یک {{domxref('FileSystemFileHandle')}} و اگر یک پوشه باشد، با یک {{domxref('FileSystemDirectoryHandle')}} تکمیل می‌شود.
- {{domxref("DataTransferItem.getAsString()")}}
  - : تابع بازگشتی مشخص‌شده را با رشته آیتم داده‌ای کشیدن به‌عنوان آرگومان فراخوانی می‌کند.
- {{domxref("DataTransferItem.webkitGetAsEntry()")}}
  - : یک شیء بر اساس {{domxref("FileSystemEntry")}} برمی‌گرداند که نشان‌دهنده ورودی فایل انتخابی در سامانه فایل آن است. این شیء معمولاً یا یک {{domxref("FileSystemFileEntry")}} است یا یک {{domxref("FileSystemDirectoryEntry")}}.

## مثال

همه روش‌ها و ویژگی‌های این رابط صفحه مرجع خود را دارند و هر صفحه مرجع شامل یک مثال از کاربرد آن است.

## مشخصات‌ها

{{Specifications}}

## سازگاری مرورگر

{{Compat}}