---
title: "Document: queryCommandState() method"
short-title: queryCommandState()
slug: Web/API/Document/queryCommandState
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.Document.queryCommandState
---

{{ApiRef("DOM")}}{{deprecated_header}}{{Non-standard_header}}

> [!NOTE]
> اگرچه متد {{domxref("Document/execCommand", "execCommand()")}} منسوخ شده است، اما هنوز موارد استفاده‌ی معتبری وجود دارد که جایگزین مناسبی برای آن‌ها در دسترس نیست، همانطور که در مقاله‌ی `execCommand()` اشاره شده است. در این موارد، ممکن است این متد برای پیاده‌سازی یک تجربه‌ی کاربری کامل مفید واقع شود، اما حتماً سازگاری بین مرورگرها را آزمایش کنید.

متد **`queryCommandState()`** به شما می‌گوید که آیا یک فرمان خاص از {{domxref("Document.execCommand()")}} روی انتخاب فعلی اعمال شده است یا نه.

## نحو

```js-nolint
queryCommandState(command)
```

### پارامترها

- `command`
  - : یک فرمان از {{domxref("Document.execCommand()")}}

### مقدار بازگشتی

`queryCommandState()` می‌تواند یک مقدار بولی (boolean) یا `null` را در صورت نامشخص بودن وضعیت بازگرداند.

## مثال

### HTML

```html
<div contenteditable="true">Select a part of this text!</div>
<button>Test the state of the 'bold' command</button>
<hr />
<div id="output"></div>
```

```css hidden
hr,
button {
  margin: 1rem 0;
}
```

### JavaScript

```js
function makeBold() {
  const state = document.queryCommandState("bold");
  let message;
  switch (state) {
    case true:
      message = "The bold formatting will be removed from the selected text.";
      break;
    case false:
      message = "The selected text will be displayed in bold.";
      break;
    default:
      message = "The state of the 'bold' command is indeterminable.";
      break;
  }
  document.querySelector("#output").textContent = `Output: ${message}`;
  document.execCommand("bold");
}

document.querySelector("button").addEventListener("click", makeBold);
```

### نتیجه

{{EmbedLiveSample('Example', '100', '180')}}

## مشخصات

این ویژگی بخشی از هیچ مشخصات فعلی نیست. دیگر در مسیر تبدیل شدن به یک استاندارد قرار ندارد. یک پیش‌نویس غیررسمی از [W3C execCommand spec draft](https://w3c.github.io/editing/docs/execCommand/) وجود دارد.

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLElement.contentEditable")}}
- {{domxref("document.designMode")}}
- {{domxref("document.execCommand()")}}
- اشکالات مرورگر مرتبط با `queryCommandState()`: [Scribe's "Browser Inconsistencies" documentation](https://github.com/guardian/scribe/blob/master/BROWSERINCONSISTENCIES.md#documentquerycommandstate)