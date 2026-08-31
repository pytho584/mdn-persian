---
title: "CanvasRenderingContext2D: globalCompositeOperation property"
short-title: globalCompositeOperation
slug: Web/API/CanvasRenderingContext2D/globalCompositeOperation
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.globalCompositeOperation
---

{{APIRef("Canvas API")}}

ویژگی **`CanvasRenderingContext2D.globalCompositeOperation`** در Canvas 2D API نوع عملیات ترکیب (compositing) را برای زمان رسم اشکال جدید تعیین می‌کند.

همچنین به [Compositing and clipping](/en-US/docs/Web/API/Canvas_API/Tutorial/Compositing) در [Canvas Tutorial](/en-US/docs/Web/API/Canvas_API/Tutorial) مراجعه کنید.

## مقدار

یک رشته که مشخص می‌کند از کدام یک از عملیات ترکیب یا حالت ترکیب (blending mode) استفاده شود. این رشته می‌تواند هر یک از مقادیر زیر باشد:

- `"source-over"`
  - : این تنظیم پیش‌فرض است و اشکال جدید را روی محتوای موجود بوم (canvas) رسم می‌کند.
- `"source-in"`
  - : شکل جدید فقط در جایی رسم می‌شود که هم شکل جدید و هم بوم مقصد هم‌پوشانی دارند. بقیه قسمت‌ها شفاف می‌شوند.
- `"source-out"`
  - : شکل جدید در جایی رسم می‌شود که با محتوای موجود بوم هم‌پوشانی ندارد.
- `"source-atop"`
  - : شکل جدید فقط در جایی رسم می‌شود که با محتوای موجود بوم هم‌پوشانی دارد.
- `"destination-over"`
  - : اشکال جدید پشت محتوای موجود بوم رسم می‌شوند.
- `"destination-in"`
  - : محتوای موجود بوم در جایی که هم شکل جدید و هم محتوای موجود بوم هم‌پوشانی دارند حفظ می‌شود. بقیه قسمت‌ها شفاف می‌شوند.
- `"destination-out"`
  - : محتوای موجود در جایی که با شکل جدید هم‌پوشانی ندارد حفظ می‌شود.
- `"destination-atop"`
  - : بوم موجود فقط در جایی که با شکل جدید هم‌پوشانی دارد حفظ می‌شود. شکل جدید پشت محتوای بوم رسم می‌شود.
- `"lighter"`
  - : در جایی که هر دو شکل هم‌پوشانی دارند، رنگ با جمع مقادیر رنگ تعیین می‌شود.
- `"copy"`
  - : فقط شکل جدید نمایش داده می‌شود.
- `"xor"`
  - : اشکال در جایی که هم‌پوشانی دارند شفاف می‌شوند و در بقیه جاها به صورت عادی رسم می‌شوند.
- `"multiply"`
  - : پیکسل‌های لایه بالا در پیکسل‌های متناظر لایه پایین ضرب می‌شوند. نتیجه تصویری تیره‌تر است.
- `"screen"`
  - : پیکسل‌ها معکوس، ضرب و دوباره معکوس می‌شوند. نتیجه تصویری روشن‌تر است (برعکس `multiply`).
- `"overlay"`
  - : ترکیبی از `multiply` و `screen`. قسمت‌های تیره در لایه پایه تیره‌تر و قسمت‌های روشن روشن‌تر می‌شوند.
- `"darken"`
  - : تیره‌ترین پیکسل‌های هر دو لایه را حفظ می‌کند.
- `"lighten"`
  - : روشن‌ترین پیکسل‌های هر دو لایه را حفظ می‌کند.
- `"color-dodge"`
  - : لایه پایین را بر لایه بالای معکوس شده تقسیم می‌کند.
- `"color-burn"`
  - : لایه پایین معکوس شده را بر لایه بالا تقسیم می‌کند و سپس نتیجه را معکوس می‌کند.
- `"hard-light"`
  - : مانند `overlay`، ترکیبی از `multiply` و `screen` – اما با جابجایی لایه بالا و لایه پایین.
- `"soft-light"`
  - : نسخه نرم‌تر `hard-light`. سیاه یا سفید خالص منجر به سیاه یا سفید خالص نمی‌شود.
