---
title: Ayarlar deposundan hizmet bilgileri alınıyor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51aa0369793fe5dc4b39fe510c069a7ec93d102a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647975"
---
# <a name="get-service-information-from-the-settings-store"></a>Ayarlar deposundan hizmet bilgilerini al
Tüm kullanılabilir hizmetleri bulmak veya belirli bir hizmetin yüklenip yüklenmediğini öğrenmek için ayarlar deposunu kullanabilirsiniz. Hizmet sınıfının türünü bilmeniz gerekir.

## <a name="to-list-the-available-services"></a>Kullanılabilir hizmetleri listelemek için

1. @No__t_0 adlı bir VSıX projesi oluşturun ve sonra `FindServicesCommand` adlı özel bir komut ekleyin. Özel bir komut oluşturma hakkında daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)

2. *FindServicesCommand.cs*' de, aşağıdaki using yönergelerini ekleyin:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Yapılandırma ayarları deposunu alın ve ardından hizmet adlı alt koleksiyonu bulun. Bu koleksiyon, kullanılabilir tüm hizmetleri içerir. @No__t_0 yönteminde, var olan kodu kaldırın ve aşağıdaki kodla değiştirin:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string message = "Available services:\n";
        IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services");
        int n = 0;
        foreach (string service in collection)
        {
            message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n";
        }

        MessageBox.Show(message);
    }
    ```

4. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görüntülenir.

5. Deneysel örnekte, **Araçlar** menüsünde **Findservicescommand komutunu çağır**' a tıklayın.

     Tüm hizmetlerin listelendiği bir ileti kutusu görmeniz gerekir.

     Bu ayarları doğrulamak için kayıt defteri düzenleyicisini kullanabilirsiniz.

## <a name="find-a-specific-service"></a>Belirli bir hizmeti bulma
 Ayrıca, belirli bir hizmetin yüklenip yüklenmediğini anlamak için <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> yöntemini kullanabilirsiniz. Hizmet sınıfının türünü bilmeniz gerekir.

1. Önceki yordamda oluşturduğunuz projenin MenuItemCallback öğesinde, hizmet GUID 'SI tarafından adlandırılan alt koleksiyonun bulunduğu `Services` koleksiyonu için yapılandırma ayarları deposunda arama yapın. Bu durumda, yardım hizmetine bakacağız.

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper();
        bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID);
        string message = "Help Service Available: " + hasHelpService;

        MessageBox.Show(message);
    }
    ```

2. Projeyi derleyin ve hata ayıklamayı başlatın.

3. Deneysel örnekte, **Araçlar** menüsünde **Findservicescommand komutunu çağır**' a tıklayın.

     Metin **yardım hizmeti kullanılabilir** bir ileti görmeniz gerekir: **true** veya **false**. Bu ayarı doğrulamak için, önceki adımlarda gösterildiği gibi bir kayıt defteri düzenleyici kullanabilirsiniz.
