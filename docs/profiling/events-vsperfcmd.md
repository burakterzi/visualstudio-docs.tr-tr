---
title: Olaylar (VSPerfCmd) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 46b47f9b615c824d25e931cd3d05f5d2a04257ba
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777327"
---
# <a name="events-vsperfcmd"></a>Olaylar (VSPerfCmd)
*VSPerfCmd. exe* **olayları** seçeneği, Windows IÇIN olay izleme (ETW) günlüğünü denetler. ETW verileri, profil oluşturucu veri dosyasından ayrı bir. etl dosyasına kaydedilir. Veriler [VSPerfReport](../profiling/vsperfreport.md) /Summary: ETW komutu kullanılarak bir raporda görüntülenebilir.

 Profil oluşturma işlemini durdurmak için VSPerfCmd **kapatmadan** önce herhangi bir zamanda **Olaylar** seçeneği çağrılabilir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]
```

#### <a name="parameters"></a>Parametreler
 &#124;**Kapalı** on, olay verilerini toplamayı başlatır veya sonlandırır.

 sağlayıcı denetiminin GUID 'Sini `Guid`.

 Windows Yönetim Araçları (WMI) ile kaydedilen sağlayıcının adını `ProviderName`.

 Olay sağlayıcısı tarafından tanımlanan bir "0x" önekli onaltılık bayrak değeri `Flags`.

 `Level` toplanan veri miktarını belirtir. `Level`, olay sağlayıcısı tarafından tanımlanır.

 **Olaylar** seçeneği, aşağıdaki çekirdek anahtar sözcüklerini sağlayıcı adları olarak anlamıştır:

 **İşlem** Olayları işle

 **Iş parçacığı** İş parçacığı olayları

 **Görüntü** Görüntü yükleme ve kaldırma olayları

 **Disk** Disk g/ç olayları

 **Dosya** Dosya g/ç olayları

 **Hardfault** Sabit sayfa hataları

 **Pagefault** Geçici sayfa hataları

 **Ağ** Ağ olayları

 **Kayıt defteri** Kayıt defteri erişim olayları

 Çekirdek sağlayıcının yalnızca etkinleştiğine de emin olun. İzleyici kapanana kadar devre dışı bırakılamaz veya bayrakları değiştirilemez.

## <a name="remarks"></a>Açıklamalar

> [!NOTE]
> CLR ETW olayları etkinleştirildiğinde, Izleme görünümü raporunda ek başlangıç verileri de toplanır. Raporda görünen başlangıç olaylarını dışlamak için aşağıdaki komutu kullanın:

```cmd
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5
```

> [!IMPORTANT]
> Başlangıç olaylarını dışlayamazsınız, bu olaylar Yönetilen Nesne Biçimi (MOF) dosyasında listelenmediğinden raporda GUID olarak görünürler. Daha fazla bilgi için Microsoft Web sitesindeki şu sayfaya bakın: [örnek yönetilen nesne biçimi (MOF) dosyası](https://msdn.microsoft.com/library/default.aspx).

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
