---
title: "Attr"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Attr"
translated_by: "n8n + AI"
---

---
title: Attr
slug: Web/API/Attr
page-type: web-api-interface
browser-compat: api.Attr
---

{{APIRef("DOM")}}

رابطِ **`Attr`** یکی از ویژگی‌های یک عنصر را به‌صورت یک شیء نمایش می‌دهد. در بیشتر مواقع، مقدار ویژگی را مستقیماً به‌صورت رشته دریافت می‌کنید (مثلاً {{domxref("Element.getAttribute()")}})، اما برخی موارد ممکن است نیاز به تعامل با نمونه‌های `Attr` داشته باشند (مثلاً {{domxref("Element.getAttributeNode()")}}).

{{InheritanceDiagram}}

ایده اصلی یک شیء از نوع `Attr` ارتباط بین یک _نام_ و یک _مقدار_ است. یک ویژگی همچنین ممکن است بخشی از یک _فضای نام_ باشد و در این صورت، یک URI برای شناسایی فضای نام و یک پیشوند که مخفف فضای نام است نیز دارد.

نام زمانی _محلی_ در نظر گرفته می‌شود که پیشوند فضای نام احتمالی را نادیده بگیرد و زمانی _واجد شرایط_ در نظر گرفته می‌شود که پیشوند فضای نام را، در صورت وجود، شامل شود و با دو نقطه (`:`) از نام محلی جدا شود. سه حالت داریم: ویژگی خارج از فضای نام، ویژگی داخل فضای نام بدون پیشوند تعریف‌شده، ویژگی داخل فضای نام با پیشوند:

| ویژگی | نام فضای نام | پیشوند فضای نام | نام محلی ویژگی | نام واجد شرایط ویژگی |
| --------- | -------------- | ---------------- | -------------------- | ------------------------ |
| `myAttr`  | _هیچ_         | _هیچ_           | `myAttr`             | `myAttr`                 |
| `myAttr`  | `mynamespace`  | _هیچ_           | `myAttr`             | `myAttr`                 |
| `myAttr`  | `mynamespace`  | `myns`           | `myAttr`             | `myns:myAttr`            |

> [!NOTE]
> این رابط فقط ویژگی‌های موجود در نمایش درختی یک {{domxref("Element")}} از نوع SVG، HTML یا MathML را نشان می‌دهد. این رابط خصوصیات رابط مرتبط با آن عنصر را نشان نمی‌دهد، مانند خصوصیات {{domxref("HTMLTableElement")}} برای عنصر {{HTMLElement("table")}}. (برای اطلاعات بیشتر درباره ویژگی‌ها و چگونگی _بازتاب_ آن‌ها به خصوصیات، به {{Glossary("Attribute", "این مقاله")}} مراجعه کنید.)

## خصوصیات نمونه

_این رابط همچنین خصوصیات رابط‌های والد خود، {{domxref("Node")}} و {{domxref("EventTarget")}} را به ارث می‌برد._

- {{domxref("Attr.localName", "localName")}} {{ReadOnlyInline}}
  - : رشته‌ای که بخش محلی نام واجد شرایط ویژگی را نشان می‌دهد.
- {{domxref("Attr.name", "name")}} {{ReadOnlyInline}}
  - : _نام واجد شرایط_ ویژگی. اگر ویژگی در یک فضای نام نباشد، با خاصیت {{domxref("attr.localName", "localName")}} یکسان خواهد بود.
- {{domxref("Attr.namespaceURI", "namespaceURI")}} {{ReadOnlyInline}}
  - : رشته‌ای که URI فضای نام ویژگی را نشان می‌دهد، یا اگر فضای نامی وجود نداشته باشد `null`.
- {{domxref("Attr.ownerElement", "ownerElement")}} {{ReadOnlyInline}}
  - : {{domxref("Element")}} ای که ویژگی به آن تعلق دارد.
- {{domxref("Attr.prefix", "prefix")}} {{ReadOnlyInline}}
  - : رشته‌ای که پیشوند فضای نام ویژگی را نشان می‌دهد، یا اگر فضای نام بدون پیشوند یا بدون فضای نام مشخص شده باشد، `null`.
- {{domxref("Attr.specified", "specified")}} {{ReadOnlyInline}} {{deprecated_inline}}
  - : این خاصیت همیشه `true` برمی‌گرداند.
- {{domxref("Attr.value", "value")}}
  - : مقدار ویژگی، یک رشته که می‌توان با استفاده از این خاصیت آن را تنظیم و دریافت کرد.

## روش‌های نمونه

_این رابط هیچ روش خاصی ندارد، اما روش‌های رابط‌های والد خود، {{domxref("Node")}} و {{domxref("EventTarget")}} را به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- گره‌های دیگر عبارت‌اند از {{domxref("CDATASection")}}، {{domxref("CharacterData")}}، {{domxref("Comment")}}، {{domxref("Document")}}، {{domxref("Element")}}، {{domxref("ProcessingInstruction")}} و {{domxref("Text")}}.