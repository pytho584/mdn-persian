---
title: "DOMMatrix: fromMatrix() static method"
short-title: fromMatrix()
slug: Web/API/DOMMatrix/fromMatrix_static
page-type: web-api-static-method
browser-compat: api.DOMMatrix.fromMatrix_static
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد استاتیک **`fromMatrix()`** در رابط {{domxref("DOMMatrix")}} یک شیء {{domxref("DOMMatrix")}} جدید بر اساس یک ماتریس موجود یا شیئی که مقادیر ویژگی‌های آن را فراهم می‌کند، می‌سازد.

## Syntax

```js-nolint
DOMMatrix.fromMatrix()
DOMMatrix.fromMatrix(other)
```

### Parameters

- `other` {{optional_inline}}
  - : یک {{domxref("DOMMatrix")}}، {{domxref("DOMMatrixReadOnly")}}، یا شیئی با همان ویژگی‌ها. همهٔ ویژگی‌ها به‌صورت پیش‌فرض `0` هستند. ویژگی‌ها عبارت‌اند از:
    - `is2D`
      - : یک مقدار بولی. اگر ماتریس باید به‌عنوان یک ماتریس دوبعدی ساخته شود، `true` است. اگر حداقل یکی از `m13`، `m14`، `m23`، `m24`، `m31`، `m32`، `m34` یا `m43` غیرصفر باشد، یا حداقل یکی از `m33` یا `m44` برابر با `1` نباشد، مقدار پیش‌فرض `false` است؛ در غیر این صورت، پیش‌فرض `true` است.
    - `m11`، `m12`، `m13`، `m14`، `m21`، `m22`، `m23`، `m24`، `m31`، `m32`، `m33`، `m34`، `m41`، `m42`، `m43`، `m44`
      - : اعدادی که هر مؤلفهٔ یک ماتریس ۴×۴ را نشان می‌دهند؛ به‌طوری که `m11` تا `m14` ستون اول، `m21` تا `m24` ستون دوم، و به همین ترتیب هستند. `m11`، `m22`، `m33` و `m44` به‌صورت پیش‌فرض `1` هستند و همهٔ مؤلفه‌های دیگر به‌صورت پیش‌فرض `0` هستند.

        اگر `is2D` به‌صراحت روی `true` تنظیم شود، `m13`، `m14`، `m23`، `m24`، `m31`، `m32`، `m34` یا `m43` باید یا حذف شوند یا روی `0` تنظیم شوند، و `m33` و `m44` باید یا حذف شوند یا روی `1` تنظیم شوند.

    - `a`، `b`، `c`، `d`، `e`، `f`
      - : به‌ترتیب نام‌های مستعار برای `m11`، `m12`، `m21`، `m22`، `m41` و `m42` برای راحتی هنگام مقداردهی به ماتریس‌های دوبعدی. اگر این نام‌های مستعار همراه با همتای‌های `m` ارائه شوند، مقادیر آن‌ها باید برابر باشند.

### Return value

یک شیء {{domxref("DOMMatrix")}}.

### Exceptions

- {{jsxref("TypeError")}}
  - : اگر ویژگی‌های شیء ارائه‌شده ناسازگار باشند (مثلاً اگر هم `a` و هم `m11` ارائه شده باشند اما مقادیر متفاوتی داشته باشند)، پرتاب می‌شود.

## Examples

### ایجاد یک ماتریس از یک شیء

این مثال با ارائه‌دادن مقادیر ماتریس در یک شیء، یک `DOMMatrix` ایجاد می‌کند.

```js
const matrix = DOMMatrix.fromMatrix({
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

### ایجاد یک ماتریس از یک ماتریس موجود

این مثال یک `DOMMatrix` جدید از یک `DOMMatrix` موجود ایجاد می‌کند.

```js
const matrix1 = new DOMMatrix([1, 0, 0, 1, 100, 100]);
const matrix2 = DOMMatrix.fromMatrix(matrix1);

console.log(matrix2.toString());
// Output: matrix(1, 0, 0, 1, 100, 100)

// Now we can mutate it
matrix2.translateSelf(50, 25);

console.log(matrix2.toString());
// Output: matrix(1, 0, 0, 1, 150, 125)

console.log(matrix1.toString());
// Output: matrix(1, 0, 0, 1, 100, 100)
```

### ایجاد یک ماتریس همانی پیش‌فرض

این مثال نشان می‌دهد که چگونه فراخوانی `fromMatrix()` بدون آرگومان، یک ماتریس همانی ایجاد می‌کند.

```js
const identityMatrix = DOMMatrix.fromMatrix();

console.log(identityMatrix.toString());
// Output: matrix(1, 0, 0, 1, 0, 0)

console.log(identityMatrix.isIdentity);
// Output: true
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- سازندهٔ {{domxref("DOMMatrix.DOMMatrix", "DOMMatrix()")}}
- {{domxref("DOMMatrix.fromFloat32Array_static", "DOMMatrix.fromFloat32Array()")}}
- {{domxref("DOMMatrix.fromFloat64Array_static", "DOMMatrix.fromFloat64Array()")}}