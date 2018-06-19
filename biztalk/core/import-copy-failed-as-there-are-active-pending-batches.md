---
title: 匯入複製失敗，因為有作用中擱置批次 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17803f0a-3c70-4a8a-8e8d-7f874ed9ad92
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e3055f3e95ef3d0fb8bf5a36dae5957e318f6e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256718"
---
# <a name="import-copy-failed-as-there-are-active-pending-batches"></a><span data-ttu-id="26531-102">匯入複製失敗，因為有作用中擱置批次</span><span class="sxs-lookup"><span data-stu-id="26531-102">Import-Copy failed as there are active-pending batches</span></span>
## <a name="details"></a><span data-ttu-id="26531-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="26531-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="26531-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="26531-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="26531-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="26531-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="26531-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="26531-106">Event ID</span></span>|-|  
|<span data-ttu-id="26531-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="26531-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="26531-108">EDI</span><span class="sxs-lookup"><span data-stu-id="26531-108"> EDI</span></span>|  
|<span data-ttu-id="26531-109">元件</span><span class="sxs-lookup"><span data-stu-id="26531-109">Component</span></span>|<span data-ttu-id="26531-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="26531-110">EDI Engine</span></span>|  
|<span data-ttu-id="26531-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="26531-111">Symbolic Name</span></span>|<span data-ttu-id="26531-112">Err_ActiveBatchFound</span><span class="sxs-lookup"><span data-stu-id="26531-112">Err_ActiveBatchFound</span></span>|  
|<span data-ttu-id="26531-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="26531-113">Message Text</span></span>|<span data-ttu-id="26531-114">匯入/複製失敗，因為有作用中/擱置中的批次。</span><span class="sxs-lookup"><span data-stu-id="26531-114">Import/Copy failed as there are active/pending batches.</span></span> <span data-ttu-id="26531-115">停止作用中/擱置中的批次，然後再次嘗試匯入/複製。</span><span class="sxs-lookup"><span data-stu-id="26531-115">Stop active/pending batches and try importing/copying.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="26531-116">說明</span><span class="sxs-lookup"><span data-stu-id="26531-116">Explanation</span></span>  
 <span data-ttu-id="26531-117">這個錯誤/警告/資訊事件表示 BizTalk Server 無法匯入繫結檔案，或複製的設定，受影響的合約具有一或多個作用中或暫止的批次。</span><span class="sxs-lookup"><span data-stu-id="26531-117">This Error/Warning/Information event indicates BizTalk Server was unable to Import a binding file or copy the settings as the affected Agreement(s) have one or more active or pending batch.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="26531-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="26531-118">User Action</span></span>  
 <span data-ttu-id="26531-119">若要解決這個錯誤，請確定在受影響的協議中的所有批次會顯示為協議屬性中已停止。</span><span class="sxs-lookup"><span data-stu-id="26531-119">To resolve this error, ensure that all the batches in affected agreements are showing as stopped in the Agreement properties.</span></span>