---
title: HTML DOM API
slug: Web/API/HTML_DOM_API
page-type: web-api-overview
browser-compat: api.HTMLElement
---

{{DefaultAPISidebar("HTML DOM")}}

**HTML DOM API** از مجموعه‌ای از رابط‌ها (interfaces) تشکیل شده است که عملکرد هر یک از {{Glossary("element", "عنصرهای")}} موجود در {{Glossary("HTML")}} و همچنین انواع و رابط‌های پشتیبانی‌کننده‌ای که آن‌ها به آن وابسته هستند را تعریف می‌کنند.

حوزه‌های عملکردی موجود در HTML DOM API عبارتند از:

- دسترسی به عناصر HTML و کنترل آن‌ها از طریق {{Glossary("DOM")}}.
- دسترسی به داده‌های فرم و دستکاری آن‌ها.
- تعامل با محتویات تصاویر دو بعدی و بافت (context) یک {{HTMLElement("canvas")}} در HTML، برای مثال برای ترسیم روی آن‌ها.
- مدیریت رسانه‌های متصل به عناصر رسانه‌ای HTML ({{HTMLElement("audio")}} و {{HTMLElement("video")}}).
- کشیدن و رها کردن (drag and drop) محتوا در صفحات وب.
- دسترسی به تاریخچه پیمایش مرورگر.
- رابط‌های پشتیبان و اتصالی برای سایر APIها مانند [Web Components](/en-US/docs/Web/API/Web_components)، {{DOMxRef("Web_Storage_API", "Web Storage", "", "1")}}، {{DOMxRef("Web_Workers_API", "Web Workers", "", "1")}}، {{DOMxRef("WebSockets_API", "WebSocket", "", "1")}} و {{DOMxRef("Server-sent_events", "Server-sent events", "", "1")}}.

## مفاهیم و کاربرد HTML DOM

در این مقاله، بر بخش‌هایی از HTML DOM تمرکز خواهیم کرد که با عناصر HTML سروکار دارند. بحث درباره حوزه‌های دیگر، مانند {{DOMxRef("HTML_Drag_and_Drop_API", "Drag and Drop", "", "1")}}، {{DOMxRef("WebSockets_API", "WebSockets", "", "1")}}، {{DOMxRef("Web_Storage_API", "Web Storage", "", "1")}} و غیره، در مستندات مربوط به آن APIها یافت می‌شود.

### ساختار یک سند HTML

مدل شیء سند (Document Object Model یا {{Glossary("DOM")}}) معماری‌ای است که ساختار یک {{domxref("document")}} را توصیف می‌کند؛ هر سند با یک نمونه از رابط {{domxref("Document")}} نمایش داده می‌شود. یک سند به نوبه خود از یک درخت سلسله‌مراتبی از **گره‌ها** (nodes) تشکیل شده است که در آن هر گره یک رکورد بنیادی است که یک شیء واحد درون سند (مانند یک عنصر یا گره متنی) را نمایش می‌دهد.

گره‌ها ممکن است صرفاً سازمانی باشند، یعنی وسیله‌ای برای گروه‌بندی گره‌های دیگر یا فراهم کردن نقطه‌ای برای ساخت سلسله‌مراتب فراهم کنند؛ گره‌های دیگر ممکن است اجزای قابل مشاهده یک سند را نمایش دهند. هر گره بر اساس رابط {{domxref("Node")}} است که ویژگی‌هایی برای دریافت اطلاعات درباره گره و همچنین روش‌هایی برای ایجاد، حذف و سازماندهی گره‌ها در DOM فراهم می‌کند.

گره‌ها هیچ مفهوم وابسته به محتوایی که واقعاً در سند نمایش داده می‌شود ندارند. آن‌ها ظرف‌های خالی هستند. مفهوم بنیادی گره‌ای که می‌تواند محتوای بصری را نمایش دهد توسط رابط {{domxref("Element")}} معرفی می‌شود. یک نمونه شیء `Element` یک عنصر واحد در سند را نمایش می‌دهد که با استفاده از HTML یا یک واژگان {{glossary("XML")}} مانند {{glossary("SVG")}} ایجاد شده است.

برای مثال، سندی با دو عنصر در نظر بگیرید که یکی از آن‌ها دو عنصر دیگر را درون خود جای داده است:

![ساختار یک سند با عناصر داخل یک سند در یک پنجره](dom-structure.svg)

