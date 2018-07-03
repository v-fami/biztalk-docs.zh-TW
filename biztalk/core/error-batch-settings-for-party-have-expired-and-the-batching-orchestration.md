---
title: 合作對象的批次設定已過期，和批次處理協調流程即將終止 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2f272b6-4da2-4736-8d61-ce48359f36dd
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 471d42035f0c8c279fd25e8bb5ba480f7e0f962a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990055"
---
# <a name="the-batch-settings-for-party-have-expired-and-the-batching-orchestration-is-being-terminated"></a><span data-ttu-id="52d8f-102">合作對象的批次設定已過期，正在終止批次處理協調流程</span><span class="sxs-lookup"><span data-stu-id="52d8f-102">The batch settings for party have expired and the batching orchestration is being terminated</span></span>
## <a name="details"></a><span data-ttu-id="52d8f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="52d8f-103">Details</span></span>  
  
|                 |                                                                                                                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="52d8f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="52d8f-104">Product Name</span></span>   |                                                  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                   |
| <span data-ttu-id="52d8f-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="52d8f-105">Product Version</span></span> |                                                              [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                               |
|    <span data-ttu-id="52d8f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="52d8f-106">Event ID</span></span>     |                                                                                           -                                                                                           |
|  <span data-ttu-id="52d8f-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="52d8f-107">Event Source</span></span>   |                                                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="52d8f-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="52d8f-108"> EDI</span></span>                                                 |
|    <span data-ttu-id="52d8f-109">元件</span><span class="sxs-lookup"><span data-stu-id="52d8f-109">Component</span></span>    |                                                                                    <span data-ttu-id="52d8f-110">批次引擎</span><span class="sxs-lookup"><span data-stu-id="52d8f-110">Batching Engine</span></span>                                                                                    |
|  <span data-ttu-id="52d8f-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="52d8f-111">Symbolic Name</span></span>  |                                                                                 <span data-ttu-id="52d8f-112">BatchSettingsExpired</span><span class="sxs-lookup"><span data-stu-id="52d8f-112">BatchSettingsExpired</span></span>                                                                                  |
|  <span data-ttu-id="52d8f-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="52d8f-113">Message Text</span></span>   | <span data-ttu-id="52d8f-114">合作對象的批次設定{0}已過期批次處理協調流程即將終止。</span><span class="sxs-lookup"><span data-stu-id="52d8f-114">The batch settings for party {0} have expired and the batching orchestration is being terminated.</span></span> <span data-ttu-id="52d8f-115">將不會產生其他批次，直到此合作對象的批次處理啟動</span><span class="sxs-lookup"><span data-stu-id="52d8f-115">Further batches will not be generated till the batching is activated for this party</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="52d8f-116">說明</span><span class="sxs-lookup"><span data-stu-id="52d8f-116">Explanation</span></span>  
 <span data-ttu-id="52d8f-117">這則警告表示批次協調流程執行個體已停用，因為已達到啟用範圍的結尾。</span><span class="sxs-lookup"><span data-stu-id="52d8f-117">This Warning indicates that the batching orchestration instance has been deactivated because the end of the activation range has been reached.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="52d8f-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="52d8f-118">User Action</span></span>  
 <span data-ttu-id="52d8f-119">若要解決這個錯誤，重新啟動下列批次處理程序：</span><span class="sxs-lookup"><span data-stu-id="52d8f-119">To resolve this error, restart the batching process by doing the following:</span></span>  
  
1.  <span data-ttu-id="52d8f-120">開啟 BizTalk Server 管理主控台中，並移至 [交換批次建立設定] 頁面的 [EDI 屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="52d8f-120">Open the BizTalk Server Administration Console, and move to the Interchange Batch Creation Settings Page of the EDI Properties dialog box.</span></span>  
  
2.  <span data-ttu-id="52d8f-121">重設結束準則，並按一下來重新啟動協調流程**啟動**。</span><span class="sxs-lookup"><span data-stu-id="52d8f-121">Reset the end criteria, and then restart the orchestration by clicking **Start**.</span></span>  
  
3.  <span data-ttu-id="52d8f-122">當您按下的時間之前開始的日期時間是否**開始**，按一下**是**更新目前的日期時間的開始日期時間。</span><span class="sxs-lookup"><span data-stu-id="52d8f-122">If the Start datetime is prior to the time when you clicked **Start**, click **Yes** to update the Start datetime to the current datetime.</span></span>