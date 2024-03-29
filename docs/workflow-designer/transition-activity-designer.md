---
title: İş Akışı Tasarımcısı geçişi etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Transition.UI
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: a0a058a874903a7b316ebbe45e117e920d238870
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649811"
---
# <a name="transition-activity-designer"></a>Transition Etkinlik Tasarımcısı

@No__t_0 iki durum arasındaki geçişi temsil eder.

## <a name="using-the-transition-activity-designer"></a>Geçiş etkinliği tasarımcısını kullanma

Geçiş etkinliği Tasarımcısı iki durum arasında geçiş yapılandırmanızı sağlar.

### <a name="transition-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı geçiş özellikleri

Aşağıdaki tabloda, iş akışı Tasarımcısı kullanılarak ayarlayabilecekleri <xref:System.Activities.Statements.Transition> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|False|@No__t_0 etkinlik tasarımcısının kolay adını belirtir. Varsayılan değer **T1**' dir. Değer, genişletilmiş geçiş tasarımcısının üst bilgisinde ve genişletilmiş geçiş Tasarımcısı içindeki eylem bölümünde bulunan özellik kılavuzunda düzenlenebilir. @No__t_0, iş akışı tasarımcısının üst kısmında görüntülenen içerik haritası gezintisinde kullanılır.<br /><br /> @No__t_0 kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.Transition.Condition%2A>|False|Varsa, denetim hedef durumuna geçirilmeden önce **true** olarak değerlendirilmesi gereken bir ifade belirtir. Bu koşul, özellik kılavuzunda ve genişletilmiş geçiş tasarımcısında düzenlenebilir. Paylaşılan bir geçişte birden çok koşul, geçiş tasarımcısında göründükleri sırayla değerlendirilir. **Note:**  Bir geçişin <xref:System.Activities.Statements.Transition.Condition%2A> **false** olarak değerlendirilirse (veya paylaşılan bir tetikleyici geçişinin tüm koşullarının **yanlış**olduğunu değerlendirmesi), geçişin gerçekleşmeyeceğini ve durumdan gelen tüm geçişlerin her tetikleyicisinin yeniden planlanacağını unutmayın. Bu öğreticide, koşulların yapılandırıldığı şekilde bu durum gerçekleşmemelidir (tahminin doğru veya hatalı olması için özel eylemlerdir).|
|**Kaynaktaki**|Doğru|Bu geçişin kaynaklandığı durumu gösterir. Kaynak durumunun adına tıklamak, tasarımcı görünümünü bu durumun genişletilmiş bir görünümüne geçirir. Bu değer, geçiş oluşturulduğunda ayarlanır ve değiştirilemez.|
|<xref:System.Activities.Statements.Transition.Trigger%2A>|False|Tamamlanması geçişi Başlatan etkinliği belirtir. Bu etkinliği ayarlamak için, **araç kutusundan** bir etkinliği sürükleyin ve geçişin **tetikleme** bölümüne bırakın.|
|<xref:System.Activities.Statements.Transition.Action%2A>|False|Tetikleyici etkinliği tamamlandığında ve varsa <xref:System.Activities.Statements.Transition.Condition%2A>, **true**olarak değerlendirilirse yürütülen etkinliği belirtir. Bu etkinlik, kaynak durumu için <xref:System.Activities.Statements.State.Exit%2A> etkinliği varsa, hedef duruma geçiş yaparken yürütülür. Geçiş Tasarımcısı genişletildiğinde, bu değer **araç kutusundan** bir etkinlik sürüklenerek geçişin **eylem** bölümüne bırakılarak ayarlanabilir. Tek bir geçiş için birden çok eylem olabilir. Tek tek eylemler genişletilebilir ve uygulanabilir olur ve bir geçişte birden çok eylem olduğunda, eylemde görüntülenen yukarı veya aşağı oka tıklanarak sıralanabilir.|
|**Hedefine**|Doğru|Geçiş tamamlandıktan sonra durum makinesinin geçiş durumunu gösterir. Bu, nesne modelindeki geçişin <xref:System.Activities.Statements.Transition.To%2A> özelliğine karşılık gelir. Hedef durumunun adına tıklamak, tasarımcı görünümünü bu durumun genişletilmiş bir görünümüne geçirir. Bu değer, geçiş oluşturulduğunda ayarlanır ve geçişi tasarımcıda hedef durumuna bağlayan ok sürüklenerek değiştirilebilir.|

### <a name="creating-transitions"></a>Geçişler oluşturma

Geçişler bir durumdan diğerine sürüklenerek veya bir durum başka bir durum üzerinde sürüklendiğinde görüntülenen üçgenlere bir durum bırakılarak oluşturulur. Sürükleyerek bir geçiş oluşturmak için, fareyi kaynak durumunun kenarının üzerine getirin ve kaynak durumdan bir çizgiyi hedef durumuna sürükleyin. Bırakarak geçiş oluşturmak için, hedef durumunu sürükleyin ve kaynak durumunun üzerine gelin ve kaynak durumu etrafında görüntülenen dört üçgenden birine bırakın. Hedef durum, **araç kutusundan**sürüklenen yeni bir durum ya da iş akışı tasarımcısından sürüklenen mevcut bir durum olabilir.

> [!NOTE]
> Bir durum makinesindeki tek bir durum, iş akışı Tasarımcısı kullanılarak oluşturulan en fazla 76 geçişine sahip olabilir. Tasarımcı dışında oluşturulan iş akışları için bir durum geçişleri sınırı yalnızca sistem kaynaklarıyla sınırlıdır.

Paylaşılan tetikleyici geçişleri, aynı tetikleyici olayını paylaşan geçişler kümesidir. Paylaşılan tetikleyici, ortak bir tetikleyici olayını paylaşan birden çok geçiş için yapılandırılmış ifadelerin değerlendirmesine bağlı olarak bir hedef duruma yönelik koşullu ilerlemeyi sağlar. Bir geçişe ek eylemler eklemek ve paylaşılan bir geçiş oluşturmak için, istenen geçişin başlangıcını belirten daireye tıklayın ve istediğiniz duruma sürükleyin. Yeni geçiş, başlangıç geçişi olarak aynı tetikleyiciyi paylaşır, ancak benzersiz bir koşula ve eyleme sahip olur. Paylaşılan geçişler, geçiş Tasarımcısı ' nın altında **Paylaşılan tetikleyici geçişi ekle** ' ye tıklayıp, ardından **bağlantı kurmak için kullanılabilir durumlar** ' da istenen hedef durumu seçilerek geçiş Tasarımcısı içinden da oluşturulabilir açılır liste.

## <a name="see-also"></a>Ayrıca bkz.

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [State](../workflow-designer/state-activity-designer.md)