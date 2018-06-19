---
title: 更新應用程式的重要考量 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- updating, applications
- applications, planning
- applications, updating
- planning, applications
- planning, updating
- updating, planning
ms.assetid: e7690bdf-943d-4bb6-b8cd-a6841b722d40
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c24528dcce390376b7ac2e47199aa5ae06d412a4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257742"
---
# <a name="important-considerations-for-updating-applications"></a><span data-ttu-id="ecf48-102">更新應用程式的重要考量</span><span class="sxs-lookup"><span data-stu-id="ecf48-102">Important Considerations for Updating Applications</span></span>
<span data-ttu-id="ecf48-103">以下是在更新應用程式 (特別是在實際執行環境中執行的應用程式) 之前要考量的重要事項。</span><span class="sxs-lookup"><span data-stu-id="ecf48-103">The following are important issues to consider before updating an application, especially one that is running in a production environment.</span></span>  
  
## <a name="general-considerations"></a><span data-ttu-id="ecf48-104">一般考量</span><span class="sxs-lookup"><span data-stu-id="ecf48-104">General considerations</span></span>  
  
-   <span data-ttu-id="ecf48-105">群組領域可以看到合作對象和規則，所以加入額外的合作對象和規則可能會中斷其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="ecf48-105">Parties and rules are visible at a group scope, so adding additional parties and rules could disrupt other applications.</span></span>  
  
-   <span data-ttu-id="ecf48-106">如果要解除部署其他成品所相依的成品，則必須先解除部署相依的成品。</span><span class="sxs-lookup"><span data-stu-id="ecf48-106">If you are undeploying an artifact on which another artifact depends, the dependent artifact must be undeployed first.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ecf48-107">BizTalk Server 管理主控台會顯示警告，以防止您以錯誤的順序解除部署成品：</span><span class="sxs-lookup"><span data-stu-id="ecf48-107">The BizTalk Server Administration console will display a warning and prevent you from undeploying artifacts in the incorrect order.</span></span>  
  
-   <span data-ttu-id="ecf48-108">如果更新現有的應用程式中的 BizTalk 組件時，您可能需要重新啟動主控件執行個體，變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="ecf48-108">If a BizTalk assembly in an existing application is updated, you may need to restart host instances for the changes to take effect.</span></span> <span data-ttu-id="ecf48-109">重新啟動主控件執行個體，就會停止所有其他主控件執行個體執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ecf48-109">Restarting a host instance stops all other applications that are running on the host instance.</span></span>  
  
-   <span data-ttu-id="ecf48-110">如果使用 Visual Studio 將應用程式部署到實際執行環境 (我們強烈建議您不要這麼做)，而在專案屬性中，將 [重新啟動主控件執行個體] 選項設定為 True，則在您部署應用程式時，所有的主控件執行個體都將重新啟動，包括未與此應用程式關聯的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="ecf48-110">If you use Visual Studio to deploy an application into a production environment (which we strongly recommend against doing) and the Restart Host Instances option is set to True in project properties, all host instances will restart when you deploy the application, including those that are not associated with this application.</span></span> <span data-ttu-id="ecf48-111">這樣會停止在本機電腦的任何主控件執行個體上執行的所有其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="ecf48-111">This will stop all other applications that are running on any host instance on the local computer.</span></span>  
  
-   <span data-ttu-id="ecf48-112">如果您想要更新已部署為 BizTalk 應用程式的 BizTalk Server 組件 (包含協調流程、結構描述或對應)，則可以執行下列任何一項：</span><span class="sxs-lookup"><span data-stu-id="ecf48-112">If you want to update a BizTalk Server assembly (containing an orchestration, schema, or map) which is deployed as a BizTalk application, you can do any of the following:</span></span>  
  
    -   <span data-ttu-id="ecf48-113">執行並存部署。</span><span class="sxs-lookup"><span data-stu-id="ecf48-113">Perform a side-by-side deployment.</span></span> <span data-ttu-id="ecf48-114">一般只要遞增版本，就可以適當地修改較新的組件。</span><span class="sxs-lookup"><span data-stu-id="ecf48-114">You can appropriately modify the newer assembly typically by incrementing the version.</span></span> <span data-ttu-id="ecf48-115">這樣讓兩個組件都會有相異完整組件名稱。</span><span class="sxs-lookup"><span data-stu-id="ecf48-115">This makes both the assemblies have a distinct fully qualified assembly name.</span></span> <span data-ttu-id="ecf48-116">如需詳細資訊，請參閱[如何部署新版應用程式來執行的並行與現有版本](../core/deploy-new-application-version-to-run-side-by-side-with-existing-version.md)。</span><span class="sxs-lookup"><span data-stu-id="ecf48-116">For more information, see [How to Deploy a New Version of an Application to Run Side-by-side with an Existing Version](../core/deploy-new-application-version-to-run-side-by-side-with-existing-version.md).</span></span>  
  
    -   <span data-ttu-id="ecf48-117">將現有的 BizTalk Server 組件以新的組件取代。</span><span class="sxs-lookup"><span data-stu-id="ecf48-117">Replace the existing BizTalk Server assembly with a new assembly.</span></span> <span data-ttu-id="ecf48-118">您必須停止所有可能會載入過時組件的主控件執行個體，並取代 GAC 中的過時組件，然後重新啟動主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="ecf48-118">You must stop all host instances that can possibly load the out-dated assembly, replace the out-dated assembly in the GAC, and then restart the host instances.</span></span>  
  
