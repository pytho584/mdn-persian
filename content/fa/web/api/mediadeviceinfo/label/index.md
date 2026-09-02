---
title: "MediaDeviceInfo: label property"
short-title: label
slug: Web/API/MediaDeviceInfo/label
page-type: web-api-instance-property
browser-compat: api.MediaDeviceInfo.label
---

{{APIRef("Media Capture and Streams")}}{{securecontext_header}}

خاصیت فقط خواندنی **`label`** از رابط {{domxref("MediaDeviceInfo")}} یک رشته را برمی‌گرداند که این دستگاه را توصیف می‌کند (مثلاً «وبکم USB خارجی»).

این ویژگی فقط در زمان استفاده فعال از `MediaStream` یا زمانی که مجوزهای دائمی اعطا شده باشند، در دسترس است.

## مقدار

یک رشته که دستگاه رسانه را توصیف می‌کند. به دلایل امنیتی، اگر کاربر مجوز استفاده از حداقل یک دستگاه رسانه را به دست نیاورده باشد، چه با شروع یک جریان از میکروفون یا دوربین، چه با اعطای مجوزهای دائمی، `label` همیشه یک رشته خالی (`""`) است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}