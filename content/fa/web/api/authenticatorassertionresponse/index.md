---
title: "AuthenticatorAssertionResponse"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AuthenticatorAssertionResponse"
translated_by: "n8n + AI"
---

---
title: AuthenticatorAssertionResponse
slug: Web/API/AuthenticatorAssertionResponse
page-type: web-api-interface
browser-compat: api.AuthenticatorAssertionResponse
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

[Web Authentication API](/en-US/docs/Web/API/Web_Authentication_API) 的 **`AuthenticatorAssertionResponse`** 接口包含来自特定 WebAuthn 凭据私钥的[数字签名](/en-US/docs/Glossary/Signature/Security)。依赖方的服务器可以验证此签名以认证用户，例如在用户登录时。

当一次成功的 {{domxref("CredentialsContainer.get()", "navigator.credentials.get()")}} 调用返回一个 {{domxref("PublicKeyCredential")}} 对象时，其 {{domxref("PublicKeyCredential.response", "response")}} 属性中即可获得一个 `AuthenticatorAssertionResponse` 对象实例。

此接口继承自 {{domxref("AuthenticatorResponse")}}。

{{InheritanceDiagram}}

> [!NOTE]
> 此接口仅限于顶级上下文。从 {{HTMLElement("iframe")}} 元素内部使用将不会产生任何效果。

## 实例属性

_另继承其父接口 {{domxref("AuthenticatorResponse")}} 的属性。_

- {{domxref("AuthenticatorAssertionResponse.authenticatorData")}} {{ReadOnlyInline}}
  - : 一个 {{jsxref("ArrayBuffer")}}，包含来自认证器的信息，例如依赖方 ID 哈希（rpIdHash）、签名计数器、用户存在性测试和用户验证标志，以及认证器处理的任何扩展。
- {{domxref("AuthenticatorResponse.clientDataJSON")}} {{ReadOnlyInline}}
  - : 包含从浏览器传递给认证器以使用此凭据进行认证的数据的 JSON 兼容序列化——即当使用 `publicKey` 选项调用 {{domxref("CredentialsContainer.get()")}} 时。此数据包含传入 `get()` 调用的选项中的一些信息，以及一些由浏览器控制的信息。
- {{domxref("AuthenticatorAssertionResponse.signature")}} {{ReadOnlyInline}}
  - : 对 {{domxref("AuthenticatorAssertionResponse.authenticatorData")}} 和 {{domxref("AuthenticatorResponse.clientDataJSON")}} 的断言签名。该断言签名使用最初在 {{domxref("CredentialsContainer.create()","navigator.credentials.create()")}} 调用期间创建的密钥对中的私钥创建，并使用同一密钥对中的公钥进行验证。
- {{domxref("AuthenticatorAssertionResponse.userHandle")}} {{ReadOnlyInline}}
  - : 一个 {{jsxref("ArrayBuffer")}}，包含一个不透明的用户标识符，该标识符在传递给原始 {{domxref("CredentialsContainer.create()","navigator.credentials.create()")}} 调用的选项中指定为 `user.id`。

## 实例方法

无。

## 示例

请参阅[获取公钥凭据](/en-US/docs/Web/API/CredentialsContainer/get#retrieving_a_public_key_credential)获取详细示例。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("AuthenticatorAttestationResponse")}}：创建新凭据时所给响应类型的接口。
- {{domxref("AuthenticatorResponse")}}：父接口。