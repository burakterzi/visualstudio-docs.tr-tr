---
title: "Nasıl yapılır: belirli dll 'Lerle Izleme sınırlandırma | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, runtime profiling control window
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 066262a3fae35e82904b011165813e9dd75d9987
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778823"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Nasıl yapılır: belirli dll 'Lerle izleme sınırlandırma

İzleme profili oluşturma yöntemini kullanarak, bir uygulamadaki bir veya daha fazla dll ile profil oluşturma verilerinin toplanmasını sınırlayabilirsiniz. Bir uygulamada bir veya daha fazla dll profili oluşturmak için, içeren bir performans oturumu oluşturursunuz. hedef olarak *DLL* dosyaları. Bir Visual Studio çözümünde veya bağımsız ikili dosyalarda proje olarak profil eklemek istediğiniz dll 'Leri belirtebilirsiniz.

## <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Bir Visual Studio çözümünde belirli dll 'Leri izleme ile sınırlamak için

1. Visual Studio 'da DLL dosyasını içeren çözümü açın.

2. **Çözümle** menüsünde, **Performans Sihirbazını Başlat**' ı seçin.

3. Profil oluşturma yöntemi olarak **Araçlar** ' ı seçin ve ardından **İleri**' ye tıklayın.

4. **Aşağıdaki kullanılabilir hedeflerden hangisi profilini oluşturmak istersiniz?** altında, adını seçin. tıklayın ve ardından **İleri**' ye tıklayın.

5. Sihirbazdan çıkmak için **son** ' a tıklayın ve yeni performans oturumunu **Performans Gezgini** penceresinde görüntüleyin.

6. **Hedefler** ' e sağ tıklayın ve ardından **hedef proje Ekle**' yi seçin.

7. **Hedef proje Ekle** LISTESINDEN, dll 'yi kullanmak için kullanmak istediğiniz çalıştırılabilir projeyi seçin.

     İsteğe bağlı. Profil eklemek istediğiniz herhangi bir DLL projesini ekleyebilirsiniz.

8. Eklenen bir proje için veri toplamayı engellemek için, projenin adına sağ tıklayın ve ardından **gereç** onay kutusunu temizleyin.

## <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Belirli dll 'Lerin bağımsız ikili dosyalar olarak profilini belirtmek için

1. Visual Studio'yu açın.

2. **Çözümle** menüsünde, **Performans Sihirbazını Başlat**' ı seçin.

3. **Aşağıdaki kullanılabilir hedeflerden hangisi profilini oluşturmak**istersiniz, **bir dinamik bağlantı kitaplığı profili seçin (. DLL)** ve ardından **İleri**' ye tıklayın.

4. Sihirbazın ikinci sayfasında, aşağıdaki adımları uygulayın:

    - Yolunu ve dosya adını yazın. dll dosyasında, **DLL yolunda**profil yapmak istediğiniz *DLL* dosyası. Ayrıca, dosyayı **profile olan dinamik bağlantı kitaplığı** iletişim kutusunda bulmak için üç nokta düğmesini (...) de tıklayabilirsiniz. Kopyasını belirtmeniz gerektiğini unutmayın. yürütülebilir dosya tarafından başlatılacak *DLL* dosyası (. *exe*) dosyasını seçin.

    - Yürütülebilir dosyanın yolunu ve adını yazın (. *exe*) dosyası ile çalışır. *DLL* **yürütülebilir dosya yolu**. Ayrıca, **başlatılacak yürütülebilir** iletişim kutusunda dosyayı bulmak için üç nokta düğmesini (...) de tıklayabilirsiniz.

    - İsteğe bağlı. **Komut satırı bağımsız değişkenlerinde**yürütülebilir dosyaya geçirmek istediğiniz komut satırı bağımsız değişkenlerini yazın. Gerekirse, **çalışma dizinindeki**uygulama için çalışma dizinini belirtin.

    - **İleri**'ye tıklayın.

5. Profil oluşturma yöntemi olarak **Araçlar** ' ı seçin ve ardından **İleri**' ye tıklayın.

6. Sihirbazdan çıkmak için **son** ' a tıklayın ve yeni performans oturumunu **Performans Gezgini** penceresinde görüntüleyin.

7. İsteğe bağlı. Daha fazlasını ekleyin. *DLL* dosyaları, **hedefler** ' e sağ tıklayın ve ardından **hedef ikilisi Ekle**' yi seçin. **Hedef Ikili Ekle** iletişim kutusundan dosyaları seçin.

    > [!NOTE]
    > Yürütülebilir dosyayı belirtmeyin (. *exe*) dosyası dll 'leri uygulayan dosya.

## <a name="see-also"></a>Ayrıca bkz.

[Denetim verileri toplama](../profiling/controlling-data-collection.md)
[nasıl yapılır: belirli işlevlerle izleme sınırlandırma](../profiling/how-to-limit-instrumentation-to-specific-functions.md)
