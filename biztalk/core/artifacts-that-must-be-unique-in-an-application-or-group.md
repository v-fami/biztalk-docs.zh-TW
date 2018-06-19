---
title: 中的應用程式或群組必須是唯一的成品 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- groups, artifacts
- artifacts, requirements
- applications, artifacts
ms.assetid: a758cd74-a962-4e75-aea2-47752ab72a64
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfe9ff033621ed491b7f1deae9e3f2e467e54f83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230382"
---
# <a name="artifacts-that-must-be-unique-in-an-application-or-group"></a><span data-ttu-id="79f44-102">在應用程式或群組中必須是唯一的成品</span><span class="sxs-lookup"><span data-stu-id="79f44-102">Artifacts That Must Be Unique in an Application or Group</span></span>
<span data-ttu-id="79f44-103">BizTalk 群組或應用程式中某些類型的成品必須是唯一的，如下所示：</span><span class="sxs-lookup"><span data-stu-id="79f44-103">Certain types of artifacts in a BizTalk group or application must be unique, as follows:</span></span>  
  
-   <span data-ttu-id="79f44-104">BizTalk 組件和非 BizTalk .NET 組件在此群組中都必須有唯一的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="79f44-104">Both BizTalk assemblies and non-BizTalk .NET assemblies must have a unique full name in the group.</span></span> <span data-ttu-id="79f44-105">完整名稱是由檔案名稱、公開金鑰語彙基元、文化特性和版本所組成。</span><span class="sxs-lookup"><span data-stu-id="79f44-105">The full name consists of a file name, public key token, culture, and version.</span></span>  
  
-   <span data-ttu-id="79f44-106">規則和原則在此群組中都必須有唯一的名稱和版本號碼。</span><span class="sxs-lookup"><span data-stu-id="79f44-106">Rules and policies must have a unique name and version number in the group.</span></span>  
  
-   <span data-ttu-id="79f44-107">傳送埠、傳送埠群組、接收埠和接收位置在此群組中必須有唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="79f44-107">Send ports, send port groups, receive ports, and receive locations must have a unique name in the group.</span></span>  
  
-   <span data-ttu-id="79f44-108">網站在此群組中必須有唯一的虛擬目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="79f44-108">Web sites must have a unique virtual directory name in the group.</span></span>  
  
-   <span data-ttu-id="79f44-109">BAM 資源在此群組中必須有唯一的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="79f44-109">BAM resources must have a unique file name in the group.</span></span>  
  
-   <span data-ttu-id="79f44-110">憑證在此群組中必須有唯一的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="79f44-110">Certificates must have a unique thumbprint in the group.</span></span>  
  
-   <span data-ttu-id="79f44-111">COM 元件在此群組中必須有唯一的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="79f44-111">COM components must have a unique file name in the group.</span></span>  
  
-   <span data-ttu-id="79f44-112">以檔案為基礎的成品 (如指令碼和其他一般檔案) 在應用程式中必須有唯一的檔案名稱 (而不是在此群組中)。</span><span class="sxs-lookup"><span data-stu-id="79f44-112">File-based artifacts, such as scripts and other flat files, must have unique file names in the application, but not in the group.</span></span>  
  
 <span data-ttu-id="79f44-113">如果某成品已經存在於應用程式中，而且其類型在應用程式中必須是唯一的，您可以指定覆寫選項來匯入或新增此成品至應用程式。</span><span class="sxs-lookup"><span data-stu-id="79f44-113">You can specify the overwrite option to import or add an artifact to an application if the artifact already exists in the application and it is of a type that must be unique in an application.</span></span> <span data-ttu-id="79f44-114">如果此成品已經存在於此群組的另一個應用程式中，而且其類型在此群組中必須是唯一的，您將無法新增或匯入它。</span><span class="sxs-lookup"><span data-stu-id="79f44-114">If the artifact already exists in another application in the group, and it is a type that must be unique in the group, you can neither add nor import it.</span></span>  
  
 <span data-ttu-id="79f44-115">如果您需要使用某個應用程式中的成品，而且它已經存在於此群組的另一個應用程式中，您可以建立一個參考，使其參考包含此成品的應用程式。</span><span class="sxs-lookup"><span data-stu-id="79f44-115">If you need to use an artifact in one application and it already exists in another application in the group, you can create a reference to the application containing the artifact.</span></span> <span data-ttu-id="79f44-116">如需詳細資訊，請參閱[如何加入另一個應用程式的參考](../core/how-to-add-a-reference-to-another-application.md)。</span><span class="sxs-lookup"><span data-stu-id="79f44-116">For more information see [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79f44-117">您可以檢視大部分成品類型的完整名稱的應用程式中使用 BTSTask 的 ListApp 命令中所述[ListApp 命令](../core/listapp-command.md)。</span><span class="sxs-lookup"><span data-stu-id="79f44-117">You can view the full name of most types of artifacts in an application by using the ListApp command of BTSTask, as described in [ListApp Command](../core/listapp-command.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79f44-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79f44-118">See Also</span></span>  
 [<span data-ttu-id="79f44-119">了解 BizTalk 應用程式部署和管理</span><span class="sxs-lookup"><span data-stu-id="79f44-119">Understanding BizTalk Application Deployment and Management</span></span>](../core/understanding-biztalk-application-deployment-and-management.md)