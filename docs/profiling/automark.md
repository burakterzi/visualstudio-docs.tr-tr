---
title: Otomatik Işaret | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 072f80508f81a7b42ad481048f604cbd4c54af88
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779798"
---
# <a name="automark"></a>AutoMark
**Otomatik işaret** seçeneği, Windows yazılım performansı sayaç olaylarının toplanması arasındaki milisaniye sayısını belirtir. Windows performans sayaçları **WinCounter** seçeneğinde belirtilmiştir.

 Komut satırında yalnızca bir **otomatik işaret** seçeneği belirtilebilir. **Otomatik işaret** tarafından belirtilen **WinCounter** örnekleme aralığının, ana örnekleme aralığından bağımsız olduğunu unutmayın.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds
```

#### <a name="parameters"></a>Parametreler
 `Milliseconds`, Windows performans sayacı olaylarının koleksiyonları arasındaki milisaniye sayısını belirtir.

## <a name="required-options"></a>Gerekli seçenekler
 **WinCounter:** `Path` toplanacak Windows performans sayacını belirtir. İzleme yöntemini kullanırken, birden çok Windows sayacı belirtilebilir. Örnekleme yöntemini kullanırken yalnızca bir yazılım sayacı belirtilebilir. **WinCounter** seçeneği, **Start** seçeneğini içeren bir komut satırında belirtilmelidir.

## <a name="example"></a>Örnek
 Bu örnekte, iki Windows performans sayacı için 1000 milisaniyelik bir örnekleme aralığı ayarlanır.

```cmd
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
