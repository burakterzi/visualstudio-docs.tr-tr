---
title: Yük testi çalışma ayarına bağlam parametreleri ekleme
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, context parameters
- load tests, context parameters
ms.assetid: a8a0b97e-8040-4711-85ab-36548b130ed2
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e630bfccb1741e3b194b6be4c6f8cdb065d8b942
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664854"
---
# <a name="how-to-add-context-parameters-to-a-load-test-run-setting"></a>Nasıl yapılır: yük testi çalışma ayarına bağlam parametreleri ekleme

**Yeni Yük Testi Sihirbazı**kullanarak yük testinizi oluşturduktan sonra, test ihtiyaçlarını ve hedeflerinizi karşılamak üzere senaryolar özelliklerini değiştirmek için **Yük Testi Düzenleyicisi** kullanabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Çalışma ayarları özelliklerinin tam listesi ve açıklamaları için bkz. [Yük testi çalıştırma ayarları özellikleri](../test/load-test-run-settings-properties.md).

Yük Testi Düzenleyicisi kullanarak yük testi çalıştırma ayarında kullanmak için bağlam parametreleri oluşturabilirsiniz. Bağlam parametreleri bir dizeyi parametreleştirietmenize olanak tanır.

Yük testiniz bir bağlam parametresi kullanarak zaten parametreli bir Web sunucusu URL 'SI kullanan bir Web performans testi içerdiğini varsayalım. Web performans testinde kullanılan ile aynı ad değerini kullanan bir yük testi çalıştırma ayarına bağlam parametresi ekleyebilirsiniz. Bu işlem, yük testini çalıştırdığınızda Web performans testini farklı bir sunucuya eşler. Örneğin, yük testiniz URL 'deki Web sunucusunun adı için WebServer1 adlı bir bağlam parametresi kullanan bir Web performans testi içeriyorsa. Daha sonra, WebServer1 adlı yük testi çalışma ayarınız içinde bir bağlam parametresi belirtirseniz, yük testi yük testi çalıştırma ayarında atadığınız bağlam parametresini kullanır. Netleştirmek için, yük testinde Web performans testi, yük testinde bir bağlam parametresi olarak aynı bağlam parametresi adını kullanıyorsa, yük testindeki bağlam parametresi, Web performans testinde kullanılan bağlam parametresini geçersiz kılar.

> [!WARNING]
> Bir çalışma ayarında bağlam parametreleri kullandığınızda bir Web performans testinin bağlam parametresini istenmeden geçersiz kılmamaya dikkat edin. Bunu bilerek yapmadığınız takdirde aynı bağlam parametresi adlarını kullanmaktan kaçının.

WebServer1 context parametresinin değerini `http://CorporateStagingWebServer` atarsanız, yük testi boyunca `WebServer1` kullanabilirsiniz ve bu sayede değeri dilediğiniz zaman kolayca farklı bir Web sunucusuna değiştirebilirsiniz.

Ayrıca, farklı yük testi çalışma ayarlarında aynı adı kullanarak bir bağlam parametresine farklı değerler atayarak, farklı ortamları kullanarak yük testini çalıştırabilirsiniz:

- Kurumsal hazırlama Web sunucusu çalıştırma ayarı: `WebServer1=http://CorporateStagingWebServer` adlı bağlam parametresi

- Kurumsal üretim Web sunucusu çalıştırma ayarı: `WebServer1=http://CorporateProductionWebServer` adlı bağlam parametresi

  **Çalıştırma ayarını komut satırından değiştirme**

  Bağlam parametresi stratejisinden faydalanmak için komut satırından farklı çalışma ayarları kullanmak istiyorsanız aşağıdaki komutları kullanın:

  **Test. UseRunSetting = CorporateStagingWebServer ayarla**

  '

  **MSTest/testcontainer: LoadTest1. LoadTest**

## <a name="to-add-a-context-parameter-to-a-run-setting"></a>Bir çalıştırma ayarına bağlam parametresi eklemek için

1. Bir yük testi açın.

2. Yük Testi Düzenleyicisi yük testi ağacındaki **çalışma ayarları** klasörünü genişletin.

3. Bağlam parametresi eklemek istediğiniz özel çalıştırma ayarına sağ tıklayın ve sonra **Bağlam parametresi Ekle**' yi seçin.

     Yük testi ağacındaki **çalışma ayarları** klasöründeki **Bağlam parametreleri** klasörüne yeni bir bağlam parametresi eklenir.

     veya

     Çalıştırma ayarı zaten bir **Bağlam parametreleri** klasörü içeriyorsa, sağ tıklayıp **Bağlam parametresi Ekle**' yi seçebilirsiniz.

4. **Özellikler** penceresinde, **ad** için değeri uygun şekilde değiştirin (örneğin, WebServer1). **Özellikler** penceresinde, **değerini** kullanmak istediğiniz parametreye değiştirin (örneğin, `http://CorporateStagingWebServer`).

5. Seçim 3 ile 5 arasındaki adımları yineleyin ve **değer** özelliği için farklı bir dize kullanın (örneğin, `http://CorporateProductionWebServer`).

6. Hangi çalıştırma ayarlarının etkin olmasını istediğinizi seçin. Çalıştır ayarları ' nın kısayol menüsünü açın ve **etkin olarak ayarla**' yı seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandır](../test/configure-load-test-run-settings.md)