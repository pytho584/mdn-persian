---
title: "HTMLFormElement: formdata event"
short-title: formdata
slug: Web/API/HTMLFormElement/formdata_event
page-type: web-api-event
browser-compat: api.HTMLFormElement.formdata_event
---

{{APIRef("HTML DOM")}}

رویداد **`formdata`** پس از ساختهشدن فهرست ورودیهایی که دادههای فرم را نشان میدهند، فعال میشود. این اتفاق هنگام ارسال فرم رخ میدهد، اما میتواند با فراخوانی سازندهی {{domxref("FormData.FormData", "FormData()")}} نیز ایجاد شود.

این رویداد قابل لغو (cancelable) نیست و حبابزدگی (bubble) ندارد.

## نحو (Syntax)

برای استفاده از نام رویداد در روشهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا تنظیم خاصیت رویدادگردان (event handler property) میتوانید از آن استفاده کنید.

```js-nolint
addEventListener("formdata", (event) => { })

onformdata = (event) => { }
```

## نوع رویداد

یک {{domxref("FormDataEvent")}} که از {{domxref("Event")}} به ارث میرسد.

{{InheritanceDiagram("FormDataEvent")}}

## مثالها

```js
// grab reference to form

const formElem = document.querySelector("form");

// submit handler

formElem.addEventListener("submit", (e) => {
  // on form submission, prevent default
  e.preventDefault();

  console.log(formElem.querySelector('input[name="field1"]')); // FOO
  console.log(formElem.querySelector('input[name="field2"]')); // BAR

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
  // formdata gets modified by the formdata event
  formData.set("field1", formData.get("field1").toLowerCase());
  formData.set("field2", formData.get("field2").toLowerCase());
});
```

نسخهی `onformdata` به این شکل خواهد بود:

```js
formElem.onformdata = (e) => {
  console.log("formdata fired");

  // modifies the form data
  const formData = e.formData;
  formData.set("field1", formData.get("field1").toLowerCase());
  formData.set("field2", formData.get("field2").toLowerCase());
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML {{htmlElement("form")}}
- {{domxref("FormDataEvent")}}