---
title: 'IDiaReadExeAtOffsetCallback:: ReadExecutableAt | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d913a229dafb64570728434576716ba396648af3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742825"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
Bir yürütülebilir dosyadan belirtilen uzaklığa başlayarak belirtilen sayıda bayt okur.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT ReadExecutableAt ( 
   DWORDLONG fileOffset,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>Parametreler
 Dosya kayması

'ndaki Okumaya başlamak için çalıştırılabilir dosyadaki fark.

 cbData

'ndaki Okunacak bayt sayısı.

 pcbData

dışı Okunan bayt sayısını döndürür.

 veri []

[in, out] Dosyadan okunan bayt ile doldurulmuş bir dizi.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, tam bir dosya boşluğu kullanılarak yürütülebilir dosyadan veri baytları yüklemek için ÇYA destek kodu tarafından çağırılır. Bu yöntem, [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodunu desteklemek için çağrılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)