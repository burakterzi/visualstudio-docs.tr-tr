---
title: HPC üzerinde profil oluşturma (yüksek performanslı bilgi Işlem) kümeleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.hpc.wizard.exeoptions
- vs.performance.hpc.wizard.summary
- vs.performance.hpc.wizard.startoptions
- vs.performance.hpc.wizard.intro
- vs.performance.hpc.property.basic
- vs.performance.hpc.wizard.application
- vs.performance.hpc.wizard.clusteroptions
- vs.performance.hpc.property.advanced
helpviewer_keywords:
- profililng tools,HPC
- HPC profiling
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f2d3949194dedab6d7e7ea2faa1aea304d889bc4
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74772126"
---
# <a name="profile-on-hpc-high-performance-computing-clusters"></a>HPC (yüksek performanslı bilgi işlem) kümelerinde profil

Visual Studio Profil Oluşturma Araçları örnekleme yöntemini kullanarak Microsoft Windows HPC kümelerinin işlem düğümlerinde profil oluşturabilirsiniz. HPC hakkında daha fazla bilgi için bkz. Microsoft Web sitesinde [WINDOWS HPC](https://azure.microsoft.com/solutions/big-compute/) .

## <a name="prerequisites"></a>Prerequisites

Bir HPC işlem düğümünde profil yapmak için aşağıdakileri yapmanız gerekir:

- Microsoft HPC Pack 2008 ' i Visual Studio ile aynı bilgisayara yükler. Bilgisayar HPC kümesinin bir parçası olmak zorunda değildir. HPC Pack 'i [Microsoft Indirme merkezi](https://www.microsoft.com/download/details.aspx?id=4812)' nde yükleyebilirsiniz.

- .NET Framework 4 ve Profil Oluşturma Araçları tek başına sürümünü HPC işlem düğümüne yükler. Hem .NET Framework hem de tek başına profil Oluşturucu için program yükleme, Visual Studio yükleme medyasında bulunabilir. **Göz önünde** .NET Framework yükledikten ve Profil Oluşturma Araçları yüklemeden önce işlemi yeniden başlatmanız gerekir.

  .NET Framework 4 ve tek başına Profil Oluşturma Araçları etkin bir HPC işlem düğümüne yüklemek ve küme makinesinde profil oluşturmayı etkinleştirmek için şu adımları izleyin:

1. HPC Pack ile yüklenen komut istemi penceresini açın.

2. Aşağıdaki komutları ayrı komut istemlerine yazın:

    1. `clusrun /all /scheduler:` *% Headnode%% FxPath%* `/q /norestart`

    2. `clusrun /all /scheduler:` *% Headnode%* `shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`

    3. %% *ProfilerPath% `/q /norestart` `clusrun /all /scheduler:`% Headnode*

| | |
|------------------| - |
| *Baş düğümüne* | Kümenin baş düğümünün adı. |
| *% FxPath%* | .NET Framework 4 yükleyicisinin yolu. Visual Studio yükleme medyasında yol şu şekilde olur: WCU\dotNetFramework\ dotNetFx40_Full_x86_x64. exe |
| *% ProfilerPath%* | Profil Oluşturma Araçları yükleyicisinin bağımsız sürümünün yolu. Visual Studio yükleme medyasında yol: tek başına Profiler\x64\ vs_profiler. exe ' dir |

## <a name="profile-on-an-hpc-compute-node"></a>HPC işlem düğümündeki profil

HPC kümesi ve hedef bilgilerini belirtmek için HPC performans sihirbazını kullanarak bir profil oluşturma oturumu yapılandırırsınız. Performans oturumu özellik sayfalarında ek seçenekler belirleyebilirsiniz. Profil Oluşturma Araçları, gerekli hedef ikilileri otomatik olarak dağıtır ve profil oluşturucu ve HPC uygulamasını başlatır.

1. **Çözümle** menüsünde **HPC Performans Sihirbazını Başlat**' ı tıklatın. Komut kullanılamıyorsa, yukarıda listelenen önkoşullara sahip olduğunuzdan emin olun.

2. Sihirbazın ilk sayfasında **İleri** ' ye tıklayın.

3. Sihirbazın ikinci sayfasında, profil atamak istediğiniz uygulamayı seçin.

   - [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]Şu anda açık olan bir projenin profilini almak için, **bir veya daha fazla kullanılabilir proje** seçeneğini belirleyin ve ardından listeden proje adını seçin.

   - Açık bir projede olmayan bir ikilinin profilini eklemek için **çalıştırılabilir (. EXE dosyası)** seçeneğini.

4. **İleri**'ye tıklayın.

5. Sihirbazın üçüncü sayfasında:

    - Açık bir projede olmayan bir yürütülebilirin profilini oluşturuyorsanız, **yürütülebilir dosyanın tam yolu olan**ikili dosyanın yolunu belirtin.

    - Açık bir projede olmayan bir yürütülebilir dosya profili oluşturuyorsanız, **komut satırı bağımsız değişkenlerinde**işleme geçirilecek komut satırı bağımsız değişkenlerini belirtebilirsiniz.

    - **Uzak çalışma dizini**' nde, bireysel işlem düğümlerinde işlem örnekleri tarafından kullanılan klasörün yolunu belirtin.

    - **Dağıtım konumu**' nda HPC sunucusunun dağıtım için görüntüleri hazırlamak üzere kullandığı dizinin yolunu belirtin.

6. **İleri**'ye tıklayın.

7. Sihirbazın dördüncü sayfasında:

    - **Baş düğüm** listesinde, profil oluşturma çalıştırmasında HPC head düğümü olarak davranan bilgisayara tıklayın. Baş düğüm "localhost" olabilir ve bu, yerel makinede bir kümeye gerek duymadan profil gerçekleştirmenizi sağlar.

    - **Işlem sayısı** listesinde, çalıştırılacak uygulamanın örnek sayısına tıklayın.

    - **Profil oluşturma seçenekleri** listesinden profil oluşturma hedefini seçin.

         Kümede belirli bir işlemi profili eklemek için, **derece üzerinde profil** seçeneğini belirleyin ve ardından açılır listeden işlemin sırasını seçin.

         HPC kümesindeki belirli bir düğümde çalışan işlem veya işlemlerin profilini belirlemek için **düğüm üzerinde profil** seçeneğini belirleyin ve ardından açılan listeden düğümü seçin.

8. **İleri**'ye tıklayın.

9. Sihirbazın beşinci sayfasında, profil oluşturucuyu ve profil oluşturma işlemini hemen başlatmayı veya Performans Gezgini kullanarak daha sonra profil oluşturmayı başlatmayı seçebilirsiniz.

    - Profil oluşturmayı hemen başlatmak için **sihirbaz bittikten sonra profil oluşturmayı Başlat** ' ı seçin veya profil oluşturmayı el ile başlatmak için onay kutusunun işaretini kaldırın.

10. **Son**'a tıklayın.

## <a name="set-hpc-profiling-properties-by-using-performance-session-property-pages"></a>Performans oturumu özellik sayfalarını kullanarak HPC profil oluşturma özelliklerini ayarlama

Performans oturumu özellikleri sayfasının HPC Başlatma Özellikleri sayfasında HPC profil oluşturma Sihirbazı 'nda ayarladığınız performans oturumu özelliklerini değiştirebilirsiniz. HPC gelişmiş özellikler sayfasında ek seçenekleri ayarlarsınız.

### <a name="to-open-the-performance-session-property-pages"></a>Performans oturumu özellik sayfalarını açmak için

1. Gerekirse, Performans Gezgini ' de performans oturumu (. psess) dosyasını açın. **Dosya** menüsünde **Aç** ' a tıklayın ve dosyayı bulun.

2. Performans Gezgini, performans oturumu adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.

3. Özellik sayfaları iletişim kutusunda, aşağıdaki yöntemlerden birini kullanın:

    - **Genel** ' e tıklayın ve HPC profil oluşturmayı açmak Için HPC **kümesinde topla** ' yı seçin veya HPC profil oluşturmayı devre dışı bırakmak için onay kutusunun işaretini kaldırın.

    - HPC uygulamasını Başlatan özellikleri değiştirmek için **HPC Başlatma Özellikleri** ' ne tıklayın.

    - Ek seçenekleri ayarlamak için **HPC gelişmiş özellikler** ' e tıklayın

### <a name="hpc-launch-properties"></a>HPC Başlatma Özellikleri

|Özellik|Açıklama|
|--------------|-----------------|
|**Baş düğüm**|Profil oluşturma çalıştırmasında HPC head düğümü olarak davranan bilgisayarı belirtir.|
|**İşlem sayısı**|Profili oluşturulan uygulamada çalıştırılacak uygulamanın örnek sayısını belirtir.|
|**Sırasıyla profil**|Kümede belirli bir işlemi profili eklemek için, **derece üzerinde profil** seçeneğini belirleyin ve ardından açılır listeden işlemin sırasını seçin.|
|**Düğüm üzerindeki profil**|HPC kümesindeki belirli bir düğümde çalışan işlem veya işlemlerin profilini belirlemek için **düğüm üzerinde profil** seçeneğini belirleyin ve ardından açılan listeden düğümü seçin.|
|**Uzak çalışma dizini**|Bireysel işlem düğümlerinde işlem örnekleri tarafından kullanılan klasörün yolunu belirtir.|
|**Dağıtım konumu**|HPC sunucusunun dağıtım için görüntüleri hazırlamak üzere kullandığı dizinin yolunu belirtir.|

### <a name="advanced-properties"></a>Gelişmiş Özellikler

| Özellik | Açıklama |
|---------------------------------------| - |
| **Proje adı** | Geçerli [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] projesinin veya çözümün adı. |
| **Profil Oluşturucu durdurulduğunda temizle** | Doğru olduğunda, yürütme dizinine dağıtılan ikilileri kaldırır. Kullanıcı programı tarafından oluşturulan dosyalar ve dizinler bu adımda kaldırılmaz. Yürütme dizini ve dağıtım dizini IDE tarafından oluşturulduysa, IDE bunları kaldırmaya çalışır, ancak IDE tarafından dağıtılmayan dosyalar varsa bunu yapmaz. |
| **Dağıtılacak ek dosyalar** | İşlem düğümünde dağıtılacak ek dosyaların noktalı virgülle ayrılmış bir listesini belirtir. Bir iletişim kutusunu kullanarak birden çok dosya seçmek için üç nokta düğmesini ( **...** ) tıklayabilirsiniz. |
| **Mpiexec komutu** | MPı uygulamasını Başlatan uygulamayı belirtir. Varsayılan değer **Mpiexec. exe** ' dir |
| **Mpiexec bağımsız değişkenleri** | Mpiexec. exe komutuna geçirilecek bağımsız değişkenleri belirtir. |
| **Kümede istenen düğümler** | Uygulamanın çalıştırılacağı kümedeki düğüm sayısını belirtir. |
| **CRT dosyaları dağıtma** | Doğru olduğunda, küme üzerinde C/C++ çalışma süresini dağıtır. |
| **Ön profil betiği** | Profil oluşturma oturumu başlamadan önce yerel geliştirme bilgisayarında çalıştırılacak betiğin yolunu ve dosya adını belirtir. |
| **Profil öncesi betik bağımsız değişkenleri** | Profil öncesi betiğe geçirilecek bağımsız değişkenleri belirtir. |
| **Profil sonrası betiği** | Profil oluşturma oturumu bittikten sonra yerel geliştirme bilgisayarında çalıştırılacak betiğin yolunu ve dosya adını belirtir. |
| **Profil sonrası betik bağımsız değişkenleri** | Profil sonrası betiğe geçirilecek bağımsız değişkenleri belirtir. |
