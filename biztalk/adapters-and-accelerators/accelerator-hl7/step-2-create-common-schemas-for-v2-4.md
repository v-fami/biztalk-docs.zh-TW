---
title: 步驟 2： 建立 V2.4 通用結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interrogative tutorial, common schemas
ms.assetid: 333ae85a-a307-4ab1-97f4-4d7b986e91de
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60b199bcd350a3341640baa05b875347c4f04bb5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25960708"
---
# <a name="step-2-create-common-schemas-for-v24"></a><span data-ttu-id="bfc56-102">步驟 2： 建立 V2.4 通用結構描述</span><span class="sxs-lookup"><span data-stu-id="bfc56-102">Step 2: Create Common Schemas for V2.4</span></span>
<span data-ttu-id="bfc56-103">V2.4 結構描述是經常參考的結構描述，以用來驗證查詢和回應訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="bfc56-103">The V2.4 schemas are commonly referenced schemas, which you use to validate the query and response message instances.</span></span>  
  
### <a name="to-create-the-common-schemas-for-v24"></a><span data-ttu-id="bfc56-104">若要建立 V2.4 常見的結構描述</span><span class="sxs-lookup"><span data-stu-id="bfc56-104">To create the common schemas for V2.4</span></span>  
  
1.  <span data-ttu-id="bfc56-105">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="bfc56-105">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="bfc56-106">在 [新增專案] 對話方塊中**專案類型**清單中，展開**BizTalk 專案**，然後選取**BTAHL7Projects**。</span><span class="sxs-lookup"><span data-stu-id="bfc56-106">In the New Project dialog box, in the **Project Types** list, expand **BizTalk Projects**, and then select **BTAHL7Projects**.</span></span>  
  
3.  <span data-ttu-id="bfc56-107">在**範本**清單中，選取**BTAHL7V24Common 專案**。</span><span class="sxs-lookup"><span data-stu-id="bfc56-107">In the **Templates** list, select **BTAHL7V24Common Project**.</span></span>  
  
4.  <span data-ttu-id="bfc56-108">在**名稱**欄位中，輸入**Interrogative_24Schemas**。</span><span class="sxs-lookup"><span data-stu-id="bfc56-108">In the **Name** field, type **Interrogative_24Schemas**.</span></span>  
  
5.  <span data-ttu-id="bfc56-109">在 方案 欄位中，選取**將加入至方案**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="bfc56-109">In the Solution field, select **Add to Solution**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="bfc56-110">在方案總管 中，請注意，在專案中包含三個結構描述 （datatypes_24.xsd、 segments_24.xsd 和 tablevalues_24.xsd）。</span><span class="sxs-lookup"><span data-stu-id="bfc56-110">In Solution Explorer, notice that three schemas (datatypes_24.xsd, segments_24.xsd, and tablevalues_24.xsd) are included in the project.</span></span>  
  
6.  <span data-ttu-id="bfc56-111">在 [方案總管] 中，以滑鼠右鍵按一下**Interrogative_24Schemas**專案，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="bfc56-111">In Solution Explorer, right-click **Interrogative_24Schemas** project,and then click **Properties**.</span></span>  
  
7.  <span data-ttu-id="bfc56-112">在 [Interrogative_24Schemas 屬性頁] 對話方塊中，按一下**組件**。</span><span class="sxs-lookup"><span data-stu-id="bfc56-112">In the Interrogative_24Schemas Property Pages dialog box, click **Assembly**.</span></span>  
  
8.  <span data-ttu-id="bfc56-113">在右窗格中，向下捲動至**強式名稱**區段中，按一下右邊的欄位**組件金鑰檔案**，然後按一下省略符號 （...） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="bfc56-113">In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (…) button.</span></span>  
  
9. <span data-ttu-id="bfc56-114">在**組件金鑰檔案**對話方塊中，瀏覽至\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\Interrogative 教學課程，按一下**key.snk**，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="bfc56-114">In the **Assembly Key File** dialog box, browse to \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\Interrogative Tutorial, click **key.snk**, and then click **Open**.</span></span>  
  
10. <span data-ttu-id="bfc56-115">在 Interrogative_24Schemas 屬性頁 對話方塊中，按一下**確定**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="bfc56-115">In the Interrogative_24Schemas Property Pages dialog box, click **OK** to save your changes.</span></span>  
  
11. <span data-ttu-id="bfc56-116">在 [方案總管] 中，以滑鼠右鍵按一下**Interrogative_24Schemas**專案，然後再按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="bfc56-116">In Solution Explorer, right-click **Interrogative_24Schemas** project, and then click **Deploy**.</span></span> <span data-ttu-id="bfc56-117">按一下**確定**對話方塊要求您將變更儲存到方案。</span><span class="sxs-lookup"><span data-stu-id="bfc56-117">Click **OK** to the dialog box asking you to save changes to the solution.</span></span> <span data-ttu-id="bfc56-118">確定成功的訊息出現在 [輸出] 視窗。</span><span class="sxs-lookup"><span data-stu-id="bfc56-118">Ensure a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bfc56-119">如果未出現正確的訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的結構描述。</span><span class="sxs-lookup"><span data-stu-id="bfc56-119">If the correct message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your schemas.</span></span>  
  
 <span data-ttu-id="bfc56-120">若要繼續[步驟 3： 建立和部署觸發程序事件 （訊息） 專案](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-deploy-a-trigger-event-message-project-hl7-main.md)。</span><span class="sxs-lookup"><span data-stu-id="bfc56-120">Proceed to [Step 3: Create and Deploy a Trigger Event (Message) Project](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-deploy-a-trigger-event-message-project-hl7-main.md).</span></span>