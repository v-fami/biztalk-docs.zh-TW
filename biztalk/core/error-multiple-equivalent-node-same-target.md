---
title: "錯誤-多個相等節點相同目標 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.multipleEquivNodeSameTarget
ms.assetid: d8ca9f94-1d87-41bb-9479-6a01a5b6702d
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12df4f7a68bb1eceaa3211c6aad6e9a581f17a4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---multiple-equivalent-node-same-target"></a><span data-ttu-id="edfe8-102">錯誤-多個相等節點相同目標</span><span class="sxs-lookup"><span data-stu-id="edfe8-102">Error - Multiple Equivalent Node Same Target</span></span>
<span data-ttu-id="edfe8-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="edfe8-103">**Error Code**</span></span>  
  
 <span data-ttu-id="edfe8-104">btm1025</span><span class="sxs-lookup"><span data-stu-id="edfe8-104">btm1025</span></span>  
  
 <span data-ttu-id="edfe8-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="edfe8-105">**Explanation**</span></span>  
  
 <span data-ttu-id="edfe8-106">指定來源結構描述中節點的子節點衝突的**相等**群組節點，您可以同時連結至目的結構描述中指定的節點。</span><span class="sxs-lookup"><span data-stu-id="edfe8-106">The indicated nodes in the source schema, which are conflicting child nodes of an **Equivalent** group node, are both linked to the indicated node in the destination schema.</span></span> <span data-ttu-id="edfe8-107">在指定的執行個體訊息中，只能有其中一種來源結構描述中的節點存在。</span><span class="sxs-lookup"><span data-stu-id="edfe8-107">Only one of these nodes in the source schema can occur in a given instance message.</span></span>  
  
 <span data-ttu-id="edfe8-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="edfe8-108">**User Action**</span></span>  
  
 <span data-ttu-id="edfe8-109">請確定只有一個子系的節點**相等**群組節點都會連接到目的結構描述中指定的節點。</span><span class="sxs-lookup"><span data-stu-id="edfe8-109">Ensure that only one of the child nodes of the **Equivalent** group node is connected to a given node in the destination schema.</span></span>