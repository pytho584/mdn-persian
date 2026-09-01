---
title: "DOMQuad: DOMQuad() سازنده"
short-title: "DOMQuad()"
slug: Web/API/DOMQuad/DOMQuad
page-type: web-api-constructor
browser-compat: api.DOMQuad.DOMQuad
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

سازنده **`DOMQuad()`** یک شیء جدید {{domxref("DOMQuad")}} ایجاد و برمی‌گرداند. این سازنده مقادیر برخی یا تمام ویژگی‌های آن را می‌گیرد.

همچنین می‌توانید با استفاده از توابع استاتیک {{domxref("DOMQuad.fromRect_static", "DOMQuad.fromRect()")}} یا {{domxref("DOMQuad.fromQuad_static", "DOMQuad.fromQuad()")}} یک `DOMQuad` ایجاد کنید. این توابع هر شیءای را که پارامترهای مورد نیاز را داشته باشد، از جمله یک {{domxref("DOMRect")}}، {{domxref("DOMRectReadOnly")}}، یا یک `DOMQuad` دیگر، می‌پذیرند.

## نحو (Syntax)

```js-nolint
new DOMQuad()
new DOMQuad(p1)
new DOMQuad(p1, p2)
new DOMQuad(p1, p2, p3)
new DOMQuad(p1, p2, p3, p4)
```

### پارامترها

- {{domxref("DOMQuad/p1", "p1")}} {{optional_inline}}، {{domxref("DOMQuad/p2", "p2")}} {{optional_inline}}، {{domxref("DOMQuad/p3", "p3")}} {{optional_inline}}، {{domxref("DOMQuad/p4", "p4")}} {{optional_inline}}
  - : هر کدام یک {{domxref("DOMPoint")}} یا یک شیء با ویژگی‌های مشابه که نماینده یک گوشه از چهارضلعی است.

## مثال‌ها

این مثال یک `DOMQuad` با استفاده از یک {{domxref("DOMPoint")}} و سه نقطه اضافی که به عنوان اشیاء تعریف شده‌اند، ایجاد می‌کند.

```js
const point = new DOMPoint(2, 0);
const quad = new DOMQuad(
  point,
  { x: 12, y: 0 },
  { x: 12, y: 10 },
  { x: 2, y: 10 },
);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMPoint")}}
- {{domxref("DOMRect")}}
- {{domxref("DOMMatrix")}}