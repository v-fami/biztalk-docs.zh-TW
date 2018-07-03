---
title: 步驟 10： 建立協調流程 |Microsoft Docs
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
ms.openlocfilehash: e896b5a5723b84cfc94d735aa51b8bee848b41b9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989775"
---
# <a name="step-10-create-an-orchestration"></a><span data-ttu-id="daf6e-102">步驟 10： 建立協調流程</span><span class="sxs-lookup"><span data-stu-id="daf6e-102">Step 10: Create an Orchestration</span></span>
<span data-ttu-id="daf6e-103">在此步驟中，您可以使用 協調流程設計師建立協調流程代表商務程序來擷取其他的病患詳細資料，以完全填入 ADT_A04 訊息。</span><span class="sxs-lookup"><span data-stu-id="daf6e-103">In this step, you use Orchestration Designer to create an orchestration to represent the business process for retrieving additional patient details to fully populate an ADT_A04 message.</span></span> <span data-ttu-id="daf6e-104">使用協調流程設計師 」，選取表示此商務程序的動作所需的協調流程圖形。</span><span class="sxs-lookup"><span data-stu-id="daf6e-104">Using Orchestration Designer, you select the orchestration shapes required to represent actions for this business process.</span></span> <span data-ttu-id="daf6e-105">在更新版本的練習中，您可以提供其他的資訊，來設定圖形，以便它們可以正確運作。</span><span class="sxs-lookup"><span data-stu-id="daf6e-105">In later exercises, you provide additional information to configure the shapes so that they can function properly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="daf6e-106">在下列步驟中建立的協調流程僅適用於本教學課程的內容中。</span><span class="sxs-lookup"><span data-stu-id="daf6e-106">The orchestration created in the following steps only works in the context of this tutorial.</span></span> <span data-ttu-id="daf6e-107">為了讓協調流程才能正常運作，它需要的組件參考、 對應和您在使用本教學課程時所建立的成品。</span><span class="sxs-lookup"><span data-stu-id="daf6e-107">In order for the orchestration to work correctly, it needs the assembly references, maps, and the other artifacts that you create while using this tutorial.</span></span>  
  
### <a name="to-create-an-orchestration"></a><span data-ttu-id="daf6e-108">建立協調流程</span><span class="sxs-lookup"><span data-stu-id="daf6e-108">To create an orchestration</span></span>  
  
1. <span data-ttu-id="daf6e-109">在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7 專案**，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="daf6e-109">In Solution Explorer, right-click **BTAHL7 Project**, point to **Add**, and then click **New Item**.</span></span>  
  
2. <span data-ttu-id="daf6e-110">在 **加入新項目**對話方塊的 **類別**窗格中，按一下**協調流程檔案**。</span><span class="sxs-lookup"><span data-stu-id="daf6e-110">In the **Add New Item** dialog box, in the **Categories** pane, click **Orchestration Files**.</span></span>  
  
3. <span data-ttu-id="daf6e-111">在 **範本**窗格中，按一下**BizTalk 協調流程**。</span><span class="sxs-lookup"><span data-stu-id="daf6e-111">In the **Templates** pane, click **BizTalk Orchestration**.</span></span>  
  
4. <span data-ttu-id="daf6e-112">在 **名稱**欄位中，輸入**Doorbell Orchestration.odx** (請注意這個字之間沒有空格**Doorbell**並**協調流程**) 作為協調流程的名稱，然後按一下**新增**以建立新的協調流程檔案。</span><span class="sxs-lookup"><span data-stu-id="daf6e-112">In the **Name** field, type **Doorbell Orchestration.odx** (note that there is a space between the word **Doorbell** and **Orchestration**) as the orchestration name, and then click **Add** to create a new orchestration file.</span></span>  
  
5. <span data-ttu-id="daf6e-113">在 **檢視**功能表上，按一下**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="daf6e-113">In the **View** menu, click **Toolbox**.</span></span>  
  
