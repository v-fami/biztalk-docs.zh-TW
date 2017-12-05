---
title: "步驟 2： 建立新的專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, projects
- projects, creating
- message enrichment tutorial, projects
ms.assetid: 6e994845-53b8-4de8-a64f-32d36f7b5412
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4b296b01179b3ce52aef41dc246dbed2588c3e6
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="step-2-create-a-new-project"></a><span data-ttu-id="0eb48-102">步驟 2： 建立新的專案</span><span class="sxs-lookup"><span data-stu-id="0eb48-102">Step 2: Create a New Project</span></span>
<span data-ttu-id="0eb48-103">在此步驟中，您必須建立新的方案使用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="0eb48-103">In this step, you build a new solution by using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)] environment.</span></span> <span data-ttu-id="0eb48-104">首先，您會建立新的專案 (BTAHL7V22Common) 包含三個一般結構描述 （適用於資料類型、 區段和資料表值），使用 V2.2 HL7 結構描述，包括將用於外寄 HL7 訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="0eb48-104">First, you create a new project (BTAHL7V22Common) that contains the three common schemas (for data types, segments, and table values) that the HL7 V2.2 schemas use, including the schema that you will use for the outgoing HL7 message.</span></span> <span data-ttu-id="0eb48-105">第二，您可以建立另一個新的專案 (BTAHL7V2XCommon) 包含用於 HL7 訊息 (MSH_25_GLO_DEF) 中的標頭的一般標準結構描述。</span><span class="sxs-lookup"><span data-stu-id="0eb48-105">Second, you build another new project (BTAHL7V2XCommon) that contains the common standard schema used for headers in HL7 messages (MSH_25_GLO_DEF).</span></span>  
  
### <a name="to-create-a-new-project"></a><span data-ttu-id="0eb48-106">建立新的專案</span><span class="sxs-lookup"><span data-stu-id="0eb48-106">To create a new project</span></span>  
  
1.  <span data-ttu-id="0eb48-107">啟動**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="0eb48-107">Start **Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="0eb48-108">在 **[檔案]** 功能表上，指向 **[開新檔案]**，然後按一下 **[專案]**。</span><span class="sxs-lookup"><span data-stu-id="0eb48-108">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="0eb48-109">在 [新增專案] 對話方塊中，展開**BizTalk 專案**資料夾，然後再按一下**BTAHL7Projects**資料夾。</span><span class="sxs-lookup"><span data-stu-id="0eb48-109">In the New Project dialog box, expand the **BizTalk Projects** folder, and then click the **BTAHL7Projects** folder.</span></span>  
  
