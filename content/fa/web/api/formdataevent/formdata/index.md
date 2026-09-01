---
title: "FormDataEvent: formData property"
short-title: formData
slug: Web/API/FormDataEvent/formData
page-type: web-api-instance-property
browser-compat: api.FormDataEvent.formData
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی `formData` از رابط {{domxref("FormDataEvent")}}، حاوی شیء {{domxref("FormData")}} است که داده‌های موجود در فرم را هنگام رخ‌دادن رویداد نشان می‌دهد.

## مقدار

یک شیء {{domxref("FormData")}}.

## مثال‌ها

```js
// grab reference to form

const formElem = document.querySelector("form");

// submit handler

formElem.addEventListener("submit", (e) => {
  // on form submission, prevent default
  e.preventDefault();

  // construct a FormData object, which fires the formdata event
  new FormData(formElem);
});

// formdata handler to retrieve data

formElem.addEventListener("formdata", (e) => {
  console.log("formdata fired");

  // Get the form data from the event object
  let data = e.formData;
  for (const value of data.values()) {
    console.log(value);
  }

  // submit the data via XHR
  const request = new XMLHttpRequest();
  request.open("POST", "/formHandler");
  request.send(data);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("XMLHttpRequest")}}
- [استفاده از XMLHttpRequest](/en-US/docs/Web/API/XMLHttpRequest_API/Using_XMLHttpRequest)
- [استفاده از اشیاء FormData](/en-US/docs/Web/API/XMLHttpRequest_API/Using_FormData_Objects)
- {{HTMLElement("Form")}}