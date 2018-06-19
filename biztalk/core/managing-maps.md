---
title: 管理對應 |Microsoft 文件
description: 將在 BizTalk Server 中，包括檢視和移除對應的對應連結
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0e8e3057-5a9f-4b6b-b6ee-c71b7e6a51ac
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c86a1cd23fe8f06c2671be163409cd405e9cbe1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263126"
---
# <a name="manage-maps"></a><span data-ttu-id="65fad-103">管理對應</span><span class="sxs-lookup"><span data-stu-id="65fad-103">Manage Maps</span></span>

## <a name="overview"></a><span data-ttu-id="65fad-104">概觀</span><span class="sxs-lookup"><span data-stu-id="65fad-104">Overview</span></span>
<span data-ttu-id="65fad-105">本節提供使用 BizTalk Server 管理主控台管理對應的指示。</span><span class="sxs-lookup"><span data-stu-id="65fad-105">This section provides instructions on managing maps by using the BizTalk Server Administration console.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="65fad-106">您可以使用對應來轉譯的記錄和記錄的一個結構描述中的欄位和另一個結構描述中的欄位。</span><span class="sxs-lookup"><span data-stu-id="65fad-106"> uses maps to translate the records and fields in one schema to the records and fields in another schema.</span></span> <span data-ttu-id="65fad-107">對應可供協調流程、傳送埠和接收埠使用。</span><span class="sxs-lookup"><span data-stu-id="65fad-107">Maps may be used by orchestrations, send ports, and receive ports.</span></span>  

## <a name="add-maps-to-an-application"></a><span data-ttu-id="65fad-108">將地圖加入至應用程式</span><span class="sxs-lookup"><span data-stu-id="65fad-108">Add maps to an application</span></span>  
 <span data-ttu-id="65fad-109">對應內建於 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，並被編譯到 BizTalk 組件中。</span><span class="sxs-lookup"><span data-stu-id="65fad-109">Maps are built in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and compiled into BizTalk assemblies.</span></span> <span data-ttu-id="65fad-110">您無法將對應個別新增至應用程式；對應會在下列情況中新增至應用程式：</span><span class="sxs-lookup"><span data-stu-id="65fad-110">You cannot add a map to an application individually; a map is added to an application as follows:</span></span>  
  
-   <span data-ttu-id="65fad-111">當您將加入含有應用程式，對應的 BizTalk 組件中所述[如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="65fad-111">When you add a BizTalk assembly containing a map to the application, as described in [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span></span>  
  
-   <span data-ttu-id="65fad-112">當您匯入.msi 檔案中所述，包含 BizTalk 組件包含對應的應用程式[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="65fad-112">When you import an .msi file into an application that includes a BizTalk assembly containing a map, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).</span></span>  
  
-   <span data-ttu-id="65fad-113">當開發人員應用程式組件部署到包含從對應[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]中所述，[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="65fad-113">When a developer deploys into an application an assembly containing a map from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], as described in [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span></span>  
  
 <span data-ttu-id="65fad-114">如需對應的背景資訊，請參閱[對應](../core/maps.md)。</span><span class="sxs-lookup"><span data-stu-id="65fad-114">For background information about maps, see [Maps](../core/maps.md).</span></span> <span data-ttu-id="65fad-115">如需建立對應資訊，請參閱[建立對應使用 BizTalk 對應工具](../core/creating-maps-using-biztalk-mapper.md)。</span><span class="sxs-lookup"><span data-stu-id="65fad-115">For information about creating maps, see [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65fad-116">您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。</span><span class="sxs-lookup"><span data-stu-id="65fad-116">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="65fad-117">如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="65fad-117">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="65fad-118">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="65fad-118">Next steps</span></span> 
  
-   [<span data-ttu-id="65fad-119">檢視應用程式的對應</span><span class="sxs-lookup"><span data-stu-id="65fad-119">View the Maps for an Application</span></span>](../core/how-to-view-the-maps-for-an-application.md)  
  
-   [<span data-ttu-id="65fad-120">從應用程式中移除對應</span><span class="sxs-lookup"><span data-stu-id="65fad-120">Remove a Map from an Application</span></span>](../core/how-to-remove-a-map-from-an-application.md)