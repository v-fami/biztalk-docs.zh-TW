---
title: "FileAct 配接器儲存與轉送 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50110bf0-75c2-426c-9833-65c3117224b2
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1201a5ab5cb45ceba2622aa1c269404acec910df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="fileact-adapter-store-and-forward"></a>FileAct 配接器儲存與轉送
存放區中，順向 (SnF) 模式的檔案傳遞給佇列在傳送時，並從目的地佇列中擷取。 中繼會傳回回應的 SWIFTNet 寄件者之前檔案安全地傳遞到目的地。  
  
## <a name="sending-using-snf"></a>使用 [SnF 傳送  
 如果您建立的單向傳送埠時，配接器 SnF 模式運作，並將訊息傳送至佇列。  
  
## <a name="receiving-using-snf"></a>接收使用 SnF  
 SnF FileAct 推送模式中的運作方式。 這是執行階段選項。  
  
 才能從佇列擷取訊息，SWIFTNet SnF 應該會收到取得佇列的要求。 這會透過叫用跨處理序 COM + 元件接收配接器。 成功取得之後, 會建立一個工作階段。 然後會在要求中指定的模式中開啟佇列。 所有訊息會都回到發出要求的實體節點。  
  
 訊息傳遞指定的順序 （請注意互動和 FileAct 傳輸可以顛倒，並依照優先順序排列。）不過，在排序的訊息，是取決於它們所儲存的時間。 FileAct，如果這是檔案存放裝置已完成，不會在它啟動的時間。  
  
### <a name="push-a-file-from-the-queue"></a>從佇列推送檔案  
 FileAct 配接器 （伺服器） 接收 HandleFileRequest 從 SWIFTNet，包含佇列、 工作階段和順序的資訊。 伺服器會回應 HandleFileResponse。  
  
 伺服器接著會發出 FetchFileRequest 和檔案傳遞至伺服器。  
  
## <a name="see-also"></a>另請參閱  
 [FileAct 配接器架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md)   
 [FileAct 配接器即時的端對端原型](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md)   
 [FileAct 配接器即時區域基本型別](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md)   
 [FileAct 配接器安全性架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md)   
 [FileAct 配接器檔案和傳輸識別碼](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md)   
 [FileAct 配接器支援資訊傳輸](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md)   
 [FileAct 配接器傳遞通知](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md)   
 [FileAct 配接器狀態監視](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)