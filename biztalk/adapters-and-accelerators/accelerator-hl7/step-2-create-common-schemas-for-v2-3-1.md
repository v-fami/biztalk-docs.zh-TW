---
title: "步驟 2： 建立 V2.3.1 通用結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, common schemas
- common schemas
ms.assetid: db1a2206-559f-475a-803d-55522cce007e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5f8ed36b4a1ae8553e8df488e8fd5a606c0eabd
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-create-common-schemas-for-v231"></a><span data-ttu-id="7c506-102">步驟 2： 建立 V2.3.1 通用結構描述</span><span class="sxs-lookup"><span data-stu-id="7c506-102">Step 2: Create Common Schemas for V2.3.1</span></span>
<span data-ttu-id="7c506-103">V2.3.1 結構描述是經常參考的結構描述，以用來驗證訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="7c506-103">The V2.3.1 schemas are commonly referenced schemas, which you use to validate the message instance.</span></span>  
  
### <a name="to-create-a-common-schema-for-v231"></a><span data-ttu-id="7c506-104">若要建立 V2.3.1 通用的結構描述</span><span class="sxs-lookup"><span data-stu-id="7c506-104">To create a common schema for V2.3.1</span></span>  
  
1.  <span data-ttu-id="7c506-105">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="7c506-105">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="7c506-106">在 [新增專案] 對話方塊中**專案類型**區段中，展開**BizTalk 專案**，然後選取**BTAHL7Projects**。</span><span class="sxs-lookup"><span data-stu-id="7c506-106">In the New Project dialog box, in the **Project Types** section, expand **BizTalk Projects**, and then select **BTAHL7Projects**.</span></span>  
  
3.  <span data-ttu-id="7c506-107">在 [範本] 區段中，選取**BTAHL7V231Common 專案**。</span><span class="sxs-lookup"><span data-stu-id="7c506-107">In the Templates section, select **BTAHL7V231Common Project**.</span></span>  
  
4.  <span data-ttu-id="7c506-108">在**名稱**方塊中，輸入**BTAHL7V231Common 專案**做為專案名稱。</span><span class="sxs-lookup"><span data-stu-id="7c506-108">In the **Name** box, enter **BTAHL7V231Common Project** as the project name.</span></span>  
  
5.  <span data-ttu-id="7c506-109">在**方案**方塊中，選取**將加入至方案**。</span><span class="sxs-lookup"><span data-stu-id="7c506-109">In the **Solution** box, select **Add to Solution**.</span></span>  
  
6.  <span data-ttu-id="7c506-110">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="7c506-110">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7c506-111">在方案總管 中，三個結構描述 （datatypes_231.xsd、 segments_231.xsd 和 tablevalues_231.xsd） 都包含在專案中。</span><span class="sxs-lookup"><span data-stu-id="7c506-111">In Solution Explorer, three schemas (datatypes_231.xsd, segments_231.xsd, and tablevalues_231.xsd) are included in the project.</span></span>  
  
7.  <span data-ttu-id="7c506-112">在 方案總管 中，以滑鼠右鍵按一下**BTAHL7V231Common 專案**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="7c506-112">In Solution Explorer, right-click **BTAHL7V231Common Project**, and then click **Properties**.</span></span>  
  
8.  <span data-ttu-id="7c506-113">在 BTAHL7V231Common 屬性頁面上，按一下 **簽署**。</span><span class="sxs-lookup"><span data-stu-id="7c506-113">On the BTAHL7V231Common Property Page, click **Signing**.</span></span>  
  
9. <span data-ttu-id="7c506-114">選取**簽署組件**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="7c506-114">Select the **Sign the assembly** check box.</span></span>  
  
10. <span data-ttu-id="7c506-115">在**選擇強式名稱金鑰檔**，選取**\<瀏覽...\>** .</span><span class="sxs-lookup"><span data-stu-id="7c506-115">In **Choose a strong name key file**, select **\<Browse…\>** .</span></span>  
  
11. <span data-ttu-id="7c506-116">瀏覽至\<磁碟機\>: \Batching 教學課程中，選取**key.snk**，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="7c506-116">Browse to \<drive\>:\Batching Tutorial, select **key.snk**, and then click **Open**.</span></span>  
  
12. <span data-ttu-id="7c506-117">在 方案總管 中，以滑鼠右鍵按一下**BTAHL7V231Common 專案**，然後按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="7c506-117">In Solution Explorer, right-click **BTAHL7V231Common Project**, and then click **Deploy**.</span></span> <span data-ttu-id="7c506-118">確定成功的訊息出現在 [輸出] 視窗。</span><span class="sxs-lookup"><span data-stu-id="7c506-118">Ensure a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7c506-119">如果未出現正確的訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的結構描述。</span><span class="sxs-lookup"><span data-stu-id="7c506-119">If the correct message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your schemas.</span></span>  
  
 <span data-ttu-id="7c506-120">若要繼續[步驟 3： 新增觸發程序事件 （訊息） 結構描述](../../adapters-and-accelerators/accelerator-hl7/step-3-add-a-trigger-event-message-schema.md)。</span><span class="sxs-lookup"><span data-stu-id="7c506-120">Proceed to [Step 3: Add a Trigger Event (Message) Schema](../../adapters-and-accelerators/accelerator-hl7/step-3-add-a-trigger-event-message-schema.md).</span></span>