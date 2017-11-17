---
title: "第 4 課： 建立和部署組件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- building assemblies
- deploying, assemblies
- assemblies, building
- assemblies, deploying
ms.assetid: 58397c35-6048-4ac9-a8b8-a528dd1cb82a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5521b5921dbfcc3c8a3c5916fc4d4a2dc96eebbd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-4-building-and-deploying-the-assembly"></a><span data-ttu-id="240ec-102">第 4 課： 建立和部署組件</span><span class="sxs-lookup"><span data-stu-id="240ec-102">Lesson 4: Building and Deploying the Assembly</span></span>
<span data-ttu-id="240ec-103">在這一課，您會建置並部署此專案以產生包含您在先前的課程中建立的結構描述的組件。</span><span class="sxs-lookup"><span data-stu-id="240ec-103">In this lesson, you build and deploy the project to generate an assembly that contains the schemas you created in the previous lessons.</span></span> <span data-ttu-id="240ec-104">這項工作可確保您到目前為止所建立的工作中沒有編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="240ec-104">This task ensures there are no compilation errors in the work you created so far.</span></span>  
  
 <span data-ttu-id="240ec-105">部署組件的組件的複本置於組態資料庫，並將它安裝在全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="240ec-105">Deploying an assembly places a copy of the assembly in the Configuration database and installs it in the global assembly cache (GAC).</span></span> <span data-ttu-id="240ec-106">在下列程序中，您將部署直接從 [方案總管]。</span><span class="sxs-lookup"><span data-stu-id="240ec-106">In the following procedure, you deploy directly from Solution Explorer.</span></span>  
  
 <span data-ttu-id="240ec-107">當專案編譯成組件 （DLL 檔案）， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]將儲存在 DLL \<*磁碟機*>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for SWIFT\bin\在專案資料夾中的開發資料夾。</span><span class="sxs-lookup"><span data-stu-id="240ec-107">When the project compiles into an assembly (DLL file), [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] saves the DLL in the \<*drive*>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for SWIFT\bin\Development folder within the project folder.</span></span>  
  
### <a name="to-build-and-deploy-the-project"></a><span data-ttu-id="240ec-108">建置和部署專案</span><span class="sxs-lookup"><span data-stu-id="240ec-108">To build and deploy the project</span></span>  
  
1.  <span data-ttu-id="240ec-109">在 方案總管 中，以滑鼠右鍵按一下**SWIFTSchemas**，然後按一下 **建置**。</span><span class="sxs-lookup"><span data-stu-id="240ec-109">In Solution Explorer, right-click **SWIFTSchemas**, and then click **Build**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="240ec-110">確認**建置成功**會出現在畫面左下角。</span><span class="sxs-lookup"><span data-stu-id="240ec-110">Verify that **Build Succeeded** appears in the lower left-hand corner of the screen.</span></span> <span data-ttu-id="240ec-111">在編譯過程中，您可能會看到某些狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="240ec-111">During the compilation process, you may see some status messages.</span></span> <span data-ttu-id="240ec-112">這些訊息都是正常的處理 SWIFT 的結構描述時。</span><span class="sxs-lookup"><span data-stu-id="240ec-112">These messages are normal when dealing with the SWIFT schemas.</span></span> <span data-ttu-id="240ec-113">如果出現任何錯誤，請按一下 工具，然後按一下 BizTalk Server 管理 以開啟 BizTalk Server 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="240ec-113">If any errors appear, click Tools, and then click BizTalk Server Administration to open the BizTalk Server Administration Console.</span></span> <span data-ttu-id="240ec-114">使用事件檢視器和健全狀況與活動追蹤 (HAT) 中的功能 BizTalk 管理主控台來更正錯誤，然後再重建。</span><span class="sxs-lookup"><span data-stu-id="240ec-114">Use the Event Viewer and the Health and Activity Tracking (HAT) feature in the BizTalk Administration Console to correct your errors and rebuild.</span></span>  
  
2.  <span data-ttu-id="240ec-115">使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至  **\<*磁碟機*>: \labs\SWIFTProject\SWIFTSchemas\bin\Development** 資料夾，並確認**SWIFTSchemas.dll**檔案位於此資料夾。</span><span class="sxs-lookup"><span data-stu-id="240ec-115">Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the **\<*drive*>:\labs\SWIFTProject\SWIFTSchemas\bin\Development** folder, and verify that the **SWIFTSchemas.dll** file exists in this folder.</span></span>  
  
3.  <span data-ttu-id="240ec-116">在 方案總管 中，以滑鼠右鍵按一下**SWIFTSchemas**，然後按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="240ec-116">In Solution Explorer, right-click **SWIFTSchemas**, and then click **Deploy**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="240ec-117">確認**部署成功**會出現在畫面左下角。</span><span class="sxs-lookup"><span data-stu-id="240ec-117">Verify that **Deploy Succeeded** appears in the lower left corner of the screen.</span></span>  
  
### <a name="to-confirm-deployment-success"></a><span data-ttu-id="240ec-118">若要確認部署成功</span><span class="sxs-lookup"><span data-stu-id="240ec-118">To confirm deployment success</span></span>  
  
1.  <span data-ttu-id="240ec-119">按一下**檢視**，然後按一下  **BizTalk 總管**。</span><span class="sxs-lookup"><span data-stu-id="240ec-119">Click **View** and then click **BizTalk Explorer**.</span></span>  
  
2.  <span data-ttu-id="240ec-120">展開**組件**節點，並確認**SWIFTSchemas (1.0.0.0)**出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="240ec-120">Expand the **Assemblies** node and confirm that **SWIFTSchemas (1.0.0.0)** appears in the list.</span></span>  
  
     <span data-ttu-id="240ec-121">如果 SWIFTSchemas 出現在清單中，組件已成功部署和可參考，並使用從其他[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="240ec-121">If SWIFTSchemas appears in the list, the assembly deployed successfully and can be referenced and used from other [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projects.</span></span>  
  
 <span data-ttu-id="240ec-122">若要繼續[模組 3： 新增管線專案](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md)。</span><span class="sxs-lookup"><span data-stu-id="240ec-122">Proceed to [Module 3: Adding a Pipeline Project](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md).</span></span>