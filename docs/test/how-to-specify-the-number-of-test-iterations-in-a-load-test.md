---
title: Yük testi çalıştırma ayarında test yinelemesi sayısını belirtin
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 45a625db-b3e7-4d64-beda-b9a76248096d
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aa5de5f7f9c1bfef78ad3698886e8d7af43a4812
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653388"
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>Nasıl yapılır: bir yük testi çalışma ayarında test yineleme sayısını belirtme

**Yeni Yük Testi Sihirbazı**yük testinizi oluşturduktan sonra, test ihtiyaçlarını ve hedeflerinizi karşılamak üzere senaryolar özelliklerini değiştirmek için **Yük Testi Düzenleyicisi** kullanabilirsiniz. Daha fazla bilgi için bkz. [Izlenecek yol: yük testi oluşturma ve çalıştırma](../test/walkthrough-create-and-run-a-load-test.md).

**Yük Testi Düzenleyicisi**kullanarak, **Özellikler** penceresinde bir çalışma ayarları değerinin **test yinelemeleri** özelliğini düzenleyebilirsiniz. **Test yinelemeleri** özelliği, **Yük Testi Düzenleyicisi**kullanarak bir yük testinde tüm senaryolarda tüm Web performansı ve birim testlerinde çalıştırılacak yineleme sayısını belirtir.

> [!NOTE]
> Çalışma ayarları özelliklerinin ve açıklamalarının tüm listesi için bkz. [Yük testi çalıştırma ayarları özellikleri](../test/load-test-run-settings-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-the-number-of-test-iterations-in-a-run-setting"></a>Çalışma ayarında test yinelemesi sayısını belirtmek için

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görüntülenir ve yük testi ağacını görüntüler.

2. Yük testi ağacında, **çalışma ayarları** klasöründe bir çalıştırma ayarı seçin.

3. **Görünüm** menüsünde **Özellikler penceresi** ' ni seçerek yük çalıştırma ayarlarının kategorilerini ve özelliklerini görüntüleyin.

4. **Test Yinelemeleri Kullan** özelliğini **doğru**olarak ayarlayın.

5. **Test yinelemeleri** özelliğinde, yük testi sırasında çalıştırılacak test yinelemesi sayısını gösteren bir sayı girin.

6. Özelliği değiştirmeyi bitirdikten sonra **Dosya** menüsünde **Kaydet** ' i seçin. Ardından, yeni **test yinelemeleri** değerini kullanarak yük testinizi çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandır](../test/configure-load-test-run-settings.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)