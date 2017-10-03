---
title: "通訊模式錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06656073-9bae-4d6f-98ae-2714a72ee79c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36677694b8f2d0973c04d942a196d055b696bd5c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="communication-pattern-errors"></a><span data-ttu-id="bfeab-102">通訊模式錯誤</span><span class="sxs-lookup"><span data-stu-id="bfeab-102">Communication Pattern Errors</span></span>
<span data-ttu-id="bfeab-103">診斷及解決 WCF 通訊模式錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="bfeab-103">Information for diagnosing and resolving WCF Communication Pattern errors.</span></span>  

## <a name="fault-messages-are-not-supported-on-one-way-ports"></a><span data-ttu-id="bfeab-104">錯誤訊息不支援單向連接埠</span><span class="sxs-lookup"><span data-stu-id="bfeab-104">Fault messages are not supported on one-way ports</span></span>
  
||<span data-ttu-id="bfeab-105">錯誤詳細資料</span><span class="sxs-lookup"><span data-stu-id="bfeab-105">Error details</span></span>|  
|-|-|  
|<span data-ttu-id="bfeab-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="bfeab-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="bfeab-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="bfeab-107">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="bfeab-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="bfeab-108">Event ID</span></span>|<span data-ttu-id="bfeab-109">0</span><span class="sxs-lookup"><span data-stu-id="bfeab-109">0</span></span>|  
|<span data-ttu-id="bfeab-110">事件來源</span><span class="sxs-lookup"><span data-stu-id="bfeab-110">Event Source</span></span>|<span data-ttu-id="bfeab-111">0</span><span class="sxs-lookup"><span data-stu-id="bfeab-111">0</span></span>|  
|<span data-ttu-id="bfeab-112">元件</span><span class="sxs-lookup"><span data-stu-id="bfeab-112">Component</span></span>|<span data-ttu-id="bfeab-113">0</span><span class="sxs-lookup"><span data-stu-id="bfeab-113">0</span></span>|  
|<span data-ttu-id="bfeab-114">符號名稱</span><span class="sxs-lookup"><span data-stu-id="bfeab-114">Symbolic Name</span></span>|<span data-ttu-id="bfeab-115">0</span><span class="sxs-lookup"><span data-stu-id="bfeab-115">0</span></span>|  
|<span data-ttu-id="bfeab-116">訊息文字</span><span class="sxs-lookup"><span data-stu-id="bfeab-116">Message Text</span></span>|<span data-ttu-id="bfeab-117">錯誤訊息不支援單向連接埠。</span><span class="sxs-lookup"><span data-stu-id="bfeab-117">Fault messages are not supported on one-way ports.</span></span> <span data-ttu-id="bfeab-118">更正服務描述"{0}"連接埠類型 」 {1}"，然後再重新執行精靈</span><span class="sxs-lookup"><span data-stu-id="bfeab-118">Correct service description "{0}" port type "{1}" and rerun the wizard</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bfeab-119">說明</span><span class="sxs-lookup"><span data-stu-id="bfeab-119">Explanation</span></span>  
 <span data-ttu-id="bfeab-120">此錯誤表示嘗試從中使用的服務是單向的服務和指定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="bfeab-120">This error indicates the service trying to be consumed is a one-way service and has the fault specified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bfeab-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="bfeab-121">User Action</span></span>  
 <span data-ttu-id="bfeab-122">更正服務，請切換至要求-回應從單向通訊模式。</span><span class="sxs-lookup"><span data-stu-id="bfeab-122">Correct the service by switching the communication pattern from one-way to request-response.</span></span> <span data-ttu-id="bfeab-123">或在程式碼中移除該錯誤。</span><span class="sxs-lookup"><span data-stu-id="bfeab-123">Or remove the fault in the code.</span></span>
 
 