---
title: "DOMStringList"
slug: Web/API/DOMStringList
page-type: web-api-interface
browser-compat: api.DOMStringList
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

رابط **`DOMStringList`** یک نوع قدیمی (legacy) است که توسط برخی APIها بازگردانده می‌شود و یک لیست غیرقابل‌تغییر از رشته‌ها (`DOMString`) را نشان می‌دهد.

این رابط تلاشی [برای ایجاد یک لیست غیرقابل‌تغییر](https://stackoverflow.com/questions/74630989/why-use-domstringlist-rather-than-an-array/74641156#74641156) بود و تنها برای اینکه کدهای موجود را نشکند همچنان پشتیبانی می‌شود. APIهای مدرن ساختارهای لیست را با استفاده از انواع مبتنی بر [آرایه‌های](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) جاوااسکریپت نمایش می‌دهند، بنابراین بسیاری از متدهای آرایه در دسترس هستند و در عین حال معناشناسی اضافی بر استفاده از آنها تحمیل می‌کنند (مانند readonly کردن آیتم‌ها).

این دلایل تاریخی به این معنی نیست که شما به عنوان توسعه‌دهنده باید از `DOMStringList` اجتناب کنید. شما خودتان اشیاء `DOMStringList` را نمی‌سازید، بلکه آنها را از APIهایی مانند `Location.ancestorOrigins` دریافت می‌کنید و این APIها منسوخ نشده‌اند. با این حال، مراقب تفاوت‌های معنایی با یک آرایه واقعی باشید.

این رابط در [IndexedDB](/en-US/docs/Web/API/IndexedDB_API) و در API {{domxref("Location")}} استفاده می‌شود:

- {{domxref("IDBDatabase.objectStoreNames")}}
- {{domxref("IDBObjectStore.indexNames")}}
- {{domxref("Location.ancestorOrigins")}}

## ویژگی‌های نمونه (Instance properties)

- {{domxref("DOMStringList.length")}} {{ReadOnlyInline}}
  - : طول لیست را برمی‌گرداند.

## روش‌های نمونه (Instance methods)

- {{domxref("DOMStringList.item()")}}
  - : یک رشته از لیست با اندیس داده شده را برمی‌گرداند.
- {{domxref("DOMStringList.contains()")}}
  - : یک مقدار بولی را برمی‌گرداند که نشان می‌دهد آیا رشته داده شده در لیست وجود دارد یا خیر.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}