---
title: CSSNumericValue
slug: Web/API/CSSNumericValue
page-type: web-api-interface
browser-compat: api.CSSNumericValue
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

رابط **`CSSNumericValue`** در [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API) عملیاتی را نشان می‌دهد که همه مقادیر عددی می‌توانند انجام دهند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

هیچ.

## روش‌های ایستا

- {{domxref('CSSNumericValue/parse_static', 'CSSNumericValue.parse')}}
  - : به شما امکان می‌دهد یک `CSSNumericValue` را مستقیماً از رشته‌ای حاوی CSS بسازید.

## روش‌های نمونه

- {{domxref('CSSNumericValue.add')}}
  - : عدد داده‌شده را به `CSSNumericValue` اضافه می‌کند.
- {{domxref('CSSNumericValue.sub')}}
  - : عدد داده‌شده را از `CSSNumericValue` کم می‌کند.
- {{domxref('CSSNumericValue.mul')}}
  - : `CSSNumericValue` را در مقدار داده‌شده ضرب می‌کند.
- {{domxref('CSSNumericValue.div')}}
  - : `CSSNumericValue` را بر مقدار داده‌شده تقسیم می‌کند.
- {{domxref('CSSNumericValue.min')}}
  - : کمترین مقدار ارسال‌شده را برمی‌گرداند.
- {{domxref('CSSNumericValue.max')}}
  - : بیشترین مقدار ارسال‌شده را برمی‌گرداند.
- {{domxref('CSSNumericValue.equals')}}
  - : اگر همه مقادیر دقیقاً همان نوع و مقدار یکسان و به همان ترتیب باشند، _درست_ است؛ در غیر این صورت _نادرست_.
- {{domxref('CSSNumericValue.to')}}
  - : `value` را به مقدار دیگری با _واحد_ مشخص‌شده تبدیل می‌کند.
- {{domxref('CSSNumericValue.toSum')}}
  - : یک `CSSNumericValue` موجود را به یک شیء {{domxref("CSSMathSum")}} با مقادیری از یک واحد مشخص تبدیل می‌کند.
- {{domxref('CSSNumericValue.type')}}
  - : نوع `CSSNumericValue` را برمی‌گرداند؛ یکی از `angle`، `flex`، `frequency`، `length`، `resolution`، `percent`، `percentHint` یا `time`.

## رابط‌های مبتنی بر CSSNumericValue

- {{domxref('CSSMathClamp')}}
- {{domxref('CSSMathInvert')}}
- {{domxref('CSSMathMax')}}
- {{domxref('CSSMathMin')}}
- {{domxref('CSSMathNegate')}}
- {{domxref('CSSMathProduct')}}
- {{domxref('CSSMathSum')}}
- {{domxref('CSSMathValue')}}
- {{domxref('CSSNumericArray')}}
- {{domxref('CSSUnitValue')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref('CSSImageValue')}}
- {{domxref('CSSKeywordValue')}}
- {{domxref('CSSPositionValue')}}
- {{domxref('CSSTransformValue')}}
- {{domxref('CSSUnparsedValue')}}