---
title: 如何將應用程式的名稱變更 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- naming conventions, renaming
- naming conventions, applications
- applications, renaming
ms.assetid: ae59c792-44bd-43e0-a4ae-e67bcad2e128
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5620bc481f5350e752b71a1706e187016ed25977
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992439"
---
# <a name="how-to-change-the-name-of-an-application"></a><span data-ttu-id="6bd79-102">如何變更應用程式的名稱</span><span class="sxs-lookup"><span data-stu-id="6bd79-102">How to Change the Name of an Application</span></span>
<span data-ttu-id="6bd79-103">本主題將描述如何使用 BizTalk Server 管理主控台來變更應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="6bd79-103">This topic describes how to use the BizTalk Server Administration console to change the name of an application.</span></span> <span data-ttu-id="6bd79-104">您所使用的應用程式名稱不能已存在於群組中。</span><span class="sxs-lookup"><span data-stu-id="6bd79-104">The application name that you use cannot already exist in the group.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6bd79-105">如果您匯出的應用程式 .msi 檔案會參考此重新命名的應用程式，則當您匯入此 .msi 檔案時，該參考將無法再運作。</span><span class="sxs-lookup"><span data-stu-id="6bd79-105">If you have exported an .msi file for an application that has a reference to the renamed application, the reference will no longer function when you import the .msi file.</span></span> <span data-ttu-id="6bd79-106">您將需要使用新的應用程式名稱來更新此參考。</span><span class="sxs-lookup"><span data-stu-id="6bd79-106">You will need to update the reference with the new application name.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6bd79-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="6bd79-107">Prerequisites</span></span>  
 <span data-ttu-id="6bd79-108">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="6bd79-108">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="6bd79-109">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="6bd79-109">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-change-the-name-of-an-application"></a><span data-ttu-id="6bd79-110">若要變更應用程式的名稱</span><span class="sxs-lookup"><span data-stu-id="6bd79-110">To change the name of an application</span></span>  
  
1. <span data-ttu-id="6bd79-111">按一下 **開始**，指向**程式**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="6bd79-111">Click **Start**, point to **Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="6bd79-112">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，以滑鼠右鍵按一下您想要變更，然後按一下其名稱的應用程式**屬性**。</span><span class="sxs-lookup"><span data-stu-id="6bd79-112">In the console tree, expand  **BizTalk Server Administration**, right-click the application whose name you want to change, and click **Properties**.</span></span>  
  
3. <span data-ttu-id="6bd79-113">在 **名稱**方塊中，輸入新名稱，則應用程式，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="6bd79-113">In the **Name** box, type a new name for the application, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bd79-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bd79-114">See Also</span></span>  
 [<span data-ttu-id="6bd79-115">建立和修改 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="6bd79-115">Creating and Modifying BizTalk Applications</span></span>](../core/creating-and-modifying-biztalk-applications.md)