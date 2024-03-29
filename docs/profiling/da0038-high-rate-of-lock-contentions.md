---
title: 'DA0038: yüksek oranda kilit çekişmeleri | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.38
- vs.performance.rules.DA0038
- vs.performance.DA0038
ms.assetid: ae0c8b2f-17b2-4f3d-a834-aa2f6371753b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d8e0218b01a162a3af8c35009bc8e733f5c386ef
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777508"
---
# <a name="da0038-high-rate-of-lock-contentions"></a>DA0038: yüksek oranda kilit çekişmeleri

|||
|-|-|
|Kural Kimliği|DA0038|
|Kategori|.NET Framework kullanımı|
|Profil oluşturma yöntemi|Aşağıdakine<br /><br /> İzleme<br /><br /> .NET belleği|
|İleti|Yüksek oranda .NET kilit çekişmeleri meydana geldiğini belirtir. Lütfen eşzamanlılık profilini çalıştırarak bu kilit çakışmasının nedenini araştırın.|
|Kural türü|Bilgisi|

 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 25 örnek toplamanız gerekir.

## <a name="cause"></a>Sebep
 Profil oluşturma verileriyle toplanan sistem performansı verileri, uygulama yürütmesi sırasında önemli ölçüde yüksek bir kilit çekişmesinin gerçekleştiğini gösterir. Çekişmelerin nedenini bulmak için eşzamanlılık profil oluşturma yöntemini kullanarak profil oluşturmayı yeniden düşünün.

## <a name="rule-description"></a>Kural açıklaması
 Kilitler, çok iş parçacıklı bir uygulamada tek seferde bir iş parçacığı tarafından yürütülmesi gereken önemli kod bölümlerini korumak için kullanılır. Microsoft .NET ortak dil çalışma zamanı (CLR), tam bir eşitleme ve kilitleme temelleri kümesi sağlar. Örneğin, C# dil bir kilit ifadesini (Visual Basic 'de SyncLock) destekler. Yönetilen bir uygulama, doğrudan bir kilit edinmek ve serbest bırakmak için System. Threading ad alanındaki Monitor. Enter ve Monitor. Exit yöntemlerini çağırabilir. .NET Framework, zaman uyumu sağlayıcılar, Readerwriterkilitleri ve semaforları destekleyen sınıflar da dahil olmak üzere ek eşitleme ve kilitleme temel öğelerini destekler. Daha fazla bilgi için, MSDN Web sitesindeki .NET Framework Geliştirici kılavuzundaki [eşitleme temel bilgilerine genel bakış](/dotnet/standard/threading/overview-of-synchronization-primitives) konusuna bakın. .NET Framework sınıfları, Windows işletim sisteminde yerleşik olarak bulunan alt düzey Eşitleme Hizmetleri üzerinde katmanlıdır. Bunlar, kritik bölüm nesnelerini ve birçok farklı bekleme ve olay sinyali işlevini içerir. Daha fazla bilgi için, MSDN Kitaplığı 'nda Win32 ve COM Geliştirme 'nin [eşitleme](/windows/win32/sync/synchronization) bölümüne bakın.

 Hem .NET Framework sınıfları hem de eşitleme ve kilitleme için kullanılan yerel Windows nesnelerini temel alan, birbirine kenetlenmiş işlemler kullanılarak değiştirilmesi gereken paylaşılan bellek konumlarıdır. Birbirine kenetlenmiş işlemler, Atomik işlemler kullanılarak durumlarını değiştirmek üzere paylaşılan bellek konumlarında çalışan donanıma özgü yönergeler kullanır. Atomik işlemlerin makinedeki tüm işlemciler arasında tutarlı olması garanti edilir. Kilitler ve WaitHandle, otomatik olarak karşılıklı kilitleme işlemlerini ayarlanan veya sıfırlanan zaman kullanan .NET nesneleridir. Uygulamanızda, iş parçacığı güvenli bir biçimde güncelleştirilmesini sağlamak için birbirine kenetlenmiş işlemleri de kullanmanızı gerektiren başka paylaşılan bellek veri yapıları olabilir. Daha fazla bilgi için bkz. MSDN Kitaplığı 'nın .NET Framework bölümünde [karşılıklı kilitleme işlemleri](/dotnet/api/system.threading.interlocked) .

 Eşitleme ve kilitleme, çok iş parçacıklı uygulamaların doğru şekilde yürütmesini sağlamak için kullanılan mekanizmalarda bulunur. Çok iş parçacıklı bir uygulamanın her iş parçacığı, işletim sistemi tarafından bağımsız olarak zamanlanan bağımsız bir yürütme birimidir. Bir kilit elde edilmeye çalışan bir iş parçacığı gecikmeli tutulduğu için kilit çakışması oluşur.

 Kilitler genellikle iç içe geçmiş. İç içe geçme, kritik bir bölümü yürüten bir iş parçacığı daha sonra başka bir kilit gerektiren bir işlev gerçekleştirdiğinde oluşur. Kilit iç içe geçme miktarı kaçınılmaz. Kritik bölüm, iş parçacığı açısından güvenli olduğundan emin olmak için kilitlerin kullanıldığı bir .NET Framework yöntemi çağırabilir. Uygulamanızdaki bazı kritik bölümden, farklı bir kilit tanıtıcısı kullanarak da kilitleyen bir çerçeve yöntemine yapılan çağrı, kilitlerin iç içe geçmesine neden olur. İç içe kilitleme koşulları, kaçınılması ve düzeltilmesi açısından önemli bir şekilde zor olan performans sorunlarına neden olabilir.

 Bu kural, bir profil oluşturma çalışması sırasında alınan ölçümler, aşırı yüksek miktarda kilit çakışması olduğunu gösteriyorsa ateşlenir. Kilit çekişmeleri, kilidi bekleyen iş parçacıklarının yürütülmesini geciktirecek. Birim testlerinde veya daha düşük bir uçta çalışan yük testlerinde çok az miktarda kilit çakışması araştırılmalıdır.

