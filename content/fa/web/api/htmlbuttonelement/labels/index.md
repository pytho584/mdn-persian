---  
title: "HTMLButtonElement: labels property"  
short-title: labels  
slug: Web/API/HTMLButtonElement/labels  
page-type: web-api-instance-property  
browser-compat: api.HTMLButtonElement.labels  
---  

{{APIRef("DOM")}}  

خاصیت فقط خواندنی **`HTMLButtonElement.labels`** یک {{domxref("NodeList")}} از عناصر {{HTMLElement("label")}} مرتبط با عنصر {{HTMLElement("button")}} را برمی‌گرداند.  

## مقدار  

یک {{domxref("NodeList")}} شامل عناصر `<label>` مرتبط با عنصر `<button>`.  

## مثال‌ها  

### HTML  

```html  
<label id="label1" for="test">Label 1</label>  
<button id="test">Button</button>  
<label id="label2" for="test">Label 2</label>  
```  

### JavaScript  

```js  
const button = document.getElementById("test");  
for (const label of button.labels) {  
  console.log(label.textContent); // "Label 1" and "Label 2"  
}  
```  

{{EmbedLiveSample("Examples", "100%", 30)}}  

## Specifications  

{{Specifications}}  

## Browser compatibility  

{{Compat}}