-   <span data-ttu-id="ecf48-119">如果要部署全新的應用程式以取代現有的應用程式，則必須修改其他應用程式與您要取代之應用程式間的所有參考。</span><span class="sxs-lookup"><span data-stu-id="ecf48-119">If you deploy an entirely new application to replace an existing application, you must correct any references between other applications and the application that you are replacing.</span></span>  
  
## <a name="considerations-for-updating-schemas"></a><span data-ttu-id="ecf48-120">更新結構描述的考量</span><span class="sxs-lookup"><span data-stu-id="ecf48-120">Considerations for updating schemas</span></span>  
  
-   <span data-ttu-id="ecf48-121">如果您將組件加入 BizTalk 群組中包含具有相同的訊息類型做為現有的結構描述的新結構描述的應用程式時，發生在管線中的結構描述解析時將使用具有最高的版本號碼的結構描述。</span><span class="sxs-lookup"><span data-stu-id="ecf48-121">If you add an assembly to an application that includes a new schema with the same message type as an existing schema in the BizTalk group, the schema with the highest version number will be used when schema resolution occurs in pipelines.</span></span> <span data-ttu-id="ecf48-122">此外，如果一種訊息類型參考一個以上的.NET 型別，模稜兩可能導致管線執行失敗。</span><span class="sxs-lookup"><span data-stu-id="ecf48-122">In addition, if one message type refers to more than one .NET type, this ambiguity may cause pipeline execution failure.</span></span> <span data-ttu-id="ecf48-123">這是因為結構描述查閱會使用訊息類型、目標命名空間以及執行個體的根名稱。</span><span class="sxs-lookup"><span data-stu-id="ecf48-123">This is because schema lookup uses message type, the target namespace, and root name of the instance.</span></span> <span data-ttu-id="ecf48-124">在任何應用程式中，如果使用的結構描述具有與新結構描述相同的訊息類型，則管線都可能會發生這種狀況。</span><span class="sxs-lookup"><span data-stu-id="ecf48-124">This can occur for pipelines in any application that uses a schema with the same message type as the new schema.</span></span> <span data-ttu-id="ecf48-125">如需結構描述解析的詳細資訊，請參閱[管線元件中的結構描述解析](../core/schema-resolution-in-pipeline-components.md)。</span><span class="sxs-lookup"><span data-stu-id="ecf48-125">For more information about schema resolution, see [Schema Resolution in Pipeline Components](../core/schema-resolution-in-pipeline-components.md).</span></span>  
  
-   <span data-ttu-id="ecf48-126">在更新結構描述時，也必須更新對應以參考結構描述 (或建立新對應) 以及任何依賴該結構描述的協調流程。</span><span class="sxs-lookup"><span data-stu-id="ecf48-126">When you update a schema, you must also update the maps that reference the schema (or create new maps) as well as any orchestrations that rely on the schema.</span></span>  
  
-   <span data-ttu-id="ecf48-127">如果要增加結構描述版本，則應該針對任何使用結構描述的管線執行個體和管線元件，更新結構描述的參考。</span><span class="sxs-lookup"><span data-stu-id="ecf48-127">If you increment a schema version, you should update the reference to the schema for any pipeline instances and pipeline components that use it.</span></span>  
  
-   <span data-ttu-id="ecf48-128">解除部署結構描述會導致舊版結構描述成為作用中 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="ecf48-128">Undeploying a schema causes the previous version of the schema, if available, to become active.</span></span>  
  
## <a name="considerations-for-updating-policies"></a><span data-ttu-id="ecf48-129">更新原則的考量</span><span class="sxs-lookup"><span data-stu-id="ecf48-129">Considerations for updating policies</span></span>  
  
-   <span data-ttu-id="ecf48-130">BizTalk Server 執行階段會使用已部署狀態的最新版原則。</span><span class="sxs-lookup"><span data-stu-id="ecf48-130">The highest version of a policy that is in a deployed state is used by the BizTalk Server runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecf48-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecf48-131">See Also</span></span>  
 [<span data-ttu-id="ecf48-132">更新 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="ecf48-132">Updating BizTalk Applications</span></span>](../core/updating-biztalk-applications.md)