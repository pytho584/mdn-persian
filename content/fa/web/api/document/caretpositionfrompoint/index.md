---
title: "Document: caretPositionFromPoint() method"
---

---
title: "Document: caretPositionFromPoint() method"
short-title: caretPositionFromPoint()
slug: Web/API/Document/caretPositionFromPoint
page-type: web-api-instance-method
browser-compat: api.Document.caretPositionFromPoint
---

{{APIRef("CSSOM view API")}}

متد **`caretPositionFromPoint()`** از رابط {{domxref("Document")}} یک شیء {{domxref('CaretPosition')}} برمی‌گرداند که شامل گره DOM، و همچنین مکان‌نما و افست کاراکتری مکان‌نما درون آن گره است.

## نحو

```js-nolint
caretPositionFromPoint(x, y)
caretPositionFromPoint(x, y, options)
```

### پارامترها

- `x`
  - : مختصات افقی یک نقطه.
- `y`
  - : مختصات عمودی یک نقطه.
- `options` {{optional_inline}}
  - : ویژگی‌های اختیاری زیر نیز می‌توانند مشخص شوند.
    - `shadowRoots` {{optional_inline}}
      - : آرایه‌ای از شیءهای {{domxref("ShadowRoot")}}.
        این متد می‌تواند موقعیت مکان‌نما را برای گره‌ای که درون Shadow DOM یک ریشه سایه‌ی ارائه‌شده تعریف شده است بازگرداند.
        اگر موقعیت مکان‌نما درون یک ریشه سایه باشد که ارائه نشده است، {{domxref('CaretPosition')}} بازگشتی به گره‌ای که میزبان ریشه سایه است نقشه‌برداری مجدد می‌شود.

### مقدار بازگشتی

یک شیء {{domxref('CaretPosition')}} یا `null`.

اگر هیچ نمای دید (viewport) مرتبط با سند وجود نداشته باشد، اگر `x` یا `y` منفی یا خارج از ناحیه نمای دید باشند، یا اگر مختصات به نقطه‌ای اشاره کنند که در آن هیچ نشانگر نقطه‌ی درج متن نمی‌تواند قرار گیرد، مقدار بازگشتی `null` خواهد بود.

## مثال‌ها

### تقسیم گره‌های متنی در موقعیت مکان‌نما در DOM

این مثال نشان می‌دهد که چگونه می‌توان موقعیت مکان‌نما را از یک گره DOM انتخاب‌شده به‌دست آورد، از این موقعیت برای تقسیم گره استفاده کرد، و یک شکست خط (line break) بین دو گره درج کرد. این مثال از `caretPositionFromPoint()` برای دریافت موقعیت مکان‌نما در صورت پشتیبانی استفاده می‌کند و در غیر این صورت از متد غیراستاندارد {{domxref("Document.caretRangeFromPoint()")}} به‌عنوان جایگزین استفاده می‌کند.

توجه داشته باشید که بخش‌هایی از کد، از جمله کد مورد استفاده برای ثبت وقایع (logging)، پنهان شده‌اند؛ زیرا برای درک این متد مفید نیستند.

#### HTML

HTML یک پاراگراف متن را تعریف می‌کند.

```html hidden
<div id="message">
  This browser supports neither document.caretRangeFromPoint nor
  document.caretPositionFromPoint
</div>
```

```html hidden
<button id="reset" type="button">Reset</button>
```

```html
<p>
  Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy
  eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam
  voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita
  kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.
</p>
```

```html hidden
<pre id="log">Log</pre>
```

```css hidden
#log {
  height: 30px;
  padding: 0.5rem;
  border: 1px solid black;
}
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = text;
}

const reload = document.querySelector("#reset");

reload.addEventListener("click", () => {
  window.location.reload(true);
});
```

```css hidden
#message {
  color: red;
  font-weight: bold;
}

#message.fallback {
  color: darkorange;
}

#message.supported {
  color: green;
}
```

#### JavaScript

متد زیر ابتدا پشتیبانی از `document.caretPositionFromPoint` را بررسی می‌کند و از آن برای دریافت گره متنی و افست در موقعیت مکان‌نما استفاده می‌کند. اگر مرورگر از آن متد پشتیبانی نکند، کد سپس {{domxref("Document.caretRangeFromPoint", "document.caretRangeFromPoint")}} را بررسی کرده و به‌جای آن از آن استفاده می‌کند.

