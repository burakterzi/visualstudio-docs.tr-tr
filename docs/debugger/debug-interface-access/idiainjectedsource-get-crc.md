---
title: 'IDiaInjectedSource:: get_crc | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_crc method
ms.assetid: 2ecdda93-950e-40d6-b79b-4ae3c55b6cfc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e20cdf82af3b36c589879c81c492a3f58b67f90
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743389"
---
# <a name="idiainjectedsourceget_crc"></a>IDiaInjectedSource::get_crc
Kaynak kodun baytlarından hesaplanan Döngüsel artıklık denetimi (CRC) alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_crc ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Kaynak kodun baytlarından hesaplanan CRC 'yi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Bu özellik desteklenmiyorsa `S_FALSE` döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)