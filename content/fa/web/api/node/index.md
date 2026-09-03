---
title: Node
slug: Web/API/Node
page-type: web-api-interface
browser-compat: api.Node
---

{{APIRef("DOM")}}

رابط {{Glossary("DOM")}} **`Node`** یک کلاس پایه انتزاعی است که بسیاری از اشیای API دیگر DOM بر اساس آن ساخته شده‌اند، بنابراین به این نوع اشیا اجازه می‌دهد به طور مشابه و اغلب به جای یکدیگر استفاده شوند. به عنوان یک کلاس انتزاعی، چیزی به عنوان یک شی `Node` ساده وجود ندارد. تمام اشیایی که عملکرد `Node` را پیاده‌سازی می‌کنند بر اساس یکی از زیرکلاس‌های آن هستند. قابل توجه‌ترین آنها {{domxref("Document")}}، {{domxref("Element")}} و {{domxref("DocumentFragment")}} هستند.

علاوه بر این، هر نوع گره DOM توسط یک رابط مبتنی بر `Node` نمایش داده می‌شود. این‌ها شامل {{DOMxRef("Attr")}}، {{DOMxRef("CharacterData")}} (که {{DOMxRef("Text")}}، {{DOMxRef("Comment")}}، {{DOMxRef("CDATASection")}} و {{DOMxRef("ProcessingInstruction")}} همگی بر اساس آن هستند) و {{DOMxRef("DocumentType")}} می‌شوند.

در برخی موارد، ممکن است یک ویژگی خاص از رابط پایه `Node` برای یکی از رابط‌های فرزند آن اعمال نشود؛ در آن صورت، گره ارث‌برنده ممکن است بسته به شرایط `null` برگرداند یا یک استثنا پرتاب کند. به عنوان مثال، تلاش برای افزودن فرزندان به نوع گرهی که نمی‌تواند فرزند داشته باشد، یک استثنا پرتاب می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_علاوه بر ویژگی‌های زیر، `Node` ویژگی‌هایی را از والد خود، {{DOMxRef("EventTarget")}}، به ارث می‌برد._

- {{DOMxRef("Node.baseURI")}} {{ReadOnlyInline}}
  - : یک رشته (string) را برمی‌گرداند که نشان‌دهنده URL پایه سند حاوی این `Node` است.
- {{DOMxRef("Node.childNodes")}} {{ReadOnlyInline}}
  - : یک {{DOMxRef("NodeList")}} زنده شامل تمام فرزندان این گره (اعم از عناصر، متن و نظرات) را برمی‌گرداند. زنده بودن {{DOMxRef("NodeList")}} به این معنی است که اگر فرزندان `Node` تغییر کنند، شی {{DOMxRef("NodeList")}} به طور خودکار به‌روز می‌شود.
- {{DOMxRef("Node.firstChild")}} {{ReadOnlyInline}}
  - : یک `Node` را برمی‌گرداند که نشان‌دهنده اولین گره فرزند مستقیم گره است، یا اگر گره فرزندی نداشته باشد `null` را برمی‌گرداند.
- {{DOMxRef("Node.isConnected")}} {{ReadOnlyInline}}
  - : یک مقدار بولی که نشان می‌دهد آیا Node به شی زمینه متصل است (به طور مستقیم یا غیرمستقیم) یا خیر، به عنوان مثال، شی {{DOMxRef("Document")}} در مورد DOM عادی، یا {{DOMxRef("ShadowRoot")}} در مورد DOM سایه.
- {{DOMxRef("Node.lastChild")}} {{ReadOnlyInline}}
  - : یک `Node` را برمی‌گرداند که نشان‌دهنده آخرین گره فرزند مستقیم گره است، یا اگر گره فرزندی نداشته باشد `null` را برمی‌گرداند.
- {{DOMxRef("Node.nextSibling")}} {{ReadOnlyInline}}
  - : یک `Node` را برمی‌گرداند که نشان‌دهنده گره بعدی در درخت است، یا اگر چنین گره‌ای وجود نداشته باشد `null` را برمی‌گرداند.
- {{DOMxRef("Node.nodeName")}} {{ReadOnlyInline}}
  - : یک رشته حاوی نام `Node` را برمی‌گرداند. ساختار نام با نوع گره متفاوت خواهد بود. به عنوان مثال، یک {{DOMxRef("HTMLElement")}} حاوی نام تگ مربوطه خواهد بود، مانند `'AUDIO'` برای یک {{DOMxRef("HTMLAudioElement")}}، یک گره {{DOMxRef("Text")}} رشته `'#text'` را خواهد داشت، یا یک گره {{DOMxRef("Document")}} رشته `'#document'` را خواهد داشت.
