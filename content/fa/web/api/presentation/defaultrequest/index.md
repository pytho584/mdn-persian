---
title: "Presentation: defaultRequest property"
---

---
title: "Presentation: defaultRequest property"
short-title: defaultRequest
slug: Web/API/Presentation/defaultRequest
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Presentation.defaultRequest
---

{{APIRef("Presentation API")}}{{SeeCompatTable}}{{SecureContext_Header}}

در یک [عامل کاربرِ کنترل‌کننده](https://www.w3.org/TR/presentation-api/#dfn-controlling-user-agent)، ویژگی **`defaultRequest`** _باید_ در صورت وجود، [درخواستِ ارائهٔ پیش‌فرض](https://www.w3.org/TR/presentation-api/#dfn-default-presentation-request) را بازگرداند و در غیر این صورت، `null` را برگرداند. در یک [زمینهٔ مرورِ دریافت‌کننده](https://www.w3.org/TR/presentation-api/#dfn-receiving-browsing-context)، این ویژگی _باید_ `null` برگرداند.

اگر مقداردهی اولیه توسط [کنترل‌کننده](https://www.w3.org/TR/presentation-api/#dfn-controller) انجام شده باشد، [عامل کاربرِ کنترل‌کننده](https://www.w3.org/TR/presentation-api/#dfn-controlling-user-agent) _بایستی_ از مقدار ویژگی `defaultRequest` به‌عنوان _درخواستِ ارائهٔ پیش‌فرض_ برای آن [زمینهٔ مرورِ کنترل‌کننده](https://www.w3.org/TR/presentation-api/#dfn-controlling-browsing-context) استفاده کند. اگر [مجموعهٔ پرچم‌های شن‌باکسِ فعال](https://www.w3.org/TR/presentation-api/#dfn-active-sandboxing-flag-set) شیء سند شامل [پرچمِ زمینهٔ مرورِ شن‌باکس‌شده برای ارائه](https://www.w3.org/TR/presentation-api/#sandboxed-presentation-browsing-context-flag) باشد، [عامل کاربرِ کنترل‌کننده](https://www.w3.org/TR/presentation-api/#dfn-controlling-user-agent) _بایستی_ طوری رفتار کند که گویی درخواستِ پیش‌فرض برای آن زمینهٔ مرور تنظیم نشده است. هرگاه [عامل کاربرِ کنترل‌کننده](https://www.w3.org/TR/presentation-api/#dfn-controlling-user-agent) بخواهد به نمایندگی از آن زمینهٔ مرور یک {{DOMxRef("PresentationConnection")}} را آغاز کند، _باید_ با استفاده از [درخواستِ ارائهٔ پیش‌فرض](https://www.w3.org/TR/presentation-api/#dfn-default-presentation-request) برای [کنترل‌کننده](https://www.w3.org/TR/presentation-api/#dfn-controller) اقدام به [شروع یک ارائه](https://www.w3.org/TR/presentation-api/#dfn-start-a-presentation) کند (درست مانند این است که کنترل‌کننده متد {{DOMxRef("PresentationRequest.start","defaultRequest.start()")}} را فراخوانده باشد).

[عامل کاربرِ کنترل‌کننده](https://www.w3.org/TR/presentation-api/#dfn-controlling-user-agent) _بایستی_ تنها در صورتی ارائه را با استفاده از [درخواستِ ارائهٔ پیش‌فرض](https://www.w3.org/TR/presentation-api/#dfn-default-presentation-request) شروع کند که کاربر با یک ژست کاربری قصد خود را ابراز کرده باشد؛ برای نمونه با کلیک کردن روی دکمه‌ای در مرورگر.

> [!NOTE]
> برخی از [عامل‌های کاربرِ کنترل‌کننده](https://www.w3.org/TR/presentation-api/#dfn-controlling-user-agent) ممکن است به کاربر اجازه دهند با همان ژست کاربری، یک [اتصالِ ارائهٔ پیش‌فرض](https://www.w3.org/TR/presentation-api/#dfn-presentation-connection) را آغاز کند و یک [نمایشگرِ ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-display) را نیز انتخاب کند. برای مثال، رابطِ مرورگر (browser chrome) ممکن است به کاربر اجازه دهد نمایشگری را از یک فهرست انتخاب کند، یا روی نمایشگری که از [ارتباطات میدان‌نزدیک (NFC)](https://nfc-forum.org/) پشتیبانی می‌کند ضربه بزند. در این حالت، وقتی [عامل کاربرِ کنترل‌کننده](https://www.w3.org/TR/presentation-api/#dfn-controlling-user-agent) هنگام [شروعِ یک ارائه](https://www.w3.org/TR/presentation-api/#dfn-start-a-presentation) درخواستِ اجازه می‌کند، مرورگر می‌تواند آن نمایشگر را به‌عنوان گزینهٔ پیش‌فرض پیشنهاد دهد، یا ژست کاربر را به منزلهٔ اعطای مجوز برای آن نمایشگر در نظر بگیرد و انتخابِ نمایشگر را به‌کلی حذف کند.

> [!NOTE]
> اگر [عامل کاربرِ کنترل‌کننده](https://www.w3.org/TR/presentation-api/#dfn-controlling-user-agent) از آغازِ [اتصالِ ارائه](https://www.w3.org/TR/presentation-api/#dfn-presentation-connection) از طریق رابطِ مرورگر پشتیبانی نکند، تنظیم `defaultRequest` هیچ تأثیری نخواهد داشت.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}