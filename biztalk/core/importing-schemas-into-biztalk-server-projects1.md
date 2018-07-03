---
title: 結構描述匯入到 BizTalk Server Projects1 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- importing schemas
- orchestration variables, messages
- schemas, importing into BizTalk Server
- orchestration types, port types
ms.assetid: fa640195-a735-4201-a893-48f3405ddcb5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70eff140259cd7cf815e8e05125f9ade78bf5493
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982359"
---
# <a name="importing-schemas-into-biztalk-server-projects"></a><span data-ttu-id="87ede-102">結構描述匯入至 BizTalk Server 專案</span><span class="sxs-lookup"><span data-stu-id="87ede-102">Importing Schemas into BizTalk Server Projects</span></span>
<span data-ttu-id="87ede-103">下列資訊說明如何將結構描述匯入至 BizTalk Server 專案。</span><span class="sxs-lookup"><span data-stu-id="87ede-103">The following information describes how to import schemas into a BizTalk Server project.</span></span>  
  
## <a name="importing-schemas"></a><span data-ttu-id="87ede-104">匯入結構描述</span><span class="sxs-lookup"><span data-stu-id="87ede-104">Importing Schemas</span></span>  
  
#### <a name="to-import-schemas"></a><span data-ttu-id="87ede-105">若要匯入結構描述</span><span class="sxs-lookup"><span data-stu-id="87ede-105">To import schemas</span></span>  
  
1. <span data-ttu-id="87ede-106">在 [方案總管] 中，以滑鼠右鍵按一下專案，指向**新增**，然後選取**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="87ede-106">In Solution Explorer, right-click the project, point to **Add**, and select **Add Generated Items**.</span></span>  
  
2. <span data-ttu-id="87ede-107">按一下 **新增配接器**，然後選取**開啟**。</span><span class="sxs-lookup"><span data-stu-id="87ede-107">Click **Add adapter**, and then select **Open**.</span></span>  
  
3. <span data-ttu-id="87ede-108">選取配接器<strong>，J.D.Edwards OneWorld XE</strong>。</span><span class="sxs-lookup"><span data-stu-id="87ede-108">Select the adapter<strong>, J.D. Edwards OneWorld XE</strong>.</span></span>  
  
4. <span data-ttu-id="87ede-109">在下拉式清單中，選取 連接埠**SSOSendToJD Edwards OneWorld XE**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="87ede-109">In the drop-down list, select the port **SSOSendToJD Edwards OneWorld XE**, and then click **Next**.</span></span>  
  
    <span data-ttu-id="87ede-110">MyJ.D。</span><span class="sxs-lookup"><span data-stu-id="87ede-110">The myJ.D.</span></span> <span data-ttu-id="87ede-111">Edwards OneWorld XESSO 邏輯系統隨即出現在瀏覽器中 （這個邏輯系統使用 SSOSendToJ.D 建立。</span><span class="sxs-lookup"><span data-stu-id="87ede-111">Edwards OneWorld XESSO logical system appears in the browser (this logical system was created with the SSOSendToJ.D.</span></span> <span data-ttu-id="87ede-112">Edwards OneWorld XE 連接埠）。</span><span class="sxs-lookup"><span data-stu-id="87ede-112">Edwards OneWorld XE port).</span></span>  
  
5. <span data-ttu-id="87ede-113">展開**myJ.D。Edwards OneWorld XESSO**。</span><span class="sxs-lookup"><span data-stu-id="87ede-113">Expand **myJ.D. Edwards OneWorld XESSO**.</span></span>  
  
6. <span data-ttu-id="87ede-114">按一下箭頭圖示來移動項目 （或直接拖曳） 以進入**傳輸**視窗中，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="87ede-114">Click the arrow icon to move the item (or simply drag it) into the **Transmit** window, and then click **OK**.</span></span>  
  
    <span data-ttu-id="87ede-115">結構描述隨即加入至 SSOSchedule 專案。</span><span class="sxs-lookup"><span data-stu-id="87ede-115">The schemas are added to the SSOSchedule project.</span></span>  
  
7. <span data-ttu-id="87ede-116">在 [方案總管] 中，展開**SSOSchedule 專案**。</span><span class="sxs-lookup"><span data-stu-id="87ede-116">In Solution Explorer, expand **SSOSchedule project**.</span></span>  
  
