---
title: Bir performans sorununun düzeltilme olasılığını nasıl artırabileceğiniz
description: Visual Studio 'da performans sorunları göndermek için ek bilgiler ve en iyi uygulamalar
author: seaniyer
ms.author: seiyer
ms.date: 11/19/2019
ms.topic: reference
ms.openlocfilehash: 3bf61c1ecbed5a3da1fe7ec0bcf9c6d4b7580b8d
ms.sourcegitcommit: 0b90e1197173749c4efee15c2a75a3b206c85538
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2019
ms.locfileid: "74904000"
---
# <a name="how-to-increase-the-chances-of-a-performance-issue-being-fixed"></a>Bir performans sorununun düzeltilme olasılığını artırma

"[Sorun bildir](https://aka.ms/vs-rap)" Aracı, Visual Studio kullanıcıları tarafından yaygın olarak bir dizi sorunu bildirmek için kullanılır. Visual Studio ekip noktaları kilitlenme ve Kullanıcı geri bildirimleriyle ilgili eğilimleri yavaşlayor ve kullanıcıların büyük bir bölümünü etkileyen sorunları gidermektedir. Belirli bir geri bildirim bileti daha fazla eyleme çıkılarak, büyük olasılıkla ürün ekibi tarafından hızlı bir şekilde tanılanabilir ve çözümlenir. Bu belge, daha fazla işlem yapılabilir olması için kilitlenme veya yavaşlık sorunları bildirirken en iyi uygulamaları açıklar.

## <a name="general-best-practices"></a>Genel en iyi uygulamalar

Visual Studio, çok sayıda dili, proje türünü, platformu ve daha fazlasını destekleyen büyük ve karmaşık bir platformdur. Uygulamasının nasıl gerçekleştirdiği, bir oturumda hangi bileşenlerin yüklü ve etkin olduğu, yüklü uzantılar, Visual Studio ayarları, makine yapılandırması ve son olarak düzenlenmekte olan kodun şekli. Değişken sayısı verildiğinde, bir kullanıcıdan gelen sorun raporunun, başka bir kullanıcıdan sorun raporu olarak aynı olup olmadığını, görünür belirti aynı olsa bile söylemek zordur. Bu, belirli sorun raporunuzun tanıma olasılığının daha yüksek olduğundan emin olmak için bazı en iyi yöntemler aşağıda verilmiştir.

**Mümkün olduğunca belirli bir başlık sağlayın**

Bildirilmekte olan soruna yönelik ayrı imzalar bulun ve başlıkta mümkün olduğunca fazla sayıda dahil edin. Başlık açıklayıcı ise, ilgisiz sorunları olan (ancak aynı yararlanmayan belirti) kullanıcıların *biletinizi* oylamasını veya yorum yapmasını, böylece sorununuzun tanılamasını zorlaştırır.

**Şüpheli olduğunda, yeni bir sorun raporu Kaydet**

Birçok sorun için herhangi bir farklı imza veya yeniden oluşturma adımı bulunmayabilir. Bu gibi durumlarda, yeni bir rapor, bir veya daha fazla rapor üzerinde, benzer bir dışa dönük *belirti*bildiren bir açıklamadan daha iyidir. Raporun türüne bağlı olarak, bu belgenin ilerleyen kısımlarında açıklandığı gibi Raporunuza ek tanılama dosyaları ekleyin.

**Soruna özgü en iyi yöntemler**

Aşağıda açıklanan sorunlar iyi tanılama dosyaları olmadan tanılanması zor olan sorunlardır. Sorununuzu en iyi açıklayan durumu tanımladıktan sonra, bu servis talebine özgü geri bildirim adımlarını izleyin.

