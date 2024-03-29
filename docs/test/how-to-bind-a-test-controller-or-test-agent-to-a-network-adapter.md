---
title: Bir test denetleyicisini veya test aracısını ağ bağdaştırıcısına bağlama
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- controllers, netwrok adapter
- agents, configuring
- agents, network adapter
- controllers, configuring
ms.assetid: 7eb9290a-f9f6-4e41-9caa-796fcfaf0610
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b0dc70169deb8d09fed45bcb921c783765e87c0e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643775"
---
# <a name="how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter"></a>Nasıl yapılır: bir test denetleyicisini veya test aracısını ağ bağdaştırıcısına bağlama

Test denetleyicisi veya test aracısı yazılımının yüklü olduğu bir bilgisayarda birden çok ağ bağdaştırıcısı varsa, bu test denetleyicisini veya test aracısını tanımlamak için bilgisayarın adı yerine IP adresini belirtmeniz gerekir.

> [!WARNING]
> Bir test aracısı ayarlamaya çalıştığınızda şu hatayı alabilirsiniz:
>
> **Hata 8110. Belirtilen denetleyici bilgisayarına bağlanılamıyor veya denetleyici nesnesine erişilemiyor**
>
> Bu hata, test denetleyicisinin birden fazla ağ bağdaştırıcısı olan bir bilgisayara yüklenmesi nedeniyle oluşabilir. Aracıları başarıyla yüklemek de mümkündür ve bir test çalıştırmayı deneene kadar bu sorunu görmez.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="bind-a-test-controller-to-a-specific-network-adapter"></a>Belirli bir ağ bağdaştırıcısına bir test denetleyicisi bağlama

### <a name="to-obtain-the-ip-addresses-of-the-network-adapters"></a>Ağ bağdaştırıcılarının IP adreslerini almak için

1. Microsoft Windows 'da **Başlat**' ı seçin, **aramaya başla** kutusuna tıklayın, **cmd**yazın ve **ENTER**' a tıklayın.

2. **İpconfig/all**yazın.

     Ağ bağdaştırıcılarınız için IP adresleri görüntülenir. Denetleyicinizi bağlamak istediğiniz ağ bağdaştırıcısının IP adresini kaydedin.

### <a name="to-bind-a-network-adapter-to-a-test-controller"></a>Bir ağ bağdaştırıcısını bir test denetleyicisine bağlamak için

1. Microsoft Windows 'da **Başlat**' ı seçin, **aramaya başla** kutusunda, **Services. msc**yazın ve ardından **ENTER**' u seçin.

     **Hizmetler** iletişim kutusu görüntülenir.

2. Sonuçlar bölmesinde, **ad** sütununun altında, **Visual Studio test denetleyicisi** hizmeti ' ne sağ tıklayın ve ardından **Durdur**' u seçin.

     veya

     Yükseltilmiş bir komut istemi açın ve aşağıdaki komutu bir komutta çalıştırın:

     `net stop vsttcontroller`

3. *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017 \\ \<edition > \Common7\IDE*konumunda bulunan *QTCcontroller. exe. config* XML yapılandırma dosyasını açın.

4. `<appSettings>` etiketini bulun.

    ```xml
    <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentConnectionTimeoutInSeconds" value="120"/>
      <add key="AgentSyncTimeoutInSeconds" value="300"/>
      <add key="ControllerServicePort" value="6901"/>
      <add key="ControllerUsersGroup" value="TeamTestControllerUsers"/>
      <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins"/>
      <add key="CreateTraceListener" value="no"/>
    </appSettings>
    ```

5. @No__t_1 bölümünde kullanılacak ağ bağdaştırıcısını belirtmek için `BindTo` anahtarını ekleyin.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Test denetleyicisi hizmetini başlatın. Bunu yapmak için, komut isteminde aşağıdaki komutu çalıştırın:

    `net start vsttcontroller`

    > [!WARNING]
    > Test aracısını denetleyiciye bağlamak için test aracısı yüklemesini yeniden çalıştırmanız gerekir. Bu kez, denetleyici adı yerine denetleyicinin IP adresini belirtin.

     Bu, denetleyici, aracı hizmeti ve Aracı işlemi için geçerlidir. Birden çok ağ bağdaştırıcısına sahip bir bilgisayarda çalışan her işlem için `BindTo` özelliği ayarlanmalıdır. @No__t_0 özelliğini ayarlama yordamı, test denetleyicisi için bu konuda daha önce belirtildiği gibi, üç işlem için de aynıdır.

### <a name="to-bind-a-network-interface-card-to-a-test-agent"></a>Bir ağ arabirimi kartını bir test aracısına bağlamak için

1. Microsoft Windows 'da **Başlat**' ı seçin, **aramaya başla** kutusunda, **Services. msc**yazın ve ardından **ENTER**' u seçin.

    **Hizmetler** iletişim kutusu görüntülenir.

2. Sonuçlar bölmesinde, **ad** sütununun altında, **Visual Studio Test Aracısı** hizmetine sağ tıklayın ve ardından **Durdur**' u seçin.

     veya

     Yükseltilmiş bir komut istemi açın ve aşağıdaki komutu bir komutta çalıştırın:

     **net stop vsttagent**

3. *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017 \\ \<edition > \Common7\IDE*konumunda bulunan *QTAgentService. exe. config* XML yapılandırma dosyasını açın.

4. `<appSettings>` etiketini bulun.

    ```xml
    <appSettings>
      <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentServicePort" value="6910"/>
      <add key="ControllerConnectionPeriodInSeconds" value="30"/>
      <add key="StopTestRunCallTimeoutInSeconds" value="120"/>
      <add key="CreateTraceListener" value="no"/>
      <add key="GetCollectorDataTimeout" value="300"/>
    </appSettings>  </appSettings>
    ```

5. @No__t_1 bölümünde kullanılacak ağ bağdaştırıcısını belirtmek için `BindTo` anahtarını ekleyin.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Test Aracısı hizmetini başlatın. Bunu yapmak için, komut isteminde aşağıdaki komutu çalıştırın:

    `net start vsttagent`

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
- [Yük testi günlük ayarlarını değiştir](../test/modify-load-test-logging-settings.md)
- [Test denetleyicileri ve test aracıları için bağlantı noktalarını yapılandırma](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Nasıl yapılır: test denetleyicileri ve test aracıları için zaman aşımı sürelerini belirtme](../test/how-to-specify-timeout-periods-for-test-controllers-and-test-agents.md)