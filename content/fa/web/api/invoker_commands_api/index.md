---
title: Invoker Commands API
slug: Web/API/Invoker_Commands_API
page-type: web-api-overview
browser-compat:
  - api.CommandEvent
  - api.HTMLButtonElement.commandForElement
  - api.HTMLButtonElement.command
---

{{DefaultAPISidebar("Invoker Commands API")}}

**Invoker Commands API** راهی برای اختصاص اعلانی رفتارها به دکمه‌ها فراهم می‌کند و امکان کنترل عناصر تعاملی را هنگام فعال شدن دکمه (با کلیک کردن یا از طریق فشردن کلیدی مانند نوار فاصله یا کلید بازگشت) می‌دهد.

یک الگوی رایج در وب این است که عناصر {{HTMLElement("button")}} جنبه‌های مختلف صفحه را کنترل کنند، مانند باز و بسته کردن {{domxref("Popover API", "popovers", "", "nocode")}} یا عناصر {{HTMLElement("dialog")}}، قالب‌بندی متن و موارد بیشتر.

در گذشته، ایجاد این نوع کنترل‌ها مستلزم افزودن شنونده‌های رویداد جاوااسکریپت به دکمه بود که سپس می‌توانستند APIهای عنصر تحت کنترل را فراخوانی کنند. ویژگی‌های {{domxref("HTMLButtonElement.commandForElement", "commandForElement")}} و {{domxref("HTMLButtonElement.command", "command")}} راهی برای انجام این کار به صورت اعلانی برای مجموعه‌ای محدود از اقدامات فراهم می‌کنند. این موضوع می‌تواند برای فرمان‌های داخلی مفید باشد، زیرا کاربر برای تعاملی شدن این دکمه‌ها نیازی به انتظار برای دانلود و اجرای جاوااسکریپت ندارد.

## ویژگی‌های HTML

- [`commandfor`](/en-US/docs/Web/HTML/Reference/Elements/button#commandfor)
  - : یک عنصر {{htmlelement("button")}} را به فراخواننده فرمان (command invoker) تبدیل می‌کند و عنصر تعاملی مشخص‌شده را کنترل می‌کند؛ شناسه عنصر مورد کنترل را به عنوان مقدار خود می‌گیرد.
- [`command`](/en-US/docs/Web/HTML/Reference/Elements/button#command)
  - : اقدامی را که باید روی عنصری که توسط یک `<button>` کنترلی کنترل می‌شود انجام گیرد، مشخص می‌کند؛ این اقدام از طریق ویژگی `commandfor` تعیین می‌شود.

## رابط‌ها

- {{domxref("CommandEvent")}}
  - : نشان‌دهنده رویدادی است که به کاربر اطلاع می‌دهد فرمانی صادر شده است. این شیء رویداد برای رویداد {{domxref("HTMLElement/command_event", "command")}} است. رویداد روی عنصری که توسط {{domxref("HTMLButtonElement.commandForElement", "commandForElement")}} ارجاع شده است، رخ می‌دهد.

## افزونه‌های رابط‌های دیگر

### ویژگی‌های نمونه

- {{domxref("HTMLButtonElement.commandForElement")}}
  - : عنصر کنترل‌شده توسط دکمه را دریافت و تنظیم می‌کند. معادل جاوااسکریپتی ویژگی HTML [`commandfor`](/en-US/docs/Web/HTML/Reference/Elements/button#commandfor) است.
- {{domxref("HTMLButtonElement.command")}}
  - : اقدامی را که باید روی عنصر کنترل‌شده توسط دکمه انجام شود دریافت و تنظیم می‌کند. منعکس‌کننده مقدار ویژگی HTML [`command`](/en-US/docs/Web/HTML/Reference/Elements/button#command) است.

### رویدادها

- رویداد {{domxref("HTMLElement.command_event", "command")}}
  - : روی عنصری که توسط دکمه ارجاع شده است، رخ می‌دهد.

## مثال‌ها

### ایجاد پاپاورهای اعلانی

```html
<button commandfor="mypopover" command="toggle-popover">
  Toggle the popover
</button>
<div id="mypopover" popover>
  <button commandfor="mypopover" command="hide-popover">Close</button>
  Popover content
</div>
```

### ایجاد دیالوگ‌های اعلانی

```html
<button commandfor="mydialog" command="show-modal">Show modal dialog</button>
<dialog id="mydialog">
  <button commandfor="mydialog" command="close">Close</button>
  Dialog Content
</dialog>
```

### ایجاد فرمان‌های سفارشی

```html
<button commandfor="my-img" command="--rotate-left">Rotate left</button>
<button commandfor="my-img" command="--rotate-right">Rotate right</button>
<img id="my-img" src="photo.jpg" alt="[add appropriate alt text here]" />
```

```js
const myImg = document.getElementById("my-img");

myImg.addEventListener("command", (event) => {
  if (event.command === "--rotate-left") {
    myImg.style.rotate = "-90deg";
  } else if (event.command === "--rotate-right") {
    myImg.style.rotate = "90deg";
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## جستارهای وابسته

- ویژگی {{domxref("HTMLButtonElement.command", "command")}}
- ویژگی {{domxref("HTMLButtonElement.commandForElement", "commandForElement")}}
- رابط {{domxref("CommandEvent", "CommandEvent")}}