---
title: 'Hata: Web sunucusu doğru yapılandırılmamış | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 875ba87f-c372-4126-8fe3-e33931cf26c0
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f5df9fb04849fce94d1a82748f2fc88f9577667
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297431"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Hata: Web sunucusu doğru yapılandırılmamış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu hatanın olası nedenleri şunlardır:  
  
- Farklı bir makineye kopyalanmış, el ile yeniden adlandırılan veya taşınan bir .NET Web uygulaması hata ayıklaması yapılmaya çalışılıyor.  
  
- Yeterli sayıda IIS bağlantısı yok. Web sitesini IIS 'ye dağıtma hakkında daha fazla bilgi için bkz. [Web sitesi oluşturma](https://docs.microsoft.com/iis/get-started/getting-started-with-iis/create-a-web-site).  
  
- Bir ASP.NET uygulamasında hata ayıklamaya çalışıyorsanız, IIS 7,5 çalıştıran uzak bir bilgisayara dağıtmaya ilişkin yönergeler için IIS 8 veya üzeri çalıştıran uzak bir bilgisayara dağıtma veya [uzak bır ııs 7,5 bilgisayarında uzaktan hata ayıklama ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) ile ilgili yönergeler için bkz. [IIS 'de yayımlama](https://docs.asp.net/en/latest/publishing/iis.html) .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