4.  <span data-ttu-id="0eb48-110">在**範本**] 窗格中，按一下 [ **BTAHL7V22Common 專案**。</span><span class="sxs-lookup"><span data-stu-id="0eb48-110">In the **Templates** pane, click **BTAHL7V22Common Project**.</span></span>  
  
5.  <span data-ttu-id="0eb48-111">在**名稱**欄位中，輸入**BTAHL7V22Common**做為專案名稱。</span><span class="sxs-lookup"><span data-stu-id="0eb48-111">In the **Name** field, type **BTAHL7V22Common** as the project name.</span></span>  
  
6.  <span data-ttu-id="0eb48-112">在**位置**欄位中，輸入*\<磁碟機\>***: \Tutorial**作為路徑，然後按一下**確定**開啟新的專案。</span><span class="sxs-lookup"><span data-stu-id="0eb48-112">In the **Location** field, type *\<drive\>***:\Tutorial** as the path, and then click **OK** to open the new project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0eb48-113">BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 將新的專案加入至方案總管 中，有三種常見的結構描述：</span><span class="sxs-lookup"><span data-stu-id="0eb48-113">BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) adds a new project to Solution Explorer with the three common schemas:</span></span>  
  
    -   <span data-ttu-id="0eb48-114">datatypes_22.xsd</span><span class="sxs-lookup"><span data-stu-id="0eb48-114">datatypes_22.xsd</span></span>  
  
    -   <span data-ttu-id="0eb48-115">segments_22.xsd</span><span class="sxs-lookup"><span data-stu-id="0eb48-115">segments_22.xsd</span></span>  
  
    -   <span data-ttu-id="0eb48-116">tablevalues_22.xsd</span><span class="sxs-lookup"><span data-stu-id="0eb48-116">tablevalues_22.xsd</span></span>  
  
     [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="0eb48-117">建立專案資料夾和檔案中\<*磁碟機*\>: \Tutorial\BTAHL7V22Common 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0eb48-117"> creates the project folder and files in the \<*drive*\>:\Tutorial\BTAHL7V22Common folder.</span></span>  
  
7.  <span data-ttu-id="0eb48-118">在 **[檔案]** 功能表上，指向 **[開新檔案]**，然後按一下 **[專案]**。</span><span class="sxs-lookup"><span data-stu-id="0eb48-118">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
8.  <span data-ttu-id="0eb48-119">在 [新增專案] 對話方塊中，展開**BizTalk 專案**資料夾，然後再按一下**BTAHL7Projects**資料夾。</span><span class="sxs-lookup"><span data-stu-id="0eb48-119">In the New Project dialog box, expand the **BizTalk Projects** folder, and then click the **BTAHL7Projects** folder.</span></span>  
  
9. <span data-ttu-id="0eb48-120">在**範本**] 窗格中，按一下 [ **btahl7v2xc 通用專案**。</span><span class="sxs-lookup"><span data-stu-id="0eb48-120">In the **Templates** pane, click **BTAHL7V2XCommon Project**.</span></span>  
  
10. <span data-ttu-id="0eb48-121">在**名稱**欄位中，輸入**btahl7v2xc 通用**做為專案名稱。</span><span class="sxs-lookup"><span data-stu-id="0eb48-121">In the **Name** field, type **BTAHL7V2XCommon** as the project name.</span></span>  
  
11. <span data-ttu-id="0eb48-122">在**位置**欄位中，輸入*\<磁碟機\>***: \Tutorial**做為路徑。</span><span class="sxs-lookup"><span data-stu-id="0eb48-122">In the **Location** field, type *\<drive\>***:\Tutorial** as the path.</span></span>  
  
12. <span data-ttu-id="0eb48-123">在**方案**欄位中，選取**將加入至方案**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="0eb48-123">In the **Solution** field, select **Add to Solution**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="0eb48-124">具有下列結構描述會將新的專案加入方案總管 中：</span><span class="sxs-lookup"><span data-stu-id="0eb48-124"> adds a new project to Solution Explorer with the following schemas:</span></span>  
  
    -   <span data-ttu-id="0eb48-125">ACK_24_GLO_DEF.xsd</span><span class="sxs-lookup"><span data-stu-id="0eb48-125">ACK_24_GLO_DEF.xsd</span></span>  
  
    -   <span data-ttu-id="0eb48-126">ACK_25_GLO_DEF.xsd</span><span class="sxs-lookup"><span data-stu-id="0eb48-126">ACK_25_GLO_DEF.xsd</span></span>  
  
    -   <span data-ttu-id="0eb48-127">MSH_25_GLO_DEF.xsd</span><span class="sxs-lookup"><span data-stu-id="0eb48-127">MSH_25_GLO_DEF.xsd</span></span>  
  
     [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="0eb48-128">建立專案資料夾和檔案中**\<磁碟機\>: \Tutorial\BTAHL7V22Common\BTAHL72XCommon**資料夾。</span><span class="sxs-lookup"><span data-stu-id="0eb48-128"> creates the project folder and files in the **\<drive\>:\Tutorial\BTAHL7V22Common\BTAHL72XCommon** folder.</span></span>  
  
 <span data-ttu-id="0eb48-129">若要繼續[步驟 3： 指派強式名稱組件](../../adapters-and-accelerators/accelerator-hl7/step-3-assign-a-strong-name-to-the-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="0eb48-129">Proceed to [Step 3: Assign a Strong Name to the Assembly](../../adapters-and-accelerators/accelerator-hl7/step-3-assign-a-strong-name-to-the-assembly.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eb48-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="0eb48-130">See Also</span></span>  
 [<span data-ttu-id="0eb48-131">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="0eb48-131">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)