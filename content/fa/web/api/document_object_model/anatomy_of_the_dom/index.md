---
title: "کالبدشکافی DOM"
slug: Web/API/Document_Object_Model/Anatomy_of_the_DOM
page-type: guide
---

{{DefaultAPISidebar("DOM")}}

DOM یک سند XML یا HTML را به صورت یک درخت نمایش می‌دهد. این صفحه ساختار پایهٔ درخت DOM و ویژگی‌ها و روش‌های مختلفی را که برای پیمایش آن استفاده می‌شوند، معرفی می‌کند.

برای شروع، باید چند مفهوم مرتبط با درخت‌ها را معرفی کنیم. درخت یک ساختار داده است که از _گره‌ها_ تشکیل شده است. هر گره حاوی مقداری _داده_ است. گره‌ها به صورت سلسله‌مراتبی سازماندهی می‌شوند – هر گره یک _گره والد_ دارد (به جز گره ریشه که والد ندارد) و یک لیست مرتب از صفر یا چند _گره فرزند_. اکنون می‌توانیم موارد زیر را تعریف کنیم:

- گره‌ای که والد ندارد، _ریشه_ درخت نامیده می‌شود.
- گره‌ای که فرزندی ندارد، _برگ_ نامیده می‌شود.
- گره‌هایی که والد یکسانی دارند، _خواهر و برادر_ نامیده می‌شوند. خواهر و برادرها به لیست فرزندان یکسان والد خود تعلق دارند، بنابراین ترتیب مشخصی دارند.
- اگر بتوانیم از گره A به گره B با دنبال کردن مکرر پیوندهای والد برویم، آن‌گاه A _نواده_ B و B _جد_ A است.
- گره‌های یک درخت به _ترتیب درخت_ فهرست می‌شوند، به این صورت که ابتدا خود گره و سپس به صورت بازگشتی هر یک از گره‌های فرزند آن به ترتیب (پیمایش پیش‌ترتیب، عمق‌اول) فهرست می‌شوند.

و در اینجا چند ویژگی مهم درخت‌ها آورده شده است:

- هر گره با یک گره ریشهٔ یکتا مرتبط است.
- اگر گره A والد گره B باشد، آن‌گاه گره B فرزند گره A است.
- چرخه مجاز نیست: هیچ گره‌ای نمی‌تواند جد یا نوادهٔ خودش باشد.

## واسط Node و زیرکلاس‌های آن

تمام گره‌های DOM توسط اشیایی نمایش داده می‌شوند که واسط {{domxref("Node")}} را پیاده‌سازی می‌کنند. واسط `Node` بسیاری از مفاهیم تعریف‌شدهٔ پیشین را در خود جای داده است:

