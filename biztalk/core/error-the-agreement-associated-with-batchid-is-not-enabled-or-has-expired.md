---
title: 與 BatchId 相關的協議尚未啟用，或已過期。 批次處理無法繼續。 |Microsoft Docs
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
ms.openlocfilehash: ace947d1c05774882b1e8f78f7b093f0795ba919
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018286"
---
# <a name="the-agreement-associated-with-batchid-is-not-enabled-or-has-expired-batching-cannot-continue"></a><span data-ttu-id="b8cf1-103">與 BatchId 相關的協議尚未啟用，或已過期。</span><span class="sxs-lookup"><span data-stu-id="b8cf1-103">The agreement associated with BatchId is not enabled or has expired.</span></span> <span data-ttu-id="b8cf1-104">批次處理無法繼續。</span><span class="sxs-lookup"><span data-stu-id="b8cf1-104">Batching cannot continue</span></span>
## <a name="details"></a><span data-ttu-id="b8cf1-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b8cf1-105">Details</span></span>  
  
|                 |                                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="b8cf1-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b8cf1-106">Product Name</span></span>   |         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]         |
| <span data-ttu-id="b8cf1-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="b8cf1-107">Product Version</span></span> |                     [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                     |
|    <span data-ttu-id="b8cf1-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b8cf1-108">Event ID</span></span>     |                                                 -                                                  |
|  <span data-ttu-id="b8cf1-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="b8cf1-109">Event Source</span></span>   |       [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b8cf1-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="b8cf1-110"> EDI</span></span>       |
|    <span data-ttu-id="b8cf1-111">元件</span><span class="sxs-lookup"><span data-stu-id="b8cf1-111">Component</span></span>    |                                             <span data-ttu-id="b8cf1-112">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="b8cf1-112">EDI Engine</span></span>                                             |
|  <span data-ttu-id="b8cf1-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b8cf1-113">Symbolic Name</span></span>  |                                    <span data-ttu-id="b8cf1-114">ErrorBatchAgreementDisabled</span><span class="sxs-lookup"><span data-stu-id="b8cf1-114">ErrorBatchAgreementDisabled</span></span>                                     |
|  <span data-ttu-id="b8cf1-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b8cf1-115">Message Text</span></span>   | <span data-ttu-id="b8cf1-116">與 BatchId 相關的協議{0}未啟用或已過期。</span><span class="sxs-lookup"><span data-stu-id="b8cf1-116">The agreement associated with BatchId {0} is not enabled or has expired.</span></span> <span data-ttu-id="b8cf1-117">批次處理無法繼續。</span><span class="sxs-lookup"><span data-stu-id="b8cf1-117">Batching cannot continue.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="b8cf1-118">說明</span><span class="sxs-lookup"><span data-stu-id="b8cf1-118">Explanation</span></span>  
 <span data-ttu-id="b8cf1-119">這個錯誤/警告/資訊事件表示 BizTalk Server 無法啟動，批次或程序的批次訊息因為取得過期的合約。</span><span class="sxs-lookup"><span data-stu-id="b8cf1-119">This Error/Warning/Information event indicates BizTalk Server was not able to start a batch or process a batch message because of Agreement getting expired.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b8cf1-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b8cf1-120">User Action</span></span>  
 <span data-ttu-id="b8cf1-121">若要解決這個錯誤，請確定具有指定識別碼的批次存在內含協議的協議屬性中，且其開始和結束日期落在協議的開始和結束日期。</span><span class="sxs-lookup"><span data-stu-id="b8cf1-121">To resolve this error, ensure that a batch with the given Id is present in the Agreement properties of the containing Agreement and its start and end date fall within the start and end dates of the Agreement.</span></span> <span data-ttu-id="b8cf1-122">也請確定已啟用合約。</span><span class="sxs-lookup"><span data-stu-id="b8cf1-122">Also make sure that the agreement is enabled.</span></span>