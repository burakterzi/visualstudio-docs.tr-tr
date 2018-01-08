---
title: "Yönetilen kod için genelleştirme kuralları kural kümesi | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 07a2e8da87eb486f8247a79263ec371a8fd4afc5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Yönetilen kod için Genelleştirme Kuralları kural kümesi
Microsoft Genelleştirme kuralları kural kümesi farklı diller, yerel ayarlar ve kültürlere doğru görünmesini uygulamanızdaki verileri engelleyebilecek sorunları odaklanmak için kullanabilirsiniz. Bu kural, uygulama globalized, yerelleştirilmiş ise, kümesi veya her ikisini de içermelidir.  
  
|Kural|Açıklama|  
|----------|-----------------|  
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|MessageBoxOptions belirtme|  
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Yinelenen hızlandırıcılardan kaçının|  
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Yerel özel dizeleri değil stillerinizin yapın|  
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Değişmez değerler yerelleştirilmiş parametreler olarak geçmeyin|  
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|CultureInfo belirtme|  
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|Iformatprovider belirtme|  
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Veri türleri için kümesi yerel ayar|  
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|StringComparison belirtme|  
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Dizeleri büyük harfe normalleştirin|  
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Sıralı StringComparison kullanın|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|P/Invoke dize bağımsız değişkenleri için sıralama belirtin|