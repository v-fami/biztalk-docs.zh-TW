---
title: 找不到批次 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e967e1a-b87f-4c87-a157-a6f63ba96d78
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fab810e4cfadc77c8fafe34b5cb78aaa417dfe5c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015063"
---
# <a name="the-batch-was-not-found"></a><span data-ttu-id="7aeed-102">找不到批次</span><span class="sxs-lookup"><span data-stu-id="7aeed-102">The batch was not found</span></span>
## <a name="details"></a><span data-ttu-id="7aeed-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7aeed-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="7aeed-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7aeed-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="7aeed-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="7aeed-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="7aeed-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7aeed-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="7aeed-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="7aeed-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7aeed-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="7aeed-108"> EDI</span></span> |
|    <span data-ttu-id="7aeed-109">元件</span><span class="sxs-lookup"><span data-stu-id="7aeed-109">Component</span></span>    |                                       <span data-ttu-id="7aeed-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="7aeed-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="7aeed-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7aeed-111">Symbolic Name</span></span>  |                                   <span data-ttu-id="7aeed-112">Err_BatchNotFound</span><span class="sxs-lookup"><span data-stu-id="7aeed-112">Err_BatchNotFound</span></span>                                    |
|  <span data-ttu-id="7aeed-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7aeed-113">Message Text</span></span>   |                                <span data-ttu-id="7aeed-114">找不到批次。</span><span class="sxs-lookup"><span data-stu-id="7aeed-114">The batch was not found.</span></span>                                |
  
## <a name="explanation"></a><span data-ttu-id="7aeed-115">說明</span><span class="sxs-lookup"><span data-stu-id="7aeed-115">Explanation</span></span>  
 <span data-ttu-id="7aeed-116">這個錯誤/警告/資訊事件表示 BizTalk Server 找不到批次期間啟動/停止批次，或當 「 批次處理協調流程嘗試批次訊息。</span><span class="sxs-lookup"><span data-stu-id="7aeed-116">This Error/Warning/Information event indicates BizTalk Server was unable to find a batch during the start/stop of a batch or while the Batching Orchestration was trying to batch a message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7aeed-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7aeed-117">User Action</span></span>  
 <span data-ttu-id="7aeed-118">若要解決這個錯誤，請確定個別的批次存在內含協議的協議屬性中。</span><span class="sxs-lookup"><span data-stu-id="7aeed-118">To resolve this error, ensure that the respective batch is present in the Agreement properties of the containing Agreement.</span></span>