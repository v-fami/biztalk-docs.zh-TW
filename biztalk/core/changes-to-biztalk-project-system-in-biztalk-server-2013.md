---
title: 在 BizTalk Server 2013 中的 BizTalk 專案系統變更 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82f0dd18-073c-4cba-aa0d-48076c58f874
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 836ffa11e3b15b379b8f4a07def2269f0f29a453
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006271"
---
# <a name="changes-to-biztalk-project-system-in-biztalk-server-2013"></a><span data-ttu-id="465c5-102">在 BizTalk Server 2013 中的 BizTalk 專案系統變更</span><span class="sxs-lookup"><span data-stu-id="465c5-102">Changes to BizTalk Project System in BizTalk Server 2013</span></span>
<span data-ttu-id="465c5-103">本主題可讓您變更的概要 BizTalk 專案系統，BizTalk Server 中。</span><span class="sxs-lookup"><span data-stu-id="465c5-103">This topic gives you a high-level overview of changes to the BizTalk Project System in BizTalk Server.</span></span>  
  
## <a name="project-properties-are-displayed-in-project-designer-window"></a><span data-ttu-id="465c5-104">專案屬性會顯示在專案設計工具視窗中</span><span class="sxs-lookup"><span data-stu-id="465c5-104">Project properties are displayed in project designer window</span></span>  
 <span data-ttu-id="465c5-105">BizTalk Server 專案的屬性現在會顯示於 Visual Studio 的專案設計工具中，而非 [屬性] 對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="465c5-105">Properties for a BizTalk Server project are now displayed in the Project Designer of Visual Studio instead of in a Properties dialog.</span></span> <span data-ttu-id="465c5-106">專案設計工具提供了可供管理專案屬性、設定和資源的集中式位置。</span><span class="sxs-lookup"><span data-stu-id="465c5-106">The Project Designer provides a centralized location for managing project properties, settings, and resources.</span></span> <span data-ttu-id="465c5-107">專案設計工具會和其他設計工具 (如表單或類別設計工具) 一樣，以單一視窗的形式顯示在 Visual Studio IDE 中，並包含一些可透過左側索引標籤存取的頁面。</span><span class="sxs-lookup"><span data-stu-id="465c5-107">The Project Designer appears as a single window in the Visual Studio IDE, much the same as other designers such as the Form or Class designers and contains a number of pages that are accessed through tabs on the left-hand side.</span></span> <span data-ttu-id="465c5-108">如需詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=190417](http://go.microsoft.com/fwlink/?LinkId=190417)。</span><span class="sxs-lookup"><span data-stu-id="465c5-108">For more information, see [http://go.microsoft.com/fwlink/?LinkId=190417](http://go.microsoft.com/fwlink/?LinkId=190417).</span></span>  
  
## <a name="properties-for-schema-and-map-files-are-displayed-in-properties-window"></a><span data-ttu-id="465c5-109">結構描述與對應檔案的屬性會顯示在屬性視窗中</span><span class="sxs-lookup"><span data-stu-id="465c5-109">Properties for schema and map files are displayed in Properties window</span></span>  
 <span data-ttu-id="465c5-110">屬性結構描述和對應檔案，例如**輸入執行個體檔案名稱**和**測試對應輸入執行個體**會顯示在 屬性 視窗而不是在個別**屬性**  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="465c5-110">Properties for schema and map files such as **Input Instance Filename** and **Test Map Input Instance** are displayed in the Properties window with instead of in a separate **Properties** dialog box.</span></span>  
  
## <a name="add-web-reference-option-on-projects"></a><span data-ttu-id="465c5-111">專案上的加入 Web 參考選項</span><span class="sxs-lookup"><span data-stu-id="465c5-111">Add Web Reference option on projects</span></span>  
 <span data-ttu-id="465c5-112">**加入 Web 參考**選項時，無法使用您以滑鼠右鍵按一下專案名稱或**參考**在 [方案總管] 中。</span><span class="sxs-lookup"><span data-stu-id="465c5-112">The **Add Web Reference** option is not available when you right-click the project name or **References** in the Solution Explorer.</span></span> <span data-ttu-id="465c5-113">您可以使用下列步驟，加入 Web 服務 (.asmx) 的 Web 參考︰</span><span class="sxs-lookup"><span data-stu-id="465c5-113">You can add a Web reference to a Web service (.asmx) by using the following steps:</span></span>  
  
1.  <span data-ttu-id="465c5-114">以滑鼠右鍵按一下**參考**中專案，然後按一下**加入服務參考**。</span><span class="sxs-lookup"><span data-stu-id="465c5-114">Right-click **References** in the project, and then click **Add Service Reference**.</span></span>  
  
2.  <span data-ttu-id="465c5-115">在**加入服務參考**對話方塊中，按一下 **進階**。</span><span class="sxs-lookup"><span data-stu-id="465c5-115">In the **Add Service Reference** dialog box, click **Advanced**.</span></span>  
  
3.  <span data-ttu-id="465c5-116">在**服務參考設定**對話方塊中，按一下 **加入 Web 參考**。</span><span class="sxs-lookup"><span data-stu-id="465c5-116">In the **Service Reference Settings** dialog box, click **Add Web Reference**.</span></span>  
  
4.  <span data-ttu-id="465c5-117">輸入 URL，然後按一下**移**。</span><span class="sxs-lookup"><span data-stu-id="465c5-117">Type the URL, and then click **Go**.</span></span>  
  
5.  <span data-ttu-id="465c5-118">按一下**加入參考**加入 Web 參考。</span><span class="sxs-lookup"><span data-stu-id="465c5-118">Click **Add Reference** to add the Web reference.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="465c5-119">加入 Web 參考加入 BizTalk 專案之後,**加入 Web 參考**參考、 Web 參考和專案節點上就提供功能表選項。</span><span class="sxs-lookup"><span data-stu-id="465c5-119">After you add a Web reference to a BizTalk project, the **Add Web Reference** menu option is available on the References, Web References and project nodes.</span></span>  
  
 <span data-ttu-id="465c5-120">如需加入服務與 Web 參考的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=131577](http://go.microsoft.com/fwlink/?LinkId=131577)。</span><span class="sxs-lookup"><span data-stu-id="465c5-120">For more information about adding service and Web references, see [http://go.microsoft.com/fwlink/?LinkId=131577](http://go.microsoft.com/fwlink/?LinkId=131577).</span></span>  
  
## <a name="msbuild-integration"></a><span data-ttu-id="465c5-121">MSBUILD 整合</span><span class="sxs-lookup"><span data-stu-id="465c5-121">MSBUILD Integration</span></span>  
 <span data-ttu-id="465c5-122">Visual Studio 使用 MSBUILD 專案檔案格式來儲存有關受管理專案 (包含 BizTalk 專案) 的建置資訊。</span><span class="sxs-lookup"><span data-stu-id="465c5-122">Visual Studio uses the MSBUILD project file format to store build information about managed projects including BizTalk projects.</span></span> <span data-ttu-id="465c5-123">如需詳細資訊，請參閱[與 Visual Studio 的 MSBUILD 整合](../core/msbuild-integration-with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="465c5-123">For more information, see [MSBUILD Integration with Visual Studio](../core/msbuild-integration-with-visual-studio.md).</span></span>  
  
## <a name="team-foundation-server-integration"></a><span data-ttu-id="465c5-124">Team Foundation Server 整合</span><span class="sxs-lookup"><span data-stu-id="465c5-124">Team Foundation Server integration</span></span>  
 <span data-ttu-id="465c5-125">您可以使用 Team Foundation Server 做為 BizTalk 專案的來源控制系統。</span><span class="sxs-lookup"><span data-stu-id="465c5-125">You can use Team Foundation Server as a source control system for BizTalk projects.</span></span> <span data-ttu-id="465c5-126">您可以從 [方案總管] 視窗本身執行存回及取出等作業。</span><span class="sxs-lookup"><span data-stu-id="465c5-126">You can perform operations such as check-in and check-out from Solution Explorer window itself.</span></span>  
  
## <a name="support-for-unit-testing"></a><span data-ttu-id="465c5-127">支援單元測試</span><span class="sxs-lookup"><span data-stu-id="465c5-127">Support for unit testing</span></span>  
 <span data-ttu-id="465c5-128">這項功能可讓您進行結構描述、對應和管線的單元測試。</span><span class="sxs-lookup"><span data-stu-id="465c5-128">This feature allows you to unit test schemas, maps, and pipelines.</span></span> <span data-ttu-id="465c5-129">如需詳細資訊，請參閱[單元測試使用 BizTalk Server 專案](../core/unit-testing-with-biztalk-server-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="465c5-129">For more information, see [Unit Testing with BizTalk Server Projects](../core/unit-testing-with-biztalk-server-projects.md).</span></span>  
  
## <a name="debug-map-feature"></a><span data-ttu-id="465c5-130">偵錯對應功能</span><span class="sxs-lookup"><span data-stu-id="465c5-130">Debug Map feature</span></span>  
 <span data-ttu-id="465c5-131">**偵錯對應功能**。</span><span class="sxs-lookup"><span data-stu-id="465c5-131">**Debug Map feature**.</span></span> <span data-ttu-id="465c5-132">您可以使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中內嵌的 XSLT 偵錯工具，以偵錯對應 (XSLT)。</span><span class="sxs-lookup"><span data-stu-id="465c5-132">You can debug a map (XSLT) by using the inline XSLT debugger with in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="465c5-133">如需詳細資訊，請參閱[如何偵錯對應](../core/how-to-debug-maps.md)。</span><span class="sxs-lookup"><span data-stu-id="465c5-133">For more information, see [How to Debug Maps](../core/how-to-debug-maps.md).</span></span>  
  
## <a name="migrating-biztalk-server-projects"></a><span data-ttu-id="465c5-134">移轉的 BizTalk Server 專案</span><span class="sxs-lookup"><span data-stu-id="465c5-134">Migrating BizTalk Server projects</span></span>  
 <span data-ttu-id="465c5-135">針對較早版本開發的 visual Studio 專案[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以使用 Visual Studio 轉換精靈移轉至 BizTalk Server 環境。</span><span class="sxs-lookup"><span data-stu-id="465c5-135">Visual Studio projects developed for earlier version of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can be migrated to the BizTalk Server environment by using the Visual Studio conversion wizard.</span></span> <span data-ttu-id="465c5-136">如需詳細資訊，請參閱[移轉 BizTalk Server 專案](../core/migrating-a-biztalk-server-project.md)。</span><span class="sxs-lookup"><span data-stu-id="465c5-136">For more information, see [Migrating a BizTalk Server Project](../core/migrating-a-biztalk-server-project.md).</span></span>  
  
## <a name="release-and-debug-build-types"></a><span data-ttu-id="465c5-137">發行和偵錯組建類型</span><span class="sxs-lookup"><span data-stu-id="465c5-137">Release and Debug build types</span></span>  
 <span data-ttu-id="465c5-138">BizTalk 專案現在有兩個組建類型：**發行**和**偵錯**，取代了**開發**和**部署**的前面版本。</span><span class="sxs-lookup"><span data-stu-id="465c5-138">BizTalk projects now have two build types: **Release** and **Debug**, which replaces **Development** and **Deployment** of earlier versions.</span></span> <span data-ttu-id="465c5-139">不過，您將會繼續看見**開發**和**部署**從移轉的專案組態[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="465c5-139">However, you will continue to see the **Development** and **Deployment** configurations for the projects that are migrated from [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)].</span></span>  
  
## <a name="embedding-tracking-and-debugging-information"></a><span data-ttu-id="465c5-140">內嵌追蹤和偵錯資訊</span><span class="sxs-lookup"><span data-stu-id="465c5-140">Embedding tracking and debugging information</span></span>  
 <span data-ttu-id="465c5-141">**內嵌追蹤資訊**和**產生偵錯資訊**輸出組態屬性會取代**定義 TRACE 常數**和**定義 DEBUG 常數**上建置選項**建置**專案設計工具 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="465c5-141">The **Embed Tracking Information** and **Generate Debugging Information** output configuration properties are replaced by the **Define TRACE constant** and **Define DEBUG constant** build options on the **Build** tab of Project Designer.</span></span> <span data-ttu-id="465c5-142">**BPEL 規範程式碼產生**組態屬性會取代**BPEL 規範程式碼產生**專案屬性 視窗中的屬性。</span><span class="sxs-lookup"><span data-stu-id="465c5-142">The **BPEL Compliance code generation** configuration property is replaced by **BPEL compliance code generation** property in the project properties window.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="465c5-143">Visual Studio 轉換精靈會負責將前述設定自動移轉到新環境。</span><span class="sxs-lookup"><span data-stu-id="465c5-143">The Visual Studio Conversion Wizard takes care of automatically migrates the preceding mentioned settings to new environment.</span></span>  
  
## <a name="user-access-control"></a><span data-ttu-id="465c5-144">使用者存取控制</span><span class="sxs-lookup"><span data-stu-id="465c5-144">User Access Control</span></span>  
 <span data-ttu-id="465c5-145">除非您以系統管理權限執行 Visual Studio，否則 Visual Studio 不會讓您在已開啟使用者存取控制 (UAC) 功能的電腦上部署 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="465c5-145">Visual Studio does not let you deploy a BizTalk project on a computer with the User Access Control (UAC) feature turned on unless you run Visual Studio with administrative privileges.</span></span> <span data-ttu-id="465c5-146">以系統管理權限執行 Visual Studio，請按一下**啟動**，指向 **所有程式**，指向  **Microsoft Visual Studio**，以滑鼠右鍵按一下**Microsoft Visual Studio\<版本\>**，然後按一下 **系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="465c5-146">To run Visual Studio with administrative privileges, click **Start**, point to **All Programs**, point to **Microsoft Visual Studio**, right-click **Microsoft Visual Studio \<version\>**, and then click **Run as administrator**.</span></span>  
  
## <a name="c-files-in-a-biztalk-project"></a><span data-ttu-id="465c5-147">BizTalk 專案中的 C# 檔案</span><span class="sxs-lookup"><span data-stu-id="465c5-147">C# files in a BizTalk project</span></span>  
 <span data-ttu-id="465c5-148">BizTalk Server 可讓您結合只有滿足您彈性封裝需要的 BizTalk 成品的 helper 類別。</span><span class="sxs-lookup"><span data-stu-id="465c5-148">BizTalk Server allows you to combine helper classes with BizTalk artifacts for flexible packaging needs only.</span></span>  <span data-ttu-id="465c5-149">不過，您無法加入新的 C# 檔案直接透過使用**加入新項目**或**加入新類別**功能表選項。</span><span class="sxs-lookup"><span data-stu-id="465c5-149">However, you cannot add a new C# file directly by using the **Add New Item** or **Add New Class** menu options.</span></span>  
  
## <a name="generatecsfiles-registry-key-is-obsolete"></a><span data-ttu-id="465c5-150">GenerateCSFiles 登錄機碼已過時</span><span class="sxs-lookup"><span data-stu-id="465c5-150">GenerateCSFiles registry key is obsolete</span></span>  
 <span data-ttu-id="465c5-151">**GenerateCSFiles**登錄機碼現在已過時。</span><span class="sxs-lookup"><span data-stu-id="465c5-151">The **GenerateCSFiles** registry key is obsolete now.</span></span> <span data-ttu-id="465c5-152">所有產生的 .cs 檔都會顯示在 [方案總管] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="465c5-152">All generated .cs files are displayed in the Solution Explorer window.</span></span> <span data-ttu-id="465c5-153">您可能需要按一下**顯示所有檔案**中，查看與某些 BizTalk 項目相關聯的.cs 檔案的 [方案總管] 視窗的工具列項目。</span><span class="sxs-lookup"><span data-stu-id="465c5-153">You may need to click **Show All Files** toolbar item in the Solution Explorer window to see .cs files associated with some of the BizTalk items.</span></span>