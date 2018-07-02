---
title: 步驟 3e： 建置和部署 BizTalk Server 解決方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bbfc382b-ed4a-4401-9343-be1bffd747c9
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: abe1a747057852bae5d404ccfb3272ca9712948b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969095"
---
# <a name="step-3e-build-and-deploy-the-biztalk-server-solution"></a><span data-ttu-id="dd43d-102">步驟 3e： 建置和部署 BizTalk Server 解決方案</span><span class="sxs-lookup"><span data-stu-id="dd43d-102">Step 3e: Build and Deploy the BizTalk Server Solution</span></span>
<span data-ttu-id="dd43d-103">本主題中，我們會將部署兩個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案 (**BtsSalesforceIntegration**並**CustomPipeline**) 我們在先前步驟中建立。</span><span class="sxs-lookup"><span data-stu-id="dd43d-103">In this topic, we’ll deploy the two [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] projects (**BtsSalesforceIntegration** and **CustomPipeline**) that we created in the earlier steps.</span></span>  
  
### <a name="to-build-and-deploy-the-biztalk-server-projects"></a><span data-ttu-id="dd43d-104">若要建置和部署 BizTalk Server 專案</span><span class="sxs-lookup"><span data-stu-id="dd43d-104">To build and deploy the BizTalk Server projects</span></span>  
  
1. <span data-ttu-id="dd43d-105">在 [方案總管] 中，以滑鼠右鍵按一下**BtsSalesforceIntegration** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="dd43d-105">In the Solution Explorer, right-click the **BtsSalesforceIntegration**[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="dd43d-106">在 **部署**索引標籤上，如**應用程式名稱**，輸入**SalesforceIntegration**。</span><span class="sxs-lookup"><span data-stu-id="dd43d-106">In the **Deployment** tab, for **Application Name**, enter **SalesforceIntegration**.</span></span> <span data-ttu-id="dd43d-107">按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="dd43d-107">Click **Save**.</span></span>  
  
3. <span data-ttu-id="dd43d-108">同樣地，以滑鼠右鍵按一下**CustomPipeline** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案中，按一下 **屬性**，然後在**部署**索引標籤上，針對**應用程式名稱**屬性中，輸入**SalesforceIntegration**一次。</span><span class="sxs-lookup"><span data-stu-id="dd43d-108">Similarly, right-click the **CustomPipeline**[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project, click **Properties**, and in the **Deployment** tab, for the **Application Name** property, enter **SalesforceIntegration** again.</span></span> <span data-ttu-id="dd43d-109">按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="dd43d-109">Click **Save**.</span></span> <span data-ttu-id="dd43d-110">這可確保將自訂管線元件會部署到相同的應用程式**BtsSalesforceIntegration**專案。</span><span class="sxs-lookup"><span data-stu-id="dd43d-110">This ensures that the custom pipeline component is deployed to the same application as the **BtsSalesforceIntegration** project.</span></span>  
  
4. <span data-ttu-id="dd43d-111">以滑鼠右鍵按一下 方案總管 中的方案名稱，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="dd43d-111">Right-click the solution name in the Solution Explorer, and click **Properties**.</span></span> <span data-ttu-id="dd43d-112">在 [方案屬性頁] 對話方塊中，按一下**組態屬性**，並確認**建置**並**部署**核取方塊已選取兩者**BtsSalesforceIntegration**並**CustomPipeline**專案。</span><span class="sxs-lookup"><span data-stu-id="dd43d-112">In the Solution Property Pages dialog box, click **Configuration Properties**, and verify that the **Build** and **Deploy** check boxes are selected both for **BtsSalesforceIntegration** and **CustomPipeline** projects.</span></span>  
  
5. <span data-ttu-id="dd43d-113">以滑鼠右鍵按一下 [方案總管] 中的方案名稱，然後按一下**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="dd43d-113">Right-click the solution name in the Solution Explorer and then click **Build Solution**.</span></span> <span data-ttu-id="dd43d-114">方案建置完成之後，以滑鼠右鍵按一下方案名稱，然後**部署方案**。</span><span class="sxs-lookup"><span data-stu-id="dd43d-114">After the solution builds successfully, right-click the solution name again, and then click **Deploy Solution**.</span></span> <span data-ttu-id="dd43d-115">若要部署解決方案[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="dd43d-115">The solution is deployed to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd43d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd43d-116">See Also</span></span>  
 [<span data-ttu-id="dd43d-117">步驟 3：在 Visual Studio 中建立 BizTalk Server 解決方案</span><span class="sxs-lookup"><span data-stu-id="dd43d-117">Step 3: Create the BizTalk Server Solution in Visual Studio</span></span>](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)