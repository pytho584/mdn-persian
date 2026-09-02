```yaml
---
title: "KeyframeEffect: setKeyframes() method"
short-title: setKeyframes()
slug: Web/API/KeyframeEffect/setKeyframes
page-type: web-api-instance-method
browser-compat: api.KeyframeEffect.setKeyframes
---

{{ APIRef("Web Animations") }}

متد **`setKeyframes()`** از رابط {{domxref("KeyframeEffect")}}، فریم‌های کلیدی (keyframes) تشکیل‌دهنده‌ی `KeyframeEffect` مورد نظر را با یک مجموعه فریم کلیدی جدید جایگزین می‌کند.

## نحو (Syntax)

```js-nolint
setKeyframes(keyframes)
```

### پارامترها

- `keyframes`
  - : یک شیء فریم کلیدی یا `null`. اگر `null` تنظیم شود، فریم‌های کلیدی با دنباله‌ای از فریم‌های کلیدی خالی جایگزین می‌شوند.
    اطلاعات بیشتر درباره [قالب](/en-US/docs/Web/API/Web_Animations_API/Keyframe_Formats#syntax) یک شیء فریم کلیدی.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها (Exceptions)

<table class="no-markdown">
  <thead>
    <tr>
      <th scope="col">استثنا</th>
      <th scope="col">توضیح</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>TypeError</code></td>
      <td>
        یک یا چند فریم از نوع صحیح شیء نبودند، فریم‌های کلیدی
        <a href="https://w3c.github.io/web-animations/#loosely-sorted-by-offset"
          >بر اساس offset به صورت تقریبی مرتب نشده بودند</a
        >، یا فریم کلیدی با offset کمتر از 0 یا بیشتر از 1 وجود داشت.
      </td>
    </tr>
  </tbody>
</table>

> [!NOTE]
> اگر فریم‌های کلیدی قابل پردازش نباشند یا بد فرمت (malformed) باشند، فریم‌های کلیدی `KeyframeEffect` تغییر نمی‌کنند.

## مثال‌ها

```js
// عبور دادن یک آرایه از اشیاء فریم کلیدی
existingKeyframeEffect.setKeyframes([
  { color: "blue" },
  { color: "green", left: "10px" },
]);

// عبور دادن یک شیء با آرایه‌هایی برای مقادیر
existingKeyframeEffect.setKeyframes({
  color: ["blue", "green"],
  left: ["0", "10px"],
});

// عبور دادن یک شیء تک عضوی
existingKeyframeEffect.setKeyframes({
  color: "blue",
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [رابط KeyframeEffect](/en-US/docs/Web/API/KeyframeEffect)
- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
```