اگر گره در موقعیت مکان‌نما یک گره متنی باشد، کد سپس [گره را](/en-US/docs/Web/API/Text/splitText) در افست انتخاب‌شده به دو بخش تقسیم می‌کند و یک شکست خط بین دو گره درج می‌کند.

```js
function insertBreakAtPoint(e) {
  let range;
  let textNode;
  let offset;

  if (document.caretPositionFromPoint) {
    range = document.caretPositionFromPoint(e.clientX, e.clientY);
    textNode = range.offsetNode;
    offset = range.offset;
  } else if (document.caretRangeFromPoint) {
    // Use WebKit-proprietary fallback method
    range = document.caretRangeFromPoint(e.clientX, e.clientY);
    textNode = range.startContainer;
    offset = range.startOffset;
  } else {
    // Neither method is supported, do nothing
    return;
  }

  // Logging code (uses hidden method to get substring with ^ at offset)
  if (textNode?.nodeType === 3) {
    const caretInText = getSubstringAroundOffset(textNode.textContent, offset);
    log(
      `node: ${textNode.nodeName}, offset: ${offset}, insert: ${caretInText}`,
    );
  }

  // Only split TEXT_NODEs
  if (textNode?.nodeType === 3) {
    let replacement = textNode.splitText(offset);
    let br = document.createElement("br");
    textNode.parentNode.insertBefore(br, replacement);
  }
}
```

این متد به‌عنوان کنترل‌کننده رویداد کلیک برای هر عنصر پاراگراف اضافه شده است.

```js
const paragraphs = document.getElementsByTagName("p");
for (const paragraph of paragraphs) {
  paragraph.addEventListener("click", insertBreakAtPoint);
}
```

```js hidden
// Inserts ^ at offset and gets a substring for log
function getSubstringAroundOffset(text, offset, length = 10) {
  const start = Math.max(0, offset - length);
  const end = Math.min(text.length, offset + length + 1);
  // Insert the caret character at the offset
  const modifiedText = `${text.substring(0, offset)}^${text.substring(offset)}`;
  return `...${modifiedText.substring(start, end)}...`;
}
```

```js hidden
let message = document.getElementById("message");
if (document.caretPositionFromPoint) {
  message.textContent =
    "This browser supports the standard document.caretPositionFromPoint";
  message.classList.add("supported");
} else if (document.caretRangeFromPoint) {
  message.textContent =
    "This browser supports the non-standard document.caretRangeFromPoint";
  message.classList.add("supported");
}
```

#### نتایج

برای درج شکست خط در نقطه‌ای که کلیک می‌کنید، در هر جای پاراگراف **Lorem ipsum ...** زیر کلیک کنید. توجه داشته باشید که گزارش (log) نام گره (`nodeName`)، افست، و بخشی از گره انتخاب‌شده را با کاراکتر `^` در محل افست نشان می‌دهد.

{{EmbedLiveSample('Split text nodes at caret position in DOM','100%','400px')}}

### تقسیم گره‌های متنی در موقعیت‌های مکان‌نما در یک Shadow DOM

این مثال نشان می‌دهد که چگونه می‌توان موقعیت مکان‌نما را از یک گره انتخاب‌شده درون یک ریشه سایه (shadow root) به‌دست آورد. این مثال بسیار شبیه به مثال فقط-DOM در بالا است، با این تفاوت که بخشی از متن درون یک ریشه سایه قرار دارد. ما یک دکمه برای این فراهم کرده‌ایم تا تفاوت زمانی که یک ریشه سایه به `caretPositionFromPoint()` ارسال می‌شود/ارسال نمی‌شود را ببینید.

توجه داشته باشید که بخش‌هایی از کد، از جمله کد مورد استفاده برای ثبت وقایع (logging)، پنهان شده‌اند؛ زیرا برای درک این متد مفید نیستند.

#### HTML

HTML یک پاراگراف متن را درون یک عنصر {{htmlelement("div")}} تعریف می‌کند. پاراگراف شامل یک عنصر {{htmlelement("span")}} با `id` برابر با "host" است که از آن به‌عنوان میزبان یک ریشه سایه استفاده خواهیم کرد. همچنین چند دکمه وجود دارد که برای بازنشانی مثال و برای افزودن/حذف آرگومان گزینه‌ی ریشه سایه به `caretPositionFromPoint()` استفاده می‌کنیم.

