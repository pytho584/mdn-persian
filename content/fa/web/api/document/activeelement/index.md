---
title: "Document: activeElement property"
short-title: activeElement
slug: Web/API/Document/activeElement
page-type: web-api-instance-property
browser-compat: api.Document.activeElement
---

{{APIRef("DOM")}}

خاصیت فقط‌خواندنی **`activeElement`** از رابط {{domxref("Document")}}، عنصر {{domxref("Element")}}ای را درون DOM بازمی‌گرداند که رویدادهای صفحه‌کلید مانند {{domxref("Element/keydown_event", "keydown")}} و {{domxref("Element/keyup_event", "keyup")}} را دریافت می‌کند. این معمولاً معادل عنصر متمرکز (focused) است.

اینکه کدام عناصر قابل تمرکز هستند، به پلتفرم و پیکربندی فعلی مرورگر بستگی دارد. برای مثال، در Safari با پیروی از رفتار macOS، عناصری که ورودی متن نیستند به‌طور پیش‌فرض قابل تمرکز نیستند، مگر اینکه گزینه «Full Keyboard Access» در تنظیمات سیستم فعال شده باشد.

معمولاً کاربر می‌تواند با فشردن کلید <kbd>Tab</kbd>، فوکوس را بین عناصر قابل تمرکز در صفحه جابه‌جا کند و با حرکات صفحه‌کلید مانند <kbd>Space</kbd> یا <kbd>Enter</kbd>، کلیک روی عنصر متمرکز را شبیه‌سازی کند.

> [!NOTE]
> فوکوس (اینکه کدام عنصر رویدادهای ورودی کاربر را دریافت می‌کند) با انتخاب (selection) (بخش برجسته‌شده فعلی سند) یکسان نیست. می‌توانید انتخاب فعلی را با استفاده از {{domxref("window.getSelection()")}} به دست آورید.

## مقدار

عمیق‌ترین {{domxref('Element')}}ای که در حال حاضر فوکوس دارد.

- اگر عنصر متمرکز درون یک درخت سایه (shadow tree) درون سند فعلی باشد (مثلاً عنصر متمرکز داخل یک `iframe` است و `document` فراخوانی‌شده شامل آن iframe است)، آنگاه این مقدار ریشهٔ آن درخت خواهد بود (در این مثال، همان `iframe`).
- اگر عنصر متمرکز درون یک درخت سند باشد که از سند فعلی منشعب نشده است (مثلاً عنصر متمرکز در سند اصلی است و `document` فراخوانی‌شده یک iframe توکار است)، آنگاه این مقدار `null` خواهد بود.
- اگر هیچ عنصر متمرکزی وجود نداشته باشد، این مقدار {{domxref("Document.body")}} یا {{domxref("Document.documentElement")}} است.

## مثال‌ها

### HTML

```html
<p>متن زیر را از یکی از جعبه‌های متنی زیر انتخاب کنید:</p>

<form>
  <textarea name="ta-example-one" id="ta-example-one" rows="7" cols="40">
این جعبه متن شماره یک است. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec tincidunt, lorem a porttitor molestie, odio nibh iaculis libero, et accumsan nunc orci eu dui.</textarea>
  <textarea name="ta-example-two" id="ta-example-two" rows="7" cols="40">
این جعبه متن شماره دو است. Fusce ullamcorper, nisl ac porttitor adipiscing, urna orci egestas libero, ut accumsan orci lacus laoreet diam. Morbi sed euismod diam.</textarea>
</form>

<p>شناسه عنصر فعال: <em id="output-element"></em></p>
<p>متن انتخاب‌شده: <em id="output-text"></em></p>
```

### JavaScript

```js
function onMouseUp(e) {
  const activeTextarea = document.activeElement;
  const selection = activeTextarea.value.substring(
    activeTextarea.selectionStart,
    activeTextarea.selectionEnd,
  );

  const outputElement = document.getElementById("output-element");
  const outputText = document.getElementById("output-text");
  outputElement.textContent = activeTextarea.id;
  outputText.textContent = selection;
}

const textarea1 = document.getElementById("ta-example-one");
const textarea2 = document.getElementById("ta-example-two");
textarea1.addEventListener("mouseup", onMouseUp);
textarea2.addEventListener("mouseup", onMouseUp);
```

### نتیجه

{{ EmbedLiveSample('Examples', '400', '400') }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document.hasFocus")}}