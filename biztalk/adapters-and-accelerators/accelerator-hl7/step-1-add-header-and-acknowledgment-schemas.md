---
title: 步驟 1： 加入標頭和通知結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 808132bf-02e7-4ff4-b914-9fae5d27e5fd
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f79778801b1ca70d4e8356a24886c792fe447e33
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26005335"
---
# <a name="step-1-add-header-and-acknowledgment-schemas"></a><span data-ttu-id="b03a5-102">步驟 1： 加入標頭和通知結構描述</span><span class="sxs-lookup"><span data-stu-id="b03a5-102">Step 1: Add Header and Acknowledgment Schemas</span></span>
<span data-ttu-id="b03a5-103">在此步驟中，您可以建立新 BTAHL72XCommon 專案範本為基礎的專案。</span><span class="sxs-lookup"><span data-stu-id="b03a5-103">In this step, you create a new project based on the BTAHL72XCommon Project template.</span></span> <span data-ttu-id="b03a5-104">此範本包含三種常見的結構描述，訊息標頭 (MSH_25_GLO_DEF.xsd) 和通知 (ACK_24_GLO_DEF.xsd) 和 (ACK_25_GLO_DEF.xsd)。</span><span class="sxs-lookup"><span data-stu-id="b03a5-104">This template contains the three common schemas for message headers (MSH_25_GLO_DEF.xsd) and acknowledgments (ACK_24_GLO_DEF.xsd) and (ACK_25_GLO_DEF.xsd).</span></span> <span data-ttu-id="b03a5-105">您必須包含在專案中這些結構描述，該 BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 組建及/或正確驗證的訊息標頭和通知。</span><span class="sxs-lookup"><span data-stu-id="b03a5-105">You must include these schemas in a project so that BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) builds and/or validates the message headers and acknowledgments correctly.</span></span> <span data-ttu-id="b03a5-106">此程序之間是共通的所有結構描述版本[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2.X。</span><span class="sxs-lookup"><span data-stu-id="b03a5-106">This process is common across all schema versions of [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 2.X.</span></span>  
  
 <span data-ttu-id="b03a5-107">您也建立強式金鑰、 將它指派給組件，然後再部署組件。</span><span class="sxs-lookup"><span data-stu-id="b03a5-107">You also create a strong key, assign it to the assembly, and then deploy the assembly.</span></span> <span data-ttu-id="b03a5-108">強式金鑰組件提供安全性和身分識別，而且不需要進行部署。</span><span class="sxs-lookup"><span data-stu-id="b03a5-108">The strong key provides security and identity to the assembly, and is necessary for deployment.</span></span> <span data-ttu-id="b03a5-109">當您部署組件時，它會儲存在組態資料庫 （也稱為 「 BizTalk 管理資料庫） 和全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="b03a5-109">When you deploy the assembly, it is stored in the Configuration database (also known as the BizTalk Management database) and the global assembly cache (GAC).</span></span>  
  
### <a name="to-create-the-project-and-add-header-and-acknowledgment-schemas"></a><span data-ttu-id="b03a5-110">若要建立專案並加入標頭和通知結構描述</span><span class="sxs-lookup"><span data-stu-id="b03a5-110">To create the project and add header and acknowledgment schemas</span></span>  
  
1.  <span data-ttu-id="b03a5-111">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="b03a5-111">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="b03a5-112">在 新增專案 對話方塊中**專案類型**清單中，展開**BizTalk 專案**，然後按一下  **BTAHL7Projects**。</span><span class="sxs-lookup"><span data-stu-id="b03a5-112">In the New Project dialog box, in the **Project Types** list, expand **BizTalk Projects**, and then click **BTAHL7Projects**.</span></span>  
  
3.  <span data-ttu-id="b03a5-113">在**範本**清單中，按一下**btahl7v2xc 通用專案**。</span><span class="sxs-lookup"><span data-stu-id="b03a5-113">In the **Templates** list, click **BTAHL7V2XCommon Project**.</span></span>  
  
4.  <span data-ttu-id="b03a5-114">在**名稱**方塊中，輸入**btahl7v2xc 通用**做為專案名稱。</span><span class="sxs-lookup"><span data-stu-id="b03a5-114">In the **Name** box, type **BTAHL7V2XCommon** as the project name.</span></span>  
  
5.  <span data-ttu-id="b03a5-115">在**位置**方塊中，瀏覽至 **\<** *磁碟機***:\>\Batching 教學課程**。</span><span class="sxs-lookup"><span data-stu-id="b03a5-115">In the **Location** box, browse to **\<***drive***:\>\Batching Tutorial**.</span></span>  
  
6.  <span data-ttu-id="b03a5-116">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b03a5-116">Click **OK**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b03a5-117">在方案總管 中，三個結構描述 （MSH_25_GLO_DEF.xsd、 ACK_24_GLO_DEF.xsd 和 ACK_25_GLO_DEF.xsd） 都包含在專案中。</span><span class="sxs-lookup"><span data-stu-id="b03a5-117">In Solution Explorer, three schemas (MSH_25_GLO_DEF.xsd, ACK_24_GLO_DEF.xsd, and ACK_25_GLO_DEF.xsd) are included in the project.</span></span>  
  
### <a name="to-assign-a-strong-key-to-the-assembly-and-deploy"></a><span data-ttu-id="b03a5-118">若要指派至組件的強式金鑰，部署</span><span class="sxs-lookup"><span data-stu-id="b03a5-118">To assign a strong key to the assembly and deploy</span></span>  
  
1.  <span data-ttu-id="b03a5-119">開啟**Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="b03a5-119">Open **Visual Studio Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="b03a5-120">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]命令提示字元中，瀏覽至 **\<** *磁碟機***\>: \Batching 教學課程**資料夾。</span><span class="sxs-lookup"><span data-stu-id="b03a5-120">On the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] command prompt, browse to the **\<***drive***\>:\Batching Tutorial** folder.</span></span>  
  
