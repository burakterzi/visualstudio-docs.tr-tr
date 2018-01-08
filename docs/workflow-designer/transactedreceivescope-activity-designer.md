---
title: "TransactedReceiveScope etkinlik Tasarımcısı | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 20dce7d4b3dc306c7bcd4f83a1f4e8fea10c6a94
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope etkinlik Tasarımcısı
**TransactedReceiveScope** Tasarımcısı oluşturmak ve yapılandırmak için kullanılan bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik.  
  
## <a name="the-transactedreceivescope-activity"></a>TransactedReceiveScope etkinliği  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> Etkinliğini bir iş akışı veya gönderen tarafından oluşturulan sunucu hareketleri harekete akış olanak sağlar.  
  
### <a name="using-the-transactedreceivescope-activity-designer"></a>TransactedReceiveScope etkinlik Tasarımcısı'nı kullanarak  
 **TransactedReceiveScope** etkinlik Tasarımcısı bulunabilir **ileti** kategorisini **araç**, hangi tıklayarak erişildiğinde **araç kutusu**  sekmesi [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (Alternatif olarak, seçin **araç** gelen **Görünüm** menüsü veya CTRL + ALT + X.)  
  
 **TransactedReceiveScope** gelen etkinlik Tasarımcısı sürüklenebilir **araç** ve oturum bırakılan [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] yüzey yerde etkinlikleri genellikle yerleştirilir. Bu oluşturur bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> varsayılan etkinlik **DisplayName** TransactedReceiveScope biri. <xref:System.Activities.Activity.DisplayName%2A> Üstbilgisinde düzenlenebilir **TransactedReceiveScope** etkinlik Tasarımcısı veya **DisplayName** ve özellik ızgarasının kutusu.  
  
 **TransactedReceiveScope** Tasarımcısı içeren **isteği** ve **gövde** kutuları. Bunlar yapılandırmak için kullanılan <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> belirtir özelliği bir <xref:System.ServiceModel.Activities.Receive> etkinliği ve bir <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> başka belirtir özelliği <xref:System.Activities.Activity>. <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> Bir işlem oluşturur. İşlemin ardından kapsamını ortam yapılan <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> böylece bu kapsam içinde herhangi bir etkinlik bu işlem içinde yürütür.  
  
### <a name="the-transactedreceivescope-properties"></a>TransactedReceiveScope özellikleri  
 Aşağıdaki tabloda <xref:System.ServiceModel.Activities.TransactedReceiveScope> özellikleri ve bunların Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır. Bunlar <xref:System.Activities.Activity.DisplayName%2A> özelliği, özellik kılavuzu veya üzerinde düzenlenebilir [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] yüzeyini, ancak diğer gerekir düzenlenmesi tasarım yüzeyine.  
  
|Özellik adı|Gerekli|Kullanım|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|İsteğe bağlı kolay adını <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik. TransactedReceiveScope varsayılandır.<br /><br /> Ancak <xref:System.Activities.Activity.DisplayName%2A> adı kesinlikle gerekli değil, bir görünen ad kullanmak için en iyi bir uygulamadır.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|Doğru|Düşme bir <xref:System.ServiceModel.Activities.Receive> etkinliğini **isteği** etkinlik Tasarımcısı yüzeyinde bloğu.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Düşme bir <xref:System.Activities.Activity> içine **gövde** etkinlik Tasarımcısı yüzeyinde bloğu.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Alma](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Gönder](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)