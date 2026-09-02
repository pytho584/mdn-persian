---
title: "MediaTrackConstraints: echoCancellation property"
short-title: echoCancellation
slug: Web/API/MediaTrackConstraints/echoCancellation
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.echoCancellation_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`echoCancellation`** در دیکشنری {{domxref("MediaTrackConstraints")}} یک [`ConstrainBooleanOrDOMString`](/en-US/docs/Web/API/MediaTrackConstraints#constrainbooleanordomstring) است که محدودیت‌های درخواستی یا الزامیِ اعمال‌شده بر مقدار ویژگیِ محدودیت‌پذیر {{domxref("MediaTrackSettings.echoCancellation", "echoCancellation")}} را توصیف می‌کند.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.echoCancellation")}} که از فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} به دست می‌آید، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا نه. اما معمولاً چنین بررسی‌ای ضروری نیست؛ مرورگرها هر محدودیتی را که با آن آشنا نیستند نادیده می‌گیرند.

## مقدار

مقدار می‌تواند یک مقدار بولی، یک رشته، یا یک شیء [`ConstrainBooleanOrDOMString`](/en-US/docs/Web/API/MediaTrackConstraints#constrainbooleanordomstring) باشد.

اگر مرورگر از انواع مشخصی از حذف پژواک پشتیبانی کند، مقدار می‌تواند یکی از موارد زیر باشد:

- `"all"` {{experimental_inline}}
  - : تمام صداهای تولیدشده توسط سیستم کاربر که توسط میکروفون کاربر ضبط می‌شوند، حذف می‌شوند. این حالت برای مثال در شرایطی مفید است که می‌خواهید از ضبط صداهای حساس به حریم خصوصی، مانند خروجیِ صفحه‌خوان یا اعلان‌های سیستم‌عامل، جلوگیری کنید.
- `"remote-only"` {{experimental_inline}}
  - : فقط آن دسته از صداهای تولیدشده توسط سیستم کاربر که از منابع راه دور می‌آیند و توسط میکروفون کاربر ضبط می‌شوند (و به‌صورت {{domxref("MediaStreamTrack")}}هایی که از یک {{domxref("RTCPeerConnection")}} دریافت می‌شوند بازنمایی می‌شوند) حذف می‌شوند. این حالت زمانی مفید است که بخواهید پژواک ارتباط با همتایان راه دور را حذف کنید اما همچنان صدای محلی را به اشتراک بگذارید؛ مانند کلاس موسیقی که در آن معلم می‌خواهد صدای هنرجویان را در حالی که همراه با یک قطعه صوتی می‌نوازند بشنود و در عین حال به‌وضوح با آنان ارتباط برقرار کند.
- `true`
  - : مرورگر تعیین می‌کند چه صداهایی از سیگنال‌های ضبط‌شده توسط میکروفون حذف شوند. باید حداقل به‌اندازه‌ی حالت `remote-only` تلاش خود را برای حذف پژواک انجام دهد و بهتر است به‌اندازه‌ی حالت `all` تلاش کند.
- `false`
  - : هیچ صدایی حذف نمی‌شود؛ هیچ حذف پژواکی انجام نخواهد شد.

اگر مرورگر از انواع مشخصی از حذف پژواک پشتیبانی نکند، مقدار می‌تواند `true` یا `false` باشد.

اگر مقدار به‌صورت یکی از مقادیر بالا تعیین شود، عامل کاربر (user agent) در صورت امکان تلاش می‌کند رسانه را با حذف پژواکِ فعال یا غیرفعال، طبق مقدار تعیین‌شده، به دست آورد؛ اما اگر چنین کاری ممکن نباشد، درخواست با شکست مواجه نمی‌شود.

اگر مقدار به‌صورت یک شیء با فیلد `exact` داده شود، مقدارِ آن فیلد یک تنظیمِ الزامی برای ویژگی حذف پژواک را نشان می‌دهد؛ اگر نتوان آن را برآورده کرد، درخواست منجر به خطا خواهد شد.

## مثال‌ها

برای مثال، [آزمایشگرِ محدودیت](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints")}}
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}