- ویژگی {{domxref("Node/parentNode", "parentNode")}} گره والد را برمی‌گرداند، یا اگر گره والد نداشته باشد `null` را برمی‌گرداند.
- ویژگی {{domxref("Node/childNodes", "childNodes")}} یک {{domxref("NodeList")}} از گره‌های فرزند را برمی‌گرداند. ویژگی‌های {{domxref("Node/firstChild", "firstChild")}} و {{domxref("Node/lastChild", "lastChild")}} به ترتیب اولین و آخرین عنصر این لیست را برمی‌گردانند، یا اگر فرزندی وجود نداشته باشد `null` را برمی‌گردانند.
- متد {{domxref("Node/getRootNode", "getRootNode()")}} ریشهٔ درختی که گره در آن قرار دارد را با دنبال کردن مکرر پیوندهای والد برمی‌گرداند.
- متد {{domxref("Node/hasChildNodes", "hasChildNodes()")}} اگر گره دارای هر گره فرزندی باشد (یعنی برگ نباشد)، `true` برمی‌گرداند.
- ویژگی‌های {{domxref("Node/previousSibling", "previousSibling")}} و {{domxref("Node/nextSibling", "nextSibling")}} به ترتیب گره خواهر و برادر قبلی و بعدی را برمی‌گردانند، یا اگر چنین خواهر و برادری وجود نداشته باشد `null` را برمی‌گردانند.
- متد {{domxref("Node/contains", "contains()")}} اگر یک گرهٔ مشخص نوادهٔ گره باشد، `true` برمی‌گرداند.
- متد {{domxref("Node/compareDocumentPosition", "compareDocumentPosition()")}} دو گره را بر اساس ترتیب درخت مقایسه می‌کند. بخش [مقایسهٔ گره‌ها](#مقایسه-گره‌ها) این متد را با جزئیات بیشتری توضیح می‌دهد.

به ندرت با اشیاء `Node` ساده کار می‌کنید – در عوض، تمام اشیاء در DOM یکی از واسط‌هایی را پیاده‌سازی می‌کنند که از `Node` ارث‌بری می‌کنند، که معناشناسی‌های اضافی در سند را نشان می‌دهند. انواع گره محدود می‌کنند که چه داده‌ای می‌توانند داشته باشند و چه نوع فرزندانی مجاز هستند. در نظر بگیرید که سند HTML زیر چگونه در DOM نمایش داده می‌شود:

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <h1>Hello, world!</h1>
    <p>This is a paragraph.</p>
  </body>
</html>
```

درخت DOM زیر را تولید می‌کند:

![درخت DOM سند HTML قبلی](/shared-assets/images/diagrams/api/dom/tree-structure.svg)

ریشهٔ این درخت DOM یک گره {{domxref("Document")}} است که کل سند را نشان می‌دهد. این گره به صورت سراسری به عنوان متغیر {{domxref("Window/document", "document")}} در دسترس است. این گره دو گره فرزند مهم دارد:

- یک گره اختیاری {{domxref("DocumentType")}} که اعلان {{glossary("doctype")}} را نشان می‌دهد. در مورد ما، یکی وجود دارد. این گره همچنین از طریق ویژگی {{domxref("Document/doctype", "doctype")}} گره `Document` قابل دسترسی است.
- یک گره اختیاری {{domxref("Element")}} که عنصر ریشه را نشان می‌دهد. برای اسناد HTML (مانند مورد ما)، این معمولاً {{domxref("HTMLHtmlElement")}} است. برای اسناد SVG، این معمولاً {{domxref("SVGSVGElement")}} است. این گره همچنین از طریق ویژگی {{domxref("Document/documentElement", "documentElement")}} گره `Document` قابل دسترسی است.

گره `DocumentType` همیشه یک گره برگ است. گره `Element` جایی است که بیشتر محتوای سند در آن نمایش داده می‌شود. هر عنصر زیر آن، مانند {{htmlelement("head")}}، {{htmlelement("body")}}، و {{htmlelement("p")}}، نیز توسط یک گره `Element` نمایش داده می‌شود. در واقع، هر کدام یک زیرکلاس از `Element` خاص برای آن نام تگ هستند که در مشخصات HTML تعریف شده‌اند، مانند {{domxref("HTMLHeadElement")}} و {{domxref("HTMLBodyElement")}}، با ویژگی‌ها و روش‌های اضافی برای نمایش معناشناسی آن عنصر، اما در اینجا روی رفتارهای مشترک DOM تمرکز می‌کنیم. گره‌های `Element` می‌توانند گره‌های `Element` دیگر را به عنوان فرزند داشته باشند که عناصر تو در تو را نشان می‌دهند. برای مثال، عنصر {{htmlelement("head")}} سه فرزند دارد: دو عنصر {{htmlelement("meta")}} و یک عنصر {{htmlelement("title")}}. علاوه بر این، عناصر می‌توانند گره‌های {{domxref("Text")}} و {{domxref("CDATASection")}} را نیز به عنوان فرزند داشته باشند که محتوای متنی را نشان می‌دهند. برای مثال، عنصر {{htmlelement("p")}} یک فرزند دارد، یک گره `Text` حاوی رشته "This is a paragraph.". گره‌های `Text` و `CDATASection` همیشه گره‌های برگ هستند.

تمام گره‌هایی که می‌توانند فرزند داشته باشند ({{domxref("Document")}}، {{domxref("DocumentFragment")}}، و {{domxref("Element")}}) دو نوع فرزند را مجاز می‌دانند: گره‌های {{domxref("Comment")}} و {{domxref("ProcessingInstruction")}}. این گره‌ها همیشه گره‌های برگ هستند.

هر عنصر، علاوه بر داشتن گره‌های فرزند، می‌تواند ویژگی‌هایی نیز داشته باشد که به صورت گره‌های {{domxref("Attr")}} نمایش داده می‌شوند. `Attr` از واسط `Node` ارث‌بری می‌کند، اما بخشی از ساختار درخت اصلی نیستند، زیرا فرزند هیچ گره‌ای نیستند و گره والد آنها `null` است. در عوض، آنها در یک نقشه گره نام‌گذاری شدهٔ جداگانه ذخیره می‌شوند که از طریق ویژگی {{domxref("Element/attributes", "attributes")}} گره `Element` قابل دسترسی است.

واسط `Node` یک ویژگی {{domxref("Node/nodeType", "nodeType")}} تعریف می‌کند که نوع گره را نشان می‌دهد. به طور خلاصه، انواع گره زیر را معرفی کردیم:

| نوع گره                            | مقدار `nodeType`                       | فرزندان معتبر (به غیر از `Comment` و `ProcessingInstruction`)          |
| ----------------------------------- | -------------------------------------- | ---------------------------------------------------------------------- |
| {{domxref("Document")}}             | `Node.DOCUMENT_NODE` (9)               | {{domxref("DocumentType")}}، {{domxref("Element")}}                     |
| {{domxref("DocumentType")}}         | `Node.DOCUMENT_TYPE_NODE` (10)         | هیچکدام                                                                |
| {{domxref("Element")}}              | `Node.ELEMENT_NODE` (1)                | {{domxref("Element")}}، {{domxref("Text")}}، {{domxref("CDATASection")}}|
| {{domxref("Text")}}                 | `Node.TEXT_NODE` (3)                   | هیچکدام                                                                |
| {{domxref("CDATASection")}}         | `Node.CDATA_SECTION_NODE` (4)          | هیچکدام                                                                |
| {{domxref("Comment")}}              | `Node.COMMENT_NODE` (8)                | هیچکدام                                                                |
| {{domxref("ProcessingInstruction")}}| `Node.PROCESSING_INSTRUCTION_NODE` (7) | هیچکدام                                                                |
| {{domxref("Attr")}}                 | `Node.ATTRIBUTE_NODE` (2)              | هیچکدام                                                                |

> [!NOTE]
> ممکن است متوجه شده باشید که برخی انواع گره را در اینجا حذف کرده‌ایم. مقادیر `Node.ENTITY_REFERENCE_NODE` (5)، `Node.ENTITY_NODE` (6) و `Node.NOTATION_NODE` (12) دیگر استفاده نمی‌شوند، در حالی که مقدار `Node.DOCUMENT_FRAGMENT_NODE` (11) در [ساخت و به‌روزرسانی درخت DOM](/en-US/docs/Web/API/Document_Object_Model/Building_and_updating_the_DOM_tree) معرفی خواهد شد.

## داده‌های هر گره

هر نوع گره روش مخصوص خود را برای نمایش داده‌هایی که نگه می‌دارد دارد. واسط `Node` خود سه ویژگی مرتبط با داده تعریف می‌کند که در جدول زیر خلاصه شده‌اند:

| نوع گره                            | {{domxref("Node/nodeName", "nodeName")}}             | {{domxref("Node/nodeValue", "nodeValue")}} | {{domxref("Node/textContent", "textContent")}}               |
| ----------------------------------- | ---------------------------------------------------- | ------------------------------------------ | ------------------------------------------------------------ |
| {{domxref("Document")}}             | `"#document"`                                        | `null`                                     | `null`                                                       |
| {{domxref("DocumentType")}}         | [`name`](#documenttype) آن (مثلاً `"html"`)          | `null`                                     | `null`                                                       |
| {{domxref("Element")}}              | [`tagName`](#element) آن (مثلاً `"HTML"`، `"BODY"`)  | `null`                                     | الحاق همه نوادگان گره متنی آن به ترتیب درخت                   |
| {{domxref("Text")}}                 | `"#text"`                                            | [`data`](#characterdata) آن                 | [`data`](#characterdata) آن                                  |
| {{domxref("CDATASection")}}         | `"#cdata-section"`                                   | [`data`](#characterdata) آن                 | [`data`](#characterdata) آن                                  |
| {{domxref("Comment")}}              | `"#comment"`                                         | [`data`](#characterdata) آن                 | [`data`](#characterdata) آن                                  |
| {{domxref("ProcessingInstruction")}}| [`target`](#characterdata) آن                        | [`data`](#characterdata) آن                 | [`data`](#characterdata) آن                                  |
| {{domxref("Attr")}}                 | [`name`](#attr) آن                                   | [`value`](#attr) آن                         | [`value`](#attr) آن                                          |

### Document

گره `Document` خود هیچ داده‌ای نگه نمی‌دارد، بنابراین `nodeValue` و `textContent` آن همیشه `null` هستند. `nodeName` آن همیشه `"#document"` است.

`Document` برخی فراداده‌ها را در مورد سند تعریف می‌کند که از محیط می‌آیند (برای مثال، پاسخ HTTP که سند را ارائه کرده است):

- ویژگی‌های {{domxref("Document/URL", "URL")}} و {{domxref("Document/documentURI", "documentURI")}} URL سند را برمی‌گردانند.
- ویژگی {{domxref("Document/characterSet", "characterSet")}} رمزگذاری کاراکتر مورد استفاده توسط سند را برمی‌گرداند، مانند `"UTF-8"`.
- ویژگی {{domxref("Document/compatMode", "compatMode")}} حالت رندرینگ سند را برمی‌گرداند، یا `"CSS1Compat"` (حالت استاندارد) یا `"BackCompat"` (حالت quirks).
- ویژگی {{domxref("Document/contentType", "contentType")}} [نوع رسانه](/en-US/docs/Web/HTTP/Guides/MIME_types) سند را برمی‌گرداند، مانند `"text/html"` برای اسناد HTML.

### DocumentType

یک `DocumentType` در سند به این شکل است:

```xml
<!doctype name PUBLIC "publicId" "systemId">
```

سه بخش وجود دارد که می‌توانید مشخص کنید، که با سه ویژگی گره `DocumentType` مطابقت دارد: {{domxref("DocumentType/name", "name")}}، {{domxref("DocumentType/publicId", "publicId")}}، و {{domxref("DocumentType/systemId", "systemId")}}. برای اسناد HTML، doctype همیشه `<!doctype html>` است، بنابراین `name` برابر `"html"` و هر دو `publicId` و `systemId` رشته‌های خالی هستند.

### Element

یک `Element` در سند به این شکل است:

```html
<p class="note" id="intro">This is a paragraph.</p>
```

علاوه بر محتوا، دو بخش وجود دارد که می‌توانید مشخص کنید: نام تگ و ویژگی‌ها. نام تگ با ویژگی {{domxref("Element/tagName", "tagName")}} گره `Element` مطابقت دارد که در این مورد `"P"` است (توجه کنید که برای عناصر HTML همیشه با حروف بزرگ است). ویژگی‌ها با گره‌های `Attr` ذخیره شده در ویژگی {{domxref("Element/attributes", "attributes")}} گره `Element` مطابقت دارند. ویژگی‌ها را در بخش [Element و ویژگی‌های آن](#element-و-ویژگی-های-آن) با جزئیات بیشتری بررسی خواهیم کرد.

گره `Element` خود هیچ داده‌ای نگه نمی‌دارد، بنابراین `nodeValue` آن همیشه `null` است. `textContent` آن الحاق همه نوادگان گره متنی آن به ترتیب درخت است که در این مورد `"This is a paragraph."` است. برای عنصر زیر:

```html
<div>Hello, <span>world</span>!</div>
```

`textContent` برابر `"Hello, world!"` است، که گره متنی `"Hello, "`، گره متنی `"world"` داخل عنصر {{htmlelement("span")}}، و گره متنی `"!"` را به هم می‌چسباند.

### CharacterData

{{domxref("Text")}}، {{domxref("CDATASection")}}، {{domxref("Comment")}}، و {{domxref("ProcessingInstruction")}} همگی از واسط {{domxref("CharacterData")}} ارث‌بری می‌کنند که زیرکلاس `Node` است. واسط `CharacterData` یک ویژگی به نام {{domxref("CharacterData/data", "data")}} تعریف می‌کند که محتوای متنی گره را نگه می‌دارد. ویژگی `data` همچنین برای پیاده‌سازی ویژگی‌های `nodeValue` و `textContent` این گره‌ها استفاده می‌شود.

برای `Text` و `CDATASection`، ویژگی `data` محتوای متنی گره را نگه می‌دارد. در سند زیر (توجه کنید که از یک سند SVG استفاده می‌کنیم، زیرا HTML بخش‌های CDATA را مجاز نمی‌داند):

```svg
<text>Some text</text>
<style><![CDATA[h1 { color: red; }]]></style>
```

گره متنی داخل عنصر {{svgelement("text")}} دارای `"Some text"` به عنوان `data` است، و بخش CDATA داخل عنصر {{svgelement("style")}} دارای `"h1 { color: red; }"` به عنوان `data` است.

برای `Comment`، ویژگی `data` محتوای نظر را نگه می‌دارد، که از بعد از `<!--` شروع می‌شود و قبل از `-->` خاتمه می‌یابد. برای مثال، در سند زیر:

```html
<!-- This is a comment -->
```

گره نظر دارای `" This is a comment "` به عنوان `data` است.

برای `ProcessingInstruction`، ویژگی `data` محتوای دستورالعمل پردازش را نگه می‌دارد، که از بعد از هدف شروع می‌شود و قبل از `?>` خاتمه می‌یابد. برای مثال، در سند زیر:

```xml
<?xml-stylesheet type="text/xsl" href="style.xsl"?>
```

گره دستورالعمل پردازش دارای `'type="text/xsl" href="style.xsl"'` به عنوان `data` و `"xml-stylesheet"` به عنوان {{domxref("ProcessingInstruction/target", "target")}} خود است.

علاوه بر این، واسط `CharacterData` ویژگی {{domxref("CharacterData/length", "length")}} را تعریف می‌کند که طول رشته `data` را برمی‌گرداند، و متد {{domxref("CharacterData/substringData", "substringData()")}} که یک زیررشته از `data` را برمی‌گرداند.

### Attr

برای عنصر زیر:

```html
<p class="note" id="intro">This is a paragraph.</p>
```

عنصر `<p>` دو ویژگی دارد که توسط دو گره `Attr` نمایش داده می‌شوند. هر ویژگی از یک نام و یک مقدار تشکیل شده است که با ویژگی‌های {{domxref("Attr/name", "name")}} و {{domxref("Attr/value", "value")}} مطابقت دارد. ویژگی اول دارای `"class"` به عنوان `name` و `"note"` به عنوان `value` است، در حالی که ویژگی دوم دارای `"id"` به عنوان `name` و `"intro"` به عنوان `value` است.

## Element و ویژگی‌های آن

همانطور که قبلاً ذکر شد، ویژگی‌های یک گره `Element` توسط گره‌های `Attr` نمایش داده می‌شوند که در یک نقشه گره نام‌گذاری شدهٔ جداگانه ذخیره می‌شوند و از طریق ویژگی {{domxref("Element/attributes", "attributes")}} گره `Element` قابل دسترسی هستند. این واسط {{domxref("NamedNodeMap")}} سه ویژگی مهم را تعریف می‌کند:

- {{domxref("NamedNodeMap/length", "length")}} که تعداد ویژگی‌ها را برمی‌گرداند.
- متد {{domxref("NamedNodeMap/item", "item()")}} که `Attr` را در یک ایندکس مشخص برمی‌گرداند.
- متد {{domxref("NamedNodeMap/getNamedItem", "getNamedItem()")}} که `Attr` را با یک نام مشخص برمی‌گرداند.

واسط `Element` همچنین چندین متد برای کار مستقیم با ویژگی‌ها تعریف می‌کند، بدون نیاز به دسترسی به نقشه گره نام‌گذاری شده:

- {{domxref("Element/getAttribute", "element.getAttribute(name)")}} معادل `element.attributes.getNamedItem(name).value` است، اگر ویژگی وجود داشته باشد.
- {{domxref("Element/getAttributeNode", "element.getAttributeNode(name)")}} معادل `element.attributes.getNamedItem(name)` است.
- {{domxref("Element/hasAttribute", "element.hasAttribute(name)")}} معادل `element.attributes.getNamedItem(name) !== null` است.
- {{domxref("Element/getAttributeNames", "element.getAttributeNames()")}} یک آرایه از همه نام ویژگی‌ها را برمی‌گرداند.
- {{domxref("Element/hasAttributes", "element.hasAttributes()")}} معادل `element.attributes.length > 0` است.

همچنین می‌توانید از طریق ویژگی {{domxref("Attr/ownerElement", "ownerElement")}} گره `Attr` به عنصر مالک یک ویژگی دسترسی پیدا کنید.

دو ویژگی خاص به نام‌های `id` و `class` وجود دارند که ویژگی‌های مخصوص به خود را روی واسط `Element` دارند: {{domxref("Element/id", "id")}} و {{domxref("Element/className", "className")}} که [منعکس‌کننده](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes) مقدار ویژگی مربوطه هستند. علاوه بر این، ویژگی {{domxref("Element/classList", "classList")}} یک {{domxref("DOMTokenList")}} را برمی‌گرداند که لیست کلاس‌های موجود در ویژگی `class` را نشان می‌دهد.

## کار با درخت عنصر

از آنجایی که گره‌های `Element` ستون فقرات ساختار سند را تشکیل می‌دهند، می‌توانید به طور خاص گره‌های عنصر را پیمایش کنید و از سایر گره‌ها (مانند `Text` و `Comment`) صرف‌نظر کنید.

- برای همه گره‌ها، ویژگی {{domxref("Node/parentElement", "parentElement")}} گره والد را در صورتی که یک `Element` باشد برمی‌گرداند، یا اگر والد یک `Element` نباشد (مثلاً اگر والد یک `Document` باشد) `null` را برمی‌گرداند. این در تضاد با {{domxref("Node/parentNode", "parentNode")}} است که صرف‌نظر از نوع، گره والد را برمی‌گرداند.
- برای `Document`، `DocumentFragment`، و `Element`، ویژگی {{domxref("Element/children", "children")}} یک {{domxref("HTMLCollection")}} از فقط گره‌های فرزند `Element` را برمی‌گرداند. این در تضاد با {{domxref("Node/childNodes", "childNodes")}} است که همه گره‌های فرزند را برمی‌گرداند. ویژگی‌های {{domxref("Element/firstElementChild", "firstElementChild")}} و {{domxref("Element/lastElementChild", "lastElementChild")}} به ترتیب اولین و آخرین عنصر این مجموعه را برمی‌گردانند، یا اگر هیچ عنصر فرزندی وجود نداشته باشد `null` را برمی‌گردانند. ویژگی {{domxref("Element/childElementCount", "childElementCount")}} تعداد عناصر فرزند را برمی‌گرداند.
- برای `Element` و `CharacterData`، ویژگی‌های {{domxref("Element/previousElementSibling", "previousElementSibling")}} و {{domxref("Element/nextElementSibling", "nextElementSibling")}} به ترتیب گره خواهر و برادر قبلی و بعدی که یک `Element` است را برمی‌گردانند، یا اگر چنین خواهر و برادری وجود نداشته باشد `null` را برمی‌گردانند. این در تضاد با {{domxref("Node/previousSibling", "previousSibling")}} و {{domxref("Node/nextSibling", "nextSibling")}} است که ممکن است هر نوع گره خواهر و برادری را برگردانند.

## مقایسهٔ گره‌ها

سه روش مهم برای مقایسه گره‌ها وجود دارد: {{domxref("Node/isEqualNode", "isEqualNode()")}}، {{domxref("Node/isSameNode", "isSameNode()")}}، {{domxref("Node/compareDocumentPosition", "compareDocumentPosition()")}}.

متد `isSameNode()` قدیمی است. اکنون مانند [عملگر برابری دقیق](/en-US/docs/Web/JavaScript/Reference/Operators/Strict_equality) (`===`) رفتار می‌کند و `true` را برمی‌گرداند اگر و فقط اگر دو گره شیء یکسانی باشند.

متد `isEqualNode()` دو گره را از نظر ساختاری مقایسه می‌کند. دو گره برابر در نظر گرفته می‌شوند اگر نوع یکسان، داده یکسان داشته باشند و گره‌های فرزند آنها نیز در هر ایندکس برابر باشند. در بخش [داده‌های هر گره](#داده-های-هر-گره)، داده‌های مرتبط برای هر نوع گره را تعریف کردیم:

- برای `Document`، داده‌ای وجود ندارد، بنابراین فقط گره‌های فرزند باید مقایسه شوند.
- برای `DocumentType`، ویژگی‌های `name`، `publicId` و `systemId` باید مقایسه شوند.
- برای `Element`، `tagName` (دقیق‌تر، `namespaceURI`، `prefix` و `localName`؛ این‌ها را در راهنمای [فضاهای نام XML](/en-US/docs/Web/API/Document_Object_Model/XML_namespaces) معرفی خواهیم کرد) و ویژگی‌ها باید مقایسه شوند.
- برای `Attr`، `name` (دقیق‌تر، `namespaceURI`، `prefix` و `localName`؛ این‌ها را در راهنمای [فضاهای نام XML](/en-US/docs/Web/API/Document_Object_Model/XML_namespaces) معرفی خواهیم کرد) و ویژگی‌های `value` باید مقایسه شوند.
- برای همه گره‌های `CharacterData` (`Text`، `CDATASection`، `Comment` و `ProcessingInstruction`)، ویژگی `data` باید مقایسه شود. برای `ProcessingInstruction`، ویژگی `target` نیز باید مقایسه شود.

متد `a.compareDocumentPosition(b)` دو گره را بر اساس ترتیب درخت مقایسه می‌کند. یک بیت‌ماسک را برمی‌گرداند که موقعیت نسبی آنها را نشان می‌دهد. موارد ممکن عبارتند از:

- اگر `a` و `b` یک گره باشند، `0` را برمی‌گرداند.
- اگر دو گره هر دو ویژگی‌های یک عنصر باشند، اگر `a` در لیست ویژگی‌ها مقدم بر `b` باشد، `Node.DOCUMENT_POSITION_PRECEDING | Node.DOCUMENT_POSITION_IMPLEMENTATION_SPECIFIC` (34) را برمی‌گرداند، یا اگر `a` پس از `b` بیاید، `Node.DOCUMENT_POSITION_FOLLOWING | Node.DOCUMENT_POSITION_IMPLEMENTATION_SPECIFIC` (36) را برمی‌گرداند. اگر هر یک از گره‌ها یک ویژگی باشد، عنصر مالک برای مقایسه‌های بیشتر استفاده می‌شود.
- اگر دو گره ریشه یکسانی نداشته باشند، یا `Node.DOCUMENT_POSITION_DISCONNECTED | Node.DOCUMENT_POSITION_IMPLEMENTATION_SPECIFIC | Node.DOCUMENT_POSITION_PRECEDING` (35) یا `Node.DOCUMENT_POSITION_DISCONNECTED | Node.DOCUMENT_POSITION_IMPLEMENTATION_SPECIFIC | Node.DOCUMENT_POSITION_FOLLOWING` (37) را برمی‌گرداند. اینکه کدام یک برگردانده شود، به پیاده‌سازی بستگی دارد.
- اگر `a` جد `b` باشد (از جمله زمانی که `b` یک ویژگی از `a` باشد)، `Node.DOCUMENT_POSITION_CONTAINS | Node.DOCUMENT_POSITION_PRECEDING` (10) را برمی‌گرداند.
- اگر `a` نواده `b` باشد (از جمله زمانی که `a` یک ویژگی از `b` باشد)، `Node.DOCUMENT_POSITION_CONTAINED_BY | Node.DOCUMENT_POSITION_FOLLOWING` (20) را برمی‌گرداند.
- اگر `a` در ترتیب درخت مقدم بر `b` باشد، `Node.DOCUMENT_POSITION_PRECEDING` (2) را برمی‌گرداند.
- اگر `a` در ترتیب درخت پس از `b` بیاید، `Node.DOCUMENT_POSITION_FOLLOWING` (4) را برمی‌گرداند.

از مقادیر بیت‌ماسک استفاده می‌شود، بنابراین می‌توانید از یک عملیات AND بیتی برای بررسی روابط خاص استفاده کنید. برای مثال، برای بررسی اینکه آیا `a` مقدم بر `b` است، می‌توانید این کار را انجام دهید:

```js
if (a.compareDocumentPosition(b) & Node.DOCUMENT_POSITION_PRECEDING) {
  // a مقدم بر b است
}
```

که مواردی را که `a` و `b` ویژگی‌های یک عنصر هستند، `a` جد `b` است، و `a` در ترتیب درخت مقدم بر `b` است، پوشش می‌دهد.

## خلاصه

در اینجا همه ویژگی‌هایی که تاکنون معرفی کرده‌ایم آورده شده است. تعداد زیادی هستند، اما همه آنها در سناریوهای مختلف مفید هستند.

- همه گره‌های DOM واسط {{domxref("Node")}} را پیاده‌سازی می‌کنند.
- برای پیمایش درخت DOM: {{domxref("Node/parentNode", "parentNode")}}، {{domxref("Node/childNodes", "childNodes")}}، {{domxref("Node/firstChild", "firstChild")}}/{{domxref("Node/lastChild", "lastChild")}}، {{domxref("Node/hasChildNodes", "hasChildNodes()")}}، {{domxref("Node/getRootNode", "getRootNode()")}}، {{domxref("Node/previousSibling", "previousSibling")}}/{{domxref("Node/nextSibling", "nextSibling")}}.
- برای پیمایش درخت عنصر: {{domxref("Node/parentElement", "parentElement")}}، {{domxref("Element/children", "children")}}، {{domxref("Element/firstElementChild", "firstElementChild")}}/{{domxref("Element/lastElementChild", "lastElementChild")}}، {{domxref("Element/childElementCount", "childElementCount")}}، {{domxref("Element/previousElementSibling", "previousElementSibling")}}/{{domxref("Element/nextElementSibling", "nextElementSibling")}}.
- ویژگی {{domxref("Node/nodeType", "nodeType")}} نوع گره را نشان می‌دهد. ویژگی‌های {{domxref("Node/nodeName", "nodeName")}}، {{domxref("Node/nodeValue", "nodeValue")}} و {{domxref("Node/textContent", "textContent")}} داده‌های نگه‌داشته شده توسط گره را ارائه می‌دهند.
- گره {{domxref("Document")}} و دو فرزند مهم آن: {{domxref("Document/doctype", "doctype")}} و {{domxref("Document/documentElement", "documentElement")}}.
- گره {{domxref("DocumentType")}} و سه ویژگی آن: {{domxref("DocumentType/name", "name")}}، {{domxref("DocumentType/publicId", "publicId")}} و {{domxref("DocumentType/systemId", "systemId")}}.
- گره {{domxref("Element")}} و ویژگی‌های آن: {{domxref("Element/tagName", "tagName")}}، {{domxref("Element/attributes", "attributes")}}.
- گره {{domxref("Attr")}} و ویژگی‌های آن: {{domxref("Attr/name", "name")}} و {{domxref("Attr/value", "value")}}.
- واسط {{domxref("CharacterData")}} و ویژگی آن: {{domxref("CharacterData/data", "data")}}.
- چهار زیرکلاس {{domxref("CharacterData")}}: {{domxref("Text")}}، {{domxref("CDATASection")}}، {{domxref("Comment")}} و {{domxref("ProcessingInstruction")}}. `ProcessingInstruction` همچنین دارای ویژگی {{domxref("ProcessingInstruction/target", "target")}} است.
- روش‌های مختلف کار با ویژگی‌ها، از جمله ویژگی‌های {{domxref("Element/id", "id")}}، {{domxref("Element/className", "className")}} و {{domxref("Element/classList", "classList")}}.
- سه روش برای مقایسه گره‌ها: {{domxref("Node/isEqualNode", "isEqualNode()")}}، {{domxref("Node/isSameNode", "isSameNode()")}} و {{domxref("Node/compareDocumentPosition", "compareDocumentPosition()")}}.