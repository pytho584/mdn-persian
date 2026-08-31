---
title: "BroadcastChannel: postMessage() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BroadcastChannel/postMessage"
translated_by: "n8n + AI"
---

---
title: "BroadcastChannel: postMessage() method"
short-title: postMessage()
slug: Web/API/BroadcastChannel/postMessage
page-type: web-api-instance-method
browser-compat: api.BroadcastChannel.postMessage
---

{{APIRef("BroadCastChannel API")}} {{AvailableInWorkers}}

روش **`postMessage()`** از رابط {{domxref("BroadcastChannel")}} یک پیام ارسال می‌کند،
که می‌تواند از هر نوع {{jsxref("Object")}} باشد،
به هر شنونده‌ای در هر {{glossary("browsing context")}} با همان {{glossary("origin")}}.
پیام به‌عنوان یک رویداد {{domxref("BroadcastChannel/message_event", "message")}} منتقل می‌شود
که به هر {{domxref("BroadcastChannel")}} متصل به کانال هدف می‌گیرد.

## Syntax

```js-nolint
postMessage(message)
```

### Parameters

- `message`
  - : داده‌ای که به پنجره دیگر ارسال می‌شود. داده با استفاده از [الگوریتم شبیه‌سازی ساختاری](/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm) سریال‌سازی می‌شود.
    این بدان معناست که می‌توانید انواع متنوعی از اشیاء داده را به‌طور ایمن به پنجره مقصد ارسال کنید بدون اینکه خودتان آن‌ها را سریال‌سازی کنید.

    > [!NOTE]
    > ممکن است زمینه‌های اجرایی که می‌توانند با یکدیگر پیام رد و بدل کنند در یک [خوشه عامل](/en-US/docs/Web/JavaScript/Reference/Execution_model#agent_clusters_and_memory_sharing) نباشند و بنابراین نمی‌توانند حافظه را به اشتراک بگذارند. اشیاء {{jsxref("SharedArrayBuffer")}}، یا نماهای بافری که توسط یکی پشتیبانی می‌شوند، نمی‌توانند در بین خوشه‌های عامل ارسال شوند. تلاش برای انجام این کار یک رویداد {{domxref("BroadcastChannel/messageerror_event", "messageerror")}} حاوی `DataCloneError` {{domxref("DOMException")}} در سمت دریافت‌کننده ایجاد می‌کند.

### Return value

هیچ.

### Exceptions

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("BroadcastChannel")}} قبلاً بسته شده باشد پرتاب می‌شود.
- `DataCloneError` {{domxref("DOMException")}}
  - : اگر هر بخشی از داده ورودی قابل سریال‌سازی نباشد پرتاب می‌شود.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("BroadcastChannel")}}، رابطی که به آن تعلق دارد.