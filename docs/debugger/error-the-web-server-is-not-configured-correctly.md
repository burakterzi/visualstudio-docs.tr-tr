---
title: 'Hata: Web sunucusu doğru yapılandırılmamış | Microsoft Docs'
ms.date: 09/20/2017
ms.topic: troubleshooting
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be5db0a08a287e2611c29396e96e72719b5106a7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736924"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Hata: Web sunucusu doğru yapılandırılmamış

Sorunu çözmek için buradaki adımları ayrıntılandırdıktan sonra ve hata ayıklamayı yeniden denemeden önce, IIS 'yi de sıfırlamanız gerekebilir. Bunu, bir yönetici komut istemi açıp `iisreset`yazarak yapabilirsiniz.

Bu sorunu çözmek için şu adımları uygulayın:

1. Sunucuda barındırılan Web uygulaması bir yayın derlemesi olarak yapılandırılmışsa, hata ayıklama derlemesi olarak yeniden yayımlayın ve Web. config dosyasının derleme öğesinde `debug=true` içerdiğini doğrulayın. IIS 'i sıfırlayın ve yeniden deneyin.

    Örneğin, bir yayın derlemesi için bir yayımlama profili kullanıyorsanız, bunu hata ayıklama ve yeniden yayımlama için değiştirin. Aksi halde, yayımlarken hata ayıklama özniteliği `false` olarak ayarlanır.

2. ISS Fiziksel yolun doğru olduğundan emin olun. IIS 'de bu ayarı, **fiziksel ayarlar > fiziksel yol** (veya daha eski IIS sürümlerindeki **Gelişmiş ayarlar** ) içinde bulabilirsiniz.

    Web uygulaması farklı bir makineye kopyalanmışsa, el ile yeniden adlandırılırsa veya taşındığında fiziksel yol yanlış olabilir. IIS 'i sıfırlayın ve yeniden deneyin.

3. Visual Studio 'da yerel olarak hata ayıklaması yapıyorsanız, özelliklerde doğru sunucunun seçildiğini doğrulayın. (Proje türüne bağlı olarak **hata ayıklama >** **Web > sunucuları veya özellikleri > Özellikler** açın. Web Forms bir proje için, özellik sayfaları ' nı açın **> Başlat seçenekler > sunucu**).

    IIS gibi bir dış (özel) sunucu kullanıyorsanız, URL 'nin doğru olması gerekir. Aksi takdirde IIS Express seçin ve yeniden deneyin.

4. ISS Sunucuda doğru ASP.NET sürümünün yüklü olduğundan emin olun.

    IIS 'de ve Visual Studio projenizde eşleşmeyen ASP.NET sürümleri bu soruna neden olabilir. Web. config 'de Framework sürümünü ayarlamanız gerekebilir. IIS 'de ASP.NET yüklemek için [Web Platformu Yükleyicisi (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)kullanın. Ayrıca bkz. [ASP.NET 3,5 ve ASP.NET 4,5 kullanarak ııs 8,0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) veya ASP.NET Core, [Windows üzerinde IIS ile barındırma](https://docs.asp.net/en/latest/publishing/iis.html).

4. IIS 'deki `maxConnection` sınırı çok düşükse ve çok fazla bağlantınız varsa, [bağlantı sınırını artırmanız](/iis/configuration/system.applicationhost/sites/sitedefaults/limits)gerekebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzak IIS Bilgisayarında Uzaktan ASP.NET ile Hata Ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)