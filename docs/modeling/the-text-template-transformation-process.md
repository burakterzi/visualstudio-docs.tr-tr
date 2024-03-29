---
title: Metin Şablonu Dönüştürme Süreci
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 518c06f8630ad9fa7742f7b3e85ac27263cd0a86
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72605800"
---
# <a name="the-text-template-transformation-process"></a>Metin Şablonu Dönüştürme Süreci
Metin şablonu dönüştürme işlemi, girdi olarak bir metin şablonu dosyası alır ve çıktı olarak yeni bir metin dosyası oluşturur. Örneğin, Visual Basic veya C# kod oluşturmak için metin şablonlarını kullanabilir veya bir HTML raporu oluşturabilirsiniz.

 Bu işlemin parçası olan üç bileşen: motor, ana bilgisayar ve yönerge işlemcileri. Motor işlemi denetler; çıktı dosyasını oluşturmak için konak ve yönerge işlemcisi ile etkileşime girer. Ana bilgisayar, ortam ile dosya ve derleme bulma gibi herhangi bir etkileşim sağlar. Yönerge işlemcisi, bir XML dosyasından veya bir veritabanından veri okuma gibi işlevler ekler.

 Metin şablonu dönüştürme işlemi iki adımda gerçekleştirilir. İlk olarak, altyapı oluşturulan dönüştürme sınıfı olarak bilinen geçici bir sınıf oluşturur. Bu sınıf, yönergeler ve denetim blokları tarafından oluşturulan kodu içerir. Bundan sonra motor, çıktı dosyasını oluşturmak için oluşturulan dönüştürme sınıfını derler ve yürütür.

## <a name="components"></a>Bileşenler

|Bileşen|Açıklama|Özelleştirilebilir (Evet/Hayır)|
|-|-|-|
|Altyapısına|Motor bileşeni, metin şablonu dönüştürme işlemini denetler|Hayır.|
|Ana bilgisayar|Konak, motor ve Kullanıcı ortamı arasındaki arabirimdir. Visual Studio, metin dönüştürme sürecinin bir konağından oluşur.|Evet. Özel bir ana bilgisayar yazabilirsiniz.|
|Yönerge Işlemcileri|Yönerge işlemcileri, metin şablonlarındaki yönergeleri işleyen sınıflardır. Giriş kaynağından bir metin şablonuna veri sağlamak için yönergelerini kullanabilirsiniz.|Evet. Özel yönerge işlemcileri yazabilirsiniz|

## <a name="the-engine"></a>Motor
 Motor, şablonu konaktan bir dize olarak alır ve bu, dönüştürme işleminde kullanılan tüm dosyaları işler. Altyapı daha sonra ana bilgisayarın özel yönerge işlemcileri ve ortamın diğer yönlerini bulmasını ister. Ardından motor oluşturulan dönüştürme sınıfını derler ve çalıştırır. Altyapı, oluşturulan metni, normalde metin dosyasına kaydeden ana bilgisayara döndürür.

## <a name="the-host"></a>Konak
 Ana bilgisayar, dönüştürme işlemi dışındaki ortamla ilgili her şeyden sorumludur, örneğin:

- Motor veya yönerge işlemcisi tarafından istenen metin ve ikili dosyaları bulma. Konak, derlemeleri bulmak için dizinlerde ve genel derleme önbelleğinde arama yapabilir. Konak, altyapının özel yönerge işlemci kodunu bulabilir. Ana bilgisayar ayrıca metin dosyalarını bulup okuyabilir ve içeriklerini dizeler olarak döndürebilir.

- Altyapı tarafından oluşturulan dönüştürme sınıfını oluşturmak için kullanılan standart derleme ve ad alanları listesi sağlama.

- Altyapı derlendiğinde ve oluşturulan dönüştürme sınıfını yürüttüğünde kullanılan uygulama etki alanını sağlama. Ana bilgisayar uygulamasının şablon kodundaki hatalardan korunması için ayrı bir uygulama etki alanı kullanılır.

- Oluşturulan çıkış dosyası yazılıyor.

- Oluşturulan çıkış dosyası için varsayılan uzantı ayarlanıyor.

- Metin şablonu dönüştürme hatalarını işleme. Örneğin, ana bilgisayar, hataları Kullanıcı arabiriminde görüntüleyebilir veya bir dosyaya yazabilir. (Visual Studio 'da hatalar hata Iletisi penceresinde görüntülenir.)

- Bir Kullanıcı bir değer sağlamadan bir yönerge çağrılırsa gerekli bir parametre değeri sağlama. Yönerge işlemcisi, yönergenin adını ve parametresini belirtebilir ve bir tane varsa konağın varsayılan değer sağlamasını ister.

## <a name="directives-and-directive-processors"></a>Yönergeler ve yönerge Işlemcileri
 Yönerge, metin şablonunuzda bir komuttur. Oluşturma işlemine parametreler sağlar. Genellikle yönergeler, modelin kaynak ve türünü ya da başka bir girişi ve çıkış dosyasının dosya adı uzantısını tanımlar.

 Yönerge işlemcisi bir veya daha fazla yönerge işleyebilir. Bir şablonu dönüştürdüğünüzde, şablonunuzda yönergeler ile ilgilenebilmeniz için bir yönerge işlemcisi yüklemiş olmanız gerekir.

 Yönergeler oluşturulan dönüştürme sınıfına kod ekleyerek çalışır. Bir metin şablonundan yönergeleri çağırabilirsiniz ve altyapı oluşturulan dönüştürme sınıfını oluşturduğunda tüm yönerge çağrılarını işler. Bir yönergeyi başarıyla çağırdığınızda, metin şablonunuzda yazdığınız kodun geri kalanı, yönergesinin sağladığı işlevselliğe bağlı olabilir. Örneğin, şablonunuzda `import` yönergesine aşağıdaki çağrıyı yapabilirsiniz:

 `<#@ import namespace="System.Text" #>`

 Standart yönerge işlemcisi bunu, oluşturulan dönüştürme sınıfındaki bir `using` ifadesine dönüştürür. Daha sonra şablon kodunuzun geri kalanında `StringBuilder` sınıfını `System.Text.StringBuilder` olarak nitelemeden kullanabilirsiniz.