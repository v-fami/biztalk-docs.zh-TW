---
title: 如何刪除接收位置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [receive locations], deleting
- receive locations, deleting
- deleting, receive locations
ms.assetid: aa859355-af4c-48d9-b224-78fd3ef618fc
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3acc788e1c0bfeb9e722aee0b55d66e6f09d096
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991439"
---
# <a name="how-to-delete-a-receive-location"></a><span data-ttu-id="15876-102">如何刪除接收位置</span><span class="sxs-lookup"><span data-stu-id="15876-102">How to Delete a Receive Location</span></span>
<span data-ttu-id="15876-103">本主題描述如何使用 BizTalk Server 管理主控台來刪除接收位置。</span><span class="sxs-lookup"><span data-stu-id="15876-103">This topic describes how to use the BizTalk Server Administration console to delete a receive location.</span></span> <span data-ttu-id="15876-104">當您刪除接收位置時，它會從 BizTalk 管理資料庫中移除，而且不再顯示於 BizTalk Server 管理主控台中。</span><span class="sxs-lookup"><span data-stu-id="15876-104">When you delete a receive location, it is removed from the BizTalk Management database and is no longer displayed in the BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="15876-105">當您刪除接收位置時，請牢記下列要點：</span><span class="sxs-lookup"><span data-stu-id="15876-105">When deleting a receive location, bear in mind the following important points:</span></span>  
  
-   <span data-ttu-id="15876-106">您可以刪除接收位置之前，它必須先停用，如中所述[如何停用接收位置](../core/how-to-disable-a-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="15876-106">Before you can delete a receive location, it must first be disabled, as described in [How to Disable a Receive Location](../core/how-to-disable-a-receive-location.md).</span></span>  
  
-   <span data-ttu-id="15876-107">您不能刪除接收埠的主要接收位置。</span><span class="sxs-lookup"><span data-stu-id="15876-107">You cannot delete the primary receive location for a receive port.</span></span> <span data-ttu-id="15876-108">若嘗試這麼做，將收到一個錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="15876-108">If you attempt this, you will receive an error message.</span></span> <span data-ttu-id="15876-109">若要刪除此接收位置，您可以刪除接收埠 (這同時會刪除它所包含的所有接收位置)，或者您也可以指定其他接收位置做為主要接收位置，然後再刪除原始接收位置。</span><span class="sxs-lookup"><span data-stu-id="15876-109">To delete the receive location, you can either delete the receive port, which also deletes all of the receive locations that it contains, or you can make a different receive location primary and then delete the original receive location.</span></span> <span data-ttu-id="15876-110">如需接收位置建立為主要接收位置的指示，請參閱 <<c0> [ 如何編輯接收位置屬性](../core/how-to-edit-the-properties-of-a-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="15876-110">For instructions on making a receive location the primary receive location, see [How to Edit the Properties of a Receive Location](../core/how-to-edit-the-properties-of-a-receive-location.md).</span></span>  
  
-   <span data-ttu-id="15876-111">在您刪除接收位置之後，請重新啟動與所刪除接收位置對應的外掛式主控件工作者處理序。</span><span class="sxs-lookup"><span data-stu-id="15876-111">After you delete a receive location, restart the Isolated Host Worker Processes corresponding to the deleted receive location.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="15876-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="15876-112">Prerequisites</span></span>  
 <span data-ttu-id="15876-113">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="15876-113">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="15876-114">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="15876-114">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-delete-a-receive-location"></a><span data-ttu-id="15876-115">若要刪除接收位置</span><span class="sxs-lookup"><span data-stu-id="15876-115">To delete a receive location</span></span>  
  
1. <span data-ttu-id="15876-116">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="15876-116">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="15876-117">在主控台樹狀目錄中，展開您要刪除其接收位置的 BizTalk 群組和 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="15876-117">In the console tree, expand the BizTalk group and the BizTalk application for which you want to delete a receive location.</span></span>  
  
3. <span data-ttu-id="15876-118">按一下 **接收位置**，以滑鼠右鍵按一下接收位置，以刪除，然後按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="15876-118">Click **Receive Locations**, right-click the receive location to delete, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15876-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15876-119">See Also</span></span>  
 [<span data-ttu-id="15876-120">管理接收位置</span><span class="sxs-lookup"><span data-stu-id="15876-120">Managing Receive Locations</span></span>](../core/managing-receive-locations.md)