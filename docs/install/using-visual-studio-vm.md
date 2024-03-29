---
title: Visual Studio kullanarak bir Azure sanal makinesinde
titleSuffix: ''
description: Bir Azure sanal makinesinde Visual Studio kullanmayı öğrenin
ms.date: 12/06/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- azure services
- virtual machine
- installation
- visual studio
author: PhilLee-MSFT
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: dc5fc9642401b1c90f079cae714fca9e214d6d9c
ms.sourcegitcommit: 0b90e1197173749c4efee15c2a75a3b206c85538
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2019
ms.locfileid: "74903858"
---
# <a id="top"> </a> Azure'da Visual Studio görüntüleri

Önceden yapılandırılmış Azure sanal makineler'de (VM) Visual Studio kullanarak herhangi bir şey bir yukarı ve çalışan geliştirme ortamına gitmek için hızlı ve kolay bir yoludur. Sistem görüntüleri farklı Visual Studio yapılandırmalarıyla kullanılabilir [Azure Marketi](https://azuremarketplace.microsoft.com/marketplace/apps/category/compute?filters=virtual-machine-images%3Bmicrosoft%3Bwindows&page=1&subcategories=application-infrastructure).

Azure'da yeni misiniz? [Ücretsiz Azure hesabı oluşturun](https://azure.microsoft.com/free).

## <a name="what-configurations-and-versions-are-available"></a>Hangi yapılandırmaları ve sürümlerinin kullanılabilir mi?

En son ana sürümlere ait görüntüler, Visual Studio 2019, Visual Studio 2017 ve Visual Studio 2015, Azure Marketi 'nde bulunabilir.  Yayınlanan her ana sürüm için, başlangıçta "Web 'e Yayınlandı" (RTW) sürümü ve en son güncelleştirilmiş sürümleri görürsünüz.  Bu sürümlerin her biri, Visual Studio Enterprise ve Visual Studio Community sürümleri sunar.  Bu görüntüler, en son Visual Studio ve Windows güncelleştirmelerini dahil etmek için en az her ay güncelleştirilir.  Her görüntünün açıklaması, yüklü bir ürün sürümü ve görüntünün "Başlangıç" tarihi görüntüleri adları aynı kalsa da içerir.

| Yayın sürümü                                                                                                                                          | Sürümler              |    Ürün sürümü    |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------:|:---------------------:|:-----------------------:|
| [Visual Studio 2019: en son (sürüm 16,4)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio2019latest?tab=Overview) | Kurumsal ve topluluk | Sürüm 16.4.0    |
| [Visual Studio 2019: RTW](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio2019?tab=Overview)                         | Enterprise            | Sürüm 16.0.9    |
| [Visual Studio 2017: en son (sürüm 15,9)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)           | Kurumsal ve topluluk | Sürüm 15.9.17   |
| [Visual Studio 2017: RTW](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)                             | Kurumsal ve topluluk | Sürüm 15.0.27   |
| [Visual Studio 2015: latest (güncelleştirme 3)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)               | Kurumsal ve topluluk | Sürüm 14.0.25431.01 |

> [!NOTE]
> Hizmet İlkesi Microsoft uygun olarak hizmet vermek için Visual Studio 2015'in yayınlanmış (RTW) sürüm süresi doldu. Visual Studio 2015 güncelleştirme 3 için Visual Studio 2015 ürün sınıfıyla sunulan yalnızca kalan sürümüdür.

Daha fazla bilgi için [Visual Studio Hizmet İlkesi](/visualstudio/productinfo/vs-servicing-vs).

## <a name="what-features-are-installed"></a>Hangi özellikleri yüklenir?

Bu Visual Studio sürümü için önerilen özelliklere her görüntü içerir. Genel olarak, yüklemeyi içerir:

* Önerilen tüm kullanılabilir iş yükleri, her iş yükünün dahil olmak üzere isteğe bağlı bileşenler
* .NET 4.6.2 ve .NET 4.7 geliştirici araçları SDK'ları ve hedefleme paketleri
* Visual F#
* Visual Studio için GitHub uzantısı
* LINQ to SQL araçları

Görüntüleri oluştururken Visual Studio'yu yüklemek için aşağıdaki komut satırını kullanın:

```shell
    vs_enterprise.exe --allWorkloads --includeRecommended --passive ^
       --add Microsoft.Net.Component.4.7.SDK ^
       --add Microsoft.Net.Component.4.7.TargetingPack ^
       --add Microsoft.Net.Component.4.6.2.SDK ^
       --add Microsoft.Net.Component.4.6.2.TargetingPack ^
       --add Microsoft.Net.ComponentGroup.4.7.DeveloperTools ^
       --add Microsoft.VisualStudio.Component.FSharp ^
       --add Component.GitHub.VisualStudio ^
       --add Microsoft.VisualStudio.Component.LinqToSql
```

Görüntüleri gerektiren bir Visual Studio özelliği dahil etmezseniz, sayfanın sağ üst köşesindeki geri bildirim aracında aracılığıyla geri bildirim sağlayın.

## <a name="what-size-vm-should-i-choose"></a>VM boyutu seçmem gerekir?

