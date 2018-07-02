---
title: 訊息失敗的類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transformation stage
- assembly stage
- errors, disassembly stage
- errors, assembly stage
- routing, errors
- errors, transformation stage
- errors, messages [HAT]
- errors, routing
- disassembly stage, errors
- messages, errors [HAT]
ms.assetid: 3a8e1c58-4b53-4439-837d-aaa233eb9158
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8a3dc40d2b82e90332b27719adce36b27f78ebd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984007"
---
# <a name="types-of-message-failures"></a>訊息失敗的類型
本主題列出訊息失敗可能發生的不同點。  
  
 **反組譯碼階段中的失敗**  
  
 處理作業也可能在解譯階段失敗；也就是說，在其中一個管線元件中失敗。 例如，由於處理伺服器上缺少解密憑證而造成解密失敗，或由於結構描述或訊息中的問題而造成剖析失敗。  
  
 **路由中的失敗**  
  
 在訊息成功解譯之後，下一個潛在的失敗點是路由；例如，使用者啟用協調流程的對應接收位置，但忘記登錄協調流程。 在此情況下，從接收位置拾取的訊息將路由失敗，而 MessageBox 資料庫會產生「路由失敗」報告。  
  
 「路由失敗」報告會列在 [BizTalk Server 管理] 主控台中做為不可繼續的已擱置訊息。 每個「路由失敗」報告都包含發生路由失敗時取得的訊息屬性快照。 您可以使用每個報告中的資訊來判斷其關聯訊息為何路由失敗。 若關聯訊息可繼續，則您可以更正路由問題並繼續此訊息，以便處理作業繼續。 「路由失敗」報告會列在具有空白服務名稱與服務類型的結果清單中。 終止已擱置的執行個體時，預設為每分鐘執行的 Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb 工作會自動刪除與已擱置執行個體關聯的「路由失敗」報告。 如需 Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb 工作的詳細資訊，請參閱[資料庫結構與工作](../core/database-structure-and-jobs.md)。  
  
 **在轉換階段期間發生的失敗**  
  
- **接收的訊息**。 從接收位置收到訊息時，可解譯訊息 (例如解密和剖析)，選擇性地透過接收埠指定的「輸入對應」將此訊息轉換為不同格式，並發佈至 MessageBox 以路由至協調流程或傳送埠。 在此情況下，處理作業可能由於不正確的「輸入對應」，或由於結構描述或已接收訊息中的問題，而在轉換階段造成失敗。  
  
- **將訊息傳送**。 要傳送訊息至傳送位置時，在傳送埠上設定的「輸出對應」可能選擇性地轉換訊息。 然後組合已轉換的訊息並傳遞給配接器，進行最後傳輸至傳送位置。 在此情況下，處理作業可能由於不正確的「輸出對應」，或由於結構描述或來源訊息中的問題，而在轉換階段造成失敗。  
  
  **在訊息組合階段失敗**  
  
  處理作業也可能在訊息組合階段失敗；換句話說，在管線元件中發生失敗。 在訊息成功組合之後，下一個潛在的失敗點變成傳輸至傳送位置；例如，傳送位置 (屬於夥伴) 可能關閉或不存在。  
  
## <a name="see-also"></a>另請參閱  
 [調查協調流程、連接埠和訊息失敗](../core/investigating-orchestration-port-and-message-failures.md)