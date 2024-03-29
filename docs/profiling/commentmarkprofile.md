---
title: CommentMarkProfile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkProfile
- CommentMarkProfileA
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d45bab6b909fffa107158236d9050632f114c530
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74772799"
---
# <a name="commentmarkprofile"></a>CommentMarkProfile
`CommentMarkProfile` işlevi, içinde bir sayısal işaret ve metin dizesi ekler. *VSP* dosyası. İşaret ve Açıklama eklenecek şekilde, `CommentMarkProfile` işlevi içeren iş parçacığının profil oluşturma açık olmalıdır.

## <a name="syntax"></a>Sözdizimi

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(
                                   long lMarker,
                                   LPCTSTR szComment);
```

#### <a name="parameters"></a>Parametreler
 `lMarker`

 Eklenecek sayısal işaret. İşaretleyici 0 (sıfır) değerinden büyük veya buna eşit olmalıdır.

 `szComment`

 Eklenecek metin dizesinin işaretçisi. Dize, NULL Sonlandırıcı dahil 256 karakterden az olmalıdır.

## <a name="property-valuereturn-value"></a>Özellik değeri/dönüş değeri
 İşlev, **PROFILE_COMMAND_STATUS** numaralandırma kullanılarak başarılı veya başarısız olduğunu gösterir. Dönüş değeri aşağıdakilerden biri olabilir:

|Sının|Açıklama|
|----------------|-----------------|
|MARK_ERROR_MARKER_RESERVED|Parametre 0 ' dan küçük veya buna eşit. Bu değerler ayrılmıştır. İşaret ve açıklama kaydedilmez.|
|MARK_ERROR_MODE_NEVER|Profil oluşturma modu, işlev çağrıldığında hiçbir zaman olarak ayarlanmıştır. İşaret ve açıklama kaydedilmez.|
|MARK_ERROR_MODE_OFF|İşlev çağrıldığında profil oluşturma modu OFF olarak ayarlanmıştır. İşaret ve açıklama kaydedilmez.|
|MARK_ERROR_NO_SUPPORT|Bu bağlamda işaret desteği yok. İşaret ve açıklama kaydedilmez.|
|MARK_ERROR_OUTOFMEMORY|Olayı kaydetmek için bellek yoktu. İşaret ve açıklama kaydedilmez.|
|MARK_TEXTTOOLONG|Dize en fazla 256 karakter sınırını aşıyor. Açıklama dizesi kesilir ve işaret ve açıklama kaydedilir.|
|MARK_OK|Başarıyı göstermek için MARK_OK döndürülür.|

## <a name="remarks"></a>Açıklamalar
 İşaret profili işlevini içeren iş parçacığının profil oluşturma durumu, VSInstr Mark komutuyla veya işlevlerle (CommentMarkAtProfile, CommentMarkProfile veya MarkProfile) eklenen işaretler ve açıklamalar olduğunda açık olmalıdır.

 Profil işaretleri kapsamda geneldir. Örneğin, bir iş parçacığında yerleştirilen bir profil işareti, içindeki herhangi bir iş parçacığında bir veri segmentinin başlangıcını veya sonunu işaretlemek için kullanılabilir. *VSP* dosyası.

> [!IMPORTANT]
> CommentMarkProfile yöntemi, yalnızca izleme ile kullanılabilir.

## <a name="net-framework-equivalent"></a>.NET Framework eşdeğeri
 Microsoft. VisualStudio. Profiler. dll

## <a name="function-information"></a>İşlev bilgileri

|||
|-|-|
|**Üst bilgi**|VSPerf. h dahil et|
|**Kitaplığı**|VSPerf. lib kullanın|
|**Unicode**|`CommentMarkProfileW` (Unicode) ve `CommentMarkProfileA` (ANSI) olarak uygulanır.|

## <a name="example"></a>Örnek
 Aşağıdaki kod, CommentMarkProfile işlev çağrısını gösterir. Örnek, kodun [!INCLUDE[vcpransi](../profiling/includes/vcpransi_md.md)] işlev çağrısını çağırıp çağırmadığını öğrenmek için Win32 dize makroları ve Unicode derleyicisi ayarlarının kullanımını varsayar.

```cpp
void ExerciseCommentMarkProfile()
{
    // Declare and initalize variables to pass to
    // CommentMarkProfile.  The values of these
    // parameters are assigned based on the needs
    // of the code; and for the sake of simplicity
    // in this example, the variables are assigned
    // arbitrary values.
    long markId = 01;
    TCHAR * markText = TEXT("Exercising CommentMarkProfile...");

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare MarkOperationResult Enumerator.
    // Holds return value from call to CommentMarkProfile.
    PROFILE_COMMAND_STATUS markResult;

    markResult = CommentMarkProfile(
        markId,
        markText);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("CommentMarkProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, markResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio profil oluşturucu API başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)