6. <span data-ttu-id="daf6e-114">在 **工具箱**窗格拖曳到**接收**圖形至 設計 檢視介面並將它放在標示為區域上**從 工具箱 拖曳圖形**。</span><span class="sxs-lookup"><span data-stu-id="daf6e-114">In the **Toolbox** pane, drag the **Receive** shape to the Design view surface and drop it on the area labeled **Drop a shape from the toolbox here**.</span></span>  
  
7. <span data-ttu-id="daf6e-115">在 屬性 視窗 （在右下方的螢幕） 上，按一下**名稱**屬性，並輸入**DoorbellReceive**同名**接收**圖形，然後再按  **輸入**。</span><span class="sxs-lookup"><span data-stu-id="daf6e-115">In the Properties window (on the bottom right of your screen), click the **Name** property and type **DoorbellReceive** as the name of the **Receive** shape, and then press **Enter**.</span></span>  
  
8. <span data-ttu-id="daf6e-116">在 [屬性] 視窗中，變更**Activate**屬性設 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="daf6e-116">In the Properties window, change the **Activate** property to **True**.</span></span>  
  
9. <span data-ttu-id="daf6e-117">拖曳**轉換**圖形從 [工具箱]，並把它放在正下方**DoorbellReceive**圖形。</span><span class="sxs-lookup"><span data-stu-id="daf6e-117">Drag the **Transform** shape from the Toolbox and drop it directly below the **DoorbellReceive** shape.</span></span>  
  
10. <span data-ttu-id="daf6e-118">在 屬性 視窗 （在右下方的螢幕） 上，按一下 **名稱**屬性來變更名稱**轉換**圖形至**DoorbellTransform**，然後按下**輸入**。</span><span class="sxs-lookup"><span data-stu-id="daf6e-118">In the Properties window (on the bottom right of your screen), click the **Name** property to change the name of the **Transform** shape to **DoorbellTransform**, and then press **Enter**.</span></span>  
  
11. <span data-ttu-id="daf6e-119">在 **工具箱**窗格拖曳到**訊息指派**圖形至 設計 檢視介面並將它放在正下方的區域**constructmessage_1**圖形。</span><span class="sxs-lookup"><span data-stu-id="daf6e-119">In the **Toolbox** pane, drag the **Message Assignment** shape to the Design view surface and drop it on the area directly below the **ConstructMessage_1** shape.</span></span>  
  
12. <span data-ttu-id="daf6e-120">在 協調流程設計檢視 介面中，按一下  **MessageAssignment_1**圖形，然後在**屬性**窗格中，按一下 **名稱**，輸入新名稱**DoorbellFinalTransform**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="daf6e-120">In the orchestration Design view surface, click the **MessageAssignment_1** shape, and in the **Properties** pane, click **Name** and type the new name **DoorbellFinalTransform**, and then press **Enter**.</span></span>  
  
13. <span data-ttu-id="daf6e-121">拖曳**傳送**圖形從 [工具箱]，並放在正下方的連接線**DoorbellFinalTransform**圖形。</span><span class="sxs-lookup"><span data-stu-id="daf6e-121">Drag the **Send** shape from the Toolbox and drop it on the connecting line directly below the **DoorbellFinalTransform** shape.</span></span>  
  
14. <span data-ttu-id="daf6e-122">在 屬性 視窗 （在右下方的螢幕） 上，按一下 **名稱**屬性來變更名稱**傳送**圖形至**DoorbellSend**，然後按  **輸入**。</span><span class="sxs-lookup"><span data-stu-id="daf6e-122">In the Properties window (on the bottom right of your screen), click the **Name** property to change the name of the **Send** shape to **DoorbellSend**, and then press **Enter**.</span></span>  
  
    <span data-ttu-id="daf6e-123">請繼續進行[步驟 11： 建立協調流程變數](../../adapters-and-accelerators/accelerator-hl7/step-11-create-orchestration-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="daf6e-123">Proceed to [Step 11: Create Orchestration Variables](../../adapters-and-accelerators/accelerator-hl7/step-11-create-orchestration-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daf6e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="daf6e-124">See Also</span></span>  
 [<span data-ttu-id="daf6e-125">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="daf6e-125">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)