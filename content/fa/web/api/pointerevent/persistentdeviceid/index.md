---
title: "PointerEvent: persistentDeviceId property"
short-title: persistentDeviceId
slug: Web/API/PointerEvent/persistentDeviceId
page-type: web-api-instance-property
browser-compat: api.PointerEvent.persistentDeviceId
---

{{ APIRef("Pointer Events") }}

ویژگی فقط‌خواندنی **`persistentDeviceId`** در رابط {{domxref("PointerEvent")}} یک شناسهٔ یکتا برای دستگاه اشاره‌گری است که رویداد `PointerEvent` را تولید می‌کند. این ویژگی راهی امن و قابل‌اعتماد برای شناسایی چند دستگاه اشاره‌گر (مانند قلم‌ها) که به‌طور هم‌زمان با صفحه در تعامل هستند فراهم می‌کند.

یک `persistentDeviceId` در طول عمر یک نشست مرورگر پایدار می‌ماند. برای جلوگیری از خطر اثرانگشت/ردیابی، در آغاز هر نشست یک `persistentDeviceId` جدید به دستگاه‌های اشاره‌گر اختصاص داده می‌شود.

رویدادهای اشاره‌گری که دستگاه تولیدکنندهٔ آن‌ها قابل شناسایی نباشد، مقدار `persistentDeviceId` برابر با `0` به آن‌ها اختصاص داده می‌شود.

## مقدار

یک عدد صحیح، یا اگر دستگاه تولیدکنندهٔ `PointerEvent` قابل شناسایی نباشد، مقدار `0`.

> [!NOTE]
> به دلیل محدودیت‌های سخت‌افزاری دیجیتایزر و دستگاه اشاره‌گر، ممکن است `persistentDeviceId` برای همهٔ رویدادهای اشاره‌گر در دسترس نباشد، به‌ویژه با سخت‌افزارهای قدیمی‌تر. برای مثال، ممکن است دستگاه اشاره‌گر شناسهٔ سخت‌افزاری خود را به‌موقع به دیجیتایزر گزارش ندهد و در نتیجه `persistentDeviceId` رویداد `pointerdown` در ابتدا `0` باشد و برای رویدادهای بعدی در همان stroke به مقدار معتبری تغییر کند.

## مثال‌ها

### اختصاص رنگ به هر persistentDeviceId

فرض کنید HTML زیر را داریم:

```html
<canvas id="inking-surface" width="1280" height="720"></canvas>
```

جاوااسکریپت زیر یک رنگ جوهر متفاوت به حداکثر سه اشاره‌گر یکتا که با یک canvas در تعامل هستند اختصاص می‌دهد:

```js
const colorBlue = 0;
const colorGreen = 1;
const colorYellow = 2;
const colors = [colorBlue, colorGreen, colorYellow];

const pointerToColorMap = new Map();
let colorAssignmentIndex = 0;

const canvas = document.querySelector("#inking-surface");

// Listen for a pointerdown event and map the persistentDeviceId to a color
// if it exists and has not been mapped yet
canvas.addEventListener("pointerdown", (e) => {
  if (e.persistentDeviceId && !pointerToColorMap.has(e.persistentDeviceId)) {
    pointerToColorMap.set(e.persistentDeviceId, colors[colorAssignmentIndex]);

    // Bump the color assignment index and loop back over if needed
    colorAssignmentIndex = (colorAssignmentIndex + 1) % colors.length;
  }
});

// Listen for a `pointermove` and get the color assigned to this pointer
// if persistentDeviceId exists and the pointer has been color mapped
canvas.addEventListener("pointermove", (e) => {
  if (e.persistentDeviceId && pointerToColorMap.has(e.persistentDeviceId)) {
    const pointerColor = pointerToColorMap.get(e.persistentDeviceId);
    // Do some inking on the <canvas>
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}