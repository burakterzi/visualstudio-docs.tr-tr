---
title: Sayaç | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: aa4b4cdb-e6ea-433a-9579-56f3785e1385
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9e2f1684257ed39560fa0ea049d3296a6e45cdd7
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779486"
---
# <a name="counter"></a>Sayaç
**Sayaç** seçeneği, işlemci (donanım) performans sayaçlarından verileri toplar.

- Örnekleme profil oluşturma yöntemini kullanırken, **sayaç** on yonga performans sayacını ve örnekleme aralığı olarak kullanılacak sayaç olaylarının sayısını belirtir. Örnekleme kullanırken yalnızca bir sayaç belirtebilirsiniz.

- İzleme profili oluşturma yöntemini kullanırken, önceki ve geçerli koleksiyon olayları arasındaki aralıkta gerçekleşen sayaç olaylarının sayısı profil oluşturucu raporlarında ayrı alanlar olarak listelenir. Birden çok **sayaç** seçeneği, izleme kullanırken belirtilebilir.

  Her işlemci türünün kendi donanım performans sayacı kümesi vardır. Profil Oluşturucu, neredeyse tüm işlemciler için ortak olan genel performans sayaçları kümesini tanımlar. Bilgisayarınızdaki genel ve işlemciye özgü sayaçları listelemek için VSPerfCmd **QueryCounters** komutunu kullanın.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]][Options]
```

```cmd
VSPerfCmd.exe /Start:Method /Counter:Name[,Reload[,FriendlyName]][/Counter:Name[,Reload[,FriendlyName]]][Options]
```

#### <a name="parameters"></a>Parametreler
 sayacın adını `Name`. Bilgisayardaki kullanılabilir sayaçların adlarını listelemek için VSPerfCmd. exe **/QueryCounters** seçeneğini kullanın.

 Örnekleme aralığındaki sayaç olaylarının sayısını `Reload`. , İzleme yöntemiyle birlikte kullanmayın.

 `FriendlyName` (Isteğe bağlı) profil oluşturucu raporlarının ve görünümlerinin sütun başlıklarında `Name` yerine kullanılacak dize.

## <a name="required-options"></a>Gerekli seçenekler
 Sayaç seçeneği, yalnızca aşağıdaki seçeneklerden biriyle kullanılabilir:

 **Başlat:** `Trace`, izleme yöntemini kullanmak için profil oluşturucuyu başlatır.

 **Başlat:** `AppName` belirtilen uygulamayı ve profil oluşturucuyu başlatır. Örnekleme yöntemini kullanmak için profil oluşturucunun başlatılmış olması gerekir.

 **Attach:** `PID` profil oluşturucuyu başlatır ve işlem kimliği tarafından belirtilen işleme iliştirir. Örnekleme yöntemini kullanmak için profil oluşturucunun başlatılmış olması gerekir.

## <a name="example"></a>Örnek
 Örnekleme yöntemi örneği, genel Profiler sayacı Nonıtteddöngüleri her 1000 tekrarından uygulamanın nasıl örneklendiğini gösterir.

 İzleme yöntemi örneği, L2InstructionFetches sayacı olaylarını toplamak için profil oluşturucuyu nasıl başlatacağınızı gösterir. L2InstructionFetches sayaç adı işlemciye özeldir.

```cmd
; Sample Method Example
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Counter:NonHaltedCycles,1000,"Non-Halted Cycles"

;INSTRUMENTATION METHOD EXAMPLE
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /Counter:L2InstructionFetches,,"L2 Cache Instruction Fetches"
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
