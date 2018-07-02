---
title: 步驟 8： 使用 BizTalk 對應工具建立對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, maps
- creating, maps
- maps, creating
- BizTalk Mapper
ms.assetid: 785426c7-5651-48be-b3f4-7f9d8051ba23
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1b9edeca21fe9967f816f05d2ceb12ffe5c5ded
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968455"
---
# <a name="step-8-create-a-map-with-biztalk-mapper"></a><span data-ttu-id="ba457-102">步驟 8： 使用 BizTalk 對應工具建立對應</span><span class="sxs-lookup"><span data-stu-id="ba457-102">Step 8: Create a Map with BizTalk Mapper</span></span>
<span data-ttu-id="ba457-103">在此步驟中，您可以使用 BizTalk 對應工具建立對應。</span><span class="sxs-lookup"><span data-stu-id="ba457-103">In this step, you use the BizTalk Mapper to create a map.</span></span> <span data-ttu-id="ba457-104">您可以建立將資料 （欄位） 相關聯的連結，使用此對應來補充要求文件的要求拒絕文件中的資料中。</span><span class="sxs-lookup"><span data-stu-id="ba457-104">You use this map to create links that associate the data (fields) in a replenishment request document to the data in a request denied document.</span></span>  
  
### <a name="to-create-a-map"></a><span data-ttu-id="ba457-105">若要建立對應</span><span class="sxs-lookup"><span data-stu-id="ba457-105">To create a map</span></span>  
  
1. <span data-ttu-id="ba457-106">在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7 專案**，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="ba457-106">In Solution Explorer, right-click **BTAHL7 Project**, point to **Add**, and then click **New Item**.</span></span>  
  
2. <span data-ttu-id="ba457-107">在**加入新項目**對話方塊中，於**類別**窗格中，按一下 **對應檔**。</span><span class="sxs-lookup"><span data-stu-id="ba457-107">In the **Add New Item** dialog box, in the **Categories** pane, click **Map Files**.</span></span>  
  
3. <span data-ttu-id="ba457-108">在 **名稱**欄位中，輸入**DoorbellMap**來命名對應，然後按一下**新增**啟動 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="ba457-108">In the **Name** field, type **DoorbellMap** to name the map, and then click **Add** to start BizTalk Mapper.</span></span>  
  
4. <span data-ttu-id="ba457-109">在 **來源結構描述** 窗格 （左側），按一下 **開啟來源結構描述**。</span><span class="sxs-lookup"><span data-stu-id="ba457-109">In the **Source Schema** pane (left side), click **Open Source Schema**.</span></span>  
  
5. <span data-ttu-id="ba457-110">在 BizTalk 型別選擇器 對話方塊中，依序展開**BTAHL7 專案**，展開**結構描述**，按一下  **BTAHL7_Project.Doorbell**，然後按一下 **確定**.</span><span class="sxs-lookup"><span data-stu-id="ba457-110">In the BizTalk Type Picker dialog box, expand **BTAHL7 Project**, expand **Schemas**, click **BTAHL7_Project.Doorbell**, and then click **OK**.</span></span>  
  
6. <span data-ttu-id="ba457-111">在 **目的結構描述** 窗格 （右側），按一下 **開啟目的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="ba457-111">In the **Destination Schema** pane (right side), click **Open Destination Schema**.</span></span>  
  
7. <span data-ttu-id="ba457-112">在 BizTalk 型別選擇器中，展開**BTAHL7 專案**，展開**結構描述**，按一下  **BTAHL7Schemas.ADT_A04_22_GLO_DEF**，然後按一下 **確定**.</span><span class="sxs-lookup"><span data-stu-id="ba457-112">In the BizTalk Type Picker, expand **BTAHL7 Project**, expand **Schemas**, click **BTAHL7Schemas.ADT_A04_22_GLO_DEF**, and then click **OK**.</span></span>  
  
