---
title: "InputEvent: getTargetRanges() method"
short-title: getTargetRanges()
slug: Web/API/InputEvent/getTargetRanges
page-type: web-api-instance-method
browser-compat: api.InputEvent.getTargetRanges
---

{{APIRef("UI Events")}}

متد **`getTargetRanges()`** از رابط {{domxref("InputEvent")}} یک آرایه از اشیاء {{domxref("StaticRange")}} برمی‌گرداند که در صورت عدم لغو رویداد ورودی، تحت تأثیر تغییر در DOM قرار خواهند گرفت.

این امکان را به برنامه‌های وب می‌دهد تا قبل از اینکه مرورگر درخت DOM را تغییر دهد، رفتار ویرایش متن را نادیده بگیرند و کنترل بیشتری روی رویدادهای ورودی برای بهبود عملکرد فراهم می‌کند.

بسته به مقدار `inputType` و میزبان ویرایش فعلی، مقدار بازگشتی مورد انتظار این متد متفاوت است:

<table>
  <thead>
    <tr>
      <th>inputType</th>
      <th>میزبان ویرایش</th>
      <th>پاسخ <code>getTargetRanges()</code></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>"historyUndo"</code> یا <code>"historyRedo"</code></td>
      <td>هر</td>
      <td>آرایه خالی</td>
    </tr>
    <tr>
      <td>سایر موارد</td>
      <td><code>contenteditable</code></td>
      <td>
        یک آرایه از اشیاء
        {{domxref("StaticRange")}}
        مرتبط با رویداد
      </td>
    </tr>
    <tr>
      <td>سایر موارد</td>
      <td>
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input"><code>input</code></a>
        یا <a href="/en-US/docs/Web/HTML/Reference/Elements/textarea"><code>textarea</code></a>
      </td>
      <td>
        یک آرایه خالی
      </td>
    </tr>
  </tbody>
</table>

## Syntax

```js-nolint
getTargetRanges()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک آرایه از اشیاء {{domxref("StaticRange")}}.

## مثال‌ها

### تشخیص ویژگی

تابع زیر `true` را برمی‌گرداند اگر `beforeinput` و در نتیجه `getTargetRanges` پشتیبانی شود.

```js
function isBeforeInputEventAvailable() {
  return (
    window.InputEvent &&
    typeof InputEvent.prototype.getTargetRanges === "function"
  );
}
```

### استفاده پایه

مثال زیر یک عنصر `contenteditable` را انتخاب کرده و از رویداد
[`beforeinput`](/en-US/docs/Web/API/Element/beforeinput_event)
برای ثبت نتیجه `getTargetRanges()` استفاده می‌کند.

```js
const editableElem = document.querySelector('[contenteditable="true"]');

editableElem.addEventListener("beforeinput", (e) => {
  const targetRanges = e.getTargetRanges();
  console.log(targetRanges);
});
```

## Specifications

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}