---
title: 匯入 BizTalk 應用程式、 繫結和原則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- importing, applications
- importing, policies
- applications, importing
- policies, importing
- importing, bindings
- bindings, importing
ms.assetid: 678bdb03-efaa-4053-9048-b71fc539d191
caps.latest.revision: 32
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18f7ea348fb34f4f8cc08e748799dcf8368a3c35
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256774"
---
# <a name="importing-biztalk-applications-bindings-and-policies"></a><span data-ttu-id="49641-102">匯入 BizTalk 應用程式、繫結和原則</span><span class="sxs-lookup"><span data-stu-id="49641-102">Importing BizTalk Applications, Bindings, and Policies</span></span>
<span data-ttu-id="49641-103">本節中的主題說明如何將 BizTalk 應用程式、繫結和原則匯入至 BizTalk 群組或應用程式中。</span><span class="sxs-lookup"><span data-stu-id="49641-103">The topics in this section describe how to import BizTalk applications, bindings and policies into a BizTalk group or application.</span></span> <span data-ttu-id="49641-104">中所述[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)，匯出應用程式會建立您可以再使用應用程式的成品匯入到不同的 BizTalk 群組中的應用程式的 Windows Installer (.msi) 檔案。</span><span class="sxs-lookup"><span data-stu-id="49641-104">As mentioned in [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md), exporting an application creates a Windows Installer (.msi) file that you can then use to import the application's artifacts into an application in a different BizTalk group.</span></span> <span data-ttu-id="49641-105">如果群組中沒有您指定匯入的應用程式，則會建立此應用程式。</span><span class="sxs-lookup"><span data-stu-id="49641-105">If the application that you specify for the import does not already exist in the group, the application is created.</span></span> <span data-ttu-id="49641-106">此外，也會註冊應用程式的成品，並且將其資料儲存在群組的 BizTalk 資料庫。</span><span class="sxs-lookup"><span data-stu-id="49641-106">In addition, application's artifacts are registered and their data stored in the BizTalk databases of the group.</span></span> <span data-ttu-id="49641-107">如需詳細資訊，請參閱[什麼發生時匯入成品](../core/what-happens-when-artifacts-are-imported.md)。</span><span class="sxs-lookup"><span data-stu-id="49641-107">For more information, see [What Happens When Artifacts Are Imported](../core/what-happens-when-artifacts-are-imported.md).</span></span>  
  
 <span data-ttu-id="49641-108">您也可以匯入到 BizTalk 群組或應用程式，從 BizTalk 群組、 應用程式或組件，您匯出的繫結中所述[匯出繫結](../core/exporting-bindings6.md)。</span><span class="sxs-lookup"><span data-stu-id="49641-108">You can also import into a BizTalk group or application the bindings that you exported from a BizTalk group, application, or assembly, as described in [Exporting Bindings](../core/exporting-bindings6.md).</span></span> <span data-ttu-id="49641-109">匯入繫結時，會覆寫 BizTalk 群組、應用程式或組件中任何同名的現有繫結。</span><span class="sxs-lookup"><span data-stu-id="49641-109">When you import bindings, they overwrite any bindings of the same name in the BizTalk group, application, or assembly.</span></span>  
  
 <span data-ttu-id="49641-110">此外，您可以匯入原則到您的 BizTalk 群組或應用程式，從匯出的 BizTalk 群組中所述[如何匯出原則](../core/how-to-export-a-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="49641-110">In addition, you can import a policy into a BizTalk group that you exported from a BizTalk group or application, as described in [How to Export a Policy](../core/how-to-export-a-policy.md).</span></span> <span data-ttu-id="49641-111">新群組中的應用程式就可以使用此原則。</span><span class="sxs-lookup"><span data-stu-id="49641-111">Applications in the new group can then use the policy.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="49641-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="49641-112">In This Section</span></span>  
  
-   [<span data-ttu-id="49641-113">如何匯入 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="49641-113">How to Import a BizTalk Application</span></span>](../core/how-to-import-a-biztalk-application.md)  
  
-   [<span data-ttu-id="49641-114">匯入繫結</span><span class="sxs-lookup"><span data-stu-id="49641-114">Importing Bindings</span></span>](../core/importing-bindings2.md)  
  
-   [<span data-ttu-id="49641-115">如何匯入原則</span><span class="sxs-lookup"><span data-stu-id="49641-115">How to Import a Policy</span></span>](../core/how-to-import-a-policy.md)