---
title: Komutlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio, commands
- commands, Visual Studio
- command syntax
ms.assetid: 76ffa394-ee89-4629-aba9-1a62b72e6cc1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3af3685288c00e27bb63cd45c682ab8b6354f4e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72622112"
---
# <a name="visual-studio-commands"></a>Visual Studio komutları

**Komut** penceresinde, **anında** pencereye veya **Bul/komut** kutusuna Visual Studio komutlarını girebilirsiniz. Her durumda, büyüktür işareti (`>`), arama veya hata ayıklama işlemi yerine bir komutun aşağıda gösterildiği anlamına gelir.

**Araçlar**  > **Seçenekler**  > **ortamındaki** **klavye** sayfasında komutların ve sözdiziminin tamamen bir listesini bulabilirsiniz.

IDE 'nin yerelleştirilmiş sürümlerinde, komut adları IDE 'nin yerel dilinde veya Ingilizce ' de girilebilir. Örneğin, aynı komutu yürütmek için Fransızca IDE 'de `File.NewFile` ya da `Fichier.NouveauFichier` yazabilirsiniz.

Birçok komutun diğer adları vardır. Komut diğer adlarının listesi için bkz. [komut diğer adları](../../ide/reference/visual-studio-command-aliases.md). Komut klavye kısayolları için bkz. [Visual Studio 'Da varsayılan klavye kısayolları](../default-keyboard-shortcuts-in-visual-studio.md).

## <a name="escape-character"></a>Atlatma karakteri

Visual Studio komutları için kaçış karakteri bir şapka (^). Kaçış karakteri, bir denetim karakteri olarak değil, tam olarak yorumlandığı anlamına gelir. Bu, anahtar adları dışında bir parametre veya anahtar değerindeki düz tırnak işaretlerini ("), boşlukları, baştaki eğik çizgileri, yüzleri veya diğer sabit karakterleri eklemek için kullanılabilir. Örneğin:

```
>Edit.Find ^^t /regex
```

Bir giriş işareti, tırnak işaretlerinin içinde mi yoksa dışında mı olduğunu görür. Şapka, satırdaki son karakter ise yok sayılır.

## <a name="commands-with-arguments"></a>Bağımsız değişkenlerle komutlar

Aşağıdaki komutlar bağımsız değişkenler veya anahtarlar alır:

| Komut adı | Açıklama |
| - | - |
| [Var olan öğeyi Ekle](../../ide/reference/add-existing-item-command.md) | Geçerli çözüme var olan bir dosyayı ekler ve açar. |
| [Mevcut projeyi Ekle](../../ide/reference/add-existing-project-command.md) | Geçerli çözüme mevcut bir projeyi ekler. |
| [Yeni öğe Ekle](../../ide/reference/add-new-item-command.md) | Geçerli çözüme. htm,. css,. txt veya FRAMESET gibi yeni bir çözüm öğesi ekler ve onu açar. |
| [Ek](../../ide/reference/alias-command.md) | Tüm komut için yeni bir diğer ad oluşturur, komut ve bağımsız değişkenler ya da başka bir diğer ad oluşturur. |
| [Ifadeyi değerlendir](../../ide/reference/evaluate-statement-command.md) | Verilen ifadeyi değerlendirir ve görüntüler. |
| [Bilgi](../../ide/reference/find-command.md) | **Bul ve Değiştir** denetiminde bulunan seçeneklerin bir alt kümesini kullanarak dosyaları arar. |
| [Dosyalarda Bul](../../ide/reference/find-in-files-command.md) | Dosyalarında [Bul dosyalarında](../../ide/find-in-files.md)bulunan seçeneklerin bir alt kümesini kullanarak dosyaları arar. |
| [Git](../../ide/reference/go-to-command.md) | İmleci belirtilen satıra kaydırır. |
| [Çağrı yığınını Listele](../../ide/reference/list-call-stack-command.md) | Geçerli çağrı yığınını görüntüler. |
| [Ayrıştırılmış kodu Listele](../../ide/reference/list-disassembly-command.md) | Hata ayıklama işlemini başlatır ve hataların nasıl işleneceğini belirtmenizi sağlar. |
| [Belleği listeleme](../../ide/reference/list-memory-command.md) | Belirtilen bellek aralığının içeriğini görüntüler. |
| [Liste modülleri](../../ide/reference/list-modules-command.md) | Geçerli işlem için modülleri listeler. |
| [Kayıt listeleri](../../ide/reference/list-registers-command.md) | Yazmaçların bir listesini görüntüler. |
| [Kaynağı Listele](../../ide/reference/list-source-command.md) | Belirtilen kaynak kodu satırlarını görüntüler. |
| [Iş parçacıklarını Listele](../../ide/reference/list-threads-command.md) | Geçerli programdaki iş parçacıklarının listesini görüntüler. |
| [Günlük komut penceresi çıkışı](../../ide/reference/log-command-window-output-command.md) | Komut penceresi tüm giriş ve çıkışları bir dosyaya kopyalar. |
| [Yeni dosya](../../ide/reference/new-file-command.md) | Yeni bir dosya oluşturur ve onu seçili olan projeye ekler. |
| [Dosya Aç](../../ide/reference/open-file-command.md) | Var olan bir dosyayı açar ve bir düzenleyici belirtmenize olanak tanır. |
| [Projeyi aç](../../ide/reference/open-project-command.md) | Mevcut bir projeyi açar ve projeyi geçerli çözüme eklemenize olanak sağlar. |
| [Yazdırdığımda](../../ide/reference/print-command.md) | İfadeyi değerlendirir ve sonuçları veya belirtilen metni görüntüler. |
| [Hızlı Bakış Komutu](../../ide/reference/quick-watch-command.md) | **Hızlı izleme** Iletişim kutusunun **ifade** alanında seçili veya belirtilen metni görüntüler. |
| [Değiştirin](../../ide/reference/replace-command.md) | **Bul ve Değiştir** denetiminde bulunan seçeneklerin bir alt kümesini kullanarak dosyalardaki metni değiştirir. |
| [Dosyalarda Değiştir](../../ide/reference/replace-in-files-command.md) | Dosyalardaki metni [Değiştir dosyalarında](../../ide/replace-in-files.md)bulunan seçeneklerin bir alt kümesini kullanarak değiştirir. |
| [Geçerli yığın çerçevesini ayarla](../../ide/reference/set-current-stack-frame-command.md) | Belirli bir yığın çerçevesini görüntülemenize izin verir. |
| [Geçerli Iş parçacığını ayarla](../../ide/reference/set-current-thread-command.md) | Belirli bir iş parçacığını görüntülemenize izin verir. |
| [Radix ayarla](../../ide/reference/set-radix-command.md) | Görüntülenecek bayt sayısını belirler. |
| [Kabuk](../../ide/reference/shell-command.md) | Komutu komut isteminden yürütüyormuş gibi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] içinden programları başlatır. |
| [ShowWebBrowser Komutu](../../ide/reference/showwebbrowser-command.md) | Bir Web tarayıcı penceresinde belirttiğiniz URL 'YI tümleşik geliştirme ortamı (IDE) veya IDE 'nin dışında görüntüler. |
| [Start](../../ide/reference/start-command.md) | Hata ayıklama işlemini başlatır ve hataların nasıl işleneceğini belirtmenizi sağlar. |
| [Yolun](../../ide/reference/symbol-path-command.md) | Hata ayıklayıcının simge araması için dizinlerin listesini ayarlar. |
| [Kesme noktasını aç](../../ide/reference/toggle-breakpoint-command.md) | Dosyadaki geçerli konumda, geçerli durumuna bağlı olarak, kesme noktasını açar veya kapatır. |
| [İzle Komutu](../../ide/reference/watch-command.md) | Bir **Gözcü** penceresinin belirtilen bir örneğini oluşturur ve açar. |

## <a name="see-also"></a>Ayrıca bkz.

- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)