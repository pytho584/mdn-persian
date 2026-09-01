---
title: "CSSPseudoElement"
---

---
title: CSSPseudoElement
slug: Web/API/CSSPseudoElement
page-type: web-api-interface
status:
  - experimental
browser-compat: api.CSSPseudoElement
---

{{APIRef}}{{SeeCompatTable}}

رابطهٔ **`CSSPseudoElement`** یک [شبه‌عنصر (pseudo-element)](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-elements) را نمایش می‌دهد.

نمونه‌های این رابط را می‌توان با فراخوانی {{DOMxRef("Element.pseudo()")}} یا {{DOMxRef("CSSPseudoElement.pseudo()")}} به دست آورد.

## ویژگی‌های نمونه

- {{DOMxRef("CSSPseudoElement.element")}} {{Experimental_Inline}} {{ReadOnlyInline}}
  - : عنصر مبدأ نهایی (ultimate originating) شبه‌عنصر را به‌صورت {{DOMxRef("Element")}} برمی‌گرداند.
- {{DOMxRef("CSSPseudoElement.parent")}} {{Experimental_Inline}} {{ReadOnlyInline}}
  - : عنصر مبدأ بلافصل شبه‌عنصر را برمی‌گرداند.
- {{DOMxRef("CSSPseudoElement.type")}} {{Experimental_Inline}} {{ReadOnlyInline}}
  - : انتخابگر شبه‌عنصر را به‌صورت رشته برمی‌گرداند.

## روش‌های نمونه

- {{DOMxRef("CSSPseudoElement.pseudo()")}} {{experimental_inline}}
  - : یک نمونه `CSSPseudoElement` برمی‌گرداند که یک [شبه‌عنصر تودرتو](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-elements#nesting_pseudo-elements) خاص را نمایش می‌دهد.

## توصیف

رابطهٔ **`CSSPseudoElement`** یک [شبه‌عنصر](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-elements) را نمایش می‌دهد. می‌توانید با استفاده از روش {{DOMxRef("Element.pseudo()")}} نمایشی از یک شبه‌عنصر متصل به یک عنصر DOM، یا با استفاده از روش {{DOMxRef("CSSPseudoElement.pseudo()")}} نمایشی از یک [شبه‌عنصر تودرتو](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-elements#nesting_pseudo-elements) (مثلاً `::marker` در `::before::marker`) به دست آورید.

ویژگی {{DOMxRef("CSSPseudoElement.type")}} رشته‌ای را برمی‌گرداند که نوع شبه‌عنصر را مشخص می‌کند. انواع پشتیبانی‌شده عبارت‌اند از:

- {{cssxref("::after")}}
- {{cssxref("::before")}}
- {{cssxref("::marker")}}

ویژگی‌های {{DOMxRef("CSSPseudoElement.element")}} و {{DOMxRef("CSSPseudoElement.parent")}} شبیه به نظر می‌رسند، اما از نظر عملکرد تفاوت دارند:

- ویژگی `element` همیشه یک {{domxref("Element")}} برمی‌گرداند: ارجاعی به عنصر مبدأ نهایی شبه‌عنصر یا شبه‌عنصر تودرتو.
- ویژگی `parent` ارجاعی به عنصر مبدأ _بلافصل_ شبه‌عنصر برمی‌گرداند: این می‌تواند یک {{DOMxRef("Element")}} باشد یا در مورد [شبه‌عنصر تودرتو](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-elements#nesting_pseudo-elements)، یک `CSSPseudoElement`.

## مثال‌ها

### مثال پایه با استفاده از Element.pseudo

با استفاده از شبه‌عنصرها، بیشتر مرورگرهای مدرن به‌طور خودکار علامت‌های نقل‌قول را دور متن داخل یک عنصر {{HTMLElement('q')}} اضافه می‌کنند. (ممکن است برای افزودن علامت‌های نقل‌قول در مرورگرهای قدیمی‌تر به یک قانون استایل نیاز باشد.) مثال زیر ویژگی‌های پایهٔ شیء `CSSPseudoElement` را نشان می‌دهد که علامت نقل‌قول آغازین را نمایش می‌دهد.

```js
const element = document.querySelector("q");
const cssPseudoElement = element.pseudo("::before");
console.log(cssPseudoElement.element); // خروجی: [object HTMLQuoteElement]
console.log(cssPseudoElement.type); // خروجی: '::before'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{DOMxRef("Element.pseudo()")}}
- {{DOMxRef("Web Animations API", "", "", "true")}}
- {{DOMxRef("Element.animate()")}}
- [ماژول شبه‌عنصرهای CSS](/en-US/docs/Web/CSS/Guides/Pseudo-elements)