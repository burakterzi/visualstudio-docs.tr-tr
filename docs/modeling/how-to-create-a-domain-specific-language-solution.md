---
title: 'Nasıl yapılır: Etki Alanına Özgü Dil Çözümü Oluşturma'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6d4a19143ccde160a455a8247d10e5cc391e78c
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985122"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Nasıl yapılır: Etki Alanına Özgü Dil Çözümü Oluşturma
Özel bir Visual Studio çözümü kullanılarak, etki alanına özgü dil (DSL) oluşturulur.

## <a name="prerequisites"></a>Prerequisites

Bu yordamı başlatabilmeniz için önce şu bileşenleri yükleyebilirsiniz:

- Visual Studio
- Visual Studio SDK ( **Visual Studio uzantısı geliştirme** iş yükünün parçası olarak yüklenir)
- Modelleme SDK 'Sı (Visual Studio bileşeni olarak yüklenir)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="creating-a-domain-specific-language-solution"></a>Etki alanına özgü dil çözümü oluşturma

1. Yeni bir **alana özgü dil Tasarımcısı** PROJESI oluşturarak dsl Sihirbazı 'nı başlatın.

   > [!NOTE]
   > Tercihen, kod oluşturmak için kullanılabilecek proje için seçtiğiniz adın geçerli bir görsel C# tanımlayıcı olması gerekir.

   ::: moniker range="vs-2017"

   ![DSL oluştur iletişim kutusu](../modeling/media/create_dsldialog.png)

   ::: moniker-end

2. DSL şablonu seçin.

    **Etki alanına özgü dil seçeneklerini seç** sayfasında, **en az dil**gibi çözüm şablonlarından birini seçin. Oluşturmak istediğiniz DSL 'ye benzer bir şablon seçin.

    Çözüm şablonları hakkında daha fazla bilgi için bkz. [etki alanına özgü dil çözümü şablonu seçme](../modeling/choosing-a-domain-specific-language-solution-template.md).

3. **Dosya Uzantısı** sayfasında bir dosya adı uzantısı girin. Bu, bilgisayarınızda ve DSL 'yi yüklemek istediğiniz herhangi bir bilgisayarda benzersiz olmalıdır. **Hiçbir uygulama veya Visual Studio Düzenleyicisi bu uzantıyı kullanmamalıdır**iletisini görmeniz gerekir.

   - Tam yüklenmemiş olan önceki deneysel DSLs 'de dosya adı uzantısını kullandıysanız, Visual Studio SDK menüsünde bulunan **deneysel örneği Sıfırla** aracını kullanarak bunları temizleyebilirsiniz.

   - Bu dosya uzantısını kullanan başka bir Visual Studio uzantısı bilgisayarınızda tamamen yüklüyse, uygulamayı kaldırmayı düşünün. **Araçlar** menüsünde, **Uzantı Yöneticisi**' ne tıklayın.

4. Sihirbazın kalan sayfalarındaki alanları inceleyin ve gerekirse ayarlayın. Ayarlarla ilgili memnun olduğunuzda **son**' a tıklayın. Ayarlar hakkında daha fazla bilgi için bkz. [DSL Tasarımcısı Sihirbazı sayfaları](#settings).

    Sihirbaz, **DSL** ve **DslPackage**adlı iki projeye sahip bir çözüm oluşturur.

   > [!NOTE]
   > Güvenilmeyen kaynaklardan metin şablonlarını çalıştıracağınızı belirten bir ileti görürseniz, **Tamam**' a tıklayın. Bu iletiyi tekrar görünmeyecek şekilde ayarlayabilirsiniz.

## <a name="settings"></a>DSL Tasarımcısı Sihirbazı sayfaları
 Birçok alandan birini varsayılan değerlerinden farklı bırakabilirsiniz. Ancak, dosya uzantısı alanını ayarladığınızdan emin olun.

### <a name="solution-settings-page"></a>Çözüm ayarları sayfası
 **Etki alanına özgü dile hangi şablonu temel almak istiyorsunuz?**
Oluşturmak istediğiniz DSL 'ye benzer bir şablon seçin. Farklı şablonlar, uygun başlangıç noktaları sağlar. Bir çözüm şablonu seçtiğinizde, sihirbaz bir açıklama görüntüler. Çözüm şablonları hakkında daha fazla bilgi için bkz. [etki alanına özgü dil çözümü şablonu seçme](../modeling/choosing-a-domain-specific-language-solution-template.md).

 **Etki alanına özgü dilinizi ne adlandırmak istiyorsunuz?**
Çözüm adı varsayılan olarak belirlenmiştir. Kod bu değerden oluşturulur. C# Sınıf adı olarak geçerli olmalıdır.

### <a name="file-extension-page"></a>Dosya uzantısı sayfası
 **Model dosyalarının kullanması gereken uzantı nedir?**
Yeni bir dosya uzantısı yazın.

 Bu dosya uzantısının bu bilgisayarda kullanılmak üzere zaten kayıtlı olmadığından emin olun:

 **Bu uzantıyı işlemek için kayıtlı diğer araç ve uygulamalar**bölümüne bakın. **Hiçbir uygulama veya Visual Studio Düzenleyicisi tarafından bu uzantıyı kullanan**bir ileti görürseniz, bu dosya uzantısını kullanabilirsiniz.

 Araçların veya paketlerin bir listesini görürseniz, aşağıdakilerden birini yapmalısınız:

- Farklı bir dosya uzantısı yazın.

     \- veya-

- Visual Studio Deneysel örneğini sıfırlayın. Bu, daha önce oluşturduğunuz tüm DSLs 'lerin kaydını siler. **Başlat** menüsünde, **tüm programlar**, **Microsoft Visual Studio 2010 SDK**ve **araçlar**' a tıklayın ve ardından **Microsoft Visual Studio 2010 Deneysel örneğini sıfırlayın**. Yeniden kullanmak istediğiniz tüm diğer DSLs 'leri yeniden oluşturabilirsiniz.

     \- veya-

- Bu dosya uzantısını kullanan bir Visual Studio uzantısı bilgisayarınızda tamamen yüklüyse, kaldırın. **Araçlar** menüsünde, **Uzantı Yöneticisi**' ne tıklayın.

### <a name="product-settings-page"></a>Ürün ayarları sayfası
 **Yeni etki alanına özgü dilin ait olduğu ürünün adı nedir?**
DSL adını varsayılan olarak alır.

 Bu değer, bu dosya uzantısına sahip dosyaları anlatmak için Windows Gezgini 'nde (veya dosya Gezgini) kullanılır.

 **Ürünün ait olduğu şirketin adı nedir?**
Şirketinizin adı.

 Bu değer DSL paketinizin AssemblyInfo özelliklerine eklenir.

 **Bu çözümdeki projeler için kök ad alanı nedir?**
Bu, varsayılan olarak şirketinizden ve ürün adınızdan oluşan bir addır.

### <a name="signing-page"></a>İmzalama sayfası
 **Tanımlayıcı ad anahtar dosyası oluşturma** Varsayılan seçenek, DSL derlemenizi imzalamak için yeni bir anahtar oluşturmaktır.

 **Mevcut tanımlayıcı ad anahtarını kullan** DSL 'nizi başka bir derlemeyle bütünleştirmek istiyorsanız bu seçeneği kullanın.

 Tanımlayıcı adlandırma hakkında daha fazla bilgi için bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](/dotnet/standard/assembly/create-use-strong-named).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
- [Alana Özgü Dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
