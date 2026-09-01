---
title: "Document: browsingTopics() method"
short-title: browsingTopics()
slug: Web/API/Document/browsingTopics
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.Document.browsingTopics
---

{{APIRef("Topics API")}}{{non-standard_header}}{{deprecated_header}}

> [!WARNING]
> این ویژگی در حال حاضر مورد مخالفت دو فروشنده‌ی مرورگر قرار گرفته است. برای جزئیات این مخالفت‌ها، به بخش [مواضع استانداردها](/en-US/docs/Web/API/Topics_API#standards_positions) در پایین مراجعه کنید.

> [!NOTE]
> برای استفاده از این ویژگی در برنامه‌های خود، یک [فرایند ثبت‌نام](/en-US/docs/Web/Privacy/Guides/Privacy_sandbox#enrollment) الزامی است.

متد `browsingTopics()` از رابط {{domxref("Document")}} یک {{jsxref("Promise")}} برمی‌گرداند که با آرایه‌ای از اشیاء نمایانگر موضوعات برتر برای کاربر، یکی از هر یک از سه دوره‌ی زمانی اخیر، تکمیل می‌شود. این موضوعات سپس می‌توانند در یک درخواست fetch بعدی به پلتفرم فناوری تبلیغات بازگردانده شوند. به‌طور پیش‌فرض، این متد همچنین باعث می‌شود که مرورگر بازدید فعلی صفحه را به‌عنوان مشاهده‌شده توسط فراخواننده ثبت کند، تا نام میزبان صفحه بعداً در محاسبه‌ی موضوعات قابل استفاده باشد.

> [!NOTE]
> برخلاف سایر ویژگی‌های فعال‌کننده‌ی Topics API، متد `browsingTopics()` برای ارسال موضوعات و علامت‌گذاری موضوعات به‌عنوان مشاهده‌شده، به هدرهای HTTP وابسته نیست، اما عملکرد آن تا حدودی کمتر است. توصیه می‌شود از یکی از ویژگی‌های مبتنی بر هدر HTTP استفاده کنید و تنها در شرایطی که امکان تغییر هدرها وجود ندارد به `browsingTopics()` بازگشت کنید.

## نحو

```js-nolint
browsingTopics()
browsingTopics(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء گزینه‌ها که می‌تواند حاوی ویژگی‌های زیر باشد:
    - `skipObservation`
      - : یک مقدار بولی که اگر روی `true` تنظیم شود، باعث می‌شود مرورگر هنگام فراخوانی `browsingTopics()` موضوعات را _مشاهده نکند_. مقدار پیش‌فرض `false` است که باعث مشاهده‌ی موضوعات می‌شود.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با آرایه‌ای از حداکثر سه شیء نمایانگر موضوعات انتخاب‌شده‌ی کاربر فعلی برای سه دوره‌ی زمانی اخیر تکمیل می‌شود. هر شیء دارای ویژگی‌های زیر است:

- `configVersion`
  - : رشته‌ای که الگوریتم (به‌جز بخش مدل) مورد استفاده برای محاسبه‌ی موضوع را شناسایی می‌کند.
- `modelVersion`
  - : رشته‌ای نمایانگر مدلی است که برای طبقه‌بندی یک رشته (مانند نام میزبان یک صفحه‌ی وب) به شناسه‌های موضوع استفاده می‌شود.
- `taxonomyVersion`
  - : رشته‌ای نمایانگر نسخه‌ی طبقه‌بندی (taxonomy) مورد استفاده است.
- `topic`
  - : عددی نمایش‌دهنده‌ی شناسه‌ی موضوع است که مرورگر می‌تواند از آن برای بازیابی موضوع از طبقه‌بندی استفاده کند (نمونه‌ای از [طبقه‌بندی علایق](https://github.com/patcg-individual-drafts/topics/blob/main/taxonomy_v1.md) را ببینید).
- `version`
  - : مقادیر `configVersion`، `modelVersion` و `taxonomyVersion` که با دو نقطه (`:`) بین هر کدام به هم متصل شده‌اند.

مقادیر دقیق ویژگی‌ها ممکن است بسته به پیاده‌سازی مرورگر متفاوت باشد. یک شیء نمونه از Chrome ممکن است به شکل زیر باشد:

```json
{
  "configVersion": "chrome.1",
  "modelVersion": "1",
  "taxonomyVersion": "1",
  "topic": 43,
  "version": "chrome.1:1:1"
}
```

### استثناها

- `NotAllowedError` {{domxref("DOMException")}}
  - : در صورت بروز هر یک از موارد زیر ایجاد می‌شود:
    - استفاده از [Topics API](/en-US/docs/Web/API/Topics_API) توسط یک [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) با هدر {{httpheader('Permissions-Policy/browsing-topics','browsing-topics')}} ممنوع شده باشد.
    - سایت فراخواننده، Topics API را در یک [فرایند ثبت‌نام sandbox حریم خصوصی](/en-US/docs/Web/Privacy/Guides/Privacy_sandbox#enrollment) موفق شامل نشده باشد.

## مثال‌ها

```js
// Get an array of top topics for this user
const topics = await document.browsingTopics();

// Request an ad creative
const response = await fetch("https://ads.example/get-creative", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify(topics),
});

// Get the JSON from the response
const creative = await response.json();

// Display ad
```

## مشخصات

این ویژگی بخشی از یک استاندارد رسمی نیست، اگرچه در [پیش‌نویس پیشنهاد غیررسمی Topics API](https://patcg-individual-drafts.github.io/topics/) مشخص شده است.

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Topics API](/en-US/docs/Web/API/Topics_API)