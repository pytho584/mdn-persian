---
title: "ARIA: combobox role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: combobox role"
short-title: combobox
slug: Web/Accessibility/ARIA/Reference/Roles/combobox_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#combobox,
  - https://www.w3.org/WAI/ARIA/apg/patterns/combobox/examples/combobox-select-only/
sidebar: accessibilitysidebar
---

`combobox` 角色标识一个元素为 `input` 或 `button`，该元素控制另一个元素（如 `listbox` 或 `grid`），后者可以动态弹出以帮助用户设置值。组合框可以是可编辑的（允许文本输入），也可以仅限选择（只允许从弹出框中选择）。

## 描述

`combobox` 是一个复合组件，它将一个命名的输入字段与一个提供该输入字段可能值的弹出框相结合。此组件的目的是通过帮助用户选择值而无需输入完整值来改善用户体验，并且根据受支持的值是否有限，还可以防止用户输入无效或不受支持的值。

`combobox` 角色可以设置在用于可编辑组合框的 `input` 元素上，或用于仅限选择的组合框的 `button` 元素上。该元素控制另一个元素，如 `listbox` 或 `grid`，后者可以动态弹出以帮助用户设置值。

具有 `combobox` 角色的元素可以是可编辑的单行文本字段（使用 {{HTMLElement('input')}} 元素，类似于带有 {{HTMLElement('datalist')}} 的元素），也可以是仅显示当前值而不允许直接文本输入的仅限选择元素（使用 `button` 元素）。

一个 WAI-ARIA 组合框只需要一个属性：[`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded)。然而，根据实现，通常还需要几个其他属性：[`aria-haspopup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-haspopup)、[`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls)、[`aria-activedescendant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-activedescendant) 和 [`aria-autocomplete`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-autocomplete)。

通常，组合框的初始状态是折叠的，设置 `aria-expanded="false"`。在折叠状态下，只有组合框元素以及可选地一个用于调用弹出框的兄弟按钮可见。当折叠时，[`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) 的值必须设置为 `false`，因为它向辅助技术表明该组件是可展开的。

当组合框元素显示其当前值以及其关联的弹出元素可见时，组合框处于展开状态。当展开时，必须设置 `aria-expanded="true"`。

与 `combobox` 关联的弹出元素可以是 [`listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role)、[`tree`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tree_role)、[`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role) 或 [`dialog`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/dialog_role) 元素。

组合框具有隐含的 [`aria-haspopup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-haspopup) 值为 `listbox`，因此如果弹出框是 `listbox`，则包含此属性是可选的。如果组合框弹出元素是 `tree`、`grid` 或 `dialog`（除 `listbox` 以外的任何内容），则必须提供 `aria-haspopup` 属性。`aria-haspopup` 的值必须是 `tree`、`grid`、`dialog` 或 `listbox` 角色之一。请注意，对于此属性，`true` 表示 `menu`，所以确保该值对应于弹出框的角色，而不是布尔值。

当组合框的弹出框显示时，确保组合框元素上的 [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls) 属性设置为弹出 `listbox`、`tree`、`grid` 或 `dialog` 元素的 [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id)。这就是表示具有 `combobox` 角色的元素与其控制的弹出框之间关系的方式。（注意：在较旧的 ARIA 规范中，这是 `aria-owns` 而不是 `aria-controls`，因此您可能会在旧的组合框实现中看到 `aria-owns`。代码中的 `aria-owns` 应该更新为 `aria-controls`！）

如果组合框 UI 包含一个可见控件（如图标），该控件允许通过指针和触摸事件控制弹出框的可见性，则该控件应为 {{HTMLElement('button')}}、类型为 `button` 的 {{HTMLElement('input')}}，或具有 [`tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) 为 `-1` 的 [`button`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role) 角色元素。这样做将使按钮可聚焦，但不包含在键盘 Tab 序列中。它不能是角色为 `combobox` 的元素的后代。

为了键盘可访问性，必须编程实现键盘支持，以便在 `combobox` 元素和弹出 `listbox`、`tree`、`grid` 或 `dialog` 中包含的元素之间移动焦点。一种常见的约定是 <kbd>Down Arrow</kbd> 将焦点从输入移动到弹出元素的第一个可聚焦后代。

[`aria-activedescendant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-activedescendant) 属性可用于标识组合框弹出框中当前活动的元素，例如弹出 `listbox` 中的一个 `option`，适用于 DOM 焦点保持在组合框上的实现。如果 DOM 焦点在调用弹出框时没有保留在组合框上，而是移入弹出框（如对话框），则可能不需要 `aria-activedescendant`。

