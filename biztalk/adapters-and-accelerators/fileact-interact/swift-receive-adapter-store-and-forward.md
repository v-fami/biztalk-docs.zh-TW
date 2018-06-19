---
title: SWIFT 接收配接器儲存與轉送 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 11eeb335-366b-4b29-9078-de9396b258ca
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 315b9bbe6985bbce5ccb44d8d4846b18730f292b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224470"
---
# <a name="swift-receive-adapter-store-and-forward"></a>SWIFT 接收配接器儲存與轉送
接收配接器會接收來自 SWIFT 商店 和 正向 (SnF) 佇列的訊息。 若要從佇列接收訊息，配接器必須開啟工作階段與 SnF 佇列。 若要開啟佇列，它必須有專用的用戶端處理序所建立的佇列的工作階段。 在設計中，此程序會實作為 COM plus 跨處理序元件。  
  
## <a name="push-session-store-and-forward-sequence"></a>工作階段存放區和正向順序推入  
 下列清單說明 商店 和 正向順序。  
  
1.  啟動伺服器應用程式所處理的訊息。  
  
2.  伺服器處理序，開啟第一個與 Sw:HandleInitRequest SwCallback 期間為基本輸入所需的安全性內容。  
  
3.  伺服器會回應與任一個或兩個 Sw:CryptoMode Sw:FACryptoMode 設為進階 Sw:HandleInitRequest。  
  
     伺服器現在已準備好開始處理傳入要求。  
  
4.  若要從佇列啟動的訊息傳遞，用戶端處理序啟動推入工作階段。 根據配接器組態 （push 模式），則接收配接器會繁衍稱為 SnFQueueManager.exe 取得 push 模式中的佇列的用戶端處理序。  
  
5.  SwCall() 執行 Sw:AcquireSnFRequest （內 Sw:ExchangeSnFRequest) 做為輸入的基本類型。 此要求指定的佇列會啟動工作階段 （如果 SwSec:AuthorisationContext 具有所需的 RBAC 角色）。  
  
6.  緊接在 Sw:AcquireStatus 回應與 「 已接受 」，SWIFTNet SnF 會開始將訊息傳送至伺服器中取得所指定。 如果尚未啟動接收配接器，訊息就會發生例外狀況。 （這是為什麼一定要有在接收配接器已啟動。）  
  
7.  SWIFTNet SnF 啟動推入數目 （最上層視窗大小） 的訊息。  
  
8.  針對每個認可的訊息，推入新的訊息 （如果有的話）。  
  
9. 用戶端處理序 (SnFQueueManager.exe) 已完成其工作，並可立即終止。 處理程序發出 SwSec:DestroyContextRequest，清除 開啟 安全性內容。 Sw:TermRequest 後會結束處理程序。  
  
### <a name="message-correlation"></a>訊息相互關聯  
 RequestRef 欄位會保留並替換回應訊息中，接收配接器。 這可確保內送訊息和回應訊息之間的端對端相互關聯  
  
### <a name="duplicate-processing"></a>重複處理  
 如果接收 FileAct 要求，以及配接器執行個體接收訊息可能重複的指示器節點之後，它必須檢查以查看是否已成功完成的參考的傳送，或已失敗，並採取適當的動作。 如果檔案傳輸已開始然後配接器傳輸會將狀態更新為 「 Duplicate 」 否則便會更新它做為 「 已接受 」。  
  
### <a name="acknowledgments"></a>致謝  
 如果傳送者要求 FileAct 要求通知，配接器會檢查有檔案傳送完成事件，並產生收條之後正在驗證檔案的摘要值。 配接器至 BizTalk 傳送配接器拾取它，並將其傳送給傳送者傳送通知訊息。  
  
## <a name="see-also"></a>另請參閱  
 [SWIFT 接收配接器架構](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md)   
 [SWIFT 接收配接器 URI](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-uri.md)   
 [SWIFT 接收配接器初始化](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-initialization.md)   
 [SWIFT 接收配接器的安全性內容](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-security-context.md)   
 [SWIFT 接收配接器同步與延遲模式](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-synchronous-and-deferred-modes.md)