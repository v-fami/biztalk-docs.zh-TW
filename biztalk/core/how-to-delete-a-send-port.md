---
title: 如何刪除傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [send ports], deleting
- send ports, deleting
- deleting, send ports
ms.assetid: aff5980e-57bf-400c-82bd-3d02e143f227
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7fd1bdab77761787cef404f318d2965f68e3a8c6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973203"
---
# <a name="how-to-delete-a-send-port"></a><span data-ttu-id="e7ac2-102">如何刪除傳送埠</span><span class="sxs-lookup"><span data-stu-id="e7ac2-102">How to Delete a Send Port</span></span>
<span data-ttu-id="e7ac2-103">本主題描述如何使用 BizTalk Server 管理主控台，從 BizTalk 應用程式中刪除傳送埠。</span><span class="sxs-lookup"><span data-stu-id="e7ac2-103">This topic describes how to use the BizTalk Server Administration console to delete a send port from a BizTalk application.</span></span> <span data-ttu-id="e7ac2-104">這樣做也會從群組的 BizTalk 管理資料庫中刪除傳送埠。</span><span class="sxs-lookup"><span data-stu-id="e7ac2-104">When you do this, the send port is also deleted from the BizTalk Management database for the group.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e7ac2-105">移除傳送埠時，與該連接埠關聯的任何執行中服務執行個體可能再也無法取得傳送埠的相關資訊，例如傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="e7ac2-105">When you delete a send port, any running service instances associated with that port can no longer obtain configuration information about the send port, such as its name.</span></span> <span data-ttu-id="e7ac2-106">雖然這項資訊是由快取得來，但若是服務執行個體必須重新傳送訊息，則此執行個體將無法完成，而訊息也會被擱置。</span><span class="sxs-lookup"><span data-stu-id="e7ac2-106">Although this information is cached, if the service instance must resend a message, it will not be able to complete, and the message will be suspended.</span></span> <span data-ttu-id="e7ac2-107">然後再刪除傳送埠，您應該確認沒有任何執行中所述，服務執行個體，[如何檢視傳送埠的執行個體資訊](../core/how-to-view-instance-information-for-a-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="e7ac2-107">Before deleting a send port, you should verify that there are no running service instances, as described in [How to View Instance Information for a Send Port](../core/how-to-view-instance-information-for-a-send-port.md).</span></span>  
  
 <span data-ttu-id="e7ac2-108">您只有在符合下列條件時，才可以刪除傳送埠：</span><span class="sxs-lookup"><span data-stu-id="e7ac2-108">You can delete a send port only if it meets the following conditions:</span></span>  
  
-   <span data-ttu-id="e7ac2-109">沒有協調流程繫結至此傳送埠。</span><span class="sxs-lookup"><span data-stu-id="e7ac2-109">An orchestration is not bound to the send port.</span></span> <span data-ttu-id="e7ac2-110">如果發生這種情況，您可以依照下列中的指示移除繫結[如何解除繫結協調流程](../core/how-to-unbind-an-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="e7ac2-110">If this is the case, you can remove the binding by following the instructions in [How to Unbind an Orchestration](../core/how-to-unbind-an-orchestration.md).</span></span>  
  
-   <span data-ttu-id="e7ac2-111">已停止並取消登錄此傳送埠。</span><span class="sxs-lookup"><span data-stu-id="e7ac2-111">The send port is both stopped and unenlisted.</span></span> <span data-ttu-id="e7ac2-112">如需停止及取消登錄傳送埠的指示，請參閱 <<c0> [ 如何取消登錄傳送埠或傳送埠群組](../core/how-to-unenlist-a-send-port-or-send-port-group.md)並[如何停止傳送埠或傳送埠群組](../core/how-to-stop-a-send-port-or-send-port-group.md)。</span><span class="sxs-lookup"><span data-stu-id="e7ac2-112">For instructions on stopping and unenlisting a send port, see [How to Unenlist a Send Port or Send Port Group](../core/how-to-unenlist-a-send-port-or-send-port-group.md) and [How to Stop a Send Port or Send Port Group](../core/how-to-stop-a-send-port-or-send-port-group.md).</span></span>  
  
-   <span data-ttu-id="e7ac2-113">沒有合作對象參考此傳送埠。</span><span class="sxs-lookup"><span data-stu-id="e7ac2-113">The send port is not referenced by a party.</span></span> <span data-ttu-id="e7ac2-114">如需移除合作對象的傳送埠的參考的指示，請參閱[如何檢視或編輯合作對象](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca)。</span><span class="sxs-lookup"><span data-stu-id="e7ac2-114">For instructions on removing a reference to a send port from a party, see [How to View or Edit a Party](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca).</span></span>  
  
-   <span data-ttu-id="e7ac2-115">此傳送埠沒有包含在傳送埠群組中。</span><span class="sxs-lookup"><span data-stu-id="e7ac2-115">The send port is not included in a send port group.</span></span> <span data-ttu-id="e7ac2-116">如需從傳送埠群組移除傳送埠的指示，請參閱 <<c0> [ 如何從傳送埠群組移除傳送埠](../core/how-to-remove-a-send-port-from-a-send-port-group.md)。</span><span class="sxs-lookup"><span data-stu-id="e7ac2-116">For instructions on removing a send port from a send port group, see [How to Remove a Send Port from a Send Port Group](../core/how-to-remove-a-send-port-from-a-send-port-group.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7ac2-117">應用程式開發人員可以使用本主題中的程序，以刪除在開發程序的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="e7ac2-117">The application developer can delete a send port during the development process by using the procedure in this topic.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e7ac2-118">必要條件</span><span class="sxs-lookup"><span data-stu-id="e7ac2-118">Prerequisites</span></span>  
 <span data-ttu-id="e7ac2-119">若要執行本主題中的程序，您必須為 BizTalk Server 系統管理員群組的成員登入。</span><span class="sxs-lookup"><span data-stu-id="e7ac2-119">To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="e7ac2-120">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="e7ac2-120">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-delete-a-send-port"></a><span data-ttu-id="e7ac2-121">刪除傳送埠</span><span class="sxs-lookup"><span data-stu-id="e7ac2-121">To delete a send port</span></span>  
  
1. <span data-ttu-id="e7ac2-122">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="e7ac2-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="e7ac2-123">在主控台樹狀目錄中，展開 BizTalk Server 管理、 BizTalk 群組、 展開 應用程式，然後展開包含您想要刪除的傳送埠的應用程式</span><span class="sxs-lookup"><span data-stu-id="e7ac2-123">In the console tree, expand BizTalk Server Administration, expand the BizTalk group, expand Applications, and then expand the application containing the send port that you want to delete</span></span>  
  
3. <span data-ttu-id="e7ac2-124">按一下 **傳送埠**，以滑鼠右鍵按一下傳送埠，然後按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="e7ac2-124">Click **Send Ports**, right-click the send port, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7ac2-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7ac2-125">See Also</span></span>  
 [<span data-ttu-id="e7ac2-126">建立和設定傳送埠</span><span class="sxs-lookup"><span data-stu-id="e7ac2-126">Creating and Configuring Send Ports</span></span>](../core/creating-and-configuring-send-ports.md)