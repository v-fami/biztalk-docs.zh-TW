---
title: 步驟 10： 建立協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, creating
- creating, orchestrations
- message enrichment tutorial, orchestrations
ms.assetid: 10f5cf3d-4a34-4c80-89d1-c390552cfc09
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfc554a6f3c94a077b34ae79a36b8e484eadcd5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206566"
---
# <a name="step-10-create-an-orchestration"></a><span data-ttu-id="16208-102">步驟 10： 建立協調流程</span><span class="sxs-lookup"><span data-stu-id="16208-102">Step 10: Create an Orchestration</span></span>
<span data-ttu-id="16208-103">在此步驟中，您可以使用 協調流程設計師建立協調流程代表商務程序來擷取完整填入 ADT_A04 訊息的其他病患詳細資料。</span><span class="sxs-lookup"><span data-stu-id="16208-103">In this step, you use Orchestration Designer to create an orchestration to represent the business process for retrieving additional patient details to fully populate an ADT_A04 message.</span></span> <span data-ttu-id="16208-104">使用協調流程設計師 」，您會選取協調流程圖形來表示此商務程序的動作。</span><span class="sxs-lookup"><span data-stu-id="16208-104">Using Orchestration Designer, you select the orchestration shapes required to represent actions for this business process.</span></span> <span data-ttu-id="16208-105">在更新版本的練習中，您可以提供其他資訊以設定圖形，讓它們可以正常運作。</span><span class="sxs-lookup"><span data-stu-id="16208-105">In later exercises, you provide additional information to configure the shapes so that they can function properly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16208-106">下列步驟中建立的協調流程只適用於本教學課程的內容中。</span><span class="sxs-lookup"><span data-stu-id="16208-106">The orchestration created in the following steps only works in the context of this tutorial.</span></span> <span data-ttu-id="16208-107">為了讓正常運作的協調流程，它需要的組件參考、 對應和其他成品，您建立同時使用本教學課程。</span><span class="sxs-lookup"><span data-stu-id="16208-107">In order for the orchestration to work correctly, it needs the assembly references, maps, and the other artifacts that you create while using this tutorial.</span></span>  
  
### <a name="to-create-an-orchestration"></a><span data-ttu-id="16208-108">建立協調流程</span><span class="sxs-lookup"><span data-stu-id="16208-108">To create an orchestration</span></span>  
  
