---
title: 在執行升級批次協調流程期間發生例外狀況 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2221a498-98aa-43ab-bc4e-34dcbd92dcf0
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a12c1a116a0f7d35f6fbc7d2250c48f224081fae
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981343"
---
# <a name="an-exception-has-occurred-during-the-execution-of-the-upgrade-batch-orchestration"></a><span data-ttu-id="7d2d0-102">在執行升級批次協調流程期間發生例外狀況</span><span class="sxs-lookup"><span data-stu-id="7d2d0-102">An exception has occurred during the execution of the upgrade batch orchestration</span></span>
## <a name="details"></a><span data-ttu-id="7d2d0-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7d2d0-103">Details</span></span>  
  
|                 |                                                                                                       |
|-----------------|-------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="7d2d0-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7d2d0-104">Product Name</span></span>   |          [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]           |
| <span data-ttu-id="7d2d0-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="7d2d0-105">Product Version</span></span> |                      [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                       |
|    <span data-ttu-id="7d2d0-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7d2d0-106">Event ID</span></span>     |                                                   -                                                   |
|  <span data-ttu-id="7d2d0-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="7d2d0-107">Event Source</span></span>   |                                          <span data-ttu-id="7d2d0-108">BizTalk Server EDI</span><span class="sxs-lookup"><span data-stu-id="7d2d0-108">BizTalk Server EDI</span></span>                                           |
|    <span data-ttu-id="7d2d0-109">元件</span><span class="sxs-lookup"><span data-stu-id="7d2d0-109">Component</span></span>    |                                            <span data-ttu-id="7d2d0-110">批次引擎</span><span class="sxs-lookup"><span data-stu-id="7d2d0-110">Batching Engine</span></span>                                            |
|  <span data-ttu-id="7d2d0-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7d2d0-111">Symbolic Name</span></span>  |                                     <span data-ttu-id="7d2d0-112">ExceptionOccuredDuringUpgrade</span><span class="sxs-lookup"><span data-stu-id="7d2d0-112">ExceptionOccuredDuringUpgrade</span></span>                                     |
|  <span data-ttu-id="7d2d0-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7d2d0-113">Message Text</span></span>   | <span data-ttu-id="7d2d0-114">在升級批次協調流程執行期間發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7d2d0-114">An exception has occurred during the execution of the upgrade batch Orchestration.</span></span> <span data-ttu-id="7d2d0-115">ErrorMessage = {0}</span><span class="sxs-lookup"><span data-stu-id="7d2d0-115">ErrorMessage = {0}</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="7d2d0-116">說明</span><span class="sxs-lookup"><span data-stu-id="7d2d0-116">Explanation</span></span>  
 <span data-ttu-id="7d2d0-117">錯誤/警告/資訊事件表示，升級批次協調流程可能無法正確進行處理訊息因為訊息 欄位中指定的錯誤情況。</span><span class="sxs-lookup"><span data-stu-id="7d2d0-117">The Error/Warning/Information event indicates that the upgrade batch orchestration could not process the message correctly because of the error condition indicated in ErrorMessage field.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7d2d0-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7d2d0-118">User Action</span></span>  
 <span data-ttu-id="7d2d0-119">若要解決這個錯誤，判斷錯誤狀況是從 [訊息] 欄位、 解決錯誤，然後重新提交訊息。</span><span class="sxs-lookup"><span data-stu-id="7d2d0-119">To resolve this error, determine what the error condition is from the ErrorMessage field, resolve the error, and then resubmit the message.</span></span>