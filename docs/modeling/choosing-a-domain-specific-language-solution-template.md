---
title: "Bir etki alanına özgü dil çözüm şablonu seçme | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: "24"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: b636ab7937c85199c26b8ce8a95fa33cdcc7976b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Etki Alanına Özgü Dil Çözümü Şablonu Seçme
Bir etki alanına özgü dil çözüm oluşturmak için etki alanına özgü dil Tasarımcısı Sihirbazı'nda kullanılabilir çözüm şablonlardan birini seçin. Oluşturmak istediğiniz dil en çok benzeyen bir şablon seçerek başlangıç çözüme yapmak zorunda değişiklikler en aza indirebilirsiniz.  
  
 Etki alanına özgü dil Tasarımcısı Sihirbazı'nda aşağıdaki çözüm şablonları kullanılabilir.  
  
|Şablon|Özellikler|Açıklama|  
|--------------|--------------|-----------------|  
|Sınıf diyagramları|-Bölme şekiller<br />-Sınıf devralma<br />-İlişki devralma<br />-Şekil devralma<br />-İlişki özellikleri|Etki alanına özgü dil varlıkları ve özelliklere sahip ilişkileri içeriyorsa, bu çözüm şablonu kullanın. Bu şablon UML sınıf diyagramları benzer bir etki alanına özgü dil oluşturur. Temel sınıflar ve arabirimler ilişkilendirme, Genelleştirme ve uygulama ilişkileri birlikte varlıklardır. Bir sınıf veya arabirim öznitelikler listesini içeren bir kutu olarak görünür.|  
|Bileşen diyagramları|-Bağlantı noktaları|Etki alanına özgü dil bileşenler diğer bir deyişle, bir yazılım sistemin bölümleri içeriyorsa, bu çözüm şablonu kullanın. Bu şablon UML Bileşen diyagramları benzer bir etki alanına özgü dil oluşturur. Ana bileşenlerini ve dış bileşenlerinin küçük şekiller olarak görünür bağlantı noktaları varlıklardır.|  
|Görev akış diyagramları|-Görüntü ve geometri şekiller<br />-   *Kulvarları*|İş akışları, durumları veya sıraları, etki alanına özgü dil içeriyorsa, bu çözüm şablonu kullanın. Bu şablon UML etkinlik diyagramları benzer bir etki alanına özgü dil oluşturur. Bir etkinlik ana varlıktır ve etkinlikler arasında bir geçiş ana ilişkidir. Şablon başlangıç durumu, son durumunu ve bir eşitleme çubuğu gibi birkaç diğer öğeleri içerir.|  
|En az bir dil|-Bir sınıf ve Şekil<br />-Bir ilişkisi ve bağlayıcı|Etki alanına özgü dil diğer şablonlar benzemez Bu çözüm şablonu kullanın. Bu şablon, iki sınıf ve temsil edilen bir ilişkisi olan bir etki alanına özgü dil oluşturur **araç** olarak **kutusunu** ve **satır**. Sınıf ve ilişki bir örnek dize özelliğine sahip.|  
|En az WinForm Tasarımcısı|-Küçük bir model.<br />-Modeli görüntüler bir Windows formu.|DSL grafik Tasarımcı yerine bir Windows formunda bağlandı bir uygulama oluşturmak istiyorsanız, bu şablonu kullanın.<br /><br /> Dili için kullanıcı arabirimi olarak görev yapar form Dsl\UI klasöründe bulunur.<br /><br /> Form tasarımcısı açmadan önce projeyi oluşturması gerekir.<br /><br /> Daha fazla bilgi için bkz: [Windows Forms-Based etki alanına özgü dil oluşturma](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|  
|En az WPF Tasarımcısı|-Küçük modeli<br />-Modeli görüntüler bir Windows Presentation Foundation kullanıcı arabirimi|DSL grafik Tasarımcı yerine bir WPF kullanıcı arabirimi bağlandı bir uygulama oluşturmak istiyorsanız, bu şablonu kullanın.<br /><br /> Kullanıcı arabirimi için tasarımcı Dsl\UI klasöründe bulunur.<br /><br /> UI Tasarımcısı açmadan önce projeyi oluşturması gerekir.<br /><br /> Daha fazla bilgi için bkz: [WPF-Based etki alanına özgü dil oluşturma](../modeling/creating-a-wpf-based-domain-specific-language.md).|  
|DSL kitaplığı|-En az kitaplığı|Diğer DSL tanımları aktarılabilen bir kısmi DSL tanımı oluşturmak istiyorsanız bu şablonu kullanın.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etki Alanına Özgü Dil Araçlarına Genel Bakış](../modeling/overview-of-domain-specific-language-tools.md)