```html hidden
<div id="message">
  This browser supports neither document.caretRangeFromPoint nor
  document.caretPositionFromPoint
</div>
```

```html
<button id="reset" type="button">Reset</button>
<button id="shadowButton" type="button">Add Shadow</button>
<div>
  <p>
    Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy
    eirmod tempor invidunt ut <span id="host"></span> labore et dolore magna
    aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo
    dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est
    Lorem ipsum dolor sit amet.
  </p>
</div>
```

```html hidden
<pre id="log">Log</pre>
```

#### CSS

در اینجا از CSS استفاده می‌کنیم تا عنصر `#host` قرمز و توپُر (bold) شود. این کار تمایز بین متن در DOM و متن در Shadow DOM را آسان‌تر می‌کند.

```css
#host {
  color: red;
  font-weight: bold;
}
```

```css hidden
#log {
  height: 30px;
  padding: 0.5rem;
  border: 1px solid black;
}
```

```css hidden
#message {
  color: red;
  font-weight: bold;
}

#message.fallback {
  color: darkorange;
}

#message.supported {
  color: green;
}
```

#### JavaScript

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = text;
}

const reload = document.querySelector("#reset");

reload.addEventListener("click", () => {
  window.location.reload(true);
});
```

ابتدا کدی داریم که Shadow DOM ما را پر می‌کند. ما از JavaScript برای پیوست کردن یک ریشه سایه به‌صورت پویا استفاده می‌کنیم، زیرا سیستم مثال‌های MDN به ما اجازه نمی‌دهد این کار را به‌صورت اعلانی (declarative) با استفاده از عنصر {{htmlelement("template")}} انجام دهیم. محتوای Shadow DOM یک عنصر {{htmlelement("span")}} است که متن «I'm in the shadow DOM» را در خود دارد.

```js
const host = document.querySelector("#host");
const shadow = host.attachShadow({ mode: "open" });
const shadowSpan = document.createElement("span");
shadowSpan.textContent = "I'm in the shadow DOM";
shadow.appendChild(shadowSpan);
```

سپس یک کنترل‌کننده رویداد برای دکمهٔ «Enable/Disable shadow» اضافه می‌کنیم. این کد مقدار متغیر `useShadows` را تغییر می‌دهد و متن دکمه را به‌طور مناسب به‌روزرسانی می‌کند.

```js
let useShadows = false;

const shadowButton = document.querySelector("#shadowButton");
shadowButton.addEventListener("click", () => {
  useShadows = !useShadows;
  shadowButton.innerText = useShadows ? "Remove Shadow" : "Add Shadow";
});
```

متد زیر ابتدا پشتیبانی از `document.caretPositionFromPoint` را بررسی می‌کند و از آن برای دریافت گره متنی و افست در موقعیت مکان‌نما استفاده می‌کند. مقدار متغیر `useShadows` برای تعیین اینکه آیا ریشه سایه میزبانی‌شده در متن ما به `caretPositionFromPoint()` ارسال شود یا نه استفاده می‌شود.

- اگر مرورگر از آن متد پشتیبانی نکند، کد سپس {{domxref("Document.caretRangeFromPoint", "document.caretRangeFromPoint")}} را بررسی کرده و به‌جای آن از آن استفاده می‌کند.
- اگر گره در موقعیت مکان‌نما یک گره متنی باشد، کد سپس گره را در افست انتخاب‌شده تقسیم می‌کند و یک شکست خط بین آنها درج می‌کند.
- اگر گره یک گره عنصر باشد، کد یک گره عنصر شکست خط را در افست درج می‌کند.

```js
function insertBreakAtPoint(e) {
  let range;
  let textNode;
  let offset;

  if (document.caretPositionFromPoint) {
    range = document.caretPositionFromPoint(
      e.clientX,
      e.clientY,
      useShadows ? { shadowRoots: [shadow] } : null,
    );
    textNode = range.offsetNode;
    offset = range.offset;
  } else if (document.caretRangeFromPoint) {
    // Use WebKit-proprietary fallback method
    range = document.caretRangeFromPoint(e.clientX, e.clientY);
    textNode = range.startContainer;
    offset = range.startOffset;
  } else {
    // Neither method is supported, do nothing
    return;
  }

  // Logging code (uses hidden method to get substring with ^ at offset)
  if (textNode) {
    if (textNode.nodeType === 3) {
      const caretInText = getSubstringAroundOffset(
        textNode.textContent,
        offset,
      );
      log(
        `type: TEXT_NODE, name: ${textNode.nodeName}, offset: ${offset}:
${caretInText}`,
      );
    } else if (textNode.nodeType === 1) {
      log(`type: ELEMENT_NODE, name: ${textNode.nodeName}, offset: ${offset}`);
    } else {
      log(
        `type: ${textNode.nodeType}, name: ${textNode.nodeName}, offset: ${offset}`,
      );
    }
  }

  // Insert line at caret
  if (textNode?.nodeType === 3) {
    // TEXT_NODE - split text at offset and add br
    let replacement = textNode.splitText(offset);
    let br = document.createElement("br");
    textNode.parentNode.insertBefore(br, replacement);
  } else if (textNode?.nodeType === 1) {
    // ELEMENT_NODE - Add br node at offset node
    let br = document.createElement("br");
    const targetNode = textNode.childNodes[offset];
    textNode.insertBefore(br, targetNode);
  } else {
    // Do nothing
  }
}
```

در نهایت، دو کنترل‌کننده رویداد کلیک برای عناصر پاراگراف به‌ترتیب در DOM و در ریشه سایه اضافه می‌کنیم. توجه داشته باشید که باید عناصر درون `shadowRoot` را به‌طور خاص جست‌وجو کنیم، زیرا آنها برای روش‌های معمول جست‌وجوی DOM قابل مشاهده نیستند.

```js
// Click event handler <p> elements in the DOM
const paragraphs = document.getElementsByTagName("p");
for (const paragraph of paragraphs) {
  paragraph.addEventListener("click", insertBreakAtPoint);
}

