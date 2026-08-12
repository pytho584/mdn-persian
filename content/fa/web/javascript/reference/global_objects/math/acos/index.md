---
title: "Math.acos()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/acos"
status: "needs-translation"
---

---
title: Math.acos()
short-title: acos()
slug: Web/JavaScript/Reference/Global_Objects/Math/acos
page-type: javascript-static-method
browser-compat: javascript.builtins.Math.acos
sidebar: jsref
---

The **`Math.acos()`** static method returns the inverse cosine (in radians) of a number. That is,

<!-- prettier-ignore-start -->
<math display="block">
  <semantics><mrow><mo>∀</mo><mi>x</mi><mo>∊</mo><mo stretchy="false">[</mo><mrow><mo>−</mo><mn>1</mn></mrow><mo>,</mo><mn>1</mn><mo stretchy="false">]</mo><mo>,</mo><mspace width="0.2777777777777778em"></mspace><mrow><mo lspace="0em" rspace="0.16666666666666666em">𝙼𝚊𝚝𝚑.𝚊𝚌𝚘𝚜</mo><mo stretchy="false">(</mo><mi>𝚡</mi><mo stretchy="false">)</mo></mrow><mo>=</mo><mo lspace="0em" rspace="0em">arccos</mo><mo stretchy="false">(</mo><mi>x</mi><mo stretchy="false">)</mo><mo>=</mo><mtext>the unique&nbsp;</mtext><mi>y</mi><mo>∊</mo><mo stretchy="false">[</mo><mn>0</mn><mo>,</mo><mi>π</mi><mo stretchy="false">]</mo><mtext>&nbsp;such that&nbsp;</mtext><mo lspace="0em" rspace="0em">cos</mo><mo stretchy="false">(</mo><mi>y</mi><mo stretchy="false">)</mo><mo>=</mo><mi>x</mi></mrow><annotation encoding="TeX">\forall x \in [{-1}, 1],\;\mathtt{\operatorname{Math.acos}(x)} = \arccos(x) = \text{the unique } y \in [0, \pi] \text{ such that } \cos(y) = x</annotation></semantics>
</math>
<!-- prettier-ignore-end -->

{{InteractiveExample("JavaScript Demo: Math.acos()")}}

```js interactive-example
// Calculates angle of a right-angle triangle in radians
function calcAngle(adjacent, hypotenuse) {
  return Math.acos(adjacent / hypotenuse);
}

console.log(calcAngle(8, 10));
// Expected output: 0.6435011087932843

console.log(calcAngle(5, 3));
// Expected output: NaN
```

## Syntax

```js-nolint
Math.acos(x)
```

### Parameters

- `x`
  - : A number between -1 and 1, inclusive, representing the angle's cosine value.

### Return value

The inverse cosine (angle in radians between 0 and π, inclusive) of `x`. If `x` is less than -1 or greater than 1, returns {{jsxref("NaN")}}.

## Description

Because `acos()` is a static method of `Math`, you always use it as `Math.acos()`, rather than as a method of a `Math` object you created (`Math` is not a constructor).

## Examples

### Using Math.acos()

```js
Math.acos(-2); // NaN
Math.acos(-1); // 3.141592653589793 (π)
Math.acos(0); // 1.5707963267948966 (π/2)
Math.acos(0.5); // 1.0471975511965979 (π/3)
Math.acos(1); // 0
Math.acos(2); // NaN
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{jsxref("Math.asin()")}}
- {{jsxref("Math.atan()")}}
- {{jsxref("Math.atan2()")}}
- {{jsxref("Math.cos()")}}
- {{jsxref("Math.sin()")}}
- {{jsxref("Math.tan()")}}
- CSS {{cssxref("acos()")}} function
