---
title: "Highlight"
slug: Web/API/Highlight
page-type: web-api-interface
browser-compat: api.Highlight
---

{{APIRef("CSS Custom Highlight API")}}

رابط **`Highlight`** از [CSS Custom Highlight API](/en-US/docs/Web/API/CSS_Custom_Highlight_API) برای نمایش مجموعه‌ای از نمونه‌های {{domxref("AbstractRange")}} استفاده می‌شود که با استفاده از این API سبک‌دهی می‌شوند.

برای سبک‌دهی به بازه‌های دلخواه در یک صفحه، یک شیء `Highlight` جدید ایجاد کنید، یک یا چند شیء `AbstractRange` به آن اضافه کنید، و آن را با استفاده از {{domxref("HighlightRegistry")}} ثبت کنید.

یک نمونه `Highlight` یک [شیء شبیه به `Set`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set#set-like_browser_apis) است که می‌تواند یک یا چند شیء `AbstractRange` را نگه دارد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("Highlight.Highlight()", "Highlight()")}}
  - : یک شیء `Highlight` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

_رابط `Highlight` هیچ ویژگی‌ای را به ارث نمی‌برد._

- {{domxref("Highlight.priority")}}
  - : یک عدد که اولویت این شیء `Highlight` را نشان می‌دهد. هنگامی که چندین هایلایت با هم همپوشانی دارند، مرورگر از این اولویت برای تصمیم‌گیری در مورد نحوه سبک‌دهی به بخش‌های همپوشانی استفاده می‌کند.
- {{domxref("Highlight.size")}} {{ReadOnlyInline}}
  - : تعداد بازه‌های موجود در شیء `Highlight` را برمی‌گرداند.
- {{domxref("Highlight.type")}}
  - : یک {{jsxref("String")}} شمارشی که برای مشخص کردن معنای معنایی هایلایت استفاده می‌شود. این به فناوری‌های کمکی امکان می‌دهد تا این معنا را هنگام نمایش هایلایت به کاربران لحاظ کنند.

## روش‌های نمونه

_رابط `Highlight` هیچ روشی را به ارث نمی‌برد._

- {{domxref("Highlight.add()")}}
  - : یک بازه جدید به این هایلایت اضافه می‌کند.
- {{domxref("Highlight.clear()")}}
  - : تمام بازه‌ها را از این هایلایت حذف می‌کند.
- {{domxref("Highlight.delete()")}}
  - : یک بازه را از این هایلایت حذف می‌کند.
- {{domxref("Highlight.entries()")}}
  - : یک شیء پیمایش‌گر جدید برمی‌گرداند که شامل هر بازه در شیء هایلایت، به ترتیب درج است.
- {{domxref("Highlight.forEach()")}}
  - : تابع callback داده شده را یک بار برای هر بازه در شیء هایلایت، به ترتیب درج، فراخوانی می‌کند.
- {{domxref("Highlight.has()")}}
  - : یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا یک بازه در شیء هایلایت وجود دارد یا خیر.
- {{domxref("Highlight.keys()")}}
  - : یک نام مستعار برای {{domxref("Highlight.values()")}}.
- {{domxref("Highlight.values()")}}
  - : یک شیء پیمایش‌گر جدید برمی‌گرداند که بازه‌های موجود در شیء هایلایت را به ترتیب درج تولید می‌کند.

## مثال‌ها

مثال زیر نحوه برجسته‌سازی بخش‌های خاصی از یک بلوک متنی را نشان می‌دهد.

```html-nolint
<p class="foo">Lorem ipsum dolor sit amet consectetur adipisicing elit. Exercitationem
  sapiente non eum facere? Nam rem hic culpa, ipsa rerum ab itaque consectetur
  molestiae dolores vitae! Quo ex explicabo tempore? Tenetur.</p>
```

این کد جاوااسکریپت [بازه‌هایی](/en-US/docs/Web/API/Range) ایجاد می‌کند، یک شیء `Highlight` جدید برای آن‌ها نمونه‌سازی می‌کند، و آن را برای سبک‌دهی در صفحه [ثبت می‌کند](/en-US/docs/Web/API/HighlightRegistry/set):

```js
const parentNode = document.querySelector(".foo");
const textNode = parentNode.firstChild;

// Create a couple of ranges.
const range1 = new Range();
range1.setStart(textNode, 6);
range1.setEnd(textNode, 21);

const range2 = new Range();
range2.setStart(textNode, 57);
range2.setEnd(textNode, 71);

// Create a custom highlight for these ranges.
const highlight = new Highlight(range1, range2);

// Register the ranges in the HighlightRegistry.
CSS.highlights.set("my-custom-highlight", highlight);
```

قطعه کد CSS زیر نحوه سبک‌دهی به هایلایت سفارشی ثبت شده را با استفاده از شبه‌عنصر {{cssxref("::highlight")}} نشان می‌دهد:

```css
::highlight(my-custom-highlight) {
  background-color: peachpuff;
}
```

### نتیجه

{{EmbedLiveSample("example", "100%", '100')}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("css_custom_highlight_api", "CSS Custom Highlight API", "", "nocode")}}
- ماژول [CSS custom highlight API](/en-US/docs/Web/CSS/Guides/Custom_highlight_API)
- [نگاهی اولیه به CSS Custom Highlight API: آینده برجسته‌سازی بازه‌های متنی در وب](https://css-tricks.com/css-custom-highlight-api-early-look/)