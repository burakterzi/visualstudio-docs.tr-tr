---
title: Docker Hub 'a ASP.NET Core Docker kapsayıcısı dağıtma | Microsoft Docs
description: ASP.NET Core Web uygulamasını Docker Hub 'a dağıtmak için Visual Studio kapsayıcı araçlarını kullanmayı öğrenin
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 07/23/2019
ms.author: ghogen
ms.openlocfilehash: b033825bbe8facbeae3dcdee6a5b563461921522
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188754"
---
# <a name="deploy-to-docker-hub"></a>Docker Hub’a dağıtma

Docker Hub, görüntü depolarınız için uygun bir barındırma hizmeti sağlar. Visual Studio 'dan el ile Docker Hub 'ına kolayca dağıtım yapabilirsiniz.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Docker hesabı ve Docker Hub deposu oluşturma

Henüz yoksa bir Docker hesabına [kaydolun](https://hub.docker.com/signup) .

Docker Hub deponuz yoksa, [Docker Hub](https://hub.docker.com/)'da bir tane oluşturun.

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Tek bir proje görüntüsünü Docker Hub 'a yayımlama

1. Proje düğümüne sağ tıklayın ve **Yayımla...** seçeneğini belirleyin. Dağıtım seçeneklerini gösteren bir ekran görüntülenir.

   ![](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. **Bir yayımlama hedefi seçin**altında **Container Registry**' yi seçin ve ardından **Docker Hub**' ı seçin. **Docker Hub** iletişim kutusu görüntülenir.

   ![](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. Kendi deponuza bağlanıyorsanız (bir kuruluşun parçası değil), **kişisel bir depoda yayımlama** onay kutusunu işaretli olarak bırakın. Deponun sahibi bir kuruluşa aitse, onay kutusunu temizleyin ve kuruluş adını girin. Docker hesabınız için, bağlandığınız depoya erişim izni olan Docker Kullanıcı adınızı ve parolanızı girin ve ardından **Kaydet**' i seçin.  

   Visual Studio görüntünüzü Docker Hub 'ına dağıtmaya çalışır.  Başarılı olursa, **Yayımla** ekranı depo görüntüsü, resim etiketi, depo ve derleme yapılandırması * * (örneğin, **Sürüm**) URL 'si ile birlikte görüntülenir.

   ![](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. Bu sayfadaki **Yayımla** düğmesine tıklayarak görüntüyü dilediğiniz zaman güncelleştirebilirsiniz.  Ya da, URL 'nin altındaki bağlantıları kullanarak profili değiştirebilir veya kaldırabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

[Azure Container Registry dağıtım](hosting-web-apps-in-docker.md)konumundaki adımları izleyerek [Azure Container Registry](/azure/container-registry/) yayımlayın.

[Azure Pipelines](/azure/devops/pipelines/?view=azure-devops)ile sürekli tümleştirme ve teslım (CI/CD) ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio kapsayıcı araçlarına](/visualstudio/containers/) [Azure App Service
dağıtın](deploy-app-service.md) .