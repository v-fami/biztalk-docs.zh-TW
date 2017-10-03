---
title: "在升級的批次協調流程的執行期間發生例外狀況 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2221a498-98aa-43ab-bc4e-34dcbd92dcf0
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54cd439e180365010ec8881ce7165022dd7826d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="an-exception-has-occurred-during-the-execution-of-the-upgrade-batch-orchestration"></a><span data-ttu-id="4087f-102">在升級的批次協調流程的執行期間發生例外狀況</span><span class="sxs-lookup"><span data-stu-id="4087f-102">An exception has occurred during the execution of the upgrade batch orchestration</span></span>
## <a name="details"></a><span data-ttu-id="4087f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4087f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4087f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="4087f-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="4087f-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="4087f-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="4087f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="4087f-106">Event ID</span></span>|-|  
|<span data-ttu-id="4087f-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="4087f-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]<span data-ttu-id="4087f-108">EDI</span><span class="sxs-lookup"><span data-stu-id="4087f-108"> EDI</span></span>|  
|<span data-ttu-id="4087f-109">元件</span><span class="sxs-lookup"><span data-stu-id="4087f-109">Component</span></span>|<span data-ttu-id="4087f-110">批次處理引擎</span><span class="sxs-lookup"><span data-stu-id="4087f-110">Batching Engine</span></span>|  
|<span data-ttu-id="4087f-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="4087f-111">Symbolic Name</span></span>|<span data-ttu-id="4087f-112">ExceptionOccuredDuringUpgrade</span><span class="sxs-lookup"><span data-stu-id="4087f-112">ExceptionOccuredDuringUpgrade</span></span>|  
|<span data-ttu-id="4087f-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="4087f-113">Message Text</span></span>|<span data-ttu-id="4087f-114">升級的批次協調流程執行期間發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4087f-114">An exception has occurred during the execution of the upgrade batch Orchestration.</span></span> <span data-ttu-id="4087f-115">ErrorMessage = {0}</span><span class="sxs-lookup"><span data-stu-id="4087f-115">ErrorMessage = {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4087f-116">說明</span><span class="sxs-lookup"><span data-stu-id="4087f-116">Explanation</span></span>  
 <span data-ttu-id="4087f-117">錯誤/警告/資訊事件表示升級批次協調流程無法處理訊息正確因為 ErrorMessage 欄位中指定的錯誤情況。</span><span class="sxs-lookup"><span data-stu-id="4087f-117">The Error/Warning/Information event indicates that the upgrade batch orchestration could not process the message correctly because of the error condition indicated in ErrorMessage field.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4087f-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="4087f-118">User Action</span></span>  
 <span data-ttu-id="4087f-119">若要解決這個錯誤，判斷錯誤狀況是從 ErrorMessage 欄位，解決錯誤，然後再重新提交訊息。</span><span class="sxs-lookup"><span data-stu-id="4087f-119">To resolve this error, determine what the error condition is from the ErrorMessage field, resolve the error, and then resubmit the message.</span></span>