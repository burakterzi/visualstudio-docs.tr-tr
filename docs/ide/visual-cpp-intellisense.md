---
title: Visual C++ IntelliSense | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fffb892efdbe3ad2731de5b0b81f6e59f237f884
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="visual-c-intellisense"></a>Visual C++ IntelliSense

C++ için IntelliSense de tek başına dosyaları, C++ projesinin bir parçası olan dosyalar için kullanılabilir. Bir Android veya iOS bağlamında olduğunda bile platformlar arası projelerinde IntelliSense özelliklerinden bazıları .cpp ve .c dosyaları paylaşılan kod projesinde, kullanılabilir.

## <a name="intellisense-features-in-c"></a>C++'ta IntelliSense özellikleri

IntelliSense kodlama daha kullanışlı hale özellikler kümesi için verilen bir addır. Farklı kişilerin ne kullanışlı olduğu konusunda farklı fikirleri sahip olduğundan, neredeyse tüm IntelliSense özellikleri etkinleştirilebilir veya devre dışı **metin düzenleyici, C/C++, Gelişmiş** özellik sayfası.

![Araçlar, Seçenekler, metin düzenleyici, C &#47; C &#43; &#43; Gelişmiş](../ide/media/sintellisensecpptoolsoptions.PNG "sIntelliSenseCppToolsOptions")

IntelliSense erişmek için menü öğeleri ve aşağıdaki görüntüde gösterilen klavye kısayollarını kullanabilirsiniz.

![Visual C# 43; &#43; IntelliSense menü](../ide/media/vs2015_cpp_intellisense_menu.png "vs2015_cpp_intellisense_menu")

### <a name="statement-completion-and-member-list"></a>Deyim tamamlama ve üye listesi

Bir anahtar sözcük, türü, işlev, değişken adı veya derleyicisi tanır başka bir program öğesi yazmaya başladığınızda, word tamamlamanız Düzenleyici sunar

Simgeler ve anlamlarını listesi için bkz: [sınıf görünümü ve Nesne Tarayıcısı simgeleri](../ide/class-view-and-object-browser-icons.md).

![Visual C# 43; &#43; Tam sözcük penceresi](../ide/media/vs2015_cpp_complete_word.png "vs2015_cpp_complete_word")

Üye listesi çağrılan ilk kez geçerli bağlam için erişilebilir üyeleri yalnızca gösterir. Kullanırsanız **Ctrl + J** bundan sonra erişilebilirlik bağımsız olarak tüm üyeleri gösterir. Üçüncü bir kez çağırma durumunda bile daha geniş bir program öğeleri listesi gösterilir. Deyim tamamlama kapatabilirsiniz **C/C++ genel seçenekleri** sayfası.

![Visual C# 43; &#43; Üye listesi](../ide/media/vs2015_cpp_list_members.png "vs2015_cpp_list_members")

### <a name="parameter-help"></a>Parametre Yardım

Bir sınıf şablonu değişken bildirimi bir işlev çağrısı veya açılı ayraç açılan parantez yazdığınızda, düzenleyici küçük bir pencere işlevi veya oluşturucusu her yüklemesini parametre türleri ile gösterir. İmleç konumu--temel "geçerli"--kalın parametresidir. Deyim tamamlama kapatabilirsiniz **C/C++ genel seçenekleri** sayfası.

![Visual C# 43; &#43; Parametre Yardım](../ide/media/vs_2015_cpp_param_help.png "vs_2015_cpp_param_help")

### <a name="quick-info"></a>Hızlı Bilgi

Fare imlecini bir değişken geldiğinizde türü bilgilerini gösteren satır içi ve türünün tanımlandığı üstbilgi küçük bir pencere görüntülenir. İşlev imzası görmek için işlev çağrısı gelin. Hızlı bilgisini kapatabilirsiniz **metin düzenleyici, C/C++, Gelişmiş** sayfası.

![Visual C# 43; &#43; Quıckınfo](../ide/media/vs2015_cpp_quickinfo.png "vs2015_cpp_quickInfo")

### <a name="error-squiggles"></a>Hata dalgalı çizgiler

Bir program öğesi (değişkeni, anahtar sözcüğü, kuşak, tür adı ve benzeri) altında dalgalı çizgiler dikkatinizi bir hata veya olası hata kodu çağırın. Hala uygulama yazmak ihtiyacınız olduğunu anımsatmak için bir iletme bildirimi yazdığınızda yeşil dalgalı görüntülenir. Olduğunda mor dalgalı paylaşılan bir proje Android bağlamında bir hata olacaktır Windows bağlamında çalışan, ancak bir şey girin, örneğin şu anda etkin değil, kodda bir hata görüntülenir. Derleyici hatası veya uyarısı uğraşmanız gereken active kodda kırmızı dalgalı gösterir.

![Visual C# 43; &#43; hata dalgalı çizgiler](../ide/media/vs2015_cpp_error_quiggles.png "vs2015_cpp_error_quiggles")

### <a name="code-colorization-and-fonts"></a>Kod renklendirme ve yazı tipleri

Varsayılan renk ve yazı tipleri kullanarak değiştirilebilir **ortamı, yazı tipleri ve renkler** özellik sayfası. Yazı tipleri birçok UI burada yalnızca Düzenleyicisi windows için değiştirebilirsiniz. C++'ye özgü ayarları "C++ ile"; başlayın diğer tüm diller için ayarlardır.

### <a name="cross-platform-intellisense"></a>Platformlar arası IntelliSense

Paylaşılan kod projesinde bile bir Android bağlamında çalışırken dalgalı çizgiler gibi bazı IntelliSense özellikleri kullanılamaz. Etkin olmayan projesinde bir hata ile sonuçlandı bazı kodlar yazmak, IntelliSense dalgalı çizgiler görüntülenmeye devam eder, ancak geçerli bağlamda hatalara dalgalı çizgiler daha farklı bir renk bulundukları.

Burada, Android ve iOS için oluşturmak için yapılandırılmış bir OpenGLES uygulama verilmiştir. Çizimde düzenlenmekte olan paylaşılan kod gösterir. İlk görüntüde etkin projeyi Android şöyledir:

![Etkin projeyi Android projesidir. ] (../ide/media/intellisensecppcrossplatform.png "IntelliSenseCppCrossPlatform")

Aşağıdakilere dikkat edin:

- # 8 satırındaki else dalı gri çıkışı etkin olmayan bölge belirtmek için çünkü __ANDROID\_ \_ Android projesi için tanımlanmış.

- Satırı 11 Tebrik değişkeni mor dalgalı sahip HELLO tanımlayıcısıyla başlatılır. Hiçbir tanımlayıcı HELLO şu anda etkin iOS projesinde tanımlanmış olmasıdır. Android projesi satır 11 derleme, ancak iOS olmaz. Bu, bir şeyin paylaşılan kod olduğundan şu anda etkin yapılandırmasında derler olsa da değiştirmeniz gerekir.

- Satırı 12 kırmızı dalgalı BYE tanımlayıcısı içeriyor; Bu tanımlayıcı şu anda seçili etkin projedeki tanımlı değil.

Şimdi, etkin proje için iOS.StaticLibrary değiştirmek ve dalgalı çizgiler nasıl değiştiğini dikkat edin.

![iOS etkin projesi olarak seçilir. ] (../ide/media/intellisensecppcrossplatform2.png "IntelliSenseCppCrossPlatform2")

Aşağıdakilere dikkat edin:

- Satır &#6;ifdef şube etkin olmayan bölge belirtmek için çünkü gri __ANDROID\_ \_ iOS projesi için tanımlı değil.

- Satırı 11 Tebrik değişkeni şimdi kırmızı dalgalı sahip HELLO tanımlayıcısıyla başlatılır. Hiçbir tanımlayıcı HELLO şu anda etkin iOS projesinde tanımlanmış olmasıdır.

- Satırı 12 mor dalgalı BYE tanımlayıcısı içeriyor; Bu tanımlayıcı, şu anda etkin Android.NativeActivity projesinde tanımlanmadı.

### <a name="intellisense-for-stand-alone-files"></a>Tek başına dosyaları için IntelliSense

Herhangi bir projenin dışında tek bir dosyayı açtığınızda, IntelliSense hala alın. Etkinleştirmek veya giderek belirli özellikleri devre dışı bırak **metin düzenleyici, C/C++, Gelişmiş** etkinleştirmek veya IntelliSense özellikleri devre dışı bırakmak için. IntelliSense, projesinin bir parçası olmayan tek dosyaları için yapılandırmak için Ara **IntelliSense ve proje dışı dosyaları için gözatma** içinde **Gelişmiş** bölümü. Bkz: [Visual C++ Kılavuzlu Tur](http://msdn.microsoft.com/en-us/499cb66f-7df1-45d6-8b6b-33d94fd1f17c).

![Visual C# 43; &#43; tek dosya IntelliSense](../ide/media/vs2015_cpp_single_file_intellisense.png "vs2015_cpp_single_file_intellisense")

Varsayılan olarak, tek dosyalı IntelliSense yalnızca kullanan standart üstbilgi dosyaları bulmak için içeren dizinler. Ek dizinler eklemek için çözüm düğümde kısayol menüsünü açın ve dizininize eklemek **hata ayıklama kaynak kodu** listesinde, aşağıdaki çizimde gösterildiği gibi:

![Bir yol için bir üstbilgi dosyası ekleme. ] (../ide/media/intellisensedebugyourcode.jpg "IntelliSenseDebugYourCode")

## <a name="see-also"></a>Ayrıca bkz.

[IntelliSense Kullanma](../ide/using-intellisense.md)