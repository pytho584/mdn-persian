---
title: "HTMLImageElement: naturalHeight property"
short-title: naturalHeight
slug: Web/API/HTMLImageElement/naturalHeight
page-type: web-api-instance-property
browser-compat: api.HTMLImageElement.naturalHeight
---

{{APIRef("HTML DOM")}}

ویژگی فقط خواندنی **`naturalHeight`** از رابط {{domxref("HTMLImageElement")}} ارتفاع ذاتی (طبیعی) و تصحیح‌شده بر اساس تراکم تصویر را در {{Glossary("CSS pixel", "پیکسل‌های CSS")}} برمی‌گرداند.

این ارتفاعی است که تصویر در صورت ترسیم بدون هیچ محدودیت ارتفاعی خواهد داشت؛ اگر ارتفاعی برای تصویر مشخص نکنید یا آن را درون ظرفی که ارتفاع را محدود یا صریحاً مشخص می‌کند قرار ندهید، تصویر با این ارتفاع نمایش داده می‌شود.

> [!NOTE]
> در بیشتر مواقع، ارتفاع طبیعی برابر با ارتفاع واقعی تصویری است که توسط سرور ارسال می‌شود. با این حال، مرورگرها می‌توانند قبل از ارسال تصویر به رندرکننده، آن را تغییر دهند. به عنوان مثال، کروم [وضوح تصاویر را در دستگاه‌های کم‌قدرت کاهش می‌دهد](https://crbug.com/1187043#c7). در چنین مواردی، `naturalHeight` ارتفاع تصویر تغییر یافته توسط این مداخلات مرورگر را به عنوان ارتفاع طبیعی در نظر گرفته و این مقدار را برمی‌گرداند.

## Value

یک مقدار عدد صحیح که ارتفاع ذاتی تصویر را بر حسب پیکسل‌های CSS نشان می‌دهد. این ارتفاعی است که تصویر به طور طبیعی وقتی هیچ محدودیت یا مقدار مشخصی برای ارتفاع آن تعیین نشده است، ترسیم می‌شود. این ارتفاع طبیعی بر اساس تراکم پیکسلی دستگاهی که تصویر روی آن نمایش داده می‌شود تصحیح می‌شود، بر خلاف {{domxref("HTMLImageElement.height", "height")}}.

اگر ارتفاع ذاتی در دسترس نباشد - به دلیل اینکه تصویر ارتفاع ذاتی را مشخص نمی‌کند یا داده‌های تصویر برای به دست آوردن این اطلاعات در دسترس نیستند - `naturalHeight` مقدار 0 را برمی‌گرداند.

## Examples

این مثال اندازه طبیعی و تنظیم‌شده بر اساس تراکم تصویر را به همراه اندازه رندر شده آن که توسط CSS صفحه و عوامل دیگر تغییر یافته است، نمایش می‌دهد.

### HTML

```html
<div class="box">
  <img
    src="/en-US/docs/Web/HTML/Reference/Elements/img/clock-demo-400px.png"
    class="image"
    alt="A round wall clock with a white dial and black numbers" />
</div>
<pre></pre>
```

HTML شامل یک تصویر 400x398 پیکسلی است که درون یک {{HTMLElement("div")}} قرار گرفته است.

### CSS

```css
.box {
  width: 200px;
  height: 200px;
}

.image {
  width: 100%;
}
```

نکته قابل توجه در CSS بالا این است که استایل استفاده شده برای ظرفی که تصویر در آن ترسیم می‌شود 200 پیکسل عرض دارد و تصویر برای پر کردن عرض آن (100%) ترسیم می‌شود.

### JavaScript

```js
const output = document.querySelector("pre");
const image = document.querySelector("img");

image.addEventListener("load", (event) => {
  const { naturalWidth, naturalHeight, width, height } = image;
  output.textContent = `
Natural size: ${naturalWidth} x ${naturalHeight} pixels
Displayed size: ${width} x ${height} pixels
`;
});
```

کد جاوااسکریپت اندازه طبیعی و اندازه نمایش داده شده را درون {{HTMLElement("pre")}} قرار می‌دهد. این کار در پاسخ به کنترل‌کننده رویداد {{domxref("HTMLElement.load_event", "load")}} تصویر انجام می‌شود تا اطمینان حاصل شود که تصویر قبل از تلاش برای بررسی عرض و ارتفاع آن در دسترس است.

### Result

{{EmbedLiveSample("Examples", 600, 280)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("HTMLImageElement.height")}}
- {{domxref("HTMLImageElement.naturalWidth")}}