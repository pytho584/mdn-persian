---
title: "accesskey HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/accesskey"
translated_by: "n8n + AI"
---

ویژگی سراسری `accesskey` راهنمایی برای ایجاد میانبر صفحه‌کلید برای عنصر فعلی ارائه می‌دهد. مقدار این ویژگی باید یک کاراکتر قابل چاپ (شامل حروف دارای اعراب و سایر کاراکترهایی که می‌توان با صفحه‌کلید تولید کرد) باشد.

{{InteractiveExample("HTML Demo: accesskey", "tabbed-shorter")}}

```html interactive-example
<p>If you need to relax, press the <b>S</b>tress reliever!</p>
<button accesskey="s">Stress reliever</button>
```

```css interactive-example
b {
  text-decoration: underline;
}
```

روش فعال‌سازی `accesskey` به مرورگر و سیستم‌عامل بستگی دارد:

<table class="standard-table">
  <tbody>
    <tr>
      <th></th>
      <th>ویندوز</th>
      <th>لینوکس</th>
      <th>مک</th>
    </tr>
    <tr>
      <th>Firefox</th>
      <td colspan="2"><kbd>Alt</kbd> + <kbd>Shift</kbd> + <kbd><em>key</em></kbd></td>
      <td>
        <kbd>Control</kbd> + <kbd>Option</kbd> +
        <kbd><em>key</em></kbd> یا <kbd>Control</kbd> + <kbd>Alt</kbd> +
        <kbd><em>key</em></kbd>
      </td>
    </tr>
    <tr>
      <th>Microsoft Edge</th>
      <td rowspan="2"><kbd>Alt</kbd> + <kbd><em>key</em></kbd></td>
      <td rowspan="2">
        <kbd>Control</kbd> + <kbd>Option</kbd> + <kbd><em>key</em></kbd><br>یا <kbd>Control</kbd> + <kbd>Option</kbd> + <kbd>Shift</kbd> +
        <kbd><em>key</em></kbd>
      </td>
      <td rowspan="2"><kbd>Control</kbd> + <kbd>Option</kbd> + <kbd><em>key</em></kbd></td>
    </tr>
    <tr>
      <th>Google Chrome</th>
    </tr>
    <tr>
      <th>Safari</th>
      <td colspan="2">—</td>
      <td><kbd>Control</kbd> + <kbd>Option</kbd> + <kbd><em>key</em></kbd></td>
    </tr>
    <tr>
      <th>Opera</th>
      <td><kbd>Alt</kbd> + <kbd><em>key</em></kbd></td>
      <td><kbd>Alt</kbd> + <kbd>Shift</kbd> + <kbd><em>key</em></kbd></td>
      <td><kbd>Control</kbd> + <kbd>Alt</kbd> + <kbd><em>key</em></kbd></td>
    </tr>
  </tbody>
</table>

## ملاحظات دسترسی‌پذیری

استفاده از ویژگی `accesskey` با مشکلات متعددی همراه است:

- مقدار `accesskey` ممکن است با میانبر صفحه‌کلید سیستم یا مرورگر، یا با قابلیت‌های فناوری کمکی تضاد داشته باشد. چیزی که برای یک ترکیب از سیستم‌عامل، فناوری کمکی و مرورگر کار می‌کند، ممکن است برای ترکیب‌های دیگر کار نکند.
- برخی مقادیر `accesskey` ممکن است روی صفحه‌کلیدهای خاصی موجود نباشند، به‌ویژه وقتی بحث بین‌المللی‌سازی مطرح باشد. بنابراین تطبیق با زبان‌های خاص می‌تواند مشکلات بیشتری ایجاد کند.
- مقادیر `accesskey` که بر اساس اعداد هستند ممکن است برای افرادی که مشکلات شناختی دارند گیج‌کننده باشد، زیرا عدد ارتباط منطقی با عملکردی که فعال می‌کند ندارد.
- کاربر باید از وجود `accesskey`ها مطلع شود تا بتواند از این قابلیت استفاده کند. اگر سیستمی روشی برای اطلاع‌رسانی به کاربر در مورد این ویژگی نداشته باشد، کاربر ممکن است ناخواسته `accesskey`ها را فعال کند.

به دلیل این مشکلات، معمولاً توصیه می‌شود برای اکثر وب‌سایت‌ها و برنامه‌های وب عمومی از `accesskey` استفاده نکنید.

- [WebAIM: دسترسی‌پذیری صفحه‌کلید - Accesskey](https://webaim.org/techniques/keyboard/accesskey#spec)

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLElement.accessKey")}}
- {{domxref("HTMLElement.accessKeyLabel")}}
- تمام [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes).
- [`aria-keyshortcuts`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-keyshortcuts)