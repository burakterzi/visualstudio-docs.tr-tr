---
title: 'Profil oluşturucu komut satırı: .NET hizmetini gereç, bellek verilerini edinme'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2fa072fc-05fe-4420-99c0-51d2ea3ac4ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 8697f1451e3d528ff27beb2467ff7758e04267cc
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74775502"
---
# <a name="how-to-instrument-a-net-framework-service-and-collect-memory-data-by-using-the-profiler-command-line"></a>Nasıl yapılır: profil oluşturucu komut satırını kullanarak bir .NET Framework hizmeti izleme ve bellek verileri toplama
Bu makalede, bir .NET Framework hizmetini işaretlemek ve bellek kullanım verilerini toplamak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanır. Bellek ayırma verilerini toplayabilir veya hem bellek ayırma hem de nesne yaşam verileri toplayabilirsiniz.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> [!NOTE]
> Hizmet, işletim sistemi başladığında başlayan bir hizmet gibi, bilgisayar başladıktan sonra yeniden başlatılamazsa, izleme yöntemiyle bir hizmetin profilini oluşturamazsınız.
>
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

## <a name="start-the-profiling-session"></a>Profil oluşturma oturumunu Başlat
 .NET Framework bir hizmetten performans verilerini toplamak için [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) aracını kullanarak, hizmet ikili dosyasının belgelenmiş bir kopyasını oluşturmak üzere uygun ortam değişkenlerini ve [vsinstr. exe](../profiling/vsinstr.md) aracını başlatın.

 Profili oluşturmak üzere yapılandırmak için hizmeti barındıran bilgisayarın yeniden başlatılması gerekir. Hizmeti hizmet denetimi Yöneticisi 'nden de el ile başlatmanız gerekir. Ardından profil oluşturucuyu başlatıp .NET Framework hizmeti 'ni başlatabilirsiniz.

 Araçlı bileşen yürütüldüğünde, bellek verileri otomatik olarak bir veri dosyasına toplanır. Profil oluşturma oturumu sırasında veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

 Profil oluşturma oturumunu sonlandırmak için hizmeti kapatır ve profil oluşturucuyu açıkça kapatın. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemeniz önerilir.

#### <a name="to-begin-profiling-a-net-framework-service"></a>.NET Framework bir hizmetin profilini oluşturmaya başlamak için

1. Bir komut istemi penceresi açın.

2. Service binary 'ın belgelenmiş bir sürümünü oluşturmak için **vsinstr** aracını kullanın.

3. Özgün ikiliyi belgelenmiş sürümle değiştirmek için hizmet denetimi Yöneticisi 'ni kullanın. Hizmet başlatma türünün manuel olarak ayarlandığından emin olun.

