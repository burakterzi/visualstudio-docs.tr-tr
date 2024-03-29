---
title: Yönetici olarak çalıştır
ms.date: 06/05/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6086485ef20330de7971297f52a112d5183ee4a2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647342"
---
# <a name="user-permissions-and-visual-studio"></a>Kullanıcı izinleri ve Visual Studio

Güvenlik nedenleriyle, mümkün olduğunda Visual Studio 'Yu normal bir kullanıcı olarak çalıştırmanız gerekir.

> [!WARNING]
> Ayrıca güvenilir bir kişi ya da güvenilir bir konumdan gelmeyen herhangi bir Visual Studio çözümüyle derleme, başlatma veya hata ayıklama yapmadığınızdan emin olmalısınız.

Visual Studio IDE 'deki neredeyse her şeyi normal kullanıcı olarak yapabilirsiniz. Aşağıdaki görevleri gerçekleştirmek için yönetici izinlerine sahip olmanız gerekir:

|Alan|Görev|Daha fazla bilgi için|
|----------|----------| - |
|Yükleme|Visual Studio 'Yu yükler.|[Visual Studio'yu yükleyin](../install/install-visual-studio.md)|
||Yerel Yardım içeriğini yükler, güncelleştirir veya kaldırır.|[Yerel Yardım içeriğini yükleyip yönetme](../help-viewer/install-manage-local-content.md)|
|Araç Kutusu|**Araç kutusuna**klasik com denetimleri ekleyin.|[Araç Kutusu](../ide/reference/toolbox.md)|
|Oluşturma|Bir bileşeni kaydeden oluşturma sonrası olayları kullanın.|[Özel derleme adımlarını ve derleme olaylarını anlama](/cpp/build/understanding-custom-build-steps-and-build-events)|
||C++ Proje oluştururken bir kayıt adımı ekleyin.||
|Hata Ayıklama|Yükseltilmiş izinlerle çalışan uygulamalarda hata ayıklayın.|[Hata ayıklayıcısı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)|
||ASP.NET Web siteleri gibi farklı bir kullanıcı hesabı altında çalışan uygulamalarda hata ayıklayın.|[ASP.NET ve AJAX uygulamalarında hata ayıklama](../debugger/how-to-enable-debugging-for-aspnet-applications.md)|
||XAML tarayıcı uygulamaları (XBAP) için bölgede hata ayıklama.|[WPF konağı (PresentationHost. exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Microsoft Azure için bulut hizmeti projelerinde hata ayıklamak için öykünücüyü kullanın.|[Visual Studio 'da bir bulut hizmetinde hata ayıklama](/azure/vs-azure-tools-debug-cloud-services-virtual-machines)|
||Uzaktan hata ayıklama için bir güvenlik duvarı yapılandırın.|[Uzaktan hata ayıklama](../debugger/remote-debugging.md)|
|Performans araçları|Yükseltilmiş bir uygulamaya iliştirme.|[Performans profili oluşturma için yeni başlayanlar kılavuzu](../profiling/beginners-guide-to-performance-profiling.md)|
||GPU Profiler 'ı kullanın.|[GPU profili oluşturma](../profiling/gpu-usage.md)|
|Dağıtım|Bir Web uygulamasını yerel bir bilgisayarda Internet Information Services (IIS) uygulamasına dağıtın.|[Visual Studio kullanarak bir ASP.NET Web uygulaması dağıtma](/aspnet/web-forms/overview/older-versions-getting-started/deployment-to-a-hosting-provider/)|

## <a name="run-visual-studio-as-an-administrator"></a>Visual Studio 'Yu yönetici olarak çalıştırma

Visual Studio 'Yu yönetici olarak çalıştırmanız gerekiyorsa IDE 'yi açmak için aşağıdaki adımları izleyin:

> [!NOTE]
> Bu yönergeler Windows 10 içindir. Bunlar, diğer Windows sürümlerine benzerdir.

::: moniker range="vs-2017"

1. **Başlat** menüsünü açın ve Visual Studio 2017 ' a kaydırın.

1. **Visual Studio 2017**' un sağ tıklama veya bağlam menüsünden **yönetici olarak çalıştır**> **daha fazla** ' yı seçin.

   Visual Studio başladığında, başlık çubuğunda ürün adından sonra **(yönetici)** görüntülenir.

::: moniker-end

::: moniker range=">=vs-2019"

1. **Başlat** menüsünü açın ve Visual Studio 2019 ' a kaydırın.

1. **Visual Studio 2019**' un sağ tıklama veya bağlam menüsünden **yönetici olarak çalıştır**> **daha fazla** ' yı seçin.

   Visual Studio başladığında, başlık çubuğunda ürün adından sonra **(yönetici)** görüntülenir.

::: moniker-end

Ayrıca, uygulama kısayolunu her zaman yönetici izinleriyle çalışacak şekilde değiştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Visual Studio'yu yükleyin](../install/install-visual-studio.md)