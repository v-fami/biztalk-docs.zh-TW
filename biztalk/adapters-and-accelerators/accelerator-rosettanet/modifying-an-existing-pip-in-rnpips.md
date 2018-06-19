---
title: 修改 Rnpip 中的現有 PIP |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RNPIPs
- modifying, PIPs
- PIPs, modifying
- assemblies, RNPIPs
ms.assetid: f2ed25c4-1979-4691-9315-e7568e7cca8b
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce7f87d9af24e6388199e76e9cbf0eba076ceacf
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006287"
---
# <a name="modifying-an-existing-pip-in-rnpips"></a><span data-ttu-id="d231b-102">修改 Rnpip 中的現有 PIP</span><span class="sxs-lookup"><span data-stu-id="d231b-102">Modifying an Existing PIP in RNPIPs</span></span>
<span data-ttu-id="d231b-103">本主題描述如何變更和重新部署所安裝的交易夥伴介面程序 (PIP) 結構描述的其中一個[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]安裝程式。</span><span class="sxs-lookup"><span data-stu-id="d231b-103">This topic describes how to change and re-deploy one of the Partner Interface Process (PIP) schemas installed by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] setup.</span></span> <span data-ttu-id="d231b-104">您可將該結構描述部署為 RNPIP 組件的一部分。</span><span class="sxs-lookup"><span data-stu-id="d231b-104">You deploy the schema as part of the RNPIPs assembly.</span></span>  
  
### <a name="to-modify-an-existing-pip-in-rnpips"></a><span data-ttu-id="d231b-105">修改 RNPIP 中的現有 PIP</span><span class="sxs-lookup"><span data-stu-id="d231b-105">To modify an existing PIP in RNPIPs</span></span>  
  
1.  <span data-ttu-id="d231b-106">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d231b-106">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="d231b-107">找出\<*磁碟機*\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\Utilities\Schema Generator 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d231b-107">Locate the \<*drive*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\Utilities\Schema Generator folder.</span></span>  
  
3.  <span data-ttu-id="d231b-108">在命令提示字元中，輸入**CScript InstallDTD.vbs**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="d231b-108">At the command prompt, type **CScript InstallDTD.vbs**, and then press ENTER.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d231b-109">您只需要執行步驟 1 和 2 一次之後您安裝 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="d231b-109">You only have to do steps 1 and 2 one time after you install BizTalk Server.</span></span>  
  
4.  <span data-ttu-id="d231b-110">啟動**Microsoft Visual Studio 2012**。</span><span class="sxs-lookup"><span data-stu-id="d231b-110">Start **Microsoft Visual Studio 2012**.</span></span>  
  
5.  <span data-ttu-id="d231b-111">在**檔案**功能表上，指向**開啟**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="d231b-111">In the **File** menu, point to **Open**, and then click **Project**.</span></span>  
  
6.  <span data-ttu-id="d231b-112">在**開啟專案**對話方塊中，移至\<*磁碟機*\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\結構描述，然後選取**RNPIPs.btproj**。</span><span class="sxs-lookup"><span data-stu-id="d231b-112">In the **Open Project** dialog box, move to \<*drive*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\Schemas, and then select **RNPIPs.btproj**.</span></span>  
  
7.  <span data-ttu-id="d231b-113">在**檢視**功能表上，按一下  **BizTalk 總管**。</span><span class="sxs-lookup"><span data-stu-id="d231b-113">In the **View** menu, click **BizTalk Explorer**.</span></span> <span data-ttu-id="d231b-114">展開**組件**，然後以滑鼠右鍵按一下**microsoft.solutions.btarn.schemas.rnpips （3.3.0.0)**。</span><span class="sxs-lookup"><span data-stu-id="d231b-114">Expand **Assemblies**, and then right-click **Microsoft.Solutions.BTARN.Schemas.RNPIPs(3.3.0.0)**.</span></span> <span data-ttu-id="d231b-115">按一下**解除部署**。</span><span class="sxs-lookup"><span data-stu-id="d231b-115">Click **Undeploy**.</span></span>  
  