如果组合框实现为可编辑的 {{HTMLElement('input')}} 元素，则组合框的值就是输入的值。对于使用 `button` 元素实现的仅限选择组合框，该值来自弹出框中所选的选项。

[`aria-autocomplete`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-autocomplete) 属性仅适用于支持文本输入的可编辑组合框。对于这些组合框，请将该属性设置为与所提供行为对应的值：`inline`、`list` 或 `both`。该属性指示输入文本将触发显示用户预期值的一个或多个预测，并指定这些预测的呈现方式。对于使用 `button` 元素的仅限选择组合框，不应使用 `aria-autocomplete`，因为不可能进行文本输入。

每个 `combobox` 必须具有可访问名称，可以通过以下三种方式之一提供：

1. 对于 {{HTMLElement('input')}} 元素，使用关联的 {{HTMLElement('label')}}。
2. 如果 UI 中存在可见标签，请使用 [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) 引用标签元素的 `id`。
3. 如果没有可见标签，请使用 [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label)。

> [!NOTE]
> 仅使用其中一种方法；不要组合它们。

### 关联的 WAI-ARIA 角色、状态和属性

- [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded)
  - : 必需。标识组合框是打开（`true`）还是关闭（`false`）。
- [`aria-haspopup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-haspopup)
  - : 隐含。如果省略，默认为 `listbox`。也支持 `tree`、`grid` 或 `dialog`。标识组合框具有弹出框，并指示其类型。

### 键盘交互

- <kbd>Down Arrow</kbd>
  - : 如果弹出框关闭则打开它，并将焦点移动到下一个选项，如果未选择任何选项则移动到第一个选项。

- <kbd>Alt</kbd> + <kbd>Down Arrow</kbd>（可选）
  - : 如果弹出框可用但未显示，则显示弹出框而不移动焦点。

- <kbd>Up Arrow</kbd>
  - : 如果弹出框关闭则打开它，并将焦点移动到上一个选项，如果未选择任何选项则移动到最后一个选项。

- <kbd>Alt</kbd> + <kbd>Up Arrow</kbd>（可选）
  - : 如果弹出框具有焦点，则将焦点返回到组合框，否则关闭弹出框。

- <kbd>Escape</kbd>
  - : 如果弹出框打开则关闭它。如果弹出框已关闭，则清除可编辑组合框的值。

#### 可编辑组合框的键盘交互

- <kbd>Enter</kbd>
  - : 如果弹出框中选择了自动完成建议，则通过更新组合框值并将输入光标放在末尾来接受该建议。
    还可能触发默认操作（例如，在消息传递应用程序中，将接受的值添加到收件人列表）。

- <kbd>Tab</kbd>
  - : 接受当前值并将焦点移动到下一个可聚焦元素。

#### 仅限选择组合框的键盘交互

- <kbd>Enter</kbd> 或 <kbd>Space</kbd>
  - : 当弹出框关闭时，打开弹出框。当弹出框打开且选择了选项时，接受所选选项作为组合框值并关闭弹出框。

- <kbd>Tab</kbd>
  - : 接受当前选择并将焦点移动到下一个可聚焦元素。

- <kbd>Home</kbd> 或 <kbd>End</kbd>
  - : 当弹出框打开时，分别将焦点移动到第一个或最后一个选项。

## 示例

```html
<label for="jokes">选择你喜欢的笑话类型</label>
<div class="combo-wrap">
  <input
    type="text"
    id="jokes"
    role="combobox"
    aria-controls="joketypes"
    aria-autocomplete="list"
    aria-expanded="false"
    data-active-option="item1"
    aria-activedescendant="" />
  <span aria-hidden="true" data-trigger="multiselect"></span>
  <ul id="joketypes" role="listbox" aria-label="Jokes">
    <li class="active" role="option" id="item1">双关语</li>
    <li class="option" role="option" id="item2">谜语</li>
    <li class="option" role="option" id="item3">观察</li>
    <li class="option" role="option" id="item4">敲门笑话</li>
    <li class="option" role="option" id="item5">一句话笑话</li>
  </ul>
</div>
```

## 规范

{{Specifications}}

## 参见

- HTML {{HTMLElement('label')}} 元素
- HTML {{HTMLElement('select')}} 元素
- HTML {{HTMLElement('option')}} 元素
- HTML {{HTMLElement('input')}} 元素
- [ARIA: `listbox` 角色](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role)
- [ARIA: `option` 角色](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role)
- [ARIA: `list` 角色](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/list_role)
- [ARIA: `listitem` 角色](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listitem_role)
- [ARIA 最佳实践 – 组合框](https://www.w3.org/WAI/ARIA/apg/patterns/combobox/)
- [可访问的组合框模块](https://dequelabs.github.io/combobo/demo/) 由 Deque 提供的示例