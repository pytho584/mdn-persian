---
title: "CreateMonitor"
---
---
title: CreateMonitor
slug: Web/API/CreateMonitor
page-type: web-api-interface
status:
  - experimental
browser-compat: api.CreateMonitor
---

{{APIRef("Summarizer API")}}{{SeeCompatTable}}{{securecontext_header}}

رابط **`CreateMonitor`** اطلاعاتی درباره پیشرفت دانلود یک مدل هوش مصنوعی، مثلاً یک بسته زبانی یا داده‌های تنظیم دقیق (fine-tuning)، فراهم می‌کند.

می‌توان از آن از طریق موارد زیر استفاده کرد:

- {{domxref("LanguageDetector.create_static", "LanguageDetector.create()")}}
- {{domxref("LanguageModel.create_static", "LanguageModel.create()")}}
- {{domxref("Summarizer.create_static", "Summarizer.create()")}}
- {{domxref("Translator.create_static", "Translator.create()")}}

{{InheritanceDiagram}}

## رویدادها (Events)

رویدادها را از والد خود، {{DOMxRef("EventTarget")}} به ارث می‌برد.

- {{domxref("CreateMonitor/downloadprogress_event", "downloadprogress")}} {{Experimental_Inline}}
  - زمانی که پیشرفتی در دانلود مدل هوش مصنوعی حاصل شود، این رویداد فعال می‌شود.

## مثال‌ها

### استفاده پایه از `CreateMonitor`

یک نمونه از `CreateMonitor` از طریق ویژگی `monitor` متد `create()` یک API هوش مصنوعی استفاده می‌شود (در زیر {{domxref("Summarizer.create_static", "Summarizer.create()")}} نشان داده شده است). ویژگی `monitor` یک تابع callback (بازگشتی) به عنوان مقدار می‌پذیرد که آرگومان آن نمونه `CreateMonitor` است. سپس می‌توانید پیشرفت دانلود را از طریق رویداد {{domxref("CreateMonitor/downloadprogress_event", "downloadprogress")}} آن نمونه نظارت کنید.

```js
const summarizer = await Summarizer.create({
  sharedContext:
    "A general summary to help a user decide if the text is worth reading",
  monitor(monitor) {
    monitor.addEventListener("downloadprogress", (e) => {
      console.log(`download progress: ${e.loaded}/${e.total}`);
    });
  },
});

const summary = await summarizer.summarize(myText);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Prompt API](/en-US/docs/Web/API/Prompt_API/Using)
- [استفاده از Summarizer API](/en-US/docs/Web/API/Summarizer_API/Using)
- [استفاده از APIهای Translator و Language Detector](/en-US/docs/Web/API/Translator_and_Language_Detector_APIs/Using)
- [نمونه‌های Web AI](https://chrome.dev/web-ai-demos/) در chrome.dev