8.  <span data-ttu-id="d231b-116">啟動**Visual Studio 2012 的命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="d231b-116">Start **Visual Studio 2012 Command Prompt**.</span></span>  
  
9. <span data-ttu-id="d231b-117">移至的位置，在命令提示字元，輸入在步驟 6 中輸入**sn-k RNPIPs.snk**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="d231b-117">Move to the location entered in step 6, at the command prompt, type **sn -k RNPIPs.snk**, and then press **Enter**.</span></span>  
  
10. <span data-ttu-id="d231b-118">在 方案總管 中，以滑鼠右鍵按一下**Rnpip**，按一下 **屬性**，按一下 **通用屬性**，然後按一下 **組件。**</span><span class="sxs-lookup"><span data-stu-id="d231b-118">In Solution Explorer, right-click **RNPIPs**, click **Properties**, click **Common Properties**, and then click **Assembly.**</span></span>  
  
11. <span data-ttu-id="d231b-119">在右窗格中，向下捲動至**強式名稱**，請在**組件金鑰檔案**區段中，按一下省略符號按鈕 （...） 按鈕，移至在命令提示字元，輸入在步驟 6 中輸入的位置**RNPIPs.snk**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="d231b-119">In the right pane, scroll down to **Strong Name**, in the **Assembly Key File** section, click the ellipsis button (...) button, go to the location entered in step 6, at the command prompt, type **RNPIPs.snk**, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="d231b-120">在**屬性頁**對話方塊中，按一下 **組態屬性**，按一下 **部署**，按一下 **重新部署**，選取`True`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="d231b-120">In the **Property Pages** dialog box, click **Configuration Properties**, click **Deployment**, click **Redeploy**, select `True`, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="d231b-121">依需要編輯 RNPIP 中的任何現有結構描述。</span><span class="sxs-lookup"><span data-stu-id="d231b-121">Edit any of the existing schemas in RNPIPs, as required.</span></span>  
  
14. <span data-ttu-id="d231b-122">按一下**檔案**，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="d231b-122">Click **File**, and then click **Save**.</span></span>  
  
15. <span data-ttu-id="d231b-123">以滑鼠右鍵按一下專案名稱，然後**建置**。</span><span class="sxs-lookup"><span data-stu-id="d231b-123">Right-click the project name, and then click **Build**.</span></span>  
  
16. <span data-ttu-id="d231b-124">以滑鼠右鍵按一下專案名稱，然後**部署**。</span><span class="sxs-lookup"><span data-stu-id="d231b-124">Right-click the project name, and then click **Deploy**.</span></span>  
  
17. <span data-ttu-id="d231b-125">按一下**啟動**，指向 **所有程式**，指向  **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="d231b-125">Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
18. <span data-ttu-id="d231b-126">在 BizTalk 管理主控台中，依序展開**Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **（本機）**，然後展開**主機**。</span><span class="sxs-lookup"><span data-stu-id="d231b-126">In BizTalk Administration Console, expand **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **(Local)**, and then expand **Hosts**.</span></span>  
  
19. <span data-ttu-id="d231b-127">在右窗格中，主機名稱上按一下滑鼠右鍵，然後按一下 **停止**。</span><span class="sxs-lookup"><span data-stu-id="d231b-127">In the right pane, right-click the name of the host, and then click **Stop**.</span></span> <span data-ttu-id="d231b-128">服務已停止之後，以滑鼠右鍵按一下主控件名稱，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="d231b-128">After the service has stopped, right-click the name of the host, and then click **Start**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d231b-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="d231b-129">See Also</span></span>  
 <span data-ttu-id="d231b-130">[程式設計手冊](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md) </span><span class="sxs-lookup"><span data-stu-id="d231b-130">[Programming Guide](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md) </span></span>  
 [<span data-ttu-id="d231b-131">整合新的交易夥伴介面程序</span><span class="sxs-lookup"><span data-stu-id="d231b-131">Incorporating a New Partner Interface Process</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md)