4. Profil oluşturma ortamı değişkenlerini başlatın. Tür:

    **VSPerfCLREnv** { **/globaltracegc** &#124; **/globaltracegclife**}

   - **/globaltracegc** ve **/globaltracegclife** bellek ayırma ve nesne yaşam süresi verilerinin toplanmasını etkinleştirir.

       |Seçenek|Açıklama|
       |------------|-----------------|
       |**/globaltracegc**|Yalnızca bellek ayırma verilerini toplar.|
       |**/globaltracegclife**|Bellek ayırma ve nesne yaşam süresi verilerini toplar.|

5. Bilgisayarı yeniden başlatın.

6. Bir komut istemi penceresi açın.

7. Profil oluşturucuyu başlatın. Tür:

    **VSPerfCmd**  [/Start](../profiling/start.md) **: Trace**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - **/Start: çekişme** seçeneği profil oluşturucuyu başlatır.

   - **/Output:** `OutputFile` seçeneği, **/Start**ile gereklidir. `OutputFile` profil oluşturma verileri (. vsp) dosyasının adını ve konumunu belirtir.

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Sample** seçeneğiyle kullanabilirsiniz.

   > [!NOTE]
   > **/User** ve **/CrossSession** seçenekleri genellikle hizmetler için gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | ASP.NET çalışan işleminin sahibi olan hesabın etki alanını ve Kullanıcı adını belirtir. İşlem, oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa, bu seçenek gereklidir. İşlem sahibi, Windows Görev Yöneticisi 'nin Işlemler sekmesinde Kullanıcı adı sütununda listelenir. |
   | [/CrossSession](../profiling/crosssession.md) | Diğer oturum oturumlarda işlemlerin profilini oluşturmayı mümkün. ASP.NET uygulaması farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. Oturum kimliği, Windows Görev Yöneticisi 'nin **süreçler** SEKMESINDEKI **oturum kimliği** sütununda listelenir. **/CS** , **/CrossSession**için bir kısaltma olarak belirtilebilir. |
   | [/WaitStart](../profiling/waitstart.md)[ **:** `Interval`] | Profil oluşturucunun hata vermeden önce başlatılması için bekleyeceği saniye sayısını belirtir. `Interval` belirtilmemişse, profil oluşturucu süresiz olarak bekler. Varsayılan olarak, **/Start** hemen döndürür. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Veri toplama duraklatılmış şekilde profil oluşturucuyu başlatmak için, **/Start** komut satırına **/globaloff** seçeneğini ekleyin. Profil oluşturmayı sürdürmeye yönelik **/GlobalOn** kullanın. |
   | [/Counter](../profiling/counter.md) **:** `Config` | Yapılandırma içinde belirtilen işlemci performans sayacından bilgi toplar. Her profil oluşturma olayında toplanan verilere sayaç bilgileri eklenir. |
   | [/WINCOUNTER](../profiling/wincounter.md) **:** `WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/AutoMark](../profiling/automark.md) **:** `Interval` | Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Profil oluşturma sırasında toplanacak bir Windows için olay Izleme (ETW) olayı belirtir. ETW olayları ayrı bir (. *ETL*) dosyası. |

8. Gerekirse, hizmeti başlatın.

9. Profil oluşturucuyu hizmete ekleyin. Tür:

     **VSPerfCmd/Attach:** `PID`&#124;`ProcessName`

    - Hizmetin işlem KIMLIĞINI veya işlem adını belirtin. Windows Görev Yöneticisi 'nde çalışan tüm işlemlerin işlem kimliklerini ve adlarını görüntüleyebilirsiniz.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hizmet çalışırken, *VSPerfCmd. exe* seçenekleriyle dosyaya yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetlemek, program yürütmesinin, uygulamayı başlatma veya kapatma gibi belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd** seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır ( **/GlobalOn**) veya Durdur ( **/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:** `PID`|İşlem KIMLIĞI (`PID`) tarafından belirtilen işlem için veri toplamayı başlatır ( **/ProcessOn**) veya Durdur ( **/ProcessOff**).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:** `TID`|İş parçacığı KIMLIĞI (`TID`) tarafından belirtilen iş parçacığı için ( **/ThreadOn**) veya Durdur ( **/ThreadOff**) veri toplamayı başlatır.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır
 Profil oluşturma oturumunu sonlandırmak için, Araçlı bileşeni çalıştıran uygulamayı kapatın ve ardından **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) seçeneğini başlatıp profil oluşturucuyu kapatın ve profil oluşturma veri dosyasını kapatın. **VSPerfCLREnv/globaloff** komutu profil oluşturma ortam değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için

1. Hizmeti hizmet denetimi Yöneticisi 'nden durdurun.

2. Profil oluşturucuyu kapatın. Tür:

     **VSPerfCmd/shutdown**

3. Tüm profil oluşturmayı tamamladığınızda, profil oluşturma ortam değişkenlerini temizleyin. Tür:

     **VSPerfClrEnv/globaloff**

     Belgelenmiş modülün değerini özgün ile değiştirin. Gerekirse, hizmetin başlangıç türünü yeniden yapılandırın.

4. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
- [.NET bellek verileri görünümleri](../profiling/dotnet-memory-data-views.md)