1.  <span data-ttu-id="16208-109">在 方案總管 中，以滑鼠右鍵按一下**BTAHL7 專案**，指向 **新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="16208-109">In Solution Explorer, right-click **BTAHL7 Project**, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="16208-110">在**加入新項目**對話方塊中，於**類別**] 窗格中，按一下 [**協調流程檔案**。</span><span class="sxs-lookup"><span data-stu-id="16208-110">In the **Add New Item** dialog box, in the **Categories** pane, click **Orchestration Files**.</span></span>  
  
3.  <span data-ttu-id="16208-111">在**範本**] 窗格中，按一下 [ **BizTalk 協調流程**。</span><span class="sxs-lookup"><span data-stu-id="16208-111">In the **Templates** pane, click **BizTalk Orchestration**.</span></span>  
  
4.  <span data-ttu-id="16208-112">在**名稱**欄位中，輸入**Doorbell Orchestration.odx** (請注意單字之間沒有空格**Doorbell**和**協調流程**) 作為協調流程的名稱，然後按一下**新增**建立新的協調流程檔案。</span><span class="sxs-lookup"><span data-stu-id="16208-112">In the **Name** field, type **Doorbell Orchestration.odx** (note that there is a space between the word **Doorbell** and **Orchestration**) as the orchestration name, and then click **Add** to create a new orchestration file.</span></span>  
  
5.  <span data-ttu-id="16208-113">在**檢視**功能表上，按一下 **工具箱**。</span><span class="sxs-lookup"><span data-stu-id="16208-113">In the **View** menu, click **Toolbox**.</span></span>  
  
6.  <span data-ttu-id="16208-114">在**工具箱**窗格拖曳**接收**圖形至 [設計] 檢視介面並將它放在標示為區域**從 [工具箱] 拖曳圖形**。</span><span class="sxs-lookup"><span data-stu-id="16208-114">In the **Toolbox** pane, drag the **Receive** shape to the Design view surface and drop it on the area labeled **Drop a shape from the toolbox here**.</span></span>  
  
7.  <span data-ttu-id="16208-115">在 屬性 視窗 （在右下方的螢幕） 上，按一下 **名稱**屬性，並輸入**DoorbellReceive**做為名稱**接收**圖形，然後再按  **輸入**。</span><span class="sxs-lookup"><span data-stu-id="16208-115">In the Properties window (on the bottom right of your screen), click the **Name** property and type **DoorbellReceive** as the name of the **Receive** shape, and then press **Enter**.</span></span>  
  
8.  <span data-ttu-id="16208-116">在 [屬性] 視窗中，變更**Activate**屬性**True**。</span><span class="sxs-lookup"><span data-stu-id="16208-116">In the Properties window, change the **Activate** property to **True**.</span></span>  
  
9. <span data-ttu-id="16208-117">拖曳**轉換**圖形從 [工具箱]，並將它放在正下方**DoorbellReceive**圖形。</span><span class="sxs-lookup"><span data-stu-id="16208-117">Drag the **Transform** shape from the Toolbox and drop it directly below the **DoorbellReceive** shape.</span></span>  
  
10. <span data-ttu-id="16208-118">（在右下方的螢幕） 的 [屬性] 視窗中按一下**名稱**屬性來變更名稱**轉換**圖形至**DoorbellTransform**，然後按下**輸入**。</span><span class="sxs-lookup"><span data-stu-id="16208-118">In the Properties window (on the bottom right of your screen), click the **Name** property to change the name of the **Transform** shape to **DoorbellTransform**, and then press **Enter**.</span></span>  
  
11. <span data-ttu-id="16208-119">在**工具箱**窗格拖曳**訊息指派**圖形至 [設計] 檢視介面並將它放在正下方的區域上 **[constructmessage_1]** 圖形。</span><span class="sxs-lookup"><span data-stu-id="16208-119">In the **Toolbox** pane, drag the **Message Assignment** shape to the Design view surface and drop it on the area directly below the **ConstructMessage_1** shape.</span></span>  
  
12. <span data-ttu-id="16208-120">在 協調流程設計檢視介面中，按一下  **MessageAssignment_1**圖形，然後在**屬性** 窗格中，按一下 **名稱**，輸入新名稱**DoorbellFinalTransform**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="16208-120">In the orchestration Design view surface, click the **MessageAssignment_1** shape, and in the **Properties** pane, click **Name** and type the new name **DoorbellFinalTransform**, and then press **Enter**.</span></span>  
  
13. <span data-ttu-id="16208-121">拖曳**傳送**圖形從 [工具箱]，並放在正下方的連接線**DoorbellFinalTransform**圖形。</span><span class="sxs-lookup"><span data-stu-id="16208-121">Drag the **Send** shape from the Toolbox and drop it on the connecting line directly below the **DoorbellFinalTransform** shape.</span></span>  
  
14. <span data-ttu-id="16208-122">在 屬性 視窗 （在右下方的螢幕） 上，按一下 **名稱**屬性來變更名稱**傳送**圖形至**DoorbellSend**，然後按  **輸入**。</span><span class="sxs-lookup"><span data-stu-id="16208-122">In the Properties window (on the bottom right of your screen), click the **Name** property to change the name of the **Send** shape to **DoorbellSend**, and then press **Enter**.</span></span>  
  
 <span data-ttu-id="16208-123">若要繼續[步驟 11： 建立協調流程變數](../../adapters-and-accelerators/accelerator-hl7/step-11-create-orchestration-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="16208-123">Proceed to [Step 11: Create Orchestration Variables](../../adapters-and-accelerators/accelerator-hl7/step-11-create-orchestration-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16208-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16208-124">See Also</span></span>  
 [<span data-ttu-id="16208-125">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="16208-125">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)