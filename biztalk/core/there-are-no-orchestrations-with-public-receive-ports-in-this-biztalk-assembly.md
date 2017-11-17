---
title: "沒有公開使用沒有協調流程中此 BizTalk 組件的接收埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb901d49-ce3c-4bc6-806a-eb5964d32bb4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e04c10119b617ebabe07169dcae999fe60210e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="there-are-no-orchestrations-with-public-receive-ports-in-this-biztalk-assembly"></a><span data-ttu-id="82936-102">沒有公開使用沒有協調流程中此 BizTalk 組件的接收埠</span><span class="sxs-lookup"><span data-stu-id="82936-102">There are no orchestrations with public receive ports in this BizTalk assembly</span></span>
## <a name="details"></a><span data-ttu-id="82936-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="82936-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="82936-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="82936-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="82936-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="82936-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="82936-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="82936-106">Event ID</span></span>|<span data-ttu-id="82936-107">0</span><span class="sxs-lookup"><span data-stu-id="82936-107">0</span></span>|  
|<span data-ttu-id="82936-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="82936-108">Event Source</span></span>|<span data-ttu-id="82936-109">0</span><span class="sxs-lookup"><span data-stu-id="82936-109">0</span></span>|  
|<span data-ttu-id="82936-110">元件</span><span class="sxs-lookup"><span data-stu-id="82936-110">Component</span></span>|<span data-ttu-id="82936-111">0</span><span class="sxs-lookup"><span data-stu-id="82936-111">0</span></span>|  
|<span data-ttu-id="82936-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="82936-112">Symbolic Name</span></span>|<span data-ttu-id="82936-113">0</span><span class="sxs-lookup"><span data-stu-id="82936-113">0</span></span>|  
|<span data-ttu-id="82936-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="82936-114">Message Text</span></span>|<span data-ttu-id="82936-115">沒有公開使用沒有協調流程中此 BizTalk 組件的接收埠。</span><span class="sxs-lookup"><span data-stu-id="82936-115">There are no orchestrations with public receive ports in this BizTalk assembly.</span></span> <span data-ttu-id="82936-116">按一下 上一步，指定 BizTalk 組件包含使用公開的協調流程接收埠</span><span class="sxs-lookup"><span data-stu-id="82936-116">Click back and specify a BizTalk assembly containing orchestrations with public receive ports</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="82936-117">說明</span><span class="sxs-lookup"><span data-stu-id="82936-117">Explanation</span></span>  
 <span data-ttu-id="82936-118">此錯誤表示選取的協調流程並沒有公用連接埠。</span><span class="sxs-lookup"><span data-stu-id="82936-118">This error indicates the orchestration selected does not have a public port.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="82936-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="82936-119">User Action</span></span>  
 <span data-ttu-id="82936-120">您可以使用下列程序來設定公用連接埠。</span><span class="sxs-lookup"><span data-stu-id="82936-120">Use the following procedure to configure a public port.</span></span>  
  
#### <a name="to-configure-a-public-port"></a><span data-ttu-id="82936-121">若要設定公用連接埠</span><span class="sxs-lookup"><span data-stu-id="82936-121">To configure a public port</span></span>  
  
1.  <span data-ttu-id="82936-122">尋找協調流程，並建立所需的接收埠公用。</span><span class="sxs-lookup"><span data-stu-id="82936-122">Locate the orchestration and make the desired receive port public.</span></span>  
  
    1.  <span data-ttu-id="82936-123">開啟連接埠組態精靈。</span><span class="sxs-lookup"><span data-stu-id="82936-123">Open the Port Configuration wizard.</span></span>  
  
    2.  <span data-ttu-id="82936-124">在**選取連接埠類型**，變更**存取限制**從**內部**（預設） 加入**公用-沒有限制**。</span><span class="sxs-lookup"><span data-stu-id="82936-124">In **Select a Port Type**, change **Access Restrictions** from **Internal** (default) to **Public-no limits**.</span></span>  
  
2.  <span data-ttu-id="82936-125">重新編譯的組件。</span><span class="sxs-lookup"><span data-stu-id="82936-125">Recompile the assembly.</span></span>  
  
     <span data-ttu-id="82936-126">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="82936-126">\- OR -</span></span>  
  
     <span data-ttu-id="82936-127">載入具有公用的 BizTalk 組件的接收埠。</span><span class="sxs-lookup"><span data-stu-id="82936-127">Load a BizTalk assembly with public receive ports.</span></span>