---
title: 'IDiaSymbol:: get_localBasePointerRegisterId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_localBasePointerRegisterId method
ms.assetid: 9cbcaf00-9ace-45e1-b164-7a9439e08083
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f9ad47a37c2d9306cc4f087719bfef7a52be308
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739879"
---
# <a name="idiasymbolget_localbasepointerregisterid"></a>IDiaSymbol::get_localBasePointerRegisterId
Yığındaki yerel değişkenlere bir taban işaretçisi tutan kaydın KIMLIĞINI alır. [SymTagEnum numaralandırması](../../debugger/debug-interface-access/symtagenum.md) `SymTagFunction` olarak ayarlandığında kullanın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_localBasePointerRegisterId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Yığındaki yerel değişkenlere bir taban işaretçisi tutan kaydın KIMLIĞINI döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK`döndürür; Aksi takdirde, `S_FALSE` veya bir hata kodu döndürür.

> [!NOTE]
> `S_FALSE` dönüş değeri özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: dia2. h

 Kitaplık: diaguid. lib

 DLL: msdia100. dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)