- `"difference"`
  - : لایه پایین را از لایه بالا کم می‌کند – یا برعکس – تا همیشه یک مقدار مثبت به دست آید.
- `"exclusion"`
  - : مانند `difference`، اما با کنتراست کمتر.
- `"hue"`
  - : درخشندگی (luma) و خلوص رنگ (chroma) لایه پایین را حفظ می‌کند، در حالی که رنگ (hue) لایه بالا را می‌پذیرد.
- `"saturation"`
  - : درخشندگی و رنگ لایه پایین را حفظ می‌کند، در حالی که خلوص رنگ لایه بالا را می‌پذیرد.
- `"color"`
  - : درخشندگی لایه پایین را حفظ می‌کند، در حالی که رنگ و خلوص رنگ لایه بالا را می‌پذیرد.
- `"luminosity"`
  - : رنگ و خلوص رنگ لایه پایین را حفظ می‌کند، در حالی که درخشندگی لایه بالا را می‌پذیرد.

## مثال‌ها

### تغییر عملیات ترکیب

این مثال از ویژگی `globalCompositeOperation` برای رسم دو مستطیل استفاده می‌کند که در محل هم‌پوشانی یکدیگر را حذف می‌کنند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.globalCompositeOperation = "xor";

ctx.fillStyle = "blue";
ctx.fillRect(10, 10, 100, 100);

ctx.fillStyle = "red";
ctx.fillRect(50, 50, 100, 100);
```

#### نتیجه

{{ EmbedLiveSample('Changing_the_composite_operation', 700, 180) }}

### نمایش همه مقادیر

#### مقادیر سراسری

این کد مقادیر سراسری مورد استفاده بقیه برنامه را تنظیم می‌کند.

```js
const canvas1 = document.createElement("canvas");
const canvas2 = document.createElement("canvas");
const gco = [
  "source-over",
  "source-in",
  "source-out",
  "source-atop",
  "destination-over",
  "destination-in",
  "destination-out",
  "destination-atop",
  "lighter",
  "copy",
  "xor",
  "multiply",
  "screen",
  "overlay",
  "darken",
  "lighten",
  "color-dodge",
  "color-burn",
  "hard-light",
  "soft-light",
  "difference",
  "exclusion",
  "hue",
  "saturation",
  "color",
  "luminosity",
].reverse();
const gcoText = [
  "This is the default setting and draws new shapes on top of the existing canvas content.",
  "The new shape is drawn only where both the new shape and the destination canvas overlap. Everything else is made transparent.",
  "The new shape is drawn where it doesn't overlap the existing canvas content.",
  "The new shape is only drawn where it overlaps the existing canvas content.",
  "New shapes are drawn behind the existing canvas content.",
  "The existing canvas content is kept where both the new shape and existing canvas content overlap. Everything else is made transparent.",
  "The existing content is kept where it doesn't overlap the new shape.",
  "The existing canvas is only kept where it overlaps the new shape. The new shape is drawn behind the canvas content.",
  "Where both shapes overlap the color is determined by adding color values.",
  "Only the new shape is shown.",
  "Shapes are made transparent where both overlap and drawn normal everywhere else.",
  "The pixels of the top layer are multiplied with the corresponding pixel of the bottom layer. A darker picture is the result.",
  "The pixels are inverted, multiplied, and inverted again. A lighter picture is the result (opposite of multiply)",
  "A combination of multiply and screen. Dark parts on the base layer become darker, and light parts become lighter.",
  "Retains the darkest pixels of both layers.",
  "Retains the lightest pixels of both layers.",
  "Divides the bottom layer by the inverted top layer.",
  "Divides the inverted bottom layer by the top layer, and then inverts the result.",
  "A combination of multiply and screen like overlay, but with top and bottom layer swapped.",
  "A softer version of hard-light. Pure black or white does not result in pure black or white.",
  "Subtracts the bottom layer from the top layer or the other way round to always get a positive value.",
  "Like difference, but with lower contrast.",
  "Preserves the luma and chroma of the bottom layer, while adopting the hue of the top layer.",
  "Preserves the luma and hue of the bottom layer, while adopting the chroma of the top layer.",
  "Preserves the luma of the bottom layer, while adopting the hue and chroma of the top layer.",
  "Preserves the hue and chroma of the bottom layer, while adopting the luma of the top layer.",
].reverse();
const width = 320;
const height = 340;