-   [Kilitlenmeler:](#crashes) İşlem (Visual Studio) beklenmedik bir şekilde sonlandırıldığında kilitlenme oluşur.

-   [Yanıt verme süresi:](#unresponsiveness) , Uzun bir süre boyunca yanıt vermemeye başladı.

-   [Yavaşlık sorunları:](#slowness-and-high-cpu-issues) VS 'deki belirli bir eylem, istenenden daha yavaş

-   [Yüksek CPU:](#slowness-and-high-cpu-issues) Beklenmedik bir şekilde yüksek CPU kullanımı uzatılmış dönemleri

## <a name="crashes"></a>Çökme
İşlem (Visual Studio) beklenmedik bir şekilde sonlandırıldığında kilitlenme oluşur.

**Doğrudan tekrarlanabilir kilitlenmeler**

Doğrudan tekrarlanabilir kilitlenmeler, aşağıdaki özelliklerin tümüne sahip olan durumlardır:

- Bilinen bir adım kümesini izleyerek gözlemlenebilir

- Birden çok bilgisayarda (varsa) gözlemlenebilir

- Örnek kodda veya geri bildirimin bir parçası olarak bağlanabilen ya da sağlanbağlanabilen bir projede yeniden oluşturulabilir (adımlar bir proje veya belge açmak içeriyorsa)

Bu sorunlar için "[sorunu bildirme](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)" bölümündeki adımları izleyin ve şunları eklediğinizden emin olun:

-   Sorunu yeniden oluşturma adımları

-   Yukarıda açıklanan şekilde tek başına yeniden üretme projesi. Tek başına yeniden oluşturma mümkün değilse lütfen şunları ekleyin:

    -   Açık projelerin dili (C\#, C++vb.)

    -   Proje türü (konsol uygulaması, ASP.NET, vb.)


> [!NOTE]
> **En değerli geri bildirim:** Bu durumda, en değerli geri bildirim, sorunu örnek kaynak kodla birlikte yeniden oluşturma adımları kümesidir.

**Bilinmeyen kilitlenmeler**

Kilitlenmelere neden olan veya rastgele göründüler konusunda emin değilseniz, Visual Studio kilitlendiklerinde dökümleri yerel olarak yakalayabilir ve ayrı geri bildirim öğelerine ekleyebilirsiniz. Visual Studio çöküyor dökümlerini yerel olarak kaydetmek için yönetici komut penceresinde aşağıdaki komutları çalıştırın:

```
reg add "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\Windows Error
Reporting\\LocalDumps\\devenv.exe"

reg add "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\Windows Error
Reporting\\LocalDumps\\devenv.exe" /v DumpType /t REG_DWORD /d 2

reg add "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\Windows Error
Reporting\\LocalDumps\\devenv.exe" /v DumpCount /t REG_DWORD /d 2

reg add "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\Windows Error
Reporting\\LocalDumps\\devenv.exe" /v DumpFolder /t REG_SZ /d "C:\\CrashDumps"
```

Döküm sayısını ve döküm klasörünü uygun şekilde özelleştirin. Bu ayarlarla ilgili daha fazla bilgiyi [burada](https://docs.microsoft.com/windows/win32/wer/collecting-user-mode-dumps?redirectedfrom=MSDN)bulabilirsiniz.

> [!NOTE]
> Görev Yöneticisi kullanılarak yakalanan dökümlerden büyük olasılıkla yanlış bit kullanımı olabilir ve bu da daha az kullanılabilir hale gelir. Yukarıda açıklanan yordam, yığın dökümünü yakalamak için tercih edilen yoldur. Görev Yöneticisi 'ni kullanmak istiyorsanız, çalışmakta olan birini kapatın, 32bit Görev Yöneticisi 'Ni (% windir%\\sysWOW64\\taskmgr. exe) başlatın ve buradan bir yığın dökümü toplayın.

> [!NOTE] 
> Bu yöntem tarafından üretilen her döküm dosyası boyutu 4 GB 'a kadar olacaktır. DumpFolder 'ı yeterli sürücü alanına sahip bir konuma ayarladığınızdan emin olun veya DumpCount sayısını uygun şekilde ayarlayın.

Visual Studio her kilitlendiğinde, **devenv. exe döküm dosyası oluşturacaktır. [ Number]. dmp** dosyası yapılandırılmış konumda.

Ardından, Visual Studio 'nun "sorun bildir..." seçeneğini kullanın. Özellik. Uygun dökümü eklemenize olanak sağlayacak.

1.  Rapor ettiğiniz kilitlenme için döküm dosyasını bulun (doğru oluşturulma zamanına sahip bir dosya arayın)

2.  Mümkünse, geri bildirim göndermeden önce dosyanın boyutunu azaltmak için dosyayı (\*. zip) ZIP

3.  "[Sorunu bildirme](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)" bölümündeki adımları izleyin ve yığın dökümünü yeni bir geri bildirim öğesine ekleyin.

> [!NOTE] 
> **En değerli geri bildirim:** Bu durumda, en değerli geri bildirim kilitlenme sırasında yakalanan yığın dökümünden oluşur.

## <a name="unresponsiveness"></a>Yanıt verme
, Uzun bir süre boyunca yanıt vermemeye başladı.

**Doğrudan tekrarlanabilir yanıt verme**

Kilitlenmelerde karşılık gelen bölümünde açıklandığı gibi, birden çok makinede görülen ve küçük bir örnekte görünebileceği sorunlar için, en değerli geri bildirim raporları sorunu yeniden oluşturma adımlarını içeren ve sorunu gösteren örnek kaynak kodu.

**Bilinmeyen yanıt verme süresi**

Yanıt veremeyen bir şekilde kendi kendine bildirim, bir sonraki oluşumda yeni bir Visual Studio örneği başlatın ve bu örnekten bir sorun bildirin.
["Kayıt" ekranında](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019#record-a-repro)yanıt vermeyen Visual Studio oturumunu seçtiğinizden emin olun.

Yanıt vermeyen Visual Studio örneği yönetici modunda başlatılmışsa ikinci örneğin da yönetici modunda başlatılması gerekir.

>[!NOTE] 
> **En değerli geri bildirim:** Bu durumda, en değerli geri bildirim, yanıt verme sırasında yakalanan yığın dökümünlüklarıdır.

## <a name="slowness-and-high-cpu-issues"></a>Yavaşlık ve yüksek CPU sorunları

Yavaşlan veya yüksek CPU kullanımı sorunu, yavaş işlem veya yüksek CPU olayı devam ederken yakalanan bir performans izdir.

>[!NOTE] 
> Mümkün olduğunda, her senaryoyu ayrı ve belirli bir geri bildirim raporunda yalıtın.
Örneğin, yazma ve gezinme her ikisi de yavaşsa, sorun başına aşağıdaki adımları izleyin. Bu, ürün takımının belirli sorunların nedenini yalıtmasına yardımcı olur.

Performansı yakalamaya en iyi sonuçları elde etmek için şu adımları izleyin:

1.  Zaten çalışmıyorsa, Visual Studio 'nun bir kopyasını açarak sorunu yeniden oluşturacaksınız.

    -   Sorunu yeniden oluşturmak için her şeyin ayarlanmış olmasını sağlar. Örneğin, belirli bir dosya açıldığında belirli bir projenin yüklenmesi gerekiyorsa, devam etmeden önce bu adımların her ikisinin de tamamlanmış olduğundan emin olun.

    -   Bir çözümü yüklemeye özgü bir sorun *bildirmeyen* performans izlemesini kaydetmeden önce çözümü açtıktan sonra, çözüm boyutuna bağlı olarak 5-10 dakika (veya daha fazla) beklemeyi deneyin. Çözüm yükleme işlemi büyük miktarda veri üretir, bu nedenle birkaç dakika beklemek, raporlamadaki belirli bir sorunu odaklanmamıza yardımcı olur.

2.  *Hiçbir çözüm açık olmadan* Visual Studio 'nun ikinci bir kopyasını Başlat

3.  Visual Studio 'nun yeni kopyasında **sorun bildir** aracını açın

4.  "İzleme ve yığın dökümü sağlayın (isteğe bağlı)" adımına ulaşana kadar [sorun bildirme](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) bölümündeki adımları izleyin.

5.  Visual Studio 'nun ilk kopyasını (performans sorunundan bir sorunla karşılaşmadan) kaydetmeyi ve kaydı başlatmayı seçin.

    -   Adım Kaydedicisi uygulaması görüntülenir ve kayıt başlatılır.

    -   **Kayıt sırasında,** Visual Studio 'nun ilk kopyasında sorunlu eylemi gerçekleştirin. Kaydedilen süre içinde görünmedikleri takdirde belirli performans sorunlarını düzeltmemizi zorlaştırıyor.

    -   Eylem 30 saniyeden kısaysa ve kolayca tekrarlanabilir, sorunu daha fazla göstermek için eylemi tekrarlayın.

    -   Çoğu durumda, özellikle de sorunlu bir işlem 30 saniyeden uzun süre boyunca sorunları göstermek için 60 saniyelik bir izleme yeterlidir. Süre, düzeltilmesi gereken davranışı yakalamak için gerektiği şekilde ayarlanabilir.

6.  Raporlamak istediğiniz yavaş işlem veya yüksek CPU olayı tamamlandıktan hemen sonra Adım Kaydedicisi içindeki "Kaydı Durdur" seçeneğine tıklayın. Performans izlemenin işlenmesi birkaç dakika sürebilir.

7.  İşlem tamamlandıktan sonra geri bildiriminiz için birkaç ek olacaktır. Sorunu yeniden oluşturmaya yardımcı olabilecek ek dosyalar ekleyin (örnek bir proje, ekran görüntüleri, videolar vb.).

8.  Geri bildirimi gönderin.

Bir performans izlemesini kaydederken, raporlama yaptığınız yavaş işlem veya yüksek CPU bir uçtan geliyorsa kaydı hemen durdurun. Çok fazla bilgi toplanırsa, en eski bilgilerin üzerine yazılır. İzleme yakında durdurulmamışsa (birkaç saniye içinde), ilginç bir işlemden sonra, yararlı izleme verilerinin üzerine yazılır.

Geliştirici topluluğu Web sitesinde mevcut geri bildirim öğelerine doğrudan performans izlemeleri eklemeyin. Visual Studio 'nun yerleşik bir sorun aracında, ek bilgi isteme/sağlama işlemi desteklenen bir iş akışıdır. Önceki bir geri bildirim öğesini çözümlemek için bir performans izlemesi gerekliyse, geri bildirim öğesinin durumunu "daha fazla bilgi gerekiyor" olarak ayarlayacağız, bu da yeni bir sorunu raporlama ile aynı şekilde yanıt verebilir. Ayrıntılı yönergeler için lütfen sorun bildir aracının belgesi konusunun ["daha fazla bilgi gerekiyor" bölümüne](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017?view=vs-2017#when-further-information-is-needed-need-more-info) bakın.

> [!NOTE] 
> **En değerli geri bildirim:** Neredeyse tüm yavaşlamalar/yüksek CPU sorunları için en değerli geri bildirim, bu süre boyunca davranışı yakalayan performans izleme (\*. etl. zip) ile birlikte, ne yapmaya çalıştığınız hakkında üst düzey bir açıklamadır.

**Gelişmiş performans Izlemeleri**

Rapor-sorun aracında izleme koleksiyonu özellikleri çoğu senaryo için yeterlidir. Ancak, izleme koleksiyonu üzerinde daha fazla denetim gerekli olduğunda (örneğin, daha büyük bir arabellek boyutu ile izleme), bu durumda PerfView kullanmak için harika bir araçtır. PerfView aracını kullanarak performans izlemesini el ile kaydetme adımları, [PerfView Ile kaydetme performansı izlemeleri](https://github.com/dotnet/roslyn/wiki/Recording-performance-traces-with-PerfView) sayfasında bulunabilir.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio geri bildirim seçenekleri](../ide/feedback-options.md)
* [Mac için Visual Studio sorun bildirme](/visualstudio/mac/report-a-problem)
* [İle ilgili bir sorun bildirinC++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Visual Studio Geliştirici topluluğu](https://developercommunity.visualstudio.com/)
* [Geliştirici topluluğu veri gizliliği](developer-community-privacy.md)
