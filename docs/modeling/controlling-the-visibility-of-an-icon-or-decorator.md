---
title: Bir Simgenin veya Dekoratörün Görünürlüğünü Denetleme
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76db7caa14050c924706763214e92a6ee3d68975
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748497"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Bir Simgenin veya Dekoratörün Görünürlüğünü Denetleme
*Dekoratör* , etki alanına özgü DILDE (DSL) bir şekil üzerinde görüntülenen bir simge veya metin satırıdır. Modelin özelliklerinin durumuna bağlı olarak dekoratörün görünmesini ve kaybolmasını sağlayabilirsiniz. Örneğin, bir kişiyi temsil eden bir şekil üzerinde, kişinin cinsiyetine, alt öğe sayısına ve buna bağlı olarak görünen farklı simgelere sahip olabilirsiniz.

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Bir simgenin veya dekoratörün görünürlüğünü denetleme
 Aşağıdaki yordam bir şekli ve bir etki alanı sınıfıyla eşlemesini tanımlamış olduğunuzu varsayar. Daha fazla bilgi için bkz. [etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md).

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Bir simgenin veya metin dekoratörün görünürlüğünü denetlemek için

1. DSL tanımı diyagramında, görünmesini istediğiniz simgeleri veya metin dekoratlarını şekil sınıfına ekleyin.

   1. Şekil sınıfına sağ tıklayın, **Ekle**' nin üzerine gelin ve gereken dekoratör türüne tıklayın.

   2. Dekoratör 'ın **Position** özelliğini ayarlayın. Birden çok dekoratör aynı konuma sahip olabilir. Örneğin, erkek ve kadın paylaşım için aynı konumda simgeler olabilir.

   3. Bir simge dekoratörü 'nin **varsayılan Icon** özelliğini ayarlayın.

2. DSL tanımı diyagramındaki şekil sınıfı ve alan sınıfı arasındaki gri çizgi olan diyagram öğesi haritasını seçin.

3. DSL ayrıntıları penceresindeki **dekoratör haritaları** sekmesinde bir dekoratör seçin. Örneğin, MaleDecorator.

4. **Görünürlük filtre** kutusunu işaretleyin.

5. Görünürlüğü denetlemek zorunda olan etki alanı özelliği hemen etki alanı sınıfında ise, **özelliği, filtre Için yolu** boş bırakın.

    Aksi takdirde, açılan menüye tıklayın ve özelliğin bulunduğu ilişkiye veya sınıfa gidin.

   - Bir hata raporunu önlemek için, gezinti aracında "*" ile işaretlenmiş bir ilişkide gezinmemelisiniz.

6. **Filter özelliğini** bir Domain özelliği olarak ayarlayın. Örneğin, cinsiyet.

7. **Görünürlük girişleri** listesinde, bu alan özelliğinin, dekoratörün görünür olması gereken değerlerini ekleyin. Örneğin, erkek.

8. Her simge için adımları yineleyin.

9. **Tüm şablonları dönüştürün**, derleyin ve çalıştırın ve bir test diyagramı açın.

10. Denetim özelliği değerini değiştirdiğinizde dekoratörler görünmeli ve kaybolur.

    Genellikle, görünürlüğün basit bir değer kümesinden daha karmaşık bir formül tarafından denetlenmesini istersiniz. Örneğin, bir simgenin belirli bir türdeki bağlantıların sayısına bağlı olması veya bir sayının belirli bir aralıkta olup olmamasına bağlı olması için. Bu durumda, aşağıdaki yordamı kullanın.

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Bir formüle göre dekoratörün görünürlüğünü denetlemek için

1. Etki alanı sınıfına hesaplanmış bir etki alanı özelliği ekleyin. **Özellikler** penceresinde aşağıdaki değerleri ayarlayın:

     **Igözatılabilen =** `False` **-Bu, özelliği kullanıcıdan gizler**

     **Tür =** `Calculated` **-Bu, değerini hesaplayan kodu sağlayacaksınız** .

     Örnek, **Dekoratorcontrol** **adı**

     **Tür**  =  `Boolean`

     Daha fazla bilgi için bkz. [hesaplanan ve özel depolama özellikleri](../modeling/calculated-and-custom-storage-properties.md).

2. Yeni Özellik denetimini dekoratör görünürlüğünü yapın.

    1. Etki alanı sınıfından şekle gri çizgi olan diyagram öğesi haritasını seçin. **DSL ayrıntıları** penceresinde, **dekoratormap** sekmesini açın.

    2. **Görünürlük filtre** kutusunu işaretleyin.

    3. **Filter özelliğinde**, denetim özelliği **dekoratorcontrol**' u seçin.

    4. **Görünürlük girişleri**altında `True` girin.

3. **Çözüm Gezgini** araç çubuğunda **Tüm Şablonları Dönüştür** ' e tıklayın.

4. **Yapı** menüsünde **çözüm oluştur** ' a tıklayın.

5. Görüntülenen hata raporuna çift tıklayın: "*YourClass* , Getdekoratorcontrolvalue... için bir tanım içermiyor.

     Dsl\GeneratedCode\DomainClasses.cs. üzerinde metin Düzenleyicisi açılıyor Vurgulanan hatanın üstünde bir yöntem eklemenizi isteyen bir açıklama bulunur.

6. Eksik olan ad alanı, sınıf ve yöntemi unutmayın.  Örneğin, Company. FamilyTree. Person. Getdekoratorcontrolvalue ().

7. Ayrı bir kod dosyasında, eksik yöntemi içeren kısmi bir sınıf tanımı yazın. Örneğin:

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     Modeli program kodu ile özelleştirme hakkında daha fazla bilgi için bkz. [Program kodundaki bir modeli gezinme ve güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md).

8. Çözümü yeniden derleyin ve çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Şekiller ve Bağlayıcıları Tanımlama](../modeling/defining-shapes-and-connectors.md)
- [Diyagram Üzerinde Arka Plan Görüntüsü Ayarlama](../modeling/setting-a-background-image-on-a-diagram.md)
- [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Etki Alanına Özgü Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)