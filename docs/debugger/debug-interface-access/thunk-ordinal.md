---
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1de2d6c9700dcb7b1106c3693d855bb1d8ae2cfa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738506"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
Dönüştürücü türlerini belirtir.

## <a name="syntax"></a>Sözdizimi

```C++
typedef enum THUNK_ORDINAL {
    THUNK_ORDINAL_NOTYPE,
    THUNK_ORDINAL_ADJUSTOR,
    THUNK_ORDINAL_VCALL,
    THUNK_ORDINAL_PCODE,
    THUNK_ORDINAL_LOAD

    // trampoline thunk ordinals - only for use in Trampoline thunk symbols
    THUNK_ORDINAL_TRAMP_INCREMENTAL,
    THUNK_ORDINAL_TRAMP_BRANCHISLAND,
} THUNK_ORDINAL;
```

## <a name="elements"></a>Öğeler
THUNK_ORDINAL_NOTYPE standart dönüştürücü.

THUNK_ORDINAL_ADJUSTOR `this` bir dönüştürücü Dönüştürücüsü.

THUNK_ORDINAL_VCALL sanal çağrı dönüştürücü.

THUNK_ORDINAL_PCODE P-kod dönüştürücü.

THUNK_ORDINAL_LOAD gecikme yükleme Dönüştürücüsü.

THUNK_ORDINAL_TRAMP_INCREMENTAL artımlı trampoline dönüştürücü (bir trampoline dönüştürücü, bir bellek alanından diğerine yapılan çağrıları sıçramalar için kullanılır).

THUNK_ORDINAL_TRAMP_BRANCHISLAND dal noktası trampoline dönüştürücü.

## <a name="remarks"></a>Açıklamalar
Bu Numaralandırmadaki değerler, [IDiaSymbol:: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) yöntemine yapılan çağrıdan döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst. h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
