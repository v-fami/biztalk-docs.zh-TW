---
title: 步驟 8： 建置與部署 Contoso 協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- private process tutorial, building solutions
- private process tutorial, deploying solutions
ms.assetid: d350b87a-0e4e-4837-ad39-fb5b1fdc1532
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 706c5ab2b52d30aeedfba7b3e002dc637fcece93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209302"
---
# <a name="step-8-building-and-deploying-the-contoso-orchestration"></a><span data-ttu-id="73f91-102">步驟 8： 建置與部署 Contoso 協調流程</span><span class="sxs-lookup"><span data-stu-id="73f91-102">Step 8: Building and Deploying the Contoso Orchestration</span></span>
<span data-ttu-id="73f91-103">在此步驟中，您將建置協調流程專案，並使用「BizTalk 部署精靈」部署專案。</span><span class="sxs-lookup"><span data-stu-id="73f91-103">In this step, you build the Orchestration project and deploy it using the BizTalk Deployment Wizard.</span></span> <span data-ttu-id="73f91-104">這會將組件加入至組態資料庫，並將組件安裝到全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="73f91-104">This adds the assembly to the Configuration database and installs the assembly in the Global Assembly Cache (GAC).</span></span>  
  
### <a name="to-assign-a-strong-name-to-your-assembly"></a><span data-ttu-id="73f91-105">指派強式名稱給組件</span><span class="sxs-lookup"><span data-stu-id="73f91-105">To assign a strong name to your assembly</span></span>  
  
1.  <span data-ttu-id="73f91-106">在 [方案總管] 中，以滑鼠右鍵按一下**PrivateResponder**專案，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="73f91-106">In Solution Explorer, right-click the **PrivateResponder** project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="73f91-107">在 [PrivateResponder 屬性頁] 對話方塊中，選取**組件**從左窗格。</span><span class="sxs-lookup"><span data-stu-id="73f91-107">In the PrivateResponder Property Pages dialog box, select **Assembly** from the left pane.</span></span>  
  
3.  <span data-ttu-id="73f91-108">在右窗格中，向下捲動至**強式名稱**區段中，按一下右邊的欄位**組件金鑰檔案**，然後按一下省略符號按鈕 (**...**).</span><span class="sxs-lookup"><span data-stu-id="73f91-108">In the right pane, scroll down to the **Strong name** section, click the field to the right of the **Assembly Key File**, and then click the ellipsis button (**…**).</span></span>  
  
4.  <span data-ttu-id="73f91-109">找出您的專案資料夾中，選取**FabConPriceAvail.snk**檔案，然後再按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="73f91-109">Locate your project folder, select the **FabConPriceAvail.snk** file, and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="73f91-110">在右窗格中，選取**False**從**組件延遲簽章**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="73f91-110">In the right pane, select **False** from the **Assembly Delay Sign** drop down list.</span></span>  
  
6.  <span data-ttu-id="73f91-111">按一下**確定**儲存的變更。</span><span class="sxs-lookup"><span data-stu-id="73f91-111">Click **OK** to save the changes.</span></span>  
  
### <a name="to-build-and-deploy-the-orchestration-project"></a><span data-ttu-id="73f91-112">建置與部署協調流程專案</span><span class="sxs-lookup"><span data-stu-id="73f91-112">To build and deploy the orchestration project</span></span>  
  
1.  <span data-ttu-id="73f91-113">在 [方案總管] 中，以滑鼠右鍵按一下**PrivateResponder**專案，然後再按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="73f91-113">In Solution Explorer, right-click the **PrivateResponder** project, and then click **Build**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="73f91-114">您可以放心忽略在建置過程中出現的任何警告。</span><span class="sxs-lookup"><span data-stu-id="73f91-114">You can safely ignore any warnings that occur during the build process.</span></span>  
  
2.  <span data-ttu-id="73f91-115">建置成功之後，以滑鼠右鍵按一下專案，然後**部署**。</span><span class="sxs-lookup"><span data-stu-id="73f91-115">After the build has succeeded, right-click the project again, and then click **Deploy**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73f91-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73f91-116">See Also</span></span>  
 [<span data-ttu-id="73f91-117">步驟 9： 啟動 Contoso 協調流程</span><span class="sxs-lookup"><span data-stu-id="73f91-117">Step 9: Starting the Contoso Orchestration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-9-starting-the-contoso-orchestration.md)