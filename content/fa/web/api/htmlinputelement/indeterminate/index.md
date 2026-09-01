---
title: "HTMLInputElement: indeterminate property"
short-title: indeterminate
slug: Web/API/HTMLInputElement/indeterminate
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.indeterminate
---

{{APIRef("HTML DOM")}}

خاصیت **`indeterminate`** از رابط {{domxref("HTMLInputElement")}} یک مقدار بولی (boolean) برمی‌گرداند که نشان می‌دهد آیا چک‌باکس در حالت _نامعین_ (indeterminate) است. برای مثال، یک چک‌باکس «انتخاب همه/لغو انتخاب همه» ممکن است زمانی که برخی از زیرکنترل‌های آن انتخاب شده‌اند اما نه همه، در حالت نامعین باشد. حالت `indeterminate` فقط از طریق جاوااسکریپت قابل تنظیم است و فقط برای کنترل‌های [`checkbox`](/en-US/docs/Web/HTML/Reference/Elements/input/checkbox) کاربرد دارد.

این خاصیت به خاصیت {{domxref("HTMLInputElement.checked")}} ارتباطی ندارد و یک چک‌باکس نامعین می‌تواند هم انتخاب‌شده (checked) و هم انتخاب‌نشده (unchecked) باشد. حالت نامعین فقط بر ظاهر چک‌باکس تأثیر می‌گذارد (مثال زیر را ببینید)، نه بر وجود آن هنگام ارسال (که توسط وضعیت انتخاب‌شدگی کنترل می‌شود).

## مقدار

یک مقدار بولی.

## مثال‌ها

```html
<input type="checkbox" id="indeterminate-checkbox" />
<label for="indeterminate-checkbox">Indeterminate checkbox</label>
```

```js
const checkbox = document.getElementById("indeterminate-checkbox");
checkbox.indeterminate = true;
```

{{EmbedLiveSample("examples", "", 200)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLInputElement")}}
- {{domxref("HTMLInputElement.checked")}}
- {{HTMLElement("input")}}
- [چک‌باکس‌های حالت نامعین](/en-US/docs/Web/HTML/Reference/Elements/input/checkbox#indeterminate_state_checkboxes)
- خاصیت CSS {{cssxref(":indeterminate")}}