8. <span data-ttu-id="ba457-113">在 **目的結構描述**窗格 （右側），依序展開**ADT_A04_22_GLO_DEF**，展開**PID_PatientIdentification**，展開**PID.5_PatientName**.</span><span class="sxs-lookup"><span data-stu-id="ba457-113">In the **Destination Schema** pane (right side), expand **ADT_A04_22_GLO_DEF**, expand **PID_PatientIdentification**, and expand **PID.5_PatientName**.</span></span>  
  
9. <span data-ttu-id="ba457-114">在 [**來源結構描述**] 窗格 （左側），展開**DoorbellRoot**。</span><span class="sxs-lookup"><span data-stu-id="ba457-114">In the **Source Schema** pane (left side), expand **DoorbellRoot**.</span></span> <span data-ttu-id="ba457-115">拖曳**LastName**欄位設為**PN_0_FamilyName**欄位中**目的結構描述**窗格。</span><span class="sxs-lookup"><span data-stu-id="ba457-115">Drag the **LastName** field to the **PN_0_FamilyName** field in the **Destination Schema** pane.</span></span>  
  
10. <span data-ttu-id="ba457-116">在 **來源結構描述**窗格拖曳到**FirstName**欄位**PN_1_GivenName**欄位中**目的結構描述**窗格。</span><span class="sxs-lookup"><span data-stu-id="ba457-116">In the **Source Schema** pane, drag the **FirstName** field to the **PN_1_GivenName** field in the **Destination Schema** pane.</span></span>  
  
11. <span data-ttu-id="ba457-117">在 **來源結構描述**窗格拖曳到**MiddleName**欄位**PN_2_MiddleInitialOrName**欄位中**目的結構描述**窗格.</span><span class="sxs-lookup"><span data-stu-id="ba457-117">In the **Source Schema** pane, drag the **MiddleName** field to the **PN_2_MiddleInitialOrName** field in the **Destination Schema** pane.</span></span>  
  
12. <span data-ttu-id="ba457-118">在 **目的結構描述**窗格中，展開**PID_3_PatientIdInternalId**。</span><span class="sxs-lookup"><span data-stu-id="ba457-118">In the **Destination Schema** pane, expand **PID_3_PatientIdInternalId**.</span></span>  
  
13. <span data-ttu-id="ba457-119">在 **來源結構描述**窗格拖曳到**SSN**欄位**CM_PAT_ID_0_PatientID**中**目的結構描述**窗格。</span><span class="sxs-lookup"><span data-stu-id="ba457-119">In the **Source Schema** pane, drag the **SSN** field to the **CM_PAT_ID_0_PatientID** in the **Destination Schema** pane.</span></span>  
  
14. <span data-ttu-id="ba457-120">在 **檔案**功能表上，按一下**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="ba457-120">In the **File** menu, click **Save All**.</span></span>  
  
    <span data-ttu-id="ba457-121">在一般訊息豐富 」 案例中，如果任何病患資訊遺失，那麼您會在您的協調流程呼叫以病患記錄資料庫和新增遺失的資訊，然後使用的其他資訊完成對應。</span><span class="sxs-lookup"><span data-stu-id="ba457-121">In a typical message enrichment scenario, if any patient information were missing, you would make a call to a Patient Records database in your orchestration and add the missing information, then use the additional information to complete the mapping.</span></span> <span data-ttu-id="ba457-122">比方說，您可能會擷取病患的住家地址病患記錄資料庫，因為輸入的 XML doorbell 觸發程序事件訊息未提供。</span><span class="sxs-lookup"><span data-stu-id="ba457-122">For example, you might retrieve the home address of a patient from the Patient Records database, since the inbound XML doorbell trigger event message did not provide it.</span></span>  
  
    <span data-ttu-id="ba457-123">請繼續進行[步驟 9： 驗證和建置對應專案](../../adapters-and-accelerators/accelerator-hl7/step-9-validate-and-build-the-map-project.md)。</span><span class="sxs-lookup"><span data-stu-id="ba457-123">Proceed to [Step 9: Validate and Build the Map Project](../../adapters-and-accelerators/accelerator-hl7/step-9-validate-and-build-the-map-project.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba457-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba457-124">See Also</span></span>  
 [<span data-ttu-id="ba457-125">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="ba457-125">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)