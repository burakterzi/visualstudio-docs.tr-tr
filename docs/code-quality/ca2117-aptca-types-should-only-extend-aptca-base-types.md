---
title: "CA2117: APTCA türleri yalnızca APTCA taban türlerini genişletmelidir | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: be208c156e8710b6aa6b2821a5a85131f3c2e4b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: APTCA türleri yalnızca APTCA taban türlerini genişletmelidir
|||  
|-|-|  
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|  
|CheckId|CA2117|  
|Kategori|Microsoft.Security|  
|Yeni Değişiklik|Yeni|  
  
## <a name="cause"></a>Sebep  
 Bir derleme bir ortak veya korumalı türünde <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> özniteliğine sahip bir derlemede bildirilen bir türü özniteliği devralır.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Varsayılan olarak, güçlü adlara sahip derlemelerde ortak veya korumalı türü örtük olarak tarafından korunan bir <xref:System.Security.Permissions.SecurityAction.InheritanceDemand> için tam güven. Tanımlayıcı adlı derlemeler ile işaretlenen <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) özniteliği bu koruma sahip değil. Öznitelik devralma isteğe bağlı devre dışı bırakır. Bu derlemede devralınabilir bildirilen tam güven yok türleri tarafından sunulan türleri sağlar.  
  
 APTCA özniteliği üzerinde tam olarak güvenilir bir derleme var ve derlemesinde türünü kısmen güvenilen arayanlara izin vermeyen bir türünden devralan bir güvenlik açığından yararlanma mümkün olur. İki yazarsa `T1` ve `T2` aşağıdaki koşullara uyan, zararlı çağıranlar türü kullanabileceğiniz `T1` korur örtük tam güven devralma talep atlamak için `T2`:  
  
-   `T1`Ortak tür APTCA özniteliği tam güvenilen bir derlemede bildirildi.  
  
-   `T1`bir türünden devralan `T2` kendi derleme dışında.  
  
-   `T2`kişinin derleme APTCA özniteliği yok ve bu nedenle, kısmen güvenilen derlemelerindeki tarafından devralınabilir olmamalıdır.  
  
 Kısmen güvenilen türü `X` gelen devralabilirsiniz `T1`, sağlayan, erişim bildirilen devralınan üyeleri için `T2`. Çünkü `T2` APTCA özniteliği, hemen türetilmiş türü yok (`T1`) için tam güven; bir devralma talebi karşılamak gerekir `T1` tam güvene sahip ve bu nedenle bu onay karşılar. Güvenlik riski çünkü `X` korur devralma talep çağıran katılmayan `T2` güvenilmeyen sınıflara gelen. Bu nedenle, APTCA özniteliği türleriyle özniteliğine sahip olmayan türlerini genişletmelidir değil.  
  
 Başka bir güvenlik sorunu ve daha sık karşılaşılan bir belki de türetilmiş bir tür olan (`T1`) Programcı hata tam güven gerektiren türünden korumalı üyeleri hale getirebilir (`T2`). Bu durumda, güvenilmeyen arayanlar yalnızca tam olarak güvenilmeyen türleri için kullanılabilir olması gerektiğini bilgilere erişin.  
  
## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?  
 İhlali tarafından bildirilen türü APTCA özniteliği gerektirmeyen bir derlemede ise kaldırın.  
  
 APTCA özniteliği gerekiyorsa, tam güven için bir devralma talep türüne ekleyin. Bu, güvenilmeyen türlerine göre devralma karşı korur.  
  
 Derlemelere ihlali tarafından bildirilen temel türleri APTCA özniteliği ekleyerek bir ihlali düzeltmek mümkündür. Bunu, ilk derlemelerde tüm kod ve derlemelerini bağlıdır tüm kod bir yoğun güvenlik incelemesi gerçekleştirme olmadan yapmayın.  
  
## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında  
 Bu kural bir uyarıdan güvenle gizlemek için türü tarafından kullanıma sunulan korumalı üyeleri doğrudan veya dolaylı olarak hassas bilgileri, işlemler veya zararlı bir şekilde kullanılabilir kaynaklara erişmek güvenilmeyen arayanlara izin vermediğinden emin olmalısınız.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bu kural tarafından algılanan güvenlik açığı göstermek için iki derleme ve test uygulaması kullanır. İlk derleme APTCA özniteliği yok ve kısmen güvenilen türlerine göre devralınabilir olmamalıdır (tarafından temsil edilen `T2` önceki tartışma içinde).  
  
 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]  
  
## <a name="example"></a>Örnek  
 Tarafından temsil edilen ikinci derleme `T1` önceki tartışmada tam olarak güvenilir ve kısmen güvenilen arayanlara izin verir.  
  
 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]  
  
## <a name="example"></a>Örnek  
 Tarafından temsil edilen test türü `X` önceki tartışmada kısmen güvenilen bir derlemedir.  
  
 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]  
  
 Bu örnek şu çıkışı üretir.  
  
 **Shady glen adresindeki karşılayan 22/2/2003 12:00:00 AM!**  
**Test: Güneşli çayırı**  
**Güneşli çayırı adresindeki karşılayan 22/2/2003 12:00:00 AM!**   
## <a name="related-rules"></a>İlgili kuralları  
 [CA2116Ç APTCA yöntemleri yalnızca APTCA yöntemlerini çağırmalıdır](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenli kodlama yönergeleri](/dotnet/standard/security/secure-coding-guidelines)   
 [Kısmen güvenilen koddan kitaplıkları kullanma](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)   