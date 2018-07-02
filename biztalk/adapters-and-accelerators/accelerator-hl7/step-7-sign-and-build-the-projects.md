---
title: 步驟 7： 簽署和建置的專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, projects
- projects, building
- projects, signing
ms.assetid: b66e4dc1-4ec6-4ec0-a69a-419b116b19c1
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b34ad40b7ee8e083f53e18c34e65fa3c8699d352
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970119"
---
# <a name="step-7-sign-and-build-the-projects"></a><span data-ttu-id="cd1f9-102">步驟 7： 簽署和建置專案</span><span class="sxs-lookup"><span data-stu-id="cd1f9-102">Step 7: Sign and Build the Projects</span></span>
<span data-ttu-id="cd1f9-103">在此步驟中，您指派強式名稱，並建置專案以產生組件，其中包含您在中建立的資源 （結構描述）[步驟 6： 驗證結構描述](../../adapters-and-accelerators/accelerator-hl7/step-6-validate-the-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="cd1f9-103">In this step, you assign a strong name and build the project to generate an assembly that contains the resources (the schema) that you created in [Step 6: Validate the Schemas](../../adapters-and-accelerators/accelerator-hl7/step-6-validate-the-schemas.md).</span></span> <span data-ttu-id="cd1f9-104">這也可確保您到目前為止完成的工作中沒有任何編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="cd1f9-104">This also ensures that there are no compile errors in the work you have completed so far.</span></span>  
  
### <a name="to-sign-the-btahl7-project"></a><span data-ttu-id="cd1f9-105">BTAHL7 專案簽章</span><span class="sxs-lookup"><span data-stu-id="cd1f9-105">To sign the BTAHL7 Project</span></span>  
  
1.  <span data-ttu-id="cd1f9-106">在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7 專案**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="cd1f9-106">In Solution Explorer, right-click **BTAHL7 Project**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="cd1f9-107">在 [BTAHL7 專案屬性頁] 對話方塊中，按一下**組件**。</span><span class="sxs-lookup"><span data-stu-id="cd1f9-107">In the BTAHL7 Project Property Pages dialog box, click **Assembly**.</span></span>  
  
3.  <span data-ttu-id="cd1f9-108">在右窗格中，向下捲動至**強式名稱**區段中，按一下右邊的欄位**組件金鑰檔案**，然後按一下省略符號 （...） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="cd1f9-108">In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (…) button.</span></span>  
  
4.  <span data-ttu-id="cd1f9-109">在 [組件金鑰檔案] 對話方塊中，瀏覽至 **\<*磁碟機*\>: \Tutorial\BTAHL7V22Common\key.snk** (在中建立[步驟 3： 指派強式名稱組件](../../adapters-and-accelerators/accelerator-hl7/step-3-assign-a-strong-name-to-the-assembly.md))，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="cd1f9-109">In the Assembly Key File dialog box, browse to **\<*drive*\>:\Tutorial\BTAHL7V22Common\key.snk** (as created in [Step 3: Assign a Strong Name to the Assembly](../../adapters-and-accelerators/accelerator-hl7/step-3-assign-a-strong-name-to-the-assembly.md)), and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="cd1f9-110">按一下 **確定**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="cd1f9-110">Click **OK** to save changes.</span></span>  
  
### <a name="to-build-the-btahl7-project"></a><span data-ttu-id="cd1f9-111">若要建置 BTAHL7 專案</span><span class="sxs-lookup"><span data-stu-id="cd1f9-111">To build the BTAHL7 Project</span></span>  
  
- <span data-ttu-id="cd1f9-112">在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7 專案**，然後按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="cd1f9-112">In Solution Explorer, right-click **BTAHL7 Project**, and then click **Deploy**.</span></span> [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]<span data-ttu-id="cd1f9-113"> 編譯成 DLL 檔案的組件並儲存在\<*磁碟機*\>: \Tutorial\BTAHL7V22Common\Bin\Development 資料夾。</span><span class="sxs-lookup"><span data-stu-id="cd1f9-113"> compiles the assembly into a DLL file and saves it in the \<*drive*\>:\Tutorial\BTAHL7V22Common\Bin\Development folder.</span></span>  
  
  <span data-ttu-id="cd1f9-114">請繼續進行[步驟 8： 使用 BizTalk 對應工具建立對應](../../adapters-and-accelerators/accelerator-hl7/step-8-create-a-map-with-biztalk-mapper.md)。</span><span class="sxs-lookup"><span data-stu-id="cd1f9-114">Proceed to [Step 8: Create a Map with BizTalk Mapper](../../adapters-and-accelerators/accelerator-hl7/step-8-create-a-map-with-biztalk-mapper.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd1f9-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd1f9-115">See Also</span></span>  
 [<span data-ttu-id="cd1f9-116">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="cd1f9-116">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)