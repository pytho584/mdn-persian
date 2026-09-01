---
title: "DOMTokenList: supports() method"
short-title: supports()
slug: Web/API/DOMTokenList/supports
page-type: web-api-instance-method
browser-compat: api.DOMTokenList.supports
---

{{APIRef("DOM")}}

**`supports()`** 메서드는 {{domxref("DOMTokenList")}} 인터페이스의 메서드로, 주어진 `token`이 연관 속성의 지원되는 토큰 목록에 있으면 `true`를 반환합니다. 이 메서드는 기능 감지를 지원하기 위한 것입니다.

## 구문

```js-nolint
supports(token)
```

### 매개변수

- `token`
  - : 쿼리할 토큰을 포함하는 문자열입니다.

### 반환 값

토큰이 발견되었는지 여부를 나타내는 불리언 값입니다.

## 예제

```js
const iframe = document.getElementById("display");

if (iframe.sandbox.supports("an-upcoming-feature")) {
  // support code for mystery future feature
} else {
  // fallback code
}

if (iframe.sandbox.supports("allow-scripts")) {
  // instruct frame to run JavaScript
  //
  // (NOTE: This feature is well-supported; this is just an example!)
  //
}
```

## 명세

{{Specifications}}

## 브라우저 호환성

{{Compat}}