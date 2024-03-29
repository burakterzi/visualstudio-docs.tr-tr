---
title: 'CA2000: kapsamı kaybetmeden önce nesneleri atma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 89e0797afdcf299bb466018049a6d1217c5ad2dd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666152"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: Kapsamı kaybetmeden önce verileri atın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|Kategori|Microsoft. güvenilirliği|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 @No__t_0 türünün yerel bir nesnesi oluşturuldu ancak nesnenin tüm başvuruları kapsam dışına çıkarılmadan nesne atılamaz.

## <a name="rule-description"></a>Kural Tanımı
 Bir atılabilir nesnesi, tüm başvuruları kapsam dışına çıkarılmadan önce açıkça atılmaz, çöp toplayıcı nesnenin sonlandırıcısını çalıştırdığında, nesne belirsiz bir zamanda silinir. Nesnenin sonlandırıcısını çalışmasını engelleyecek olağanüstü bir olay ortaya çıkabilecek için, bunun yerine nesne açıkça atılmalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, tüm başvuruları kapsam dışına önce nesne üzerinde <xref:System.IDisposable.Dispose%2A> çağırın.

 @No__t_3 uygulayan nesneleri kaydırmak için `using` deyimin ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `Using`) kullanabileceğinizi unutmayın. Bu şekilde Sarmalanan nesneler, `using` bloğunun kapandığı zaman otomatik olarak silinir.

 Aşağıda, using ifadesinin IDisposable nesnelerini korumak için yeterli olmadığı ve CA2000 oluşmasına neden olabileceği bazı durumlar verilmiştir.

- Bir atılabilir nesnesi döndürmek için, nesnenin using bloğu dışında bir try/finally bloğunda oluşturulması gerekir.

- Bir atılabilir nesnesinin üyelerini başlatmak, using ifadesinin oluşturucusunda yapılmamalıdır.

- Yalnızca bir özel durum işleyicisi tarafından korunan oluşturucular iç içe. Örneğin,

    ```
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
    { ... }
    ```

     StreamReader nesnesinin oluşturulmasından kaynaklanan bir hata, FILESTREAM nesnesinin hiçbir şekilde kapatılmadığı için CA2000 oluşmasına neden olur.

- Dinamik nesneler, IDisposable nesnelerinin Dispose modelini uygulamak için bir gölge nesnesi kullanmalıdır.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Nesnenizde `Dispose` gibi <xref:System.IO.Stream.Close%2A> çağıran bir yöntem çağırmadığınız sürece veya uyarıyı oluşturan yöntem nesnenizi sarmalayan bir IDisposable nesnesi getirmediği sürece bu kuraldan bir uyarıyı bastırmayın.

## <a name="related-rules"></a>İlgili kurallar
 [CA2213: Atılabilen alanlar atılmalıdır](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2202: Nesneleri birden çok kez atmayın](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>Örnek
 Atılabilir nesnesi döndüren bir yöntem uygularsanız, nesnenin atılmış olduğundan emin olmak için catch bloğu olmayan bir try/finally bloğu kullanın. Bir try/finally bloğu kullanarak, özel durumların hata noktasında ortaya çıkmasına ve nesnenin atıldığından emin olmanızı sağlayabilirsiniz.

 OpenPort1 yönteminde, ISerializable nesne SerialPort 'u açma çağrısı veya SomeMethod çağrısı başarısız olabilir. Bu uygulamada bir CA2000 uyarısı oluşturulur.

 OpenPort2 yönteminde, iki SerialPort nesnesi bildirilmiştir ve null olarak ayarlanır:

- `tempPort`, yöntem işlemlerinin başarılı olduğunu test etmek için kullanılır.

- `port`, yöntemin dönüş değeri için kullanılır.

  @No__t_0 oluşturulur ve bir `try` bloğunda açılır ve diğer tüm gerekli işler aynı `try` bloğunda gerçekleştirilir. @No__t_0 bloğunun sonunda, açılan bağlantı noktası döndürülecek `port` nesnesine atanır ve `tempPort` nesnesi `null` olarak ayarlanır.

  @No__t_0 bloğu `tempPort` değerini denetler. Null değilse, yöntemdeki bir işlem başarısız olur ve tüm kaynakların serbest olduğundan emin olmak için `tempPort` kapalıdır. Döndürülen bağlantı noktası nesnesi, metodun işlemleri başarılı olursa Açık SerialPort nesnesini içerir veya bir işlem başarısız olursa null olur.

  [!code-csharp[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/cs/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.cs#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vb#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vboverflow.vb#1)]

## <a name="example"></a>Örnek
 Varsayılan olarak, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] derleyicisinde tüm aritmetik işleçler taşma için denetlenir. Bu nedenle, herhangi bir Visual Basic aritmetik işlemi bir <xref:System.OverflowException> oluşturabilir. Bu, CA2000 gibi kurallarda beklenmeyen ihlallere neden olabilir. Örneğin, Visual Basic derleyici, StreamReader atılmasına neden olacak bir özel durum oluşturabilecek ekleme için bir taşma denetimi yönergesi yaydığı için, aşağıdaki CreateReader1 işlevi bir CA2000 ihlaline neden olur.

 Bunu yapmak için, projenizdeki Visual Basic derleyicisinden taşma denetimleri yaymayı devre dışı bırakabilir veya kodunuzu aşağıdaki CreateReader2 işlevinde olarak değiştirebilirsiniz.

 Taşma denetimlerinin yayışını devre dışı bırakmak için Çözüm Gezgini ' de proje adına sağ tıklayın ve ardından **Özellikler**' e tıklayın. **Derle**' ye tıklayın, **Gelişmiş derleme seçenekleri**' ne tıklayın ve ardından **tamsayı taşma denetimlerini kaldır**' ı işaretleyin.

<!-- TODO: review snippet reference  [!CODE [FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1](FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1)]  -->

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.IDisposable> [Dispose deseninin](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)