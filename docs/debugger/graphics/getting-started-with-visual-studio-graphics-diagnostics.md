---
title: Grafik tanılama 'yı kullanmaya başlama | Microsoft Docs
ms.custom: seodec18
ms.date: 05/26/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb651d9b35dd4531f4d14e169ab6f04376d4dfff
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735706"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Visual Studio Grafik Tanılama’ya Başlarken
Bu bölümde Grafik Tanılama ilk kez kullanmaya hazırlarsınız, sonra Direct3D uygulamasından çerçeveler yakalayıp grafik Çözümleyicisi 'nde inceleyebilirsiniz.

## <a name="requirements"></a>Gereksinimler
 Visual Studio 'da Grafik Tanılama kullanmak için Visual Studio Enterprise, Visual Studio Professional veya Visual Studio Community kullanmanız gerekir.  Visual Studio Code dahil diğer sürümler bu özelliği içermez.

 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]

### <a name="windows-10-prerequisites"></a>Windows 10 önkoşulları
 İsteğe bağlı Windows özelliği *grafik araçları* , Windows 10 ' da grafik Tanılama için gereken yakalama ve kayıttan yürütme altyapısını sağlar.

 Grafik araçları 'nı yükleme hakkında bilgi için bkz. [Windows 10 Için grafik araçları 'Nı yükleme](#InstallGraphicsTools).

## <a name="InstallGraphicsTools"></a>Windows 10 için grafik araçları 'nı yükler
 Windows 10 ' da, Grafik Tanılama altyapısı, *grafik araçları*adlı Windows 'un isteğe bağlı bir özelliği tarafından sağlanır. Yakalanan uygulamanın Windows 'un önceki bir sürümünü veya hangi Direct3D sürümünü kullandığını bağımsız olarak Windows 10 ' da grafik bilgilerini yakalamak ve oynatmak için bu özellik gereklidir. Grafik araçları özelliğini bir süre önce yüklemeyi seçebilirsiniz; Aksi takdirde, Visual Studio 'dan Grafik Tanılama oturumu ilk kez başlattığınızda isteğe bağlı olarak yüklenir.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Windows 10 için grafik araçları 'nı yüklemek için

1. Ara bölümünde **uygulamalar ve Özellikler** yazın ve ardından **uygulamalar & özellikleri** ayarları ' nı açın.

2. **Uygulamalar & özellikleri** iletişim kutusunun sağ tarafında, **Isteğe bağlı özellikleri yönet** ' i ( **uygulamalar & Özellikler**altında) seçin.

   **İsteğe bağlı özellikleri yönet** iletişim kutusu görüntülenir.

3. **İsteğe bağlı özellikleri yönet** iletişim kutusunda **Özellik Ekle**' yi seçin. Yükleyebileceğiniz isteğe bağlı özelliklerin bir listesi görüntülenir.

4. Özellikler listesinden **grafik araçları** ' nı seçin ve ardından **Install**' ı seçin.

   Grafik araçları özelliği, Windows 10 SDK 'Yı yüklediğinizde de otomatik olarak yüklenir.

> [!TIP]
> Windows 10 ' un isteğe bağlı grafik araçları özelliği, geliştiricilerin geliştirici, test ve tanılama senaryolarında geliştirme, test ve tanılama senaryolarındakullanılabilecek, geliştirici Araçlar yüklü değil. Daha fazla bilgi için, bkz. [komut satırı yakalama aracı](command-line-capture-tool.md) konusu.

## <a name="using-graphics-diagnostics-for-the-first-time"></a>Grafik Tanılama ilk kez kullanma
 Artık ihtiyacınız olan her şeye sahip olduğunuza göre Grafik Tanılama kullanmaya başlamaya hazırsınız. Bu adımları izlemeniz yeterlidir.

### <a name="1---create-a-direct3d-app"></a>1-Direct3D uygulaması oluşturma
 İle Grafik Tanılama araştırmak için kendi Direct3D uygulamanız zaten varsa harika! Aksi takdirde, aşağıdakilerden birini kullanın:

- Windows 10 için **DirectX 11 uygulaması (Evrensel Windows)** veya **DirectX 12 uygulaması (Evrensel Windows)** proje şablonları.
- Windows 10 için [Direct3D 12 UAP örneği](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) .

  Uygulamasına geçmeden önce uygulamayı derlediğinizden emin olun.

### <a name="2---start-a-graphics-diagnostics-session"></a>2-Grafik Tanılama oturumu başlatma
 Şimdi ilk grafik tanılama oturumunuzu başlatmaya hazırsınız. Visual Studio 'da, ana menüdeki **Hata Ayıkla, grafikler, grafik hata ayıklamayı Başlat**' ı seçin veya **alt + F5**tuşlarına basın. Bu, uygulamanızı Grafik Tanılama altında başlatır ve Tanılama oturumu pencerelerini Visual Studio 'da görüntüler.

> [!IMPORTANT]
> Uygulamanızı Windows 10 ' da çalıştırıyorsanız ve isteğe bağlı grafik araçları özelliğini henüz yüklemediyseniz, bunu şimdi yapmanız istenir. Windows 10 ' da Grafik Tanılama kullanabilmeniz için önce bu uygulamayı yüklemelisiniz.

### <a name="3---capture-frames"></a>3-çerçeveleri yakala
 Uygulamanız başladıktan hemen sonra çerçeveler yakalamaya hazırsınız.

#### <a name="to-capture-single-frames"></a>Tek çerçeveleri yakalamak için

- Visual Studio 'da grafik araç çubuğundan veya Tanılama oturumu penceresinden **kare yakala** düğmesini seçin. Ya da uygulamanız odağa sahipse, klavyenizde **PRINT Screen** tuşuna basmanız yeterlidir.

#### <a name="to-capture-a-sequence-of-frames"></a>Çerçeve dizisini yakalamak için

- Visual Studio 'da, Tanılama oturumu penceresinde, çerçeveleri sırayla yakalamak istediğiniz çerçeve sayısına **yakalamaya** göre ayarlayın ve ardından tek çerçeveleri yakalamak için yukarıda açıklanan yöntemlerden herhangi birini kullanarak sırayı yakalayın.

   Tek kareleri yeniden yakalamak için **kareleri yakalamaya** *1*olarak ayarlayın.

  Çerçeveleri yakalamayı tamamladığınızda uygulamadan çıkmak veya grafik araç çubuğundan veya Tanılama oturumu penceresinden **Durdur** düğmesini seçmeniz yeterlidir.

### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4-grafik çözümleyici 'de yakalanan çerçeveleri İnceleme
 Şimdi, az önce yakaladığınız çerçeveleri incelemek için hazırsınız. Bir çerçeveyi çözümlemeye başlamak için, Tanılama oturumu penceresinden incelemek istediğiniz çerçevenin kare numarasını seçin. Bu, uygulamanızın işleme sorunlarını izlemek için Direct3D 'yi nasıl kullandığını incelemek için Grafik Tanılama araçlarını kullanabileceğiniz veya performansını anlamak için **Çerçeve Analizi** aracını kullanmanın **grafik Çözümleyicisi**' nde çerçeveyi açar.

 Tanılama oturumu penceresinden yanlış çerçeveyi seçtiyseniz veya farklı bir çerçeveyi incelemek istiyorsanız grafik çözümleyicisinden yeni bir tane seçebilirsiniz. Grafik günlüğü penceresinin **Işleme hedefi** sekmesinde, işleme hedefi görüntüsü altında, **çerçeve listesini** genişletin ve ardından incelemek üzere farklı bir çerçeve seçin.

 Grafik Çözümleyicisi araçlarının birlikte nasıl kullanılacağı hakkında daha fazla bilgi edinmek için [örneklere](graphics-diagnostics-examples.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Direct3D 12 grafik](/windows/desktop/direct3d12/direct3d-12-graphics)