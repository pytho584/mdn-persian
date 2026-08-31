---
title: "CommandEvent: command property"
---

---
title: "CommandEvent: command property"
short-title: command
slug: Web/API/CommandEvent/command
page-type: web-api-instance-property
browser-compat: api.CommandEvent.command
---

{{APIRef("Invoker Commands API")}}

خاصیت فقط خواندنی **`command`** از رابط {{domxref("CommandEvent")}} یک رشته حاوی مقدار خاصیت {{domxref("HTMLButtonElement.command", "command")}} در زمان ارسال رویداد را برمی‌گرداند.

## Value

یک رشته.

## Examples

در مثال ساده زیر، یک شنونده رویداد برای گوش دادن به دستور "show-modal" تنظیم کرده‌ایم:

```js
document.body.addEventListener(
  "command",
  (event) => {
    const theAction = event.command;

    if (theAction === "show-modal") {
      console.log("Showing modal dialog");
    }
  },
  { capture: true },
);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Invoker Commands API", "Invoker Commands API", "", "nocode")}}
- {{domxref("HTMLButtonElement.command")}}
- {{domxref("HTMLButtonElement.commandForElement")}}