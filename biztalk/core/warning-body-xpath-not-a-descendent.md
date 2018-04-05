---
title: 警告-Body XPath 不是子系 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.bodyXPathNotDescendant
ms.assetid: bfeff370-9b84-4fd9-81e9-1e54b166f561
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70b5d228e1119bc7c569b45cc6795f3f5b8454ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="warning---body-xpath-not-a-descendent"></a><span data-ttu-id="15ded-102">警告-Body XPath 不是子系</span><span class="sxs-lookup"><span data-stu-id="15ded-102">Warning - Body XPath Not A Descendent</span></span>
<span data-ttu-id="15ded-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="15ded-103">**Error Code**</span></span>  
  
 <span data-ttu-id="15ded-104">BEC1004</span><span class="sxs-lookup"><span data-stu-id="15ded-104">BEC1004</span></span>  
  
 <span data-ttu-id="15ded-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="15ded-105">**Explanation**</span></span>  
  
 <span data-ttu-id="15ded-106">**Body XPath**此信封結構描述中指定的根節點的屬性參考不是該根節點，所需的子系的節點。</span><span class="sxs-lookup"><span data-stu-id="15ded-106">The **Body XPath** property of the indicated root node in this envelope schema references a node that is not a descendent of that root node, as required.</span></span> <span data-ttu-id="15ded-107">應該不會發生此錯誤除非**Body XPath**修改在 [BizTalk 編輯器] 以外的屬性。</span><span class="sxs-lookup"><span data-stu-id="15ded-107">This error should not occur unless the **Body XPath** property is modified outside of BizTalk Editor.</span></span>  
  
 <span data-ttu-id="15ded-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="15ded-108">**User Action**</span></span>  
  
 <span data-ttu-id="15ded-109">選取指定的根節點，然後選取的值**Body XPath**正確識別關聯的訊息內文的最上層節點的屬性。</span><span class="sxs-lookup"><span data-stu-id="15ded-109">Select the indicated root node and select the value for the **Body XPath** property that correctly identifies the top-level node of the associated message body.</span></span>