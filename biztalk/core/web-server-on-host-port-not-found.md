---
title: "找不到的主機連接埠上的 web 伺服器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c253fd5e-b815-4697-a06d-67af65a35589
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3dce09ce00a169ad14bbc8ae2ab28fe70c039c2b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="web-server-on-host-port-not-found"></a><span data-ttu-id="75498-102">Web 伺服器上找不到的主機連接埠</span><span class="sxs-lookup"><span data-stu-id="75498-102">Web server on host port not found</span></span>
## <a name="details"></a><span data-ttu-id="75498-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="75498-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="75498-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="75498-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="75498-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="75498-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="75498-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="75498-106">Event ID</span></span>|<span data-ttu-id="75498-107">0</span><span class="sxs-lookup"><span data-stu-id="75498-107">0</span></span>|  
|<span data-ttu-id="75498-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="75498-108">Event Source</span></span>|<span data-ttu-id="75498-109">0</span><span class="sxs-lookup"><span data-stu-id="75498-109">0</span></span>|  
|<span data-ttu-id="75498-110">元件</span><span class="sxs-lookup"><span data-stu-id="75498-110">Component</span></span>|<span data-ttu-id="75498-111">0</span><span class="sxs-lookup"><span data-stu-id="75498-111">0</span></span>|  
|<span data-ttu-id="75498-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="75498-112">Symbolic Name</span></span>|<span data-ttu-id="75498-113">0</span><span class="sxs-lookup"><span data-stu-id="75498-113">0</span></span>|  
|<span data-ttu-id="75498-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="75498-114">Message Text</span></span>|<span data-ttu-id="75498-115">Web 伺服器上找不到主機"{0}"的連接埠 {1}</span><span class="sxs-lookup"><span data-stu-id="75498-115">Web server on host "{0}" port {1} not found</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="75498-116">說明</span><span class="sxs-lookup"><span data-stu-id="75498-116">Explanation</span></span>  
 <span data-ttu-id="75498-117">此錯誤表示全球資訊網 (WWW) 服務未執行。</span><span class="sxs-lookup"><span data-stu-id="75498-117">This error indicates the World Wide Web (WWW) service is not running.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="75498-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="75498-118">User Action</span></span>  
 <span data-ttu-id="75498-119">您可以使用下列程序來啟動 World Wide Web 服務。</span><span class="sxs-lookup"><span data-stu-id="75498-119">Use the following procedure to start the World Wide Web service.</span></span>  
  
#### <a name="to-start-the-world-wide-web-service"></a><span data-ttu-id="75498-120">若要啟動 World Wide Web 服務</span><span class="sxs-lookup"><span data-stu-id="75498-120">To start the World Wide Web service</span></span>  
  
1.  <span data-ttu-id="75498-121">按一下**啟動**，按一下 **控制台**，按兩下**系統管理工具**，然後按兩下**服務。**</span><span class="sxs-lookup"><span data-stu-id="75498-121">Click **Start**, click **Control Panel**, double-click **Administrative Tools**, and double-click **Services.**</span></span>  
  
2.  <span data-ttu-id="75498-122">在 [名稱] 欄中，找出**World Wide Web Publishing**。</span><span class="sxs-lookup"><span data-stu-id="75498-122">In the Name column, locate **World Wide Web Publishing**.</span></span> <span data-ttu-id="75498-123">請確定的狀態是 **已啟動**。</span><span class="sxs-lookup"><span data-stu-id="75498-123">Ensure that the status is **Started**.</span></span>  
  
3.  <span data-ttu-id="75498-124">返回**系統管理工具**視窗。</span><span class="sxs-lookup"><span data-stu-id="75498-124">Return to the **Administrative Tools** window.</span></span> <span data-ttu-id="75498-125">按兩下**Internet Information Services**。</span><span class="sxs-lookup"><span data-stu-id="75498-125">Double-click **Internet Information Services**.</span></span>  
  
4.  <span data-ttu-id="75498-126">展開資料夾區域，然後尋找網站。</span><span class="sxs-lookup"><span data-stu-id="75498-126">Expand the folder area and locate the web site.</span></span>  
  
5.  <span data-ttu-id="75498-127">請確定的狀態是 **已啟動**。</span><span class="sxs-lookup"><span data-stu-id="75498-127">Ensure that the status is **Started**.</span></span>