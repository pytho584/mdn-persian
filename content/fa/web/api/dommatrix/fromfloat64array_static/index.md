---
title: "DOMMatrix: fromFloat64Array() static method"
---

---
title: "DOMMatrix: fromFloat64Array() static method"
short-title: fromFloat64Array()
slug: Web/API/DOMMatrix/fromFloat64Array_static
page-type: web-api-static-method
browser-compat: api.DOMMatrix.fromFloat64Array_static
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

**`fromFloat64Array()`** 静态方法，来自 {{domxref("DOMMatrix")}} 接口，根据一个双精度（64位）浮点值数组创建新的 {{domxref("DOMMatrix")}} 对象。

如果数组有 6 个值，结果是一个 2D 矩阵；如果数组有 16 个值，结果是一个 3D 矩阵。否则，抛出 {{jsxref("TypeError")}} 异常。

## 语法

```js-nolint
DOMMatrix.fromFloat64Array(array)
```

### 参数

- `array`
  - : 一个 {{jsxref("Float64Array")}}，按列主序包含 6 或 16 个元素。

### 返回值

一个 {{domxref("DOMMatrix")}} 对象。

### 异常

- {{jsxref("TypeError")}}
  - : 如果 `array` 参数的长度不是 6 或 16，则抛出。

## 示例

### 从 Float64Array 创建 2D 矩阵

此示例从包含 6 个元素的 `Float64Array` 创建一个 2D 矩阵。

```js
const float64Array = new Float64Array([1, 0, 0, 1, 10, 20]);
const matrix2D = DOMMatrix.fromFloat64Array(float64Array);

console.log(matrix2D.toString());
// Output: matrix(1, 0, 0, 1, 10, 20)

console.log(matrix2D.is2D);
// Output: true

console.log(matrix2D.e, matrix2D.f);
// Output: 10 20
```

### 从 Float64Array 创建 3D 矩阵

此示例从包含 16 个元素的 `Float64Array` 创建一个 3D 矩阵。

```js
const float64Array = new Float64Array([
  1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 10, 20, 30, 1,
]);
const matrix3D = DOMMatrix.fromFloat64Array(float64Array);

console.log(matrix3D.is2D);
// Output: false

console.log(matrix3D.m41, matrix3D.m42, matrix3D.m43);
// Output: 10 20 30
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("DOMMatrix/DOMMatrix", "DOMMatrix()")}}
- {{domxref("DOMMatrixReadOnly.toFloat32Array()")}}
- {{domxref("DOMMatrixReadOnly.toFloat64Array()")}}
- {{domxref("DOMMatrix.fromFloat32Array_static", "DOMMatrix.fromFloat32Array()")}}
- {{domxref("DOMMatrix.fromMatrix_static", "DOMMatrix.fromMatrix()")}}