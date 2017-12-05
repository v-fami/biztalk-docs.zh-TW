---
title: "收集例外狀況並將訊息路由修復和重新提交 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a61658a-0bac-4802-b506-02e61a3d2a9b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a1d080cc3b87cf371729c51e1b1f26e07ae521e
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="collecting-exceptions-and-routing-messages-for-repair-and-resubmit"></a>收集例外狀況並將訊息路由修復和重新提交
在此使用情況下，自訂例外狀況處理常式收到透過 Web 服務所收到的錯誤訊息，且將其路由傳送到磁碟檔案中隨附的 InfoPath 範本相容的格式[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。 使用者可以使用 Microsoft InfoPath 開啟檔案、 編輯訊息內容，並重新提交訊息以進行處理，如圖 1 所示。  
  
 ![收集例外狀況修復](../esb-toolkit/media/ch3-collectingexceptionsrepair.gif "Ch3 CollectingExceptionsRepair")  
  
 **圖 1**  
  
 **修復和重新提交的訊息路由傳送**  
  
 「 修復和重新提交的自訂例外狀況處理常式 」 範例隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。 當協調流程中的處理序會遇到錯誤，例外狀況處理常式，協調流程會產生和發佈 ESB 錯誤訊息。 此錯誤訊息包括，在承載中，訊息 （包括其內容屬性與 BizTalk Server） 的 「 在途中 」 時，發生例外狀況，而且目前的例外狀況攔截 BizTalk 協調流程引擎。 ESB 錯誤訊息會發佈後，就是要訂閱的協調流程 （自訂例外狀況處理常式），擷取和會檢查傳遞訊息，以及系統例外狀況物件，並將訊息路由傳送至檔案的資料夾中，從中取消佇列使用者可以編輯使用 InfoPath 的訊息，並在其重新提交到 BizTalk Server 進行處理。  
  
 如需詳細資訊，請參閱[執行修復並重新提交自訂例外狀況處理常式範例](../esb-toolkit/running-the-repair-and-resubmit-custom-exception-handler-sample.md)。