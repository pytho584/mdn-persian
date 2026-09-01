---
title: "DOMMatrixReadOnly: fromMatrix() static method"
short-title: fromMatrix()
slug: Web/API/DOMMatrixReadOnly/fromMatrix_static
page-type: web-api-static-method
browser-compat: api.DOMMatrixReadOnly.fromMatrix_static
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد ایستای **`fromMatrix()`** از رابط {{domxref("DOMMatrixReadOnly")}} یک شیء جدید {{domxref("DOMMatrixReadOnly")}} ایجاد می‌کند، با گرفتن یک ماتریس موجود یا یک شیء که مقادیر ویژگی‌های آن را فراهم می‌کند.

## نحو

```js-nolint
DOMMatrixReadOnly.fromMatrix()
DOMMatrixReadOnly.fromMatrix(other)
```

### پارامترها

- `other` {{optional_inline}}
  - : یک {{domxref("DOMMatrix")}}، {{domxref("DOMMatrixReadOnly")}}، یا یک شیء با همان ویژگی‌ها. همه ویژگی‌ها به‌طور پیش‌فرض `0` هستند. ویژگی‌ها عبارت‌اند از:
    - `is2D`
      - : یک مقدار بولین (Boolean). `true` اگر ماتریس باید به‌صورت ماتریس دوبعدی ساخته شود. پیش‌فرض `false` است اگر حداقل یکی از `m13`، `m14`، `m23`، `m24`، `m31`، `m32`، `m34`، یا `m43` غیرصفر باشد، یا حداقل یکی از `m33` یا `m44` برابر با `1` نباشد؛ در غیر این صورت، پیش‌فرض `true` است.
    - `m11`, `m12`, `m13`, `m14`, `m21`, `m22`, `m23`, `m24`, `m31`, `m32`, `m33`, `m34`, `m41`, `m42`, `m43`, `m44`
      - : اعدادی که هر مؤلفه از یک ماتریس ۴×۴ را نشان می‌دهند، که در آن `m11` تا `m14` ستون اول، `m21` تا `m24` ستون دوم، و به همین ترتیب هستند. `m11`, `m22`, `m33`, و `m44` پیش‌فرض `1` دارند و همه مؤلفه‌های دیگر پیش‌فرض `0` دارند.

        اگر `is2D` به صراحت روی `true` تنظیم شود، `m13`, `m14`, `m23`, `m24`, `m31`, `m32`, `m34`, یا `m43` باید یا حذف شوند یا روی `0` تنظیم شوند، و `m33` و `m44` باید یا حذف شوند یا روی `1` تنظیم شوند.

    - `a`, `b`, `c`, `d`, `e`, `f`
      - : به ترتیب نام‌های مستعار برای `m11`, `m12`, `m21`, `m22`, `m41`, و `m42` هستند، برای سهولت هنگام مقداردهی اولیه ماتریس‌های دوبعدی. اگر این نام‌های مستعار همراه با معادل‌های `m` ارائه شوند، مقادیر آن‌ها باید برابر باشند.

### مقدار بازگشتی

یک شیء {{domxref("DOMMatrixReadOnly")}}.

### استثناها

- {{jsxref("TypeError")}}
  - : پرتاب می‌شود اگر ویژگی‌های شیء ارائه‌شده ناسازگار باشند (برای مثال، اگر هر دو `a` و `m11` ارائه شده باشند اما مقادیر متفاوتی داشته باشند).

## نمونه‌ها

### ایجاد ماتریس از روی یک شیء

این مثال یک `DOMMatrixReadOnly` را با ارائه مقادیر ماتریس در یک شیء ایجاد می‌کند.

```js
const matrix = DOMMatrixReadOnly.fromMatrix({
  a: 1,
  b: 0,
  c: 0,
  d: 1,
  e: 50,
  f: 50,
  is2D: true,
});

console.log(matrix.toString());
// Output: matrix(1, 0, 0, 1, 50, 50)

console.log(matrix.is2D);
// Output: true
```

### ایجاد ماتریس از روی یک ماتریس موجود

این مثال یک `DOMMatrixReadOnly` جدید را از یک `DOMMatrixReadOnly` موجود ایجاد می‌کند.

```js
const matrix1 = new DOMMatrixReadOnly([1, 0, 0, 1, 100, 100]);
const matrix2 = DOMMatrixReadOnly.fromMatrix(matrix1);

console.log(matrix2.toString());
// Output: matrix(1, 0, 0, 1, 100, 100)
```

### ایجاد ماتریس همانی پیش‌فرض

این مثال نشان می‌دهد که چگونه فراخوانی `fromMatrix()` بدون آرگومان، یک ماتریس همانی ایجاد می‌کند.

```js
const identityMatrix = DOMMatrixReadOnly.fromMatrix();

console.log(identityMatrix.toString());
// Output: matrix(1, 0, 0, 1, 0, 0)

console.log(identityMatrix.isIdentity);
// Output: true
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- سازنده {{domxref("DOMMatrixReadOnly.DOMMatrixReadOnly", "DOMMatrixReadOnly()")}}
- {{domxref("DOMMatrixReadOnly.fromFloat32Array_static", "DOMMatrixReadOnly.fromFloat32Array()")}}
- {{domxref("DOMMatrixReadOnly.fromFloat64Array_static", "DOMMatrixReadOnly.fromFloat64Array()")}}