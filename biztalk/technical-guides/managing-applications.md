---
title: 管理應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef1039fb-7460-444b-a45e-2783bdc7c109
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52e525499671a04228763c6792961c3204a3a2d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298670"
---
# <a name="managing-applications"></a><span data-ttu-id="0f3d1-102">管理應用程式</span><span class="sxs-lookup"><span data-stu-id="0f3d1-102">Managing Applications</span></span>
<span data-ttu-id="0f3d1-103">BizTalk 應用程式是應用程式成品，例如協調流程、 管線、 結構描述、 對應和連接埠的邏輯容器。</span><span class="sxs-lookup"><span data-stu-id="0f3d1-103">A BizTalk application is a logical container for application artifacts, such as orchestrations, pipelines, schemas, maps, and ports.</span></span> <span data-ttu-id="0f3d1-104">BizTalk 應用程式可讓您在相同的容器中包含相關的元件。</span><span class="sxs-lookup"><span data-stu-id="0f3d1-104">BizTalk applications enable you to include related components in the same container.</span></span> <span data-ttu-id="0f3d1-105">在應用程式內的任何成品可能會在該應用程式的其他成品，或任何參考的應用程式中的任何成品參考。</span><span class="sxs-lookup"><span data-stu-id="0f3d1-105">Any artifact within an application may refer to any other artifacts within that application, or to any artifact in any referenced application.</span></span> <span data-ttu-id="0f3d1-106">如需可以在 BizTalk 應用程式的成品的完整清單，請參閱[什麼是 BizTalk 應用程式？](http://go.microsoft.com/fwlink/?LinkId=154994)</span><span class="sxs-lookup"><span data-stu-id="0f3d1-106">For a complete list of artifacts that can be in a BizTalk application, see [What is a BizTalk Application?](http://go.microsoft.com/fwlink/?LinkId=154994)</span></span> <span data-ttu-id="0f3d1-107">(http://go.microsoft.com/fwlink/?LinkId=154994)。</span><span class="sxs-lookup"><span data-stu-id="0f3d1-107">(http://go.microsoft.com/fwlink/?LinkId=154994).</span></span>  
  
 <span data-ttu-id="0f3d1-108">BizTalk 應用程式簡化許多每天[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]工作。</span><span class="sxs-lookup"><span data-stu-id="0f3d1-108">BizTalk applications streamline many everyday [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tasks.</span></span> <span data-ttu-id="0f3d1-109">部署、 管理、 啟動、 停止時，即可疑難排解[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式層級。</span><span class="sxs-lookup"><span data-stu-id="0f3d1-109">You can deploy, manage, start, stop, and troubleshoot [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] at the application level.</span></span> <span data-ttu-id="0f3d1-110">如此可避免混淆與較低的使用者錯誤的風險。</span><span class="sxs-lookup"><span data-stu-id="0f3d1-110">This results in less confusion and less risk of error for users.</span></span> <span data-ttu-id="0f3d1-111">包含 BizTalk 應用程式容器</span><span class="sxs-lookup"><span data-stu-id="0f3d1-111">A BizTalk application container contains</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0f3d1-112">Visual Studio 環境部署至它的組件。</span><span class="sxs-lookup"><span data-stu-id="0f3d1-112"> assemblies that are deployed to it by the Visual Studio environment.</span></span> <span data-ttu-id="0f3d1-113">應用程式也可能包含接收埠、 接收位置、 傳送埠，屬性的追蹤設定，與角色連結。</span><span class="sxs-lookup"><span data-stu-id="0f3d1-113">The application may also contain receive ports, receive locations, send ports, property tracking settings, and role links.</span></span> <span data-ttu-id="0f3d1-114">您可以手動新增[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式，或移動的組件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]從其他應用程式的組件。</span><span class="sxs-lookup"><span data-stu-id="0f3d1-114">You can manually add [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies to the application, or move [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies from other applications.</span></span> <span data-ttu-id="0f3d1-115">此外，您可以加入非[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組件和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]成品，例如商務規則引擎 (BRE) 原則和 BAM 定義檔案。</span><span class="sxs-lookup"><span data-stu-id="0f3d1-115">In addition, you can add non-[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] artifacts such as Business Rule Engine (BRE) policies and BAM definition files.</span></span> <span data-ttu-id="0f3d1-116">以隱含方式，應用程式也包含所有目前的設定都由繫結。</span><span class="sxs-lookup"><span data-stu-id="0f3d1-116">Implicitly, the application also contains all of the bindings that are represented by their current settings.</span></span>  
  
 <span data-ttu-id="0f3d1-117">您可以建立前置或後置處理指令碼來執行動作，匯入應用程式時，安裝或解除安裝。</span><span class="sxs-lookup"><span data-stu-id="0f3d1-117">You can create pre- or post-processing scripts to perform actions when an application is imported, installed, or uninstalled.</span></span> <span data-ttu-id="0f3d1-118">如需有關如何使用這類指令碼的詳細資訊，請參閱[使用前置和後置處理指令碼，以自訂應用程式部署](http://go.microsoft.com/fwlink/?LinkId=154995)(http://go.microsoft.com/fwlink/?LinkId=154995)。</span><span class="sxs-lookup"><span data-stu-id="0f3d1-118">For more information about using such scripts, see [Using Pre- and Post-processing Scripts to Customize Application Deployment](http://go.microsoft.com/fwlink/?LinkId=154995) (http://go.microsoft.com/fwlink/?LinkId=154995).</span></span>  
  
 <span data-ttu-id="0f3d1-119">本節說明如何部署版本，及更新應用程式或個別成品。</span><span class="sxs-lookup"><span data-stu-id="0f3d1-119">This section describes how to deploy, version, and update applications or individual artifacts.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0f3d1-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="0f3d1-120">In This Section</span></span>  
  
-   [<span data-ttu-id="0f3d1-121">部署應用程式</span><span class="sxs-lookup"><span data-stu-id="0f3d1-121">Deploying an Application</span></span>](../technical-guides/deploying-an-application.md)  
  
-   [<span data-ttu-id="0f3d1-122">更新應用程式</span><span class="sxs-lookup"><span data-stu-id="0f3d1-122">Updating an Application</span></span>](../technical-guides/updating-an-application.md)