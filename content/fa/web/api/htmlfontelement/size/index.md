---
title: "HTMLFontElement: size property"
short-title: size
slug: Web/API/HTMLFontElement/size
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLFontElement.size
---

{{deprecated_header}}{{ APIRef("HTML DOM") }}

ویژگی منسوخ‌شده **`HTMLFontElement.size`** یک رشته است که صفت HTML [`size`](/en-US/docs/Web/HTML/Reference/Elements/font#size) را منعکس می‌کند. این ویژگی شامل یک اندازه قلم از ۱ تا ۷، یا یک عدد نسبی نسبت به مقدار پیش‌فرض ۳ (مثلاً ۲- یا ۱+) است.

قالب رشته باید از یکی از ریز-نحوهای HTML زیر پیروی کند:

<table class="no-markdown">
  <thead>
    <tr>
      <th scope="col">ریز-نحو</th>
      <th scope="col">توضیحات</th>
      <th scope="col">مثال‌ها</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>رشته شماره اندازه معتبر</td>
      <td><em>عدد صحیح در بازه ۱ تا ۷</em></td>
      <td><code>6</code></td>
    </tr>
    <tr>
      <td>رشته اندازه نسبی</td>
      <td>
        <em>+x یا -x، که در آن x عددی نسبی نسبت به ۳ است (نتیجه باید در بازه ۱ تا ۷ باشد)</em>
      </td>
      <td>
        <code>+2<br />-1</code>
      </td>
    </tr>
  </tbody>
</table>

## مقدار

یک رشته.

## مثال‌ها

```js
// فرض می‌شود که عنصر <font id="f"> در HTML وجود دارد
const f = document.getElementById("f");
f.size = "6";
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("HTMLFontElement")}} که این ویژگی به آن تعلق دارد.