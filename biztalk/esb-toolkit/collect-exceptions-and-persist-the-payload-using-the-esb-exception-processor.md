---
title: "收集例外狀況，並將保存使用 ESB 例外狀況處理器裝載 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52650eed-e760-4ade-bc3f-2b5b2a1c43ff
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9dd0ec42ab60636202a8ff99fa8fab8d96a95a19
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="collecting-exceptions-and-persisting-the-payload-using-the-esb-exception-processor"></a>收集例外狀況，並將保存裝載使用 ESB 例外狀況處理器
在此使用情況下，協調流程的例外狀況處理常式會發佈 ESB 錯誤訊息到 BizTalk Server 訊息方塊，或是 BizTalk 失敗訊息路由的機制會產生錯誤訊息。 傳送埠，以 ESB 例外狀況編碼器管線元件，預先設定訂閱這兩個錯誤訊息類型。 它會處理錯誤訊息，並再將它們保存為磁碟檔案，您可以檢視使用 InfoPath，如圖 1 所示。  
  
 ![收集例外狀況承載](../esb-toolkit/media/ch3-collectingexceptionspayload.gif "Ch3 CollectingExceptionsPayload")  
  
 **圖 1**  
  
 **擷取錯誤訊息，並將它保存到磁碟檔案**  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包括下列：  
  
-   **預先設定傳送埠會使用 ESB 錯誤處理器傳送管線。** 您可以根據特定的需求來設定此傳送埠。  
  
-   **訊息保存自訂例外狀況處理常式範例。** 這個範例示範鬆散偶合的泛型例外狀況處理常式可以接收錯誤訊息的方式擷取它們包含、 標準化及擴充訊息，並以磁碟檔案將訊息寫入檔案系統的 BizTalk Server 訊息。  
  
-   **「 BizTalk 失敗訊息路由 」 範例。** 這個範例會示範如何 ESB 例外狀況管理架構標準化並充實原生失敗訊息路由機制在 BizTalk Server 所產生的錯誤訊息。  
  
 如需詳細資訊，請參閱[執行訊息保存自訂例外狀況處理常式範例](../esb-toolkit/running-the-message-persisting-custom-exception-handler-sample.md)和[執行 BizTalk 失敗訊息路由 ESB 處理範例](../esb-toolkit/running-the-biztalk-failed-message-routing-esb-processing-sample.md)。