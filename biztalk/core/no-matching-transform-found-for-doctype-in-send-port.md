---
title: "沒有相符的轉換傳送埠中找到的 DocType |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23f62ac7-3849-49fe-a765-2be72880a4c9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8bc45ac0edf425bc19ab526fac6b2690f3a6b6d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="no-matching-transform-found-for-doctype-in-send-port"></a><span data-ttu-id="95726-102">傳送埠中找到的文件類型不符合轉換</span><span class="sxs-lookup"><span data-stu-id="95726-102">No matching transform found for DocType in Send Port</span></span>
## <a name="details"></a><span data-ttu-id="95726-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="95726-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="95726-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="95726-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="95726-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="95726-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="95726-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="95726-106">Event ID</span></span>|-|  
|<span data-ttu-id="95726-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="95726-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="95726-108">EDI</span><span class="sxs-lookup"><span data-stu-id="95726-108"> EDI</span></span>|  
|<span data-ttu-id="95726-109">元件</span><span class="sxs-lookup"><span data-stu-id="95726-109">Component</span></span>|<span data-ttu-id="95726-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="95726-110">EDI Engine</span></span>|  
|<span data-ttu-id="95726-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="95726-111">Symbolic Name</span></span>|<span data-ttu-id="95726-112">NoMatchingTransformFoundForSendPortAndDocType</span><span class="sxs-lookup"><span data-stu-id="95726-112">NoMatchingTransformFoundForSendPortAndDocType</span></span>|  
|<span data-ttu-id="95726-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="95726-113">Message Text</span></span>|<span data-ttu-id="95726-114">在傳送埠 {1} DocType {0} 找到任何比對轉換。</span><span class="sxs-lookup"><span data-stu-id="95726-114">No matching transform found for DocType {0} in Send Port {1}.</span></span> <span data-ttu-id="95726-115">與 ExplorerOM 資訊不一致</span><span class="sxs-lookup"><span data-stu-id="95726-115">Inconsistent with ExplorerOM information</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="95726-116">說明</span><span class="sxs-lookup"><span data-stu-id="95726-116">Explanation</span></span>  
 <span data-ttu-id="95726-117">此錯誤表示，比對的轉換找不到指定的文件類型和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="95726-117">This error indicates that a matching transform was not found for a given DocType and SendPort.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="95726-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="95726-118">User Action</span></span>  
 <span data-ttu-id="95726-119">若要解決這個錯誤，請繼續進行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="95726-119">To resolve this error, proceed as follows:</span></span>  
  
1.  <span data-ttu-id="95726-120">開啟 BizTalk 管理主控台，找出傳輸，並以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="95726-120">Open the BizTalk Administration console, locate the transport, and right-click the transport name.</span></span>  
  
2.  <span data-ttu-id="95726-121">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="95726-121">Click **Properties**.</span></span>  
  
3.  <span data-ttu-id="95726-122">在 [連接埠類型] 清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="95726-122">In the port Type list, select the correct port.</span></span> <span data-ttu-id="95726-123">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="95726-123">Click **Configure**.</span></span>  
  
4.  <span data-ttu-id="95726-124">在 [連接埠名稱] 傳送埠屬性] 對話方塊中，按一下 [**輸出對應**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="95726-124">In the [port name] Send Port Properties dialog box, click **Outbound Maps** in the left pane.</span></span>  
  
5.  <span data-ttu-id="95726-125">請確認該對應會列在此處，它會對應至正確的文件類型。</span><span class="sxs-lookup"><span data-stu-id="95726-125">Verify that the map is listed here and that it corresponds to the correct document type.</span></span>