---
title: FileAct 配接器狀態監視 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 15833004-4276-4975-a0e7-8fff3c82576b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c5b717a02631d47b864cc9180cba2fba673c5da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223038"
---
# <a name="fileact-adapter-status-monitoring"></a>FileAct 配接器狀態監視
在下圖說明可能的檔案傳輸，而這些狀態之間轉換的狀態。  
  
 ![FileAct 配接器檔案傳輸狀態](../../adapters-and-accelerators/fileact-interact/media/2e01feaa-6b68-49a2-a47d-6359be1f4034.gif "2e01feaa-6b68-49a2-a47d-6359be1f4034")  
  
 檔案傳輸狀態是：  
  
-   **起始**– 用戶端交涉訊息傳送至伺服器，但是尚未收到回應。 伺服器收到的交涉要求，但尚未傳送回應。  
  
-   **接受**： 伺服器已接受要求，並且可在回應訊息中傳送 TransferAnswer，並且傳送仍在進行中。  
  
-   **拒絕**– 伺服器已拒絕要求，並在回應訊息中，擁有 TransferAnswer，且已終止傳輸。  
  
-   **持續**– 傳送正在進行中，正在進行 （上述的定期更新）。  
  
-   **完成**– 檔案傳輸的傳送該端而言，包括摘要值的比較已順利完成。  
  
-   **無法**– 檔案傳輸失敗，因為資料存取，處理時，通訊或逾時例外狀況。 (注意： SWIFTNet 連結會強制執行逾時和值取決於 SWIFT)。  
  
-   **中止**– 已中止檔案傳輸 （其中端我中止的問題）。  
  
-   **未知及重複**– 此狀態發生於僅由於計時。 寄件者，在檔案應重新傳送標記為可能重複 (PDIndicator)。 在接收者，當 PDIndicator 意味著，檔案可能已傳送，FileAct 配接器會檢查是否重複，而且如果找到，會傳回 TransferAnswer 的重複，這將會終止目前的嘗試。  
  
## <a name="see-also"></a>另請參閱  
 [FileAct 配接器架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md)   
 [FileAct 配接器即時的端對端原型](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md)   
 [FileAct 配接器即時區域基本型別](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md)   
 [FileAct 配接器儲存與轉送](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md)   
 [FileAct 配接器安全性架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md)   
 [FileAct 配接器檔案和傳輸識別碼](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md)   
 [FileAct 配接器支援資訊傳輸](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md)   
 [FileAct 配接器傳遞通知](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md)