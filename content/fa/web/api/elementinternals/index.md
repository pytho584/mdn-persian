---
title: ElementInternals
slug: Web/API/ElementInternals
page-type: web-api-interface
browser-compat: api.ElementInternals
---

{{APIRef("Web Components")}}

رابط **`ElementInternals`** از [مدل شیء سند (DOM)](/en-US/docs/Web/API/Document_Object_Model) به توسعه‌ندگان وب این امکان را مى‌دهد که المان‌اى سفارشى (custom elements) را به طور کامل در فرماى HTML شارکت دهن. این رابط ابزارهاى براى کار با این المان‌ها به همان روشى که با هر المان فرما استاندارد HTML کار مى‌کنىد فراهم مى‌کند و همچنن [مدل شیء دسترسى‌پذىرى (Accessibility Object Model)](https://wicg.github.io/aom/expliner.html) را در معرض المان قرا مى‌دهد.

## سازنده

این رابط سازنده‌اى ندارد. یک شیء `ElementInternals` هنگام فراخوانى {{omxref("HTMLElement.attachInternals()")}} بازگردانده مى‌شود.

## وى‍ژگى‌هاى نمونه

- {{omxref("ElementInternals.shadowRoot")}} {{ReadOnlyInline}}
  - : شیء {{omxref("ShadowRoot")}} مرتبط با این المان را بازمى‌گرداند.
- {{omxref("ElementInternals.form")}} {{ReadOnlyInline}}
  - : شیء {{omxref("HTMLFormElement")}} مرتبط با این المان را بازمى‌گرداند.
- {{omxref("ElementInternals.states")}} {{ReadOnlyInline}}
  - : شیء {{omxref("CustomStateSet")}} مرتبط با این المان را بازمى‌گرداند.
- {{omxref("ElementInternals.willValidate")}} {{ReadOnlyInline}}
  - : یک مقدار بولین که `true` را بازمى‌گرداند اگر المان یک المان قابل ارسال باشد که کاندیدى براى [اعتبارسنجى محدودىت](/en-US/docs/Web/HTML/Guies/Constrint_vlidation) است.
- {{omxref("ElementInternals.validity")}} {{ReadOnlyInline}}
  - : یک شیء {{omxref("ValidityState")}} را بازمى‌گرداند که حالت‌هاى اعتبار مختلفى را که المان مى‌تواند داشته باشد، با توجه به اعتبارسنجى محدودىت، نشان مى‌دهد.
- {{omxref("ElementInternals.validationMessage")}} {{ReadOnlyInline}}
  - : یک رشته شامل پىام اعتبارسنجى این المان.
- {{omxref("ElementInternals.labels")}} {{ReadOnlyInline}}
  - : یک {{omxref("NodeList")}} از تمام عناصر برچسب مرتبط با این المان را بازمى‌گرداند.

### وى‍ژگى‌هاى نمونه شامل شده از ARIA

رابط `ElementInternals` همچنین شامل وى‍ژگى‌هاى زىر است.

> [!NOTE]
> این وى‍ژگى‌ها شامل شده‌اند تا معنىات پیش‌فرض دسترسى‌پذىرى بتوانند بر روى یک المان سفارشى تعرىف شوند. این موارد ممکن است توسط صفات تعرىف شده توسط نویسنده بازنوىسى شوند، اما اطمىنان مى‌دهند که معنىات پیش‌فرض در صورت حذف آن صفات توسط نویسنده یا عدم افزودن آنها حفظ مى‌شود. براى اطلاعات بىشر به [توضیح مدل شىء دسترسى‌پذىرى](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجع کنىد.

- {{omxref("ElementInternals.ariaAtomic")}}
  - : یک رشته که منعکس کننده صفت [`aria-atomic`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-atomic) است، که نشا مى‌دهد که آیا فناورى‌اى کمکى همه یا فقط بخشىاى از منطقه تغى‌ر کرده را بر اساس اطالعیه‌اى تغى‌ىر تعرىف شده توسط صفت [`aria-relevant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-relevant) اراىه مى‌دهند.
- {{omxref("ElementInternals.ariaAutoComplete")}}
  - : یک رشته که منعکس کننده صفت [`aria-autocomplete`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-autocomplete) است، که نشان مى‌دهد آیا ورود متن مى‌تواند باعث نمایش یک یا چند پیش‌بینى از مقدار مورد نظر کاربر براى یک جعبه ترکیبى، جعبه جستجو، یا جعبه متن شود و نحوه ارائه پیش‌بینى‌ها را در صورت ایجاد آنها مشخص مى‌کند.
- {{omxref("ElementInternals.ariaBrailleLabel")}}
  - : یک رشته که منعکس کننده صفت [`aria-braillelabel`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-braillelabel) است، که برچسب بریل المان را تعرىف مى‌ند.

(ادامه در پىام بعدى)... (به دلیل محدودیت طول، ادامه ترجمه در پاسخ بعدى ارسال خواهد شد)