---
title: "Nasıl yapılır: Excel aralıklarına program aracılığıyla renk uygulama | Microsoft Docs"
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
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
ms.assetid: a9c40229-5308-459a-9216-7e13d82c7cb5
caps.latest.revision: "47"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 141186d6c37fdbb2023650d9b43dfef57176ddda
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Nasıl yapılır: Excel Aralıklarına Program Aracılığıyla Renk Uygulama
  Bir hücre aralığı içindeki metnin rengi uygulamak için kullanmak bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi veya yerel bir Excel aralık nesnesi.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>NamedRange denetimi kullanma  
 Bu örnek için belge düzeyi özelleştirmeleri içindir.  
  
#### <a name="to-apply-color-to-a-namedrange-control"></a>NamedRange denetimi için renk uygulamak için  
  
1.  Oluşturma bir <xref:Microsoft.Office.Tools.Excel.NamedRange> A1 hücresinde denetim.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]  
  
2.  Metnin rengini ayarlama <xref:Microsoft.Office.Tools.Excel.NamedRange> denetim.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]  
  
## <a name="using-native-excel-ranges"></a>Yerel Excel aralıklarını kullanma  
  
#### <a name="to-apply-color-to-a-native-excel-range-object"></a>Yerel bir Excel aralık nesnesine renk uygulamak için  
  
1.  A1 hücresinde bir aralık oluşturun ve sonra metnin rengini ayarlayın.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Aralıklarla çalışma](../vsto/working-with-ranges.md)   
 [NamedRange denetimi](../vsto/namedrange-control.md)   
 [Nasıl yapılır: program aracılığıyla çalışma kitaplarındaki aralıklara stilleri uygulayın](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Nasıl yapılır: program aracılığıyla çalışma sayfası aralıklarına başvuran](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Genişletilmiş nesneleri kullanarak Excel'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)   
 [Office Çözümlerinde İsteğe Bağlı Parametreler](../vsto/optional-parameters-in-office-solutions.md)  
  
  