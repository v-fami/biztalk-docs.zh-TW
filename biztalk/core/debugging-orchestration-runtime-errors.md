---
title: "偵錯協調流程執行階段錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7be9ee5a-b9fa-428b-8b92-0fa0f801c724
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36e881f8449e7aaac7aeade12c36c3c6d942ef12
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="debugging-orchestration-runtime-errors"></a>偵錯協調流程執行階段錯誤
本節包含設計用來協助您解決協調流程執行階段問題的問答集。  
  
## <a name="why-do-i-get-intermittent-subscription-errors-when-sending-to-a-child-orchestration-that-was-just-started-by-the-parent"></a>為何在傳送至剛由父協調流程啟動的子協調流程時，得到間歇性的訂閱錯誤？  
 訂閱錯誤「找不到訂閱」是競爭條件的結果。 競爭條件是指根據程序發生的特定順序來決定程序的結果。 在此案例中，當子協調流程未及時啟動來接收父協調流程傳送的訊息時，便會產生此競爭條件。  
  
 若要避免這個問題，子協調流程可在啟動後準備接收訊息時，傳送訊息給父協調流程。 如此一來，在傳送訊息之前，啟動子協調流程的父協調流程就會知道有接收器。  
  
## <a name="why-do-i-get-errors-when-i-attach-a-dynamic-send-port-to-a-logical-port"></a>為什麼當我將動態傳送埠附加至邏輯連接埠時，得到錯誤？  
 動態連接埠不是設計為繼承指派給它的所有連接埠屬性和特性。 動態連接埠只取得位址，不會繼承與邏輯連接埠關聯的其他資訊。  
  
 例如，如果將動態傳送埠附加至標示為 Delivery Notification = Transmitted 的邏輯連接埠，執行階段將不會傳送傳遞通知。 如果實際上透過該方法靜態設定連接埠，XLANGs 執行階段只會偵聽傳遞通知。  
  
> [!NOTE]
>  在 XLANGs，只有在靜態設定連接埠時，連接埠才會運作。  
  
## <a name="when-i-try-to-run-my-application-after-deploying-an-orchestration-with-custom-components-why-do-i-get-the-error-file-or-assembly-name-or-one-of-its-dependencies-not-found"></a>在部署具有自訂元件的協調流程之後，當我嘗試執行應用程式時，為何得到錯誤，指出找不到檔案或組件名稱或其相依檔案或組件的其中之一？  
 這個錯誤通常表示 BizTalk 協調流程引擎找不到自訂元件。 您必須在裝載應用程式的電腦上，將 BizTalk 應用程式中包含的所有組件安裝在全域組件快取中。  
  
## <a name="an-assemblyname-context-property-was-not-valid-error-occurs-when-submitting-a-document-to-a-web-service-via-an-orchestration"></a>透過協調流程將文件提交至 Web 服務時，發生 AssemblyName 內容屬性無效錯誤  
  
### <a name="problem"></a>問題  
 透過協調流程將文件提交至 Web 服務，造成 AssemblyName 內容屬性無效錯誤。  
  
### <a name="cause"></a>原因  
 BizTalk 應用程式原來設計為使用「傳訊」方法，而非中間的協調流程。 這種解決方案類型會使用傳送埠篩選條件來連結接收埠和傳送埠，讓文件能在接收時通過到達傳送埠。 之後，解決方案會修改為包含繫結至傳送埠的協調流程。  
  
### <a name="resolution"></a>解決方案  
 移除傳送埠上的篩選條件。 如果您在繫結至協調流程的傳送埠上套用篩選條件，訊息通常會略過協調流程並造成內容屬性錯誤。  
  
## <a name="a-wrongbodypartexception-occurs-when-handling-a-multipart-mime-message-in-an-orchestration"></a>在協調流程中處理多部分 MIME 訊息時，發生 "WrongBodyPartException"  
  
### <a name="problem"></a>問題  
 為協調流程接收多部分 MIME 訊息導致**WrongBodyPartException**例外狀況。  
  
### <a name="cause"></a>原因  
 如果不正確指定訊息部分的順序，或訊息不符合指定的部分位置，就會發生這個錯誤。 例如，如果您指定第三個部分是內文部分，但送達的訊息中第三個位置卻是標頭部分。  
  
### <a name="resolution"></a>解決方案  
 驗證內文部分索引設定是否正確，接著確認透過配接器送達的所有訊息是否都與設定一致。 您可以停止協調流程 (但保持登錄)，檢查在協調流程中失敗 MIME 訊息的內容。這會強制訊息發佈，所以您可以使用管理主控台來檢查訊息並驗證部分順序。  
  
## <a name="multipart-mime-message-part-cannot-be-found"></a>找不到多部分 MIME 訊息部分  
  
### <a name="problem"></a>問題  
 嘗試擷取 MIME 訊息部分的索引值大於 0 的結果，在 BizTalk Server 執行階段擲回類似的錯誤 「 找不到具有索引的多部分訊息 =\<值 > 」。  
  
### <a name="cause"></a>原因  
 導致這個錯誤的最常見原因包括：  
  
-   MIME 訊息部分少於預期。  
  
-   無法完全剖析 MIME 訊息。  
  
### <a name="resolution"></a>解決方案  
 藉由確認程式碼只從訊息來源預期的範圍內擷取訊息部分，可以解決這個問題。 在剖析問題這部分，您應該驗證原始 MIME 訊息的結構完整且已正確建構。 如果您預期偶爾會發生剖析問題，請確認協調流程有適當的例外狀況處理常式。  
  
## <a name="you-receive-a-the-file-send-adapter-cannot-open-file-for-writing-error-when-sending-using-a-dynamic-send-port"></a>使用動態傳送埠進行傳送時收到「FILE 傳送配接器無法開啟檔案進行寫入」錯誤  
  
### <a name="problem"></a>問題  
 您會收到 「 FILE 傳送配接器無法開啟檔案*\<檔名 >*進行寫入 」 錯誤時使用動態傳送 BizTalk Server 事件記錄檔中的傳送埠。  
  
 發生此問題時**BTS。OutBoundTransportLocation**屬性已定義在協調流程運算式中和已指定檔案傳輸，例如，下列運算式會造成這個錯誤，在執行階段：  
  
```  
Message2=Message1;  
Message2(BTS.OutboundTransportLocation) = "file:///c:/test/out";  
MySendPort(Microsoft.XLANGs.BaseTypes.Address)=Message2(BTS.OutboundTransportLocation);  
```  
  
 \-或者-  
  
```  
Message2=Message1;  
Message2(BTS.OutboundTransportLocation) = "file://mymachine/test/out";  
MySendPort(Microsoft.XLANGs.BaseTypes.Address)=Message2(BTS.OutboundTransportLocation);  
```  
  
### <a name="cause"></a>原因  
 因為協調流程引擎會在執行階段移除文字，就會發生這個問題 「**file://"**從指定的 URL。 因此，使用上述範例時，"file:///c:/test/out" 為評估為 \c:\test\out，而 "file://mymachine/test/out" 會評估為 mymachine\test\out。  
  
### <a name="resolution"></a>解決方案  
 當指定之 URL 的**BTS。OutBoundTransportLocation**屬性的運算式中，新增或移除"/"字元視。 使用上述範例**BTS。OutBoundTransportLocation**屬性應定義為"file://c:/test/out"，這會評估為 c:\test\out 或 「 file:///mymachine/test/out"，這會評估為\\\mymachine\test\out。