---
title: VSPackage kurulum senaryoları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eddfc0aa9b8f5b3a169ce87b31a2221983f57aaa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722181"
---
# <a name="vspackage-setup-scenarios"></a>VSPackage Kurulum Senaryoları

Bir esneklik için VSPackage yükleyicinizi tasarlamak önemlidir. Örneğin, gelecekte bir güvenlik düzeltme ekini serbest bırakmanız veya kapsamlı yan yana sürüm desteği gerektiren bir iş stratejisini değiştirmeniz gerekebilir.

[Visual Studio 'Nun birden çok sürümünü destekleyerek](../../extensibility/supporting-multiple-versions-of-visual-studio.md), VSPackage 'ın paylaşılan veya yan yana yüklemeleri ile [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yan yana yüklemelerini desteklemeye yönelik avantajlar ve sorunlar hakkında bilgi edinebilirsiniz. Kısa bir yandan yan yana VSPackages, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yeni özelliklerini desteklemek için size en fazla esneklik sağlar.

Bu konuda tartışılan senaryolar yalnızca Seçimlerinizden değildir, ancak önerilen en iyi uygulamalar olarak sunulur.

## <a name="components-privacy-and-sharing"></a>Bileşenler, gizlilik ve paylaşım

### <a name="make-your-components-independent"></a>Bileşenlerinizi bağımsız hale getirme

Bir bileşeni tanımlayıp doldurduktan sonra bir `GUID` atayıp bileşeni dağıttıktan sonra, kompozisyonunu değiştiremezsiniz. Bir bileşenin kompozisyonunu değiştirirseniz, sonuçta elde edilen bileşen yeni bir `GUID` yeni bir bileşen olmalıdır. Bu olgular verildiğinde, en büyük sürüm oluşturma esnekliği, her bileşene bağımsız, kendine bağlı birim yapılarak gerçekleştirilir. Bileşenleri yöneten kurallar hakkında daha fazla bilgi için bkz. [bileşen kodunu değiştirme](/windows/desktop/Msi/changing-the-component-code) ve [bileşen kuralları bozulur ne olur?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Bir bileşende paylaşılan ve özel kaynakları karıştırma

Başvuru sayımı bileşen düzeyinde oluşur. Sonuç olarak, paylaşılan ve özel kaynakları tek bir bileşende karıştırmak, paylaşılan kaynakların üzerine yazmadan yürütülebilir bir dosya gibi özel kaynakların güncelleştirilmesini olanaksız hale getirir. Bu senaryo, geriye dönük uyumluluk sorunları oluşturur ve yan yana yetenek oluşturma işlemini kısıtlar.

Örneğin, VSPackage 'ı [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] kaydetmek için kullanılan kayıt defteri değerleri, VSPackage 'ı Visual Studio ile kaydetmek için kullanılan bir bileşende ayrı bir bileşende tutulmalıdır. Paylaşılan dosyalar veya kayıt defteri değerleri, başka bir bileşeni de daha sonra gider.

## <a name="scenario-1-shared-vspackage"></a>Senaryo 1: Paylaşılan VSPackage

Bu senaryoda, paylaşılan bir VSPackage (Visual Studio 'nun birden çok sürümünü destekleyen tek bir ikili dosya Windows Installer bir pakette gönderilir. Visual Studio 'nun her bir sürümüyle kaydolmak, Kullanıcı tarafından seçilebilen özelliklerle denetlenir. Ayrıca, ayrı özelliklere atandığında her bir bileşen yükleme veya kaldırma için tek tek seçilebileceği anlamına gelir. Bu, kullanıcıyı VSPackage 'ı farklı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sürümleriyle tümleştirme denetimine yerleştiriyor. (Windows Installer paketlerindeki özellikleri kullanma hakkında daha fazla bilgi için bkz. [Windows Installer özellikleri](/windows/desktop/Msi/windows-installer-features) .)

![VS Paylaşılan VSPackage yükleyicisi](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Çizimde gösterildiği gibi, paylaşılan bileşenler her zaman yüklenen Feat_Common özelliğinin bir parçası haline getirilir. Feat_VS2002 ve Feat_VS2003 özelliklerini görünür hale getirerek, kullanıcılar, VSPackage 'ın hangi Visual Studio sürümlerine tümleştirileceğini istediğini bir kez seçebilirler. Kullanıcılar ayrıca, özellikleri eklemek veya kaldırmak için Windows Installer bakım modunu da kullanabilir. Bu durumda, Visual Studio 'nun farklı sürümlerindeki VSPackage kayıt bilgilerini ekler veya kaldırır.

> [!NOTE]
> Özelliğin görüntüleme sütununun 0 olarak ayarlanması onu gizler. 1 gibi düşük düzey bir sütun değeri, her zaman yüklenmesini sağlar. Daha fazla bilgi için bkz. [INSTALLLEVEL özelliği](/windows/desktop/Msi/installlevel) ve [özellik tablosu](/windows/desktop/Msi/feature-table).

## <a name="scenario-2-shared-vspackage-update"></a>Senaryo 2: Paylaşılan VSPackage güncelleştirmesi

Bu senaryoda, senaryo 1 ' de VSPackage yükleyicisinin güncelleştirilmiş bir sürümü gönderilir. Bu tartışma için, güncelleştirme Visual Studio için destek ekler, ancak daha basit bir güvenlik düzeltme eki veya hata düzeltme hizmet paketi de olabilir. Windows Installer daha yeni bileşenleri yükleme kuralları, sistemde zaten değiştirilmemiş bileşenlerin yeniden kopyalanmadığını gerektirir. Bu durumda, sürüm 1,0 olan bir sistem zaten var olan Comp_MyVSPackage. dll ' nin üzerine yazar ve kullanıcıların yeni özellik Feat_VS2005 ' i Component Comp_VS2005_Reg ile eklemesini sağlar.

> [!CAUTION]
> @No__t_0 birden çok sürümü arasında bir VSPackage paylaşıldığında, VSPackage sonraki sürümlerinin, Visual Studio 'nun önceki sürümleriyle geriye dönük uyumluluk sağlamak önemlidir. Geriye dönük uyumluluğu koruyabileceğiniz yerlerde yan yana, özel VSPackages kullanmanız gerekir. Daha fazla bilgi için bkz. [Visual Studio 'Nun birden çok sürümünü destekleme](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![VS Paylaşılan VS paketi güncelleştirme yükleyicisi](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

Bu senaryo, küçük yükseltme desteğinin Windows Installer avantajlarından yararlanarak yeni bir VSPackage yükleyicisi sunmaktadır. Kullanıcılar yalnızca sürüm 1,1 ' ü yükler ve BT sürüm 1,0 ' i yükseltir. Ancak sistemde sürüm 1,0 ' ün olması gerekmez. Aynı Yükleyici sürüm 1,1 ' i sürüm 1,0 olmadan bir sisteme yükler. Bu şekilde küçük yükseltmeler sağlamanın avantajı, bir yükseltme yükleyicisi geliştirme ve tam ürün yükleyicisi geliştirme çalışmalarından faydalanmak için gerekli değildir. Bir yükleyici her iki işi de yapar. Bunun yerine bir güvenlik düzeltme veya hizmet paketi Windows Installer düzeltme eklerinden faydalanabilir. Daha fazla bilgi için bkz. [düzeltme eki uygulama ve yükseltme](/windows/desktop/Msi/patching-and-upgrades).

## <a name="scenario-3-side-by-side-vspackage"></a>Senaryo 3: yan yana VSPackage

Bu senaryo, Visual Studio .NET 2003 ve Visual Studio 'nun her sürümü için bir tane olmak üzere iki VSPackage yükleyicisi sunar. Her yükleyici, yan yana veya özel bir VSPackage (Visual Studio 'nun belirli bir sürümü için özel olarak oluşturulmuş ve yüklenmiş bir) yüklenir. Her VSPackage kendi bileşenidir. Sonuç olarak, her biri düzeltme ekleri veya bakım yayımları ile tek tek hizmet verebilir. VSPackage DLL 'SI artık sürüme özgü olduğundan, kayıt bilgilerini DLL ile aynı bileşene eklemek güvenlidir.

![VS yan yana VS paketi yükleyicisi](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Her yükleyici Ayrıca iki yükleyici arasında paylaşılan kod içerir. Paylaşılan kod ortak bir konuma yüklenirse, hem. msi dosyalarını yüklemek paylaşılan kodu yalnızca bir kez yükler. İkinci yükleyici, bileşen üzerindeki bir başvuru sayısını artırır. Başvuru sayısı, VSPackages 'tan birinin kaldırılması durumunda, paylaşılan kodun diğer VSPackage için de kalacağını sağlar. İkinci VSPackage da kaldırılırsa, paylaşılan kod kaldırılır.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Senaryo 4: yan yana VSPackage güncelleştirmesi

Bu senaryoda, Visual Studio için VSPackage bir güvenlik güvenlik açığıyla karşılaştı ve bir güncelleştirme yapmanız gerekiyor. Senaryo 2 ' de olduğu gibi, güvenlik düzeltmesini dahil etmek için mevcut bir yüklemeyi güncelleştiren ve güvenlik düzeltmesinin zaten bulunduğu yeni yüklemeleri dağıtan yeni bir. msi dosyası oluşturabilirsiniz.

Bu durumda, VSPackage, genel derleme önbelleğinde (GAC) yüklü bir yönetilen VSPackage ' dır. Güvenlik düzeltmesini dahil etmek için onu yeniden oluşturduğunuzda, derleme sürüm numarasının düzeltme numarası bölümünü değiştirmeniz gerekir. Yeni derleme sürüm numarası için kayıt bilgileri önceki sürümün üzerine yazılır ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sabit derlemeyi yüklemesine neden olur.

![VS yan yana VS paketi güncelleştirme yükleyicisi](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Yan yana derlemelerin dağıtımı hakkında daha fazla bilgi için bkz. [.NET Framework dağıtım ve çözme dll Hell](https://msdn.microsoft.com/library/ms973843.aspx).

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [Visual Studio'nun Birden Çok Sürümünü Destekleme](../../extensibility/supporting-multiple-versions-of-visual-studio.md)