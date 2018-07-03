---
title: 批次處理協調流程中提交批次期間發生持續性例外狀況 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6e832f-9d01-46e7-aaf5-2b402d509fac
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8a1277dd26fcb2036e3378f7fa6d22067a1f7e5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37020916"
---
# <a name="a-persistence-exception-has-occurred-during-the-batch-submission-in-the-batching-orchestration"></a><span data-ttu-id="8bfab-102">批次處理協調流程中提交批次期間發生持續性例外狀況</span><span class="sxs-lookup"><span data-stu-id="8bfab-102">A persistence exception has occurred during the batch submission in the batching Orchestration</span></span>
## <a name="details"></a><span data-ttu-id="8bfab-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8bfab-103">Details</span></span>  
  
|                 |                                                                                                                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="8bfab-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8bfab-104">Product Name</span></span>   |                                                     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                     |
| <span data-ttu-id="8bfab-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="8bfab-105">Product Version</span></span> |                                                                 [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                 |
|    <span data-ttu-id="8bfab-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8bfab-106">Event ID</span></span>     |                                                                                             -                                                                                              |
|  <span data-ttu-id="8bfab-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="8bfab-107">Event Source</span></span>   |                                                   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8bfab-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="8bfab-108"> EDI</span></span>                                                   |
|    <span data-ttu-id="8bfab-109">元件</span><span class="sxs-lookup"><span data-stu-id="8bfab-109">Component</span></span>    |                                                                                      <span data-ttu-id="8bfab-110">批次引擎</span><span class="sxs-lookup"><span data-stu-id="8bfab-110">Batching Engine</span></span>                                                                                       |
|  <span data-ttu-id="8bfab-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8bfab-111">Symbolic Name</span></span>  |                                                                                <span data-ttu-id="8bfab-112">PersistenceExceptionOccured</span><span class="sxs-lookup"><span data-stu-id="8bfab-112">PersistenceExceptionOccured</span></span>                                                                                 |
|  <span data-ttu-id="8bfab-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8bfab-113">Message Text</span></span>   | <span data-ttu-id="8bfab-114">批次處理協調流程中提交批次期間發生持續性例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8bfab-114">A persistence exception has occured during the batch submission in the batching Orchestration.</span></span> <span data-ttu-id="8bfab-115">批次識別碼 = {0}，ErrorMessage = {1}。</span><span class="sxs-lookup"><span data-stu-id="8bfab-115">Batch Id = {0}, ErrorMessage = {1}.</span></span> <span data-ttu-id="8bfab-116">請檢查您的傳送埠訂閱，並加以修正。</span><span class="sxs-lookup"><span data-stu-id="8bfab-116">Please check your send port subscriptions and fix them.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="8bfab-117">說明</span><span class="sxs-lookup"><span data-stu-id="8bfab-117">Explanation</span></span>  
 <span data-ttu-id="8bfab-118">這個錯誤/警告/資訊事件表示，BizTalk Server 無法傳送的批次的交換因為任何傳送埠不訂閱該交換。</span><span class="sxs-lookup"><span data-stu-id="8bfab-118">This Error/Warning/Information event indicates that BizTalk Server could not send a batched interchange because no send port subscribed to the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8bfab-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8bfab-119">User Action</span></span>  
 <span data-ttu-id="8bfab-120">若要解決這個錯誤，請確定傳送埠訂閱批次設定下列的篩選條件屬性，傳送埠： EDI。DestinationPartyName = \<PartyName\>，EDI。BatchEncodingType = EDIFACT 或 X12，以及 EDI。ToBeBatched = False。</span><span class="sxs-lookup"><span data-stu-id="8bfab-120">To resolve this error, ensure that a send port subscribes to the batch by setting the following filter properties for the send port: EDI.DestinationPartyName = \<PartyName\>, EDI.BatchEncodingType = EDIFACT or X12, and EDI.ToBeBatched = False.</span></span>