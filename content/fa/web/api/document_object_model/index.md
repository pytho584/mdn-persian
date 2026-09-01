---
title: "Document Object Model (DOM)"
---

---
title: Document Object Model (DOM)
slug: Web/API/Document_Object_Model
page-type: web-api-overview
spec-urls: https://dom.spec.whatwg.org/
---

{{DefaultAPISidebar("DOM")}}

**مدل شیء سند** (**DOM**) ساختار یک سند — مانند HTML که یک صفحه وب را نشان می‌دهد — را در حافظه بازنمایی می‌کند و از این طریق صفحات وب را به اسکریپت‌ها یا زبان‌های برنامه‌نویسی متصل می‌سازد. معمولاً به جاوااسکریپت اشاره دارد، اگرچه مدل‌سازی اسناد HTML، SVG یا XML به شکل شیء بخشی از زبان اصلی جاوااسکریپت نیست.

DOM یک سند را با یک درخت منطقی بازنمایی می‌کند. هر شاخه از درخت به یک گره ختم می‌شود و هر گره شامل اشیایی است. متدهای DOM دسترسی برنامه‌محور به درخت را فراهم می‌کنند. با استفاده از آن‌ها می‌توانید ساختار، سبک یا محتوای سند را تغییر دهید.

گره‌ها همچنین می‌توانند دارای رویداد‌گران (event handlers) باشند. به محض فعال شدن یک رویداد، رویدادگران اجرا می‌شوند.

## مفاهیم و کاربرد

مدل شیء سند (DOM) یک رابط برنامه‌نویسی برای اسناد وب است. این مدل صفحه را به شکلی بازنمایی می‌کند که برنامه‌ها بتوانند ساختار، سبک و محتوای سند را تغییر دهند. DOM سند را به صورت گره‌ها و اشیاء نمایش می‌دهد؛ به این ترتیب زبان‌های برنامه‌نویسی می‌توانند با صفحه تعامل کنند.

یک صفحه وب سندی است که می‌تواند یا در پنجره مرورگر نمایش داده شود یا به صورت کد منبع HTML. در هر دو حالت، همان سند است، اما بازنمایی مدل شیء سند (DOM) امکان دستکاری آن را فراهم می‌کند. به عنوان یک بازنمایی شیءگرا از صفحه وب، می‌توان آن را با یک زبان اسکریپتی مانند جاوااسکریپت تغییر داد.

برای مثال، DOM مشخص می‌کند که متد `querySelectorAll` در این قطعه کد باید فهرستی از همه عناصر {{HTMLElement("p")}} در سند را بازگرداند:

```js
const paragraphs = document.querySelectorAll("p");
// paragraphs[0] is the first <p> element
// paragraphs[1] is the second <p> element, etc.
alert(paragraphs[0].nodeName);
```

همه ویژگی‌ها، متدها و رویدادهایی که برای دستکاری و ایجاد صفحات وب در دسترس هستند، در قالب اشیاء سازمان‌دهی شده‌اند. برای مثال، شیء `document` که خود سند را بازنمایی می‌کند، هر شیء `table` که رابط DOM به نام {{domxref("HTMLTableElement")}} را برای دسترسی به جدول‌های HTML پیاده‌سازی می‌کند، و غیره، همه اشیاء هستند.

DOM با استفاده از چندین API که با هم کار می‌کنند ساخته شده است. DOM اصلی موجودیت‌هایی را تعریف می‌کند که هر سند و اشیاء درون آن را توصیف می‌کنند. این تعریف بر اساس نیاز توسط APIهای دیگری که ویژگی‌ها و قابلیت‌های جدیدی به DOM اضافه می‌کنند گسترش می‌یابد. برای مثال، [HTML DOM API](/en-US/docs/Web/API/HTML_DOM_API) پشتیبانی از بازنمایی اسناد HTML را به DOM اصلی اضافه می‌کند و SVG API پشتیبانی از بازنمایی اسناد SVG را فراهم می‌آورد.

### درخت DOM چیست؟

