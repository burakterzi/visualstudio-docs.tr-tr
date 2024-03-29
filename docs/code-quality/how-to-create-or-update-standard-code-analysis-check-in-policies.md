---
title: Standart Kod Analizi İade İlkeleri Oluşturma veya Güncelleştirme
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e6d502dc75530bb6b95f38b069b9220c5ad54cac
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649470"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Nasıl yapılır: Standart Kod Çözümleme İade İlkeleri Oluşturma veya Güncelleme

Kod Analizi iade etme ilkesini kullanarak bir Azure DevOps projesindeki tüm kod projelerinde kod analizinin çalıştırılmasını zorunlu kılabilirsiniz. Kod analizini zorunlu kılmak, kod tabanına işaretlenmiş kodun kalitesini iyileştirebilir.

> [!NOTE]
> Bu özellik yalnızca Team Foundation Server kullanıyorsanız kullanılabilir.

Kod Analizi iade ilkeleri proje ayarlarında ayarlanır ve her bir kod projesi için geçerlidir. Kod Analizi çalıştırmaları, kod projesi için proje (. xxproj) dosyasındaki kod projeleri için yapılandırılır. Kod Analizi çalıştırmaları yerel bilgisayarda gerçekleştirilir. Bir kod analizi iade ilkesini etkinleştirdiğinizde, iade edilecek bir kod projesindeki dosyaların son Düzenlemeden sonra derlenmesi gerekir ve en azından içeren bir kod analizi çalıştıraldıktan sonra, proje ayarlarındaki kuralların değişikliğin bulunduğu bilgisayarda gerçekleştirilmesi gerekir yapıldı.

- Yönetilen kod için, kod analizi kurallarının bir alt kümesini içeren bir *kural kümesi* belirterek iade ilkesini ayarlarsınız.

- C/C++ Code Için, Visual Studio 2017 sürüm 15,6 ve önceki sürümlerde, iade ilkesi tüm kod analizi kurallarının çalıştırılmasını gerektirir. Azure DevOps projenizdeki bireysel kod projeleri için belirli kuralları devre dışı bırakmak üzere ön işlemci yönergeleri ekleyebilirsiniz. 15,7 ve sonraki sürümlerde, çalıştırılacak kuralları belirtmek için **/Analyze: RuleSet** komutunu kullanabilirsiniz. Daha fazla bilgi için bkz. [çalıştırılacak C++ kuralları belirtmek Için kural kümelerini kullanma](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

Yönetilen kod için bir iade ilkesi belirttikten sonra, ekip üyeleri kod projeleri için kod analizi ayarlarını Azure DevOps proje ilkesi ayarlarına eşitleyebilir.

## <a name="to-open-the-check-in-policy-editor"></a>İade İlkesi düzenleyicisini açmak için

1. Takım Gezgini, proje adına sağ tıklayın, **proje ayarları**' nın üzerine gelin ve **kaynak denetimi**' ne tıklayın.

1. **Kaynak denetimi** iletişim kutusunda, **iade ilkesi** sekmesini seçin.

1. Aşağıdakilerden birini yapın:

    - Yeni bir iade ilkesi oluşturmak için **Ekle** ' ye tıklayın.

    - İlkeyi değiştirmek için **Ilke türü** listesindeki mevcut **Kod Analizi** öğesine çift tıklayın.

## <a name="to-set-policy-options"></a>İlke seçeneklerini ayarlamak için

Aşağıdaki seçenekleri seçin veya temizleyin:

|Seçenek|Açıklama|
|------------|-----------------|
|**İade etme yalnızca geçerli çözümün parçası olan dosyaları içerecek şekilde zorla.**|Kod Analizi, yalnızca çözüm ve proje yapılandırma dosyalarında belirtilen dosyalarda çalıştırılabilir. Bu ilke, bir çözümün parçası olan tüm kodların çözümlenme garantisi sağlar.|
|**C/C++ Code analizini zorla (/Analyze)**|Tüm C veya C++ projelerin, iade etmeden önce kod analizini çalıştırmak için/analyze derleyici seçeneğiyle oluşturulması gerekir.|
|**Yönetilen kod için kod analizini zorla**|Tüm yönetilen projelerin, iade etmeden önce kod analizini ve derlemeyi çalıştırmasını gerektirir.|

## <a name="to-specify-a-managed-rule-set"></a>Yönetilen bir kural kümesi belirtmek için

**Bu kural kümesini Çalıştır** listesinde, aşağıdaki yöntemlerden birini kullanın:

- Bir Microsoft standart kural kümesi seçin.

- Kaynak denetiminden \<Select kural kümesi ' ne tıklayarak özel bir kural seçin **... >** . Sonra, kaynak denetim tarayıcısında kural kümesinin sürüm denetim yolunu yazın. Sürüm denetimi yolunun sözdizimi şöyledir:

   **$/** `TeamProjectName` **/** `VersionControlPath`

Özel bir iade ilkesi kural kümesi oluşturma ve uygulama hakkında daha fazla bilgi için bkz. [yönetilen kod Için özel Iade Ilkeleri uygulama](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Analizi iade ilkeleri oluşturma ve kullanma](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)
