---
title: 執行修復並重新送出的自訂例外狀況處理常式範例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7363c440-44aa-4d08-8290-72787d17ac60
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b8b33765cbe3ca1c8c0c7c3e7679e543678325af
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="running-the-repair-and-resubmit-custom-exception-handler-sample"></a>執行修復並重新送出的自訂例外狀況處理常式範例
修復和重新提交的自訂例外狀況處理常式範例示範非常有效的技術，將人為介入整合到 ESB 和 Microsoft BizTalk 型應用程式處理，並實作實用的設計模式。 範例程式碼能夠在 ESB 例外狀況管理系統內緊密整合。  
  
 此範例顯示如何在協調流程中使用的自訂例外狀況處理常式。 當處理程序協調流程 (EAIProcess.odx) 中的發生錯誤時，會產生例外狀況處理常式，並發佈 ESB 錯誤訊息。 此錯誤訊息納入其裝載了 「 在途中 」 訊息 （包括其 BizTalk 相關的內容屬性） 例外狀況發生時，BizTalk 協調流程引擎捕捉到的目前 System.Exception 執行個體。 當發生這種情況時，會保存 「 拒絕 」 的訊息和 「 已核准 」 訊息與錯誤訊息。  
  
 名為 EAIProcessHandler.odx 解除解合的方式部署並做為自訂例外狀況處理常式，在第二個協調流程訂閱產生 EAIProcess.odx 協調流程中的特定錯誤程式碼，並使用錯誤訊息。 這個例外狀況處理常式中擷取原始的訊息 （做為具類型的文件） 並將 System.Exception 執行個體原本保存在錯誤訊息。  
  
 原始訊息現在會變成可用於處理及其原始的內容屬性。 自訂例外狀況處理常式 (EAIProcessHandler.odx) 然後將 「 已拒絕 」 和 「 已核准 」 訊息寫入檔案系統中的下列位置：  
  
-   核准的訊息：  
  
    -   \Source\Samples\Exception Handling\Test\Filedrop\EAIProcess.PostApproval  
  
-   拒絕的修復和重新提交訊息：  
  
    -   \Source\Samples\Exception Handling\Test\Filedrop\EAIProcessHandler.RepairSubmit  
  
-   拒絕的訊息：  
  
    -   \Source\Samples\Exception Handling\Test\Filedrop\EAIProcessHandler.PostDecline  
  
 例外狀況處理常式會將"Denied"訊息修復和重新提交序列化至檔案系統使用的 Microsoft InfoPath 處理指示。 InfoPath 範本可讓使用者編輯表單並重新提交的結果 （請參閱圖 1），以便啟動 EAIProcess.odx 協調流程會驗證訊息。  
  
 ![修復重新提交](../esb-toolkit/media/ch6-repairresubmit.gif "第 6 章第 RepairResubmit")  
  
 **圖 1**  
  
 **InfoPath 修復和重新提交範本所產生的測試訊息**  
  
 此外，是泛型的傳送埠命名為全部。設定為使用 GlobalFaultProcessor 管線的 Exceptions_FILE。 此連接埠訂閱系統中的所有例外狀況，這兩個 BizTalk 失敗訊息路由遞送的訊息與 ESB 錯誤訊息。 例外狀況管理架構正規化它們全部加入一種格式，並將它們使用資料夾 \Source\Samples\Exception Handling\Test\Filedrop\All_Exceptions InfoPath 處理指示序列化。  
  
## <a name="installation"></a>安裝  
 所有例外狀況管理範例使用相同的核心服務和 BizTalk 應用程式成品。 因此，您必須安裝要能夠管理範例執行的所有例外狀況的例外狀況管理範例成品一次。 如需如何安裝例外狀況管理範例，請參閱[安裝例外狀況管理範例](../esb-toolkit/installing-the-exception-management-samples.md)。  
  
## <a name="running-the-sample-application"></a>執行範例應用程式  
 **若要執行修復，再重新送出的自訂例外狀況處理常式範例**  
  
1.  您第一次執行此範例之前，請確定接收位置和傳送埠 Url 指向 \Source\Samples\Exception Handling\Test\Filedrop 資料夾中的適當目錄。 接收位置應該指定資料夾 EAIProcess.RequestPort，而傳送連接埠 Url 應該指定 EAIProcess.PostApproval 以及 EAIProcessHandler.PostDecline 的資料夾。  
  
2.  如果尚未執行 GlobalBank.ESB 應用程式，使用 BizTalk 管理主控台來啟動它。  
  
3.  藉由複製名為 Request_EAIProcessHandler.xml，\Source\Samples\Exception Handling\Test\Data 資料夾，以指定 EAIProcess.RequestPort_FILE 接收位置的資料夾中的範例檔案啟動範例： \Source\Samples\例外狀況 Handling\Test\Filedrop\EAIProcess.RequestPort。  
  
4.  開啟名為 EAIProcessHandler.PostDecline （\Source\Samples\Exception Handling\Test\Filedrop 資料夾中） 的資料夾。 您會看到的例外狀況處理協調流程所產生的 「 已拒絕 * 」 訊息。  
  
5.  開啟名為 EAIProcessHandler.RepairSubmit （\Source\Samples\Exception Handling\Test\Filedrop 資料夾中） 的資料夾。 您會看到的例外狀況處理協調流程所產生的 「 RepairSubmit 」 訊息。  
  
6.  按兩下以開啟適當的 InfoPath 範本中的 RepairSubmit 檔案。 您會看到 準備好進行編輯並重新提交訊息。  
  
7.  值變更**單價**欄位從**0**至**2**，然後按一下 **送出**按鈕位於工具列上的 InfoPath表單提交回 BizTalk 處理已編輯的文件。 送出程序使用 BizTalk 設定的 HTTP 接收位置。  
  
8.  瀏覽至 EAIProcess.PostApproval 資料夾 （在 \Source\Samples\Exception Handling\Test\Filedrop 資料夾中）。 現在，您會看到包含單價的更新的值的 「 核准 * 」 文件。  
  
## <a name="how-the-sample-works"></a>範例的運作方式  
 您所提交的訊息啟動 EAIProcess 協調流程。 EAIProcess 協調流程處理訊息時，它會嘗試將 1 除以單價。 因為單價為零，就會發生除以零的例外狀況。 協調流程的事件處理常式中的程式碼會攔截此例外狀況，並建立錯誤訊息。 訊息中的訂單數量大於 10，所以商務邏輯決定此例外狀況有**f**欄位的值**1000年**。  
  
 EAIProcess 協調流程接著會將錯誤訊息發佈到 BizTalk Messagebox 直接繫結連接埠和協調流程會結束。  
  
 自訂錯誤處理常式的協調流程，名為 EAIProcessHandler，訂閱訊息與**f**欄位的值**1000年**，挑選新的錯誤訊息。 協調流程中的程式碼會建立"Denied"訊息和 InfoPath 檔案，並接著就會將這為 EAIProcessHandler.PostDecline 和 EAIProcessHandler.RepairSubmit 資料夾供人為介入。