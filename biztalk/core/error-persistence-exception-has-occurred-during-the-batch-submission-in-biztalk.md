---
title: "批次處理協調流程中的批次提交期間發生持續性例外狀況 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf6e832f-9d01-46e7-aaf5-2b402d509fac
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7eae4f48209dc4f5afefbc69c40706a31f2b00b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="a-persistence-exception-has-occurred-during-the-batch-submission-in-the-batching-orchestration"></a><span data-ttu-id="6e9ed-102">批次處理協調流程中的批次提交期間發生持續性例外狀況</span><span class="sxs-lookup"><span data-stu-id="6e9ed-102">A persistence exception has occurred during the batch submission in the batching Orchestration</span></span>
## <a name="details"></a><span data-ttu-id="6e9ed-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6e9ed-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6e9ed-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6e9ed-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="6e9ed-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="6e9ed-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="6e9ed-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6e9ed-106">Event ID</span></span>|-|  
|<span data-ttu-id="6e9ed-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="6e9ed-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="6e9ed-108">EDI</span><span class="sxs-lookup"><span data-stu-id="6e9ed-108"> EDI</span></span>|  
|<span data-ttu-id="6e9ed-109">元件</span><span class="sxs-lookup"><span data-stu-id="6e9ed-109">Component</span></span>|<span data-ttu-id="6e9ed-110">批次處理引擎</span><span class="sxs-lookup"><span data-stu-id="6e9ed-110">Batching Engine</span></span>|  
|<span data-ttu-id="6e9ed-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6e9ed-111">Symbolic Name</span></span>|<span data-ttu-id="6e9ed-112">PersistenceExceptionOccured</span><span class="sxs-lookup"><span data-stu-id="6e9ed-112">PersistenceExceptionOccured</span></span>|  
|<span data-ttu-id="6e9ed-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6e9ed-113">Message Text</span></span>|<span data-ttu-id="6e9ed-114">在批次處理協調流程中的批次提交期間發生持續性例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6e9ed-114">A persistence exception has occured during the batch submission in the batching Orchestration.</span></span> <span data-ttu-id="6e9ed-115">批次識別碼 = {0}，ErrorMessage = {1}。</span><span class="sxs-lookup"><span data-stu-id="6e9ed-115">Batch Id = {0}, ErrorMessage = {1}.</span></span> <span data-ttu-id="6e9ed-116">請檢查您的傳送埠訂閱，並加以修正。</span><span class="sxs-lookup"><span data-stu-id="6e9ed-116">Please check your send port subscriptions and fix them.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6e9ed-117">說明</span><span class="sxs-lookup"><span data-stu-id="6e9ed-117">Explanation</span></span>  
 <span data-ttu-id="6e9ed-118">這個錯誤/警告/資訊事件表示，BizTalk Server 無法傳送的批次的交換因為任何傳送埠不訂閱該交換。</span><span class="sxs-lookup"><span data-stu-id="6e9ed-118">This Error/Warning/Information event indicates that BizTalk Server could not send a batched interchange because no send port subscribed to the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6e9ed-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6e9ed-119">User Action</span></span>  
 <span data-ttu-id="6e9ed-120">若要解決這個錯誤，請確定傳送埠訂閱批次所設定的傳送埠的下列篩選屬性： EDI。DestinationPartyName = \<PartyName >，EDI。BatchEncodingType = EDIFACT 或 X12，以及 EDI。ToBeBatched = False。</span><span class="sxs-lookup"><span data-stu-id="6e9ed-120">To resolve this error, ensure that a send port subscribes to the batch by setting the following filter properties for the send port: EDI.DestinationPartyName = \<PartyName>, EDI.BatchEncodingType = EDIFACT or X12, and EDI.ToBeBatched = False.</span></span>