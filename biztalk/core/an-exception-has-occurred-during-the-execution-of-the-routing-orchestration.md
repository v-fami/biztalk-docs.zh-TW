---
title: 路由協調流程執行期間發生例外狀況 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 68ec8921-ba05-496e-8dcc-fd8994fcb8b7
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 917349fe1157bc672ad3f3897f504625c59e7ba3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007319"
---
# <a name="an-exception-has-occurred-during-the-execution-of-the-routing-orchestration"></a><span data-ttu-id="e58d8-102">路由協調流程執行期間發生例外狀況</span><span class="sxs-lookup"><span data-stu-id="e58d8-102">An exception has occurred during the execution of the routing orchestration</span></span>
## <a name="details"></a><span data-ttu-id="e58d8-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e58d8-103">Details</span></span>  
  
|                 |                                                                                                |
|-----------------|------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="e58d8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e58d8-104">Product Name</span></span>   |       [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]       |
| <span data-ttu-id="e58d8-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="e58d8-105">Product Version</span></span> |                   [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                   |
|    <span data-ttu-id="e58d8-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e58d8-106">Event ID</span></span>     |                                               -                                                |
|  <span data-ttu-id="e58d8-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="e58d8-107">Event Source</span></span>   |     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e58d8-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="e58d8-108"> EDI</span></span>     |
|    <span data-ttu-id="e58d8-109">元件</span><span class="sxs-lookup"><span data-stu-id="e58d8-109">Component</span></span>    |                                        <span data-ttu-id="e58d8-110">批次引擎</span><span class="sxs-lookup"><span data-stu-id="e58d8-110">Batching Engine</span></span>                                         |
|  <span data-ttu-id="e58d8-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e58d8-111">Symbolic Name</span></span>  |                                 <span data-ttu-id="e58d8-112">ExceptionOccuredDuringRouting</span><span class="sxs-lookup"><span data-stu-id="e58d8-112">ExceptionOccuredDuringRouting</span></span>                                  |
|  <span data-ttu-id="e58d8-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e58d8-113">Message Text</span></span>   | <span data-ttu-id="e58d8-114">路由協調流程執行期間發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e58d8-114">An exception has occured during the execution of the routing Orchestration.</span></span> <span data-ttu-id="e58d8-115">ErrorMessage = {0}</span><span class="sxs-lookup"><span data-stu-id="e58d8-115">ErrorMessage = {0}</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="e58d8-116">說明</span><span class="sxs-lookup"><span data-stu-id="e58d8-116">Explanation</span></span>  
 <span data-ttu-id="e58d8-117">這個錯誤/警告/資訊事件表示，由於發生 [錯誤訊息] 欄位指出的錯誤情況，因此路由協調流程無法正確地處理每份 XML 批次元素。</span><span class="sxs-lookup"><span data-stu-id="e58d8-117">This Error/Warning/Information event indicates that the routing orchestration could not process each copy of the XML batch element correctly because of the error condition indicated in ErrorMessage field.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e58d8-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e58d8-118">User Action</span></span>  
 <span data-ttu-id="e58d8-119">若要解決這個錯誤，請根據 [錯誤訊息] 欄位判斷發生的錯誤情況並解決錯誤，然後再重新提交訊息。</span><span class="sxs-lookup"><span data-stu-id="e58d8-119">To resolve this error, determine what the error condition is from the ErrorMessage field, resolve the error, and resubmit the message.</span></span>