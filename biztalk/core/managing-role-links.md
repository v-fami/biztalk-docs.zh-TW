---
title: 管理角色連結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8860e11-3d2c-450f-a7d2-cc116478999c
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e31ec8af7f8c5dd785b471654e9a9cfd7446bbf3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998943"
---
# <a name="manage-role-links"></a><span data-ttu-id="a4256-102">管理角色連結</span><span class="sxs-lookup"><span data-stu-id="a4256-102">Manage Role Links</span></span>

## <a name="overview"></a><span data-ttu-id="a4256-103">概觀</span><span class="sxs-lookup"><span data-stu-id="a4256-103">Overview</span></span>
<span data-ttu-id="a4256-104">本節提供使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台管理 BizTalk 應用程式中的角色連結的指示。</span><span class="sxs-lookup"><span data-stu-id="a4256-104">This section provides instructions on using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to manage role links in a BizTalk application.</span></span> <span data-ttu-id="a4256-105">角色連結會定義參與商務交易的合作對象之間的關係，並指定用於雙向互動的訊息及連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="a4256-105">A role link defines the relationship between parties involved in a business transaction and specifies the message and port types used in the interaction in both directions.</span></span> <span data-ttu-id="a4256-106">如需角色連結的背景資訊，請參閱[協調流程中使用角色連結](../core/using-role-links-in-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="a4256-106">For background information on role links, see [Using Role Links in Orchestrations](../core/using-role-links-in-orchestrations.md).</span></span>  

## <a name="added-to-application"></a><span data-ttu-id="a4256-107">新增至應用程式</span><span class="sxs-lookup"><span data-stu-id="a4256-107">Added to application</span></span>  
 <span data-ttu-id="a4256-108">角色連結內建於 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，並且編譯成 BizTalk 組件。</span><span class="sxs-lookup"><span data-stu-id="a4256-108">Role links are built in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and compiled into BizTalk assemblies.</span></span> <span data-ttu-id="a4256-109">您無法將角色連結個別新增至應用程式；角色連結會在下列情況中新增至應用程式：</span><span class="sxs-lookup"><span data-stu-id="a4256-109">You cannot add role links to an application individually; a role link is added to an application as follows:</span></span>  
  
- <span data-ttu-id="a4256-110">當您新增 BizTalk 組件包含應用程式，角色連結中所述[如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a4256-110">When you add a BizTalk assembly containing a role link to the application, as described in [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span></span>  
  
- <span data-ttu-id="a4256-111">當您匯入.msi 檔案包含 BizTalk 組件包含角色連結，如中所述的應用程式[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a4256-111">When you import an .msi file into an application that includes a BizTalk assembly containing a role link, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).</span></span>  
  
- <span data-ttu-id="a4256-112">當開發人員部署至應用程式包含角色連結的組件[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]中所述[從 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a4256-112">When a developer deploys into an application an assembly containing a role link from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], as described in [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span></span>  

## <a name="deploy-to-production"></a><span data-ttu-id="a4256-113">部署到生產環境</span><span class="sxs-lookup"><span data-stu-id="a4256-113">Deploy to production</span></span>  
 <span data-ttu-id="a4256-114">BizTalk 應用程式開發人員會建立角色連結以實作兩個或更多參與商務交易的合作對象 (例如您的組織和供應商) 之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="a4256-114">The BizTalk application developer creates role links to implement communications between two or more parties involved in a business transaction, such as your organization and a supplier.</span></span> <span data-ttu-id="a4256-115">開發人員不一定要指定參與交易的合作對象，只需指定其角色即可。</span><span class="sxs-lookup"><span data-stu-id="a4256-115">The developer does not necessarily specify the parties that are involved in the transaction, only their roles.</span></span> <span data-ttu-id="a4256-116">若要將包含角色連結的應用程式部署到生產環境，並且在合作對象之間啟用實際的通訊，則必須執行下列組態，如本節中所述：</span><span class="sxs-lookup"><span data-stu-id="a4256-116">To deploy an application that includes a role link to a production environment and enable actual communication between the parties, the following configuration must be performed, as described in this section:</span></span>  
  
- <span data-ttu-id="a4256-117">如果未在開發程序中完成，則必須將合作對象指派給角色連結中定義的每個角色。</span><span class="sxs-lookup"><span data-stu-id="a4256-117">If it wasn't done during the development process, a party must be assigned to each role defined in the role link.</span></span> <span data-ttu-id="a4256-118">此即所謂「登錄」角色的合作對象。</span><span class="sxs-lookup"><span data-stu-id="a4256-118">This is called "enlisting" a party for a role.</span></span> <span data-ttu-id="a4256-119">如果您不想再讓合作對象具有指派的角色，則可以事後取消登錄該合作對象。</span><span class="sxs-lookup"><span data-stu-id="a4256-119">You can later unenlist the party if you no longer want the party to have the assigned role.</span></span>  
  
- <span data-ttu-id="a4256-120">角色連結內定義的每個合作對象的邏輯連接埠必須繫結至裝載應用程式之 BizTalk 主控件執行個體上的實體連接埠。</span><span class="sxs-lookup"><span data-stu-id="a4256-120">The logical ports for each party defined within the role link must be bound to physical ports on the BizTalk host instances that will host the application.</span></span>  
  
  <span data-ttu-id="a4256-121">如需有關如何開發角色連結的詳細資訊，請參閱[協調流程中使用角色連結](../core/using-role-links-in-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="a4256-121">For more information about developing role links, see [Using Role Links in Orchestrations](../core/using-role-links-in-orchestrations.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4256-122">您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。</span><span class="sxs-lookup"><span data-stu-id="a4256-122">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="a4256-123">如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="a4256-123">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="a4256-124">下一步</span><span class="sxs-lookup"><span data-stu-id="a4256-124">Next step</span></span>
  
-   [<span data-ttu-id="a4256-125">如何登錄或取消登錄角色的合作對象</span><span class="sxs-lookup"><span data-stu-id="a4256-125">How to Enlist or Unenlist a Party for a Role</span></span>](../core/how-to-enlist-or-unenlist-a-party-for-a-role.md)