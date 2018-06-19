---
title: WCF 執行階段錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5591bd4-aa15-4c7a-903e-fc73b880692f
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97f4107ddf791b8d9fd152f2258cd3185f23498f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288190"
---
# <a name="wcf-run-time-errors"></a><span data-ttu-id="56226-102">WCF 執行階段錯誤</span><span class="sxs-lookup"><span data-stu-id="56226-102">WCF Run-Time Errors</span></span>
<span data-ttu-id="56226-103">診斷及解決 WCF 執行階段事件的資訊。</span><span class="sxs-lookup"><span data-stu-id="56226-103">Information for diagnosing and resolving WCF run-time events.</span></span>  
  
## <a name="wcf-service-host-restarted"></a><span data-ttu-id="56226-104">WCF 服務主控件已重新啟動</span><span class="sxs-lookup"><span data-stu-id="56226-104">WCF service host restarted</span></span>
  
||<span data-ttu-id="56226-105">錯誤詳細資料</span><span class="sxs-lookup"><span data-stu-id="56226-105">Error details</span></span>|  
|-|-|  
|<span data-ttu-id="56226-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="56226-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="56226-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="56226-107">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="56226-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="56226-108">Event ID</span></span>|<span data-ttu-id="56226-109">0x1FB0</span><span class="sxs-lookup"><span data-stu-id="56226-109">0x1FB0</span></span>|  
|<span data-ttu-id="56226-110">事件來源</span><span class="sxs-lookup"><span data-stu-id="56226-110">Event Source</span></span>|<span data-ttu-id="56226-111">0</span><span class="sxs-lookup"><span data-stu-id="56226-111">0</span></span>|  
|<span data-ttu-id="56226-112">元件</span><span class="sxs-lookup"><span data-stu-id="56226-112">Component</span></span>|<span data-ttu-id="56226-113">0</span><span class="sxs-lookup"><span data-stu-id="56226-113">0</span></span>|  
|<span data-ttu-id="56226-114">符號名稱</span><span class="sxs-lookup"><span data-stu-id="56226-114">Symbolic Name</span></span>|<span data-ttu-id="56226-115">BTS_I_WCF_SERVICE_HOST_RESTARTED</span><span class="sxs-lookup"><span data-stu-id="56226-115">BTS_I_WCF_SERVICE_HOST_RESTARTED</span></span>|  
|<span data-ttu-id="56226-116">訊息文字</span><span class="sxs-lookup"><span data-stu-id="56226-116">Message Text</span></span>|<span data-ttu-id="56226-117">0</span><span class="sxs-lookup"><span data-stu-id="56226-117">0</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="56226-118">說明</span><span class="sxs-lookup"><span data-stu-id="56226-118">Explanation</span></span>  
 <span data-ttu-id="56226-119">此訊息提供一個方式，讓 WCF 配接器寫入「資訊性」事件日誌項目 (針對配接器提供的 API 可用來建立警告或錯誤，但無法建立資訊)。</span><span class="sxs-lookup"><span data-stu-id="56226-119">This message provides a way for the WCF adapter to write an “informational” event log entry (the provided APIs for adapters allow the creation of warnings or errors, not information).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="56226-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="56226-120">User Action</span></span>  
 <span data-ttu-id="56226-121">如果您在事件日誌中看到此資訊事件，表示自動復原已成功。</span><span class="sxs-lookup"><span data-stu-id="56226-121">If you see this informational event in the event log, it indicates that the auto-recovery has succeeded.</span></span> <span data-ttu-id="56226-122">不需要針對此訊息採取任何進一步動作。</span><span class="sxs-lookup"><span data-stu-id="56226-122">No further action in regard to this message is necessary.</span></span>