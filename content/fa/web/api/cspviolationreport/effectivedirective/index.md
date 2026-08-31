---
title: "CSPViolationReport: effectiveDirective property"
---

---
title: "CSPViolationReport: effectiveDirective property"
short-title: effectiveDirective
slug: Web/API/CSPViolationReport/effectiveDirective
page-type: web-api-instance-property
browser-compat: api.ReportingObserver.ReportingObserver.options_parameter.types_property.csp-violation
---

{{APIRef("Reporting API")}}

**`effectiveDirective`** 属性是 {{domxref("CSPViolationReport")}} 字典的一个字符串，表示被违反的有效的[内容安全策略 (CSP)](/en-US/docs/Web/HTTP/Guides/CSP) 指令。

注意，该属性包含的是实际被违反的具体指令，例如与脚本元素相关的违规所对应的 [`script-src-elem`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/script-src-elem)，而不是策略中指定的指令，后者可能是（更一般的）[`default-src`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/default-src)。

## 值

一个字符串，表示被违反的有效 [`Content-Security-Policy` 指令](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy#directives)。

## 示例

### CSP 内联脚本违规

此示例使用内联脚本触发 CSP 违规，并通过 {{domxref("ReportingObserver")}} 报告该违规。具体来说，它会记录 `effectiveDirective` 和 `originalPolicy`，让两者的区别一目了然。

#### HTML

下面的 HTML 文件使用 [`<meta>`](/en-US/docs/Web/HTML/Reference/Elements/meta) 元素将 {{httpheader('Content-Security-Policy')}} 的 `default-src` 设置为 `self`，这允许从同一域名加载脚本和其他资源，但不允许执行内联脚本。该文档还包含一个内联脚本，应会触发 CSP 违规。

```html
<!doctype html>
<html lang="en">
  <head>
    <meta
      http-equiv="Content-Security-Policy"
      content="default-src 'self'; report-to csp-endpoint" />
    <meta
      http-equiv="Reporting-Endpoints"
      content="csp-endpoint='https://example.com/csp-reports'" />
    <script src="main.js"></script>
    <title>CSP: Violation due to inline script</title>
  </head>
  <body>
    <h1>CSP: Violation due to inline script</h1>
    <script>
      const int = 4;
    </script>
  </body>
</html>
```

#### JavaScript (main.js)

上面的文档还加载了外部脚本 `main.js`，如下所示。由于该脚本与 HTML 来自同一域名，因此不会被 CSP 阻止。

该脚本创建了一个新的 {{domxref("ReportingObserver")}} 来观察类型为 `"csp-violation"` 的内容违规报告。每次调用回调函数时，我们都会获取 reports 数组第一个条目的 `body`，并使用它将违规的 `effectiveDirective` 和 `originalPolicy` 记录到控制台。

```js
// main.js
const observer = new ReportingObserver(
  (reports, observer) => {
    console.log(`effectiveDirective: ${reports[0].body.effectiveDirective}`);
    // effectiveDirective: script-src-elem
    console.log(`originalPolicy: ${reports[0].body.originalPolicy}`);
    // originalPolicy: default-src 'self'; report-to csp-endpoint
  },
  {
    types: ["csp-violation"],
    buffered: true,
  },
);

observer.observe();
```

注意，虽然返回的数组中可能包含多个报告，但为简洁起见，我们仅记录第一个元素的值。

#### 结果

上述代码的控制台输出为：

```plain
effectiveDirective: script-src-elem
originalPolicy: default-src 'self'; report-to csp-endpoint
```

注意 `originalPolicy` 与 HTML 中 `Content-Security-Policy` 指令的 `<meta>` 内容一致，并指明策略默认为 `self`（`default-src 'self'`）。

`effectiveDirective` 是 `script-src-elem`，它指定了 JavaScript {{htmlelement("script")}} 元素的有效来源。这是实际被违反的具体指令，尽管策略中设置的是 `default-src`。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 另见

- {{domxref("SecurityPolicyViolationEvent.effectiveDirective")}}