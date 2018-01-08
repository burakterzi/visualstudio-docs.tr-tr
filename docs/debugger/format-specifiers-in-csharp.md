---
title: "Biçim belirticiler hata ayıklayıcısında (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C#], formatting values
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- specifiers, watch variable format
- QuickWatch dialog box, format specifiers in C#
- specifiers
- watch variable symbols
- Watch window, format specifiers in C#
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: c1186da8d276796816d8531963f746f222526b6d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısında C# içindeki Biçim belirticileri
İçinde bir değer görüntülenir biçimini değiştirebilirsiniz **izleme** penceresi biçim belirticilerini kullanma. İçindeki Biçim belirticileri de kullanabilirsiniz **hemen** penceresinde **komutu** penceresinde ve hatta kaynak windows. Bu windows deyimde üzerinde duraklatmak, sonuç DataTip içinde görünür. DataTips DataTip görüntüsündeki biçim belirticisi yansıtır.  
  
 Bir biçim belirticisi kullanmak için virgül ve ifadeyi yazın. Sonra virgül, uygun belirleyici ekleyin.  
  
## <a name="using-format-specifiers"></a>Biçim belirticilerini kullanma  
 Aşağıdaki kodu varsa:  
  
```CSharp  
{  
        int my_var1 = 0x0065;  
        int my_var2 = 0x0066;  
        int my_var3 = 0x0067;  
}  
```  
  
 Ekleme `my_var1` Gözcü penceresi değişken (hata ayıklama, **hata ayıklama > Windows > İzleme > İzleme 1**) ve görüntü onaltılık-ayarlayın (içinde **izleme** penceresinde, değişkeni sağ tıklayın ve seçin **onaltılı görüntü**). Şimdi **izleme** penceresi gösterir 0x0065 değeri içerir. Bkz sonra değişken adı, Ad sütununda, onaltılık bir tamsayı yerine ondalık bir tamsayı olarak ifade bu değere ondalık biçim belirteci eklemek için: **, d**. Değer sütunu artık ondalık değer 101 görüntüler  
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## <a name="format-specifiers"></a>Biçim belirticiler  
 Aşağıdaki tablo hata ayıklayıcı tarafından tanınan C# biçim belirticileri gösterir.  
  
|Belirleyici|Biçimi|Özgün izleme değeri|Görüntüler|  
|---------------|------------|--------------------------|--------------|  
|AC|Bir ifadenin değerlendirmesine zorlar. Örtük değerlendirme özellikleri ve dolaylı işlev çağrıları devre dışı bırakıldığında bu yararlı olabilir.|"Dolaylı İşlev değerlendirmesi kullanıcı tarafından devre dışı" iletisi|\<Değer >|  
|d|ondalık tamsayı|0x0065|101|  
|dinamik|Dinamik bir görünümü kullanarak belirtilen nesneyi görüntüler|Dinamik görünüm dahil olmak üzere bu nesnenin tüm üyelerini görüntüler|Yalnızca dinamik görünümü görüntüler|  
|h|onaltılık tamsayı|61541|0x0000F065|  
|Nq|tırnak işaretleri olmadan dize|"Dize my"|My dize|  
|gizli|Tüm genel ve genel olmayan üyeler görüntüler|Görüntüler Genel üyeler|Tüm üyeler görüntüler|  
|Ham|Ham öğesi düğümünde göründüğü gibi öğesi görüntüler. Proxy nesneleri yalnızca geçerli.|Sözlük\<T >|Sözlük ham görünümünü\<T >|  
|sonuçlar|Değişkeninin IEnumerable veya IEnumerable arabirimini uygulayan bir tür ile kullanılan\<T >, genellikle bir sorgu ifadesi sonucu. Sorgu sonucu içeren üyelerini görüntüler.|Tüm üyelerini görüntüler.|Üyeleri karşılamak görüntüler sorgunun koşullarını.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme ve QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Otomatik değişkenler ve yerel Windows](../debugger/autos-and-locals-windows.md)