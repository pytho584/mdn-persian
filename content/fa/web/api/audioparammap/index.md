---
title: "AudioParamMap"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioParamMap"
translated_by: "n8n + AI"
---

title: AudioParamMap
slug: Web/API/AudioParamMap
page-type: web-api-interface
browser-compat: api.AudioParamMap

{{APIRef("Web Audio API")}}

رابط **`AudioParamMap`** از [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) یک مجموعه قابل پیمایش و فقط‌خواندنی از چندین پارامتر صوتی را نشان می‌دهد.

یک نمونه `AudioParamMap` یک [شیء شبیه `Map`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map#map-like_browser_apis) فقط‌خواندنی است که در آن هر کلید یک رشته نام برای یک پارامتر است و مقدار متناظر یک {{domxref("AudioParam")}} حاوی مقدار آن پارامتر است.

## ویژگی‌های نمونه

روش‌های زیر برای همه [اشیاء شبیه `Map` فقط‌خواندنی](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map#map-like_browser_apis) در دسترس هستند (لینک‌های زیر به صفحه مرجع شیء سراسری {{jsxref("Map")}} اشاره دارند).

- {{jsxref("Map/size", "size")}}
  - : تعداد ورودی‌های موجود در نقشه را برمی‌گرداند.

## روش‌های نمونه

روش‌های زیر برای همه [اشیاء شبیه `Map` فقط‌خواندنی](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map#map-like_browser_apis) در دسترس هستند (لینک‌های زیر به صفحه مرجع شیء سراسری {{jsxref("Map")}} اشاره دارند).

- {{jsxref("Map/entries", "entries()")}}
  - : یک [شیء پیمایشگر](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Iterator) جدید برمی‌گرداند که ورودی‌ها را به صورت جفت‌های `[key, value]` در نقشه به ترتیب درج بازمی‌گرداند.
- {{jsxref("Map/forEach", "forEach()")}}
  - : یک {{glossary("callback function")}} ارائه‌شده را یک بار برای هر مقدار و کلید موجود در نقشه، به ترتیب درج، فراخوانی می‌کند.
- {{jsxref("Map/get", "get()")}}
  - : مقدار {{domxref("AudioParam")}} مرتبط با کلید رشته را برمی‌گرداند، یا اگر وجود نداشته باشد `undefined` را برمی‌گرداند.
- {{jsxref("Map/has", "has()")}}
  - : یک [بولی](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean) را برمی‌گرداند که نشان می‌دهد آیا یک کلید در نقشه وجود دارد یا خیر.
- {{jsxref("Map/keys", "keys()")}}
  - : یک شیء پیمایشگر جدید برمی‌گرداند که کلیدهای رشته را در نقشه به ترتیب درج بازمی‌گرداند.
- {{jsxref("Map/values", "values()")}}
  - : یک شیء پیمایشگر جدید برمی‌گرداند که مقادیر {{domxref("AudioParam")}} را در نقشه به ترتیب درج بازمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}