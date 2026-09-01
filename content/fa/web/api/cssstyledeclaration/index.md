---
title: "CSSStyleDeclaration"
---

---
title: CSSStyleDeclaration
slug: Web/API/CSSStyleDeclaration
page-type: web-api-interface
browser-compat: api.CSSStyleDeclaration
---

{{APIRef("CSSOM")}}

رابط **`CSSStyleDeclaration`** کلاس پایه برای اشیایی است که بلوک‌های اعلامیهٔ CSS را با مجموعه‌های مختلفی از اطلاعات سبک CSS پشتیبانی‌شده نشان می‌دهند:

- {{domxref("CSSStyleProperties")}} — سبک‌های CSS که در شیوه‌نامه اعلام شده‌اند ({{domxref("CSSStyleRule.style")}})، سبک‌های درون‌خطی برای یک عنصر مانند {{DOMxRef("HTMLElement/style","HTMLElement")}}، {{domxref("SVGElement/style","SVGElement")}} و {{domxref("MathMLElement/style","MathMLElement")}}، یا سبک محاسبه‌شده برای عنصری که توسط {{DOMxRef("Window.getComputedStyle()")}} بازگردانده شده است.
- {{domxref("CSSPageDescriptors")}} — سبک‌ها برای [قواعد at](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) در CSS.

این رابط اطلاعات سبک و روش‌ها و ویژگی‌های مختلف مرتبط با سبک را در دسترس قرار می‌دهد.
برای مثال، {{DOMxRef("CSSStyleDeclaration/getPropertyValue","getPropertyValue()" )}} را برای دریافت مقدار یک ویژگی CSS با نام دارای خط تیره، مانند `border-top`، فراهم می‌کند که به دلیل خط تیره‌های موجود در نامش نمی‌توان به‌طور مستقیم با نماد نقطه‌ای به آن دسترسی داشت.

> [!NOTE]
> نسخه‌های قبلی مشخصات از `CSSStyleDeclaration` برای نمایش همهٔ بلوک‌های اعلامیهٔ CSS استفاده می‌کردند و برخی مرورگرها و نسخه‌های مرورگر ممکن است هنوز چنین کنند (جدول‌های سازگاری مرورگر برای APIهای بالا را بررسی کنید).
> به‌طور کلی، همان کد وب در هر دو نسخهٔ قدیمی و جدید کار می‌کند، اما برخی ویژگی‌هایی که در یک `CSSStyleDeclaration` بازگردانده می‌شوند ممکن است در یک زمینهٔ خاص مرتبط نباشند.

## ویژگی‌ها

- {{DOMxRef("CSSStyleDeclaration.cssText")}}
  - : نمایش متنی بلوک اعلامیه، اگر و تنها اگر از طریق {{DOMxRef("HTMLElement.style")}} در دسترس باشد.
    تنظیم این ویژگی، سبک درون‌خطی را تغییر می‌دهد.
    اگر نمایش متنی یک بلوک اعلامیهٔ محاسبه‌شده می‌خواهید، می‌توانید آن را با `JSON.stringify()` دریافت کنید.
- {{DOMxRef("CSSStyleDeclaration.length")}} {{ReadOnlyInline}}
  - : تعداد ویژگی‌ها.
    به متد {{DOMxRef("CSSStyleDeclaration.item()", 'item()')}} در زیر مراجعه کنید.
- {{DOMxRef("CSSStyleDeclaration.parentRule")}} {{ReadOnlyInline}}
  - : {{DOMxRef("CSSRule")}} شامل آن.

### ویژگی‌های CSS

- {{DOMxRef("CSSStyleDeclaration.cssFloat", "CSSStyleDeclaration.cssFloat")}} {{deprecated_inline}}
  - : نام مستعار ویژه برای ویژگی CSS {{CSSxRef("float")}}.
- ویژگی‌های نام‌گذاری‌شدهٔ `CSSStyleDeclaration`
  - : ویژگی‌های دارای خط تیره و ویژگی‌های camelCase برای همهٔ ویژگی‌های CSS پشتیبانی‌شده.

## متدهای نمونه

- {{DOMxRef("CSSStyleDeclaration.getPropertyPriority()")}}
  - : اولویت اختیاری "important" را برمی‌گرداند.
- {{DOMxRef("CSSStyleDeclaration.getPropertyValue()")}}
  - : مقدار ویژگی را با توجه به نام ویژگی برمی‌گرداند.
- {{DOMxRef("CSSStyleDeclaration.item()")}}
  - : نام یک ویژگی CSS را بر اساس ایندکس آن برمی‌گرداند، یا اگر ایندکس خارج از محدوده باشد، رشتهٔ خالی را برمی‌گرداند.
- {{DOMxRef("CSSStyleDeclaration.removeProperty()")}}
  - : یک ویژگی را از بلوک اعلامیهٔ CSS حذف می‌کند.
- {{DOMxRef("CSSStyleDeclaration.setProperty()")}}
  - : یک ویژگی CSS موجود را تغییر می‌دهد یا یک ویژگی CSS جدید در بلوک اعلامیه ایجاد می‌کند.
- {{DOMxRef("CSSStyleDeclaration.getPropertyCSSValue()")}} {{deprecated_inline}} {{non-standard_inline}}
  - : **تنها از طریق getComputedStyle در فایرفاکس پشتیبانی می‌شود.** مقدار ویژگی را به صورت {{DOMxRef("CSSPrimitiveValue")}} برمی‌گرداند، یا برای [ویژگی‌های کوتاه‌نویس](/en-US/docs/Web/CSS/Guides/Cascade/Shorthand_properties) مقدار `null` را برمی‌گرداند.

## مثال

```js
const styleObj = document.styleSheets[0].cssRules[0].style;
console.log(styleObj.cssText);

for (let i = styleObj.length; i--;) {
  const nameString = styleObj[i];
  styleObj.removeProperty(nameString);
}

console.log(styleObj.cssText);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}