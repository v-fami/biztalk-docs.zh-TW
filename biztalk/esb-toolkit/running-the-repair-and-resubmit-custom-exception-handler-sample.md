---
title: 執行修復和重新提交自訂例外狀況處理常式範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7363c440-44aa-4d08-8290-72787d17ac60
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34bb03565f7b044f9c6c2f29332862ae8aafef7e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004479"
---
# <a name="running-the-repair-and-resubmit-custom-exception-handler-sample"></a>執行修復和重新提交自訂例外狀況處理常式範例
「 修復和重新提交自訂例外狀況處理常式 」 範例示範非常有效的技術，將人為介入整合到 ESB 和 Microsoft BizTalk 型應用程式處理，並會實作實用的設計模式。 範例程式碼緊密整合到 ESB 例外狀況管理系統。  
  
 此範例會示範如何使用自訂的例外狀況處理常式，以及在協調流程中。 當協調流程 (EAIProcess.odx) 中的程序發生錯誤時，例外狀況處理常式就會產生，並發佈 ESB 錯誤訊息。 此錯誤訊息是 「 在途中 」 訊息 （包括其相關的 BizTalk 內容屬性） 包含其承載中發生例外狀況和 BizTalk 協調流程引擎攔截到目前的 System.Exception 執行個體。 當發生這種情況時，「 拒絕 」 的訊息和 「 Approved 」 訊息會保存並顯示錯誤訊息。  
  
 名為 EAIProcessHandler.odx 部署低耦合的方式，且可做為自訂的例外狀況處理常式，第二個協調流程訂閱產生 EAIProcess.odx 協調流程中的特定錯誤程式碼，並使用錯誤訊息。 這個例外狀況處理常式會擷取原始的訊息 （做為具類型的文件） 和錯誤訊息中原本保存 System.Exception 執行個體。  
  
 原始訊息現在會變成可供處理，其原始的內容屬性的項目。 自訂例外狀況處理常式 (EAIProcessHandler.odx) 然後會將 「 拒絕 」 和 「 Approved 」 訊息寫入至檔案系統中的下列位置：  
  
- 已核准的訊息：  
  
  -   \Source\Samples\Exception Handling\Test\Filedrop\EAIProcess.PostApproval  
  
- 拒絕的訊息修復和重新提交：  
  
  -   \Source\Samples\Exception Handling\Test\Filedrop\EAIProcessHandler.RepairSubmit  
  
- 拒絕的訊息：  
  
  -   \Source\Samples\Exception Handling\Test\Filedrop\EAIProcessHandler.PostDecline  
  
  例外狀況處理常式會將"Denied"訊息修復和重新提交序列化至檔案系統使用的 Microsoft InfoPath 處理指示。 InfoPath 範本可讓使用者編輯表單，並重新提交結果 （請參閱 圖 1），這會開始驗證訊息 EAIProcess.odx 協調流程。  
  
  ![修復重新提交](../esb-toolkit/media/ch6-repairresubmit.gif "第 6 章第 RepairResubmit")  
  
  **圖 1**  
  
  **InfoPath 修復和重新提交範本所產生的測試訊息**  
  
  此外，還有名為所有的泛型的傳送埠。已設定為使用 GlobalFaultProcessor 管線的 Exceptions_FILE。 此連接埠訂閱系統中的所有例外狀況，這兩個 BizTalk 失敗訊息路由遞送的訊息與 ESB 錯誤訊息。 例外狀況管理架構將它們正規化所有成單一的格式和序列化使用資料夾 \Source\Samples\Exception Handling\Test\Filedrop\All_Exceptions InfoPath 處理指示。  
  
## <a name="installation"></a>安裝  
 所有例外狀況管理範例會使用相同的一組核心服務和 BizTalk 應用程式成品。 因此，您必須要能夠執行所有的例外狀況管理範例安裝例外狀況管理範例成品只有一次。 如需有關如何安裝例外狀況管理範例的資訊，請參閱 <<c0> [ 安裝例外狀況管理範例](../esb-toolkit/installing-the-exception-management-samples.md)。  
  
## <a name="running-the-sample-application"></a>執行範例應用程式  
 **若要執行修復和重新提交自訂例外狀況處理常式範例**  
  
1.  第一次執行此範例之前，請確定接收位置和傳送埠 Url 指向 \Source\Samples\Exception Handling\Test\Filedrop 資料夾中的適當目錄。 接收位置應該指定資料夾 EAIProcess.RequestPort，並傳送連接埠 Url 應該指定 EAIProcess.PostApproval 和 EAIProcessHandler.PostDecline 的資料夾。  
  
2.  如果尚未執行 GlobalBank.ESB 應用程式，使用 BizTalk 管理主控台來啟動它。  
  
3.  藉由複製名為 Request_EAIProcessHandler.xml，\Source\Samples\Exception Handling\Test\Data 資料夾中，指定 EAIProcess.RequestPort_FILE 接收位置的資料夾中的範例檔案，啟動範例： \Source\Samples\例外狀況 Handling\Test\Filedrop\EAIProcess.RequestPort。  
  
4.  開啟名為 EAIProcessHandler.PostDecline （\Source\Samples\Exception Handling\Test\Filedrop 資料夾中） 的資料夾。 您會看到 「 已拒絕 * 」 訊息的例外狀況處理協調流程所產生。  
  
5.  開啟名為 EAIProcessHandler.RepairSubmit （\Source\Samples\Exception Handling\Test\Filedrop 資料夾中） 的資料夾。 您會看到 「 RepairSubmit 」 訊息的例外狀況處理協調流程所產生。  
  
6.  按兩下 RepairSubmit 檔案，在適當的 InfoPath 範本中加以開啟。 您會看到 準備好進行編輯並重新提交訊息。  
  
7.  值變更**單價**欄位從**0**來**2**，然後按一下**提交**按鈕位於工具列上的 InfoPath若要提交回 BizTalk 處理編輯的文件的表單。 提交程序使用的設定 BizTalk HTTP 接收位置。  
  
8.  瀏覽至 EAIProcess.PostApproval 資料夾中 （在 [\Source\Samples\Exception Handling\Test\Filedrop] 資料夾中）。 現在，您會看到包含單價的更新的值的 「 核准 * 」 文件。  
  
## <a name="how-the-sample-works"></a>此範例的運作方式  
 您所提交的訊息啟動 EAIProcess 協調流程。 EAIProcess 協調流程處理訊息時，它會嘗試將 1 除以單價。 因為單位價格為零，就會發生除以零例外狀況。 協調流程的事件處理常式中的程式碼會攔截此例外狀況，並建立錯誤訊息。 訊息中的訂單數量大於 10，因此商務邏輯決定此例外狀況已**d**欄位的值**1000年**。  
  
 EAIProcess 協調流程接著會將錯誤訊息發佈到 BizTalk Message Box，透過直接繫結連接埠和協調流程結束。  
  
 自訂錯誤處理常式的協調流程，名為 EAIProcessHandler，其訂閱的訊息**d**欄位的值**1000年**，挑選新的錯誤訊息。 協調流程中的程式碼會建立 「 拒絕 」 訊息和 InfoPath 檔案，而且再放這到 EAIProcessHandler.PostDecline 和 EAIProcessHandler.RepairSubmit 資料夾供人為介入。