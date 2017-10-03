---
title: "找不到對應至批次的協議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d1c0480-9a6f-481a-9143-e5a55707c3b5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bce17af0e382a137dc8d55d30705da58dd52301c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="could-not-find-an-agreement-corresponding-to-batch"></a><span data-ttu-id="05cd7-102">找不到對應至批次的協議</span><span class="sxs-lookup"><span data-stu-id="05cd7-102">Could not find an Agreement corresponding to batch</span></span>
## <a name="details"></a><span data-ttu-id="05cd7-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="05cd7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="05cd7-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="05cd7-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="05cd7-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="05cd7-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="05cd7-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="05cd7-106">Event ID</span></span>|-|  
|<span data-ttu-id="05cd7-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="05cd7-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="05cd7-108">EDI</span><span class="sxs-lookup"><span data-stu-id="05cd7-108"> EDI</span></span>|  
|<span data-ttu-id="05cd7-109">元件</span><span class="sxs-lookup"><span data-stu-id="05cd7-109">Component</span></span>|<span data-ttu-id="05cd7-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="05cd7-110">EDI Engine</span></span>|  
|<span data-ttu-id="05cd7-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="05cd7-111">Symbolic Name</span></span>|<span data-ttu-id="05cd7-112">AgreementNotFoundForBatch</span><span class="sxs-lookup"><span data-stu-id="05cd7-112">AgreementNotFoundForBatch</span></span>|  
|<span data-ttu-id="05cd7-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="05cd7-113">Message Text</span></span>|<span data-ttu-id="05cd7-114">找不到對應至批次 {0} 協議。</span><span class="sxs-lookup"><span data-stu-id="05cd7-114">Could not find an Agreement corresponding to batch {0}.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="05cd7-115">說明</span><span class="sxs-lookup"><span data-stu-id="05cd7-115">Explanation</span></span>  
 <span data-ttu-id="05cd7-116">這個錯誤/警告/資訊事件表示 BizTalk Server 找不到批次對應至這個識別碼，在嘗試啟動/停止批次或處理批次訊息。</span><span class="sxs-lookup"><span data-stu-id="05cd7-116">This Error/Warning/Information event indicates BizTalk Server was unable to find a Batch corresponding to this Id while trying to start/stop a batch or process a batch message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="05cd7-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="05cd7-117">User Action</span></span>  
 <span data-ttu-id="05cd7-118">若要解決這個錯誤，請確認具有指定識別碼的批次存在內含協議的協議屬性。</span><span class="sxs-lookup"><span data-stu-id="05cd7-118">To resolve this error, ensure that a batch with the given Id is present in the Agreement properties of the containing Agreement.</span></span>