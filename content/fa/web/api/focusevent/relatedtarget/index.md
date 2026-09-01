---
title: "FocusEvent: relatedTarget property"
short-title: relatedTarget
slug: Web/API/FocusEvent/relatedTarget
page-type: web-api-instance-property
browser-compat: api.FocusEvent.relatedTarget
---

{{APIRef("UI Events")}}

ویژگی فقطخواندنی **`relatedTarget`** در رابط {{domxref("FocusEvent")}} هدف ثانویه است که بسته به نوع رویداد متفاوت است:

<table class="no-markdown">
  <thead>
    <tr>
      <th scope="col">نام رویداد</th>
      <th scope="col"><code>target</code></th>
      <th scope="col"><code>relatedTarget</code></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>{{domxref("Element/blur_event", "blur")}}</td>
      <td>{{domxref("EventTarget")}} که فوکوس را از دست می‌دهد</td>
      <td>{{domxref("EventTarget")}} که فوکوس را دریافت می‌کند (در صورت وجود).</td>
    </tr>
    <tr>
      <td>{{domxref("Element/focus_event", "focus")}}</td>
      <td>{{domxref("EventTarget")}} که فوکوس را دریافت می‌کند</td>
      <td>{{domxref("EventTarget")}} که فوکوس را از دست می‌دهد (در صورت وجود)</td>
    </tr>
    <tr>
      <td>{{domxref("Element/focusin_event", "focusin")}}</td>
      <td>{{domxref("EventTarget")}} که فوکوس را دریافت می‌کند</td>
      <td>{{domxref("EventTarget")}} که فوکوس را از دست می‌دهد (در صورت وجود)</td>
    </tr>
    <tr>
      <td>{{domxref("Element/focusout_event", "focusout")}}</td>
      <td>{{domxref("EventTarget")}} که فوکوس را از دست می‌دهد</td>
      <td>{{domxref("EventTarget")}} که فوکوس را دریافت می‌کند (در صورت وجود)</td>
    </tr>
  </tbody>
</table>

توجه داشته باشید که [بسیاری از عناصر نمی‌توانند فوکوس بگیرند](https://stackoverflow.com/questions/42764494/blur-event-relatedtarget-returns-null/42764495) که دلیل رایجی برای `null` بودن `relatedTarget` است. همچنین `relatedTarget` ممکن است به دلایل امنیتی، مانند هنگام جابه‌جایی با Tab به داخل یا خارج از صفحه، `null` باشد.

{{domxref("MouseEvent.relatedTarget")}} ویژگی مشابهی برای رویدادهای ماوس است.

## مقدار

یک نمونه از {{domxref("EventTarget")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{ domxref("FocusEvent") }}
