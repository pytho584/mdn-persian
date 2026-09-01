---
title: "HTMLMediaElement: videoTracks property"
short-title: videoTracks
slug: Web/API/HTMLMediaElement/videoTracks
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.videoTracks
---

{{APIRef("HTML DOM")}}

ویژگیِ فقط‌خواندنیِ **`videoTracks`** در اشیاء {{DOMxRef("HTMLMediaElement")}} یک شیء {{DOMxRef("VideoTrackList")}} برمی‌گرداند که همهٔ اشیاء {{DOMxRef("VideoTrack")}} نمایانگرِ ردهای ویدیوییِ عنصر رسانه را فهرست می‌کند.

لیست بازگشت‌داده‌شده _زنده_ است؛ یعنی هر زمان که ردی به عنصر رسانه اضافه یا از آن حذف شود، محتوای لیست به‌صورت پویا تغییر می‌کند. وقتی ارجاعی به لیست داشته باشید، می‌توانید آن را برای تغییرات زیر نظر بگیرید تا متوجه اضافه‌شدن ردهای ویدیویی جدید یا حذف ردهای موجود شوید. برای آشنایی بیشتر با نظارت بر تغییرات فهرست ردیِ یک عنصر رسانه، به [رویدادهای VideoTrackList](/en-US/docs/Web/API/VideoTrackList#events) مراجعه کنید.

## مقدار

یک شیء {{DOMxRef("VideoTrackList")}} که فهرست ردهای ویدیویی موجود در عنصر رسانه را نمایش می‌دهد. می‌توانید از طریق نمادِ آرایه یا با استفاده از متد {{domxref("VideoTrackList.getTrackById", "getTrackById()")}} به فهرست ردها دسترسی پیدا کنید.

هر ردی با یک شیء {{DOMxRef("VideoTrack")}} نمایش داده می‌شود که اطلاعاتی دربارهٔ آن ردی ارائه می‌دهد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLMediaElement")}}: رابطی که برای تعریف ویژگیِ `HTMLMediaElement.videoTracks` استفاده می‌شود
- {{HTMLElement("video")}}
- {{DOMxRef("VideoTrack")}}، {{DOMxRef("VideoTrackList")}}