---
title: "PermissionStatus: name property"
short-title: name
slug: Web/API/PermissionStatus/name
page-type: web-api-instance-property
browser-compat: api.PermissionStatus.name
---

{{APIRef("Permissions API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`name`** در رابط {{domxref("PermissionStatus")}}، نام مجوز درخواست‌شده را بازمی‌گرداند.

## مقدار

مقداری فقط‌خواندنی که با آرگومان `name` ارسال‌شده به {{domxref("Permissions.query", "navigator.permissions.query()")}} یکسان است.

## مثال‌ها

```js
function stateChangeListener() {
  console.log(`${this.name} permission status changed to ${this.state}`);
}
function queryAndTrackPermission(permissionName) {
  navigator.permissions
    .query({ name: permissionName })
    .then((permissionStatus) => {
      console.log(
        `${permissionName} permission state is ${permissionStatus.state}`,
      );
      permissionStatus.onchange = stateChangeListener;
    });
}
queryAndTrackPermission("geolocation");
queryAndTrackPermission("midi");
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}