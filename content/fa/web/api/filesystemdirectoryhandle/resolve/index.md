---
title: "FileSystemDirectoryHandle: resolve() method"
short-title: resolve()
slug: Web/API/FileSystemDirectoryHandle/resolve
page-type: web-api-instance-method
browser-compat: api.FileSystemDirectoryHandle.resolve
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}

**`resolve()`** 方法属于 {{domxref("FileSystemDirectoryHandle")}} 接口，返回一个 {{jsxref('Array')}}，其中包含从父句柄到指定子条目的目录名称，且子条目的名称是数组的最后一项。

## 语法

```js-nolint
resolve(possibleDescendant)
```

### 参数

- `possibleDescendant`
  - : 要返回其相对路径的 {{domxref('FileSystemHandle')}}。

### 返回值

一个 {{jsxref('Promise')}}，解析为字符串数组（{{jsxref('Array')}}）；如果 `possibleDescendant` 不是此 {{domxref('FileSystemDirectoryHandle')}} 的后代，则解析为 `null`。

### 异常

不会抛出任何异常。

## 示例

以下异步函数使用 `resolve()` 来确定所选文件相对于指定目录句柄的路径。

```js
async function returnPathDirectories(directoryHandle) {
  // Get a file handle by showing a file picker:
  const [handle] = await self.showOpenFilePicker();
  if (!handle) {
    // User cancelled, or otherwise failed to open a file.
    return;
  }

  // Check if handle exists inside our directory handle
  const relativePaths = await directoryHandle.resolve(handle);

  if (relativePaths === null) {
    // Not inside directory handle
  } else {
    // relativePath is an array of names, giving the relative path
    for (const name of relativePaths) {
      // log each entry
      console.log(name);
    }
  }
}
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [File System API](/en-US/docs/Web/API/File_System_API)
- [File System Access API：简化对本地文件的访问](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)