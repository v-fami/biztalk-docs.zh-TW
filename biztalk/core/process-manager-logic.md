---
title: "程序管理員邏輯 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, processing
- processing, processing logic
ms.assetid: 6b69fc71-0f01-4513-9361-d7787d0cde6d
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e562362fec8e13589f1860e74024ffe70dad1c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="process-manager-logic"></a>程序管理員邏輯
本章節描述如何處理序管理員， **OrderManager**協調流程、 處理訂單。 它描述不同訂單訊息中的索引鍵欄位，並在整個協調流程中追蹤新訂單和更新的訂單。  
  
 **OrderManager**協調流程會協調附屬協調流程以處理訂單。 您可以新增、 刪除或修改這些階段，而不必變更**OrderManager**。 **OrderManager**執行大部分的協調，透過.NET 類別定義的自訂訊息。 如需解決方案中的所有訊息的清單，請參閱[商務程序管理解決方案的訊息參考](../core/message-reference-for-the-business-process-management-solution.md)。 定義訊息類型與.NET 類別的相關資訊，請參閱[使用者程式碼中的 建構訊息](../core/constructing-messages-in-user-code.md)。  
  
> [!NOTE]
>  由於大小和範圍**OrderManager**，您可能想要閱讀這些章節，特別是第二個，與 Microsoft Visual Studio 中開啟協調流程。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [關鍵訊息和欄位](../core/key-messages-and-fields.md)  
  
-   [透過處理序管理員的訂單流程](../core/order-flow-through-the-process-manager.md)