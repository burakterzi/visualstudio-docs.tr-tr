---
title: "Visio nesne modeline genel bakış | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Visio
- objects [Office development in Visual Studio], Office object models
- Office object models
- Visio object model
ms.assetid: 11f0ae0c-feff-46c7-9885-b968391718f7
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0ba481206e24870e0772290beba129d373c30862
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="visio-object-model-overview"></a>Visio Nesne Modeline Genel Bakış
  Microsoft Office Visio için Office çözümleri geliştirmek için Visio nesne modeli ile etkileşim kurabilirsiniz. Bu nesne modeli sınıfları ve birincil birlikte çalışma derlemesi Visio için sağlanan ve Microsoft.Office.Interop.Visio ad alanında tanımlanan arabirimleri oluşur.  
  
 Bu konu, Visio nesne modeline kısa bir genel bakış sağlar. Office projelerinde görevleri gerçekleştirmek için Visio nesne modelini kullanma hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Visio Belgeleriyle Çalışma](../vsto/working-with-visio-documents.md)  
  
-   [Visio Şekilleri ile Çalışma](../vsto/working-with-visio-shapes.md)  
  
## <a name="understanding-the-visio-object-model"></a>Visio nesne modelini anlama  
 Visio ile etkileşim kurabilen birçok nesne sağlar. Bu nesneler kullanıcı arabirimini yakından takip eden hiyerarşik olarak düzenlenir. Hiyerarşisinin en üstünde olduğu [Microsoft.Office.Interop.Visio.Application](https://msdn.microsoft.com/library/office/ff766485.aspx) nesnesi. Bu nesne Visio'nun geçerli örneğini temsil eder. Microsoft.Office.Interop.Visio.Application nesnesi Microsoft.Office.Interop.Visio.Documents yanı sıra Microsoft.Office.Interop.Visio.Document ve Microsoft.Office.Interop.Visio.Page nesneleri içerir ve Microsoft.Office.Interop.Visio.Pages koleksiyonları. Bu nesneleri ve koleksiyonları her birçok yöntem ve işlemek ve ile etkileşim için erişebileceği özellikler vardır.  
  
 Daha fazla bilgi için VBA başvuru belgelerine bakın [Microsoft.Office.Interop.Visio.Application](https://msdn.microsoft.com/library/office/ff766485.aspx), [Microsoft.Office.Interop.Visio.Document](https://msdn.microsoft.com/library/office/ff765575.aspx), ve [ Microsoft.Office.Interop.Visio.Page](https://msdn.microsoft.com/library/office/ff767035.aspx) nesneleri ve ayrıca [Microsoft.Office.Interop.Visio.Documents](https://msdn.microsoft.com/library/office/ff768812.aspx) ve [Microsoft.Office.Interop.Visio.Pages](https://msdn.microsoft.com/library/office/ff766165.aspx) koleksiyonları.  
  
 Aşağıdaki bölümlerde, üst düzey nesneleri ve birbirleri ile nasıl etkileşim kurduklarını kısaca açıklanmaktadır. Aşağıdaki nesneler bu nesneler Ekle:  
  
-   Uygulama nesnesi  
  
-   Belge nesnesi  
  
-   Sayfa nesnesi  
  
### <a name="application-object"></a>Uygulama nesnesi  
 Microsoft.Office.Interop.Visio.Application nesnesi Visio uygulamasını temsil eder ve tüm diğer nesnelerin üst. Üyeleri, genellikle bir bütün olarak Visio uygular. Visio ortamını denetlemek için özellikleri ve yöntemleri Microsoft.Office.Interop.Visio.Application ve Microsoft.Office.Interop.Visio.ApplicationSettings nesnelerin kullanabilirsiniz.  
  
 VSTO eklenti projelerinde Microsoft.Office.Interop.Visio.Application nesnesi kullanarak erişebilirsiniz `Application` alanını `ThisAddIn` sınıfı. Daha fazla bilgi için bkz: [programlama VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  
  
### <a name="document-object"></a>Belge nesnesi  
 Programlama Visio'ya merkezi Microsoft.Office.Interop.Visio.Document nesnesidir. Çizim, şablon veya şablon dosyasını temsil eder. Visio belgelerini açın veya yeni bir belge oluşturun, Microsoft.Office.Interop.Visio.Application nesnesi Microsoft.Office.Interop.Visio.Documents koleksiyonuna eklenen yeni bir Microsoft.Office.Interop.Visio.Document nesne oluşturma .  
  
 Odaklanmış belge etkin belgeyi denir. Microsoft.Office.Interop.Visio.Application nesnesi Microsoft.Office.Interop.Visio.Application.ActiveDocument özelliği tarafından gösterilir.  
  
### <a name="page-object"></a>Sayfa nesnesi  
 Microsoft.Office.Interop.Visio.Page nesnesi bir ön plan veya arka plan sayfası çizim alanını temsil eder. Bir sayfa bir ön plan veya arka plan sayfa olup olmadığını belirlemek için Microsoft.Office.Interop.Visio.Page.Background özelliğini kullanabilirsiniz.  
  
 Şekiller oluşturmak için Microsoft.Office.Interop.Visio.Page.DrawSpline ve Microsoft.Office.Interop.Visio.Page.DrawOval yöntemleri içeren yöntemleri kullanabilirsiniz. Ayrıca, kalıp örnekleri alabilir ve Microsoft.Office.Interop.Visio.Page.Drop veya Microsoft.Office.Interop.Visio.Page.DropMany yöntemlerini kullanarak bir sayfada şekilleri yerleştirin.  
  
## <a name="using-the-visio-object-model-documentation"></a>Visio nesne modeli belgelerini kullanma  
 Visio nesne modeli hakkında tam bilgi için Visio VBA nesne modeli başvurusu başvurabilir. Visual Basic for Applications (VBA) kodundaki sunulur gibi VBA nesne modeli başvurusu Visio nesne modeline belgeler. Daha fazla bilgi için bkz: [Visio 2010 nesne modeli başvurusu](http://go.microsoft.com/fwlink/?LinkId=199775).  
  
 Tüm nesneleri ve VBA nesne modeli başvurusu üyeleri türleri ve üyeleri Visio birincil birlikte çalışma derlemesi (PIA) karşılık gelir. Örneğin, belge nesnesi VBA nesne modeli başvurusu Visio PIA Microsoft.Office.Interop.Visio.Document türüne karşılık gelir. VBA nesne modeli başvurusu kod örnekleri çoğu özellikleri, yöntemleri ve olayları sağlasa da, bunları Visual kullanarak oluşturduğunuz bir Visio VSTO eklenti projesindeki kullanmak istiyorsanız, Visual Basic veya Visual C# bu başvurusu VBA kodu çevrilmelidir Studio.  
  
> [!NOTE]  
>  Şu anda Visio birincil birlikte çalışma derlemesi için başvuru belgesi yoktur.  
  
 İlgili kod örnekleri ve Visio çözümleri oluşturmak için ek araçlar için bkz: [Visio 2010 Yazılım Geliştirme Seti](http://go.microsoft.com/fwlink/?LinkId=196501).  
  
### <a name="additional-types-in-primary-interop-assemblies"></a>Birincil birlikte çalışma derlemeleri ek türleri  
 Uygulama farklılıkları nedeniyle VBA'ya görünür olmayan birincil birlikte çalışma derlemeleri türleri bulabilirsiniz. VBA yalnızca nesneleri ve doğrudan kullanabileceğiniz üyeleri içeren Visio nesne modeline bir görünümünü sağlar. Birincil birlikte çalışma derlemeleri aynı nesne modelini sunar, ancak aynı zamanda diğer arabirimleri, sınıflar ve yönetilen kod için COM nesne modelinde Çevir üyeleri içerir. Bu ek öğeler kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.  
  
 Daha fazla bilgi için bkz: [genel bakış, sınıflar ve arabirimler Office birincil birlikte çalışma derlemeleri](http://go.microsoft.com/fwlink/?LinkId=189592) ve [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visio çözümleri](../vsto/visio-solutions.md)   
 [Visio belgeleriyle çalışma](../vsto/working-with-visio-documents.md)   
 [Visio Şekilleri ile Çalışma](../vsto/working-with-visio-shapes.md)  
  
  