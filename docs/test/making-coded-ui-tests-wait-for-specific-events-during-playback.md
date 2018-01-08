---
title: "Kayıttan yürütme sırasında testleri bekleme belirli olaylar için kodlanmış UI yapma | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41981ad6-673e-492e-b739-9863b14157b1
caps.latest.revision: "24"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: b2c507d49bca2589d7c5a70d88f8819ee68d0ce5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="making-coded-ui-tests-wait-for-specific-events-during-playback"></a>Kayıttan Yürütme Sırasında Belirli Olaylar için Kodlanmış UI Testlerini Bekletme
İçinde kodlanmış bir UI Testi kayıttan, kaybolur ve benzeri için ilerleme çubuğu oluşmasına görünmesi için bir pencere gibi belirli olaylar için beklenecek test söyleyebilirsiniz. Bunu yapmak için aşağıdaki tabloda açıklandığı gibi uygun UITestControl.WaitForControlXXX() yöntemini kullanın. Bir denetimi kullanma etkin olmasını bekler kodlanmış bir UI testi örneği <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A> yöntemi, bkz: [izlenecek yol: oluşturma, düzenleme ve kodlanmış bir UI testi koruma](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).  
  
 **Gereksinimler**  
  
 Visual Studio Enterprise  
  
> [!TIP]
>  Kodlanmış UI Test Düzenleyicisi'ni kullanarak eylemleri önce gecikmeler de ekleyebilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: kodlanmış UI Test Düzenleyicisi'ni bir gecikme önce bir UI eylemini kullanarak Ekle](http://msdn.microsoft.com/Library/509f8ef7-e105-4049-b11b-d64549e055b0).  
  
 **UITestControl.WaitForControlXXX() yöntemleri**  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlReady%2A>  
  
 Denetim için fare ve klavye girdisi kabul etmeye hazır olmasını bekler. Altyapısı denetimi herhangi bir işlem yapmadan önce hazır olmasını beklemek için bu API tüm eylemler için örtük olarak çağırır. Ancak, belirli nadir bulunan senaryoda açık çağrı yapmanız gerekebilir.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A>  
  
 Denetimin sihirbaz sunucuya çağrılar yaparak Giriş zaman uyumsuz bazı doğrulama zaman etkin olmasını bekler. Örneğin, bekleme yöntemi yapabilir **sonraki** olmasını etkin () Sihirbazı'nın düğmesi. Bu yöntem bir örnek için bkz: [izlenecek yol: oluşturma, düzenleme ve kodlanmış UI testini sürdürme](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlExist%2A>  
  
 Kullanıcı Arabirimi üzerindeki görünmesi denetimi bekler. Örneğin, uygulama parametrelerin doğrulanmasını tamamladıktan sonra bir hata iletişim kutusu bekliyorsunuz. Doğrulama için harcanan süre değişkenidir. Hata iletişim kutusunu beklemek için bu yöntemi kullanabilirsiniz.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlNotExist%2A>  
  
 Kullanıcı Arabiriminden kayboluyor denetimi bekler. Örneğin, ilerleme çubuğu kaybolmasını bekleyebilirsiniz.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyEqual%2A>  
  
 Verilen değer sağlamak için denetimi belirtilen özellik için bekler. Örneğin, durum metni değiştirmek beklemeniz **Bitti**.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyNotEqual%2A>  
  
 Belirtilen bir değeri karşıtı olmasını denetimi belirtilen özellik için bekler. Örneğin, salt okunur olmaması düzenleme kutusu için diğer bir deyişle, bekleyin düzenlenebilir.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlCondition%2A>  
  
 Belirtilen önerme olmasını döndürür bekler `true`. Bu karmaşık bekleme işlemi (veya koşulları gibi) belirli bir denetim için kullanılabilir. Örneğin, durum metni kadar bekleyebilirsiniz **başarılı** veya **başarısız** aşağıdaki kodda gösterildiği gibi:  
  
```csharp  
  
// Define the method to evaluate the condition   
private static bool IsStatusDone(UITestControl control)   
{   
    WinText statusText = control as WinText;   
    return statusText.DisplayText == "Succeeded" || statusText.DisplayText == "Failed";   
}   
  
// In test method, wait till the method evaluates to true   
statusText.WaitForControlCondition(IsStatusDone);  
  
```  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForCondition%2A>  
  
 Tüm önceki, UITestControl'un örnek yöntemleridir. Bu yöntem statik bir yöntemdir. Bu yöntem ayrıca belirtilen bir koşulu olması bekler `true` ancak birden çok denetimde (veya koşulları gibi) karmaşık bekleme işlemi için kullanılabilir. Örneğin, durum metni kadar bekleyebilirsiniz **başarılı** veya kadar aşağıdaki kodda gösterildiği gibi bir hata iletisi görüntülenir:  
  
```csharp  
  
// Define the method to evaluate the condition   
private static bool IsStatusDoneOrError(UITestControl[] controls)   
{   
    WinText statusText = controls[0] as WinText;   
    WinWindow errorDialog = controls[1] as WinWindow;   
    return statusText.DisplayText == "Succeeded" || errorDialog.Exists;   
}   
  
// In test method, wait till the method evaluates to true   
UITestControl.WaitForCondition<UITestControl[]>(new UITestControl[] { statusText, errorDialog }, IsStatusDoneOrError);  
  
```  
  
 Bu yöntemler aşağıdaki davranışa sahiptir:  
  
 Yöntemleri bekleme başarısız olursa bekleme başarılı ve false ise, true döndürür.  
  
 Bekleme işlemi için örtülü zaman aşımı tarafından belirtilen <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyTimeout%2A> özelliği. Bu özelliğin varsayılan değerini 60000 (bir dakika) milisaniyedir.  
  
 Milisaniye cinsinden açık zaman aşımı yapılacak bir aşırı yöntemi vardır. Ancak, bekleme işlem bir örtük aramada denetimi için veya uygulama meşgul olduğunda sonuçlandığında gerçek bekleme süresi belirtilen zaman aşımı değeri fazla olabilir.  
  
 Önceki işlevler güçlü ve esnektir ve neredeyse tüm koşulları karşılaması gerekir. Ancak, durumda bu yöntemler gereksinimlerinizi karşılamadığı ve ya da kod gerek bir <xref:Microsoft.VisualStudio.TestTools.UITesting.Playback.Wait%2A>, veya bir <xref:System.Threading.Thread.Sleep%2A> kodunuzda Thread.Sleep() API yerine Playback.Wait() kullanmanız önerilir. Bunun nedenleri şunlardır:  
  
 Kullanabileceğiniz <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.ThinkTimeMultiplier%2A>uyku süresini değiştirmek için özellik. Varsayılan olarak, bu değişken 1'dir ancak artırabilir veya kod'dünyanın dört bir yanındaki bekleme süresini değiştirmek için azaltabilirsiniz. Örneğin, özellikle yavaş ağ veya başka bir yavaş performans çalışması üzerinde test ediyorsanız, tüm konumlarda % 50 ilave bekleme eklemek için 1.5 için bu değişkeni bir yerde (veya hatta yapılandırma dosyasında) değiştirebilirsiniz.  
  
 Playback.Wait() içten Thread.Sleep() çağırır (sonra hesaplama yukarıda) için-kullanıcı cancel\break işlemi için denetlenirken döngü daha küçük parçalar. Diğer bir deyişle, Playback.Wait() sağlar ancak kayıttan yürütme beklemeyi sona önce iptal uyku değil veya özel durum.  
  
> [!TIP]
>  Kodlanmış UI Test Düzenleyicisi'ni kolayca kodlanmış UI testleri değiştirmenize olanak tanır. Kodlanmış UI Test Düzenleyicisi'ni kullanarak bulun, görüntülemek ve test yöntemlerinizi düzenleyin. Ayrıca, kullanıcı Arabirimi eylemlerini ve UI denetim eşlemesindeki ilişkili denetimlerini düzenleyebilirsiniz. Daha fazla bilgi için bkz: [kodlanmış UI Test Düzenleyicisi'ni kullanarak düzenleme kodlanmış UI testlerini](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
 **Kılavuz**  
  
 Ek bilgi için bkz: [Visual Studio 2012 - bölüm 5 ile sürekli teslimat için test etme: Sistem testlerini otomatikleştirme](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)   
 [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [İzlenecek yol: Oluşturma, düzenleme ve kodlanmış UI testi sürdürme](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)   
 [Kodlanmış UI testinin anatomisi](../test/anatomy-of-a-coded-ui-test.md)   
 [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Nasıl yapılır: kodlanmış UI Test Düzenleyicisi'ni kullanarak bir UI eyleminden önce gecikme ekleme](http://msdn.microsoft.com/Library/509f8ef7-e105-4049-b11b-d64549e055b0)