---
title: "FormDataEvent"
---

---
title: FormDataEvent
slug: Web/API/FormDataEvent
page-type: web-api-interface
browser-compat: api.FormDataEvent
---

{{APIRef("DOM")}}

رابطهٔ **`FormDataEvent`** نمایانگر رویداد [`formdata`](/en-US/docs/Web/API/HTMLFormElement/formdata_event) است — چنین رویدادی پس از ساخته‌شدن فهرست آیتم‌های نمایانگر داده‌های فرم، بر روی یک شیء {{domxref("HTMLFormElement")}} شلیک می‌شود. این اتفاق هنگام ارسال فرم رخ می‌دهد، اما می‌تواند با فراخوانی سازندهٔ {{domxref("FormData.FormData", "FormData()")}} نیز ایجاد شود.

این امکان به شما می‌دهد که در پاسخ به شلیک رویداد `formdata`، به‌سرعت یک شیء {{domxref("FormData")}} به‌دست آورید، به‌جای اینکه هنگام ارسال داده‌های فرم با روشی مانند {{domxref("Window/fetch", "fetch()")}} مجبور باشید خودتان آن را بسازید (به [استفاده از اشیاء FormData](/en-US/docs/Web/API/XMLHttpRequest_API/Using_FormData_Objects) مراجعه کنید).

{{InheritanceDiagram}}

## سازنده

- {{domxref("FormDataEvent.FormDataEvent","FormDataEvent()")}}
  - : یک نمونهٔ جدید از شیء `FormDataEvent` می‌سازد.

## ویژگی‌های نمونه

_ویژگی‌های رابطهٔ والد خود، {{domxref("Event")}} را به ارث می‌برد._

- {{domxref("FormDataEvent.formData")}}
  - : شامل شیء {{domxref("FormData")}} است که داده‌های موجود در فرم را هنگام شلیک رویداد نمایان می‌کند.

## متدهای نمونه

_متدهای رابطهٔ والد خود، {{domxref("Event")}} را به ارث می‌برد._

## مثال‌ها

```js
// grab reference to form

const formElem = document.querySelector("form");

// submit handler

formElem.addEventListener("submit", (e) => {
  // on form submission, prevent default
  e.preventDefault();

  console.log(form.querySelector('input[name="field1"]')); // FOO
  console.log(form.querySelector('input[name="field2"]')); // BAR

  // construct a FormData object, which fires the formdata event
  const formData = new FormData(formElem);
  // formdata gets modified by the formdata event
  console.log(formData.get("field1")); // foo
  console.log(formData.get("field2")); // bar
});

// formdata handler to retrieve data

formElem.addEventListener("formdata", (e) => {
  console.log("formdata fired");

  // modifies the form data
  const formData = e.formData;
  formData.set("field1", formData.get("field1").toLowerCase());
  formData.set("field2", formData.get("field2").toLowerCase());
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Window/fetch", "fetch()")}}
- {{domxref("FormData")}}
- [استفاده از اشیاء FormData](/en-US/docs/Web/API/XMLHttpRequest_API/Using_FormData_Objects)
- {{HTMLElement("Form")}}