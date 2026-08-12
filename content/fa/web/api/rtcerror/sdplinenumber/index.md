---
title: "RTCError: sdpLineNumber property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/RTCError/sdpLineNumber"
status: "needs-translation"
---

---
title: "RTCError: sdpLineNumber property"
short-title: sdpLineNumber
slug: Web/API/RTCError/sdpLineNumber
page-type: web-api-instance-property
browser-compat: api.RTCError.sdpLineNumber
---

{{APIRef("WebRTC")}}

The **`sdpLineNumber`** read-only property of the {{domxref("RTCError")}} interface specifies the {{Glossary("SDP")}} message line number where a syntax error occurred.

## Value

An integer value indicating the SDP message line number where the syntax error described by the `RTCError` object occurred.
The lines are numbered starting with line 1.

This property is `null` unless the value of {{domxref("RTCError.errorDetail", "errorDetail")}} is `sdp-syntax-error`.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
