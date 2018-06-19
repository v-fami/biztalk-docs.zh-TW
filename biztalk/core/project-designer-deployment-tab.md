---
title: '專案設計工具: [部署] 索引標籤 |Microsoft 文件'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties, Configuration database [BizTalk Server]
- Redeploy property
- configuration properties [deployment], Server property
- Server property
- configuration properties [deployment], Install to Global Assembly Cache (GAC) property
- properties, Management database
- Install to Global Assembly Cache (GAC) property
- Configuration database [BizTalk Server], properties
- Management database, properties
- Administration Group property
- configuration properties [deployment], Redeploy property
- configuration properties [deployment], Management database property
- configuration properties [deployment], Administration Group property
ms.assetid: 5b64f99c-4ec6-4ed3-8590-46420e2f75b8
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 972f3956a19d66d47238ee8170584b4faf6ba886
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264942"
---
# <a name="project-designer-deployment-tab"></a><span data-ttu-id="6a03d-102">專案設計工具：[部署] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="6a03d-102">Project Designer: Deployment Tab</span></span>
<span data-ttu-id="6a03d-103">**部署**屬性索引標籤的 專案設計工具可讓您設定 BizTalk 專案的部署屬性。</span><span class="sxs-lookup"><span data-stu-id="6a03d-103">The **Deployment** property tab of the Project Designer allows you to configure the deployment attributes for the BizTalk project.</span></span> <span data-ttu-id="6a03d-104">您必須同時設定**伺服器**和**組態資料庫**（也稱為 「 BizTalk 管理資料庫） 屬性為集合，部署才能成功。</span><span class="sxs-lookup"><span data-stu-id="6a03d-104">You must configure both the **Server** and the **Configuration Database** (also known as the BizTalk Management database) properties as a set for deployment to be successful.</span></span>  
  
## <a name="application-name"></a><span data-ttu-id="6a03d-105">Application Name</span><span class="sxs-lookup"><span data-stu-id="6a03d-105">Application Name</span></span>  
 <span data-ttu-id="6a03d-106">指定要部署組件的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="6a03d-106">Specify the BizTalk application in which to deploy the assembly.</span></span> <span data-ttu-id="6a03d-107">如果這個名稱是空的，專案就會部署到預設應用程式中。</span><span class="sxs-lookup"><span data-stu-id="6a03d-107">If this is empty, the project will be deployed into the default application.</span></span>  
  
## <a name="configuration-database"></a><span data-ttu-id="6a03d-108">組態資料庫</span><span class="sxs-lookup"><span data-stu-id="6a03d-108">Configuration Database</span></span>  
 <span data-ttu-id="6a03d-109">使用此欄位為已部署的組件指定「BizTalk 組態」資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="6a03d-109">You use this field to specify the name of the BizTalk Configuration database for the deployed assembly.</span></span> <span data-ttu-id="6a03d-110">若已將 BizTalk 專案設定為部署專案，則適用此選項。</span><span class="sxs-lookup"><span data-stu-id="6a03d-110">This applies if you have configured the BizTalk project as a deployment project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a03d-111">「BizTalk 組態」資料庫也稱為「BizTalk 管理」資料庫。</span><span class="sxs-lookup"><span data-stu-id="6a03d-111">The BizTalk Configuration database is also referred to as the BizTalk Management database.</span></span>  
  
 <span data-ttu-id="6a03d-112">預設的組態資料庫名稱為 BizTalkMgmtDb。</span><span class="sxs-lookup"><span data-stu-id="6a03d-112">The default Configuration database name is BizTalkMgmtDb.</span></span>  
  
## <a name="server"></a><span data-ttu-id="6a03d-113">Server</span><span class="sxs-lookup"><span data-stu-id="6a03d-113">Server</span></span>  
 <span data-ttu-id="6a03d-114">這是組態儲存機制 (也稱為「BizTalk 管理」或「BizTalk 組態」資料庫) 所在的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="6a03d-114">This is the name of the server where the Configuration repository (also known as the BizTalk Management or Configuration database) is located.</span></span> <span data-ttu-id="6a03d-115">若將 BizTalk 專案設定為「部署」，則會將 BizTalk 專案部署至此伺服器。</span><span class="sxs-lookup"><span data-stu-id="6a03d-115">You deploy the BizTalk project to this server if you configure the BizTalk project as "Deployment."</span></span>  
  
