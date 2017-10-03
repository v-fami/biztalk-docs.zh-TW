---
title: "執行保存自訂例外狀況處理常式範例訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0a4c819-f6bd-4dea-8be9-e3006337665f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6d7927357e4c2be03ecd8b2e77d45558b5bc692
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-message-persisting-custom-exception-handler-sample"></a>執行保存自訂例外狀況處理常式範例訊息
訊息保存自訂例外狀況處理常式範例示範鬆散偶合的一般處理常式會收到錯誤訊息時，會擷取包含此項目，並將其以磁碟檔案寫入至檔案系統的 Microsoft BizTalk 訊息。  
  
 此範例顯示如何在協調流程中使用的自訂例外狀況處理常式。 當處理程序協調流程 (EAIProcess.odx) 中的發生錯誤時，會產生例外狀況處理常式，並發佈 ESB 錯誤訊息。 此錯誤訊息納入其裝載了 「 在途中 」 訊息 （包括其 BizTalk 相關的內容屬性） 發生例外狀況，以及 BizTalk 協調流程引擎捕捉到的目前 System.Exception 執行個體。 當發生這種情況時，會保存 「 拒絕 」 的訊息和 「 已核准 」 訊息與錯誤訊息。  
  
 名為 EAIGenericHandler.odx 解除解合的方式部署並做為自訂例外狀況處理常式，在第二個協調流程訂閱產生 EAIGenericHandler.odx 協調流程中的特定錯誤程式碼，並使用錯誤訊息。 這個例外狀況處理常式中擷取原始的訊息 （做為無類型的文件） 並將 System.Exception 執行個體原本保存在錯誤訊息。  
  
 訊息保存自訂例外狀況處理常式範例與修復，再重新送出的自訂例外狀況處理常式範例的這個範例中使用 EAIGenericHandler.odx 協調流程沒有錯誤發行中使用的結構描述的相依性協調流程程序 (EAIProcess.odx)。 具體來說，EAIGenericHandler.odx 協調流程擷取的原始訊息的錯誤訊息當做 System.Xml.XmlDocument 執行個體，而不是根據 EAIProcess.odx 協調流程中使用的結構描述具類型的訊息。 它也會傳回訊息做為程式碼輕鬆地可列舉集合。  
  
 自訂例外狀況處理常式 (EAIGenericHandler.odx) 然後將 「 已拒絕 」 和 「 已核准 」 訊息寫入檔案系統位置 \Source\Samples\Exception Handling\Test\Filedrop\EAIGenericHandler.PostTmpMsg。  
  
 此外，是泛型的傳送埠命名為全部。Exceptions_FILE 設定為使用隨 GlobalFaultProcessor 管線[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]例外狀況管理架構。 此連接埠訂閱系統中的所有例外狀況，這兩個 BizTalk 失敗訊息路由遞送的訊息與 ESB 錯誤訊息。 例外狀況管理架構正規化它們全部加入一種格式，並將它們使用位置 \Source\Samples\Exception Handling\Test\Filedrop\All_Exceptions Microsoft InfoPath 處理指示序列化。  
  
## <a name="installation"></a>安裝  
 所有例外狀況管理範例使用相同的核心服務和 BizTalk 應用程式成品。 因此，您必須安裝要能夠管理範例執行的所有例外狀況的例外狀況管理範例成品一次。 如需如何安裝例外狀況管理範例，請參閱[安裝例外狀況管理範例](../esb-toolkit/installing-the-exception-management-samples.md)。  
  
## <a name="running-the-sample-application"></a>執行範例應用程式  
 **若要執行訊息保存自訂例外狀況處理常式範例**  
  
1.  您第一次執行此範例之前，請確定該接收位置和傳送連接埠 URL 指向 \Source\Samples\Exception Handling\Test\Filedrop 資料夾中的適當目錄。 接收位置應該指定資料夾 EAIProcess.RequestPort，而傳送連接埠 URL 應該指定 EAIGenericHandler.PostTmpMsg 的資料夾。  
  
2.  如果尚未執行 GlobalBank.ESB 應用程式，使用 BizTalk 管理主控台來啟動它。  
  
3.  藉由複製名為 Request_EAIGenericHandler.xml，\Source\Samples\Exception Handling\Test\Data 資料夾，以指定 EAIProcess.RequestPort_FILE 接收位置的資料夾中的範例檔案啟動範例： \Source\Samples\例外狀況 Handling\Test\Filedrop\EAIProcess.RequestPort。  
  
4.  開啟名為 EAIGenericHandler.PostTmpMsg （\Source\Samples\Exception Handling\Test\Filedrop\ 資料夾中） 的資料夾。 您會看到原始的訊息。  
  
## <a name="how-the-sample-works"></a>範例的運作方式  
 您所提交的訊息啟動 EAIProcess 協調流程。 EAIProcess 協調流程處理訊息時，它會嘗試將 1 除以單價。 因為單價為零，就會發生除以零的例外狀況。 協調流程的事件處理常式中的程式碼會攔截此例外狀況，並建立錯誤訊息。 訊息中的訂單數量已低於 10，商務邏輯決定，此例外狀況，並讓**f**欄位的值**2000年**。  
  
 EAIProcess 協調流程接著會將錯誤訊息發佈到 BizTalk Messagebox 直接繫結連接埠和協調流程會結束。  
  
 自訂錯誤處理常式的協調流程，名為 EAIGenericHandler，訂閱訊息與**f**欄位的值**2000年**，挑選新的錯誤訊息。 協調流程中的程式碼會從例外狀況 （錯誤） 訊息中擷取的所有訊息，並將它們寫入磁碟檔案。