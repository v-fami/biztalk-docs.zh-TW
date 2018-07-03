---
title: 找不到的主機連接埠上的網頁伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c253fd5e-b815-4697-a06d-67af65a35589
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62f9260f477669debf709ba592568a15fbaf7194
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987143"
---
# <a name="web-server-on-host-port-not-found"></a><span data-ttu-id="1400a-102">找不到的主機連接埠上的 web 伺服器</span><span class="sxs-lookup"><span data-stu-id="1400a-102">Web server on host port not found</span></span>
## <a name="details"></a><span data-ttu-id="1400a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1400a-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="1400a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1400a-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="1400a-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="1400a-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="1400a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1400a-106">Event ID</span></span>     |                                         <span data-ttu-id="1400a-107">0</span><span class="sxs-lookup"><span data-stu-id="1400a-107">0</span></span>                                          |
|  <span data-ttu-id="1400a-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="1400a-108">Event Source</span></span>   |                                         <span data-ttu-id="1400a-109">0</span><span class="sxs-lookup"><span data-stu-id="1400a-109">0</span></span>                                          |
|    <span data-ttu-id="1400a-110">元件</span><span class="sxs-lookup"><span data-stu-id="1400a-110">Component</span></span>    |                                         <span data-ttu-id="1400a-111">0</span><span class="sxs-lookup"><span data-stu-id="1400a-111">0</span></span>                                          |
|  <span data-ttu-id="1400a-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1400a-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="1400a-113">0</span><span class="sxs-lookup"><span data-stu-id="1400a-113">0</span></span>                                          |
|  <span data-ttu-id="1400a-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1400a-114">Message Text</span></span>   |                    <span data-ttu-id="1400a-115">在主機上的 web 伺服器 」{0}"的連接埠{1}找不到</span><span class="sxs-lookup"><span data-stu-id="1400a-115">Web server on host "{0}" port {1} not found</span></span>                     |
  
## <a name="explanation"></a><span data-ttu-id="1400a-116">說明</span><span class="sxs-lookup"><span data-stu-id="1400a-116">Explanation</span></span>  
 <span data-ttu-id="1400a-117">此錯誤表示全球資訊網 (WWW) 服務未執行。</span><span class="sxs-lookup"><span data-stu-id="1400a-117">This error indicates the World Wide Web (WWW) service is not running.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1400a-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1400a-118">User Action</span></span>  
 <span data-ttu-id="1400a-119">您可以使用下列程序來啟動 World Wide Web 服務。</span><span class="sxs-lookup"><span data-stu-id="1400a-119">Use the following procedure to start the World Wide Web service.</span></span>  
  
#### <a name="to-start-the-world-wide-web-service"></a><span data-ttu-id="1400a-120">若要啟動 World Wide Web 服務</span><span class="sxs-lookup"><span data-stu-id="1400a-120">To start the World Wide Web service</span></span>  
  
1.  <span data-ttu-id="1400a-121">按一下 **開始**，按一下**控制台**，按兩下**系統管理工具**，然後按兩下**服務。**</span><span class="sxs-lookup"><span data-stu-id="1400a-121">Click **Start**, click **Control Panel**, double-click **Administrative Tools**, and double-click **Services.**</span></span>  
  
2.  <span data-ttu-id="1400a-122">在 [名稱] 欄中，找出**World Wide Web Publishing**。</span><span class="sxs-lookup"><span data-stu-id="1400a-122">In the Name column, locate **World Wide Web Publishing**.</span></span> <span data-ttu-id="1400a-123">請確定狀態為**已啟動**。</span><span class="sxs-lookup"><span data-stu-id="1400a-123">Ensure that the status is **Started**.</span></span>  
  
3.  <span data-ttu-id="1400a-124">返回**系統管理工具**視窗。</span><span class="sxs-lookup"><span data-stu-id="1400a-124">Return to the **Administrative Tools** window.</span></span> <span data-ttu-id="1400a-125">按兩下**Internet Information Services**。</span><span class="sxs-lookup"><span data-stu-id="1400a-125">Double-click **Internet Information Services**.</span></span>  
  
4.  <span data-ttu-id="1400a-126">展開 [資料夾] 區域，然後找出網站。</span><span class="sxs-lookup"><span data-stu-id="1400a-126">Expand the folder area and locate the web site.</span></span>  
  
5.  <span data-ttu-id="1400a-127">請確定狀態為**已啟動**。</span><span class="sxs-lookup"><span data-stu-id="1400a-127">Ensure that the status is **Started**.</span></span>