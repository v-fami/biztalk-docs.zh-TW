---
title: 如何建立 BizTalk 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, projects
- projects, creating
- solutions
- solutions, adding projects
ms.assetid: a6900234-f989-4601-96c5-41d435c2f8b4
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 878e9c4900b24fbd61ccdd570fac2cbf02db02ad
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989799"
---
# <a name="how-to-create-biztalk-projects"></a><span data-ttu-id="620b8-102">如何建立 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="620b8-102">How to Create BizTalk Projects</span></span>
<span data-ttu-id="620b8-103">若要建立在 BizTalk Server 執行的應用程式，開始請先新增一或多個 BizTalk 專案到方案中。</span><span class="sxs-lookup"><span data-stu-id="620b8-103">To create an application that runs on BizTalk Server, you start by adding one or more BizTalk projects to a solution.</span></span> <span data-ttu-id="620b8-104">此部分敘述某些您在使用 BizTalk 專案時可能會執行的工作。</span><span class="sxs-lookup"><span data-stu-id="620b8-104">This section describes some of the tasks that you might perform when you work with BizTalk projects.</span></span>  
  
 <span data-ttu-id="620b8-105">建立方案和專案的詳細資訊，請參閱 「 簡介方案、 專案和項目 」，在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]結合的集合，在[ http://go.microsoft.com/fwlink/?LinkId=124069 ](http://go.microsoft.com/fwlink/?LinkId=124069)。</span><span class="sxs-lookup"><span data-stu-id="620b8-105">For more information about creating solutions and projects, see "Introduction to Solutions, Projects, and Items" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Combined Collection at [http://go.microsoft.com/fwlink/?LinkId=124069](http://go.microsoft.com/fwlink/?LinkId=124069).</span></span>  
  
### <a name="to-create-a-biztalk-project"></a><span data-ttu-id="620b8-106">建立 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="620b8-106">To create a BizTalk project</span></span>  
  
1. <span data-ttu-id="620b8-107">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="620b8-107">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2. <span data-ttu-id="620b8-108">在 **新的專案**對話方塊中，於**專案類型**區域中，選取**BizTalk 專案**。</span><span class="sxs-lookup"><span data-stu-id="620b8-108">In the **New Project** dialog box, in the **Project Types** area, select **BizTalk Projects**.</span></span>  
  
3. <span data-ttu-id="620b8-109">在 [**範本**] 區域中，選取其中一個 BizTalk Server 專案範本。</span><span class="sxs-lookup"><span data-stu-id="620b8-109">In the **Templates** area, select one of the BizTalk Server Project templates.</span></span>  
  
4. <span data-ttu-id="620b8-110">指定專案名稱與其位置。</span><span class="sxs-lookup"><span data-stu-id="620b8-110">Specify project name and its location.</span></span>  
  
5. <span data-ttu-id="620b8-111">選取 **建立新方案**然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="620b8-111">Select **Create New Solution** and click **OK**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="620b8-112">中的使用者可設定屬性的一些**新的專案** 對話方塊中，會出現 「 只有當您使用 BizTalk 專案系統。</span><span class="sxs-lookup"><span data-stu-id="620b8-112">Some of the user configurable properties in the **New Projects** dialog box appear only when you are working with the BizTalk project system.</span></span> <span data-ttu-id="620b8-113">如需有關不同的 BizTalk Server 專案範本和用法的詳細資訊，請參閱 < [BizTalk Server 專案範本](../core/biztalk-server-project-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="620b8-113">For more information about the different BizTalk Server project templates and their use, see [BizTalk Server Project Templates](../core/biztalk-server-project-templates.md).</span></span>  
  
### <a name="to-add-a-new-biztalk-project-to-a-solution"></a><span data-ttu-id="620b8-114">新增 BizTalk 專案到方案</span><span class="sxs-lookup"><span data-stu-id="620b8-114">To add a new BizTalk project to a solution</span></span>  
  
1. <span data-ttu-id="620b8-115">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中開啟此方案。</span><span class="sxs-lookup"><span data-stu-id="620b8-115">Open the solution in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
2. <span data-ttu-id="620b8-116">以滑鼠右鍵按一下方案名稱，指向**新增**，然後按一下**新的專案**。</span><span class="sxs-lookup"><span data-stu-id="620b8-116">Right-click the solution name, point to **Add**, and click **New Project**.</span></span>  
  
3. <span data-ttu-id="620b8-117">在 [**專案類型**區域中，選取**BizTalk 專案**，然後在**範本**] 區域中，選取其中一個 BizTalk Server 專案範本。</span><span class="sxs-lookup"><span data-stu-id="620b8-117">In the **Project Types** area, select **BizTalk Projects**, and in the **Templates** area, select one of the BizTalk Server Project templates.</span></span>  
  
4. <span data-ttu-id="620b8-118">選取**加入至方案**然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="620b8-118">Select **Add to Solution** and click **OK**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="620b8-119">不支援下列功能表命令**開放**子功能表中的**檔案**功能表：**從 Web 專案**並**檔案從 Web**。</span><span class="sxs-lookup"><span data-stu-id="620b8-119">The following menu commands are not supported on the **Open** submenu of the **File** menu: **Project From Web** and **File From Web**.</span></span> <span data-ttu-id="620b8-120">如需詳細資訊，請參閱 <<c0> [ 使用 Visual Studio](../core/using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="620b8-120">For more information, see [Using Visual Studio](../core/using-visual-studio.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="620b8-121">本節內容</span><span class="sxs-lookup"><span data-stu-id="620b8-121">In This Section</span></span>  
  
-   [<span data-ttu-id="620b8-122">建立 BizTalk 專案時的考量</span><span class="sxs-lookup"><span data-stu-id="620b8-122">Considerations When Creating BizTalk Projects</span></span>](../core/considerations-when-creating-biztalk-projects.md)  
  
-   [<span data-ttu-id="620b8-123">新增專案項目</span><span class="sxs-lookup"><span data-stu-id="620b8-123">Adding Project Items</span></span>](../core/adding-project-items.md)  
  
-   [<span data-ttu-id="620b8-124">解決方案建置設定</span><span class="sxs-lookup"><span data-stu-id="620b8-124">Solution Build Configurations</span></span>](../core/solution-build-configurations.md)