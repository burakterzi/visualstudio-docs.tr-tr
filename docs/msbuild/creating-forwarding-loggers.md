---
title: "İletme Günlükçüleri oluşturma | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, forwarding loggers
- MSBuild, logging
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
caps.latest.revision: "9"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5037b284a0f524a8b7c550a72fe76a27afd37f10
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-forwarding-loggers"></a>İletme Günlükçüleri Oluşturma
İletme günlükçüleri, çok işlemcili bir sistemde projeler derlerken izlemek istediğiniz olayları seçmenize izin vererek günlük verimliliği artırır. İletme günlükçüleri etkinleştirerek merkezi Günlükçü aşırı, derleme zamanı yavaşlamasının ve günlüğünüzü alanınızda karışıklık istenmeyen olayları engelleyebilir.  
  
 Bir iletme Kaydedici oluşturmak için her iki uygulama yapabilir <xref:Microsoft.Build.Framework.IForwardingLogger> arabirim ve yöntemleri el ile uygulamak veya kullanmak <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> sınıfı ve onun önceden yapılandırılmış yöntemleri. (İkinci çoğu uygulama için yeterli olacaktır.)  
  
## <a name="register-events-and-respond-to-them"></a>YAZMAÇ olayları ve bunlara yanıt  
 Ana derleme süreci tarafından birden çok işlemcili sistem üzerinde bir derleme sırasında oluşturulan bir alt işlem ikincil yapı altyapısı tarafından bildirilen bir iletme Kaydedici yapı olaylar hakkında bilgi toplar. Ardından, verdiğiniz yönergelere dayalı merkezi Günlükçü iletmek için olayları iletme Günlükçü seçer.  
  
 İzlemek istediğiniz olayları işlemek için iletme günlükçüleri kaydetmeniz gerekir. Günlükçüleri olaylarını kaydetmek için kılmalıdır <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> yöntemi. Bu yöntem artık isteğe bağlı bir parametre içeriyor `nodecount`, ayarlanabilecek işlemci sayısını sistemde. (Varsayılan değeri 1'dir.)  
  
 Olayları izleyebilirsiniz örnekleri <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>, ve <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.  
  
 Birden çok işlemcili ortamda bozuk alınabilmesi olay iletileri olasıdır. Bu nedenle, olay işleyicisi iletme Günlükçü kullanarak olayları değerlendirmek ve iletmek üzere merkezi Günlükçü yeniden yönlendirici'ye geçirmek için hangi olayların belirlemek için programın gerekir. Bunu gerçekleştirmek için kullanabilirsiniz <xref:Microsoft.Build.Framework.BuildEventContext> sınıfı, her ileti iletmek istediğiniz olayların tanımlamaya yardımcı olmak için ekli olduğu ve olaylara adlarını geçirin <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> sınıfı (veya onu öğesinin bir alt kümesi). Bu yöntemi kullandığınızda, diğer belirli kodlama iletme olaylarına gerekli değildir.  
  
## <a name="specify-a-forwarding-logger"></a>İletme Günlükçü belirtin  
 Bir derlemeye iletme Günlükçü derlendikten sonra söylemelisiniz [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] derlemeleri sırasında kullanılacak. Bunu yapmak için kullanın `/FileLogger`, `/FileLoggerParameters`, ve `/DistributedFileLogger` MSBuild.exe birlikte anahtarları. `/FileLogger` Anahtar Günlükçü doğrudan bağlı olduğu MSBuild.exe söyler. `/DistributedFileLogger` Anahtar düğümü başına bir günlük dosyası olduğu anlamına gelir. İletme Günlükçü parametrelerini ayarlamak için kullanın `/FileLoggerParameters` geçin. Bunlar ve diğer MSBuild.exe anahtarları hakkında daha fazla bilgi için bkz: [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="multi-processor-aware-loggers"></a>Birden çok işlemciye duyarlı günlükçüler  
 Çok işlemcili bir sistemde bir projeyi derlerken her işlemci derleme iletilerden otomatik olarak birleşik sıradaki bir araya eklemeli değil. Bunun yerine, öncelik kullanarak gruplandırma bir ileti kurmalısınız <xref:Microsoft.Build.Framework.BuildEventContext> her iletisine sınıfı. Birden çok işlemcili oluşturma hakkında daha fazla bilgi için bkz: [birden çok işlemcili ortamda oturum açma](../msbuild/logging-in-a-multi-processor-environment.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Derleme günlüklerini alma](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Günlükçüleri derleme](../msbuild/build-loggers.md)   
 [Birden Çok İşlemcili Ortamda Oturum Açma](../msbuild/logging-in-a-multi-processor-environment.md)