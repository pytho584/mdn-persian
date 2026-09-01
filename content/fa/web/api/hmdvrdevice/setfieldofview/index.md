---
title: "HMDVRDevice: setFieldOfView() method"
short-title: setFieldOfView()
slug: Web/API/HMDVRDevice/setFieldOfView
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.HMDVRDevice.setFieldOfView
---

{{deprecated_header}}{{APIRef("WebVR API")}}{{Non-standard_header}}

متد **`setFieldOfView()`** در رابط {{domxref("HMDVRDevice")}} برای تنظیم میدان دید برای یک چشم یا هر دو چشم به‌طور همزمان به کار می‌رود.

## سینتکس

```js-nolint
setFieldOfView(leftFOV, rightFOV, zNear, zFar)
```

### پارامترها

- `leftFOV` {{optional_inline}}
  - : یک شیء {{domxref("VRFieldOfView")}} که میدان دید جدید را برای چشم چپ تعریف می‌کند. اگر مشخص نشود، میدان دید چشم چپ تغییری نخواهد کرد.
- `rightFOV` {{optional_inline}}
  - : یک شیء {{domxref("VRFieldOfView")}} که میدان دید جدید را برای چشم راست تعریف می‌کند. اگر مشخص نشود، میدان دید چشم راست تغییری نخواهد کرد.
- `zNear` {{optional_inline}}
  - : فاصله از چشم‌ها تا نزدیک‌ترین نقطهٔ دید. اشیا می‌توانند تا این فاصله نزدیک شوند و همچنان در دید قرار بگیرند. اگر مشخص نشود، مقدار پیش‌فرض استفاده می‌شود — `0.01`.
- `zFar` {{optional_inline}}
  - : فاصله از چشم‌ها تا دورترین نقطهٔ دید. اشیا می‌توانند تا این فاصله دور شوند و همچنان در دید قرار بگیرند. اگر مشخص نشود، مقدار پیش‌فرض استفاده می‌شود — `10000.0`.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

مثال سادهٔ زیر تابعی را نشان می‌دهد که می‌توان از آن برای تنظیم یک میدان دید سفارشی با چهار مقدار درجهٔ مشخص برای بالا، راست، پایین و چپ استفاده کرد. سازندهٔ `VRFieldOfView()` برای ایجاد یک شیء {{domxref("VRFieldOfView")}} از مقادیر ارائه‌شده استفاده می‌شود و سپس این شیء به متد `setFieldOfView()` داده می‌شود (در این حالت همیشه از مقادیر پیش‌فرض `zNear` و `zFar` استفاده می‌شود).

```js
function setCustomFOV(up, right, down, left) {
  const testFOV = new VRFieldOfView(up, right, down, left);

  gHMD.setFieldOfView(testFOV, testFOV, 0.01, 10000.0);

  const lEye = gHMD.getEyeParameters("left");
  const rEye = gHMD.getEyeParameters("right");
  console.log(lEye.currentFieldOfView);
  console.log(rEye.currentFieldOfView);
}
```

> [!NOTE]
> هنگام آزمایش، تنظیم یک میدان دید غیرعادی/بسیار کوچک می‌تواند دید شما را به‌هم بریزد. بهتر است ابتدا میدان دید فعلی را (با استفاده از {{domxref("VREyeParameters.fieldOfView")}}) بگیرید و سپس تغییرات اساسی اعمال کنید تا در صورت نیاز بتوانید بعداً آن را بازنشانی کنید.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebVR API](/en-US/docs/Web/API/WebVR_API)