- {{DOMxRef("Node.nodeType")}} {{ReadOnlyInline}}
  - : یک `unsigned short` را برمی‌گرداند که نشان‌دهنده نوع گره است. مقادیر ممکن:

    | نام                          | مقدار |
    | ----------------------------- | ----- |
    | `ELEMENT_NODE`                | `1`   |
    | `ATTRIBUTE_NODE`              | `2`   |
    | `TEXT_NODE`                   | `3`   |
    | `CDATA_SECTION_NODE`          | `4`   |
    | `PROCESSING_INSTRUCTION_NODE` | `7`   |
    | `COMMENT_NODE`                | `8`   |
    | `DOCUMENT_NODE`               | `9`   |
    | `DOCUMENT_TYPE_NODE`          | `10`  |
    | `DOCUMENT_FRAGMENT_NODE`      | `11`  |

- {{DOMxRef("Node.nodeValue")}}
  - : مقدار گره فعلی را برمی‌گرداند/تنظیم می‌کند.
- {{DOMxRef("Node.ownerDocument")}} {{ReadOnlyInline}}
  - : {{DOMxRef("Document")}}ای که این گره به آن تعلق دارد را برمی‌گرداند. اگر خود گره یک سند باشد، `null` را برمی‌گرداند.
- {{DOMxRef("Node.parentNode")}} {{ReadOnlyInline}}
  - : یک `Node` که والد این گره است را برمی‌گرداند. اگر چنین گره‌ای وجود نداشته باشد — برای مثال، اگر این گره رأس درخت باشد، یا در درختی شرکت نداشته باشد — این ویژگی `null` را برمی‌گرداند.
- {{DOMxRef("Node.parentElement")}} {{ReadOnlyInline}}
  - : یک {{DOMxRef("Element")}} که والد این گره است را برمی‌گرداند. اگر گره والد نداشته باشد، یا اگر آن والد یک {{DOMxRef("Element")}} نباشد، این ویژگی `null` را برمی‌گرداند.
- {{DOMxRef("Node.previousSibling")}} {{ReadOnlyInline}}
  - : یک `Node` را برمی‌گرداند که نشان‌دهنده گره قبلی در درخت است، یا اگر چنین گره‌ای وجود نداشته باشد `null` را برمی‌گرداند.
- {{DOMxRef("Node.textContent")}}
  - : محتوای متنی یک عنصر و تمام نوادگان آن را برمی‌گرداند/تنظیم می‌کند.

## روش‌های نمونه

_علاوه بر روش‌های زیر، `Node` روش‌هایی را از والد خود، {{DOMxRef("EventTarget")}}، به ارث می‌برد._

- {{DOMxRef("Node.appendChild()")}}
  - : آرگومان `childNode` مشخص شده را به عنوان آخرین فرزند به گره فعلی اضافه می‌کند. اگر آرگومان به یک گره موجود در درخت DOM اشاره کند، آن گره از موقعیت فعلی خود جدا شده و در موقعیت جدید قرار می‌گیرد.
- {{DOMxRef("Node.cloneNode()")}}
  - : یک `Node` و به صورت اختیاری، تمام محتویات آن را کلون می‌کند. به طور پیش‌فرض، محتوای گره را کلون می‌کند.
- {{DOMxRef("Node.compareDocumentPosition()")}}
  - : موقعیت گره فعلی را نسبت به گره دیگری در هر سند دیگری مقایسه می‌کند.
- {{DOMxRef("Node.contains()")}}
  - : یک مقدار `true` یا `false` را برمی‌گرداند که نشان می‌دهد آیا یک گره از نوادگان گره فراخواننده است یا خیر.
- {{DOMxRef("Node.getRootNode()")}}
  - : ریشه شی زمینه را برمی‌گرداند که به صورت اختیاری شامل ریشه سایه (shadow root) نیز می‌شود.
- {{DOMxRef("Node.hasChildNodes()")}}
  - : یک مقدار بولی را برمی‌گرداند که نشان می‌دهد آیا عنصر دارای هیچ گره فرزندی است یا خیر.
- {{DOMxRef("Node.insertBefore()")}}
  - : یک `Node` را قبل از گره مرجع به عنوان فرزندی از یک گره والد مشخص شده درج می‌کند.
- {{DOMxRef("Node.isDefaultNamespace()")}}
  - : یک URI namespace را به عنوان آرگومان می‌پذیرد و یک مقدار بولی برمی‌گرداند که اگر namespace، namespace پیش‌فرض در گره داده شده باشد `true` و در غیر این صورت `false` است.
- {{DOMxRef("Node.isEqualNode()")}}
  - : یک مقدار بولی را برمی‌گرداند که نشان می‌دهد آیا دو گره از یک نوع هستند و تمام نقاط داده تعریف‌کننده آنها مطابقت دارد یا خیر.
- {{DOMxRef("Node.isSameNode()")}}
  - : یک مقدار بولی را برمی‌گرداند که نشان می‌دهد آیا دو گره یکسان هستند (یعنی به یک شی اشاره می‌کنند) یا خیر.
