---
title: CPU ve Windows sayaçları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.counters
helpviewer_keywords:
- Windows counters in Profiling Tools
- CPU counters in Profiling Tools
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9accd3d0ab5ff1f7a3084d5973cace08e66396b9
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779556"
---
# <a name="cpu-and-windows-counters"></a>CPU ve Windows sayaçları

Visual Studio Profiler, işletim sistemi (Windows sayaçları) tarafından oluşturulan performans verilerini ve işlemci birimi (CPU sayaçları) tarafından oluşturulan performans verilerini toplamanıza olanak sağlar.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="windows-counters"></a>Windows sayaçları

Windows sayaçları, işletim sisteminin veya bir uygulamanın, bir hizmetin veya bir sürücünün performansı hakkında bilgi sağlayan Windows Tanılama altyapısının bir parçasıdır. Windows sayaçları, geçerli bilgisayarın yapılandırmasına bağlıdır ve diğer bilgisayarlarda kullanılamayabilir. Windows performans sayaçları, profil oluşturma işaretleri olarak veri dosyalarında toplanır ve bu sayede görünümleri ve raporları filtrelemek için kullanılabilir.

## <a name="cpu-counters"></a>CPU sayaçları

CPU sayaçları, donanım ile ilgili olayların sayısını depolayan bilgisayarın CPU özelliğidir. İzleme profili oluşturma yöntemini kullanarak CPU sayacı verileri topladığınızda, veriler işlevler ve modüller için verilere eklenir. İzleme yöntemini kullanarak birden çok CPU sayacı toplayabilirsiniz. Örnekleme yöntemini kullandığınızda, örneklendiği olay olarak kullanılacak bir sayaç seçersiniz.

Performans sayaçları, CPU 'ya özeldir. Bir CPU 'nun farklı modelleri ve sürümleri, aynı performans sayacını etkinleştirmek için önemli ölçüde farklı yapılandırma ayarlarına sahip olabilir. [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] Profiler taşınabilir olayları belirli işlemcilerin bazı yaygın performans sayaçlarını ayırır ve genel performans olaylarını toplamanıza veya örneklemenizi sağlar.

Profil oluşturucuyu kullandığınızda belirli bir olayı saymak istiyorsanız, örneğin L2 önbellek isabetsizliği, bu olay göndericisinin çevresinde bir performans oturumu oluşturabilirsiniz. Bunu L2 önbelleğiyle herhangi bir CPU 'da yapabilirsiniz. Performans oturumu, değişiklik yapılmadan platformdan platforma taşınabilir.

Visual Studio Profiler, belirli bir platform için belirli olayları desteklemeye devam eder. Örneğin, bir Pentium 4 platformunda bir geliştirici Netpatlaması mimarisine özgü olan olayları saymak isteyebilir. Bu olay taşınabilir değildir, ancak belirli bir platformda belirli bir performans oturumu için geliştirici tarafından kullanılabilir.

## <a name="portable-and-platform-events"></a>Taşınabilir ve platform olayları

Taşınabilir olaylar, belirli bir işlemciye özgü olmayan bir CPU sayaçları grubudur. Diğer tüm CPU sayaçlarına platform olayları denir ve çeşitli platformlarda desteklenmeyebilir.

 Hem taşınabilir hem de platform olaylarının sayaçları ' de tanımlanmıştır. sayaçlarıyla ilgili belirli değerlerin sağlandığı *XML* dosyaları. Farklı CPU 'lar için birden çok dosya vardır, çünkü Örneğin, Intel ve AMD CPU 'Lar için veriler farklıdır. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] Profiler, bu bilgileri, hem taşınabilir hem de platform için uygun sayaçları, performans ölçümü için kullanıcıya sunmak üzere kullanır.

### <a name="portable-events"></a>Taşınabilir olaylar

Taşınabilir olaylar aşağıdaki olayları içerir:

**Genel olaylar**

|Olay adı|Olay Açıklaması|
|----------------|-----------------------|
|Yönergeler kullanımdan kaldırıldı|Olay tamamlanana kadar yürütülen yönergelerin sayısını belirtir.|
|Durdurulmayan döngüler|Yalnızca işlemcinin durdurulmadığını belirtir (örneğin, g/ç bekleniyor).|

**Ön uç olayları**

