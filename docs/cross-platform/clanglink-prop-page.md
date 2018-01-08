---
title: "Clang bağlayıcı Özellikleri (Android C++) | Microsoft Docs"
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66e88848-116c-4eb0-bc57-183394d35b57
author: corob
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- VC.Project.VCLinkerTool.ShowProgress
- VC.Project.VCLinkerTool.Version
- VC.Project.VCLinkerTool.VerboseOutput
- VC.Project.VCLinkerTool.IncrementalLink
- VC.Project.VCLinkerTool.SharedLibrarySearchPath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
- VC.Project.VCLinkerTool.UnresolvedReferences
- VC.Project.VCLinkerTool.OptimizeForMemory
- VC.Project.VCLinkerTool.IgnoreDefaultLibraryNames
- VC.Project.VCLinkerTool.ForceSymbolReferences
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.OmitDebuggerSymbolInformation
- VC.Project.VCLinkerTool.GenerateMapFile
- VC.Project.VCLinkerTool.Relocation
- VC.Project.VCLinkerTool.FunctionBinding
- VC.Project.VCLinkerTool.NoExecStackRequired
- VC.Project.WholeArchive
- VC.Project.AdditionalOptionsPage
- VC.Project.VCLinkerTool.AdditionalDependencies
- VC.Project.VCLinkerTool.LibraryDependencies
ms.workload: xplat-cplusplus
ms.openlocfilehash: f74ad5934d48c941195da30d9228c35483479f69
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="clang-linker-properties-android-c"></a>Clang bağlayıcı Özellikleri (Android C++)

Özellik | Açıklama | Seçenekler
--- | ---| ---
Çıkış dosyası | Varsayılan ad ve konum bağlayıcı oluşturur programın seçeneğini geçersiz kılar. (-o).
İlerlemesini Göster | Bağlayıcı ilerleme iletilerini yazdırır.
Sürüm | Sürüm seçenek yürütülebilir dosya üstbilgisinde bir sürüm numarası koymak için bağlayıcı söyler.
Ayrıntılı çıktı etkinleştir | Verbose seçenek hata ayıklama için ayrıntılı ileti çıkışı için bağlayıcı söyler.
Artımlı bağlantılandırma etkinleştir | Seçenek artımlı bağlantılandırma etkinleştirmek için bağlayıcı söyler.
Paylaşılan kitaplık arama yolu | Paylaşılan kitaplık arama yolu doldurmak olanak tanır.
Ek Kitaplık dizinleri | Ortam Kitaplığı yol geçersiz kılmanıza olanak tanır. (-M klasörü).
Çözümlenmemiş simge başvurularını raporu | Bu seçenek etkinleştirildiğinde çözümlenmemiş sembol başvuruları bildirir.
Bellek kullanımı için en iyi duruma getirme | Sembol tabloları gerektiği gibi yeniden okumaya bellek kullanımı için en iyi duruma getirme.
Belirli varsayılan kitaplıkları yoksay | Bir veya daha fazla yok saymak için varsayılan kitaplık adını belirtir.
Simge başvurularını zorla | Tanımlanmamış bir simge olarak çıktı dosyasında girilecek simgesi zorlar.
Hata ayıklayıcı sembol bilgileri | Sembol bilgilerini çıktı dosyası hata ayıklayıcı. | **Tüm içerir**<br>**Yeniden konumlandırma işlenmek üzere gereksiz simgeleri atlayın**<br>**Hata ayıklayıcı sembol bilgileri yalnızca atlayın**<br>**Tüm simge bilgilerini atlayın**<br>
Paket hata ayıklayıcı sembol bilgileri | Hata ayıklayıcı simgeleri bilgilerin paketlemeden önce Şerit.  Özgün ikili bir kopyasını, hata ayıklama için kullanılır.
Dosya adı eşleme | Map seçeneği kullanıcı belirtilen ada sahip bir harita dosyası oluşturmak için bağlayıcı söyler.
Yeniden konumlandırma sonra işareti değişkenleri salt okunur | Bu seçenek, sonra yeniden konumlandırma değişkenleri salt okunur işaretler.
Hemen işlev bağlama etkinleştir | Bu seçenek nesne hemen işlev bağlama için işaretler.
Yürütülebilir yığını gerektirir | Bu seçenek çıktı yürütülebilir yığını gerektirmeyen olarak işaretler.
Tüm arşiv | Tüm arşiv kaynakları ve ek bağımlılıklar tüm koddan kullanır.
Ek Seçenekler | Ek Seçenekler.
Ek Bağımlılıklar | Bağlantı komut satırına eklenecek ek öğelerini belirtir.
Kitaplık bağımlılıkları | Bu seçenek bağlayıcı komut satırına eklenecek ek kitaplıklarını belirtme sağlar. Ek kitaplıklar 'lib' bağlayıcı komut satırı Başlarken sonuna ve bitiş 'bir' veya '.so' uzantılı eklenir.  (-lFILE)