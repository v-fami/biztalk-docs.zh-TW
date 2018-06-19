---
title: 結構描述匯入到 BizTalk Server Projects1 |Microsoft 文件
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
ms.openlocfilehash: 719679dffa5bcffdeddcbcd889f847f147a705b4
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015445"
---
# <a name="importing-schemas-into-biztalk-server-projects"></a><span data-ttu-id="5d548-102">結構描述匯入至 BizTalk Server 專案</span><span class="sxs-lookup"><span data-stu-id="5d548-102">Importing Schemas into BizTalk Server Projects</span></span>
<span data-ttu-id="5d548-103">下列資訊說明如何將結構描述匯入至 BizTalk Server 專案。</span><span class="sxs-lookup"><span data-stu-id="5d548-103">The following information describes how to import schemas into a BizTalk Server project.</span></span>  
  
## <a name="importing-schemas"></a><span data-ttu-id="5d548-104">匯入結構描述</span><span class="sxs-lookup"><span data-stu-id="5d548-104">Importing Schemas</span></span>  
  
#### <a name="to-import-schemas"></a><span data-ttu-id="5d548-105">若要匯入結構描述</span><span class="sxs-lookup"><span data-stu-id="5d548-105">To import schemas</span></span>  
  
1.  <span data-ttu-id="5d548-106">在 [方案總管] 中，以滑鼠右鍵按一下專案，指向**新增**，然後選取**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="5d548-106">In Solution Explorer, right-click the project, point to **Add**, and select **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="5d548-107">按一下**新增配接器**，然後選取**開啟**。</span><span class="sxs-lookup"><span data-stu-id="5d548-107">Click **Add adapter**, and then select **Open**.</span></span>  
  
3.  <span data-ttu-id="5d548-108">選取的介面卡 **，J.D.Edwards OneWorld XE**。</span><span class="sxs-lookup"><span data-stu-id="5d548-108">Select the adapter **, J.D. Edwards OneWorld XE**.</span></span>  
  
4.  <span data-ttu-id="5d548-109">在下拉式清單中，選取 連接埠**SSOSendToJD Edwards OneWorld XE**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="5d548-109">In the drop-down list, select the port **SSOSendToJD Edwards OneWorld XE**, and then click **Next**.</span></span>  
  
     <span data-ttu-id="5d548-110">MyJ.D。</span><span class="sxs-lookup"><span data-stu-id="5d548-110">The myJ.D.</span></span> <span data-ttu-id="5d548-111">Edwards OneWorld XESSO 邏輯系統隨即出現在瀏覽器中 （這個邏輯系統使用 SSOSendToJ.D 建立。</span><span class="sxs-lookup"><span data-stu-id="5d548-111">Edwards OneWorld XESSO logical system appears in the browser (this logical system was created with the SSOSendToJ.D.</span></span> <span data-ttu-id="5d548-112">Edwards OneWorld XE 連接埠）。</span><span class="sxs-lookup"><span data-stu-id="5d548-112">Edwards OneWorld XE port).</span></span>  
  
5.  <span data-ttu-id="5d548-113">展開**myJ.D。Edwards OneWorld XESSO**。</span><span class="sxs-lookup"><span data-stu-id="5d548-113">Expand **myJ.D. Edwards OneWorld XESSO**.</span></span>  
  
6.  <span data-ttu-id="5d548-114">按一下箭頭圖示來移動項目 （或直接拖曳） 到**傳輸**視窗中，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="5d548-114">Click the arrow icon to move the item (or simply drag it) into the **Transmit** window, and then click **OK**.</span></span>  
  
     <span data-ttu-id="5d548-115">結構描述隨即加入至 SSOSchedule 專案。</span><span class="sxs-lookup"><span data-stu-id="5d548-115">The schemas are added to the SSOSchedule project.</span></span>  
  
7.  <span data-ttu-id="5d548-116">在 [方案總管] 中，展開**SSOSchedule 專案**。</span><span class="sxs-lookup"><span data-stu-id="5d548-116">In Solution Explorer, expand **SSOSchedule project**.</span></span>  
  
8.  <span data-ttu-id="5d548-117">以滑鼠右鍵按一下**BizTalk orchestration.odx**，然後按一下 **刪除**。</span><span class="sxs-lookup"><span data-stu-id="5d548-117">Right-click **BizTalk orchestration.odx**, and then click **Delete**.</span></span>  
  
