---
title: "ConstantSourceNode: offset property"
short-title: offset
slug: Web/API/ConstantSourceNode/offset
page-type: web-api-instance-property
browser-compat: api.ConstantSourceNode.offset
---

{{ APIRef("Web Audio API") }}

ویژگیِ فقط‌خواندنیِ `offset` در رابط {{ domxref("ConstantSourceNode") }} یک شیء {{domxref("AudioParam}} را برمی‌گرداند که مقدار عددیِ [a-rate](/en-US/docs/Web/API/AudioParam#a-rate) را نشان می‌دهد که منبع صدا هنگام درخواست نمونهٔ بعدی، همیشه آن را برمی‌گرداند.

> [!NOTE]
> اگرچه `AudioParam` با نام `offset` فقط‌خواندنی است، اما
> ویژگیِ `value` درونِ آن این‌گونه نیست. بنابراین می‌توانید مقدارِ
> `offset` را با تنظیم کردنِ مقدارِ
> `ConstantSourceNode.offset.value` تغییر دهید:
>
> ```js
> myConstantSourceNode.offset.value = newValue;
> ```

## مقدار

یک شیء {{ domxref("AudioParam") }} که مقدارِ [a-rate](/en-US/docs/Web/API/AudioParam#a-rate) بازگردانده‌شده برای هر نمونه توسط این گره را نشان می‌دهد. مقدار پیش‌فرض 1.0 است.

برای دسترسی به مقدارِ فعلی پارامترِ `offset`، به ویژگیِ `value` آن پارامتر دسترسی پیدا کنید، همان‌طور که در کادرِ نحو در بالا نشان داده شده است.

## مثال‌ها

این مثال نشان می‌دهد که چگونه یک `ConstantSourceNode` را طوری تنظیم کنیم که `offset` آن به عنوان ورودیِ یک جفت {{domxref("GainNode")}} استفاده شود؛ این قطعه‌کد از مثالِ کاملی که در [کنترل چند پارامتر با ConstantSourceNode](/en-US/docs/Web/API/Web_Audio_API/Controlling_multiple_parameters_with_ConstantSourceNode) می‌یابید، گرفته شده است.

```js
gainNode2 = context.createGain();
gainNode3 = context.createGain();
gainNode2.gain.value = gainNode3.gain.value = 0.5;

volumeSliderControl.value = gainNode2.gain.value;

constantSource = context.createConstantSource();
constantSource.connect(gainNode2.gain);
constantSource.connect(gainNode3.gain);
```

ابتدا، گره‌های بهره (gain) ساخته و پیکربندی می‌شوند و مقدار یک کنترلِ لغزنده به‌گونه‌ای تنظیم می‌شود که با بهرهٔ دو گره مطابقت داشته باشد. سپس یک {{domxref("ConstantSourceNode")}} جدید می‌سازیم و آن را به‌عنوان منبع برای مقادیرِ {{domxref("GainNode.gain")}} دو گرهٔ بهره قرار می‌دهیم. هر یک از آن مقادیر نیز یک {{domxref("AudioParam")}} هستند.

فرض کنید یک کنترل‌کنندهٔ رویداد داریم (در این مورد، برای رویدادهای {{domxref("Element/click_event", "click")}}) که باید با تغییر دادنِ مقدارِ دو گرهٔ بهره پاسخ دهد. با اتصالی که در بالا برقرار شد، این کار را می‌توان با این کنترل‌کنندهٔ رویدادِ ساده انجام داد:

```js
function handleClickEvent(event) {
  constantSource.offset.value = volumeSliderControl.value;
}
```

تنها کاری که این تابع باید انجام دهد این است که مقدارِ فعلیِ کنترلِ لغزنده‌ای را که برای کنترلِ بهرهٔ گره‌های جفت‌شده استفاده می‌کنیم، دریافت کند و سپس آن مقدار را در پارامترِ `offset` گرهٔ `ConstantSourceNode` ذخیره کند. این کار با تغییر دادنِ محتویاتِ ویژگیِ {{domxref("AudioParam.value")}} آن انجام می‌شود. دو گرهٔ بهره به‌سرعت سطح صدای جدید را اعمال می‌کنند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- {{domxref("ConstantSourceNode")}}
- {{domxref("AudioNode")}}
- {{domxref("AudioParam")}}