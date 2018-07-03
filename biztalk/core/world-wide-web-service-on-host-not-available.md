---
title: 無法使用的主機上的 World Wide Web 服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6b14eaae-2158-4aef-9561-610d033998be
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6c3623a7f39f773f720fa33cd64a7e93c3668d9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991103"
---
# <a name="world-wide-web-service-on-host-not-available"></a><span data-ttu-id="c64d6-102">無法使用的主機上的 World Wide Web 服務</span><span class="sxs-lookup"><span data-stu-id="c64d6-102">World Wide Web service on host not available</span></span>
## <a name="details"></a><span data-ttu-id="c64d6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c64d6-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="c64d6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c64d6-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="c64d6-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="c64d6-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="c64d6-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c64d6-106">Event ID</span></span>     |                                         <span data-ttu-id="c64d6-107">0</span><span class="sxs-lookup"><span data-stu-id="c64d6-107">0</span></span>                                          |
|  <span data-ttu-id="c64d6-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="c64d6-108">Event Source</span></span>   |                                         <span data-ttu-id="c64d6-109">0</span><span class="sxs-lookup"><span data-stu-id="c64d6-109">0</span></span>                                          |
|    <span data-ttu-id="c64d6-110">元件</span><span class="sxs-lookup"><span data-stu-id="c64d6-110">Component</span></span>    |                                         <span data-ttu-id="c64d6-111">0</span><span class="sxs-lookup"><span data-stu-id="c64d6-111">0</span></span>                                          |
|  <span data-ttu-id="c64d6-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c64d6-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="c64d6-113">0</span><span class="sxs-lookup"><span data-stu-id="c64d6-113">0</span></span>                                          |
|  <span data-ttu-id="c64d6-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c64d6-114">Message Text</span></span>   |             <span data-ttu-id="c64d6-115">在主機上的 World Wide Web 服務 (W3SVC) 」{0}"無法使用</span><span class="sxs-lookup"><span data-stu-id="c64d6-115">World Wide Web service (W3SVC) on host "{0}" not available</span></span>             |
  
## <a name="explanation"></a><span data-ttu-id="c64d6-116">說明</span><span class="sxs-lookup"><span data-stu-id="c64d6-116">Explanation</span></span>  
 <span data-ttu-id="c64d6-117">此錯誤表示全球資訊網服務並未執行。</span><span class="sxs-lookup"><span data-stu-id="c64d6-117">This error indicates the World Wide Web service is not running.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c64d6-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c64d6-118">User Action</span></span>  
 <span data-ttu-id="c64d6-119">您可以使用下列程序來啟動 World Wide Web 服務。</span><span class="sxs-lookup"><span data-stu-id="c64d6-119">Use the following procedure to start the World Wide Web service.</span></span>  
  
#### <a name="to-start-the-world-wide-web-service"></a><span data-ttu-id="c64d6-120">若要啟動 World Wide Web 服務</span><span class="sxs-lookup"><span data-stu-id="c64d6-120">To start the World Wide Web service</span></span>  
  
1.  <span data-ttu-id="c64d6-121">按一下 **開始**，按一下**控制台**，按兩下**系統管理工具**，然後按兩下**服務**。</span><span class="sxs-lookup"><span data-stu-id="c64d6-121">Click **Start**, click **Control Panel**, double-click **Administrative Tools**, and double-click **Services**.</span></span>  
  
2.  <span data-ttu-id="c64d6-122">在 [名稱] 欄中，找出**World Wide Web Publishing**。</span><span class="sxs-lookup"><span data-stu-id="c64d6-122">In the Name column, locate **World Wide Web Publishing**.</span></span> <span data-ttu-id="c64d6-123">請確定狀態為**已啟動**。</span><span class="sxs-lookup"><span data-stu-id="c64d6-123">Ensure that the status is **Started**.</span></span>