Azure sanal makine boyutları sunar. Visual Studio, güçlü, çok iş parçacıklı bir uygulama olduğundan, 7 GB bellek ve en az iki işlemcileri içeren bir VM boyutu istersiniz. Visual Studio görüntüleri için aşağıdaki VM boyutları öneririz:

* Standard_D2_v3
* Standard_D2s_v3
* Standard_D4_v3
* Standard_D4s_v3
* Standard_D2_v2
* Standard_D2S_v2
* Standard_D3_v2

En son makine boyutları hakkında daha fazla bilgi için bkz. [boyutları için Windows azure'da sanal makineler](/azure/virtual-machines/windows/sizes).

Azure ile ilk seçiminizi VM'yi yeniden boyutlandırmadan olarak yeniden dengeleyebilir. Daha uygun bir boyut ile yeni bir VM sağlama veya farklı bir temel alınan donanım için var olan sanal makinenizi yeniden boyutlandırma. Daha fazla bilgi için [Windows VM'yi yeniden boyutlandırma](/azure/virtual-machines/windows/resize-vm).

## <a name="after-the-vm-is-running-whats-next"></a>Sanal makine çalışmaya başladıktan sonra bu sırada ne var?

Visual Studio, azure'a "kendi lisansını getir" modelini kullanır. Bir yüklemede gibi özel bir donanım ile ilk adımlarından biri Visual Studio yüklemenizin lisanslama. Visual Studio ya da kilidini açmak için:
- Visual Studio aboneliğiyle ilişkili Microsoft hesabınızla oturum açın
- Visual Studio ile ilk Alışverişinizi verilen ürün anahtarı kilidini aç

Daha fazla bilgi için [Visual Studio'da oturum](../ide/signing-in-to-visual-studio.md) ve [Visual Studio kilidini açma](../ide/how-to-unlock-visual-studio.md).

## <a name="how-do-i-save-the-development-vm-for-future-or-team-use"></a>Nasıl miyim gelecek için VM geliştirme kaydetme veya takım kullanıyor musunuz?

Geliştirme ortamlarını spektrumun büyük ve gerçek maliyet daha karmaşık ortamları oluşturmaya ile ilişkili. Ortamınızın yapılandırmasını bağımsız olarak kaydedebilir veya yakalama, bir "temel görüntü olarak" diğer ekip üyelerinin veya ileride kullanmak için yapılandırılan sanal makinenizin. Ardından, yeni bir sanal makine önyükleme yaparken, bunu Azure Market görüntüsü yerine temel görüntü sağlayın.

Kısa bir Özet: Sistem Hazırlama (Sysprep) aracını kullanın ve çalışan sanal makineyi ve ardından yakalamak *(Şekil 1)* Azure portalındaki kullanıcı Arabirimi aracılığıyla bir görüntü olarak VM. Azure kaydeder `.vhd` seçtiğiniz depolama hesabındaki görüntüsünü içeren dosya. Yeni görüntü sonra aboneliğinizin kaynak listesi bir görüntü kaynağı olarak görünür.

![Azure portal kullanıcı arabiriminden bir görüntü yakala](media/capture-vm.png)

*(Şekil 1) Azure portal kullanıcı arabiriminden bir görüntü yakalayın.*

Daha fazla bilgi için [Azure'da bir genelleştirilmiş VM'nin yönetilen görüntüsünü oluşturma](/azure/virtual-machines/windows/capture-image-resource).

> [!IMPORTANT]
> VM'yi hazırlama için Sysprep kullanma unutmayın. Bu adımı atlarsanız Azure VM'den görüntü sağlayamazsınız.

> [!NOTE]
> Yine de görüntülerin depolama için bazı maliyetler doğurur, ancak bir gereksinim duyan her ekip üyesi için sıfırdan bir VM yeniden oluşturmak için yüksek maliyetleri karşılaştırıldığında maliyet artışı Önemsiz olabilir. Örneğin, oluşturmak ve takımınız tarafından yeniden kullanılabilir bir ay için 127 GB'lık görüntü depolamak için birkaç lira karşılığında maliyeti. Ancak, bu her çalışan oluşturmak ve bunların bireysel kullanıma yönelik bir düzgün bir şekilde yapılandırılmış geliştirme kutusunda doğrulamak için yatırım alışkanlıklarını saate kıyasla anlamsız ücretlerdir.

Ayrıca, geliştirme görevleri veya teknolojileri geliştirme yapılandırmaları ve birden çok makine yapılandırmaları çeşitleri gibi daha fazla ölçek gerekebilir. Azure DevTest Labs oluşturmak için kullanabileceğiniz _tarifler_ , "altın görüntü." yapımı otomatikleştirin DevTest Labs, ekibinizin çalışan VM'ler için ilkelerini yönetmek için de kullanabilirsiniz. [Geliştiriciler için Azure DevTest Labs'i kullanarak](/azure/devtest-lab/devtest-lab-developer-lab) DevTest Labs hakkında daha fazla bilgi için en iyi bir kaynaktır.

## <a name="next-steps"></a>Sonraki adımlar

Önceden yapılandırılmış Visual Studio görüntüler hakkında artık bildiğinize göre sonraki adım yeni bir VM oluşturmaktır:

* [Azure portalından bir VM oluşturma](/azure/virtual-machines/windows/quick-create-portal)
* [Windows sanal makinelerine genel bakış](/azure/virtual-machines/windows/overview)
