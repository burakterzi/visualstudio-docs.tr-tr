---
title: "Nasıl yapılır: Word belgelerini ve Excel çalışma kitaplarına Eylemler bölmesi ekleme | Microsoft Docs"
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
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
ms.assetid: cea3c2b6-9364-4134-b812-50888ad8bd76
caps.latest.revision: "63"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: dc97f27ce59f101047cc48022d682faebf253c9d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Nasıl Yapılır: Word Belgelerine veya Excel Çalışma Kitaplarına Eylemler Bölmesi Ekleme
  Microsoft Office Word belgesine veya Microsoft Excel çalışma kitabına Eylemler bölmesi eklemek için önce bir Windows Forms kullanıcı denetimi oluşturun. Ardından, kullanıcı denetimi Ekle <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> özelliği `ThisDocument.ActionsPane` alan (Word) veya `ThisWorkbook.ActionsPane` projenizdeki alanı (Excel).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz: [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="creating-the-user-control"></a>Kullanıcı denetimi oluşturma  
 Aşağıdaki yordam, kullanıcı denetimi Word'de oluşturma veya Excel projesi gösterir. Ayrıca bir düğmeye tıklandığında belge veya çalışma kitabını metin yazar kullanıcı denetimini ekler.  
  
#### <a name="to-create-the-user-control"></a>Kullanıcı denetimi oluşturmak için  
  
1.  Word veya Excel belge düzeyi projenizi Visual Studio'da açın.  
  
2.  Üzerinde **proje** menüsünde tıklatın **Yeni Öğe Ekle**.  
  
3.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **Eylemler bölmesi denetimi**, adlandırın **HelloControl**, tıklatıp **Ekle**.  
  
    > [!NOTE]  
    >  Alternatif olarak ekleyebileceğiniz bir **kullanıcı denetimi** projenize öğesi. Tarafından oluşturulan sınıflar **Eylemler bölmesi denetimi** ve **kullanıcı denetimi** öğeleri işlevsel olarak eşdeğerdir.  
  
4.  Gelen **Windows Forms** sekmesinde **araç kutusu,** sürükleyin bir **düğmesini** denetimi üzerine denetim.  
  
    > [!NOTE]  
    >  Denetim Tasarımcısı'nda görünür durumda değilse, çift tıklayarak **HelloControl** içinde **Çözüm Gezgini**.  
  
5.  Koda ekleme <xref:System.Windows.Forms.Control.Click> düğmesi olay işleyicisi. Aşağıdaki örnek, Microsoft Office Word belgesi için kodu gösterir.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]  
  
6.  C# ' ta düğmesini tıklatın için bir olay işleyicisi eklemeniz gerekir. Bu kodu koyabilirsiniz `HelloControl` çağrısından sonra Oluşturucusu `IntializeComponent`.  
  
     Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]  
  
## <a name="adding-the-user-control-to-the-actions-pane"></a>Kullanıcı denetimi Eylemler bölmesi ekleme  
 Eylemler bölmesini göstermek için kullanıcı denetimi Ekle <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> özelliği `ThisDocument.ActionsPane` alan (Word) veya `ThisWorkbook.ActionsPane` alan (Excel).  
  
#### <a name="to-add-the-user-control-to-the-actions-pane"></a>Kullanıcı denetimi Eylemler bölmesine eklemek için  
  
1.  Aşağıdaki kodu ekleyin `ThisDocument` veya `ThisWorkbook` sınıfına sınıf düzeyi bildirimi olarak (Bu kodu bir yönteme eklemeyin).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]  
  
2.  Aşağıdaki kodu ekleyin `ThisDocument_Startup` olay işleyicisi `ThisDocument` sınıfı veya `ThisWorkbook_Startup` olay işleyicisi `ThisWorkbook` sınıfı.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)   
 [İzlenecek yol: Eylemler bölmesinden belgeye metin ekleme](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Nasıl yapılır: Eylemler bölmesindeki denetim düzenini yönetme](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [İzlenecek Yol: Eylemler Bölmesinden Belgeye Metin Ekleme](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  