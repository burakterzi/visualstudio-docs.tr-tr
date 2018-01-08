---
title: "Nasıl yapılır: izinleri ayarla | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling, setting permissions
- security [Visual Studio ALM], setting permissions
- permissions [Visual Studio ALM], profiling
- profiling tools, setting profiling permissions
- performance tools, setting profiling permissions
ms.assetid: 69f27896-8f46-4ef3-bfb7-726d95304f3a
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 44f67dd4b1c6717dfaf48ada0f093a845899e16c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-permissions"></a>Nasıl yapılır: izinleri ayarla
Bu konuda, bir bilgisayarın yönetici bir kullanıcı veya bu bilgisayarda yönetici izinlerine sahip olmayan grubuna profil için gerekli güvenlik izinleri nasıl verir açıklanmaktadır.  
  
 Temel güvenlik ilkesini uygulamaların en çok ihtiyaç duydukları izinleri ile çalışması gerektiğini belirtir. Bu ilkeyi kullanıcılar için de geçerlidir. Bunlar Yöneticiler grubu yerine Users grubunun bir üyesi olarak oturum açtığınızda kullanıcılar tam olarak etkili olabilir, bunlar yönetici izinleri verilmemelidir. "Kullanıcı izinlerine sahip bir kullanıcı hesabı oluşturmak için" ilk yordamı, kullanıcılar grubunun bir üyesi için bir kullanıcı hesabı oluşturma açıklar.  
  
 **Gereksinimler**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Users grubunun üyeleri, disk üzerindeki diğer takım üyeleri ile paylaşılan dosya ve klasörleri erişimi gerekir. "Paylaşılan proje dosyalarına erişim vermek için" ikinci yordam, bu erişim vermesi açıklar.  
  
 Bir yöneticinin bunları profil oluşturma araçları için yazılım sürücüsü için erişim verirse Users grubunun üyeleri profil oluşturma araçları çalıştırabilirsiniz. "Profil sürücü erişim vermek için" son yordamı, bu sürücüyü erişim açıklar.  
  
> [!NOTE]
>  Bu yordamlarda bulunan adımları izlemek için yönetici izinlerine sahip olmanız gerekir.  
  
### <a name="to-create-a-user-account-that-has-user-permissions"></a>Kullanıcı izinleri olan bir kullanıcı hesabı oluşturmak için  
  
1.  Sağ **Bilgisayarım** ve ardından **Yönet**.  
  
     **Bilgisayar Yönetimi** penceresi açılır.  
  
2.  Genişletme **yerel kullanıcılar ve gruplar**.  
  
3.  Sağ **kullanıcılar** klasörünü ve ardından **yeni kullanıcı**.  
  
     **Yeni kullanıcı** iletişim kutusu görüntülenir.  
  
4.  Bu iletişim kutusunda, oluşturduğunuz kullanıcı hesabını bilgilerle alanları doldurun. Bir parola belirtin. İsteğe bağlı olarak, kullanıcı değiştirme sonraki oturumda parola gerektiren onay kutusunu seçin.  
  
5.  Tıklatın **oluşturma** ve ardından **Kapat**.  
  
     Yeni kullanıcı kullanıcılar grubu, bir Grup yönetici izinlerine sahip olmayan kullanıcıların görünür.  
  
### <a name="to-grant-access-to-shared-project-files"></a>Proje dosyaları paylaşılan erişim izni vermek için  
  
1.  Windows Gezgini (veya dosya Gezgini'ni), bu kullanıcı tarafından kullanılan ve proje ekibi tarafından paylaşılan proje dosyaları için klasör ağacının kökü bulun.  
  
     Bu klasör yolu şöyle olabilir:  
  
    ```  
    D:\ourProject  
    ```  
  
2.  Klasöre sağ tıklayın ve ardından **özellikleri**.  
  
      **\<Klasör adı > Özellikler** iletişim kutusu görüntülenir.  
  
3.  Tıklatın **güvenlik** sekmesi.  
  
4.  Kullanıcı hesabının adını tıklatın **grup veya kullanıcı adları** kutusu.  
  
5.  İçinde **izinlerini \<kullanıcı adı >** kutusunda, onay kutusunu seçin **tam denetim**.  
  
6.  **Tamam**'ı tıklatın.  
  
     Bu kullanıcıya 5. adımda seçtiğiniz klasör ile başlayan paylaşılan klasör ağacı için izinler verir.  
  
### <a name="to-grant-access-to-the-profiling-driver"></a>Profil oluşturma sürücü erişim vermek için  
  
1.  Komut istemini yönetici olarak açın.  
  
2.  Dizinine değiştirin:  
  
    ```  
    <drive>:\Program Files\Microsoft Visual Studio 10\Team Tools\Performance Tools  
    ```  
  
3.  Şu komutu çalıştırın:  
  
    ```  
    vsperfcmd /admin:driver,start /admin:service,start  
    ```  
  
     Bu komut, yükler ve profil oluşturma araçları için sürücü başlatır.  
  
     Bu komut profil sürücü ve hizmeti başlatır yönetici olmayan kullanıcılar kendi kullanıcı işlem alanında kullanılabilen profil özellikleri kullanabilir. Yalnızca bir yönetici komut çalışabilir; ve yönetici olmayan kullanıcılar için başarısız olur.  
  
     Bu adım etkilerini sonra geri bildirim bilgisayarı yeniden başlatır, bu yordamda ayrıca son adım gerçekleştirmediğiniz sürece.  
  
4.  Bir kullanıcı veya bilgisayar için yönetici erişimine sahip değil grubu tarafından sürücü işlevleri profil erişimi sağlamak üzere komutu çalıştırın:  
  
    ```  
    vsperfcmd /admin:security,allow,<right[,right],<user name|group name>  
    ```  
  
     Bu komut verir \<kullanıcı adı > veya \<grubu adı > Hesap profil oluşturma araçları için erişim. \<Sağ > seçeneğini belirler profil işlevselliği kullanıcı erişebilir. \<Sağ > seçeneği, bir veya daha fazla aşağıdaki değerlerden biri olabilir:  
  
    -   FullAccess - örnekleme Hizmetleri'nden performans verileri toplama dahil olmak üzere tüm profil oluşturma yöntemleri erişmesini sağlar ve profil oluşturma oturumu arası.  
  
    -   SampleProfiling - örnek profil oluşturma yöntemlerini erişmesine izin verir  
  
    -   CrossSession - Hizmetleri profil için gerekli olduğu profil oluşturma oturumu arası erişim sağlar.  
  
5.  (İsteğe bağlı) Bilgisayar yeniden başlatıldıktan sonra önceki adımları sonuçlarını korumak için aşağıdaki komutu çalıştırın:  
  
    ```  
    vsperfcmd /admin:driver,autostart,on  
    ```  
  
 Belirtilen kullanıcılar oturum açma sonra artık yönetici izinleri olmayan profil oluşturma araçları kullanmanız mümkün olacaktır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil oluşturma ve Windows Vista güvenliği](../profiling/profiling-and-windows-vista-security.md)