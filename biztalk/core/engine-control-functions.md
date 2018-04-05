---
title: 引擎控制函式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Business Rules Engine, functions
ms.assetid: a7900e59-c52c-4a6d-9ca3-ee4ec659f9b5
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 033a4213a6552319f44a98e23562d7e8703fdd42
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="engine-control-functions"></a><span data-ttu-id="e3b24-102">引擎控制函式</span><span class="sxs-lookup"><span data-stu-id="e3b24-102">Engine Control Functions</span></span>
<span data-ttu-id="e3b24-103">本節會說明與數個商務規則引擎控制函式相關的行為，這些函式可允許應用程式或原則來控制規則引擎工作記憶體中的事實。</span><span class="sxs-lookup"><span data-stu-id="e3b24-103">This section explains the behaviors associated with several Business Rule engine control functions that allow an application or policy to control the facts in the rule engine's working memory.</span></span> <span data-ttu-id="e3b24-104">工作記憶體中出現的事實會驅動要評估的條件及要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="e3b24-104">The presence of facts in the working memory drives the conditions that are evaluated and the actions that are executed.</span></span>  
  
 <span data-ttu-id="e3b24-105">本節將探討**Assert**， **Retract**， **RetractByType**，**重新判斷提示**，和**更新**函式不同的事實：.NET 物件、 **TypedXmlDocument**， **DataConnection**，和**TypedDataTable**。</span><span class="sxs-lookup"><span data-stu-id="e3b24-105">This section examines the **Assert**, **Retract**, **RetractByType**, **Reassert**, and **Update** functions for different facts: .NET objects, **TypedXmlDocument**, **DataConnection**, and **TypedDataTable**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e3b24-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="e3b24-106">In This Section</span></span>  
  
-   [<span data-ttu-id="e3b24-107">判斷提示</span><span class="sxs-lookup"><span data-stu-id="e3b24-107">Assert</span></span>](../core/assert.md)  
  
-   [<span data-ttu-id="e3b24-108">撤銷</span><span class="sxs-lookup"><span data-stu-id="e3b24-108">Retract</span></span>](../core/retract.md)  
  
-   [<span data-ttu-id="e3b24-109">RetractByType</span><span class="sxs-lookup"><span data-stu-id="e3b24-109">RetractByType</span></span>](../core/retractbytype.md)  
  
-   [<span data-ttu-id="e3b24-110">重新判斷提示</span><span class="sxs-lookup"><span data-stu-id="e3b24-110">Reassert</span></span>](../core/reassert.md)  
  
-   [<span data-ttu-id="e3b24-111">Update</span><span class="sxs-lookup"><span data-stu-id="e3b24-111">Update</span></span>](../core/update1.md)  
  
-   [<span data-ttu-id="e3b24-112">暫止</span><span class="sxs-lookup"><span data-stu-id="e3b24-112">Halt</span></span>](../core/halt.md)