9. <span data-ttu-id="5d548-118">在 [方案總管] 中，按兩下 **[getlist.odx]** 檢查協調流程。</span><span class="sxs-lookup"><span data-stu-id="5d548-118">In Solution Explorer, double-click **GetList.odx** to inspect the orchestration.</span></span>  
  
## <a name="orchestration-types---port-types"></a><span data-ttu-id="5d548-119">協調流程類型 - 連接埠類型</span><span class="sxs-lookup"><span data-stu-id="5d548-119">Orchestration Types - Port Types</span></span>  
  
-   <span data-ttu-id="5d548-120">**PortTypeIn/中/要求：** SSOSchedule.myJ.D。</span><span class="sxs-lookup"><span data-stu-id="5d548-120">**PortTypeIn/In/Request:** SSOSchedule.myJ.D.</span></span> <span data-ttu-id="5d548-121">Edwards OneWorld XEsso_transmitService_3.method</span><span class="sxs-lookup"><span data-stu-id="5d548-121">Edwards OneWorld XEsso_transmitService_3.method</span></span>  
  
-   <span data-ttu-id="5d548-122">**PortTypeOut/Out/回應：** SSOSchedule.myJ.D。</span><span class="sxs-lookup"><span data-stu-id="5d548-122">**PortTypeOut/Out/response:** SSOSchedule.myJ.D.</span></span> <span data-ttu-id="5d548-123">Edwards OneWorld XE sso_transmitService_3.methodResponse</span><span class="sxs-lookup"><span data-stu-id="5d548-123">Edwards OneWorld XE sso_transmitService_3.methodResponse</span></span>  
  
-   <span data-ttu-id="5d548-124">**PortTypeInOut/InOut/要求：** SSOSchedule.myJ.D。</span><span class="sxs-lookup"><span data-stu-id="5d548-124">**PortTypeInOut/InOut/Request:** SSOSchedule.myJ.D.</span></span> <span data-ttu-id="5d548-125">Edwards OneWorld XEsso_transmitService_3.method</span><span class="sxs-lookup"><span data-stu-id="5d548-125">Edwards OneWorld XEsso_transmitService_3.method</span></span>  
  
-   <span data-ttu-id="5d548-126">**PortTypeInOut/InOut/回應：** SSOSchedule.myJ.D。</span><span class="sxs-lookup"><span data-stu-id="5d548-126">**PortTypeInOut/InOut/Response:** SSOSchedule.myJ.D.</span></span> <span data-ttu-id="5d548-127">Edwards OneWorld XE sso_transmitService_3.methodResponse</span><span class="sxs-lookup"><span data-stu-id="5d548-127">Edwards OneWorld XE sso_transmitService_3.methodResponse</span></span>  
  
## <a name="orchestration-variables---messages"></a><span data-ttu-id="5d548-128">協調流程變數 - 訊息</span><span class="sxs-lookup"><span data-stu-id="5d548-128">Orchestration Variables - Messages</span></span>  
  
-   <span data-ttu-id="5d548-129">**MessageIn:** SSOSchedule.myJ.D。</span><span class="sxs-lookup"><span data-stu-id="5d548-129">**MessageIn:** SSOSchedule.myJ.D.</span></span> <span data-ttu-id="5d548-130">Edwards OneWorld XEsso_transmitService_3.method</span><span class="sxs-lookup"><span data-stu-id="5d548-130">Edwards OneWorld XEsso_transmitService_3.method</span></span>  
  
-   <span data-ttu-id="5d548-131">**MessageOut:** SSOSchedule.myJ.D。</span><span class="sxs-lookup"><span data-stu-id="5d548-131">**MessageOut:** SSOSchedule.myJ.D.</span></span> <span data-ttu-id="5d548-132">Edwards OneWorld XE sso_transmitService_3.methodResponse</span><span class="sxs-lookup"><span data-stu-id="5d548-132">Edwards OneWorld XE sso_transmitService_3.methodResponse</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d548-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d548-133">See Also</span></span>  
 [<span data-ttu-id="5d548-134">在配接器的安全性</span><span class="sxs-lookup"><span data-stu-id="5d548-134">Security in the adapter</span></span>](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)