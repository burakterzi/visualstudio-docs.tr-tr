---
title: "Nasıl yapılır: bir etki alanına özgü dil Namespace değiştirme | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: "19"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 3d0dbf6c74c309972862db460f2536d8c6b16801
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Nasıl yapılır: Etki Alanına Özgü bir Dilin Ad Alanını Değiştirme
Bir etki alanına özgü dil ad alanı değiştirebilirsiniz. Değişiklik yapmanız gereken **DSL Explorer**, Dsl paket proje özelliklerini ve derleme bilgileri.  
  
### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Bir etki alanına özgü dil ad alanı değiştirmek için  
  
1.  İçinde **DSL Explorer**, tıklatın **Dsl** düğümü.  
  
2.  İçinde **özellikleri** penceresinde, değişiklik **Namespace** özelliği.  
  
3.  Çözüm kaydedin ve şablonları dönüştürme.  
  
4.  Üzerinde **proje** menüsünde tıklatın **Dsl özellikleri**.  
  
     Projeniz için Özellikler görünür.  
  
5.  Tıklatın **uygulama** sekmesi.  
  
6.  Değişiklik **varsayılan ad alanı** özelliği için yeni ad alanı adı.  
  
7.  Ayrıca derlemenin adını değiştirmek isterseniz, değiştirmek **derleme name özelliği.**  
  
8.  Derleme adı değişirse, DslPackage\Package.tt açın ve bu satırı güncelleştirin:  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. Özel kod yazdıysanız, ad alanını ve sınıf başvurularını kod dosyalarında değiştirdiğinizden emin olun.  
  
10. Visual Studio deneysel örneği sıfırlayın.  
  
    1.  Silme **\Users\\***{ad}***\AppData\Local\Microsoft\VisualStudio\\\*Exp**  
  
    2.  Windows **Başlat** menüsünde seçin **tüm programlar**, **Microsoft Visual Studio 2010 SDK**, **Araçları**, **Sıfırla Deneysel örneği**.  
  
11. Üzerinde **yapı** menüsünde seçin **çözümü yeniden derle**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etki alanına özgü dil araçları sözlüğü](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)