در حالی که رابط {{domxref("Document")}} به عنوان بخشی از مشخصات {{DOMxRef("Document_Object_Model", "DOM", "", "1")}} تعریف شده است، مشخصات HTML آن را به‌طور قابل توجهی گسترش می‌دهد تا اطلاعات خاص استفاده از DOM در زمینه مرورگر وب، و همچنین استفاده از آن برای نمایش اسناد HTML را به‌طور خاص اضافه کند.

از جمله مواردی که توسط استاندارد HTML به `Document` اضافه شده است:

- پشتیبانی از دسترسی به اطلاعات مختلف ارائه‌شده توسط سرصفحه‌های {{Glossary("HTTP")}} هنگام بارگذاری صفحه، مانند {{DOMxRef("Document/location", "location", "", "1")}} (مکان) که سند از آن بارگذاری شده، {{DOMxRef("Document/cookie", "cookies", "", "1")}} (کوکی‌ها)، {{DOMxRef("Document/lastModified", "modification date", "", "1")}} (تاریخ تغییر)، {{DOMxRef("Document/referrer", "referring site", "", "1")}} (سایت ارجاع‌دهنده) و غیره.
- دسترسی به فهرست عناصر در بلوک {{HTMLElement("head")}} سند و {{DOMxRef("Document/body", "body", "", "1")}}، و همچنین فهرست‌های {{DOMxRef("Document/images", "images", "", "1")}} (تصاویر)، {{DOMxRef("Document/links", "links", "", "1")}} (پیوندها)، {{DOMxRef("Document/scripts", "scripts", "", "1")}} (اسکریپت‌ها) و غیره موجود در سند.
- پشتیبانی از تعامل با کاربر با بررسی {{DOMxRef("Document/hasFocus", "focus", "", "1")}} (فوکوس) و با اجرای دستورات روی [محتوای قابل ویرایش](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable).
- مدیریت‌کننده‌های رویداد برای رویدادهای سند که توسط استاندارد HTML تعریف شده‌اند تا امکان دسترسی به رویدادهای {{DOMxRef("MouseEvent", "mouse", "", "1")}} و {{DOMxRef("KeyboardEvent", "keyboard", "", "1")}}، {{DOMxRef("HTML_Drag_and_Drop_API", "drag and drop", "", "1")}}، {{DOMxRef("HTMLMediaElement", "media control", "", "1")}} و موارد دیگر فراهم شود.
- مدیریت‌کننده‌های رویداد برای رویدادهایی که می‌توانند به عناصر و اسناد تحویل داده شوند؛ این موارد در حال حاضر فقط شامل اقدامات {{DOMxRef("Element/copy_event", "copy")}} (کپی)، {{DOMxRef("Element/cut_event", "cut")}} (برش) و {{DOMxRef("Element/paste_event", "paste")}} (چسباندن) هستند.

### رابط‌های عنصر HTML

رابط `Element` بیشتر برای نمایش عناصر HTML به‌طور خاص با معرفی رابط {{domxref("HTMLElement")}} سازگار شده است، که همه کلاس‌های خاص‌تر عنصر HTML از آن ارث می‌برند. این کار کلاس `Element` را گسترش می‌دهد تا ویژگی‌های عمومی خاص HTML را به گره‌های عنصر اضافه کند. ویژگی‌های اضافه‌شده توسط `HTMLElement` عبارتند از برای مثال {{domxref("HTMLElement.hidden", "hidden")}} و {{domxref("HTMLElement.innerText", "innerText")}}.

یک سند {{Glossary("HTML")}} یک درخت DOM است که در آن هر گره یک عنصر HTML است که توسط رابط {{domxref("HTMLElement")}} نمایش داده می‌شود. کلاس `HTMLElement` به نوبه خود `Node` را پیاده‌سازی می‌کند، بنابراین هر عنصر یک گره نیز هست (اما عکس آن درست نیست). به این ترتیب، ویژگی‌های ساختاری پیاده‌سازی‌شده توسط رابط {{domxref("Node")}} نیز در دسترس عناصر HTML قرار می‌گیرند و به آن‌ها اجازه می‌دهند درون یکدیگر تودرتو شوند، ایجاد و حذف شوند، جابجا شوند و غیره.

با این حال، رابط `HTMLElement` عمومی است و فقط عملکرد مشترک میان همه عناصر HTML را فراهم می‌کند، مانند شناسه عنصر، مختصات آن، HTML سازنده عنصر، اطلاعات مربوط به موقعیت اسکرول و غیره.

