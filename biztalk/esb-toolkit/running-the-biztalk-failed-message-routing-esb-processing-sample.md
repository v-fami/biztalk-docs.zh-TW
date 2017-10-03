---
title: "執行 BizTalk 失敗訊息路由 ESB 處理範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2a536a0-cfc8-4ba3-adcd-2b8b580bff85
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a19f8c29c22638be97ae62dfea88d0d2feca6c55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-biztalk-failed-message-routing-esb-processing-sample"></a>執行 BizTalk 失敗訊息路由 ESB 處理範例
Microsoft BizTalk 失敗訊息路由 ESB 處理的範例，示範如何使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]做為通用的機制來管理、 序列化，以及轉譯中的所有條件之下發生例外狀況的例外狀況管理架構[!INCLUDE[prague](../includes/prague-md.md)]. 這包括產生 BizTalk 失敗訊息路由機制和錯誤訊息從例外狀況管理架構，協調流程內所產生的例外狀況。  
  
 BizTalk 失敗訊息路由機制是的錯誤處理功能[!INCLUDE[prague](../includes/prague-md.md)]; 藉由使用設計工具可以指定自動化的處理傳訊失敗做為替代的傳統 （現在的預設行為） 放置失敗「 擱置 」 佇列中的訊息。 這會自動處理路由至任何訂閱路由目的地，像是傳送埠或協調流程的錯誤訊息。 錯誤訊息是原始訊息已降級之所有先前升級屬性與選取的屬性升級至訊息內容與特定傳訊失敗相關的複製。  
  
 若要啟用的接收埠或傳送埠上的 BizTalk 失敗訊息路由機制，請選取**啟用的路由失敗訊息**核取方塊，如圖 1 所示。  
  
 ![啟用路由](../esb-toolkit/media/ch6-enabledrouting.gif "第 6 章第 EnabledRouting")  
  
 **圖 1**  
  
 **啟用 BizTalk 失敗訊息路由的機制**  
  
 不過，沒有任何錯誤或失敗的協調流程中發生類似的機制。 相反地，在協調流程的例外狀況處理常式的程式碼可以利用例外狀況管理架構 API 來模擬 BizTalk 失敗訊息路由機制的功能。  
  
 在此範例中，名為 EAIProcess.RequestPort_FILE 接收位置拾取檔案複製到位置 \Source\Samples\Exception Handling\Test\Filedrop\EAIProcess.RequestPort。  
  
 此外，是泛型的傳送埠命名為全部。Exceptions_FILE 設定為使用 GlobalFaultProcessor 管線安裝在例外狀況管理架構的一部分。 此連接埠會訂閱在系統中發生的所有例外狀況，這兩個 BizTalk 失敗訊息路由遞送的訊息與 ESB 錯誤訊息，如圖 2 所示。  
  
 ![傳送埠](../esb-toolkit/media/ch6-sendport.gif "第 6 章第傳送埠")  
  
 **圖 2**  
  
 **ALL。例外狀況的傳送埠訂閱，所有類型的錯誤或例外狀況**  
  
 例外狀況管理架構正規化為單一格式的所有例外狀況，並將它們使用位置 \Source\Samples\Exception Handling\Test\Filedrop\All_Exceptions Microsoft InfoPath 處理指示序列化。  
  
## <a name="installation"></a>安裝  
 所有例外狀況管理範例使用相同的核心服務和 BizTalk 應用程式成品。 因此，您必須安裝要能夠管理範例執行的所有例外狀況的例外狀況管理範例成品一次。 如需如何安裝例外狀況管理範例，請參閱[安裝例外狀況管理範例](../esb-toolkit/installing-the-exception-management-samples.md)。  
  
## <a name="running-the-sample-application"></a>執行範例應用程式  
 **執行 BizTalk 失敗訊息路由 ESB 處理範例**  
  
1.  您第一次執行此範例之前，請確定該接收位置和傳送連接埠 URL 指向 \Source\Samples\Exception Handling\Test\Filedrop 資料夾中的適當目錄。 接收位置應該指定資料夾 EAIProcess.RequestPort，而傳送連接埠 URL 應該指定 All_Exceptions 的資料夾。  
  
2.  如果尚未執行 GlobalBank.ESB 應用程式，使用 BizTalk 管理主控台來啟動它。  
  
3.  從資料夾 \Source\Samples\Exception Handling\Test\Data FlatFileReceive_in.txt 具名命名 EAIProcess.RequestPort （\Source\Samples\Exception Handling\Test\Filedrop 資料夾中） 的接收位置資料夾將檔案複製。  
  
4.  這個訊息是文字檔案，而將會造成例外狀況。 開啟名為 All_Exceptions （在 \Source\Samples\Exception Handling\Test\Filedrop 資料夾中） 的資料夾，然後按兩下 錯誤訊息，以開啟在 InfoPath 使用適當的範本。 您會看到的 ESB 例外狀況處理機制適當序列化內容，以允許 InfoPath 進行轉譯。  
  
5.  接下來，將具名 EAIProcess.RequestPort 從資料夾 \Source\Samples\Exception Handling\Test\Data soapmessage [1].xml 檔案複製接收位置資料夾中。  
  
6.  這個訊息是 XML 文件，其中包含 CDATA 區段內，而將會造成例外狀況。 開啟 All_Exceptions 輸出資料夾，然後按兩下以開啟在 InfoPath 的錯誤訊息。 您會看到的 ESB 例外狀況處理機制適當地序列化此內容，以允許 InfoPath 進行轉譯。  
  
7.  最後，將從資料夾 \Source\Samples\Exception Handling\Test\Data 具名 EAIProcess.RequestPort Csqzav01.pdf 檔案複製接收位置。  
  
8.  這個訊息是 PDF 檔案，而將會造成例外狀況。 開啟 All_Exceptions 輸出資料夾，然後按兩下以開啟在 InfoPath 中的錯誤訊息。 您會看到的 ESB 例外狀況處理機制序列化 Base 64 編碼的內容，以允許進行轉譯 InfoPath。