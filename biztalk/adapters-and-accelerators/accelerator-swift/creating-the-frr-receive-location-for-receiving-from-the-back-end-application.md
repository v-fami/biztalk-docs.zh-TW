---
title: 建立 FRR 接收位置接收來自後端應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive locations, creating
- creating, receive locations
- FRR, creating receive locations
ms.assetid: 78bd8084-ddec-4066-a474-ab5b1a0a849f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26ac72c9d122b626411e67cfc6e18f76de226415
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002855"
---
# <a name="creating-the-frr-receive-location-for-receiving-from-the-back-end-application"></a><span data-ttu-id="e1b9f-102">建立 FRR 接收位置接收來自後端應用程式</span><span class="sxs-lookup"><span data-stu-id="e1b9f-102">Creating the FRR Receive Location for Receiving from the Back-End Application</span></span>
<span data-ttu-id="e1b9f-103">若要執行 FIN 回應對帳，您必須建立接收位置從後端應用程式接收訊息[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e1b9f-103">To perform FIN Response Reconciliation, you need to create a receive location that receives a message from the back-end application into [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span></span>  

 <span data-ttu-id="e1b9f-104">**摘要**</span><span class="sxs-lookup"><span data-stu-id="e1b9f-104">**Summary**</span></span>  

 <span data-ttu-id="e1b9f-105">建立接收位置具有下列屬性和元件：</span><span class="sxs-lookup"><span data-stu-id="e1b9f-105">Create a receive location with the following properties and components:</span></span>  


| <span data-ttu-id="e1b9f-106">屬性/元件</span><span class="sxs-lookup"><span data-stu-id="e1b9f-106">Property/Component</span></span> |                                                                 <span data-ttu-id="e1b9f-107">設定</span><span class="sxs-lookup"><span data-stu-id="e1b9f-107">Setting</span></span>                                                                 |
|--------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
|    <span data-ttu-id="e1b9f-108">接收埠</span><span class="sxs-lookup"><span data-stu-id="e1b9f-108">Receive port</span></span>    |                                                              <span data-ttu-id="e1b9f-109">單向連接埠</span><span class="sxs-lookup"><span data-stu-id="e1b9f-109">One-way port</span></span>                                                               |
|   <span data-ttu-id="e1b9f-110">傳輸類型</span><span class="sxs-lookup"><span data-stu-id="e1b9f-110">Transport type</span></span>   |                                           <span data-ttu-id="e1b9f-111">後端應用程式所使用的傳輸類型</span><span class="sxs-lookup"><span data-stu-id="e1b9f-111">The transport type used by the back-end application</span></span>                                           |
|    <span data-ttu-id="e1b9f-112">位址 URI</span><span class="sxs-lookup"><span data-stu-id="e1b9f-112">Address URI</span></span>     |                                                   <span data-ttu-id="e1b9f-113">視需要傳輸類型</span><span class="sxs-lookup"><span data-stu-id="e1b9f-113">As required for the transport type</span></span>                                                    |
|  <span data-ttu-id="e1b9f-114">接收處理常式</span><span class="sxs-lookup"><span data-stu-id="e1b9f-114">Receive handler</span></span>   |                                                        <span data-ttu-id="e1b9f-115">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="e1b9f-115">BizTalkServerApplication</span></span>                                                         |
|  <span data-ttu-id="e1b9f-116">接收管線</span><span class="sxs-lookup"><span data-stu-id="e1b9f-116">Receive pipeline</span></span>  | <span data-ttu-id="e1b9f-117">[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收您為 FRR 建立的管線</span><span class="sxs-lookup"><span data-stu-id="e1b9f-117">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receive pipeline that you created for FRR</span></span> |

### <a name="to-add-an-frr-receive-location-for-receiving-from-the-back-end-application"></a><span data-ttu-id="e1b9f-118">若要新增的 FRR 接收位置接收來自後端應用程式</span><span class="sxs-lookup"><span data-stu-id="e1b9f-118">To add an FRR receive location for receiving from the back-end application</span></span>  

1. <span data-ttu-id="e1b9f-119">在 [BizTalk Server 管理主控台中，展開**BizTalk Server 管理]**， **BizTalk 群組**，**應用程式**，和**BizTalk 應用程式1**節點。</span><span class="sxs-lookup"><span data-stu-id="e1b9f-119">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and **BizTalk Application 1** nodes.</span></span>  

2. <span data-ttu-id="e1b9f-120">以滑鼠右鍵按一下**管線**，然後按一下**重新整理**。</span><span class="sxs-lookup"><span data-stu-id="e1b9f-120">Right-click **Pipelines**, and then click **Refresh**.</span></span>  

3. <span data-ttu-id="e1b9f-121">以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="e1b9f-121">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  

4. <span data-ttu-id="e1b9f-122">在接收埠屬性 對話方塊中，在**名稱**方塊中，輸入接收埠，例如 FRRBackEndReceivePort 的名稱。</span><span class="sxs-lookup"><span data-stu-id="e1b9f-122">In the Receive Port Properties dialog box, in the **Name** box, type a name for the receive port, such as FRRBackEndReceivePort.</span></span>  

5. <span data-ttu-id="e1b9f-123">按一下 **套用**要繫結連接埠，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="e1b9f-123">Click **Apply** to bind the port, and then click **OK**.</span></span>  

6. <span data-ttu-id="e1b9f-124">在管理主控台中，以滑鼠右鍵按一下**接收位置**，指向**新增**，然後按一下**單向接收位置**。</span><span class="sxs-lookup"><span data-stu-id="e1b9f-124">In the Administration Console, right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  

7. <span data-ttu-id="e1b9f-125">在 [選取接收埠] 對話方塊中，選取您剛才的接收埠建立，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="e1b9f-125">In the Select a Receive Port dialog box, select the receive port that you just created, and then click **OK**.</span></span>  

8. <span data-ttu-id="e1b9f-126">在 [接收位置屬性] 對話方塊中，在**名稱**方塊中，輸入接收位置的名稱。</span><span class="sxs-lookup"><span data-stu-id="e1b9f-126">In the Receive Location Properties dialog box, in the **Name** box, type a name for the receive location.</span></span>  

9. <span data-ttu-id="e1b9f-127">在 [**傳輸**] 區段中，如**類型**文字方塊中，選取後端應用程式使用的傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="e1b9f-127">In the **Transport** section, for the **Type** text box, select the transport type used by the back-end application.</span></span>  

10. <span data-ttu-id="e1b9f-128">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="e1b9f-128">Click **Configure**.</span></span>  

11. <span data-ttu-id="e1b9f-129">在 [FILE 傳輸屬性] 對話方塊中，填入所需的傳輸類型的屬性，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="e1b9f-129">In the FILE Transport Properties dialog box, fill in the properties required for the transport type, and then click **OK**.</span></span>  

12. <span data-ttu-id="e1b9f-130">在 [接收位置屬性] 對話方塊中，如**接收處理常式**，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="e1b9f-130">In the Receive Location Properties dialog box, for **Receive Handler**, select **BizTalkServerApplication**.</span></span>  

13. <span data-ttu-id="e1b9f-131">在 [接收位置屬性] 對話方塊中，如**接收管線**，選取[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收您為 FRR 建立的管線。</span><span class="sxs-lookup"><span data-stu-id="e1b9f-131">In the Receive Location Properties dialog box, for **Receive Pipeline**, select the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receive pipeline that you created for FRR.</span></span>  

14. <span data-ttu-id="e1b9f-132">按一下 [**套用**，然後按一下 **[確定]** 以關閉**接收位置屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e1b9f-132">Click **Apply**, and then click **OK** to close the **Receive Location Properties** dialog box.</span></span>  

15. <span data-ttu-id="e1b9f-133">在 [BizTalk 總管] 中，以滑鼠右鍵按一下您剛才的接收位置建立，，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="e1b9f-133">In BizTalk Explorer, right-click the receive location that you just created, and then click **Enable**.</span></span>
