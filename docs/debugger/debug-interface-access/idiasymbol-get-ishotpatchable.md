---
title: 'IDiaSymbol:: get_isHotpatchable | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isHotpatchable method
ms.assetid: b7b6f490-1cf2-4a68-9237-b152dac84d3c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27218a2814e14e0a1ec30bd7fb4dc4840589251c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740226"
---
# <a name="idiasymbolget_ishotpatchable"></a>IDiaSymbol::get_isHotpatchable
Modülün [/hotpatch (düzeltme eki uygulanmış görüntü oluşturma)](/cpp/build/reference/hotpatch-create-hotpatchable-image) derleyici anahtarı ile derlendiğini belirten bir bayrak alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isHotpatchable(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

dışı Modül Hot-patchable ise `TRUE` döndürür. Aksi takdirde, `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, `S_FALSE` veya hata kodu döndürür.

> [!NOTE]
> @No__t_0 dönüş değeri özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="remarks"></a>Açıklamalar
 Bu özellik `SymTagCompilandDetails` sembol türünden kullanılabilir (bkz. [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)).

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)