برای گسترش عملکرد رابط اصلی `HTMLElement` به منظور فراهم کردن ویژگی‌های مورد نیاز یک عنصر خاص، کلاس `HTMLElement` زیرکلاس‌سازی می‌شود تا خواص و روش‌های لازم اضافه شود. برای مثال، عنصر {{HTMLElement("canvas")}} توسط یک شیء از نوع {{domxref("HTMLCanvasElement")}} نمایش داده می‌شود. `HTMLCanvasElement` نوع `HTMLElement` را با افزودن ویژگی‌هایی مانند {{domxref("HTMLCanvasElement.height", "height")}} و روش‌هایی مانند {{domxref("HTMLCanvasElement.getContext", "getContext()")}} برای فراهم کردن ویژگی‌های خاص بوم (canvas) تقویت می‌کند.

سلسله‌مراتب کلی ارث‌بری برای کلاس‌های عنصر HTML به این شکل است:

![سلسله‌مراتب رابط‌ها برای عناصر HTML](html-dom-hierarchy.svg)

بنابراین، یک عنصر ویژگی‌ها و روش‌های همه اجداد خود را به ارث می‌برد. برای مثال، یک عنصر {{HTMLElement("a")}} را در نظر بگیرید که در DOM توسط یک شیء از نوع {{domxref("HTMLAnchorElement")}} نمایش داده می‌شود. بنابراین، عنصر شامل ویژگی‌ها و روش‌های خاص پیوند (anchor) است که در مستندات آن کلاس توضیح داده شده است، اما همچنین آن‌هایی که توسط {{domxref("HTMLElement")}} و {{domxref("Element")}} تعریف شده‌اند، و همچنین از {{domxref("Node")}} و در نهایت {{domxref("EventTarget")}}.

هر سطح یک جنبه کلیدی از کاربرد عنصر را تعریف می‌کند. از `Node`، عنصر مفاهیم مربوط به توانایی عنصر برای قرار گرفتن درون عنصر دیگر و نیز در بر گرفتن عناصر دیگر را به ارث می‌برد. از اهمیت ویژه‌ای برخوردار است آنچه از ارث بردن از `EventTarget` به دست می‌آید: توانایی دریافت و مدیریت رویدادهایی مانند کلیک‌های ماوس، رویدادهای پخش و توقف و غیره.

عناصری وجود دارند که اشتراکاتی دارند و بنابراین یک نوع واسط اضافی دارند. برای مثال، عناصر {{HTMLElement("audio")}} و {{HTMLElement("video")}} هر دو رسانه دیداری-شنیداری ارائه می‌دهند. انواع متناظر، {{domxref("HTMLAudioElement")}} و {{domxref("HTMLVideoElement")}}، هر دو بر اساس نوع مشترک {{domxref("HTMLMediaElement")}} هستند، که به نوبه خود بر اساس {{domxref("HTMLElement")}} و غیره است. `HTMLMediaElement` روش‌ها و ویژگی‌های مشترک بین عناصر صوتی و تصویری را تعریف می‌کند.

این رابط‌های خاص عنصر، بخش عمده HTML DOM API را تشکیل می‌دهند و تمرکز این مقاله هستند. مقاله [DOM](/en-US/docs/Web/API/Document_Object_Model) مقدمه‌ای کلی درباره DOM و مفاهیم آن ارائه می‌دهد.

## مخاطب هدف HTML DOM

ویژگی‌های ارائه‌شده توسط HTML DOM از پرکاربردترین APIها در جعبه‌ابزار توسعه‌دهنده وب هستند. تقریباً همه برنامه‌های وب به جز ساده‌ترین آن‌ها از برخی ویژگی‌های HTML DOM استفاده خواهند کرد.

## رابط‌های API HTML DOM

بیشتر رابط‌هایی که HTML DOM API را تشکیل می‌دهند تقریباً یک‌به‌یک با عناصر HTML منفرد یا گروه کوچکی از عناصر با عملکرد مشابه مطابقت دارند. علاوه بر این، HTML DOM API شامل چند رابط و نوع برای پشتیبانی از رابط‌های عنصر HTML است.

### رابط‌های عنصر HTML

این رابط‌ها عناصر HTML خاص (یا مجموعه‌هایی از عناصر مرتبط که ویژگی‌ها و روش‌های یکسانی دارند) را نمایش می‌دهند.

