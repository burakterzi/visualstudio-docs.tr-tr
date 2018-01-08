---
title: "Visual Studio 2017 değiştirme | Microsoft Docs"
description: "Visual Studio, adım adım değiştirme hakkında bilgi edinin."
ms.custom: H1Hack27Feb2017
ms.date: 11/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8278b138e8cf7a8780ad83d591a823fdb85f2b08
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="modify-visual-studio-2017-by-adding-or-removing-workloads-and-components"></a>Visual Studio 2017 ekleyerek veya kaldırarak iş yükleri ve bileşenleri değiştirme
Biz yalnızca yaptığınız daha kolay gerçekleştirmek istediğiniz görevlerin eşleştirmek için Visual Studio kişiselleştirmek için de, Visual Studio, çok özelleştirmek daha kolay yaptık. Bunu yapmak için Denetim Masası'nda arama fazla; Bunun yerine, yeni Visual Studio Yükleyicisi'ni başlatın ve istediğiniz değişiklikleri yapın.

İşte nasıl.  

## <a name="modify-workloads"></a>İş yüklerini değiştirme  
 İş yükleri programlama dili veya kullanmakta olduğunuz platform için gerek duyduğunuz özellikler içerir. Böylece yapmak istediğiniz zaman yapmak istediğiniz iş destekleyen Visual Studio değiştirmek için iş yüklerini kullanın.  

>[!IMPORTANT]
>Yüklemek, güncelleştirme veya Visual Studio değiştirmek için yönetim izinlerine sahip bir hesapla oturum açmalısınız. Daha fazla bilgi için bkz: [kullanıcı izinleri ve Visual Studio](../ide/user-permissions-and-visual-studio.md).

1.  Visual Studio yükleyicisi bilgisayarınızda bulun.  

     Örneğin, Windows 10 Anniversary güncelleştirme çalıştıran bir bilgisayarda seçin **Başlat**ve ardından harfi kaydırma **V**, olarak listelenen burada **Visual Studio yükleyicisi**.  

     ![Visual Studio yükleyicisi](media/vs2017-locate-the-visual-studio-installer.PNG "Microsoft Visual Studio yükleyicisi bulun")

     >[!NOTE]
     Bazı bilgisayarlarda, Visual Studio yükleyicisi harf altında listelenebilir **"M"** olarak **Microsoft Visual Studio yükleyicisi**.<br/><br/> Alternatif olarak, Visual Studio yükleyicisi şu konumda bulabilirsiniz:`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

2.  ' I tıklatın veya yükleyiciyi başlatmak için'a dokunun ve ardından **Değiştir**.  

     ![Başlatma veya Visual Studio değiştirmek](media/vs2017-modify.PNG "Visual Studio 2017 değiştirme")  

3.  Gelen **iş yükleri** ekranında, seçin veya yüklemek veya kaldırmak istediğiniz iş yüklerini seçimini kaldırın.  

    ![Visual Studio 2017 Kurulum iletişim](media/vs2017-modify-workloads.PNG "bir iş yükü Visual Studio 2017 seçin")

4. ' A tıklayın veya dokunun **Değiştir** yeniden.  

5. Yeni iş yükleri ve bileşenleri yüklendikten sonra tıklatın **başlatma**.

## <a name="modify-individual-components"></a>Bileşenleri tek tek değiştirme

Kullanışlı iş yükleri özelliği kullanmak Visual Studio yüklemenizi özelleştirmek için seçin istemiyorsanız, **bileşenleri tek tek** seçeneği Visual Studio Yükleyicisi'nden, neleri istediğiniz ve ardından izleyin seçmek ister.  

## <a name="get-support"></a>Destek alma
Bazı durumlarda, şeyler yanlış gidebilirsiniz. Visual Studio yüklemenizin başarısız olursa bkz [sorun giderme Visual Studio 2017 yükleme ve yükseltme sorunlarını](troubleshooting-installation-issues.md) sayfası. Sorun giderme adımlarını hiçbiri yardımcı, bize yükleme Yardımı (yalnızca İngilizce) için canlı sohbet tarafından başvurabilirsiniz. Ayrıntılar için bkz [Visual Studio destek sayfası](https://www.visualstudio.com/vs/support/#talktous).

Birkaç diğer destek seçenekleri şunlardır:
* Ürün sorunları bize bildirebilirsiniz [bir sorun bildirmek](../ide/how-to-report-a-problem-with-visual-studio-2017.md) hem Visual Studio Yükleyicisi ve Visual Studio IDE görünür aracı.
* Üzerinde bir ürün önerisi bizimle paylaşın [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Ürün sorunları izleyebilir [Visual Studio Geliştirici topluluğu](https://developercommunity.visualstudio.com/), soru sorun ve yanıtlarını bulun.
* ABD ve diğer Visual Studio geliştiriciler aracılığıyla devreye bizim [Gitter topluluk Visual Studio konuşmada](https://gitter.im/Microsoft/VisualStudio).  (Bu seçenek gerektiren bir [GitHub](https://github.com/) hesabı.)

## <a name="see-also"></a>Ayrıca bkz.
* [Visual Studio 2017 yükleyin](install-visual-studio.md)
* [Visual Studio 2017 güncelleştir](update-visual-studio.md)
* [Visual Studio 2017 kaldırma](uninstall-visual-studio.md)