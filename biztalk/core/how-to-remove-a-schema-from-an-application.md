---
title: 如何從應用程式移除結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deleting, schemas
- applications, schemas
- schemas, deleting
- managing [schemas], deleting
- managing [schemas], applications
- schemas, applications
ms.assetid: 17dd5869-b56c-4166-9f02-03e04e691eda
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6535764af00156325c006388a88803207329e5fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254646"
---
# <a name="how-to-remove-a-schema-from-an-application"></a><span data-ttu-id="ffb6f-102">如何從應用程式移除結構描述</span><span class="sxs-lookup"><span data-stu-id="ffb6f-102">How to Remove a Schema from an Application</span></span>
<span data-ttu-id="ffb6f-103">本主題說明如何使用 BizTalk Server 管理主控台，從應用程式移除結構描述。</span><span class="sxs-lookup"><span data-stu-id="ffb6f-103">This topic describes how to use the BizTalk Server Administration console to remove a schema from an application.</span></span> <span data-ttu-id="ffb6f-104">這個程序也會從群組的 BizTalk 管理資料庫中移除結構描述。</span><span class="sxs-lookup"><span data-stu-id="ffb6f-104">This procedure removes the schema from the BizTalk Management database for the group as well.</span></span> <span data-ttu-id="ffb6f-105">您可能會想要在部署新版的結構描述之後，移除結構描述。</span><span class="sxs-lookup"><span data-stu-id="ffb6f-105">You might want to remove a schema after deploying a new version of the schema.</span></span> <span data-ttu-id="ffb6f-106">如需詳細資訊和更新應用程式成品的重要考量，請參閱[更新 BizTalk 應用程式](../core/updating-biztalk-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="ffb6f-106">For more information and important considerations for updating application artifacts, see [Updating BizTalk Applications](../core/updating-biztalk-applications.md).</span></span>  
  
 <span data-ttu-id="ffb6f-107">當您移除結構描述時，如果某個先前版本的結構描述具有存在於應用程式中的相同根命名空間，這個版本便會成為作用中的版本。</span><span class="sxs-lookup"><span data-stu-id="ffb6f-107">When you remove a schema, and a previous version of the schema having the same root namespace exists in the application, the previous version will become active.</span></span>  
  
 <span data-ttu-id="ffb6f-108">當您移除結構描述時，會發生下列情況：</span><span class="sxs-lookup"><span data-stu-id="ffb6f-108">When you remove a schema, the following occurs:</span></span>  
  
-   <span data-ttu-id="ffb6f-109">從 BizTalk 管理資料庫中刪除結構描述。</span><span class="sxs-lookup"><span data-stu-id="ffb6f-109">The schema is deleted from the BizTalk Management database.</span></span>  
  
-   <span data-ttu-id="ffb6f-110">包含結構描述的 BizTalk 組件會從 BizTalk 管理資料庫中刪除，但是不會從本機檔案系統或全域組件快取 (GAC) 中移除 (如果存在於這些位置)。</span><span class="sxs-lookup"><span data-stu-id="ffb6f-110">The BizTalk assembly that contains the schema is deleted from the BizTalk Management database, but is not removed from the local file system or the global assembly cache (GAC), if it exists in these locations.</span></span>  
  
-   <span data-ttu-id="ffb6f-111">由於會刪除 BizTalk 組件，所以包含在組件中的所有成品也會從 BizTalk 管理資料庫中移除。</span><span class="sxs-lookup"><span data-stu-id="ffb6f-111">As a consequence of the BizTalk assembly being deleted, all artifacts contained in the assembly are removed deleted the BizTalk Management database as well.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ffb6f-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="ffb6f-112">Prerequisites</span></span>  
 <span data-ttu-id="ffb6f-113">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="ffb6f-113">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="ffb6f-114">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="ffb6f-114">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-remove-a-schema"></a><span data-ttu-id="ffb6f-115">若要移除結構描述</span><span class="sxs-lookup"><span data-stu-id="ffb6f-115">To remove a schema</span></span>  
  
1.  <span data-ttu-id="ffb6f-116">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="ffb6f-116">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="ffb6f-117">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組包含結構描述移除與包含結構描述的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ffb6f-117">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the schema to remove and the application containing the schema.</span></span>  
  
3.  <span data-ttu-id="ffb6f-118">按一下**結構描述**，結構描述中，以滑鼠右鍵按一下，然後按一下**移除**。</span><span class="sxs-lookup"><span data-stu-id="ffb6f-118">Click **Schemas**, right-click the schema, and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffb6f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffb6f-119">See Also</span></span>  
 [<span data-ttu-id="ffb6f-120">管理結構描述</span><span class="sxs-lookup"><span data-stu-id="ffb6f-120">Managing Schemas</span></span>](../core/managing-schemas.md)