3.  <span data-ttu-id="b03a5-121">在命令提示字元中，輸入**sn – k key.snk**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="b03a5-121">At the command prompt, type **sn –k key.snk**, and then press ENTER.</span></span> <span data-ttu-id="b03a5-122">請在 [輸出] 視窗中出現的成功訊息。</span><span class="sxs-lookup"><span data-stu-id="b03a5-122">Ensure that a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b03a5-123">如果未出現正確的訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的組件。</span><span class="sxs-lookup"><span data-stu-id="b03a5-123">If the correct message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your assembly.</span></span>  
  
4.  <span data-ttu-id="b03a5-124">在 方案總管 中，以滑鼠右鍵按一下**btahl7v2xc 通用專案**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="b03a5-124">In Solution Explorer, right-click **BTAHL7V2Xcommon Project**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="b03a5-125">在**btahl7v2xc 通用專案屬性頁**對話方塊中，按一下 **簽署**。</span><span class="sxs-lookup"><span data-stu-id="b03a5-125">In the **BTAHL7V2XCommon Project Property Page** dialog box, click **Signing**.</span></span>  
  
6.  <span data-ttu-id="b03a5-126">請檢查**簽署組件**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="b03a5-126">Check **Sign the assembly** check box.</span></span>  
  
7.  <span data-ttu-id="b03a5-127">在**選擇強式名稱**金鑰檔 下拉式清單中，選取**\<瀏覽...\>**.</span><span class="sxs-lookup"><span data-stu-id="b03a5-127">In **Choose a Strong name** key file drop down list select **\<Browse…\>**.</span></span>  
  
8.  <span data-ttu-id="b03a5-128">瀏覽至\<*磁碟機*\>: \Batching 教學課程中，選取**key.snk**，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="b03a5-128">Browse to \<*drive*\>:\Batching Tutorial, select **key.snk**, and then click **Open**.</span></span>  
  
9. <span data-ttu-id="b03a5-129">在 btahl7v2xc 通用專案屬性頁 視窗中，按一下**確定**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="b03a5-129">In the BTAHL7V2XCommon Project Property Pages window, click **OK** to save your changes.</span></span>  
  
10. <span data-ttu-id="b03a5-130">在 方案總管 中，以滑鼠右鍵按一下**btahl7v2xc 通用專案**，然後按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="b03a5-130">In Solution Explorer, right-click **BTAHL7V2Xcommon Project**, and then click **Deploy**.</span></span> <span data-ttu-id="b03a5-131">確定成功的訊息出現在 [輸出] 視窗。</span><span class="sxs-lookup"><span data-stu-id="b03a5-131">Ensure a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b03a5-132">如果未出現正確的部署訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的部署。</span><span class="sxs-lookup"><span data-stu-id="b03a5-132">If the correct deploy message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your deployment.</span></span>  
  
 <span data-ttu-id="b03a5-133">若要繼續[步驟 2： 加入常見的結構描述的 v2.3.1](../../adapters-and-accelerators/accelerator-hl7/step-2-add-common-schemas-for-v2-3-1.md)。</span><span class="sxs-lookup"><span data-stu-id="b03a5-133">Proceed to [Step 2: Add Common Schemas for v2.3.1](../../adapters-and-accelerators/accelerator-hl7/step-2-add-common-schemas-for-v2-3-1.md).</span></span>