// lum in sRGB
const lum = {
  r: 0.33,
  g: 0.33,
  b: 0.33,
};
// resize canvas
canvas1.width = width;
canvas1.height = height;
canvas2.width = width;
canvas2.height = height;
```

#### برنامه اصلی

این کد، `runComposite()`، بخش عمده کار را انجام می‌دهد و به تعدادی توابع کمکی برای انجام کارهای سخت وابسته است.

```js
function createCanvas(op) {
  const canvas = document.createElement("canvas");
  canvas.style.background = `url(${JSON.stringify(op.data)})`;
  canvas.style.border = "1px solid black";
  canvas.style.margin = "5px";
  canvas.width = width / 2;
  canvas.height = height / 2;
  return canvas;
}

function runComposite(op) {
  const dl = document.createElement("dl");
  document.body.appendChild(dl);
  while (gco.length) {
    const pop = gco.pop();
    const dt = document.createElement("dt");
    dt.textContent = pop;
    dl.appendChild(dt);
    const dd = document.createElement("dd");
    const p = document.createElement("p");
    p.textContent = gcoText.pop();
    dd.appendChild(p);

    const canvasToDrawOn = createCanvas(op);
    const canvasToDrawFrom = createCanvas(op);
    const canvasToDrawResult = createCanvas(op);

    let ctx = canvasToDrawResult.getContext("2d");
    ctx.clearRect(0, 0, width, height);
    ctx.save();
    ctx.drawImage(canvas1, 0, 0, width / 2, height / 2);
    ctx.globalCompositeOperation = pop;
    ctx.drawImage(canvas2, 0, 0, width / 2, height / 2);
    ctx.globalCompositeOperation = "source-over";
    ctx.fillStyle = "rgb(0 0 0 / 80%)";
    ctx.fillRect(0, height / 2 - 20, width / 2, 20);
    ctx.fillStyle = "white";
    ctx.font = "14px arial";
    ctx.fillText(pop, 5, height / 2 - 5);
    ctx.restore();

    ctx = canvasToDrawOn.getContext("2d");
    ctx.clearRect(0, 0, width, height);
    ctx.save();
    ctx.drawImage(canvas1, 0, 0, width / 2, height / 2);
    ctx.fillStyle = "rgb(0 0 0 / 80%)";
    ctx.fillRect(0, height / 2 - 20, width / 2, 20);
    ctx.fillStyle = "white";
    ctx.font = "14px arial";
    ctx.fillText("existing content", 5, height / 2 - 5);
    ctx.restore();

    ctx = canvasToDrawFrom.getContext("2d");
    ctx.clearRect(0, 0, width, height);
    ctx.save();
    ctx.drawImage(canvas2, 0, 0, width / 2, height / 2);
    ctx.fillStyle = "rgb(0 0 0 / 80%)";
    ctx.fillRect(0, height / 2 - 20, width / 2, 20);
    ctx.fillStyle = "white";
    ctx.font = "14px arial";
    ctx.fillText("new content", 5, height / 2 - 5);
    ctx.restore();

    dd.appendChild(canvasToDrawOn);
    dd.appendChild(canvasToDrawFrom);
    dd.appendChild(canvasToDrawResult);

    dl.appendChild(dd);
  }
}
```

#### توابع کمکی

برنامه به تعدادی توابع کمکی وابسته است.

```js
function lightMix() {
  const ctx = canvas2.getContext("2d");
  ctx.save();
  ctx.globalCompositeOperation = "lighter";
  ctx.beginPath();
  ctx.fillStyle = "red";
  ctx.arc(100, 200, 100, Math.PI * 2, 0, false);
  ctx.fill();
  ctx.beginPath();
  ctx.fillStyle = "blue";
  ctx.arc(220, 200, 100, Math.PI * 2, 0, false);
  ctx.fill();
  ctx.beginPath();
  ctx.fillStyle = "lime";
  ctx.arc(160, 100, 100, Math.PI * 2, 0, false);
  ctx.fill();
  ctx.restore();
  ctx.beginPath();
  ctx.fillStyle = "red";
  ctx.fillRect(0, 0, 30, 30);
  ctx.fill();
}
```

```js
function colorSphere() {
  const ctx = canvas1.getContext("2d");
  const width = 360;
  const halfWidth = width / 2;
  const rotate = (1 / 360) * Math.PI * 2; // per degree
  const offset = 0; // scrollbar offset
  const oLeft = -20;
  const oTop = -20;
  for (let n = 0; n <= 359; n++) {
    const gradient = ctx.createLinearGradient(
      oLeft + halfWidth,
      oTop,
      oLeft + halfWidth,
      oTop + halfWidth,
    );
    const color = Color.HSV_RGB({ H: (n + 300) % 360, S: 100, V: 100 });
    gradient.addColorStop(0, "transparent");
    gradient.addColorStop(0.7, `rgb(${color.R} ${color.G} ${color.B})`);
    gradient.addColorStop(1, "white");
    ctx.beginPath();
    ctx.moveTo(oLeft + halfWidth, oTop);
    ctx.lineTo(oLeft + halfWidth, oTop + halfWidth);
    ctx.lineTo(oLeft + halfWidth + 6, oTop);
    ctx.fillStyle = gradient;
    ctx.fill();
    ctx.translate(oLeft + halfWidth, oTop + halfWidth);
    ctx.rotate(rotate);
    ctx.translate(-(oLeft + halfWidth), -(oTop + halfWidth));
  }
  ctx.beginPath();
  ctx.fillStyle = "blue";
  ctx.fillRect(15, 15, 30, 30);
  ctx.fill();
  return ctx.canvas;
}
```

```js
// HSV (1978) = H: Hue / S: Saturation / V: Value
Color = {};
Color.HSV_RGB = (o) => {
  const S = o.S / 100;
  let H = o.H / 360,
    V = o.V / 100;
  let R, G;
  let A, B, C, D;
  if (S === 0) {
    R = G = B = Math.round(V * 255);
  } else {
    if (H >= 1) H = 0;
    H *= 6;
    D = H - Math.floor(H);
    A = Math.round(255 * V * (1 - S));
    B = Math.round(255 * V * (1 - S * D));
    C = Math.round(255 * V * (1 - S * (1 - D)));
    V = Math.round(255 * V);
    switch (Math.floor(H)) {
      case 0:
        R = V;
        G = C;
        B = A;
        break;
      case 1:
        R = B;
        G = V;
        B = A;
        break;
      case 2:
        R = A;
        G = V;
        B = C;
        break;
      case 3:
        R = A;
        G = B;
        B = V;
        break;
      case 4:
        R = C;
        G = A;
        B = V;
        break;
      case 5:
        R = V;
        G = A;
        // B remains unchanged
        break;
    }
  }
  return { R, G, B };
};

function createInterlace(size, color1, color2) {
  const proto = document.createElement("canvas").getContext("2d");
  proto.canvas.width = size * 2;
  proto.canvas.height = size * 2;
  proto.fillStyle = color1; // top-left
  proto.fillRect(0, 0, size, size);
  proto.fillStyle = color2; // top-right
  proto.fillRect(size, 0, size, size);
  proto.fillStyle = color2; // bottom-left
  proto.fillRect(0, size, size, size);
  proto.fillStyle = color1; // bottom-right
  proto.fillRect(size, size, size, size);
  const pattern = proto.createPattern(proto.canvas, "repeat");
  pattern.data = proto.canvas.toDataURL();
  return pattern;
}

const op8x8 = createInterlace(8, "white", "#eeeeee");
```

#### شروع اجرا

در نهایت، توابع را برای راه‌اندازی همه چیز فراخوانی می‌کنیم.

```js
lightMix();
colorSphere();
runComposite(op8x8);
```

#### نتیجه

{{EmbedLiveSample("Demonstration of all values", "100%", 7250)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این ویژگی: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.globalAlpha")}}