> [!NOTE]
> Profil oluşturma verilerinde raporlanan kilit çekişmelerinin oranı aşırı yüksek olduğunda, bu bilgi iletisi yerine [DA0039: çok yüksek oranda kilit çekişmeleri](../profiling/da0039-very-high-rate-of-lock-contentions.md) uyarı iletisi tetiklenir.

## <a name="how-to-investigate-a-warning"></a>Uyarı araştırma
 Profil oluşturma verilerinin [işaretler](../profiling/marks-view.md) görünümüne gitmek için iletiye çift tıklayın.  **.NET CLR Locksandthreads\çekişme hız/sn** sütununu bulun. Kilit çekişmesinin diğer aşamalara göre daha ağır olduğu program yürütmesinin belirli aşamaları olup olmadığını belirleme.

 Bu kural yalnızca eşzamanlılık profil oluşturma yöntemini kullanmadığınız durumlarda ateşlenir. Eşzamanlılık profili oluşturma yöntemi, uygulamanızdaki kilit çakışması ile ilgili performans sorunlarını tanılamak için kullanılan en iyi araçtır. Uygulamanızın kilitleme davranışını anlamak için eşzamanlılık profili oluşturma verileri toplayın. Bu, hangi kilitlerin çok fazla sürdüğünü, iş parçacığı yürütme zamanının, contenerme kilitleri için ne kadar gecikdiğini ve belirli kodun ne tür bir şekilde olduğunu anlamayı içerir. Eşzamanlılık profilleri, yerel Windows tesislerinin kilitleme davranışı, .NET Framework sınıfları ve uygulamanızın başvurduğu diğer üçüncü taraf kitaplıkları da dahil olmak üzere tüm kilit çekişmeleri üzerinde veri toplar. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 'den eşzamanlılık profili oluşturma hakkında daha fazla bilgi için bkz. [iş parçacığı toplama ve eşzamanlılık verilerini işleme](../profiling/collecting-thread-and-process-concurrency-data.md). Komut satırından eşzamanlılık profili oluşturma hakkındaki bilgilerin bağlantıları için, [komut satırından profil oluşturma yöntemlerini kullanma](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)konusunun **kaynak çekişmesini ve iş parçacığı etkinlik verilerini toplamak Için eşzamanlılık yöntemini kullanma** bölümüne bakın.
