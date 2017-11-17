---
title: "錯誤-空的結構描述根參考 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.edit.error.rootRefEmpty
ms.assetid: 172e6ad8-6118-40db-9451-92808a3a2051
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7217f6f9ea328aff4864cfdf3bee9ea71de3741
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---schema-root-reference-empty"></a><span data-ttu-id="7db58-102">錯誤-空的結構描述根參考</span><span class="sxs-lookup"><span data-stu-id="7db58-102">Error - Schema Root Reference Empty</span></span>
<span data-ttu-id="7db58-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="7db58-103">**Error Code**</span></span>  
  
 <span data-ttu-id="7db58-104">BEC2005</span><span class="sxs-lookup"><span data-stu-id="7db58-104">BEC2005</span></span>  
  
 <span data-ttu-id="7db58-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="7db58-105">**Explanation**</span></span>  
  
 <span data-ttu-id="7db58-106">**根參考**屬性**結構描述**節點未設定。</span><span class="sxs-lookup"><span data-stu-id="7db58-106">The **Root Reference** property of the **Schema** node is not set.</span></span> <span data-ttu-id="7db58-107">當**標準**屬性**結構描述**以外節點設定為值**XML**，您必須設定**根參考**屬性指出哪個子節點**結構描述**要當做此結構描述定義訊息的根節點。</span><span class="sxs-lookup"><span data-stu-id="7db58-107">When the **Standard** property of the **Schema** node is set to a value other than **XML**, you must set the **Root Reference** property to indicate which child node of the **Schema** node is meant to be used as the root of the message defined by this schema.</span></span>  
  
 <span data-ttu-id="7db58-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="7db58-108">**User Action**</span></span>  
  
 <span data-ttu-id="7db58-109">根據您的結構描述，請將**標準**屬性**結構描述**節點**XML**，或設定**根參考**屬性**結構描述**適當的子節點的節點**結構描述**節點。</span><span class="sxs-lookup"><span data-stu-id="7db58-109">As appropriate for your schema, either set the **Standard** property of the **Schema** node to **XML**, or set the **Root Reference** property of the **Schema** node to the appropriate child node of the **Schema** node.</span></span> <span data-ttu-id="7db58-110">這些子節點位於**根參考**屬性下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="7db58-110">These child nodes are the available in the **Root Reference** property drop-down list.</span></span>