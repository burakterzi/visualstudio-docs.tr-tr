---
title: Razor Web uygulamaları oluşturma
description: Mac için Visual Studio ASP.NET Core uygulamalarda Razor desteği hakkında bilgi sağlar.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: fe9ef921ccfc42b77bd08925805aeac6f4aec777
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73715882"
---
# <a name="create-razor-web-apps"></a>Razor Web uygulamaları oluşturma

Bu kılavuzda, ilk Razor Web uygulamanızı oluşturmaya yönelik bir giriş sunulmaktadır. Daha ayrıntılı rehberlik için bkz. [ASP.NET Core Razor Pages giriş](/aspnet/core/razor-pages/index).

Mac için Visual Studio, IntelliSense ve *. cshtml* dosyalarında sözdizimi vurgulama dahil olmak üzere Razor düzenlemesi için destek sağlar. Mac 8.3 için Visual Studio 2019 ' deki yenilikler + bir Razor dosyası içinde içerik algılayan IntelliSense 'in, bir belgede Şu anda düzenlemekte olduğunuz dille eşleşen bir IntelliSense elde etme olanağıdır.

![Mac için Visual Studio 'de Razor düzenlemesi](media/razor-2019.png)

## <a name="creating-a-new-razor-project"></a>Yeni bir Razor projesi oluşturma

1. Yeni bir proje oluşturmak için hoş geldiniz ekranında **Yeni** ' yi seçin:

   ![Yeni Mac için Visual Studio proje](media/razor-new.png)
1. **Yeni proje** iletişim kutusunda, **.NET Core** > **App** > **Web uygulaması** ' na gidin ve ileri ' **yi**seçin:

   ![Razor proje şablonu](media/razor-new-project1.png)
1. .NET Core hedef çatısını seçin (sürüm 2,2 veya üzeri önerilir) ve ardından **İleri**' yi seçin. Projeniz için bir ad seçin ve gerekirse git desteği ekleyin. Projeyi oluşturmak için **Oluştur** ' u seçin.

   ![Razor proje adı](media/razor-new-project2.png)

   Mac için Visual Studio, projenizi kod düzeni penceresinde açar.
1. **Komut + Option + F5**kullanarak projeyi hata ayıklama olmadan çalıştırın.

   Visual Studio [Kestrel](/aspnet/core/fundamentals/servers/kestrel)başlar, `https://localhost:5001`için bir tarayıcı açar ve ilk Razor Web uygulamanızı görüntüler.

   ![Safari 'de Razor Web uygulaması](media/razor-webapp.png)

## <a name="project-anatomy"></a>Proje anatomumu

Razor Web uygulamaları aşağıdaki bileşenleri içerir.

### <a name="pages-folder"></a>Sayfalar klasörü

Bu klasör bir projenin Web sayfalarını, her biri için arka plan kodu içerir:
   - HTML biçimlendirme ve Razor söz dizimi için bir *\*. cshtml* dosyası.
   - Sayfa olaylarını işlemek için arka plan C# kodu için bir *\*. cshtml.cs* dosyası.

Destekleyici dosyalar bir alt çizgiyle başlayan adlara sahiptir. Örneğin, _Layout. cshtml dosyası tüm sayfalarda ortak kullanıcı arabirimi öğelerini yapılandırır. Bu dosya, sayfanın üst kısmındaki gezinti menüsünü ve en alttaki telif hakkı bildirimini ayarlar. Daha fazla bilgi için [ASP.NET Core düzen](/aspnet/core/mvc/views/layout)bölümüne bakın.

### <a name="launch-settings"></a>Başlatma ayarları

*Launchsettings. JSON* dosyası IIS ayarlarını, uygulama URL 'sini ve diğer ilgili ayarları içerir.

### <a name="app-settings"></a>Uygulama ayarları

*AppSettings. JSON* dosyası bağlantı dizeleri gibi yapılandırma verilerini içerir.

Yapılandırma hakkında daha fazla bilgi için [ASP.net Kılavuzu 'Ndaki yapılandırmaya](/aspnet/core/fundamentals/configuration/index)bakın.

### <a name="wwwroot-folder"></a>Wwwroot klasörü

Bu klasör HTML, JavaScript ve CSS dosyaları gibi statik dosyaları içerir. Daha fazla bilgi için [ASP.NET Core Içindeki statik dosyalar](/aspnet/core/fundamentals/static-files)bölümüne bakın.

### <a name="programcs"></a>Program.cs

Bu dosya, program için giriş noktasını içerir. Daha fazla bilgi için bkz. [ASP.NET Core Web Host](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Bu dosya, uygulamanın tanımlama bilgileri için izin gerektirip gerektirmediğini belirtir gibi uygulama davranışını yapılandıran kodu içerir. Daha fazla bilgi için [ASP.NET Core uygulamasında uygulama başlatma](/aspnet/core/fundamentals/startup)bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

Razor Web uygulamaları oluşturmaya yönelik daha kapsamlı bir kılavuz için bkz. [ASP.NET Core Razor Pages giriş](/aspnet/core/razor-pages/index).
