---
title: 移轉 BizTalk Server 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a4dde72-6555-4bf6-b90e-676aa65312ff
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0fd15de7aec81c046ab6b2fc23b6c63a1ec0615
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50752702"
---
# <a name="migrating-a-biztalk-server-project"></a><span data-ttu-id="842e3-102">移轉 BizTalk Server 專案</span><span class="sxs-lookup"><span data-stu-id="842e3-102">Migrating a BizTalk Server Project</span></span>
[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] <span data-ttu-id="842e3-103">針對開發專案[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以移轉至較新的環境，使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]轉換。</span><span class="sxs-lookup"><span data-stu-id="842e3-103">projects developed for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can be migrated to the newer environments by using  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] conversion.</span></span> <span data-ttu-id="842e3-104">如需支援的移轉版本的清單，請參閱 <<c0> [ 支援的升級路徑與安裝指南](http://social.technet.microsoft.com/wiki/contents/articles/28554.biztalk-server-supported-upgrade-paths-and-installation-guides.aspx)。</span><span class="sxs-lookup"><span data-stu-id="842e3-104">For a list of the supported migration versions, see [Supported Upgrade Paths and Installation Guides](http://social.technet.microsoft.com/wiki/contents/articles/28554.biztalk-server-supported-upgrade-paths-and-installation-guides.aspx).</span></span>  

## <a name="biztalk-project-changes-after-running-the-conversion-wizard"></a><span data-ttu-id="842e3-105">執行轉換精靈後 BizTalk 專案的變更</span><span class="sxs-lookup"><span data-stu-id="842e3-105">BizTalk Project Changes After Running the Conversion Wizard</span></span>  
 <span data-ttu-id="842e3-106">下表顯示如何[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]專案組態名稱變更，和其中部分特定組態屬性，將專案重新配置所轉換至較新[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="842e3-106">The following table shows how [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] project configuration names change, and where some specific configuration properties relocate after the project is converted to a newer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span> <span data-ttu-id="842e3-107">大部分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-相關的專案設定都位於**部署**] 索引標籤的 [專案設計工具。</span><span class="sxs-lookup"><span data-stu-id="842e3-107">Most of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-related project settings are located on the **Deployment** tab of Project Designer.</span></span>  


| [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] <span data-ttu-id="842e3-108">專案</span><span class="sxs-lookup"><span data-stu-id="842e3-108">project</span></span> | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] <span data-ttu-id="842e3-109">專案</span><span class="sxs-lookup"><span data-stu-id="842e3-109">project</span></span> |
|--------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
|             <span data-ttu-id="842e3-110">**內嵌追蹤資訊**輸出組態屬性</span><span class="sxs-lookup"><span data-stu-id="842e3-110">**Embed Tracking Information** output configuration property</span></span>             |      <span data-ttu-id="842e3-111">**定義 TRACE 常數**建置選項**建置**] 索引標籤的 [專案設計工具</span><span class="sxs-lookup"><span data-stu-id="842e3-111">**Define TRACE constant** build option on the **Build** tab of Project Designer</span></span>       |
|           <span data-ttu-id="842e3-112">**產生偵錯資訊**輸出組態屬性</span><span class="sxs-lookup"><span data-stu-id="842e3-112">**Generate Debugging Information** output configuration property</span></span>           |      <span data-ttu-id="842e3-113">**定義 DEBUG 常數**建置選項**建置**] 索引標籤的 [專案設計工具</span><span class="sxs-lookup"><span data-stu-id="842e3-113">**Define DEBUG constant** build option on the **Build** tab of Project Designer</span></span>       |
|              <span data-ttu-id="842e3-114">**BPEL 合規性**程式碼產生組態屬性</span><span class="sxs-lookup"><span data-stu-id="842e3-114">**BPEL Compliance** code generation configuration property</span></span>              |       <span data-ttu-id="842e3-115">**BPEL 合規性**程式碼專案的 [屬性] 視窗中的產生屬性</span><span class="sxs-lookup"><span data-stu-id="842e3-115">**BPEL Compliance** code generation property in the project properties window</span></span>        |

> [!NOTE]
>  <span data-ttu-id="842e3-116">BizTalk 專案現在有兩種組建類型：**發行**並**偵錯**，取代了**開發**並**部署**的稍早版本。</span><span class="sxs-lookup"><span data-stu-id="842e3-116">BizTalk projects now have two build types: **Release** and **Debug**, which replaces **Development** and **Deployment** of earlier versions.</span></span> <span data-ttu-id="842e3-117">不過，您將會繼續看見**Development**並**部署**從移轉的專案組態[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="842e3-117">However, you will continue to see the **Development** and **Deployment** configurations for the projects that are migrated from [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)].</span></span>  
> 
> [!CAUTION]
>  <span data-ttu-id="842e3-118">只有\*.btproj 和\*。 因為選擇備份選項，在轉換期間備份.btproj.user 專案檔。</span><span class="sxs-lookup"><span data-stu-id="842e3-118">Only the \*.btproj and \*.btproj.user project files are backed up as a result of choosing the back up option during the conversion.</span></span> <span data-ttu-id="842e3-119">其他檔案必須手動備份。</span><span class="sxs-lookup"><span data-stu-id="842e3-119">Other files must be manually backed up.</span></span>  
> 
> [!CAUTION]
>  <span data-ttu-id="842e3-120">轉換期間將遺失對自動產生的項目 (例如 XSD 與 ODX 檔案) 所做的自訂設定。</span><span class="sxs-lookup"><span data-stu-id="842e3-120">Any customizations to auto-generated items such XSD and ODX files will be lost during conversion.</span></span> <span data-ttu-id="842e3-121">對於將 Web 參考新增至 BizTalk 專案時產生的 XSD 檔案，結果也是一樣。</span><span class="sxs-lookup"><span data-stu-id="842e3-121">This applies to XSD files generated when a web reference is added to a BizTalk project as well.</span></span>  

## <a name="project-migration-and-delay-signing"></a><span data-ttu-id="842e3-122">專案移轉與延遲簽章</span><span class="sxs-lookup"><span data-stu-id="842e3-122">Project Migration and Delay Signing</span></span>  
 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] <span data-ttu-id="842e3-123">專案使用[延遲簽章](http://go.microsoft.com/fwlink/p/?LinkId=140992)可能無法建置程序期間進行的轉換後[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="842e3-123">projects that use [Delay Signing](http://go.microsoft.com/fwlink/p/?LinkId=140992) may fail during the build process after being converted for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="842e3-124">如果此情形**產生序列化組件**組建設定已移轉的專案組態不會設定為**關閉**。</span><span class="sxs-lookup"><span data-stu-id="842e3-124">This can happen if **Generate serialization assembly** build setting for the migrated project configuration is not set to **Off**.</span></span>  

## <a name="project-migration-and-msmqt"></a><span data-ttu-id="842e3-125">專案移轉與 MSMQT</span><span class="sxs-lookup"><span data-stu-id="842e3-125">Project Migration and MSMQT</span></span>  
 <span data-ttu-id="842e3-126">MSMQT 不再是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的一部分。</span><span class="sxs-lookup"><span data-stu-id="842e3-126">MSMQT is no longer part of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="842e3-127">如需這如何影響專案移轉的詳細資訊，請參閱主題[MSMQT 過時](../core/msmqt-deprecation.md)。</span><span class="sxs-lookup"><span data-stu-id="842e3-127">For more information on how this can affect project migration, see the topic [MSMQT Deprecation](../core/msmqt-deprecation.md).</span></span>  

## <a name="project-conversion-requires-the-project-and-solution-file"></a><span data-ttu-id="842e3-128">專案轉換需要專案與方案檔</span><span class="sxs-lookup"><span data-stu-id="842e3-128">Project Conversion requires the project and solution file</span></span>  
 <span data-ttu-id="842e3-129">如果您嘗試轉換 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 專案，但是卻沒有方案檔案，將會收到下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="842e3-129">If you attempt to convert a [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] project and do not have the solution file you will receive the following error:</span></span>  

 <span data-ttu-id="842e3-130">**轉換專案檔時發生錯誤。子項目\<BIZTALK\>項目的\<VisualStudioProject\>無效。**</span><span class="sxs-lookup"><span data-stu-id="842e3-130">**Error converting project file. Child element \<BIZTALK\> of element \<VisualStudioProject\> is not valid.**</span></span>  

 <span data-ttu-id="842e3-131">專案轉換需要 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案中的方案檔 (.sln)。</span><span class="sxs-lookup"><span data-stu-id="842e3-131">Project conversion requires the solution file (.sln) from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span> <span data-ttu-id="842e3-132">如果方案檔不存在，您必須使用 [!INCLUDE[btsVStudioNet2005](../includes/btsvstudionet2005-md.md)] 建立一個，並將 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 專案新增到該方案。</span><span class="sxs-lookup"><span data-stu-id="842e3-132">If the solution file is not available, you must create one with [!INCLUDE[btsVStudioNet2005](../includes/btsvstudionet2005-md.md)] and add the [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] project to the solution.</span></span> <span data-ttu-id="842e3-133">然後執行 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 轉換精靈。</span><span class="sxs-lookup"><span data-stu-id="842e3-133">Then run the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] conversion wizard.</span></span>  

> [!NOTE]
>  <span data-ttu-id="842e3-134">您可以將轉換只有專案檔 (.btproj) 使用 Visual Studio 專案。</span><span class="sxs-lookup"><span data-stu-id="842e3-134">You may be able to convert the project using only the project file (.btproj) with Visual Studio.</span></span>