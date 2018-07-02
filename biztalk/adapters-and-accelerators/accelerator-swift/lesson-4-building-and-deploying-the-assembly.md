---
title: 第 4 課： 建置和部署組件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- building assemblies
- deploying, assemblies
- assemblies, building
- assemblies, deploying
ms.assetid: 58397c35-6048-4ac9-a8b8-a528dd1cb82a
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 867fe91ad0dd8dcb00c0293da08753f38e5005d6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988271"
---
# <a name="lesson-4-building-and-deploying-the-assembly"></a><span data-ttu-id="06dc4-102">第 4 課： 建置和部署組件</span><span class="sxs-lookup"><span data-stu-id="06dc4-102">Lesson 4: Building and Deploying the Assembly</span></span>
<span data-ttu-id="06dc4-103">在這一課，您可以建置並部署此專案以產生包含您在先前的課程中建立的結構描述的組件。</span><span class="sxs-lookup"><span data-stu-id="06dc4-103">In this lesson, you build and deploy the project to generate an assembly that contains the schemas you created in the previous lessons.</span></span> <span data-ttu-id="06dc4-104">此工作可確保您到目前為止所建立的工作中沒有任何編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="06dc4-104">This task ensures there are no compilation errors in the work you created so far.</span></span>  
  
 <span data-ttu-id="06dc4-105">部署組件會將組態資料庫中的組件的複本，並安裝到全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="06dc4-105">Deploying an assembly places a copy of the assembly in the Configuration database and installs it in the global assembly cache (GAC).</span></span> <span data-ttu-id="06dc4-106">在下列程序中，您將部署直接從 [方案總管]。</span><span class="sxs-lookup"><span data-stu-id="06dc4-106">In the following procedure, you deploy directly from Solution Explorer.</span></span>  
  
 <span data-ttu-id="06dc4-107">當專案編譯成組件 （DLL 檔案），Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]將儲存在 DLL \<*磁碟機*\>: \Program Files\\Microsoft BizTalk Accelerator for SWIFT\bin\在專案資料夾中的 [開發] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="06dc4-107">When the project compiles into an assembly (DLL file), Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] saves the DLL in the \<*drive*\>:\Program Files\\Microsoft  BizTalk Accelerator for SWIFT\bin\Development folder within the project folder.</span></span>  
  
### <a name="to-build-and-deploy-the-project"></a><span data-ttu-id="06dc4-108">建置和部署專案</span><span class="sxs-lookup"><span data-stu-id="06dc4-108">To build and deploy the project</span></span>  
  
1. <span data-ttu-id="06dc4-109">在 [方案總管] 中，以滑鼠右鍵按一下**SWIFTSchemas**，然後按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="06dc4-109">In Solution Explorer, right-click **SWIFTSchemas**, and then click **Build**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="06dc4-110">確認**建置成功**會出現在畫面左下角。</span><span class="sxs-lookup"><span data-stu-id="06dc4-110">Verify that **Build Succeeded** appears in the lower left-hand corner of the screen.</span></span> <span data-ttu-id="06dc4-111">在編譯過程中，您可能會看到一些狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="06dc4-111">During the compilation process, you may see some status messages.</span></span> <span data-ttu-id="06dc4-112">SWIFT 結構描述在處理時，這些訊息是正常的。</span><span class="sxs-lookup"><span data-stu-id="06dc4-112">These messages are normal when dealing with the SWIFT schemas.</span></span> <span data-ttu-id="06dc4-113">如果出現任何錯誤，請按一下 工具，然後按一下 BizTalk Server 管理，以開啟 BizTalk Server 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="06dc4-113">If any errors appear, click Tools, and then click BizTalk Server Administration to open the BizTalk Server Administration Console.</span></span> <span data-ttu-id="06dc4-114">在 BizTalk 管理主控台使用 「 事件檢視器 」 和健全狀況與活動追蹤 (HAT) 功能，若要更正錯誤並重建。</span><span class="sxs-lookup"><span data-stu-id="06dc4-114">Use the Event Viewer and the Health and Activity Tracking (HAT) feature in the BizTalk Administration Console to correct your errors and rebuild.</span></span>  
  
2. <span data-ttu-id="06dc4-115">使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至 **\<*磁碟機*\>: \labs\SWIFTProject\SWIFTSchemas\bin\Development**資料夾中，並確認**SWIFTSchemas.dll**檔案存在於這個資料夾中。</span><span class="sxs-lookup"><span data-stu-id="06dc4-115">Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the **\<*drive*\>:\labs\SWIFTProject\SWIFTSchemas\bin\Development** folder, and verify that the **SWIFTSchemas.dll** file exists in this folder.</span></span>  
  
3. <span data-ttu-id="06dc4-116">在 [方案總管] 中，以滑鼠右鍵按一下**SWIFTSchemas**，然後按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="06dc4-116">In Solution Explorer, right-click **SWIFTSchemas**, and then click **Deploy**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="06dc4-117">確認**部署成功**會出現在畫面的左下角。</span><span class="sxs-lookup"><span data-stu-id="06dc4-117">Verify that **Deploy Succeeded** appears in the lower left corner of the screen.</span></span>  
  
### <a name="to-confirm-deployment-success"></a><span data-ttu-id="06dc4-118">若要確認部署成功</span><span class="sxs-lookup"><span data-stu-id="06dc4-118">To confirm deployment success</span></span>  
  
1. <span data-ttu-id="06dc4-119">按一下 [**檢視**，然後按一下**BizTalk 總管] 中**。</span><span class="sxs-lookup"><span data-stu-id="06dc4-119">Click **View** and then click **BizTalk Explorer**.</span></span>  
  
2. <span data-ttu-id="06dc4-120">依序展開**組件**節點，並確認**SWIFTSchemas (1.0.0.0)** 出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="06dc4-120">Expand the **Assemblies** node and confirm that **SWIFTSchemas (1.0.0.0)** appears in the list.</span></span>  
  
    <span data-ttu-id="06dc4-121">如果 SWIFTSchemas 出現在清單中，組件已成功部署和可參考，並使用從其他[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="06dc4-121">If SWIFTSchemas appears in the list, the assembly deployed successfully and can be referenced and used from other [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projects.</span></span>  
  
   <span data-ttu-id="06dc4-122">請繼續進行[模組 3： 新增管線專案](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md)。</span><span class="sxs-lookup"><span data-stu-id="06dc4-122">Proceed to [Module 3: Adding a Pipeline Project](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md).</span></span>