---
title: Hizmet Başvurularında Sorun Giderme
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 28ff14f10cd6ad5612551bb65b7b17f0280358f3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639598"
---
# <a name="troubleshoot-service-references"></a>Hizmet başvurularında sorun giderme

Bu konuda, Visual Studio 'da Windows Communication Foundation (WCF) veya WCF Veri Hizmetleri başvurularıyla çalışırken oluşabilecek yaygın sorunlar listelenmektedir.

## <a name="error-returning-data-from-a-service"></a>Hizmetten veri döndürme hatası

Bir hizmetten bir `DataSet` veya `DataTable` döndürdüğünüzde, "gelen iletiler için en büyük boyut kotası aşıldı" özel durumunu alabilirsiniz. Varsayılan olarak bazı bağlamaların `MaxReceivedMessageSize` özelliği, hizmet reddi saldırılarına maruz kalma olasılığını sınırlamak için görece küçük bir değere ayarlanır. Özel durumu engellemek için bu değeri artırabilirsiniz. Daha fazla bilgi için bkz. <xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>.

Bu hatayı onarmak için:

1. **Çözüm Gezgini**, açmak için *app. config* dosyasına çift tıklayın.

2. @No__t_0 özelliğini bulun ve daha büyük bir değerle değiştirin.

## <a name="cannot-find-a-service-in-my-solution"></a>Çözümünüzde bir hizmet bulunamıyor

**Hizmet başvuruları Ekle** Iletişim kutusunda **bul** düğmesine tıkladığınızda, çözümdeki BIR veya daha fazla WCF hizmet kitaplığı projesi Hizmetler listesinde görünmez. Bu, çözüme bir hizmet kitaplığı eklendiyse ancak henüz derlenmemişse meydana gelebilir.

Bu hatayı onarmak için:

- **Çözüm Gezgini**, WCF hizmet kitaplığı projesine sağ tıklayın ve **Oluştur**' a tıklayın.

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Uzak Masaüstü üzerinden bir hizmete erişilirken hata oluştu

Bir Kullanıcı, bir Uzak Masaüstü bağlantısı üzerinden Web 'de barındırılan bir WCF hizmetine eriştiğinde ve kullanıcının yönetim izinleri yoksa, NTLM kimlik doğrulaması kullanılır. Kullanıcı yönetici izinlerine sahip değilse, Kullanıcı şu hata iletisini alabilir: "HTTP isteği, istemci kimlik doğrulama düzeni ' anonim ' ile yetkilendirilmemiş. Sunucudan alınan kimlik doğrulama üst bilgisi ' NTLM ' idi. "

Bu hatayı onarmak için:

1. Web sitesi projesinde **Özellikler** sayfalarını açın.

2. **Başlangıç seçenekleri** sekmesinde, **NTLM kimlik doğrulaması** onay kutusunu temizleyin.

    > [!NOTE]
    > Yalnızca WCF hizmetleri içeren Web siteleri için NTLM kimlik doğrulamasını kapatmanız gerekir. WCF Hizmetleri için güvenlik, *Web. config* dosyasındaki yapılandırma üzerinden yönetilir. Bu, NTLM kimlik doğrulamasını gereksiz hale getirir.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>Oluşturulan sınıflar için erişim düzeyi ayarı etkisizdir

**Hizmet başvurularını Yapılandır** Iletişim kutusunda **iç** veya **arkadaş** olarak **oluşturulan sınıflar için erişim düzeyi** seçeneğinin ayarlanması her zaman çalışmayabilir. İletişim kutusunda seçenek ayarlanmış gibi görünse de, elde edilen destek sınıfları bir `Public` erişim düzeyiyle oluşturulur.

Bu, <xref:System.Xml.Serialization.XmlSerializer> kullanılarak serileştirilenler gibi belirli türlerin bilinen bir sınırlamasıdır.

## <a name="error-debugging-service-code"></a>Hizmet kodunda hata ayıklama hatası

İstemci kodundan bir WCF hizmeti için kod içine adımlayın, eksik simgelerle ilgili bir hata alabilirsiniz. Bu, çözümünüzün parçası olan bir hizmet çözümden taşındığında veya kaldırıldığında gerçekleşebilir.

Geçerli çözümün parçası olan bir WCF hizmetine ilk kez başvuru eklediğinizde, hizmet projesi ve hizmet istemci projesi arasında açık bir derleme bağımlılığı eklenir. Bu, istemcinin, istemci kodundan hizmet koduna atlama gibi hata ayıklama senaryoları için önemli olan güncel hizmet ikililerini her zaman erişmesi güvence altına alır.

Hizmet projesi çözümden kaldırılırsa, bu açık derleme bağımlılığı geçersiz kılınır. Visual Studio artık hizmet projesinin gerektiği şekilde yeniden oluşturulmasını garanti etmez.

Bu hatayı onarmak için, hizmet projesini el ile yeniden oluşturmanız gerekir:

1. **Araçlar** menüsünde **Seçenekler**' e tıklayın.

2. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **genel**' i seçin.

3. **Gelişmiş derleme yapılandırmasını göster** onay kutusunun seçili olduğundan emin olun ve ardından **Tamam**' a tıklayın.

4. WCF hizmeti projesini yükleyin.

5. **Configuration Manager** iletişim kutusunda, **etkin çözüm yapılandırmasını** **Hata Ayıkla**olarak ayarlayın. Daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md).

6. **Çözüm Gezgini**, WCF hizmeti projesini seçin.

7. WCF hizmeti projesini yeniden derlemek için **Derle** menüsünde **yeniden derle** ' ye tıklayın.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF Veri Hizmetleri tarayıcıda gösterme

Bir [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] verilerin XML temsilini görüntülemeye çalıştığında, Internet Explorer verileri bir RSS akışı olarak yanlış yorumlayabilir. RSS akışlarını görüntüleme seçeneğinin devre dışı olduğundan emin olun.

Bu hatayı onarmak için RSS akışlarını devre dışı bırakın:

1. Internet Explorer 'da, **Araçlar** menüsünde **Internet seçenekleri**' ne tıklayın.

2. **İçerik** sekmesinde, **akışlar** bölümünde, **Ayarlar**' a tıklayın.

3. **Akış ayarları** iletişim kutusunda, **akış okuma görünümünü aç** onay kutusunu temizleyin ve ardından **Tamam**' a tıklayın.

4. **Internet seçenekleri** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)