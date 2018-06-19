---
title: 步驟 2： 建立 Orchestration1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a88cafbb-3b6f-4d27-8516-79a2391b4e31
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1989fe18d9c9c81741ac83bd2f96627ea818eb91
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276486"
---
# <a name="step-2-create-the-orchestration"></a>步驟 2： 建立協調流程
協調流程設定使用名為 BeginDocTest 的專案，包括下列項目：  
  
-   連接埠  
  
-   訊息  
  
-   傳送與接收  
  
-   建構訊息  
  
-   轉換  
  
 協調流程並不會進行任何例外狀況處理。 J.D. Edwards OneWorld 執行的 BeginDoc 和隱含交易內的後續作業會在連線逾時發生時進行回復。因而，BizTalk 協調流程不需要對 J.D. Edwards OneWorld 造成的變更進行任何回復 。 然而，逾時會在 BizTalk 協調流程中導致例外狀況。 BizTalk 會將例外狀況記錄在事件日誌中。 如果您想要加入例外狀況處理協調流程，請參閱 < 如何新增 Catch 例外狀況區塊 」 和 「 如何新增補償區塊 」 在 Microsoft BizTalk Server 說明中。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [工作 1： 建立連接埠](../core/task-1-create-the-ports2.md)  
  
-   [工作 2： 建立訊息](../core/task-2-create-the-messages1.md)  
  
-   [工作 3： 設定傳送埠和接收圖形](../core/task-3-configure-the-send-and-receive-shapes1.md)  
  
-   [工作 4： 設定建構訊息圖形](../core/task-4-configure-the-construct-message-shape2.md)  
  
-   [工作 5： 設定轉換圖形](../core/task-5-configure-the-transform-shape1.md)