|Olay adı|Olay Açıklaması|
|----------------|-----------------------|
|ILB Isabetsizliği|Bir isabetsizlik ile sonuçlanan yönerge çevirisi arama arabelleği aramalarının sayısını belirtir.|

**Dal olayları**

|Olay adı|Olay Açıklaması|
|----------------|-----------------------|
|Dallar kullanımdan kaldırıldı|Olay tamamlanana kadar yürütülen dal yönergelerinin sayısını belirtir.|
|Yanlış tahmin edilen dallar|İşlemcinin hatalı bir yolu tahmin ettiğinden oluşan, yanlış tahmin edilen dalları gösterir. Yanlış tahmin edilen dallar, işlemcinin tüm işleri atıp doğru bir yolda yeniden başlaması gerektiğinden performansı etkiler.|

**Bellek olayları:**

|Olay adı|Olay Açıklaması|
|----------------|-----------------------|
|L2 önbellek okuma Isabetsizliği|İkinci düzey önbellek okuma isabetsizlik sayısını belirtir.|
|L2 önbellek okuma başvuruları|İkinci düzey önbellek okuma başvurularının sayısını belirtir. Yükleme isabetsizliği ve sahiplik (RFO) isabetsizliği ve isabetler için okuma içerir.|

## <a name="view-available-counters"></a>Kullanılabilir sayaçları görüntüle

Visual Studio IDE 'deki kullanılabilir CPU sayaçlarını bir komut Istemi penceresinde listeleyebilirsiniz.

### <a name="visual-studio-ui"></a>Visual Studio Kullanıcı arabirimi

Visual Studio IDE 'deki bir bilgisayardaki kullanılabilir sayaçları listelemek için Performans Gezgini bir profiler performans oturumunun açık olması gerekir.

#### <a name="to-view-a-list-of-a-list-of-all-cpu-counters-that-are-supported-on-the-current-platform"></a>Geçerli platformda desteklenen tüm CPU sayaçlarının listesini görüntülemek için

1. Performans Gezgini, performans oturumuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. Aşağıdakilerden birini yapın:

   - **Örnekleme**' ye tıklayın ve ardından **örnek** olay listesinden **performans sayacı** ' nı seçin. CPU sayaçları **kullanılabilir performans sayaçlarında**listelenir.

      **Göz önünde** Önceki örnekleme yapılandırmasına geri dönmek için **iptal** 'e tıklayın.

     veya

   - **CPU sayaçlarını**seçin ve ardından **CPU sayaçlarını topla**' yı seçin. CPU sayaçları **kullanılabilir sayaçlara**göre listelenmiştir.

      **Göz önünde** Önceki sayaç koleksiyonu yapılandırmasına dönmek için **iptal** 'e tıklayın.

#### <a name="to-view-a-list-of-a-list-of-window-counters-that-are-supported-on-the-current-platform"></a>Geçerli platformda desteklenen pencere sayaçlarının listesinin bir listesini görüntülemek için

1. Performans Gezgini, performans oturumuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Windows sayaçları**' na tıklayın.

3. **Windows sayaçlarını topla**' yı seçin.

4. **Sayaç kategorisi** listesinden bir sayaç grubu seçin. Grubun Windows sayacı liste kutusunda görüntülenir.

     **Note:** Önceki sayaç koleksiyonu yapılandırmasına dönmek için **iptal** 'e tıklayın.

### <a name="command-line"></a>Komut satırı

[VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracını kullanarak bir BILGISAYARDAKI kullanılabilir CPU sayaçlarını komut satırından listeleyebilirsiniz.

#### <a name="to-list-of-cpu-counters-that-are-supported-on-the-current-platform"></a>Geçerli platformda desteklenen CPU sayaçlarının listesi

1. Bir komut istemi penceresi açın.

2. Tür

     **\<Visual Studio performans araçları dizini > \VSPerfCmd/QueryCounters**

     *\<Visual Studio performans araçları dizin >* , Visual Studio yüklemenizin performans araçları dizininin yoludur. Performans araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="see-also"></a>Ayrıca bkz.

[Genel bakış](../profiling/overviews-performance-tools.md)
[nasıl yapılır: örnekleme olaylarını seçme](../profiling/how-to-choose-sampling-events.md)
nasıl yapılır: [CPU sayacı verilerini toplama](../profiling/how-to-collect-cpu-counter-data.md)
[nasıl yapılır: Windows sayaç verileri toplama](../profiling/how-to-collect-windows-counter-data.md)
