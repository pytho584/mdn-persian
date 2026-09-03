---
title: "Node: insertBefore() method"
short-title: insertBefore()
slug: Web/API/Node/insertBefore
page-type: web-api-instance-method
browser-compat: api.Node.insertBefore
---

{{APIRef("DOM")}}

متد **`insertBefore()`** از رابط {{domxref("Node")}} یک گره را به‌عنوان فرزندِ یک _گره والدِ_ مشخص، قبل از یک _گره مرجع_ درج می‌کند.

اگر گره داده‌شده از قبل در سند وجود داشته باشد، `insertBefore()` آن را از موقعیت فعلی‌اش به موقعیت جدید منتقل می‌کند. (یعنی به‌طور خودکار از والدِ فعلی خود حذف می‌شود و سپس به والدِ جدیدِ مشخص‌شده اضافه می‌گردد.)

بنابراین، یک گره نمی‌تواند هم‌زمان در دو مکان از سند قرار بگیرد.

> [!NOTE]
> برای کپی کردن گره قبل از افزودن آن به والدِ جدید می‌توان از {{domxref("Node.cloneNode()")}} استفاده کرد. توجه داشته باشید که کپی‌های ساخته‌شده با `cloneNode()` به‌طور خودکار با گره اصلی همگام نمی‌مانند.

اگر گره داده‌شده یک {{domxref("DocumentFragment")}} باشد، تمام محتوای آن `DocumentFragment` به فهرست فرزندانِ والدِ مشخص‌شده منتقل می‌شود.

## سینتکس

```js-nolint
insertBefore(newNode, referenceNode)
```

### پارامترها

- `newNode`
  - : گره‌ای که باید درج شود.
- `referenceNode`
  - : گره‌ای که `newNode` قبل از آن درج می‌شود. اگر این مقدار `null` باشد، `newNode` در انتهای فرزندانِ آن گره درج می‌شود.
    > [!NOTE]
    > `referenceNode` یک پارامتر **اختیاری نیست**.
    > باید به‌صراحت یک {{domxref("Node")}} یا `null` به آن پاس دهید.
    > اگر آن را ارائه ندهید یا مقادیر نامعتبر پاس دهید، ممکن است در نسخه‌های مختلف مرورگرها [رفتار](https://crbug.com/419780) [متفاوتی](https://bugzil.la/119489) داشته باشد.

### مقدار بازگشتی

فرزند اضافه‌شده را برمی‌گرداند؛ مگر اینکه `newNode` یک {{domxref("DocumentFragment")}} باشد که در آن صورت، {{domxref("DocumentFragment")}} خالی بازگردانده می‌شود.

### استثناها

اعتبار پیش از درج

## مثال

### مثال ۱

```html
<div id="parentElement">
  <span id="childElement">foo bar</span>
</div>
```

```js
// Create the new node to insert
const newNode = document.createElement("span");

// Get a reference to the parent node
const parentDiv = document.getElementById("childElement").parentNode;

// Begin test case [ 1 ] : Existing childElement (all works correctly)
let sp2 = document.getElementById("childElement");
parentDiv.insertBefore(newNode, sp2);
// End test case [ 1 ]

// Begin test case [ 2 ] : childElement is of Type undefined
sp2 = undefined; // Non-existent node of id "childElement"
parentDiv.insertBefore(newNode, sp2); // Implicit dynamic cast to type Node
// End test case [ 2 ]

// Begin test case [ 3 ] : childElement is of Type "undefined" (string)
sp2 = "undefined"; // Non-existent node of id "childElement"
parentDiv.insertBefore(newNode, sp2); // Generates "Type Error: Invalid Argument"
// End test case [ 3 ]
```

### مثال ۲

```html
<div id="parentElement">
  <span id="childElement">foo bar</span>
</div>
```

```js
// Create a new, plain <span> element
const sp1 = document.createElement("span");

// Get the reference element
const sp2 = document.getElementById("childElement");
// Get the parent element
const parentDiv = sp2.parentNode;

// Insert the new element into before sp2
parentDiv.insertBefore(sp1, sp2);
```

> [!NOTE]
> متد `insertAfter()` وجود ندارد.
> می‌توان آن را با ترکیب متد `insertBefore` و {{domxref("Node.nextSibling")}} شبیه‌سازی کرد.
>
> در مثال قبلی، می‌توان `sp1` را با کد زیر بعد از `sp2` درج کرد:
>
> ```js
> parentDiv.insertBefore(sp1, sp2.nextSibling);
> ```
>
> اگر `sp2` گره همسایه‌ی بعدی (`next sibling`) نداشته باشد، یعنی باید آخرین فرزند باشد؛ در این حالت، `sp2.nextSibling` مقدار `null` برمی‌گرداند و `sp1` در انتهای فهرست گره‌های فرزند، بلافاصله بعد از `sp2`، درج می‌شود.

### مثال ۳

یک عنصر را با استفاده از ویژگی {{domxref("Node/firstChild", "firstChild")}} قبل از اولین فرزند درج کنید.

```js
// Get the parent element
const parentElement = document.getElementById("parentElement");
// Get the parent's first child
const theFirstChild = parentElement.firstChild;

// Create a new element
const newElement = document.createElement("div");

// Insert the new element before the first child
parentElement.insertBefore(newElement, theFirstChild);
```

وقتی عنصر اولین فرزند را نداشته باشد، `firstChild` برابر `null` است. در این حالت، عنصر همچنان به والد اضافه می‌شود؛ یعنی بعد از آخرین فرزندِ والد قرار می‌گیرد.

چون والدِ موردنظر اولین فرزند را نداشته، آخرین فرزند را نیز نداشته است. در نتیجه، عنصر تازه‌درج‌شده، _تنها_ فرزند آن والد است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("Node.removeChild()")}}
- {{domxref("Node.replaceChild()")}}
- {{domxref("Node.appendChild()")}}
- {{domxref("Node.hasChildNodes()")}}
- {{domxref("Element.insertAdjacentElement()")}}
- {{domxref("Element.prepend()")}}
- {{domxref("Element.before()")}}
- {{domxref("Element.after()")}}
