---
title: 步驟 1： 建立及部署標頭和通知結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, header schemas
- header schemas
ms.assetid: 3ff013a4-6c67-4bac-be97-81b2dc5b6119
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9ffa8ab8d80a8b2da172378349eb9761a728fb7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25960740"
---
# <a name="step-1-create-and-deploy-header-and-acknowledgment-schemas"></a><span data-ttu-id="ac87a-102">步驟 1： 建立及部署標頭和通知結構描述</span><span class="sxs-lookup"><span data-stu-id="ac87a-102">Step 1: Create and Deploy Header and Acknowledgment Schemas</span></span>
<span data-ttu-id="ac87a-103">您可以使用標頭結構描述來驗證訊息執行個體的標頭 （MSH 區段）。</span><span class="sxs-lookup"><span data-stu-id="ac87a-103">You use the header schema to validate the header (MSH segment) of the message instance.</span></span> <span data-ttu-id="ac87a-104">您可以使用通知結構描述來產生訊息執行個體的通知。</span><span class="sxs-lookup"><span data-stu-id="ac87a-104">You use the acknowledgment schema to generate the acknowledgment for the message instance.</span></span> <span data-ttu-id="ac87a-105">此程序之間是共通的所有結構描述版本[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2.X。</span><span class="sxs-lookup"><span data-stu-id="ac87a-105">This process is common across all schemas versions of [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 2.X.</span></span>  
  
### <a name="to-create-the-header-and-acknowledgment-schemas"></a><span data-ttu-id="ac87a-106">若要建立之標頭和通知結構描述</span><span class="sxs-lookup"><span data-stu-id="ac87a-106">To create the header and acknowledgment schemas</span></span>  
  
1.  <span data-ttu-id="ac87a-107">啟動**Microsoft Visual Studio 2012**。</span><span class="sxs-lookup"><span data-stu-id="ac87a-107">Start **Microsoft Visual Studio 2012**.</span></span>  
  
2.  <span data-ttu-id="ac87a-108">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="ac87a-108">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="ac87a-109">在 [新增專案] 對話方塊中**專案類型**區段中，展開**BizTalk 專案**，然後選取**BTAHL7Projects**。</span><span class="sxs-lookup"><span data-stu-id="ac87a-109">In the New Project dialog box, in the **Project Types** section, expand **BizTalk Projects**, and then select **BTAHL7Projects**.</span></span>  
  
4.  <span data-ttu-id="ac87a-110">在 範本 區段中，選取**btahl7v2xc 通用專案**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="ac87a-110">In the Templates section, select **BTAHL7V2XCommon Project**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ac87a-111">在方案總管 中，請注意，在專案中包含三個結構描述 （ACK_24_GLO_DEF.xsd ACK_25_GLO_DEF.xsd 和 MSH_25_GLO_DEF.xsd）。</span><span class="sxs-lookup"><span data-stu-id="ac87a-111">In Solution Explorer, notice that the three schemas (ACK_24_GLO_DEF.xsd ACK_25_GLO_DEF.xsd, and MSH_25_GLO_DEF.xsd) are included in the project.</span></span>  
  
## <a name="step-1a-assign-a-strong-key-to-the-assembly-and-deploy"></a><span data-ttu-id="ac87a-112">步驟 1A： 指派強式金鑰組件和部署</span><span class="sxs-lookup"><span data-stu-id="ac87a-112">Step 1A: Assign a Strong Key to the Assembly and Deploy</span></span>  
 <span data-ttu-id="ac87a-113">若要將組件的強式金鑰，然後再部署組件使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="ac87a-113">Use the following procedure to assign a strong key to the assembly and then deploy the assembly.</span></span>  
  
#### <a name="to-assign-a-strong-key-and-deploy-the-assembly"></a><span data-ttu-id="ac87a-114">指派強式金鑰，並部署組件</span><span class="sxs-lookup"><span data-stu-id="ac87a-114">To assign a strong key and deploy the assembly</span></span>  
  
1.  <span data-ttu-id="ac87a-115">啟動**Visual Studio 2012 的命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="ac87a-115">Start **Visual Studio 2012 Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="ac87a-116">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]命令提示字元中，瀏覽至\<*磁碟機*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本\>Accelerator for HL7 \SDK\端對端教學課程的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ac87a-116">At the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] command prompt, browse to the \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for HL7 \SDK\End-to-End Tutorial folder.</span></span>  
  
3.  <span data-ttu-id="ac87a-117">在命令提示字元中，輸入**sn – k key.snk**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="ac87a-117">At the command prompt, type **sn –k key.snk**, and then press ENTER.</span></span> <span data-ttu-id="ac87a-118">請確定下列成功訊息出現在 輸出 視窗，然後關閉 命令視窗。</span><span class="sxs-lookup"><span data-stu-id="ac87a-118">Ensure the following success message appears in the output window, and then close the command window.</span></span>  
  
     <span data-ttu-id="ac87a-119">**「 金鑰組寫入 key.snk。 」**</span><span class="sxs-lookup"><span data-stu-id="ac87a-119">**"Key pair written to key.snk."**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ac87a-120">如果未出現正確的訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的組件。</span><span class="sxs-lookup"><span data-stu-id="ac87a-120">If the correct message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your assembly.</span></span>  
  
4.  <span data-ttu-id="ac87a-121">在 方案總管 中，以滑鼠右鍵按一下**btahl7v2xc 通用 Project1**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="ac87a-121">In Solution Explorer, right-click **BTAHL7V2XCommon Project1**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="ac87a-122">在 btahl7v2xc 通用 Project1 屬性頁] 頁面上，按一下 [**組件**。</span><span class="sxs-lookup"><span data-stu-id="ac87a-122">On the BTAHL7V2XCommon Project1 Property Pages page, click **Assembly**.</span></span>  
  
6.  <span data-ttu-id="ac87a-123">在右窗格中，向下捲動至**強式名稱**區段中，按一下右邊的欄位**組件金鑰檔案**，然後按一下省略符號 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ac87a-123">In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (**…**) button.</span></span>  
  
7.  <span data-ttu-id="ac87a-124">在 [組件金鑰檔案] 對話方塊中，瀏覽至\<*磁碟機*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端教學課程，請選取**key.snk**，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="ac87a-124">In the Assembly Key File dialog box, browse to \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial, select **key.snk**, and then click **Open**.</span></span>  
  
8.  <span data-ttu-id="ac87a-125">Btahl7v2xc 通用專案屬性] 頁面上，按一下 [**確定**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="ac87a-125">On the BTAHL7V2XCommon Project Property page, click **OK** to save your changes.</span></span>  
  
9. <span data-ttu-id="ac87a-126">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，請在**方案總管] 中**，以滑鼠右鍵按一下**btahl7v2xc 通用專案**，然後按一下 [**部署**。</span><span class="sxs-lookup"><span data-stu-id="ac87a-126">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in **Solution Explorer**, right-click **BTAHL7V2XCommon Project**, and then click **Deploy**.</span></span> <span data-ttu-id="ac87a-127">確定成功的訊息出現在 [輸出] 視窗。</span><span class="sxs-lookup"><span data-stu-id="ac87a-127">Ensure a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ac87a-128">如果未出現正確的部署訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的部署。</span><span class="sxs-lookup"><span data-stu-id="ac87a-128">If the correct deploy message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your deployment.</span></span>  
  
 <span data-ttu-id="ac87a-129">若要繼續[步驟 2： 建立 V2.3.1 的通用結構描述](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-3-1.md)。</span><span class="sxs-lookup"><span data-stu-id="ac87a-129">Proceed to [Step 2: Create Common Schemas for V2.3.1](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-3-1.md).</span></span>