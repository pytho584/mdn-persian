---
title: "Element: setAttributeNodeNS() method"
short-title: setAttributeNodeNS()
slug: Web/API/Element/setAttributeNodeNS
page-type: web-api-instance-method
browser-compat: api.Element.setAttributeNodeNS
---

{{ APIRef("DOM") }}

متد **`setAttributeNodeNS()`** در رابط {{domxref("Element")}} یک گره {{domxref("Attr")}} نام‌فضایی جدید به یک عنصر اضافه می‌کند.

اگر قبل از اضافه کردن نیازی به کار با گره ویژگی (مثلاً برای شبیه‌سازی از یک عنصر دیگر) ندارید، می‌توانید از متد {{domxref("Element.setAttributeNS()", "setAttributeNS()")}} استفاده کنید.

اگر با اسناد HTML کار می‌کنید و نیازی به مشخص کردن ویژگی درخواستی به‌عنوان بخشی از یک نام‌فضای خاص ندارید، از متد {{domxref("Element.setAttribute()", "setAttribute()")}} استفاده کنید.

## Syntax

```js-nolint
setAttributeNodeNS(attributeNode)
```

### Parameters

- `attributeNode`
  - : گره {{domxref("Attr")}} که قرار است به عنصر اضافه شود.

### Return value

گره ویژگی جایگزین‌شده، در صورت وجود، که توسط این تابع برگردانده می‌شود.

## Examples

```js
// <div id="one" xmlns:myNS="http://www.mozilla.org/ns/specialspace"
//            myNS:special-align="utterleft">one</div>
// <div id="two">two</div>

const myns = "http://www.mozilla.org/ns/specialspace";
const d1 = document.getElementById("one");
const d2 = document.getElementById("two");
const a = d1.getAttributeNodeNS(myns, "special-align");
d2.setAttributeNodeNS(a.cloneNode(true));
alert(d2.attributes[1].value); // returns: `utterleft'
```

## Notes

اگر ویژگی مشخص‌شده از قبل روی عنصر وجود داشته باشد، آن ویژگی با ویژگی جدید جایگزین می‌شود و ویژگی جایگزین‌شده برگردانده می‌شود.

توجه داشته باشید که اگر بخواهید بدون شبیه‌سازی (clone) کردن گره، آن را تنظیم کنید، ممکن است خطای `NS_ERROR_DOM_INUSE_ATTRIBUTE_ERR` «ویژگی در حال استفاده است» را ببینید؛ زیرا DOM برای استفاده مجدد از {{domxref("Attr")}} نیاز به شبیه‌سازی دارد (برخلاف سایر گره‌ها که می‌توانند جابه‌جا شوند).

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Document.createAttribute()")}}
- {{domxref("Document.createAttributeNS()")}}
- {{domxref("Element.getAttributeNodeNS()")}}