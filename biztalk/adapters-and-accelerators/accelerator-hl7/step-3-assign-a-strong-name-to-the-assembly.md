---
title: "步驟 3： 指派強式名稱組件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies
- message enrichment tutorial, strong name assemblies
- strong name assemblies
ms.assetid: 8709e4e1-b428-42af-ba3c-08225c17a9eb
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85c8b74a40ee5a3e265e68197c97b1d9560daffe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-assign-a-strong-name-to-the-assembly"></a><span data-ttu-id="8352d-102">步驟 3： 指派強式名稱組件</span><span class="sxs-lookup"><span data-stu-id="8352d-102">Step 3: Assign a Strong Name to the Assembly</span></span>
<span data-ttu-id="8352d-103">在此步驟中，建立並指派強式名稱[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]組件。</span><span class="sxs-lookup"><span data-stu-id="8352d-103">In this step, you create and assign a strong name for the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] assembly.</span></span> <span data-ttu-id="8352d-104">強式名稱組件提供數個安全性優點，才能部署您的專案在全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="8352d-104">A strong-named assembly provides several security benefits and is required in order to deploy your project in the global assembly cache (GAC).</span></span> <span data-ttu-id="8352d-105">強式名稱可保證組件的唯一性，藉由指派數位簽章和唯一的索引鍵組合。</span><span class="sxs-lookup"><span data-stu-id="8352d-105">A strong name guarantees the uniqueness of the assembly by assigning a digital signature and a unique key pair.</span></span> <span data-ttu-id="8352d-106">這也會保護方法是確保沒有人可以產生後續版本的組件的組件的歷程。</span><span class="sxs-lookup"><span data-stu-id="8352d-106">This also protects the lineage of the assembly by ensuring that no one can generate a subsequent version of the assembly.</span></span> <span data-ttu-id="8352d-107">最後，強式名稱提供強式的完整性檢查，以保證組件的內容有不會變更建置它之後。</span><span class="sxs-lookup"><span data-stu-id="8352d-107">Lastly, a strong name provides a strong integrity check to guarantee that the contents of the assembly have not changed since you built it.</span></span>  
  
### <a name="to-assign-a-strong-name-to-the-assembly"></a><span data-ttu-id="8352d-108">若要指派強式名稱組件</span><span class="sxs-lookup"><span data-stu-id="8352d-108">To assign a strong name to the assembly</span></span>  
  
1.  <span data-ttu-id="8352d-109">啟動**[!INCLUDE[vs2012](../../includes/vs2012-md.md)]命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="8352d-109">Start **[!INCLUDE[vs2012](../../includes/vs2012-md.md)] Command Prompt**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8352d-110">如果您已經建立強式名稱金鑰，您可以重複使用。</span><span class="sxs-lookup"><span data-stu-id="8352d-110">If you have already created a strong name key, you can reuse it.</span></span>  
  
2.  <span data-ttu-id="8352d-111">在命令提示字元中，移至**\<*磁碟機*>: \Tutorial\BTAHL7V22Common** (其中\<*磁碟機*> 是安裝磁碟機字母），然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="8352d-111">At the command prompt, move to**\<*drive*>:\Tutorial\BTAHL7V22Common** (where \<*drive*> is your installation drive letter) and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="8352d-112">在命令提示字元中，輸入**sn – k key.snk**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="8352d-112">At the command prompt, type **sn –k key.snk**, and then press **Enter**.</span></span> <span data-ttu-id="8352d-113">出現訊息指出，[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]金鑰組寫入金鑰檔 key.snk。</span><span class="sxs-lookup"><span data-stu-id="8352d-113">A message appears indicating that [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] wrote the key pair to the key file key.snk.</span></span>  
  
4.  <span data-ttu-id="8352d-114">在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7V22Common**專案，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="8352d-114">In Solution Explorer, right-click the **BTAHL7V22Common** project, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="8352d-115">在 [BTAHL7V22Common 屬性頁] 對話方塊中，按一下**組件**。</span><span class="sxs-lookup"><span data-stu-id="8352d-115">In the BTAHL7V22Common Property Pages dialog box, click **Assembly**.</span></span>  
  
6.  <span data-ttu-id="8352d-116">在右窗格中，向下捲動至**強式名稱**區段中，按一下右邊的欄位**組件金鑰檔案**，然後按一下省略符號 （...） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="8352d-116">In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (…) button.</span></span>  
  
7.  <span data-ttu-id="8352d-117">在 組件金鑰檔案 對話方塊中，瀏覽至  **\<*磁碟機*>: \Tutorial\BTAHL7V22Common\key.snk**，按一下 **開啟**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="8352d-117">In the Assembly Key File dialog box, browse to **\<*drive*>:\Tutorial\BTAHL7V22Common\key.snk**, click **Open**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="8352d-118">在 方案總管 中，以滑鼠右鍵按一下**BTAHL7V22Common**，然後按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="8352d-118">In Solution Explorer, right-click **BTAHL7V22Common**, and then click **Deploy**.</span></span> [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="8352d-119">建立您可以從下一個專案參考的組件。</span><span class="sxs-lookup"><span data-stu-id="8352d-119"> creates an assembly that you can reference from your next project.</span></span>  
  
9. <span data-ttu-id="8352d-120">Btahl7v2xc 通用專案重複步驟 4 到 8。</span><span class="sxs-lookup"><span data-stu-id="8352d-120">Repeat steps 4 through 8 for the BTAHL7V2XCommon project.</span></span>  
  
 <span data-ttu-id="8352d-121">若要繼續[步驟 4： 建立結構描述](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="8352d-121">Proceed to [Step 4: Create the Schemas](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-schemas.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8352d-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8352d-122">See Also</span></span>  
 [<span data-ttu-id="8352d-123">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="8352d-123">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)