---
title: Durum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bf5e0fdf478e067f61b1d0e259cb1624380e4f02
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778251"
---
# <a name="status"></a>Durum
*VSPerfCmd. exe* **durum** seçeneği, profil oluşturucunun durumu ve şu anda profili oluşturulan tüm süreçler hakkındaki bilgileri görüntüler.

 **Durum** seçeneği, komut satırında belirtilen tek seçenek olmalıdır. Herhangi bir durumun görüntülenebilmesi için Profiler 'ın *VSPerfCmd. exe* **Start** seçeneğiyle başlatılması gerekir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Status
```

#### <a name="parameters"></a>Parametreler
 Yok.

## <a name="remarks"></a>Açıklamalar
 **Durum** seçeneği, Profil Oluşturucu için aşağıdaki durum bilgilerini görüntüler.

 **Çıkış dosyası adı** Geçerli profil oluşturucu veri dosyasının yolu ve dosya adı.

 **Toplama modu** ÖRNEK veya Izleme

 **En fazla işlem** Tek seferde profili oluşturulabilecek en fazla işlem sayısı ve şu anda etkin olan işlem sayısı.

 **En fazla Iş parçacığı** Tek seferde profili oluşturulabilecek en fazla iş parçacığı sayısı.

 **Arabellek sayısı** Profil oluşturma verilerini yazmak için ayrılan bellek arabelleği sayısı.

 **Arabelleklerin boyutu** Bellek arabelleğinin bayt cinsinden boyutu.

 **Durum** seçeneği, şu anda profili oluşturulan her işlem için aşağıdaki durum bilgilerini görüntüler.

 **İşlem** Profili oluşturulan işlemin adı.

 **Işlem kimliği** İşlemin sistem tanımlayıcısı.

 **Iş parçacığı sayısı** Şu anda yürütülmekte olan iş parçacıklarının sayısı.

 **Başlangıç/durdurma sayısı** Bu işlem için veri toplamayı denetlemek üzere birincil iç profil oluşturucu sayısı. Sayım, veri toplamak için bire eşit olmalıdır. Başlat/Durdur sayısı profil oluşturucu API 'Leri ve VSPerfCmd seçenekleri **GlobalOn**, **globaloff**, **ProcessOn**, **ProcessOff**, **ThreadOn**ve **ThreadOff**tarafından yönetilebilir.

 **Askıya alma/sürdürülme sayısı** Bu işlem için veri toplamayı denetlemek üzere ikincil iç profil oluşturucu sayısı. Sayım, veri toplamak için sıfırdan küçük veya sıfıra eşit olmalıdır. **Askıya alma/sürdürülme** sayısı yalnızca profil oluşturucu API 'leri tarafından yönetilebilir.

 **İzlemek için erişim haklarına sahip kullanıcılar** Profil oluşturucuya erişimi olan kullanıcıların adlarını listeler. Ek kullanıcılara VSPerfCmd. exe **yönetici** seçeneği kullanılarak erişim verilebilir

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
