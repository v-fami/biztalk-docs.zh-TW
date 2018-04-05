---
title: 步驟 1： 建立及部署通用標頭和通知結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interrogative tutorial, headers
ms.assetid: e0f11f58-9a8c-4567-a537-3d182fa7dce2
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 222f78232afd988e5bb47b2aa12bb75eb4635ce5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-create-and-deploy-common-header-and-acknowledgment-schemas"></a><span data-ttu-id="cf374-102">步驟 1： 建立及部署通用標頭和通知結構描述</span><span class="sxs-lookup"><span data-stu-id="cf374-102">Step 1: Create and Deploy Common Header and Acknowledgment Schemas</span></span>
<span data-ttu-id="cf374-103">您可以使用標頭結構描述來驗證訊息執行個體的標頭 （MSH 區段）。</span><span class="sxs-lookup"><span data-stu-id="cf374-103">You use the header schema to validate the header (MSH segment) of the message instance.</span></span> <span data-ttu-id="cf374-104">您可以使用通知結構描述來產生訊息執行個體的通知。</span><span class="sxs-lookup"><span data-stu-id="cf374-104">You use the acknowledgment schema to generate the acknowledgment for the message instance.</span></span> <span data-ttu-id="cf374-105">此程序適用於所有 HL7 結構描述版本。</span><span class="sxs-lookup"><span data-stu-id="cf374-105">This process is common across all HL7 schema versions.</span></span>  
  
### <a name="to-create-the-header-and-acknowledgment-schemas"></a><span data-ttu-id="cf374-106">若要建立之標頭和通知結構描述</span><span class="sxs-lookup"><span data-stu-id="cf374-106">To create the header and acknowledgment schemas</span></span>  
  
1.  <span data-ttu-id="cf374-107">啟動**Microsoft Visual Studio 2012**。</span><span class="sxs-lookup"><span data-stu-id="cf374-107">Start **Microsoft Visual Studio 2012**.</span></span>  
  
2.  <span data-ttu-id="cf374-108">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="cf374-108">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="cf374-109">在 [新增專案] 對話方塊中**專案類型**清單中，展開**BizTalk 專案**，然後選取**BTAHL7Projects**。</span><span class="sxs-lookup"><span data-stu-id="cf374-109">In the New Project dialog box, in the **Project Types** list, expand **BizTalk Projects**, and then select **BTAHL7Projects**.</span></span>  
  
4.  <span data-ttu-id="cf374-110">在**範本**清單中，選取**btahl7v2xc 通用專案**。</span><span class="sxs-lookup"><span data-stu-id="cf374-110">In the **Templates** list, select **BTAHL7V2XCommon Project**.</span></span>  
  
5.  <span data-ttu-id="cf374-111">在**名稱**欄位中，輸入**Interrogative_2XSchemas**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="cf374-111">In the **Name** field, type **Interrogative_2XSchemas**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="cf374-112">在方案總管 中，請注意，在專案中包含三個結構描述 （ACK_24_GLO_DEF.xsd、 ACK_25_GLO_DEF.xsd 和 MSH_25_GLO_DEF.xsd）。</span><span class="sxs-lookup"><span data-stu-id="cf374-112">In Solution Explorer, notice that three schemas (ACK_24_GLO_DEF.xsd, ACK_25_GLO_DEF.xsd, and MSH_25_GLO_DEF.xsd) are included in the project.</span></span>  
  
     <span data-ttu-id="cf374-113">保持開啟，Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="cf374-113">Leave Visual Studio open.</span></span>  
  
## <a name="step-1a-assign-a-strong-key-to-the-assembly-and-deploy"></a><span data-ttu-id="cf374-114">步驟 1A： 指派強式金鑰組件和部署</span><span class="sxs-lookup"><span data-stu-id="cf374-114">Step 1A: Assign a Strong Key to the Assembly and Deploy</span></span>  
 <span data-ttu-id="cf374-115">若要將組件的強式金鑰，然後再部署組件使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="cf374-115">Use the following procedure to assign a strong key to the assembly and then deploy the assembly.</span></span>  
  
#### <a name="to-assign-a-strong-key-and-deploy-the-assembly"></a><span data-ttu-id="cf374-116">指派強式金鑰，並部署組件</span><span class="sxs-lookup"><span data-stu-id="cf374-116">To assign a strong key and deploy the assembly</span></span>  
  
1.  <span data-ttu-id="cf374-117">啟動**Visual Studio 2012 的命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="cf374-117">Start **Visual Studio 2012 Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="cf374-118">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]命令提示字元，將您的目錄變更\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\Interrogative教學課程的資料夾。</span><span class="sxs-lookup"><span data-stu-id="cf374-118">At the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] command prompt, change your directory to the \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\Interrogative Tutorial folder.</span></span>  
  
3.  <span data-ttu-id="cf374-119">在命令提示字元中，輸入**sn – k key.snk**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="cf374-119">At the command prompt, type **sn –k key.snk**, and then press **Enter**.</span></span> <span data-ttu-id="cf374-120">請在 [輸出] 視窗中出現的成功訊息。</span><span class="sxs-lookup"><span data-stu-id="cf374-120">Ensure that a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cf374-121">如果未出現正確的訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的組件。</span><span class="sxs-lookup"><span data-stu-id="cf374-121">If the correct message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your assembly.</span></span>  
  
4.  <span data-ttu-id="cf374-122">在 [方案總管] 中，以滑鼠右鍵按一下**Interrogative_2XSchemas**專案，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="cf374-122">In Solution Explorer, right-click **Interrogative_2XSchemas** project, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="cf374-123">在 [Interrogative_2XSchemas 屬性頁] 對話方塊中，按一下**組件**。</span><span class="sxs-lookup"><span data-stu-id="cf374-123">In the Interrogative_2XSchemas Property Pages dialog box, click **Assembly**.</span></span>  
  
6.  <span data-ttu-id="cf374-124">在右窗格中，向下捲動至**強式名稱**區段中，按一下右邊的欄位**組件金鑰檔案**，然後按一下省略符號 （...） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="cf374-124">In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (…) button.</span></span>  
  
7.  <span data-ttu-id="cf374-125">在 組件金鑰檔案 對話方塊中，瀏覽至\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\Interrogative 教學課程中，按一下  **key.snk**，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="cf374-125">In the Assembly Key File dialog box, browse to \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\Interrogative Tutorial, click **key.snk**, and then click **Open**.</span></span>  
  
8.  <span data-ttu-id="cf374-126">在 Interrogative_2XSchemas 屬性頁 對話方塊中，按一下**確定**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="cf374-126">In the Interrogative_2XSchemas Property Pages dialog box, click **OK** to save your changes.</span></span>  
  
9. <span data-ttu-id="cf374-127">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，以滑鼠右鍵按一下**Interrogative_2XSchemas**專案，然後再按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="cf374-127">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in Solution Explorer, right-click **Interrogative_2XSchemas** project, and then click **Deploy**.</span></span> <span data-ttu-id="cf374-128">確定成功的訊息出現在 [輸出] 視窗。</span><span class="sxs-lookup"><span data-stu-id="cf374-128">Ensure a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cf374-129">如果未出現正確的部署訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的部署。</span><span class="sxs-lookup"><span data-stu-id="cf374-129">If the correct deploy message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your deployment.</span></span>  
  
 <span data-ttu-id="cf374-130">若要繼續[步驟 2： 建立 V2.4 的通用結構描述](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-4.md)。</span><span class="sxs-lookup"><span data-stu-id="cf374-130">Proceed to [Step 2: Create Common Schemas for V2.4](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-4.md).</span></span>