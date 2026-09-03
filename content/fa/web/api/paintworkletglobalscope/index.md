---
title: PaintWorkletGlobalScope
slug: Web/API/PaintWorkletGlobalScope
page-type: web-api-interface
status:
  - experimental
browser-compat: api.PaintWorkletGlobalScope
---

{{APIRef("CSS Painting API")}}{{SeeCompatTable}}

رابطهٔ **`PaintWorkletGlobalScope`** در [CSS Painting API](/en-US/docs/Web/API/CSS_Painting_API) نمایانگر شیء سراسری موجود در داخل یک {{domxref("Worklet")}} نقاشی است.

## نگرانی‌های حریم خصوصی

برای جلوگیری از درز اطلاعات لینک‌های بازدیدشده، این قابلیت در مرورگرهای مبتنی بر Chrome برای عناصر {{HTMLElement("a")}} دارای ویژگی `href` و همچنین عناصر فرزند آن‌ها در حال حاضر غیرفعال است. برای جزئیات بیشتر، به موارد زیر مراجعه کنید:

- بخش [ملاحظات حریم خصوصی](https://drafts.css-houdini.org/css-paint-api/#privacy-considerations) در مشخصات CSS Painting API
- بحث مربوط به مشخصات CSS Painting API با عنوان [«CSS Paint API سابقهٔ مرور را درز می‌دهد»](https://github.com/w3c/css-houdini-drafts/issues/791)

## ویژگی‌های نمونه

_این رابط ویژگی‌ها را از {{domxref('WorkletGlobalScope')}} به ارث می‌برد._

- {{domxref('PaintWorkletGlobalScope.devicePixelRatio')}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : نسبت پیکسل‌های فیزیکی به پیکسل‌های منطقی دستگاه فعلی را برمی‌گرداند.

## روش‌های نمونه

_این رابط روش‌ها را از {{domxref('WorkletGlobalScope')}} به ارث می‌برد._

- {{domxref('PaintWorkletGlobalScope.registerPaint()')}} {{Experimental_Inline}}
  - : یک کلاس را ثبت می‌کند تا به صورت برنامه‌نویسی‌شده تصویری تولید کند که در جایی که یک ویژگی CSS انتظار یک فایل را دارد استفاده شود.

## مثال‌ها

سه مثال زیر در کنار هم نشان می‌دهند که چگونه یک `Worklet` نقاشی ساخته، بارگذاری و استفاده می‌شود.

### ایجاد یک paint worklet

در زیر یک نمونه ماژول worklet نشان داده شده است. این کد باید در یک فایل جاوااسکریپت جداگانه قرار گیرد. توجه کنید که `registerPaint()` بدون ارجاع به یک paint `Worklet` فراخوانی می‌شود.

```js
class CheckerboardPainter {
  paint(ctx, geom, properties) {
    // شیء سراسری در اینجا یک PaintWorkletGlobalScope است
    // متدها و ویژگی‌ها می‌توانند مستقیماً
    // به عنوان قابلیت‌های سراسری یا با پیشوند self در دسترس باشند
    const dpr = self.devicePixelRatio;

    // از ctx طوری استفاده کنید که گویی یک بوم نقاشی معمولی است
    const colors = ["red", "green", "blue"];
    const size = 32;
    for (let y = 0; y < geom.height / size; y++) {
      for (let x = 0; x < geom.width / size; x++) {
        const color = colors[(x + y) % colors.length];
        ctx.beginPath();
        ctx.fillStyle = color;
        ctx.rect(x * size, y * size, size, size);
        ctx.fill();
      }
    }
  }
}

// کلاس خود را با یک نام مشخص ثبت کنید
registerPaint("checkerboard", CheckerboardPainter);
```

### بارگذاری یک paint worklet

مثال زیر نحوهٔ بارگذاری worklet فوق را از فایل جاوااسکریپت آن با استفاده از تشخیص قابلیت نشان می‌دهد.

```js
if ("paintWorklet" in CSS) {
  CSS.paintWorklet.addModule("checkerboard.js");
}
```

### استفاده از یک paint worklet

این مثال نحوهٔ استفاده از یک paint `Worklet` را در یک stylesheet نشان می‌دهد، از جمله ساده‌ترین روش برای ارائهٔ یک جایگزین در صورت عدم پشتیبانی از `CSS.paintWorklet`.

```css
textarea {
  background-image: url("checkerboard.png"); /* جایگزین */
  background-image: paint(checkerboard);
}
```

همچنین می‌توانید از at-rule مربوط به {{cssxref('@supports')}} استفاده کنید.

```css
@supports (background: paint(id)) {
  textarea {
    background-image: paint(checkerboard);
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از CSS Painting API](/en-US/docs/Web/API/CSS_Painting_API/Guide)
- [CSS Painting API](/en-US/docs/Web/API/CSS_Painting_API)
- [Houdini APIs](/en-US/docs/Web/API/Houdini_APIs)