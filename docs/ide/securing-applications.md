---
title: Güvenlik
ms.date: 06/01/2018
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio], applications
- application design, securability
ms.assetid: 7d32c4cf-8bec-4307-a2a8-42f0ceddf3eb
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 605a8301e0a016699822e32e24f82592862bb765
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72621607"
---
# <a name="secure-applications"></a>Uygulamaları güvenli hale getirme

Uygulama geliştirme sürecinizde, tasarımdan geliştirmeye kadar her yönüyle güvenliği göz önünde bulundurmalısınız. Visual Studio 'Yu olabildiğince güvenli şekilde çalıştırarak başlayın. Bkz. [Kullanıcı izinleri](../ide/user-permissions-and-visual-studio.md).

Etkin bir şekilde güvenli uygulamalar geliştirmenize yardımcı olması için, geliştirmekte olduğunuz platformların güvenlik kavramları ve güvenlik özellikleri hakkında temel bilgiye sahip olmanız gerekir. Güvenli kodlama tekniklerini de anlamanız gerekir.

## <a name="code-for-security"></a>Güvenlik için kod

Güvenlik açıklarına neden olan çoğu kodlama hatası, geliştiricilerin Kullanıcı girişiyle çalışırken yanlış varsayımlar yaptıkları veya geliştirdikleri platformu tam olarak anlayamadığı için oluşur.

- [Güvenli kodlama yönergeleri](/dotnet/standard/security/secure-coding-guidelines) , .net Code 'un güvenlik sistemiyle çalışmak üzere tasarlanma yöntemlerinin farklı yollarını açıklar.
- [İçin C++ en iyi güvenlik uygulamaları](/cpp/top/security-best-practices-for-cpp) , geliştiriciler için C++ güvenlik araçları ve uygulamalar hakkında bilgi içerir.

## <a name="build-for-security"></a>Güvenlik için derleme

Güvenlik Ayrıca derleme sürecinde önemli bir noktadır. Birkaç ek adım, dağıtılan bir uygulamanın güvenliğini iyileştirep yetkisiz tersine mühendislik, yanıltma veya diğer saldırıları önlemeye yardımcı olabilir:

- [Dotfuscator](dotfuscator/index.md) ücretsizdir ve yetkisiz hata ayıklama gibi .NET derlemelerini tersine mühendislik ve yetkisiz kullanıma karşı korumaya yardımcı olur.
- [Güçlü ad imzalama](managing-assembly-and-manifest-signing.md) , yazılım bileşenlerini benzersiz şekilde tanımlamak ve ad yanıltmasını engellemek için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET 'te güvenlik](/dotnet/standard/security/index)
- [Azure güvenliği](/azure/security/)
- [Windows 10 Mobile Güvenlik Kılavuzu](/windows/security/threat-protection/windows-10-mobile-security-guide)
- [Apache Cordova platformu güvenlik özellikleri](/visualstudio/cross-platform/tools-for-cordova/security/best-practices?view=toolsforcordova-2017)
- [ASP.NET Core güvenliği](/aspnet/core/security/?view=aspnetcore-2.1)
- [Windows Forms güvenliği](/dotnet/framework/winforms/windows-forms-security)