8. <span data-ttu-id="87ede-117">以滑鼠右鍵按一下**BizTalk orchestration.odx**，然後按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="87ede-117">Right-click **BizTalk orchestration.odx**, and then click **Delete**.</span></span>  
  
9. <span data-ttu-id="87ede-118">在 [方案總管] 中，按兩下 **[getlist.odx]** 來檢查協調流程。</span><span class="sxs-lookup"><span data-stu-id="87ede-118">In Solution Explorer, double-click **GetList.odx** to inspect the orchestration.</span></span>  
  
## <a name="orchestration-types---port-types"></a><span data-ttu-id="87ede-119">協調流程類型 - 連接埠類型</span><span class="sxs-lookup"><span data-stu-id="87ede-119">Orchestration Types - Port Types</span></span>  
  
-   <span data-ttu-id="87ede-120">**PortTypeIn/中/要求：** SSOSchedule.myJ.D。</span><span class="sxs-lookup"><span data-stu-id="87ede-120">**PortTypeIn/In/Request:** SSOSchedule.myJ.D.</span></span> <span data-ttu-id="87ede-121">Edwards OneWorld XEsso_transmitService_3.method</span><span class="sxs-lookup"><span data-stu-id="87ede-121">Edwards OneWorld XEsso_transmitService_3.method</span></span>  
  
-   <span data-ttu-id="87ede-122">**PortTypeOut/Out/回應：** SSOSchedule.myJ.D。</span><span class="sxs-lookup"><span data-stu-id="87ede-122">**PortTypeOut/Out/response:** SSOSchedule.myJ.D.</span></span> <span data-ttu-id="87ede-123">Edwards OneWorld XE sso_transmitService_3.methodResponse</span><span class="sxs-lookup"><span data-stu-id="87ede-123">Edwards OneWorld XE sso_transmitService_3.methodResponse</span></span>  
  
-   <span data-ttu-id="87ede-124">**PortTypeInOut/InOut/要求：** SSOSchedule.myJ.D。</span><span class="sxs-lookup"><span data-stu-id="87ede-124">**PortTypeInOut/InOut/Request:** SSOSchedule.myJ.D.</span></span> <span data-ttu-id="87ede-125">Edwards OneWorld XEsso_transmitService_3.method</span><span class="sxs-lookup"><span data-stu-id="87ede-125">Edwards OneWorld XEsso_transmitService_3.method</span></span>  
  
-   <span data-ttu-id="87ede-126">**PortTypeInOut/InOut/回應：** SSOSchedule.myJ.D。</span><span class="sxs-lookup"><span data-stu-id="87ede-126">**PortTypeInOut/InOut/Response:** SSOSchedule.myJ.D.</span></span> <span data-ttu-id="87ede-127">Edwards OneWorld XE sso_transmitService_3.methodResponse</span><span class="sxs-lookup"><span data-stu-id="87ede-127">Edwards OneWorld XE sso_transmitService_3.methodResponse</span></span>  
  
## <a name="orchestration-variables---messages"></a><span data-ttu-id="87ede-128">協調流程變數 - 訊息</span><span class="sxs-lookup"><span data-stu-id="87ede-128">Orchestration Variables - Messages</span></span>  
  
-   <span data-ttu-id="87ede-129">**MessageIn:** SSOSchedule.myJ.D。</span><span class="sxs-lookup"><span data-stu-id="87ede-129">**MessageIn:** SSOSchedule.myJ.D.</span></span> <span data-ttu-id="87ede-130">Edwards OneWorld XEsso_transmitService_3.method</span><span class="sxs-lookup"><span data-stu-id="87ede-130">Edwards OneWorld XEsso_transmitService_3.method</span></span>  
  
-   <span data-ttu-id="87ede-131">**MessageOut:** SSOSchedule.myJ.D。</span><span class="sxs-lookup"><span data-stu-id="87ede-131">**MessageOut:** SSOSchedule.myJ.D.</span></span> <span data-ttu-id="87ede-132">Edwards OneWorld XE sso_transmitService_3.methodResponse</span><span class="sxs-lookup"><span data-stu-id="87ede-132">Edwards OneWorld XE sso_transmitService_3.methodResponse</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87ede-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87ede-133">See Also</span></span>  
 [<span data-ttu-id="87ede-134">配接器中的安全性</span><span class="sxs-lookup"><span data-stu-id="87ede-134">Security in the adapter</span></span>](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)