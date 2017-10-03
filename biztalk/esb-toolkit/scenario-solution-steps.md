---
title: "實例解決方案步驟 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77751c15-9b67-4587-8bc8-2be65f13d339
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dff3b2feda86ad0b8edbbded26a290c7276a63af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-solution-steps"></a>實例解決方案的步驟
在 ESB 例外狀況管理架構提供簡單的解決方案來處理例外狀況，當發票訊息包含無效的資料在處理期間，會造成錯誤，如本主題稍早所述。 以下是您可能需要的其中一個方法：  
  
1.  指派最近財務報表應用程式根據您的小組的開發人員的 Microsoft BizTalk 的責任。  
  
2.  新的 ESB 錯誤訊息到達在 ESB 管理入口網站中。訊息會指出在財務報告的 BizTalk 應用程式中的協調流程中的資料完整性問題。  
  
3.  系統管理員或操作員通知開發人員的新的例外狀況，或例外狀況發生時，開發人員註冊自動通知。 下列原因，可能會發生此通知：  
  
    -   它可能會發生例外狀況已超過閾值，預先定義中以事件為基礎商務活動監控 (BAM)。  
  
    -   它可能是因為 BizTalk 訂用帳戶有特定的應用程式、 服務、 範圍及開發人員轉送給例外狀況的錯誤碼。  
  
4.  開發人員檢查錯誤訊息、 個別的協調流程訊息，以及其保存的內容屬性值。 開發人員可以檢視這項資訊透過 ESB 管理入口網站或透過 BizTalk 訂閱使用 Microsoft Outlook。  
  
5.  讓開發人員決定這是常見的錯誤。 它將需要手動介入和修正由與 ｢ 財務團隊，後面接著重新提交至系統。  
  
6.  開發人員建立並部署獨立的 BizTalk 協調流程專案，以訂閱特定的應用程式和例外狀況類型。  
  
7.  協調流程專案的 ESB 錯誤訊息會擷取無效的訊息、 傳送訊息到更正與 ｢ 財務團隊、 將修正過的訊息傳回至協調流程中，相互關聯和重新提交它。  
  
8.  一週後，開發人員可巡覽到 ESB 管理入口網站，以探索此解決方案已部署，因為無效的訊息應用程式例外狀況的趨勢已大幅減少。