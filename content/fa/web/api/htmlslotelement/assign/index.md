---
title: "HTMLSlotElement: assign() method"
short-title: assign()
slug: Web/API/HTMLSlotElement/assign
page-type: web-api-instance-method
browser-compat: api.HTMLSlotElement.assign
---

{{APIRef("Shadow DOM API")}}

متد **`assign()`** در رابط {{domxref("HTMLSlotElement")}}، گره‌های _اختصاص‌یافته دستی_ اسلات را به یک مجموعه مرتب از عناصر قابل‌اسلات (slottables) تنظیم می‌کند. مجموعه گره‌های اختصاص‌یافته دستی در ابتدا خالی است تا زمانی که گره‌ها با استفاده از `assign()` اختصاص داده شوند.

> [!NOTE]
> نمی‌توانید اختصاص اسلات دستی (امری) و نام‌گذاری‌شده (اعلانی، خودکار) را با هم ترکیب کنید. بنابراین، برای اینکه این متد کار کند، درخت سایه باید با گزینه `slotAssignment: "manual"` [ایجاد شده](/en-US/docs/Web/API/Element/attachShadow) باشد.

## نحو (Syntax)

```js-nolint
assign(node1)
assign(node1, node2)
assign(node1, node2, /* …, */ nodeN)
```

### پارامترها

- `node1`، …، `nodeN`
  - : مجموعه‌ای از گره‌های {{domxref("Element")}} یا {{domxref("Text")}}.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- `NotAllowedError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که این متد روی یک اسلات اختصاص‌یافته خودکار فراخوانی شود.

## مثال‌ها

در مثال زیر، از متد `assign()` برای نمایش تب صحیح در یک برنامه مبتنی بر تب استفاده شده است. این تابع فراخوانی می‌شود و پنل موردنظر برای نمایش به آن منتقل می‌شود، که سپس به اسلات اختصاص داده می‌شود.

```js
function UpdateDisplayTab(elem, tabIdx) {
  const shadow = elem.shadowRoot;
  const slot = shadow.querySelector("slot");
  const panels = elem.querySelectorAll("tab-panel");
  if (panels.length && tabIdx && tabIdx <= panels.length) {
    slot.assign(panels[tabIdx - 1]);
  } else {
    slot.assign();
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.attachShadow()")}}