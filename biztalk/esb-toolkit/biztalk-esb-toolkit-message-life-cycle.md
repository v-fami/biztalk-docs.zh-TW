---
title: BizTalk ESB 工具組訊息生命週期 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c72fdbda-b9ef-431a-8322-56dba98e9eab
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f93a4ee2024fcb9cfaf65e7cf33922784a47030
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979135"
---
# <a name="biztalk-esb-toolkit-message-life-cycle"></a>BizTalk ESB 工具組訊息生命週期
以下是訊息的來自外部系統，並透過連線到其最終目的地 ESB 周遊生命週期：  

1. 匝道接收的訊息。 根據提交的合作對象或用戶端上，訊息可能或可能不會包含定義訊息的處理指示的路線。  

2. ESB 管線元件複製路線 （如果有 SOAP 標頭中） 到訊息的內容為升級的屬性。 路線沒有收到訊息時，可以設定特定的管線元件，以從資料庫中，根據訊息內容或內容中，選取適當的路線，，然後複製到訊息內容的 路線。 訊息的存留期期間，訊息內容中會保持路線。  

3. 雖然仍會在管線中，評估路線，並且以訊息為基礎的路線服務可以處理訊息。 這些路線服務可能會轉換該訊息，或設定路由的端點。  

4. 訊息會發佈到 Microsoft BizTalk Server Messagebox 資料庫。  

5. BizTalk Server 的一或多個 「 訂閱者 」，訊息將評估的訊息和佇列的升級的屬性。  

6. 訂閱者會處理訊息使用一般的 BizTalk Server 機制。 訂閱者可以是下列其中一項：  

   -   使用篩選條件直接繫結上設定 BizTalk Server 協調流程接收埠  

   -   動態的 BizTalk Server 傳送埠，也稱為 ESB 出口匝。 行程會判斷連接埠以繼續處理訊息的設定方式。  

   替代路線入口匝透過到達的訊息，BizTalk Server 協調流程也可以發佈訊息至 Messagebox 的 ESB 處理：  

7. BizTalk Server 協調流程內建立一則訊息。  

8. 訊息的內容會填入 ESB 路線。  

9. 訊息會發佈到 Messagebox 資料庫直接繫結連接埠。
