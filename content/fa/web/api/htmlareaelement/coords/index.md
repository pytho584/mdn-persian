---
title: "HTMLAreaElement: coords property"
short-title: coords
slug: Web/API/HTMLAreaElement/coords
page-type: web-api-instance-property
browser-compat: api.HTMLAreaElement.coords
---

{{APIRef("HTML DOM")}}

ویژگی **`coords`** در رابط {{DOMxRef("HTMLAreaElement")}} مختصات شکل عنصر را بهصورت فهرستی از اعداد اعشاری مشخص میکند. این ویژگی بازتابی از ویژگی [`coords`](/en-US/docs/Web/HTML/Reference/Elements/area#coords) عنصر {{htmlelement("area")}} است.

اگر `shape` برابر با `rect` باشد، شکل یک مستطیل است و چهار عدد جداشده با کاما در مقدار رشته، مختصات گوشهٔ بالا-چپ و پایین-راست مستطیل را مشخص میکنند. برای مثال، `0,0,200,20` مختصات را بهصورت `0,0` (گوشهٔ بالا-چپ نقشهٔ تصویری) و `200,20` (۲۰۰ پیکسل از چپ و ۲۰ پیکسل از بالای گوشهٔ بالا-چپ نقشهٔ تصویری) تعریف میکند.

اگر `shape` برابر با `circle` باشد، سه عدد جداشده با کاما، مختصات x و y مرکز دایره و شعاع آن را نشان میدهند.

اگر شکل `poly` باشد، رشته شامل حداقل ۶ عدد جداشده با کاما است که حداقل ۳ جفت مختصات را نشان میدهند و رئوس چندضلعی را تعریف میکنند.

برای همهٔ مختصات، مبدأ، گوشهٔ بالا-چپ تصویر عنصر {{htmlelement("map")}} است.

## مقدار

یک رشته؛ شامل یک سری اعداد جدا شده با کاما.

## مثال‌ها

```js
const areaElement = document.getElementById("circleArea");
console.log(areaElement.coords);
areaElement.coords = "25,25,25";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{DOMXref("HTMLAreaElement.shape")}}
- {{DOMXref("HTMLAreaElement.alt")}}
- {{DOMXref("HTMLMapElement")}}
- {{HTMLElement("area")}}
- {{HTMLElement("map")}}
- {{HTMLElement("a")}}