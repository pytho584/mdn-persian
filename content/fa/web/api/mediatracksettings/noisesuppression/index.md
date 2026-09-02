---
title: "MediaTrackSettings: noiseSuppression property"
short-title: noiseSuppression
slug: Web/API/MediaTrackSettings/noiseSuppression
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.noiseSuppression_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`noiseSuppression`** در دیکشنری {{domxref("MediaTrackSettings")}} یک مقدار بولی است که فعال یا غیرفعال بودن فناوری حذف نویز را روی یک ترک صوتی نشان می‌دهد. این ویژگی به شما امکان می‌دهد مقداری را که برای منطبق شدن با محدودیت‌های تعیین‌شده برای این ویژگی انتخاب شده است مشاهده کنید؛ همان محدودیت‌هایی که در ویژگی {{domxref("MediaTrackConstraints.noiseSuppression")}} هنگام فراخوانی {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} یا {{domxref("MediaStreamTrack.applyConstraints()")}} مشخص کرده بودید.

حذف نویز به‌طور خودکار صدا را فیلتر می‌کند و نویز پس‌زمینه، وزوز (hum) ناشی از تجهیزات و موارد مشابه را پیش از رساندن صدا به کد شما از آن حذف می‌کند. این ویژگی معمولاً روی میکروفون‌ها استفاده می‌شود، اگرچه از نظر فنی ممکن است منابع ورودی دیگری نیز آن را ارائه کنند.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.noiseSuppression")}} که در نتیجه فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، از پشتیبانی شدن این محدودیت مطلع شوید. البته معمولاً انجام این کار ضروری نیست؛ چرا که مرورگرها هر محدودیتی را که نشناسند نادیده می‌گیرند.

## مقدار

یک مقدار بولی است؛ اگر حذف نویز روی ترک ورودی فعال باشد مقدار آن `true` و اگر حذف نویز غیرفعال باشد مقدار آن `false` است.

## مثال‌ها

برای مشاهده مثال، [Constraint exerciser](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [Capabilities, constraints, and settings](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints.noiseSuppression")}}
- {{domxref("MediaTrackSupportedConstraints")}}