---
title: "建立 FRR 接收位置從後端應用程式接收 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, creating
- creating, receive locations
- FRR, creating receive locations
ms.assetid: 78bd8084-ddec-4066-a474-ab5b1a0a849f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46895ff64e6585c8b80979c09874dffb510cf049
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-the-frr-receive-location-for-receiving-from-the-back-end-application"></a><span data-ttu-id="6426a-102">建立 FRR 接收位置從後端應用程式接收</span><span class="sxs-lookup"><span data-stu-id="6426a-102">Creating the FRR Receive Location for Receiving from the Back-End Application</span></span>
<span data-ttu-id="6426a-103">若要執行 FIN 回應重新調整，您必須建立接收位置從後端應用程式進入接收之訊息[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6426a-103">To perform FIN Response Reconciliation, you need to create a receive location that receives a message from the back-end application into [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span></span>  
  
 <span data-ttu-id="6426a-104">**摘要**</span><span class="sxs-lookup"><span data-stu-id="6426a-104">**Summary**</span></span>  
  
 <span data-ttu-id="6426a-105">建立具有下列屬性和元件的接收位置：</span><span class="sxs-lookup"><span data-stu-id="6426a-105">Create a receive location with the following properties and components:</span></span>  
  
|<span data-ttu-id="6426a-106">屬性/元件</span><span class="sxs-lookup"><span data-stu-id="6426a-106">Property/Component</span></span>|<span data-ttu-id="6426a-107">設定</span><span class="sxs-lookup"><span data-stu-id="6426a-107">Setting</span></span>|  
|-------------------------|-------------|  
|<span data-ttu-id="6426a-108">接收埠</span><span class="sxs-lookup"><span data-stu-id="6426a-108">Receive port</span></span>|<span data-ttu-id="6426a-109">單向連接埠</span><span class="sxs-lookup"><span data-stu-id="6426a-109">One-way port</span></span>|  
|<span data-ttu-id="6426a-110">傳輸類型</span><span class="sxs-lookup"><span data-stu-id="6426a-110">Transport type</span></span>|<span data-ttu-id="6426a-111">後端應用程式所使用的傳輸類型</span><span class="sxs-lookup"><span data-stu-id="6426a-111">The transport type used by the back-end application</span></span>|  
|<span data-ttu-id="6426a-112">位址的 URI</span><span class="sxs-lookup"><span data-stu-id="6426a-112">Address URI</span></span>|<span data-ttu-id="6426a-113">傳輸類型的必要項</span><span class="sxs-lookup"><span data-stu-id="6426a-113">As required for the transport type</span></span>|  
|<span data-ttu-id="6426a-114">接收處理常式</span><span class="sxs-lookup"><span data-stu-id="6426a-114">Receive handler</span></span>|<span data-ttu-id="6426a-115">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="6426a-115">BizTalkServerApplication</span></span>|  
|<span data-ttu-id="6426a-116">接收管線</span><span class="sxs-lookup"><span data-stu-id="6426a-116">Receive pipeline</span></span>|<span data-ttu-id="6426a-117">[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收管線所建立的 FRR</span><span class="sxs-lookup"><span data-stu-id="6426a-117">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receive pipeline that you created for FRR</span></span>|  
  
### <a name="to-add-an-frr-receive-location-for-receiving-from-the-back-end-application"></a><span data-ttu-id="6426a-118">若要加入 FRR 接收接收位置從後端應用程式</span><span class="sxs-lookup"><span data-stu-id="6426a-118">To add an FRR receive location for receiving from the back-end application</span></span>  
  
1.  <span data-ttu-id="6426a-119">在 BizTalk Server 管理主控台中，展開**BizTalk Server 管理**， **BizTalk 群組**，**應用程式**，和**BizTalk 應用程式1**節點。</span><span class="sxs-lookup"><span data-stu-id="6426a-119">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and **BizTalk Application 1** nodes.</span></span>  
  
2.  <span data-ttu-id="6426a-120">以滑鼠右鍵按一下**管線**，然後按一下 **重新整理**。</span><span class="sxs-lookup"><span data-stu-id="6426a-120">Right-click **Pipelines**, and then click **Refresh**.</span></span>  
  
3.  <span data-ttu-id="6426a-121">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="6426a-121">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
4.  <span data-ttu-id="6426a-122">在 [接收埠屬性] 對話方塊中**名稱**方塊中，輸入接收埠，例如 FRRBackEndReceivePort 的名稱。</span><span class="sxs-lookup"><span data-stu-id="6426a-122">In the Receive Port Properties dialog box, in the **Name** box, type a name for the receive port, such as FRRBackEndReceivePort.</span></span>  
  
5.  <span data-ttu-id="6426a-123">按一下**套用**來繫結連接埠，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="6426a-123">Click **Apply** to bind the port, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="6426a-124">在管理主控台中，以滑鼠右鍵按一下**接收位置**，指向 **新增**，然後按一下 **單向接收位置**。</span><span class="sxs-lookup"><span data-stu-id="6426a-124">In the Administration Console, right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
7.  <span data-ttu-id="6426a-125">在 [選取接收埠] 對話方塊中，選取您剛才的接收埠建立，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="6426a-125">In the Select a Receive Port dialog box, select the receive port that you just created, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="6426a-126">在 [接收位置屬性] 對話方塊中**名稱**方塊中，輸入接收位置的名稱。</span><span class="sxs-lookup"><span data-stu-id="6426a-126">In the Receive Location Properties dialog box, in the **Name** box, type a name for the receive location.</span></span>  
  
9. <span data-ttu-id="6426a-127">在**傳輸** 區段中，針對**類型**文字方塊中，選取由後端應用程式使用的傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="6426a-127">In the **Transport** section, for the **Type** text box, select the transport type used by the back-end application.</span></span>  
  
10. <span data-ttu-id="6426a-128">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="6426a-128">Click **Configure**.</span></span>  
  
11. <span data-ttu-id="6426a-129">在 FILE 傳輸屬性 對話方塊中，填入所需的傳輸類型的屬性，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6426a-129">In the FILE Transport Properties dialog box, fill in the properties required for the transport type, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="6426a-130">在 [接收位置屬性] 對話方塊的**接收處理常式**，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="6426a-130">In the Receive Location Properties dialog box, for **Receive Handler**, select **BizTalkServerApplication**.</span></span>  
  
13. <span data-ttu-id="6426a-131">在 [接收位置屬性] 對話方塊的**接收管線**，選取[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收管線 FRR 所建立。</span><span class="sxs-lookup"><span data-stu-id="6426a-131">In the Receive Location Properties dialog box, for **Receive Pipeline**, select the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receive pipeline that you created for FRR.</span></span>  
  
14. <span data-ttu-id="6426a-132">按一下**套用**，然後按一下 [**確定**關閉**接收位置屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6426a-132">Click **Apply**, and then click **OK** to close the **Receive Location Properties** dialog box.</span></span>  
  
15. <span data-ttu-id="6426a-133">在 [BizTalk 總管] 中，以滑鼠右鍵按一下您剛才的接收位置建立，，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="6426a-133">In BizTalk Explorer, right-click the receive location that you just created, and then click **Enable**.</span></span>