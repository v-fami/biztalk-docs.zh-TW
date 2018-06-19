---
title: BizTalk ESB Toolkit 訊息生命週期 |Microsoft 文件
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
ms.openlocfilehash: 2cb15a4c87a497a5595327b65019ca95b3201664
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22290350"
---
# <a name="biztalk-esb-toolkit-message-life-cycle"></a>BizTalk ESB Toolkit 訊息生命週期
以下是訊息的來自外部系統，並透過連線到其最終目的地 ESB 周遊週期：  
  
1.  上手接收的訊息。 根據正在提交的合作對象或用戶端，訊息可能或可能不包含會定義訊息的處理指示的路線。  
  
2.  ESB 管線元件複製路線 （如果有 SOAP 標頭中） 的訊息內容做為升級屬性。 如果路線沒有收到訊息時，可以設定特定的管線元件以從資料庫中，根據訊息內容或內容中，選取適當的路線，然後複製到訊息內容的 路線。 訊息的存留期間，會維護訊息內容中的路線。  
  
3.  雖然仍在管線中，會評估路線，且訊息為基礎的路線服務可以處理訊息。 這些路線服務可能會將訊息轉換，或設定路由的端點。  
  
4.  訊息會發佈到 Microsoft BizTalk Server Messagebox 資料庫。  
  
5.  BizTalk Server 評估一個或多個 「 訂閱者 」 的升級的屬性的訊息和佇列訊息。  
  
6.  訂閱者會處理訊息使用一般的 BizTalk Server 機制。 「 訂閱者 」 可以是下列其中一項：  
  
    -   使用直接繫結上設定篩選的 BizTalk Server 協調流程接收埠  
  
    -   動態的 BizTalk Server 傳送埠，也稱為 ESB 匝道。 路線判斷連接埠設定來繼續處理訊息的方式。  
  
 或者透過路線上手抵達的訊息，BizTalk Server 協調流程也發佈訊息至訊息槽 ESB 處理：  
  
1.  BizTalk Server 協調流程內建立一則訊息。  
  
2.  訊息的內容填入 ESB 行程。  
  
3.  訊息會發佈到 Messagebox 資料庫的直接繫結連接埠。