---
title: 步驟 2： 新增 v2.3.1 通用結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: da98fe6c-4776-4cb8-8454-af3128dea4ab
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36b07419b50d02d1f810dffbd7417533e844a3ea
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994159"
---
# <a name="step-2-add-common-schemas-for-v231"></a><span data-ttu-id="23293-102">步驟 2： 新增 v2.3.1 通用結構描述</span><span class="sxs-lookup"><span data-stu-id="23293-102">Step 2: Add Common Schemas for v2.3.1</span></span>
<span data-ttu-id="23293-103">在此步驟中，您可以建立根據 BTAHL7231Common 專案範本的新專案。</span><span class="sxs-lookup"><span data-stu-id="23293-103">In this step, you create a new project based on the BTAHL7231Common Project template.</span></span> <span data-ttu-id="23293-104">此範本包含三個常見的結構描述 （適用於資料類型、 區段和資料表值），Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 用以驗證 v2.3.1 訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="23293-104">This template contains the three common schemas (for data types, segments, and table values) that Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) uses to validate v2.3.1 message instances.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="23293-105"> HL7 v2.3.1 結構描述，包括您要用於內送的批次中的個別訊息的結構描述搭配使用這些常見的結構描述 (ADT ^ 將 adt^a03)。</span><span class="sxs-lookup"><span data-stu-id="23293-105"> uses these common schemas in conjunction with the HL7 v2.3.1 schemas, including the schema that you will use for the individual messages in the incoming batch (ADT^A03).</span></span>  
  
 <span data-ttu-id="23293-106">在此步驟結束時，您指派給組件的強式金鑰，並部署。</span><span class="sxs-lookup"><span data-stu-id="23293-106">At the end of the step, you assign a strong key to the assembly and deploy.</span></span> <span data-ttu-id="23293-107">您不需要建立第二個的強式金鑰;您可以使用您在中建立的強式金鑰[步驟 1： 新增標頭和通知結構描述](../../adapters-and-accelerators/accelerator-hl7/step-1-add-header-and-acknowledgment-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="23293-107">You do not have to create a second strong key; you can use the strong key that you created in [Step 1: Add Header and Acknowledgment Schemas](../../adapters-and-accelerators/accelerator-hl7/step-1-add-header-and-acknowledgment-schemas.md).</span></span>  
  
### <a name="to-add-v231-common-schemas-and-deploy-the-assembly"></a><span data-ttu-id="23293-108">若要新增 v2.3.1 通用結構描述，並部署組件</span><span class="sxs-lookup"><span data-stu-id="23293-108">To add v2.3.1 common schemas and deploy the assembly</span></span>  
  
1. <span data-ttu-id="23293-109">在 [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="23293-109">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2. <span data-ttu-id="23293-110">在 [新增專案] 對話方塊中，在**專案類型**區段中，展開**BizTalk 專案**，然後選取**BTAHL7Projects**。</span><span class="sxs-lookup"><span data-stu-id="23293-110">In the New Project dialog box, in the **Project Types** section, expand **BizTalk Projects**, and then select **BTAHL7Projects**.</span></span>  
  
3. <span data-ttu-id="23293-111">在 **範本**區段中，選取**BTAHL7V231Common 專案**。</span><span class="sxs-lookup"><span data-stu-id="23293-111">In the **Templates** section, select **BTAHL7V231Common Project**.</span></span>  
  
4. <span data-ttu-id="23293-112">在 **名稱**方塊中，輸入**BTAHL7V231Common 專案**做為專案名稱。</span><span class="sxs-lookup"><span data-stu-id="23293-112">In the **Name** box, enter **BTAHL7V231Common Project** as the project name.</span></span>  
  
5. <span data-ttu-id="23293-113">在 **解決方案**方塊中，選取**加入至方案**。</span><span class="sxs-lookup"><span data-stu-id="23293-113">In the **Solution** box, select **Add to Solution**.</span></span>  
  
6. <span data-ttu-id="23293-114">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="23293-114">Click **OK**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="23293-115">在 [方案總管] 中，三個結構描述 （datatypes_231.xsd segments_231.xsd 和 tablevalues_231.xsd），會包含在專案中。</span><span class="sxs-lookup"><span data-stu-id="23293-115">In Solution Explorer, three schemas (datatypes_231.xsd, segments_231.xsd, and tablevalues_231.xsd) are included in the project.</span></span>  
  
7. <span data-ttu-id="23293-116">在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7V231Common 專案**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="23293-116">In Solution Explorer, right-click **BTAHL7V231Common Project**, and then click **Properties**.</span></span>  
  
8. <span data-ttu-id="23293-117">在 BTAHL7V231Common 屬性頁 對話方塊中，按一下 **簽署**。</span><span class="sxs-lookup"><span data-stu-id="23293-117">On the BTAHL7V231Common Property Pages dialog box, click **Signing**.</span></span>  
  
9. <span data-ttu-id="23293-118">請檢查**簽署組件**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="23293-118">Check **Sign the assembly** check box.</span></span>  
  
10. <span data-ttu-id="23293-119">在 選擇強式名稱金鑰檔下拉式清單中選取。</span><span class="sxs-lookup"><span data-stu-id="23293-119">In Choose a strong name key file drop down list select.</span></span>  
  
11. <span data-ttu-id="23293-120">瀏覽至 **: \Batching 教學課程**，選取**key.snk**，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="23293-120">Browse to **:\Batching Tutorial**, select **key.snk**, and then click **Open**.</span></span>  
  
12. <span data-ttu-id="23293-121">以滑鼠右鍵按一下**BTAHL7V231Common**，然後按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="23293-121">Right-click **BTAHL7V231Common**, and then click **Deploy**.</span></span> <span data-ttu-id="23293-122">請確定在 [輸出] 視窗中會出現成功訊息。</span><span class="sxs-lookup"><span data-stu-id="23293-122">Ensure a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="23293-123">如果未出現正確的訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的結構描述。</span><span class="sxs-lookup"><span data-stu-id="23293-123">If the correct message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your schemas.</span></span>  
  
    <span data-ttu-id="23293-124">請繼續進行[步驟 3： 新增觸發程序事件 （訊息） 結構描述](../../adapters-and-accelerators/accelerator-hl7/step-3-add-a-trigger-event-message-schema.md)。</span><span class="sxs-lookup"><span data-stu-id="23293-124">Proceed to [Step 3: Add a Trigger Event (Message) Schema](../../adapters-and-accelerators/accelerator-hl7/step-3-add-a-trigger-event-message-schema.md).</span></span>