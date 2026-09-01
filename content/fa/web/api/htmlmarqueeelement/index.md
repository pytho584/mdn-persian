---
title: "HTMLMarqueeElement"
---

---
title: HTMLMarqueeElement
slug: Web/API/HTMLMarqueeElement
page-type: web-api-interface
status:
  - deprecated
browser-compat: api.HTMLMarqueeElement
---

{{APIRef("HTML DOM")}}{{Deprecated_Header}}

رابطِ **`HTMLMarqueeElement`** روش‌هایی برای کار با عناصر {{HTMLElement("marquee")}} فراهم می‌کند.

این رابط، ویژگی‌ها و روش‌ها را از رابط {{DOMxRef("HTMLElement")}} به ارث می‌برد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌های والد خود، {{DOMxRef("HTMLElement")}} را به ارث می‌برد._

- `HTMLMarqueeElement.behavior` {{Deprecated_Inline}}
  - : نحوهٔ اسکرول متن را در داخل marquee تعیین می‌کند. مقادیر ممکن عبارتند از `scroll`، `slide` و `alternate`. اگر مقداری مشخص نشود، مقدار پیش‌فرض `scroll` است.
- `HTMLMarqueeElement.bgColor` {{Deprecated_Inline}}
  - : رنگ پس‌زمینه را از طریق نام رنگ یا مقدار هگزادسیمال تنظیم می‌کند.
- `HTMLMarqueeElement.direction` {{Deprecated_Inline}}
  - : جهت اسکرول را در داخل marquee تعیین می‌کند. مقادیر ممکن عبارتند از `left`، `right`، `up` و `down`. اگر مقداری مشخص نشود، مقدار پیش‌فرض `left` است.
- `HTMLMarqueeElement.height` {{Deprecated_Inline}}
  - : ارتفاع را بر حسب پیکسل یا مقدار درصدی تنظیم می‌کند.
- `HTMLMarqueeElement.hspace` {{Deprecated_Inline}}
  - : حاشیهٔ افقی را تنظیم می‌کند.
- `HTMLMarqueeElement.loop` {{Deprecated_Inline}}
  - : تعداد دفعات اسکرول marquee را تعیین می‌کند. اگر مقداری مشخص نشود، مقدار پیش‌فرض −1 است، یعنی marquee به‌طور پیوسته اسکرول می‌شود.
- `HTMLMarqueeElement.scrollAmount` {{Deprecated_Inline}}
  - : مقدار اسکرول را در هر بازهٔ زمانی بر حسب پیکسل تعیین می‌کند. مقدار پیش‌فرض 6 است.
- `HTMLMarqueeElement.scrollDelay` {{Deprecated_Inline}}
  - : فاصلهٔ زمانی بین هر حرکت اسکرول را بر حسب میلی‌ثانیه تعیین می‌کند. مقدار پیش‌فرض 85 است. توجه داشته باشید که هر مقدار کمتر از 60 نادیده گرفته می‌شود و به جای آن از مقدار 60 استفاده می‌شود، مگر اینکه `trueSpeed` برابر `true` باشد.
- `HTMLMarqueeElement.trueSpeed` {{Deprecated_Inline}}
  - : به‌طور پیش‌فرض، مقادیر `scrollDelay` کمتر از 60 نادیده گرفته می‌شوند. اگر `trueSpeed` برابر `true` باشد، این مقادیر نادیده گرفته نمی‌شوند.
- `"HTMLMarqueeElement.vspace` {{Deprecated_Inline}}
  - : حاشیهٔ عمودی را تنظیم می‌کند.
- `HTMLMarqueeElement.width` {{Deprecated_Inline}}
  - : عرض را بر حسب پیکسل یا مقدار درصدی تنظیم می‌کند.

## روش‌های نمونه

_روش‌های والد خود، {{DOMxRef("HTMLElement")}} را به ارث می‌برد._

- `HTMLMarqueeElement.start()` {{Deprecated_Inline}}
  - : اسکرول marquee را شروع می‌کند.
- `HTMLMarqueeElement.stop()` {{Deprecated_Inline}}
  - : اسکرول marquee را متوقف می‌کند.

## رویدادها

- `bounce` {{Deprecated_Inline}}
  - : زمانی که marquee به انتهای موقعیت اسکرول خود می‌رسد، فعال می‌شود. این رویداد فقط زمانی می‌تواند فعال شود که ویژگی behavior روی `alternate` تنظیم شده باشد.
- `finish` {{Deprecated_Inline}}
  - : زمانی که marquee میزان اسکرول تعیین‌شده توسط ویژگی loop را به پایان برساند، فعال می‌شود. این رویداد فقط زمانی می‌تواند فعال شود که ویژگی loop روی عددی بزرگ‌تر از 0 تنظیم شده باشد.
- `start` {{Deprecated_Inline}}
  - : زمانی که marquee اسکرول را شروع می‌کند، فعال می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{HTMLElement("marquee")}}