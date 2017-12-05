---
title: "方案組建組態 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Configuration Manager
- building, solutions
- building, Configuration Manager
- solutions, deploying
- deploying, building
- solutions, developing
- solutions, build configuration
ms.assetid: 6f2cce47-388d-4c93-9146-768f53b8207e
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c48791d26842b7224bb950334d6b184452a54d6
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="solution-build-configurations"></a><span data-ttu-id="f6183-102">方案建置組態</span><span class="sxs-lookup"><span data-stu-id="f6183-102">Solution Build Configurations</span></span>
<span data-ttu-id="f6183-103">如同您在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中所建置的其他專案一樣，您可以使用「組態管理員」以指定方案建置組態。</span><span class="sxs-lookup"><span data-stu-id="f6183-103">As with other projects that you build in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], you can use Configuration Manager to specify solution build configurations.</span></span> <span data-ttu-id="f6183-104">方案組建組態可讓您決定哪些專案来包含在建置方案的如果將部署。</span><span class="sxs-lookup"><span data-stu-id="f6183-104">Solution build configurations enable you to determine which projects to include in builds of a solution and if they will be deployed.</span></span> <span data-ttu-id="f6183-105">BizTalk Server 支援**偵錯**和**發行**組建組態。</span><span class="sxs-lookup"><span data-stu-id="f6183-105">BizTalk Server supports both **Debug** and **Release** build configurations.</span></span>  
  
 <span data-ttu-id="f6183-106">方案建置組態中的核取記號**建置**資料行可讓您建置方案，以及當您完成時產生組件。</span><span class="sxs-lookup"><span data-stu-id="f6183-106">A solution build configuration with a check mark in the **Build** column enables you to build a solution and to generate an assembly when you are finished.</span></span> <span data-ttu-id="f6183-107">如果核取記號也會出現在**部署**資料行，則應用程式將會部署專案設計工具中的部署設定所決定。</span><span class="sxs-lookup"><span data-stu-id="f6183-107">If a check mark is also present in the **Deploy** column, then the application will be deployed based on deployment settings in the Project Designer.</span></span>  
  
 <span data-ttu-id="f6183-108">Configuration Manager 和組態的完整參考選項提供由對話方塊方塊中，請參閱下列參考連結： [http://go.microsoft.com/fwlink/?LinkId=125365](http://go.microsoft.com/fwlink/?LinkId=125365)。</span><span class="sxs-lookup"><span data-stu-id="f6183-108">A complete reference to Configuration Manager and the configuration options provided by the dialog box can be found at the following reference link: [http://go.microsoft.com/fwlink/?LinkId=125365](http://go.microsoft.com/fwlink/?LinkId=125365).</span></span>  
  
### <a name="to-configure-build-properties-in-configuration-manager"></a><span data-ttu-id="f6183-109">在組態管理員中設定建置屬性</span><span class="sxs-lookup"><span data-stu-id="f6183-109">To configure build properties in Configuration Manager</span></span>  
  
1.  <span data-ttu-id="f6183-110">按一下 [ **建置** ] 功能表上的 [ **組態管理員**]。</span><span class="sxs-lookup"><span data-stu-id="f6183-110">On the **Build** menu, click **Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="f6183-111">在**Configuration Manager**對話方塊中，選取其中一個下列命令來設定建置屬性。</span><span class="sxs-lookup"><span data-stu-id="f6183-111">In the **Configuration Manager** dialog box, select one of following to configure the build properties.</span></span>  
  
    |<span data-ttu-id="f6183-112">使用</span><span class="sxs-lookup"><span data-stu-id="f6183-112">Use this</span></span>|<span data-ttu-id="f6183-113">動作</span><span class="sxs-lookup"><span data-stu-id="f6183-113">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="f6183-114">**Configuration**</span><span class="sxs-lookup"><span data-stu-id="f6183-114">**Configuration**</span></span>|<span data-ttu-id="f6183-115">選擇從**發行**或**偵錯**專案的組態。</span><span class="sxs-lookup"><span data-stu-id="f6183-115">Choose from **Release** or **Debug** configurations for the project.</span></span> <span data-ttu-id="f6183-116">或者，建立新的組態或編輯現有的組態。</span><span class="sxs-lookup"><span data-stu-id="f6183-116">Alternatively, create a new configuration or edit an existing one.</span></span>|  
    |<span data-ttu-id="f6183-117">**平台**</span><span class="sxs-lookup"><span data-stu-id="f6183-117">**Platform**</span></span>|<span data-ttu-id="f6183-118">為專案選擇代表編譯後組件之 CPU 架構的平台。</span><span class="sxs-lookup"><span data-stu-id="f6183-118">Choose a platform for the project representing the CPU architecture of the compiled assembly.</span></span> <span data-ttu-id="f6183-119">或者，建立新的平台，或編輯現有。</span><span class="sxs-lookup"><span data-stu-id="f6183-119">Alternatively, create a new platform or edit an existing one.</span></span>|  
    |<span data-ttu-id="f6183-120">**建置**</span><span class="sxs-lookup"><span data-stu-id="f6183-120">**Build**</span></span>|<span data-ttu-id="f6183-121">針對專案核取此欄位的方塊，以建置或重新建置專案來回應方案的建置命令。</span><span class="sxs-lookup"><span data-stu-id="f6183-121">Check the box in this column for a project to have the project built or rebuilt in response to a build command for the solution.</span></span>|  
    |<span data-ttu-id="f6183-122">**部署**</span><span class="sxs-lookup"><span data-stu-id="f6183-122">**Deploy**</span></span>|<span data-ttu-id="f6183-123">針對方案或專案發出建置命令後，核取此欄位的方塊以依據部署設定來部署專案。</span><span class="sxs-lookup"><span data-stu-id="f6183-123">Check the box in this column to have the project deployed based on deployment settings when a build command is issued for the solution or project.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f6183-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="f6183-124">See Also</span></span>  
 <span data-ttu-id="f6183-125">[如何部署 BizTalk 組件從 Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="f6183-125">[How to Deploy a BizTalk Assembly from Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md) </span></span>  
 [<span data-ttu-id="f6183-126">如何建立 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="f6183-126">How to Create BizTalk Projects</span></span>](../core/how-to-create-biztalk-projects.md)