- {{DOMxRef("HTMLAnchorElement")}}
- {{DOMxRef("HTMLAreaElement")}}
- {{DOMxRef("HTMLAudioElement")}}
- {{DOMxRef("HTMLBaseElement")}}
- {{DOMxRef("HTMLBodyElement")}}
- {{DOMxRef("HTMLBRElement")}}
- {{DOMxRef("HTMLButtonElement")}}
- {{DOMxRef("HTMLCanvasElement")}}
- {{DOMxRef("HTMLDataElement")}}
- {{DOMxRef("HTMLDataListElement")}}
- {{DOMxRef("HTMLDetailsElement")}}
- {{DOMxRef("HTMLDialogElement")}}
- {{DOMxRef("HTMLDirectoryElement")}}
- {{DOMxRef("HTMLDivElement")}}
- {{DOMxRef("HTMLDListElement")}}
- {{DOMxRef("HTMLElement")}}
- {{DOMxRef("HTMLEmbedElement")}}
- {{DOMxRef("HTMLFieldSetElement")}}
- {{DOMxRef("HTMLFormElement")}}
- {{DOMxRef("HTMLHRElement")}}
- {{DOMxRef("HTMLHeadElement")}}
- {{DOMxRef("HTMLHeadingElement")}}
- {{DOMxRef("HTMLHtmlElement")}}
- {{DOMxRef("HTMLIFrameElement")}}
- {{DOMxRef("HTMLImageElement")}}
- {{DOMxRef("HTMLInputElement")}}
- {{DOMxRef("HTMLLabelElement")}}
- {{DOMxRef("HTMLLegendElement")}}
- {{DOMxRef("HTMLLIElement")}}
- {{DOMxRef("HTMLLinkElement")}}
- {{DOMxRef("HTMLMapElement")}}
- {{DOMxRef("HTMLMediaElement")}}
- {{DOMxRef("HTMLMenuElement")}}
- {{DOMxRef("HTMLMetaElement")}}
- {{DOMxRef("HTMLMeterElement")}}
- {{DOMxRef("HTMLModElement")}}
- {{DOMxRef("HTMLObjectElement")}}
- {{DOMxRef("HTMLOListElement")}}
- {{DOMxRef("HTMLOptGroupElement")}}
- {{DOMxRef("HTMLOptionElement")}}
- {{DOMxRef("HTMLOutputElement")}}
- {{DOMxRef("HTMLParagraphElement")}}
- {{DOMxRef("HTMLPictureElement")}}
- {{DOMxRef("HTMLPreElement")}}
- {{DOMxRef("HTMLProgressElement")}}
- {{DOMxRef("HTMLQuoteElement")}}
- {{DOMxRef("HTMLScriptElement")}}
- {{DOMxRef("HTMLSelectElement")}}
- {{DOMxRef("HTMLSlotElement")}}
- {{DOMxRef("HTMLSourceElement")}}
- {{DOMxRef("HTMLSpanElement")}}
- {{DOMxRef("HTMLStyleElement")}}
- {{DOMxRef("HTMLTableCaptionElement")}}
- {{DOMxRef("HTMLTableCellElement")}}
- {{DOMxRef("HTMLTableColElement")}}
- {{DOMxRef("HTMLTableElement")}}
- {{DOMxRef("HTMLTableRowElement")}}
- {{DOMxRef("HTMLTableSectionElement")}}
- {{DOMxRef("HTMLTemplateElement")}}
- {{DOMxRef("HTMLTextAreaElement")}}
- {{DOMxRef("HTMLTimeElement")}}
- {{DOMxRef("HTMLTitleElement")}}
- {{DOMxRef("HTMLTrackElement")}}
- {{DOMxRef("HTMLUListElement")}}
- {{DOMxRef("HTMLUnknownElement")}}
- {{DOMxRef("HTMLVideoElement")}}

#### رابط‌های عنصر HTML منسوخ‌شده

- {{DOMxRef("HTMLMarqueeElement")}} {{deprecated_inline}}

#### رابط‌های عنصر HTML منسوخ‌شده (obsolete)

- {{DOMxRef("HTMLFontElement")}} {{deprecated_inline}}
- {{DOMxRef("HTMLFrameElement")}} {{deprecated_inline}}
- {{DOMxRef("HTMLFrameSetElement")}} {{deprecated_inline}}

### رابط‌های برنامه وب و یکپارچه‌سازی مرورگر

این رابط‌ها دسترسی به پنجره مرورگر و سندی که HTML را در بر دارد، و همچنین به وضعیت مرورگر، افزونه‌های موجود (در صورت وجود) و گزینه‌های پیکربندی مختلف را فراهم می‌کنند.

- {{DOMxRef("BarProp")}}
- {{DOMxRef("Navigator")}}
- {{DOMxRef("Window")}}

#### رابط‌های منسوخ‌شده برنامه وب و یکپارچه‌سازی مرورگر

- {{DOMxRef("Plugin")}} {{dep