- {{DOMxRef("Node.lookupPrefix()")}}
  - : یک رشته حاوی پیشوند (prefix) برای یک URI namespace داده شده را برمی‌گرداند، در صورت وجود، و در غیر این صورت `null` را برمی‌گرداند. هنگامی که چندین پیشوند ممکن است، نتیجه به پیاده‌سازی بستگی دارد.
- {{DOMxRef("Node.lookupNamespaceURI()")}}
  - : یک پیشوند را می‌پذیرد و URI namespace مرتبط با آن را در گره داده شده در صورت یافتن برمی‌گرداند (و در غیر این صورت `null`). ارائه `null` برای پیشوند، namespace پیش‌فرض را برمی‌گرداند.
- {{DOMxRef("Node.normalize()")}}
  - : تمام گره‌های متنی زیر این عنصر را تمیز می‌کند (مجاورها را ادغام کرده، خالی‌ها را حذف می‌کند).
- {{DOMxRef("Node.removeChild()")}}
  - : یک گره فرزند را از عنصر فعلی حذف می‌کند که باید فرزند گره فعلی باشد.
- {{DOMxRef("Node.replaceChild()")}}
  - : یک گره فرزند `Node` از گره فعلی را با دومی که در پارامتر داده شده جایگزین می‌کند.

## رویدادها

- {{domxref("Node/selectstart_event", "selectstart")}}
  - : هنگامی که کاربر یک انتخاب جدید را در این گره شروع می‌کند، فعال می‌شود.

## مثال‌ها

### حذف همه فرزندان تو در تو درون یک گره

این تابع هر فرزند اول یک عنصر را تا زمانی که هیچ‌کدام باقی نمانده است حذف می‌کند.

```js
function removeAllChildren(element) {
  while (element.firstChild) {
    element.removeChild(element.firstChild);
  }
}
```

استفاده از این تابع یک فراخوانی واحد است. در اینجا بدنه سند را خالی می‌کنیم:

```js
removeAllChildren(document.body);
```

یک جایگزین می‌تواند تنظیم `textContent` به رشته خالی باشد: `document.body.textContent = ""`.

### پیمایش بازگشتی در گره‌های فرزند

تابع زیر به صورت بازگشتی یک تابع callback را برای هر گره موجود در یک گره ریشه (از جمله خود ریشه) فراخوانی می‌کند:

```js
function eachNode(rootNode, callback) {
  if (!callback) {
    const nodes = [];
    eachNode(rootNode, (node) => {
      nodes.push(node);
    });
    return nodes;
  }

  if (callback(rootNode) === false) {
    return false;
  }

  if (rootNode.hasChildNodes()) {
    for (const node of rootNode.childNodes) {
      if (eachNode(node, callback) === false) {
        return;
      }
    }
  }
}
```

این تابع به صورت بازگشتی یک تابع را برای هر گره از نوادگان `rootNode` (از جمله خود ریشه) فراخوانی می‌کند.

اگر `callback` حذف شود، تابع به جای آن یک {{jsxref("Array")}} شامل `rootNode` و تمام گره‌های موجود درون آن برمی‌گرداند.

اگر `callback` ارائه شود و در هنگام فراخوانی `false` برگرداند، سطح بازگشت فعلی لغو می‌شود و تابع اجرا را از آخرین سطح والد از سر می‌گیرد. این می‌تواند برای لغو حلقه‌ها پس از یافتن یک گره استفاده شود (مانند جستجوی یک گره متنی که حاوی یک رشته خاص است).

تابع دو پارامتر دارد:

- `rootNode`
  - : شی `Node`ای که نوادگان آن پیمایش خواهند شد.
- `callback` {{optional_inline}}
  - : یک تابع callback اختیاری که یک `Node` را به عنوان تنها آرگومان خود دریافت می‌کند. اگر حذف شود، `eachNode` یک {{jsxref("Array")}} از تمام گره‌های موجود درون `rootNode` (از جمله خود ریشه) برمی‌گرداند.

مثال زیر یک استفاده واقعی از تابع `eachNode()` را نشان می‌دهد: جستجوی متن در یک صفحه وب.

ما از یک تابع wrapper به نام `grep` برای انجام جستجو استفاده می‌کنیم:

```js
function grep(parentNode, pattern) {
  let matches = [];
  let endScan = false;

  eachNode(parentNode, (node) => {
    if (endScan) {
      return false;
    }

    // Ignore anything which isn't a text node
    if (node.nodeType !== Node.TEXT_NODE) {
      return;
    }

    if (typeof pattern === "string" && node.textContent.includes(pattern)) {
      matches.push(node);
    } else if (pattern.test(node.textContent)) {
      if (!pattern.global) {
        endScan = true;
        matches = node;
      } else {
        matches.push(node);
      }
    }
  });

  return matches;
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}