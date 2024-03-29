---
title: 'Test alanı 7: paylaşma | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c7b698f3802425a16476931513b6e4fe314d9954
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722375"
---
# <a name="test-area-7-share"></a>Test Alanı 7: Paylaşma
Bu test alanı, **paylaşma** komutu aracılığıyla konumlar arasında öğelerin paylaşılmasını ele alır.

 Bir ssgıons işlemi, bir kaynak denetimi dosya hiyerarşisi içindeki iki veya daha fazla konum arasındaki dosya ve klasör öğelerinin görünür bir şekilde çoğaltılmasıyla yapılır. Çoğaltma sunucuda gerçekten gerçekleşmiyor, ancak Kullanıcı, belirtilen iki veya daha fazla konumda aynı dosyayı görür. Paylaşılan öğeler üzerinde değişiklik yapıldığında, bu değişiklikler diğer tüm paylaşılan konumlarda görünür.

 Klasörler halinde paylaşma, kaynak denetimi altında en az bir dosya içeren bir klasör seçerseniz işe yarar. Share komutu aşağıdaki koşullarda devre dışı bırakılır:

- Seçili klasör boş bir klasörstur.

- Gerçek bir klasör varsa ancak kaynak denetimi dosyası içermiyorsa.

- Sanal bir klasör varsa, kaynak denetimi altındaki dosyaların içinde olup olmadığı.

- Bir uzak site Web projesi varsa.

## <a name="command-menu-access"></a>Komut menüsü erişimi
 Aşağıdaki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı menü yolları test durumlarında kullanılır.

 Share: **dosya** ->**kaynak denetimi** ->**Share**.

## <a name="expected-behavior"></a>Beklenen davranış

- Paylaşılan dosya paylaşılan konumda görüntülenir.

- Kaynak denetimi sürüm deposu geçmişini görüntülemek, dosyaların paylaşıldığını gösterir.

- Paylaşılan bir dosyayı düzenleme, dosyanın her iki konumunu da düzenler.

## <a name="test-cases"></a>Test çalışmaları
 Aşağıda, paylaşma testi alanı için özel test çalışmaları verilmiştir.

|Eylem|Test adımları|Doğrulanacak beklenen sonuçlar|
|------------|----------------|--------------------------------|
|Kaynak denetimi altındaki yüklü bir projeden başka bir yüklü projeye dosya paylaşma|1. yeni bir proje oluşturun.<br />2. çözüme ikinci bir proje ekleyin.<br />3. ikinci projede ilk projede olmayan bir ada sahip bir dosya oluşturun.<br />4. çözümü kaynak denetimine ekleyin.<br />5. ilk projeyi seçin.<br />6. **Share** iletişim kutusunu açın (**Dosya**  -> **kaynak denetimi**  -> **Share**).<br />7. dosyayı ikinci projeden ilk proje ile paylaşabilirsiniz.<br />8. istenirse **kullanıma alma** kabul edin.|Ortak beklenen davranış.|
|Bir projeden diğerine dosya paylaşma|1. yeni bir proje oluşturun.<br />2. kaynak denetimine ekleyin.<br />3. çözümü kapatın.<br />4. ikinci bir proje oluşturun (yeni çözüm.)<br />5. çözümü kaynak denetimine ekleyin.<br />6. projeyi seçin.<br />7. **paylaşma** iletişim kutusunu açın (**Dosya**  -> **kaynak denetimi**  -> **Share**).<br />8. önceden eklenen projeden bir dosyayı açık projeye paylaşabilirsiniz.<br />9. istenirse **kullanıma alma** kabul edin.|Ortak beklenen davranış.|
|Projenin bir parçası olmayan dosyayı kaynak denetiminden o anda yüklü olan projeye paylaşma|1. yeni bir proje oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. kaynak denetimine proje veya çözümün parçası olmayan bir dosya ekleyin.<br />4. projeyi seçin ve **paylaşma** iletişim kutusunu açın (**Dosya**  -> **kaynak denetimi**  -> **Share**).<br />5. **paylaşma** iletişim kutusunda geçerli proje veya çözüm içinde olmayan bir dosya seçin ve onu paylaşabilirsiniz.<br />6. istenirse **kullanıma alma** kabul edin.|Kaynak denetimi deposu bir get gerçekleştirdi, bu nedenle dosya şimdi projenin yerel konumudur.|
|Aynı proje içindeki dosyaları farklı bir klasöre paylaşma|1. **araçlar**  -> **Seçenekler**  -> **kaynak denetimi**' ne **otomatik olarak kullanıma alma** seçeneğini belirleyin.<br />2. yeni bir proje oluşturun ve kaynak denetimine ekleyin.<br />3. projeye bir klasör ekleyin.<br />4. klasöre bir dosya ekleyin ve klasörü iade edin.<br />5. klasörü seçin.<br />6. **Share** iletişim kutusunu açın (**Dosya**  -> **kaynak denetimi**  -> **Share**).<br />7. dosyayı seçili klasöre paylaşabilirsiniz.|Ortak beklenen davranış.<br /><br /> Klasör, paylaşımda kullanılmadan önce içindeki bir dosyayla birlikte iade edilmiş olmalıdır.|
|Yüklenen projede bir klasörü paylaşma — özyinelemeli|1. yeni bir proje oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. projeyi seçin.<br />4. **paylaşma** iletişim kutusunu açın (**Dosya**  -> **kaynak denetimi**  -> **Share**).<br />5. bir klasör seçin.<br />6. klasörü yinelemeli olarak projeyle paylaşabilirsiniz.|Ortak beklenen davranış.|
|Birden çok dosyayı bir projeden diğerine paylaşma|1. içinde birden çok dosya içeren yeni bir proje oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. çözümü kapatın.<br />4. yeni bir çözümde yeni bir proje oluşturun.<br />5. çözümü kaynak denetimine ekleyin.<br />6. projeyi seçin.<br />7. **paylaşma** iletişim kutusunu açın (**Dosya**  -> **kaynak denetimi**  -> **Share**).<br />8. daha önce oluşturulan projeden birkaç dosyayı şu anda açık olan projeyle paylaşabilirsiniz.|Ortak beklenen davranış.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)