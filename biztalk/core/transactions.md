---
title: "交易 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, transactions
- Orchestration Designer, BizTalk Server Orchestration Engine
- BizTalk Server Orchestration Engine
- Orchestration Designer, transactions
ms.assetid: d9a748c7-be9f-4965-a30f-6b05bd6b42a3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74827beade56e6e54414371c9796454d3b48609e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="transactions"></a>交易
BizTalk Server 協調流程引擎管理會管理狀態、套用商務規則，並叫用複雜處理序和 (或) 交易集合的支援應用程式。  
  
 商務程序可以使用不可部分完成的交易而編輯為不連續的工作，此類交易會在發生錯誤或執行時間過長時自動回復所有的變更，其中可能包含巢狀交易，且會使用自訂的例外狀況處理來復原錯誤案例。 通常會透過協調流程設計師中的範圍建構來管理這些交易語意。  
  
 長時間執行的處理序，其執行時間可能會長達數天、數週或更長。 長時間執行的處理序通常會利用關聯，將接收到的訊息與可能會傳送的訊息相互關聯。 協調流程引擎管理通常會將這些執行個體凍結，以保留系統資源，然後在接到這些相關訊息時再將處理序解除凍結。 協調流程引擎會在已知的檢查點將協調流程狀態保存到 MessageBox 資料庫，以從任何應用程式或系統例外狀況進行復原。  
  
 為 BizTalk 協調流程引擎提供的交易程式設計模型包括下列項目的支援：例外狀況的處理以及從失敗交易復原、會在錯誤發生時自動回復其動作的不可部分完成的交易，或可能包含其他交易以及自訂例外狀況處理的長時間執行的交易。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [不可部分完成交易](../core/atomic-transactions.md)  
  
-   [使用不可部分完成交易的案例](../core/scenarios-using-atomic-transactions.md)  
  
-   [長時間執行的交易](../core/long-running-transactions.md)  
  
-   [使用長時間執行交易的案例](../core/scenarios-using-long-running-transactions.md)  
  
-   [在協調流程中的持續性](../core/persistence-in-orchestrations.md)