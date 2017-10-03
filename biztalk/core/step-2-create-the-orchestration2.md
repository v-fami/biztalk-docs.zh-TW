---
title: "步驟 2： 建立 Orchestration2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08d65525-77a9-4be2-a509-40ea60fa7401
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13973edb14fbaed331a33eff429d623a33c3ff71
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-create-the-orchestration"></a>步驟 2： 建立協調流程
協調流程設定使用名為 BeginDocTest 的專案，包括下列項目：  
  
 • 連接埠  
  
 • 訊息  
  
 • 傳送與接收  
  
 • 建構訊息  
  
 • 轉換  
  
 協調流程並不會進行任何例外狀況處理。 J.D. Edwards EnterpriseOne 執行的 BeginDoc 和隱含交易則會復原，如果連接逾時內的後續作業。因而，BizTalk 協調流程不需要對 J.D. Edwards OneWorld 造成的變更進行任何回復 Edwards EnterpriseOne 可讓。 然而，逾時會在 BizTalk 協調流程中導致例外狀況。 BizTalk 會將例外狀況記錄在事件日誌中。 如果您要在協調流程中加入例外狀況處理，請參閱 Microsoft BizTalk 2006 主要說明內容中的＜如何新增 Catch 例外狀況區塊＞和＜如何新增補償區塊＞。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [工作 1： 建立連接埠](../core/task-1-create-the-ports1.md)  
  
-   [工作 2： 建立訊息](../core/task-2-create-the-messages2.md)  
  
-   [工作 3： 設定傳送埠和接收圖形](../core/task-3-configure-the-send-and-receive-shapes2.md)  
  
-   [工作 4： 設定建構訊息圖形](../core/task-4-configure-the-construct-message-shape1.md)  
  
-   [工作 5： 設定轉換圖形](../core/task-5-configure-the-transform-shape2.md)