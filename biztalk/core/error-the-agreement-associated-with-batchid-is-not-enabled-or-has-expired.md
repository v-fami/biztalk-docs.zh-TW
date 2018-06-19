---
title: 批次識別碼相關聯的協議未啟用，或已過期。 無法繼續批次處理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d92cb07-7646-42b3-90a8-18acbcd145cd
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e68e91fe1cd2d91c20c84a32afd37212769a4736
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241486"
---
# <a name="the-agreement-associated-with-batchid-is-not-enabled-or-has-expired-batching-cannot-continue"></a><span data-ttu-id="b6ca0-103">批次識別碼相關聯的協議未啟用，或已過期。</span><span class="sxs-lookup"><span data-stu-id="b6ca0-103">The agreement associated with BatchId is not enabled or has expired.</span></span> <span data-ttu-id="b6ca0-104">批次無法繼續</span><span class="sxs-lookup"><span data-stu-id="b6ca0-104">Batching cannot continue</span></span>
## <a name="details"></a><span data-ttu-id="b6ca0-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b6ca0-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b6ca0-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b6ca0-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="b6ca0-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="b6ca0-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="b6ca0-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b6ca0-108">Event ID</span></span>|-|  
|<span data-ttu-id="b6ca0-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="b6ca0-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b6ca0-110">EDI</span><span class="sxs-lookup"><span data-stu-id="b6ca0-110"> EDI</span></span>|  
|<span data-ttu-id="b6ca0-111">元件</span><span class="sxs-lookup"><span data-stu-id="b6ca0-111">Component</span></span>|<span data-ttu-id="b6ca0-112">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="b6ca0-112">EDI Engine</span></span>|  
|<span data-ttu-id="b6ca0-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b6ca0-113">Symbolic Name</span></span>|<span data-ttu-id="b6ca0-114">ErrorBatchAgreementDisabled</span><span class="sxs-lookup"><span data-stu-id="b6ca0-114">ErrorBatchAgreementDisabled</span></span>|  
|<span data-ttu-id="b6ca0-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b6ca0-115">Message Text</span></span>|<span data-ttu-id="b6ca0-116">BatchId {0} 相關聯的協議未啟用，或已過期。</span><span class="sxs-lookup"><span data-stu-id="b6ca0-116">The agreement associated with BatchId {0} is not enabled or has expired.</span></span> <span data-ttu-id="b6ca0-117">無法繼續執行批次。</span><span class="sxs-lookup"><span data-stu-id="b6ca0-117">Batching cannot continue.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b6ca0-118">說明</span><span class="sxs-lookup"><span data-stu-id="b6ca0-118">Explanation</span></span>  
 <span data-ttu-id="b6ca0-119">這個錯誤/警告/資訊事件表示 BizTalk Server 無法取得過期的協議啟動批次或程序的批次訊息。</span><span class="sxs-lookup"><span data-stu-id="b6ca0-119">This Error/Warning/Information event indicates BizTalk Server was not able to start a batch or process a batch message because of Agreement getting expired.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b6ca0-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b6ca0-120">User Action</span></span>  
 <span data-ttu-id="b6ca0-121">若要解決這個錯誤，請確定具有指定識別碼的批次存在內含協議的協議屬性，而且其開始和結束日期落在協議的開始和結束日期。</span><span class="sxs-lookup"><span data-stu-id="b6ca0-121">To resolve this error, ensure that a batch with the given Id is present in the Agreement properties of the containing Agreement and its start and end date fall within the start and end dates of the Agreement.</span></span> <span data-ttu-id="b6ca0-122">也請確定已啟用 在協議。</span><span class="sxs-lookup"><span data-stu-id="b6ca0-122">Also make sure that the agreement is enabled.</span></span>