---
title: "交易式協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, compensations
- orchestrations, transactional
- Transaction Type property
ms.assetid: c4f0b6ca-d939-4d3a-b7ef-53c6aafdea9c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8c6fb466e0c3cc5cae4a076237d1dbc970b5794
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="transacted-orchestrations"></a><span data-ttu-id="55787-102">交易的協調流程</span><span class="sxs-lookup"><span data-stu-id="55787-102">Transacted Orchestrations</span></span>
<span data-ttu-id="55787-103">協調流程可以是交易式流程，就像範圍一樣。</span><span class="sxs-lookup"><span data-stu-id="55787-103">Orchestrations can be transactional, just like scopes.</span></span> <span data-ttu-id="55787-104">事實上，協調流程本身也可以視為範圍。</span><span class="sxs-lookup"><span data-stu-id="55787-104">In fact, an orchestration can itself be considered a scope.</span></span> <span data-ttu-id="55787-105">適用於交易協調流程的相同規則通常也適用於交易範圍。</span><span class="sxs-lookup"><span data-stu-id="55787-105">In general, the same rules apply for transacted orchestrations as for transacted scopes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55787-106">協調流程和其他範圍之間的差異，在於協調流程沒有例外處理常式。</span><span class="sxs-lookup"><span data-stu-id="55787-106">One difference between orchestrations and other scopes is that orchestrations do not have exception handlers.</span></span>  
  
## <a name="orchestration-compensation"></a><span data-ttu-id="55787-107">協調流程補償</span><span class="sxs-lookup"><span data-stu-id="55787-107">Orchestration compensation</span></span>  
 <span data-ttu-id="55787-108">如果**交易類型**協調流程屬性設定為長時間執行或不可部分完成，您也可以選取的值**補償**屬性，可以是預設或自訂。</span><span class="sxs-lookup"><span data-stu-id="55787-108">If the **Transaction Type** property for your orchestration is set to long-running or atomic, you can also select a value for the **Compensation** property, which can be Default or Custom.</span></span>  
  
 <span data-ttu-id="55787-109">如果您選取**自訂**補償，**補償** 索引標籤會出現在協調流程設計介面旁邊。</span><span class="sxs-lookup"><span data-stu-id="55787-109">If you select **Custom** for the compensation, a **Compensation** tab will appear alongside the Orchestration Design Surface.</span></span> <span data-ttu-id="55787-110">此索引標籤的外觀與協調流程設計介面相同，而且您也可以使用相同的方式在上面新增圖形和連接埠。</span><span class="sxs-lookup"><span data-stu-id="55787-110">It will look the same as the Orchestration Design Surface, and you can add shapes and ports to it in the same way.</span></span>  
  
 <span data-ttu-id="55787-111">補償只會發生在其他協調流程所呼叫的協調流程上。</span><span class="sxs-lookup"><span data-stu-id="55787-111">Compensations only take place on orchestrations that are called by other orchestrations.</span></span> <span data-ttu-id="55787-112">您可以使用補償特定的協調流程執行個體**識別碼**屬性**呼叫協調流程**圖形。</span><span class="sxs-lookup"><span data-stu-id="55787-112">You can compensate a specific orchestration instance by using the **Identifier** property on the **Call Orchestration** shape.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="55787-113">如果補償存在最上層的協調流程，執行階段引擎將會忽略它。</span><span class="sxs-lookup"><span data-stu-id="55787-113">If a compensation exists on a top-level orchestration, it will be ignored by the runtime engine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55787-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55787-114">See Also</span></span>  
 <span data-ttu-id="55787-115">[建立交易式協調流程](../core/making-orchestrations-transactional.md) </span><span class="sxs-lookup"><span data-stu-id="55787-115">[Making Orchestrations Transactional](../core/making-orchestrations-transactional.md) </span></span>  
 [<span data-ttu-id="55787-116">使用交易和例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="55787-116">Using Transactions and Handling Exceptions</span></span>](../core/using-transactions-and-handling-exceptions.md)