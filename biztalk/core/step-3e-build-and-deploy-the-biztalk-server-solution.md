---
title: "步驟 3e： 建置和部署 BizTalk Server 解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbfc382b-ed4a-4401-9343-be1bffd747c9
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a970a8f7adb450156b89849eb986c84fd05ab55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3e-build-and-deploy-the-biztalk-server-solution"></a><span data-ttu-id="1fb70-102">步驟 3e： 建置和部署 BizTalk Server 解決方案</span><span class="sxs-lookup"><span data-stu-id="1fb70-102">Step 3e: Build and Deploy the BizTalk Server Solution</span></span>
<span data-ttu-id="1fb70-103">在本主題中，我們會將兩個部署[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案 (**BtsSalesforceIntegration**和**CustomPipeline**)，我們在先前步驟中建立。</span><span class="sxs-lookup"><span data-stu-id="1fb70-103">In this topic, we’ll deploy the two [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] projects (**BtsSalesforceIntegration** and **CustomPipeline**) that we created in the earlier steps.</span></span>  
  
### <a name="to-build-and-deploy-the-biztalk-server-projects"></a><span data-ttu-id="1fb70-104">若要建置和部署 BizTalk Server 專案</span><span class="sxs-lookup"><span data-stu-id="1fb70-104">To build and deploy the BizTalk Server projects</span></span>  
  
1.  <span data-ttu-id="1fb70-105">在 [方案總管] 中，以滑鼠右鍵按一下**BtsSalesforceIntegration** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="1fb70-105">In the Solution Explorer, right-click the **BtsSalesforceIntegration**[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="1fb70-106">在**部署**索引標籤上，針對**應用程式名稱**，輸入**SalesforceIntegration**。</span><span class="sxs-lookup"><span data-stu-id="1fb70-106">In the **Deployment** tab, for **Application Name**, enter **SalesforceIntegration**.</span></span> <span data-ttu-id="1fb70-107">按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="1fb70-107">Click **Save**.</span></span>  
  
3.  <span data-ttu-id="1fb70-108">同樣地，以滑鼠右鍵按一下**CustomPipeline** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案中，按一下 **屬性**，然後在**部署**索引標籤上，針對**應用程式名稱**屬性中，輸入**SalesforceIntegration**一次。</span><span class="sxs-lookup"><span data-stu-id="1fb70-108">Similarly, right-click the **CustomPipeline**[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project, click **Properties**, and in the **Deployment** tab, for the **Application Name** property, enter **SalesforceIntegration** again.</span></span> <span data-ttu-id="1fb70-109">按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="1fb70-109">Click **Save**.</span></span> <span data-ttu-id="1fb70-110">這可確保自訂管線元件會部署到相同的應用程式**BtsSalesforceIntegration**專案。</span><span class="sxs-lookup"><span data-stu-id="1fb70-110">This ensures that the custom pipeline component is deployed to the same application as the **BtsSalesforceIntegration** project.</span></span>  
  
4.  <span data-ttu-id="1fb70-111">以滑鼠右鍵按一下 [方案總管] 中的方案名稱，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="1fb70-111">Right-click the solution name in the Solution Explorer, and click **Properties**.</span></span> <span data-ttu-id="1fb70-112">在 [方案屬性頁] 對話方塊中，按一下**組態屬性**，並確認**建置**和**部署**核取方塊已選取的**BtsSalesforceIntegration**和**CustomPipeline**專案。</span><span class="sxs-lookup"><span data-stu-id="1fb70-112">In the Solution Property Pages dialog box, click **Configuration Properties**, and verify that the **Build** and **Deploy** check boxes are selected both for **BtsSalesforceIntegration** and **CustomPipeline** projects.</span></span>  
  
5.  <span data-ttu-id="1fb70-113">以滑鼠右鍵按一下 [方案總管] 中的方案名稱，然後按一下**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="1fb70-113">Right-click the solution name in the Solution Explorer and then click **Build Solution**.</span></span> <span data-ttu-id="1fb70-114">成功建置方案之後，再次以滑鼠右鍵按一下方案名稱，然後按一下**部署方案**。</span><span class="sxs-lookup"><span data-stu-id="1fb70-114">After the solution builds successfully, right-click the solution name again, and then click **Deploy Solution**.</span></span> <span data-ttu-id="1fb70-115">此方案部署到[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="1fb70-115">The solution is deployed to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fb70-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fb70-116">See Also</span></span>  
 [<span data-ttu-id="1fb70-117">步驟 3： 建立 Visual Studio 中的 BizTalk Server 解決方案</span><span class="sxs-lookup"><span data-stu-id="1fb70-117">Step 3: Create the BizTalk Server Solution in Visual Studio</span></span>](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)