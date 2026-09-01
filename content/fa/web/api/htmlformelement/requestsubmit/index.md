---
title: "HTMLFormElement: requestSubmit() method"
short-title: requestSubmit()
slug: Web/API/HTMLFormElement/requestSubmit
page-type: web-api-instance-method
browser-compat: api.HTMLFormElement.requestSubmit
---

{{APIRef("HTML DOM")}}

متد **`requestSubmit()`** از {{domxref("HTMLFormElement")}} درخواست می‌کند که فرم با استفاده از یک دکمه ارسال مشخص، ارسال شود.

## Syntax

```js-nolint
requestSubmit()
requestSubmit(submitter)
```

### پارامترها

- `submitter` {{optional_inline}}
  - : یک {{Glossary("submit button")}} که عضوی از فرم است.

    اگر `submitter` ویژگی‌های `form*` را مشخص کند، آن‌ها [رفتار ارسال فرم را لغو می‌کنند](/en-US/docs/Glossary/Submit_button#overriding_the_forms_behavior) (مثلاً `formmethod="POST"`).

    اگر `submitter` دارای ویژگی `name` باشد یا یک `{{HtmlElement('input/image', '&lt;input type="image"&gt;')}}` باشد، داده‌های آن [در ارسال فرم گنجانده می‌شود](/en-US/docs/Glossary/Submit_button#form_data_entries) (مثلاً `btnName=btnValue`).

    اگر پارامتر `submitter` را حذف کنید، خود عنصر فرم به عنوان فرستنده استفاده می‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- {{jsxref("TypeError")}}
  - : اگر `submitter` مشخص‌شده یک {{Glossary("submit button")}} نباشد، پرتاب می‌شود.
- `NotFoundError` {{domxref("DOMException")}}
  - : اگر `submitter` مشخص‌شده عضوی از فرمی نباشد که `requestSubmit()` روی آن فراخوانی شده است، پرتاب می‌شود. فرستنده باید یا از فرزندان عنصر فرم باشد یا ویژگی [`form`](/en-US/docs/Web/HTML/Reference/Elements/input#form) داشته باشد که به آن فرم اشاره کند.

## نکات استفاده

سؤال واضح این است: چرا این متد وجود دارد، در حالی که از قدیم‌الایام متد {{domxref("HTMLFormElement.submit", "submit()")}} را داشته‌ایم؟

پاسخ ساده است. `submit()` فرم را ارسال می‌کند، اما تمام کاری که انجام می‌دهد همین است. از سوی دیگر، `requestSubmit()` طوری عمل می‌کند که گویی یک دکمه ارسال کلیک شده است. محتوای فرم اعتبارسنجی می‌شود و فرم تنها در صورت موفقیت‌آمیز بودن اعتبارسنجی ارسال می‌شود. پس از ارسال فرم، رویداد {{domxref("HTMLFormElement.submit_event", "submit")}} به شیء فرم بازگردانده می‌شود.

## مثال‌ها

در مثال زیر، فرم با تلاش برای ارسال درخواست با استفاده از `requestSubmit()` در صورت موجود بودن، ارسال می‌شود. اگر دکمه ارسالی با شناسه `main-submit` پیدا شود، برای ارسال فرم استفاده می‌شود. در غیر این صورت، فرم بدون پارامتر `submitter` ارسال می‌شود، بنابراین مستقیماً توسط خود فرم ارسال می‌شود.

اگر از طرف دیگر، `requestSubmit()` در دسترس نباشد، این کد به فراخوانی متد {{domxref("HTMLFormElement.submit", "submit()")}} فرم برمی‌گردد.

```js
let myForm = document.querySelector("form");
let submitButton = myForm.querySelector("#main-submit");

if (myForm.requestSubmit) {
  if (submitButton) {
    myForm.requestSubmit(submitButton);
  } else {
    myForm.requestSubmit();
  }
} else {
  myForm.submit();
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}