**درخت DOM** یک [ساختار درختی](https://en.wikipedia.org/wiki/Tree_structure) است که گره‌های آن محتوای یک سند HTML یا XML را نشان می‌دهند. هر سند HTML یا XML یک بازنمایی درخت DOM دارد. برای مثال، سند زیر را در نظر بگیرید:

```html
<html lang="en">
  <head>
    <title>My Document</title>
  </head>
  <body>
    <h1>Header</h1>
    <p>Paragraph</p>
  </body>
</html>
```

درخت DOM آن به این شکل است:

![The DOM as a tree-like representation of a document that has a root and node elements containing content](using_the_w3c_dom_level_1_core-doctree.jpg)

اگرچه درخت بالا شبیه درخت DOM سند فوق است، اما یکسان نیستند، زیرا درخت DOM واقعی [فاصله‌های خالی (whitespace)](/en-US/docs/Web/CSS/Guides/Text/Whitespace) را حفظ می‌کند.

وقتی مرورگر وب یک سند HTML را تجزیه می‌کند، یک درخت DOM می‌سازد و سپس از آن برای نمایش سند استفاده می‌کند.

### DOM و جاوااسکریپت

مثال کوتاه قبلی، مانند تقریباً همه مثال‌ها، {{glossary("JavaScript")}} است. یعنی به زبان جاوااسکریپت _نوشته_ شده، اما از DOM برای دسترسی به سند و عناصر آن _استفاده_ می‌کند. DOM یک زبان برنامه‌نویسی نیست، اما بدون آن، زبان جاوااسکریپت هیچ مدل یا تصوری از صفحات وب، اسناد HTML، اسناد SVG و اجزای آن‌ها wouldn't داشته باشد. کل سند، سر (head)، جدول‌های داخل سند، سربرگ‌های جدول، متن داخل سلول‌های جدول و همه عناصر دیگر در یک سند، بخش‌هایی از مدل شیء سند برای آن سند هستند. همه آن‌ها را می‌توان با استفاده از DOM و یک زبان اسکریپتی مانند جاوااسکریپت دسترسی و دستکاری کرد.

DOM بخشی از زبان جاوااسکریپت نیست، بلکه یک Web API است که برای ساخت وب‌سایت‌ها استفاده می‌شود. جاوااسکریپت همچنین می‌تواند در زمینه‌های دیگر استفاده شود. برای مثال، Node.js برنامه‌های جاوااسکریپت را روی رایانه اجرا می‌کند، اما مجموعه APIهای متفاوتی ارائه می‌دهد و DOM API بخش اصلی runtime نود جی‌اس نیست.

DOM طوری طراحی شده است که مستقل از هر زبان برنامه‌نویسی خاصی باشد و بازنمایی ساختاری سند را از طریق یک API واحد و سازگار در دسترس قرار دهد. حتی اگر بیشتر توسعه‌دهندگان وب فقط از طریق جاوااسکریپت از DOM استفاده کنند، می‌توان پیاده‌سازی‌هایی از DOM را برای هر زبانی ساخت، همان‌طور که این مثال پایتون نشان می‌دهد:

```python
# Python DOM example
import xml.dom.minidom as m
doc = m.parse(r"C:\Projects\Py\chap1.xml")
doc.nodeName # DOM property of document object
p_list = doc.getElementsByTagName("para")
```

برای اطلاعات بیشتر درباره فناوری‌های مرتبط با نوشتن جاوااسکریپت در وب، به [بررسی فناوری‌های جاوااسکریپت](/en-US/docs/Web/JavaScript/Reference/JavaScript_technologies_overview) مراجعه کنید.

### دسترسی به DOM

برای شروع استفاده از DOM نیازی به انجام کار خاصی ندارید. شما مستقیماً از داخل به اصطلاح _script_، برنامه‌ای که توسط مرورگر اجرا می‌شود، از API در جاوااسکریپت استفاده می‌کنید.

وقتی یک اسکریپت ایجاد می‌کنید، چه به صورت درون‌خطی در یک عنصر `<script>` یا در صفحه وب گنجانده شده باشد، می‌توانید بلافاصله استفاده از API را برای اشیاء {{domxref("document")}} یا {{domxref("Window", "window")}} آغاز کنید تا خود سند یا هر یک از عناصر مختلف در صفحه وب (عناصر فرزند سند) را دستکاری کنید. برنامه‌نویسی DOM شما ممکن است به سادگی مثال زیر باشد که با استفاده از تابع {{domxref("console/log_static", "console.log()")}} پیامی را در کنسول نمایش می‌دهد:

```html
<body onload="console.log('Welcome to my home page!');">
  …
</body>
```

از آنجا که به طور کلی ترکیب ساختار صفحه (نوشته‌شده با HTML) و دستکاری DOM (نوشته‌شده با جاوااسکریپت) توصیه نمی‌شود، بخش‌های جاوااسکریپت در اینجا با هم گروه‌بندی شده و از HTML جدا شده‌اند.

برای مثال، تابع زیر یک عنصر {{HTMLElement("Heading_Elements", "h1")}} جدید ایجاد می‌کند، متنی به آن عنصر اضافه می‌کند و سپس آن را به درخت سند می‌افزاید:

```html
<html lang="en">
  <head> </head>
  <body>
    <script>
      // create a couple of elements in an otherwise empty HTML page
      const heading = document.createElement("h1");
      const headingText = document.createTextNode("Big Head!");
      heading.appendChild(headingText);
      document.body.appendChild(heading);
    </script>
  </body>
</html>
```

## رابط‌های DOM

در زیر همه رابط‌هایی که توسط مشخصات DOM تعریف شده‌اند آمده است:

- {{DOMxRef("AbortController")}}
- {{DOMxRef("AbortSignal")}}
- {{DOMxRef("AbstractRange")}}
- {{DOMxRef("Attr")}}
- {{DOMxRef("CDATASection")}}
- {{DOMxRef("CharacterData")}}
- {{DOMxRef("Comment")}}
- {{DOMxRef("CustomEvent")}}
- {{DOMxRef("Document")}}
- {{DOMxRef("DocumentFragment")}}
- {{DOMxRef("DocumentType")}}
- {{DOMxRef("DOMError")}} {{Deprecated_Inline}}
- {{DOMxRef("DOMException")}}
- {{DOMxRef("DOMImplementation")}}
- {{DOMxRef("DOMParser")}}
- {{DOMxRef("DOMTokenList")}}
- {{DOMxRef("Element")}}
- {{DOMxRef("Event")}}
- {{DOMxRef("EventTarget")}}
- {{DOMxRef("HTMLCollection")}}
- {{DOMxRef("MutationObserver")}}
- {{DOMxRef("MutationRecord")}}
- {{DOMxRef("NamedNodeMap")}}
- {{DOMxRef("Node")}}
- {{DOMxRef("NodeIterator")}}
- {{DOMxRef("NodeList")}}
- {{DOMxRef("ProcessingInstruction")}}
- {{DOMxRef("QuotaExceededError")}}
- {{DOMxRef("Range")}}
- {{DOMxRef("ShadowRoot")}}
- {{DOMxRef("StaticRange")}}
- {{DOMxRef("Text")}}
- {{DOMxRef("TreeWalker")}}
- {{DOMxRef("XMLDocument")}}
- {{DOMxRef("XPathEvaluator")}}
- {{DOMxRef("XPathExpression")}}
- {{DOMxRef("XPathResult")}}
- {{DOMxRef("XSLTProcessor")}}

این راهنما درباره اشیاء و _چیزهای_ واقعی است که می‌توانید برای دستکاری سلسله‌مراتب DOM از آن‌ها استفاده کنید. نقاط زیادی وجود دارد که درک نحوه کار این موارد می‌تواند گیج‌کننده باشد. برای مثال، شیء نمایانگر عنصر HTML `form` ویژگی `name` خود را از رابط `HTMLFormElement` می‌گیرد، اما ویژگی `className` خود را از رابط `HTMLElement` دریافت می‌کند. در هر دو حالت، ویژگی مورد نظر شما در آن شیء فرم وجود دارد.

اما رابطه بین اشیاء و رابط‌هایی که آن‌ها در DOM پیاده‌سازی می‌کنند می‌تواند گیج‌کننده باشد، و بنابراین این بخش می‌کوشد کمی درباره رابط‌های واقعی در مشخصات DOM و نحوه در دسترس بودن آن‌ها توضیح دهد.

### رابط‌ها و اشیاء

بسیاری از اشیاء چندین رابط مختلف را پیاده‌سازی می‌کنند. برای مثال، شیء جدول یک رابط تخصصی به نام {{domxref("HTMLTableElement")}} را پیاده‌سازی می‌کند که شامل متدهایی مانند `createCaption` و `insertRow` است. اما از آنجا که جدول همچنین یک عنصر HTML است، `table` رابط `Element` را پیاده‌سازی می‌کند که در فصل مرجع {{domxref("Element")}} در DOM توضیح داده شده است. و در نهایت، از آنجا که یک عنصر HTML از نظر DOM یک گره در درخت گره‌هایی است که مدل شیء یک صفحه HTML یا XML را تشکیل می‌دهند، شیء جدول همچنین رابط پایه‌تری به نام `Node` را پیاده‌سازی می‌کند که `Element` از آن مشتق می‌شود.

وقتی ارجاعی به یک شیء `table` می‌گیرید، همان‌طور که در مثال زیر نشان داده شده است، معمولاً از هر سه این رابط‌ها به صورت جایگزین روی شیء استفاده می‌کنید، شاید بدون اینکه بدانید.

```js
const table = document.getElementById("table");
const tableAttrs = table.attributes; // Node/Element interface
for (const attr of tableAttrs) {
  // HTMLTableElement interface: border attribute
  if (attr.nodeName.toLowerCase() === "border") {
    table.border = "1";
  }
}
// HTMLTableElement interface: summary attribute
table.summary = "note: increased border";
```

### انواع داده بنیادی

این صفحه سعی دارد انواع و اشیاء مختلف را به زبان ساده توصیف کند. اما تعدادی نوع داده مختلف در API جابه‌جا می‌شوند که باید از آن‌ها آگاه باشید.

> [!NOTE]
> از آنجا که اکثریت قریب به اتفاق کدهایی که از DOM استفاده می‌کنند حول دستکاری اسناد HTML می‌چرخند، معمول است که به گره‌های DOM به عنوان **عناصر** اشاره شود، اگرچه به طور دقیق هر گره یک عنصر نیست.

جدول زیر به طور خلاصه این انواع داده را توصیف می‌کند.

<table class="standard-table">
  <thead>
    <tr>
      <th>نوع داده (رابط)</th>
      <th>توضیحات</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>{{domxref("Document")}}</td>
      <td>
        وقتی یک عضو، شیئی از نوع <code>document</code> بازمی‌گرداند (مثلاً ویژگی
        <code>ownerDocument</code> یک عنصر، <code>document</code>ای را که عنصر به آن تعلق دارد بازمی‌گرداند)، این شیء همان شیء ریشه <code>document</code> است. فصل
        <a href="/en-US/docs/Web/API/Document">مرجع <code>document</code> در DOM</a>
        شیء <code>document</code> را توصیف می‌کند.
      </td>
    </tr>
    <tr>
      <td>{{domxref("Node")}}</td>
      <td>
        هر شیء واقع در یک سند، گره‌ای از یک نوع است. در یک سند HTML، یک شیء می‌تواند یک گره عنصر باشد، اما همچنین می‌تواند یک گره متنی یا گره ویژگی باشد.
      </td>
    </tr>
    <tr>
      <td>{{domxref("Element")}}</td>
      <td>
        نوع <code>element</code> بر اساس <code>node</code> است. این نوع به یک عنصر یا گره از نوع <code>element</code> اشاره دارد که توسط یکی از اعضای DOM API بازگردانده می‌شود. به جای اینکه مثلاً بگوییم متد {{domxref("document.createElement()")}} یک ارجاع شیء به یک <code>node</code> بازمی‌گرداند، فقط می‌گوییم این متد <code>element</code>ی را که به تازگی در DOM ایجاد شده است بازمی‌گرداند. اشیاء <code>element</code> رابط <code>Element</code> در DOM و همچنین رابط پایه‌تر <code>Node</code> را پیاده‌سازی می‌کنند که هر دو با هم در این مرجع گنجانده شده‌اند. در یک سند HTML، عناصر بیشتر توسط رابط {{domxref("HTMLElement")}} در HTML DOM API و همچنین سایر رابط‌هایی که قابلیت‌های انواع خاصی از عناصر را توصیف می‌کنند (مثلاً {{domxref("HTMLTableElement")}} برای عناصر {{HTMLElement("table")}}) تقویت می‌شوند.
      </td>
    </tr>
    <