// Click event handler <p> elements in the Shadow DOM
const shadowParagraphs = host.shadowRoot.querySelectorAll("p");
for (const paragraph of shadowParagraphs) {
  console.log(paragraph);
  paragraph.addEventListener("click", insertBreakAtPoint);
}
```

```js hidden
// Inserts ^ at offset and gets a substring for log
function getSubstringAroundOffset(text, offset, length = 10) {
  const start = Math.max(0, offset - length);
  const end = Math.min(text.length, offset + length + 1);
  // Insert the caret character at the offset
  const modifiedText = `${text.substring(0, offset)}^${text.substring(offset)}`;
  return `...${modifiedText.substring(start, end)}...`;
}
```

```js hidden
let message = document.getElementById("message");
if (document.caretPositionFromPoint) {
  message.textContent =
    "This browser supports the standard document.caretPositionFromPoint";
  message.classList.add("supported");
} else if (document.caretRangeFromPoint) {
  message.textContent =
    "This browser supports the non-standard document.caretRangeFromPoint";
  message.classList.add("supported");
}
```

#### نتایج

در پاراگراف **Lorem ipsum ...** قبل یا بعد از متن Shadow DOM کلیک کنید تا در نقطه‌ای که کلیک می‌کنید یک شکست خط درج شود. توجه کنید که در این حالت، گزارش به شما نشان می‌دهد که یک `TEXT_NODE` انتخاب کرده‌اید، همچنین افست و بخشی از گره انتخاب‌شده با کاراکتر `^` در محل افست.

در ابتدا ریشه سایه به `caretPositionFromPoint()` ارسال نمی‌شود، بنابراین اگر روی متن «I'm in the shadow DOM» کلیک کنید، گره موقعیت مکان‌نمای بازگشتی، گره والد میزبان، در افست ریشه سایه خواهد بود. بنابراین شکست خط قبل از گره اضافه می‌شود، نه در نقطه‌ای که انتخاب کرده‌اید. توجه داشته باشید که در این حالت گره موقعیت مکان‌نما دارای نوع `ELEMENT_NODE` است.

اگر روی دکمه «Add shadow» کلیک کنید، ریشه سایه به `caretPositionFromPoint()` ارسال می‌شود، بنابراین موقعیت مکان‌نمای بازگشتی، گره انتخاب‌شده‌ی خاص درون Shadow DOM است. این کار باعث می‌شود متن Shadow DOM مانند سایر متن‌های پاراگراف رفتار کند.

{{EmbedLiveSample('Split text nodes at caret positions in a Shadow DOM','100%','400px')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref('CaretPosition')}}