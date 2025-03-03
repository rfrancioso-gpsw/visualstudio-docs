---
description: "Indicates whether an address map has been established for a particular session."
title: "IDiaAddressMap::get_addressMapEnabled"
ms.date: "11/04/2016"
ms.topic: "reference"
dev_langs:
  - "C++"
helpviewer_keywords:
  - "IDiaAddressMap::get_addressMapEnabled method"
author: "mikejo5000"
ms.author: "mikejo"
manager: mijacobs
ms.subservice: debug-diagnostics
---
# IDiaAddressMap::get_addressMapEnabled

Indicates whether an address map has been established for a particular session.

## Syntax

```C++
HRESULT get_addressMapEnabled ( 
   BOOL* pRetVal
);
```

#### Parameters
 pRetVal

[out] Returns `TRUE` if the address mapping is enabled.

## Return Value
 If successful, returns `S_OK`; otherwise, returns an error code.

## Remarks
 Executable post-processors sometimes update the executable. DIA contains a mechanism to support the translation of symbols to the new layout.

 Client applications can set the address map for a particular session by getting the [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) interface from the [IDiaSession](../../debugger/debug-interface-access/idiasession.md) interface and calling the [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) method followed by a call to the [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) method. The `get_addressMapEnabled` method returns the results of calling the `put_addressMapEnabled` method.

## See also
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
