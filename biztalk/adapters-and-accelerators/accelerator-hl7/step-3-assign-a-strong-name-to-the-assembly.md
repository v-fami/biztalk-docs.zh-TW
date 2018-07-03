---
title: 步驟 3： 指派強式名稱組件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- assemblies
- message enrichment tutorial, strong name assemblies
- strong name assemblies
ms.assetid: 8709e4e1-b428-42af-ba3c-08225c17a9eb
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 591423d04d8551620036e94a6ec780271e04feec
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012623"
---
# <a name="step-3-assign-a-strong-name-to-the-assembly"></a><span data-ttu-id="c543a-102">步驟 3： 指派強式名稱組件</span><span class="sxs-lookup"><span data-stu-id="c543a-102">Step 3: Assign a Strong Name to the Assembly</span></span>
<span data-ttu-id="c543a-103">在此步驟中，建立並指派的強式名稱[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]組件。</span><span class="sxs-lookup"><span data-stu-id="c543a-103">In this step, you create and assign a strong name for the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] assembly.</span></span> <span data-ttu-id="c543a-104">強式名稱組件提供數個安全性優點，也不需要為了部署您的專案在全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="c543a-104">A strong-named assembly provides several security benefits and is required in order to deploy your project in the global assembly cache (GAC).</span></span> <span data-ttu-id="c543a-105">強式名稱可保證唯一性的組件，藉由指派數位簽章和唯一的金鑰組。</span><span class="sxs-lookup"><span data-stu-id="c543a-105">A strong name guarantees the uniqueness of the assembly by assigning a digital signature and a unique key pair.</span></span> <span data-ttu-id="c543a-106">這也會保護確保沒有人可以產生組件的後續版本的組件的歷程。</span><span class="sxs-lookup"><span data-stu-id="c543a-106">This also protects the lineage of the assembly by ensuring that no one can generate a subsequent version of the assembly.</span></span> <span data-ttu-id="c543a-107">最後，強式名稱提供強式的完整性檢查，以確保建置它之後，已不會變更組件的內容。</span><span class="sxs-lookup"><span data-stu-id="c543a-107">Lastly, a strong name provides a strong integrity check to guarantee that the contents of the assembly have not changed since you built it.</span></span>  
  
### <a name="to-assign-a-strong-name-to-the-assembly"></a><span data-ttu-id="c543a-108">若要指派強式名稱組件</span><span class="sxs-lookup"><span data-stu-id="c543a-108">To assign a strong name to the assembly</span></span>  
  
1. <span data-ttu-id="c543a-109">開始**Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="c543a-109">Start **Visual Studio Command Prompt**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="c543a-110">如果您已經建立強式名稱金鑰，您可以重複使用。</span><span class="sxs-lookup"><span data-stu-id="c543a-110">If you have already created a strong name key, you can reuse it.</span></span>  
  
2. <span data-ttu-id="c543a-111">在命令提示字元中，移至<strong>\<*磁碟機*\>: \Tutorial\BTAHL7V22Common</strong> (其中\<*磁碟機*\>是安裝磁碟機代號），然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="c543a-111">At the command prompt, move to<strong>\<*drive*\>:\Tutorial\BTAHL7V22Common</strong> (where \<*drive*\> is your installation drive letter) and then press **Enter**.</span></span>  
  
3. <span data-ttu-id="c543a-112">在命令提示字元中，輸入**sn – k key.snk**，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="c543a-112">At the command prompt, type **sn –k key.snk**, and then press **Enter**.</span></span> <span data-ttu-id="c543a-113">出現訊息指出，[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]金鑰組寫入金鑰檔 key.snk。</span><span class="sxs-lookup"><span data-stu-id="c543a-113">A message appears indicating that [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] wrote the key pair to the key file key.snk.</span></span>  
  
4. <span data-ttu-id="c543a-114">在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7V22Common**專案，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="c543a-114">In Solution Explorer, right-click the **BTAHL7V22Common** project, and then click **Properties**.</span></span>  
  
5. <span data-ttu-id="c543a-115">在 [BTAHL7V22Common 屬性頁] 對話方塊中，按一下**組件**。</span><span class="sxs-lookup"><span data-stu-id="c543a-115">In the BTAHL7V22Common Property Pages dialog box, click **Assembly**.</span></span>  
  
6. <span data-ttu-id="c543a-116">在右窗格中，向下捲動至**強式名稱**區段中，按一下右邊的欄位**組件金鑰檔案**，然後按一下省略符號 （...） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c543a-116">In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (…) button.</span></span>  
  
7. <span data-ttu-id="c543a-117">在 組件金鑰檔案 對話方塊中，瀏覽至 **\<*磁碟機*\>: \Tutorial\BTAHL7V22Common\key.snk**，按一下 **開啟**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c543a-117">In the Assembly Key File dialog box, browse to **\<*drive*\>:\Tutorial\BTAHL7V22Common\key.snk**, click **Open**, and then click **OK**.</span></span>  
  
8. <span data-ttu-id="c543a-118">在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7V22Common**，然後按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="c543a-118">In Solution Explorer, right-click **BTAHL7V22Common**, and then click **Deploy**.</span></span> [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="c543a-119"> 建立您可以從下一個專案參考的組件。</span><span class="sxs-lookup"><span data-stu-id="c543a-119"> creates an assembly that you can reference from your next project.</span></span>  
  
9. <span data-ttu-id="c543a-120">Btahl7v2xc 通用專案重複步驟 4 到 8。</span><span class="sxs-lookup"><span data-stu-id="c543a-120">Repeat steps 4 through 8 for the BTAHL7V2XCommon project.</span></span>  
  
   <span data-ttu-id="c543a-121">請繼續進行[步驟 4： 建立結構描述](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="c543a-121">Proceed to [Step 4: Create the Schemas](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-schemas.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c543a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c543a-122">See Also</span></span>  
 [<span data-ttu-id="c543a-123">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="c543a-123">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)