## <a name="redeploy"></a><span data-ttu-id="6a03d-116">重新部署</span><span class="sxs-lookup"><span data-stu-id="6a03d-116">Redeploy</span></span>  
 <span data-ttu-id="6a03d-117">您使用**重新部署**屬性來判斷是否要刪除現有組態並重新建立設定每次部署組件。</span><span class="sxs-lookup"><span data-stu-id="6a03d-117">You use the **Redeploy** property to determine whether to delete the existing configuration and re-create the configuration each time you deploy the assembly.</span></span> <span data-ttu-id="6a03d-118">預設值是`True`。</span><span class="sxs-lookup"><span data-stu-id="6a03d-118">The default value is `True`.</span></span>  
  
## <a name="install-to-global-assembly-cache"></a><span data-ttu-id="6a03d-119">安裝到全域組件快取</span><span class="sxs-lookup"><span data-stu-id="6a03d-119">Install to Global Assembly Cache</span></span>  
 <span data-ttu-id="6a03d-120">您使用**安裝到全域組件快取**屬性，指出如果[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]需要將 BizTalk 組件安裝至全域組件快取 (GAC)。</span><span class="sxs-lookup"><span data-stu-id="6a03d-120">You use the **Install to Global Assembly Cache** property to indicate if [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] needs to install the BizTalk assembly to the global assembly cache (GAC).</span></span>  
  
## <a name="restart-host-instances"></a><span data-ttu-id="6a03d-121">重新啟動主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="6a03d-121">Restart Host Instances</span></span>  
 <span data-ttu-id="6a03d-122">如果您設定**重新啟動主控件執行個體**至**True**，部署專案時，將重新啟動本機電腦上的主控件執行個體[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6a03d-122">If you set **Restart Host Instances** to **True**, the host instances on the local computer will be restarted when the project is deployed by [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="6a03d-123">這在您進行變更和經常進行重新部署的開發週期非常有用；您將不需要手動重新啟動相關的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="6a03d-123">This is useful during the development cycle when you are making changes and frequently redeploying; you will not have to manually restart related host instances.</span></span>  
  
 <span data-ttu-id="6a03d-124">如果您未重新啟動相關的主控件執行個體，最近的變更就不會反映在 BizTalk 應用程式中，因為舊版可能仍在快取中。</span><span class="sxs-lookup"><span data-stu-id="6a03d-124">If you do not restart related host instances, your latest changes may not be reflected in your BizTalk application because the old version may still be cached.</span></span> <span data-ttu-id="6a03d-125">重新啟動主控件執行個體可清除快取的組件。</span><span class="sxs-lookup"><span data-stu-id="6a03d-125">Restarting the host instance purges cached assemblies.</span></span>  
  
## <a name="enable-unit-testing"></a><span data-ttu-id="6a03d-126">啟用單元測試</span><span class="sxs-lookup"><span data-stu-id="6a03d-126">Enable Unit Testing</span></span>  
 <span data-ttu-id="6a03d-127">指定是否為專案啟用單元測試。</span><span class="sxs-lookup"><span data-stu-id="6a03d-127">Specified whether to enable unit testing for the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a03d-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a03d-128">See Also</span></span>  
 <span data-ttu-id="6a03d-129">[如何部署 BizTalk 組件從 Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="6a03d-129">[How to Deploy a BizTalk Assembly from Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md) </span></span>  
 <span data-ttu-id="6a03d-130">[BizTalk 專案 [屬性] 視窗](../core/biztalk-project-properties-window.md)</span><span class="sxs-lookup"><span data-stu-id="6a03d-130">[BizTalk Project Properties Window](../core/biztalk-project-properties-window.md)</span></span>