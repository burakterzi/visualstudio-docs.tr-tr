---
title: Proje türü tasarım kararları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d6d1df2a3b2188360b0ee60480b4d6580ed8faf
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725387"
---
# <a name="project-type-design-decisions"></a>Proje Türü Tasarım Kararları
Yeni bir proje türü oluşturmadan önce, proje türü ile ilgili çeşitli tasarım kararları almanız gerekir. Projelerinize hangi öğe türlerinin ekleneceğini, proje dosyalarının nasıl kalıcı olacağını ve hangi taahhüt modelinin kullanılacağını karar vermelisiniz.

## <a name="project-items"></a>Proje öğeleri
 Projeniz dosyaları veya soyut nesneleri kullanacak mı? Dosyaları kullanıyorsanız, bunlara başvuru tabanlı veya dizin tabanlı dosyalar olur. Dosyalar veya soyut nesneler yerel veya uzak olacak mı?

 Projedeki öğeler dosyalar olabilir veya bir veritabanı deposundaki nesneler veya Internet üzerindeki veri bağlantıları gibi daha soyut nesneler olabilir. Öğeler dosyalar ise, proje başvuru tabanlı ya da dizin tabanlı bir proje olabilir.

 Başvuru tabanlı projelerde, öğeler birden fazla projede görünebilir. Ancak, bir öğenin temsil ettiği gerçek dosya yalnızca bir dizinde bulunur. Dizin tabanlı projelerde, tüm proje öğeleri dizin yapısında bulunur.

 Yerel öğeler, uygulamanın yüklü olduğu bilgisayarda depolanır. Uzak öğeler, yerel ağdaki ayrı bir sunucuda veya Internet 'te başka bir yerde depolanabilir.

## <a name="project-file-persistence"></a>Proje dosyası kalıcılığı
 Veriler ortak düz dosya sistemlerinde mi, yoksa yapılandırılmış depolamada mı depolanacak? Dosyalar standart bir düzenleyici veya projeye özgü bir düzenleyici kullanılarak açılacak mi?

 Verilerini kalıcı hale getirmek için, çoğu uygulama verilerini bir dosyaya kaydeder ve bir kullanıcının bilgileri gözden geçirmesi veya değiştirmesi gerektiğinde onu geri okur.

 Birleşik dosyalar olarak da adlandırılan yapılandırılmış depolama, genellikle birkaç bileşen nesne modeli (COM) nesnesinin kalıcı verilerini tek bir dosyada depolaması gerektiğinde kullanılır. Yapılandırılmış depolama ile, çeşitli farklı yazılım bileşenleri tek bir disk dosyasını paylaşabilir.

 Projenizdeki öğelerin kalıcılığını göz önünde bulundurmanız gereken birkaç seçeneğiniz vardır. Aşağıdaki seçeneklerden herhangi birini yapabilirsiniz:

- Her dosyayı değiştirildiğinde tek tek kaydedin.

- Tek bir **kaydetme** işleminde çok sayıda işlem yakalayın.

- Dosyaları yerel olarak kaydedin ve sonra bir sunucuya yayımlayın veya öğe, uzak bir nesne ile bir veri bağlantısını temsil ettiğinde proje öğelerini kaydetmek için başka bir yaklaşım kullanın.

  Kalıcılık hakkında daha fazla bilgi için bkz. [Proje kalıcılığı](../../extensibility/internals/project-persistence.md) ve [Proje öğelerini açma ve kaydetme](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="project-commitment-model"></a>Proje taahhüt modeli
 Kalıcı veri nesneleri doğrudan modda veya işlem temelli modda açılacak mı?

 Veri nesneleri doğrudan modda açıldığında, verilerde yapılan değişiklikler anında veya Kullanıcı dosyayı el ile kaydettiğinde eklenir.

 Veri nesneleri işlem temelli mod kullanılarak açıldığında, değişiklikler bellekteki geçici bir konuma kaydedilir ve Kullanıcı el ile dosyayı kaydetmeyi seçinceye kadar kaydedilmez. Bu sırada, tüm değişikliklerin birlikte gerçekleşmesi veya hiçbir değişiklik yapılmayacak olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Denetim Listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Proje Öğelerini Açma ve Kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)
- [Proje Kalıcılığı](../../extensibility/internals/project-persistence.md)
- [Proje Modeli Öğeleri](../../extensibility/internals/elements-of-a-project-model.md)
- [Proje Modeli Çekirdek Bileşenleri](../../extensibility/internals/project-model-core-components.md)
- [Proje Türleri Oluşturma](../../extensibility/internals/creating-project-types.md)