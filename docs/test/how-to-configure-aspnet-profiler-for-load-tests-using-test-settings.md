---
title: Yük testleri için ASP.NET Profiler 'ı yapılandırma
ms.date: 10/13/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, ASP.NET
ms.assetid: 6832fe39-04d5-4d94-8a18-3e2730bad423
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1de7e890c60374730e297296116cb56828fa256b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643752"
---
# <a name="how-to-configure-aspnet-profiler-for-load-tests-using-test-settings-in-visual-studio"></a>Nasıl yapılır: Visual Studio 'da test ayarlarını kullanarak yük testleri için ASP.NET Profiler 'ı yapılandırma

ASP.NET Profiler bilgilerini toplamak için ASP.NET profil oluşturucu tanılama veri bağdaştırıcısını kullanabilirsiniz. Bu tanılama veri bağdaştırıcısı ASP.NET uygulamaları için performans verilerini toplar.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Bu tanılama veri bağdaştırıcısı, Microsoft Test Yöneticisi kullanılarak çalıştırılan testler için kullanılamaz. ASP.NET profil oluşturucu tanılama bağdaştırıcısını yalnızca, Visual Studio Enterprise gerektiren Web sitelerini kullanarak yük testleriyle kullanabilirsiniz.

ASP.NET Profiler tanılama veri bağdaştırıcısı, bir yük testi çalıştırdığınızda uygulama katmanından ASP.NET Profiler verileri toplamanızı sağlar. Uzun yük testleri için profil oluşturucuyu çalıştırmamanız gerekir, örneğin, bir saatten uzun süren yük testleri. Bunun nedeni profil oluşturucu dosyasının yüzlerce megabayt olması olabilir. Bunun yerine, ASP.NET profil oluşturucuyu kullanarak daha kısa yük testleri çalıştırın, bu da size performans sorunlarının derin tanılaması avantajlarından faydalanacaktır.

> [!NOTE]
> ASP.NET Profiler tanılama veri bağdaştırıcısı Internet Information Services (IIS) işlemini profillerdir. Bu nedenle, bir geliştirme Web sunucusuna karşı çalışmaz. Yük testinizde web sitesinin profilini almak için, IIS 'nin çalıştığı makineye bir test aracısı yüklemeniz gerekir. Test aracısı yük oluşturmaz, ancak yalnızca koleksiyon için bir aracı olacaktır. Daha fazla bilgi için bkz. [test aracılarını yükleyip yapılandırma](../test/lab-management/install-configure-test-agents.md).

Daha fazla bilgi için bkz. [nasıl yapılır: dağıtılmış yük testi için test ayarı oluşturma](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md).

## <a name="configure-the-aspnet-profiler-for-your-test-settings"></a>Test ayarlarınız için ASP.NET profil oluşturucuyu yapılandırın

Bu yordamdaki adımları gerçekleştirmeden önce, Visual Studio 'dan test ayarlarınızı açmanız ve **veri ve tanılama** sayfasını seçmeniz gerekir.

1. ASP.NET Profiler verilerini toplamak için kullanılacak rolü seçin.

    > [!WARNING]
    > Bu rol bir Web sunucusu olmalıdır.

2. ASP.NET profil oluşturma verilerini toplamayı etkinleştirmek için **ASP.net Profiler** ' ı seçin ve ardından **Yapılandır**' ı seçin.

     ASP.NET profil oluşturma veri toplamayı yapılandırmak için iletişim kutusu görüntülenir.

3. **Profil Oluşturucu örnekleme aralığı**içinde, ASP.NET profil oluşturma örnekleri almak arasında kaç tane DURDURULMAYAN CPU saati döngüsünü belirten bir değer yazın.

4. Katman etkileşimi profil oluşturmayı etkinleştirmek için **katman etkileşim profilini etkinleştir**' i seçin.

     Katman etkileşimi profili oluşturma, her bir yapıt için Web sunucusuna gönderilen isteklerin sayısını (örneğin, *MyPage. aspx* veya *CompanyLogo. gif*) ve her bir isteğe hizmet vermek için geçen süreyi sayar. Ayrıca, katman etkileşim profili oluşturma, sayfa isteğinin bir parçası olarak hangi ADO.NET bağlantılarının kullanıldığını ve bu isteğin hizmet verme işleminin bir parçası olarak kaç tane sorgu ve saklı yordam çağrısı yapıldığını toplar.

     İki farklı zamanlama bilgisi kümesi toplanır:

    - Her Web isteğine hizmet vermek için zamanlama bilgileri (en küçük, en fazla, ortalama ve toplam).

    - Her sorguyu yürütmenin zamanlama bilgileri (en az, en fazla, ortalama ve toplam).

Test ayarınızda yapılandırılmış ASP.NET profil oluşturucu tanılama veri bağdaştırıcısı ile, artık ASP.NET Web uygulamanızda ASP.NET profil oluşturma verileri toplayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Test ayarlarını kullanarak tanılama bilgilerini topla](../test/collect-diagnostic-information-using-test-settings.md)
- [Nasıl yapılır: dağıtılmış yük testi için test ayarı oluşturma](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)