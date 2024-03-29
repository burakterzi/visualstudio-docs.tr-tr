---
title: BasicType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fff76abdecdd8613a462225278053ef4f6d9694
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745487"
---
# <a name="basictype"></a>BasicType
Simgenin temel türünü belirtir.

## <a name="syntax"></a>Sözdizimi

```C++
enum BasicType {
    btNoType   = 0,
    btVoid     = 1,
    btChar     = 2,
    btWChar    = 3,
    btInt      = 6,
    btUInt     = 7,
    btFloat    = 8,
    btBCD      = 9,
    btBool     = 10,
    btLong     = 13,
    btULong    = 14,
    btCurrency = 25,
    btDate     = 26,
    btVariant  = 27,
    btComplex  = 28,
    btBit      = 29,
    btBSTR     = 30,
    btHresult  = 31,
    btChar16   = 32,  // char16_t
    btChar32   = 33,  // char32_t
};
```

## <a name="elements"></a>Öğeler
btNoType temel tür belirtilmedi.

btVoid temel türü bir `void`.

btChar temel türü bir `char` (C/C++ tür).

btWChar temel türü, geniş bir (Unicode) karakterdir (`WCHAR`).

btInt temel türü `signed int` (C/C++ Type).

Btuınt temel türü `unsigned int` (C/C++ Type).

btFloat temel türü bir kayan noktalı sayıdır (`FLOAT`).

btBCD temel türü ikili kodlanmış bir Decimal (`BCD`).

btBool temel türü bir Boole değeri (`BOOL`).

btLong temel türü bir `long int` (C/C++ tür).

btULong temel türü bir `unsigned long int` (C/C++ tür).

btCurrency temel türü para birimidir.

btDate temel türü tarih/saat (`DATE`).

btVariant temel türü bir değişken türü yapısıdır (`VARIANT`).

btComplex temel türü karmaşık bir sayıdır.

btBit temel türü bir bittir.

btBSTR temel türü temel veya ikili dizedir (`BSTR`).

btHresult temel türü `HRESULT`.

## <a name="remarks"></a>Açıklamalar
Bu Numaralandırmadaki değerler [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) yöntemi tarafından döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst. h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
