---
title: Test denetleyicileri ve test aracıları için bağlantı noktalarını yapılandırma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- firewalls, configuring for test agents
- firewalls, configuring for test controllers
- test agents, firewalls
- test controllers, firewalls
- agents, firewalls
- controllers, firewalls
ms.assetid: 211edbd7-9fe4-4251-ba85-8bec4363261b
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f29edf1582b709931e393faa0de5a1542a0ee662
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665200"
---
# <a name="configure-ports-for-test-controllers-and-test-agents"></a>Test denetleyicileri ve test aracıları için bağlantı noktalarını yapılandırma

Test denetleyicisi, test aracısı ve istemci tarafından kullanılan varsayılan gelen bağlantı noktalarını değiştirebilirsiniz. Bu, test denetleyicisini, test aracısını veya istemciyi bağlantı noktası ayarlarıyla çakışan diğer yazılımlarla birlikte kullanmaya çalışıyorsanız gerekli olabilir. Bağlantı noktalarını değiştirme işlemi, test denetleyicisi ve istemci arasındaki güvenlik duvarı kısıtlamasından kaynaklanır. Bu durumda, test denetleyicisinin sonuçları istemciye gönderebilmesi için bağlantı noktasını bir güvenlik duvarı için etkinleştirmeye uyum sağlayacak şekilde el ile yapılandırmak isteyebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aşağıdaki çizimde, test denetleyicisi, test aracısı ve istemci arasındaki bağlantı noktaları gösterilmektedir. Gelen ve giden bağlantılar için hangi bağlantı noktalarının kullanıldığını ve bu bağlantı noktalarında kullanılan güvenlik kısıtlamalarını özetler.

![Test denetleyicisi ve test Aracısı bağlantı noktaları ve güvenliği](../test/media/test-controller-agent-firewall.png)

## <a name="incoming-connections"></a>Gelen bağlantılar

Test denetleyicisi tarafından kullanılan varsayılan bağlantı noktası 6901 ' dir ve test aracısının varsayılan bağlantı noktası 6910 ' dir. İstemci, test denetleyicisinden test sonuçlarını almak için kullanılan varsayılan olarak rastgele bir bağlantı noktası kullanır. Tüm gelen bağlantılarda, test denetleyicisi çağıran tarafın kimliğini doğrular ve belirli bir güvenlik grubuna ait olduğunu doğrular.

- **Test denetleyicisi** Gelen bağlantılar, TCP bağlantı noktası 6901 ' dir. Gerekirse, gelen bağlantı noktasını yapılandırabilirsiniz. Daha fazla bilgi için bkz. [gelen bağlantı noktalarını yapılandırma](#configure-the-incoming-ports).

    Test denetleyicisinin Test aracılarına ve istemciye giden bağlantıları yapabilmesi gerekir.

    > [!NOTE]
    > Test denetleyicisine gelen **dosya ve yazıcı paylaşımı** bağlantısı açık olmalıdır.

- **Test Aracısı** Gelen bağlantılar, TCP bağlantı noktası 6910 ' dir. Gerekirse, gelen bağlantı noktasını yapılandırabilirsiniz. Daha fazla bilgi için bkz. [gelen bağlantı noktalarını yapılandırma](#configure-the-incoming-ports).

   Test aracısının, test denetleyicisi ile giden bağlantı kurabilmesi gerekir.

- **İstemci** Varsayılan olarak, gelen bağlantılar için rastgele bir TCP bağlantı noktası kullanılır. Gerekirse, gelen bağlantı noktasını yapılandırabilirsiniz. Daha fazla bilgi için bkz. [gelen bağlantı noktalarını yapılandırma](#configure-the-incoming-ports).

   Test denetleyicisi istemciye ilk kez bağlanmayı denediğinde güvenlik duvarı bildirimleri alabilirsiniz.

   Windows Server 2008 ' de güvenlik duvarı bildirimleri varsayılan olarak devre dışıdır ve Istemci programları için (*devenv. exe*, *MSTest. exe*, *MLD. exe*) güvenlik duvarı özel durumlarını, gelen bağlantıları kabul edecek şekilde el ile eklemeniz gerekir.

## <a name="outgoing-connections"></a>Giden bağlantılar

Rastgele TCP bağlantı noktaları tüm giden bağlantılar için kullanılır.

- **Test denetleyicisi** Test denetleyicisinin aracılara ve Istemciye giden bağlantıları yapabilmesi gerekir.

- **Test Aracısı** Test aracısının denetleyiciye giden bağlantı kurabilmesi gerekir.

- **İstemci** İstemcinin denetleyiciye giden bağlantı kurabilmesi gerekir.

## <a name="configure-the-incoming-ports"></a>Gelen bağlantı noktalarını yapılandırma

Bir test denetleyicisi ve test aracısının bağlantı noktalarını yapılandırmak için bu yönergeleri izleyin.

- **Denetleyici hizmeti** *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config* dosyasını düzenleyerek bağlantı noktasının değerini değiştirin:

    ```xml
    <appSettings>
      <add key="ControllerServicePort" value="6901"/>
    </appSettings>
    ```

- **Aracı hizmeti** *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTAgentService.exe.config* dosyasını düzenleyerek bağlantı noktasını değiştirin:

    ```xml
    <appSettings>
      <add key="AgentServicePort" value="6910"/>
    </appSettings>
    ```

- **İstemci** Aşağıdaki kayıt defteri (**DWORD**) değerlerini eklemek için kayıt defteri düzenleyicisini kullanın. İstemci, test denetleyicisinden veri almak için belirtilen aralıktaki bağlantı noktalarından birini kullanacaktır:

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeStart**

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeEnd**

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)