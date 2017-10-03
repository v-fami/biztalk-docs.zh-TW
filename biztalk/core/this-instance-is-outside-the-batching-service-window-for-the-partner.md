---
title: "這個執行個體為夥伴批次服務窗口之外 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e420d75-11fd-4221-9d97-814ca6e48c81
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e93e7e769a8f0e30b3753af690a69c5e6eaa9786
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="this-instance-is-outside-the-batching-service-window-for-the-partner"></a><span data-ttu-id="edb10-102">此執行個體在夥伴的 [批次處理服務] 視窗外</span><span class="sxs-lookup"><span data-stu-id="edb10-102">This instance is outside the Batching Service window for the partner</span></span>
## <a name="details"></a><span data-ttu-id="edb10-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="edb10-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="edb10-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="edb10-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="edb10-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="edb10-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="edb10-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="edb10-106">Event ID</span></span>|-|  
|<span data-ttu-id="edb10-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="edb10-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="edb10-108">EDI</span><span class="sxs-lookup"><span data-stu-id="edb10-108"> EDI</span></span>|  
|<span data-ttu-id="edb10-109">元件</span><span class="sxs-lookup"><span data-stu-id="edb10-109">Component</span></span>|<span data-ttu-id="edb10-110">批次處理引擎</span><span class="sxs-lookup"><span data-stu-id="edb10-110">Batching Engine</span></span>|  
|<span data-ttu-id="edb10-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="edb10-111">Symbolic Name</span></span>|<span data-ttu-id="edb10-112">OutsideBatchingServiceWindow</span><span class="sxs-lookup"><span data-stu-id="edb10-112">OutsideBatchingServiceWindow</span></span>|  
|<span data-ttu-id="edb10-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="edb10-113">Message Text</span></span>|<span data-ttu-id="edb10-114">此執行個體在夥伴的 [批次處理服務] 視窗外</span><span class="sxs-lookup"><span data-stu-id="edb10-114">This instance is outside the Batching Service window for the partner</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="edb10-115">說明</span><span class="sxs-lookup"><span data-stu-id="edb10-115">Explanation</span></span>  
 <span data-ttu-id="edb10-116">這個錯誤/警告/資訊事件表示，由於批次處理協調流程的執行個體位在合作對象的啟動範圍之外，因此該執行個體無法啟動。</span><span class="sxs-lookup"><span data-stu-id="edb10-116">This Error/Warning/Information event indicates that an instance of the batching orchestration could not be started because the instance fell outside the activation range for the party.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="edb10-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="edb10-117">User Action</span></span>  
 <span data-ttu-id="edb10-118">若要解決這個錯誤，開啟 交換批次建立設定 頁面的 EDI 屬性的合作對象，並確定協調流程執行個體是在啟動範圍內。</span><span class="sxs-lookup"><span data-stu-id="edb10-118">To resolve this error, open the Interchange Batch Creations Settings page of the EDI Properties for the party, and make sure that the orchestration instance is within the activation range.</span></span> <span data-ttu-id="edb10-119">如果沒有，請變更的開始時間屬性，然後再按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="edb10-119">If not, change the Start time property and then click **Start**.</span></span>