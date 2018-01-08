---
title: "Nasıl yapılır: bildirim temelli Kural koşulu (eski) oluşturma | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 57835632e03e8b871c29e2fec7d4b382722451e7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Nasıl yapılır: bildirim temelli Kural koşulu (eski) oluşturma
Bu konu, eski kullanarak bir kural koşulu bildirmek açıklar [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hedefleyen [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] veya [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Bir koşul deyimi değerlendiren **True** veya **False**. Bir bildirim temelli Kural koşulu kullanılarak oluşturulan bir koşul deyimi olan [Kural Koşulu Düzenleyicisi iletişim kutusu (eski)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) ve iş akışı ile XML olarak depolanır. İş akışı durumu ve birden çok koşulları birleştirir Boolean cebiri karşılaştırmak koşulları içerebilir.  
  
 Bildirim temelli kural koşulları, aşağıdaki Windows Workflow Foundation out-of-box etkinlikler kullanılır:  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [Öğeye](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Kural Koşulu Düzenleyicisi'ni kullanarak bir bildirim temelli Kural koşulu oluşturmak için  
  
1.  Etkinliğin içinde **özellikleri** penceresinde tıklatın **koşul** özelliği veya **UntilCondition** etkinliğe bağlı olarak özellik.  
  
2.  Seçin **bildirim temelli Kural koşulu** özelliği için listeden.  
  
3.  Genişletme **koşulu** veya **UntilCondition** özelliği.  
  
4.  Tıklatın **ConditionName** özelliği.  
  
5.  Tıklatın **ConditionName** üç nokta **[...]**  açmak için **seçin koşulu** iletişim kutusu.  
  
6.  Tıklatın **yeni koşul** açmak için **Kural Koşulu Düzenleyicisi** iletişim kutusu.  
  
7.  Koşul ifadesi yazın **koşulu** metin kutusu.  
  
     Koşul ifadeleri oluşturma hakkında daha fazla bilgi için bkz: [Kural Koşulu Düzenleyicisi iletişim kutusu (eski)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).  
  
8.  Koşul ifadesi oluşturmayı tamamladığınızda tıklatın **Tamam** iletişim kutusunu kapatmak ve atanmış bir ad ile Kural koşulu oluşturmak için.  
  
     **Seçin koşulu** iletişim kutusu açılır.  
  
     Nasıl kullanılacağı hakkında bilgi için **seçin koşulu** iletişim kutusu, bkz: [koşulu iletişim kutusunu (eski)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski iş akışı etkinlikleri](../workflow-designer/legacy-workflow-activities.md)   
 [ConditionedActivityGroup kullanma](http://go.microsoft.com/fwlink?LinkID=65066)   
 [Öğeye etkinliğini kullanma](http://go.microsoft.com/fwlink?LinkID=65075)   
 [Çoğaltıcı etkinliğini kullanma](http://go.microsoft.com/fwlink?LinkID=65080)   
 [While kullanarak etkinliği](http://go.microsoft.com/fwlink?LinkID=65091)   
 [Kural Koşulu Düzenleyicisi iletişim kutusu (eski)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [Koşul iletişim kutusu (eski) seçin](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [İş akışlarında koşullar kullanma](http://go.microsoft.com/fwlink?LinkID=65009)