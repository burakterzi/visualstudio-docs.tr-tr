---
title: Modelleme SDK'sı - etki alanına özgü diller | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
ms.assetid: 17a531e2-1964-4a9d-84fd-6fb1b4aee662
caps.latest.revision: 79
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 505c17635c80a165a7a094d3ce2bec3c32bd7101
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297684"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (MSDK) için modelleme SDK 'sını kullanarak, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]tümleştirilebilen güçlü model tabanlı geliştirme araçları oluşturabilirsiniz. Bir örnek olarak, UML araçları MSDK kullanılarak oluşturulur. Aynı şekilde, bir veya daha fazla model tanımı oluşturabilir ve bir araç kümesiyle tümleştirebilirsiniz.

 MSDK'nın merkezinde, iş alanınızdaki kavramları göstermek için oluşturabileceğiniz bir model tanımı bulunur. Modeli diagrammatik görünüm, kod ve diğer yapıtlar oluşturma, modeli dönüştürme komutları ve [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]kod ve diğer nesnelerle etkileşim kurma özelliği gibi çeşitli araçlarla çevreleyebilirsiniz. Modeli geliştirirken, geliştirmenizin merkezine yerleştirilen güçlü bir araç kümesi oluşturmak için onu diğer modellerle birleştirebilirsiniz.

 MSDK, etki alanına özgü dil (DSL) biçiminde bir modeli hızlı bir şekilde geliştirmenize olanak sağlar. Graf gösterimli bir şema veya soyut sözdizimi tanımlamak için özelleştirilmiş bir düzenleyici kullanarak başlarsanız. Bu tanımından, VMSDK şunları oluşturur:

- İşlem tabanlı bir depoda çalışan, türü kesin belirlenmiş bir API ile model uygulaması.

- Ağaç tabanlı bir gezgin.

- Kullanıcıların tanımladığınız modeli veya bölümlerini görüntüleyebildiği bir grafik düzenleyici.

- Modellerinizi okunabilir XML biçiminde kaydeden serileştirme yöntemleri.

- Metin şablonu kullanarak program kodu ve diğer yapıları üretmek için olanaklar.

  Bu özelliklerin tümünü özelleştirebilir ve genişletebilirsiniz. Uzantılarınız, DSL tanımını hala güncelleştirebileceğiniz ve uzantılarınızı kaybetmeden özellikleri yeniden üretebileceğiniz bir şekilde tümleştirilir.

## <a name="samples-and-the-latest-information"></a>Örnekler ve En Son Bilgiler
 [Visual Studio 2015 için modelleme SDK 'sını indirin](https://www.microsoft.com/download/details.aspx?id=48148)

 Visual Studio için modelleme SDK [örnekleri](https://go.microsoft.com/fwlink/?LinkId=186128) .

 Gelişmiş teknikler ve sorun giderme hakkında yönergeler için [Visual STUDIO DSL & modelleme araçları genişletilebilirlik Forumu](https://go.microsoft.com/fwlink/?LinkID=186074)' nu ziyaret edin.

## <a name="in-this-section"></a>Bu Bölümde
 [Etki Alanına Özgü Dillerle Çalışmaya Başlama](../modeling/getting-started-with-domain-specific-languages.md)

 [Modelleri, Sınıfları ve İlişkileri Anlama](../modeling/understanding-models-classes-and-relationships.md)

 [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)

 [Etki Alanına Özgü Dili Özelleştirme ve Genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md)

 [Etki Alanına Özgü bir Dilde Doğrulama](../modeling/validation-in-a-domain-specific-language.md)

 [Etki Alanına Özgü Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)

 [Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)

 [DSL Kodunu Anlama](../modeling/understanding-the-dsl-code.md)

 [Dosya Depolamayı ve XML Serileştirmeyi Özelleştirme](../modeling/customizing-file-storage-and-xml-serialization.md)

 [Etki Alanına Özgü Dil Çözümlerini Dağıtma](../modeling/deploying-domain-specific-language-solutions.md)

 [Windows Forms Tabanlı Etki Alanına Özgü Dil Oluşturma](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

 [WPF Tabanlı Etki Alanına Özgü Dil Oluşturma](../modeling/creating-a-wpf-based-domain-specific-language.md)

 [Nasıl yapılır: Etki Alanına Özgü Dil Tasarımcısını Genişletme](../modeling/how-to-extend-the-domain-specific-language-designer.md)

 [Görselleştirme ve SDK Modelleme için Desteklenen Visual Studio Sürümleri](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)

 [Nasıl yapılır: Etki Alanına Özgü Dili Yeni Sürüme Geçirme](../modeling/how-to-migrate-a-domain-specific-language-to-a-new-version.md)

 [Visual Studio için Modelleme SDK'sı için API Başvurusu](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
