---
title: 協調流程沒有公用接收埠，此 BizTalk 組件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb901d49-ce3c-4bc6-806a-eb5964d32bb4
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c062f5e23972ed841c4c9d614ad58967a07a4fe2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978213"
---
# <a name="there-are-no-orchestrations-with-public-receive-ports-in-this-biztalk-assembly"></a><span data-ttu-id="08667-102">協調流程沒有公用接收埠，此 BizTalk 組件</span><span class="sxs-lookup"><span data-stu-id="08667-102">There are no orchestrations with public receive ports in this BizTalk assembly</span></span>
## <a name="details"></a><span data-ttu-id="08667-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="08667-103">Details</span></span>  
  
|                 |                                                                                                                                                                               |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="08667-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="08667-104">Product Name</span></span>   |                                              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                               |
| <span data-ttu-id="08667-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="08667-105">Product Version</span></span> |                                                          [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                           |
|    <span data-ttu-id="08667-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="08667-106">Event ID</span></span>     |                                                                                       <span data-ttu-id="08667-107">0</span><span class="sxs-lookup"><span data-stu-id="08667-107">0</span></span>                                                                                       |
|  <span data-ttu-id="08667-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="08667-108">Event Source</span></span>   |                                                                                       <span data-ttu-id="08667-109">0</span><span class="sxs-lookup"><span data-stu-id="08667-109">0</span></span>                                                                                       |
|    <span data-ttu-id="08667-110">元件</span><span class="sxs-lookup"><span data-stu-id="08667-110">Component</span></span>    |                                                                                       <span data-ttu-id="08667-111">0</span><span class="sxs-lookup"><span data-stu-id="08667-111">0</span></span>                                                                                       |
|  <span data-ttu-id="08667-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="08667-112">Symbolic Name</span></span>  |                                                                                       <span data-ttu-id="08667-113">0</span><span class="sxs-lookup"><span data-stu-id="08667-113">0</span></span>                                                                                       |
|  <span data-ttu-id="08667-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="08667-114">Message Text</span></span>   | <span data-ttu-id="08667-115">協調流程沒有公用接收埠，在此 BizTalk 組件中。</span><span class="sxs-lookup"><span data-stu-id="08667-115">There are no orchestrations with public receive ports in this BizTalk assembly.</span></span> <span data-ttu-id="08667-116">按一下 [上一頁] 並指定包含具有公用的協調流程的 BizTalk 組件的接收埠</span><span class="sxs-lookup"><span data-stu-id="08667-116">Click back and specify a BizTalk assembly containing orchestrations with public receive ports</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="08667-117">說明</span><span class="sxs-lookup"><span data-stu-id="08667-117">Explanation</span></span>  
 <span data-ttu-id="08667-118">此錯誤表示選取的協調流程沒有公用連接埠。</span><span class="sxs-lookup"><span data-stu-id="08667-118">This error indicates the orchestration selected does not have a public port.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="08667-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="08667-119">User Action</span></span>  
 <span data-ttu-id="08667-120">您可以使用下列程序來設定公用連接埠。</span><span class="sxs-lookup"><span data-stu-id="08667-120">Use the following procedure to configure a public port.</span></span>  
  
#### <a name="to-configure-a-public-port"></a><span data-ttu-id="08667-121">若要設定的公用連接埠</span><span class="sxs-lookup"><span data-stu-id="08667-121">To configure a public port</span></span>  
  
1.  <span data-ttu-id="08667-122">尋找協調流程，並公開所需的接收埠。</span><span class="sxs-lookup"><span data-stu-id="08667-122">Locate the orchestration and make the desired receive port public.</span></span>  
  
    1.  <span data-ttu-id="08667-123">開啟連接埠組態精靈。</span><span class="sxs-lookup"><span data-stu-id="08667-123">Open the Port Configuration wizard.</span></span>  
  
    2.  <span data-ttu-id="08667-124">在 **選取連接埠類型**，變更**存取限制**從**內部**（預設） 加入**公用-沒有限制**。</span><span class="sxs-lookup"><span data-stu-id="08667-124">In **Select a Port Type**, change **Access Restrictions** from **Internal** (default) to **Public-no limits**.</span></span>  
  
2.  <span data-ttu-id="08667-125">重新編譯組件。</span><span class="sxs-lookup"><span data-stu-id="08667-125">Recompile the assembly.</span></span>  
  
     <span data-ttu-id="08667-126">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="08667-126">\- OR -</span></span>  
  
     <span data-ttu-id="08667-127">載入 BizTalk 組件具有公用接收埠。</span><span class="sxs-lookup"><span data-stu-id="08667-127">Load a BizTalk assembly with public receive ports.</span></span>