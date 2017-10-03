---
title: "商務程序管理解決方案中的處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, processing
- processing, process management solutions
ms.assetid: 0b26447e-d8f1-4084-aa34-6e7f8ffccea5
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 145dd8e616048f1caaa1a59ec41d099e93e47880
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="processing-in-the-business-process-management-solution"></a>商務程序管理解決方案中的處理
本節描述商務程序管理解決方案的運作方式： 如何處理訂單，它會使用插斷，以及如何處理例外狀況，該動作的方式可重試。  
  
 訂單處理依賴兩個主要的協調流程， **OrderBroker**和**OrderManager**。 **OrderBroker**協調流程的撰寫方式可以有多個訂單管理員協調流程，其中的每一種順序。 解決方案僅包括一個**OrderManager**。 它的撰寫方式也是相當一般的，使其可適用於其他類型的訂單。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [OrderBroker 協調流程中處理](../core/processing-in-the-orderbroker-orchestration.md)  
  
-   [程序管理員邏輯](../core/process-manager-logic.md)  
  
-   [訂單處理階段中的處理](../core/processing-in-the-order-processing-stages.md)  
  
-   [中斷商務程序管理解決方案中的處理](../core/interrupt-handling-in-the-business-process-management-solution.md)  
  
-   [在商務程序管理解決方案中處理的例外狀況](../core/exception-handling-in-the-business-process-management-solution.md)