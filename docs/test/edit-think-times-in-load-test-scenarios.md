---
title: Yük testi için düşünme süreleri
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, think times
- load tests, adding delays
- load tests, changing think times
ms.assetid: 8e03bee5-ab7b-4b40-9497-9dbe91ccb90e
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 661a31411a561f15809a10fb15fd71a29e6a64fa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672946"
---
# <a name="edit-think-times-to-simulate-website-human-interaction-delays-in-load-tests-scenarios"></a>Yük testi senaryolarında Web sitesi insan etkileşimi gecikmelerini benzetmek için düşünme zamanlarını düzenleyin

Düşünme süreleri, insanların bir Web sitesi ile etkileşimler arasında beklemesine neden olan insan davranışlarının benzetimini yapmak için kullanılır. Bir Web performans testindeki istekler arasında ve bir yük testi senaryosunda test yinelemeleri arasında düşünme süreleri oluşur. Bir yük testinde düşünme sürelerinin kullanılması, daha doğru yük benzetimleri oluşturmak için yararlı olabilir. Düşünme sürelerinin yük testlerinde kullanılıp kullanılmadığını veya yoksayılmadığını değiştirebilirsiniz. Düşünme sürelerinin **Yük Testi Düzenleyicisi**Yük testlerinizde kullanılıp kullanılmadığını değiştirirsiniz.

*Düşünme profili* , bir yük testinde senaryoya uygulanan bir ayardır. Ayar, Web performans testlerinde kaydedilmiş düşünme sürelerinin yük testi sırasında kullanılıp kullanılmayacağını belirler. Düşünme sürelerini bazı Web başarım testlerinde kullanmak ancak bazılarında değil de kullanmak istiyorsanız, bunları farklı senaryolara yerleştirmeniz gerekir. Senaryolar hakkında daha fazla bilgi için bkz. [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md).

Başlangıçta, **yeni Yük Testi Sihirbazı**kullanarak yük testi oluşturduğunuzda, Yük testlerinizde düşünme süreleri kullanıp kullanmayacağınızı ayarlarsınız. Daha fazla bilgi için bkz. [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md).

**Düşünme profili** seçenekleri aşağıdaki listede açıklanmıştır:

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Dışına**

Düşünme süreleri yok sayılır. Web sunucunuzu yoğun bir şekilde vurgulamak için maksimum yük oluşturmak istediğinizde bu ayarı kullanın. Bir Web sunucusuyla daha gerçekçi kullanıcı etkileşimleri oluşturmaya çalışırken bu uygulamayı kullanmayın.

**Dayanır**

Düşünme süreleri, tam olarak Web performans testinde kaydedildikleri gibi kullanılır. Web performans testlerini tamamen kaydedilmiş şekilde çalıştıran birden çok kullanıcının benzetimini yapar. Bir yük testi birden çok kullanıcının benzetimini yaptığından, aynı düşünme süresini kullanmak eşitlenen sanal kullanıcıların doğal olmayan yük düzenlerini oluşturabilir.

**Normal dağıtım**

Düşünme süreleri kullanılır, ancak normal bir eğri üzerinde değiştirilebilir. İstekler arasında düşünme süresini biraz değiştirerek sanal kullanıcıların daha gerçekçi bir benzetimi sağlar.

> [!NOTE]
> Yük testi senaryosu özelliklerinin ve açıklamalarının tüm listesi için bkz. [Yük testi senaryo özellikleri](../test/load-test-scenario-properties.md).

## <a name="change-the-think-profile"></a>Düşünme profilini değiştirme

### <a name="to-change-a-think-profile-in-a-load-test-scenario"></a>Bir yük testi senaryosunda bir düşünme profilini değiştirmek için

1. Web performans ve yük testi projesinden bir yük testi açın.

2. **Yük Testi Düzenleyicisi**, **Düşünme profilini**değiştirmek istediğiniz senaryo düğümünü seçin. **Düşünme profili** **Özellikler** penceresinde görüntülenir. **Özellikler** penceresini göstermek için **F4** tuşuna basın.

3. **Özellikler** penceresinde **Düşünme profili** özelliğini değiştirin.

4. Özellikleri değiştirmeyi bitirdikten sonra **Dosya** menüsünde **Kaydet** ' i seçin. Ardından, yeni düşünme profiliyle yük testinizi çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını Düzenle](../test/edit-load-test-scenarios.md)