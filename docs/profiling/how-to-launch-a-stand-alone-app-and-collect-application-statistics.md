---
title: 'Profil oluşturucu komut satırı: tek başına uygulamayı başlatın, uygulama istatistiklerini alın'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 52dcee2b-f178-4a76-bddc-e36c50bfcb78
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fb6228592115091dc538dbe59c227a180e75aa10
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74775424"
---
# <a name="how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line"></a>Nasıl yapılır: Profil Oluşturucu ile bağımsız bir uygulama başlatma ve komut satırını kullanarak uygulama istatistikleri toplama
Bu konu, tek başına (istemci) bir uygulamayı başlatmak ve örnekleme yöntemini kullanarak performans istatistikleri toplamak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağını açıklar.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Bir profil oluşturma çalıştırmasına katman etkileşim verileri eklemek, komut satırı profil oluşturma araçlarıyla belirli yordamlar gerektirir. Bkz. [Katman etkileşimi verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)

 Profil oluşturucu komut satırı araçlarını kullanmak için, yolu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir. Profil oluşturma araçlarını Visual Studio 'nun bir Visual Studio komut penceresinden yüklendiği bir makinede çalıştırabilirsiniz.

1. Profil oluşturma araçlarını Visual Studio 'nun yüklü olduğu bir makinede çalıştırıyorsanız, Visual Studio komut penceresi doğru yolları ayarlar. **Araçlar** menüsünde **vs komut istemi** ' ni seçin.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı Profil Oluşturucu ile başlatma
 Profil oluşturucuyu kullanarak bir hedef uygulamayı başlatmak için VSPerfCmd **/Start** ve **/Launch** seçeneklerini kullanarak profil oluşturucuyu başlatabilir ve uygulamayı başlatabilirsiniz. **/Start** ve **/Launch** seçeneklerini ve ilgili seçeneklerini tek bir komut satırında belirtebilirsiniz.

 Ayrıca, hedef uygulamanın başlangıcında veri toplamayı duraklatmak için **/globaloff** seçeneğini de ekleyebilirsiniz. Ardından, veri toplamaya başlamak için **/GlobalOn** kullanın.

#### <a name="to-start-an-application-by-using-the-profiler"></a>Profil oluşturucuyu kullanarak bir uygulamayı başlatmak için

1. Bir Komut İstemi penceresi açın.

2. Profil oluşturucuyu başlatın. Tür:

    **VSPerfCmd/start: örnek/output:** `OutputFile` [`Options`]

   - [/Start](../profiling/start.md) **: örnek** seçeneği, profil oluşturucuyu başlatır.

   - [/Output](../profiling/output.md) **:** `OutputFile` seçeneği, **/Start**ile gereklidir. `OutputFile` profil oluşturma verileri (. vsp) dosyasının adını ve konumunu belirtir.

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Sample** seçeneğiyle kullanabilirsiniz.

   | Seçenek | Açıklama |
   | - | - |
   | [/WINCOUNTER](../profiling/wincounter.md) **:** `WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/AutoMark](../profiling/automark.md) **:** `Interval` | Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Profil oluşturma sırasında toplanacak bir Windows için olay Izleme (ETW) olayı belirtir. ETW olayları ayrı bir (. *ETL*) dosyası. |

3. Hedef uygulamayı başlatın. Tür:**VSPerfCmd/Launch:** `appName` [`Options`] [`Sample Event`]

    **/Launch** seçeneğiyle aşağıdaki seçeneklerden birini veya daha fazlasını kullanabilirsiniz.

   |Seçenek|Açıklama|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:** `Arguments`|Hedef Uygulamaya geçirilecek komut satırı bağımsız değişkenlerini içeren bir dize belirtir.|
   |[/Console](../profiling/console.md)|Hedef komut satırı uygulamasını ayrı bir pencerede başlatır.|

    Varsayılan olarak, performans verileri 10.000.000 her durdurulmayan işlemci saati döngüsünde örneklenir. Bu, yaklaşık olarak 1 GHz işlemci üzerinde 10 saniyede bir bir süredir. Saat çevrimi aralığını değiştirmek veya farklı bir örnekleme olayı belirtmek için aşağıdaki seçeneklerden birini belirtebilirsiniz.

   |Örnek olay|Açıklama|
   |------------------|-----------------|
   |[/Timer](../profiling/timer.md) **:** `Interval`|Örnekleme aralığını, `Interval`tarafından belirtilen durdurulmayan saat döngüsü sayısına dönüştürür.|
   |[/PF](../profiling/pf.md)[ **:** `Interval`]|Örnekleme olayını sayfa hatalarına dönüştürür. `Interval` belirtilirse, örnekler arasında sayfa hatalarının sayısını ayarlar. Varsayılan değer 10 ' dur.|
   |[/sys](../profiling/sys-vsperfcmd.md)[ **:** `Interval`]|Örnekleme olayını, işlemden işletim sistemi çekirdeğine (syscalls) sistem çağrıları olarak değiştirir. `Interval` belirtilirse, örnekler arasındaki çağrı sayısını ayarlar. Varsayılan değer 10 ' dur.|
   |[/Counter](../profiling/counter.md) **:** `Config`|Örnekleme olayını ve aralığını, `Config`belirtilen işlemci performans sayacı ve aralığına göre değiştirir.|

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd. exe* seçeneklerini kullanarak profil oluşturucu veri dosyasına veri yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetlemek, program yürütmesinin, uygulamayı başlatma veya kapatma gibi belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır ( **/GlobalOn**) veya Durdur ( **/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID`[/ProcessOff](../profiling/processon-and-processoff.md) **:** `PID`|İşlem KIMLIĞI (`PID`) tarafından belirtilen işlem için veri toplamayı başlatır ( **/ProcessOn**) veya Durdur ( **/ProcessOff**).|
    |[/Attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/Detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|**/Attach** , `PID` veya işlem adı (ProcName) tarafından belirtilen işlem için veri toplamaya başlar. **/Detach** belirtilen işlem veya belirli bir işlem belirtilmemişse tüm işlemler için veri toplamayı durduruyor.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır
 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun profili oluşturulmuş herhangi bir işleme bağlı olmaması ve profil oluşturucunun açıkça kapatılması gerekir. Profil oluşturucuyu, uygulamayı kapatarak veya **VSPerfCmd/detach** seçeneğini çağırarak örnekleme yöntemini kullanarak profili oluşturulmuş bir uygulamadan ayırabilirsiniz. Ardından, profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd/shutdown** seçeneğini çağırın. **VSPerfCLREnv/off** komutu profil oluşturma ortam değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için

1. Profil oluşturucuyu hedef uygulamadan ayırmak için aşağıdaki adımlardan birini gerçekleştirin:

    - Hedef uygulamayı kapatın.

         veya

    - **VSPerfCmd/detach** yazın

2. Profil oluşturucuyu kapatın. Tür:

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
