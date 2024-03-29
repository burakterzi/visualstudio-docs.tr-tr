---
title: 'Nasıl yapılır: Iş akışı hata ayıklayıcısını çağırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 13fd54eeebf0323fcb9b8cad6a8cd8b75ae11fb3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292886"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Nasıl yapılır: Iş akışı hata ayıklayıcısını çağırma
Genellikle, diğer Visual Studio programlama dillerinde yazılmış programlarda hata ayıkladığınızda olduğu gibi iş akışlarında hata ayıklaması yapabilirsiniz. İş akışı hata ayıklayıcısını aşağıdaki yollarla başlatabilirsiniz:

- İş akışı örneğiniz için çalışan konak işlemini seçmek üzere **hata ayıklama** menüsünde **İşleme İliştir** ' i seçin. Bu yordam, Yönetilen koddaki bir ana bilgisayar işlemine iliştirme ile aynıdır.

- İş akışının bir örneğini çalıştırmaya başlamak veya bir kesme noktası isabet ettikten sonra çalışmaya devam etmek için **F5** tuşuna basın.

- Uzaktan hata ayıklamayı kullan. Uzaktan hata ayıklamayı kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: uzaktan hata ayıklamayı etkinleştirme](https://go.microsoft.com/fwlink/?LinkId=196257).

    > [!NOTE]
    > İş akışı uygulaması x86 mimarisini hedefliyorsa ve 64 bitlik bir işletim sistemi çalıştıran bir makinede barındırılıyorsa, uzak makineye [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] yüklenmezse veya iş akışı uygulamasının hedefi **herhangi BIR CPU**olarak değiştirilmediği takdirde uzaktan hata ayıklama çalışmaz.

### <a name="stepping-through-code"></a>Kod üzerinden adımla

- **Adım adım**: **F11**kullanarak bir etkinliğe adım adım ekleyebilirsiniz. Hata ayıklama adımlarında içinde tanımlanan herhangi bir işleyici. Hiçbir tutucusu tanımlanmazsa, etkinliğin adım veya diğer etkinlikler içeren bileşik etkinliklerle ilk yürütme etkinliğini adım.

- **Dışarı adımla:** **SHIFT-F11**kullanarak bir etkinliğin dışına ilerliğinizi sağlayabilirsiniz. Bir etkinlik dışına Adımlama geçerli etkinliği ve tüm eşdüzey tamamlanana kadar etkinlikleri çalıştırır. Hata ayıklayıcı, ardından geçerli etkinliğin üst öğede keser. Bir kod işleyicisinden Adımlama, hata ayıklayıcı işleyici ilişkilendirildiği faaliyete keser.

- **Adımlama**: **F10**kullanarak bir etkinliğin üzerinde ilerliğinizi yapabilirsiniz. Bileşik bir etkinliğin üzerine adımlarken, hata ayıklayıcı bileşik etkinliğin ilk yürütülebilir alt öğesi üzerinde kesilir. <xref:System.Activities.Statements.Assign> etkinlik gibi bir bileşik olmayan üzerinde Adımlama yaparken, hata ayıklayıcı aktiviteyi ve ilgili işleyicileri ve bir sonraki etkinliğin üzerinde kesintiler yürütür. Yürütülen etkinlik bileşik bir etkinlikte son alt etkinlikse, yürütmeden sonra hata ayıklayıcı üst etkinliği keser.

### <a name="debugging-with-f5"></a>F5 tuşuna basarak hata ayıklama

- Bir Iş akışı konsol uygulaması projesi oluşturuyorsanız, uygulamanızda ve iş akışınızda hata ayıklamaya başlamak için **F5** tuşuna basın. Kendi başına bir etkinlik kitaplığı oluşturuyorsanız, başlangıç projesi olarak bir çalıştırılabilir konak uygulamanız olması gerekir. **Çözüm Gezgini**bir başlangıç projesi ayarlamak için konağın proje adına sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır:](../workflow-designer/how-to-set-breakpoints-in-workflows.md) [iş akışı Tasarımcısı iş akışlarında hata ayıklama Iş](../workflow-designer/debugging-workflows-with-the-workflow-designer.md) akışlarında kesme noktaları ayarlama