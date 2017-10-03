---
title: "如何建立傳送埠群組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, send port groups
- send port groups, creating
- managing [send port groups], creating
ms.assetid: de3e72aa-83f4-4760-9f39-a488f904f1d3
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f308c950d56569c06403df1394580302089a453e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-send-port-group"></a><span data-ttu-id="752c1-102">如何建立傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="752c1-102">How to Create a Send Port Group</span></span>
<span data-ttu-id="752c1-103">本主題描述如何使用 BizTalk Server 管理主控台，在 BizTalk 應用程式中建立傳送埠群組，然後在其中新增傳送埠。</span><span class="sxs-lookup"><span data-stu-id="752c1-103">This topic describes how to use the BizTalk Server Administration console to create a send port group in a BizTalk application and then add send ports to it.</span></span> <span data-ttu-id="752c1-104">您只能將靜態單向傳送埠新增到傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="752c1-104">You can add static one-way send ports only to a send port group.</span></span> <span data-ttu-id="752c1-105">傳送埠群組必須包含至少一個傳送埠，才能路由訊息。</span><span class="sxs-lookup"><span data-stu-id="752c1-105">A send port group must contain at least one send port to route messages.</span></span>  
  
 <span data-ttu-id="752c1-106">您可以新增存在於不同應用程式的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="752c1-106">You can add a send port that exists in a different application.</span></span> <span data-ttu-id="752c1-107">如果您這麼做，則必須從包含傳送埠群組的應用程式將參考新增到包含傳送埠的應用程式。</span><span class="sxs-lookup"><span data-stu-id="752c1-107">If you do this, you must add a reference from the application containing the send port group to the application containing the send port.</span></span> <span data-ttu-id="752c1-108">如需指示，請參閱[如何加入另一個應用程式的參考](../core/how-to-add-a-reference-to-another-application.md)。</span><span class="sxs-lookup"><span data-stu-id="752c1-108">For instructions, see [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="752c1-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="752c1-109">Prerequisites</span></span>  
 <span data-ttu-id="752c1-110">若要執行本主題中的程序，您必須為 BizTalk Server 系統管理員群組的成員登入。</span><span class="sxs-lookup"><span data-stu-id="752c1-110">To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="752c1-111">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="752c1-111">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-create-a-send-port-group"></a><span data-ttu-id="752c1-112">建立傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="752c1-112">To create a send port group</span></span>  
  
1.  <span data-ttu-id="752c1-113">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="752c1-113">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="752c1-114">在主控台樹狀結構中，展開您要在其中建立傳送埠群組的 BizTalk 群組與 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="752c1-114">In the console tree, expand the BizTalk group and the BizTalk application in which you want to create a send port group.</span></span>  
  
3.  <span data-ttu-id="752c1-115">以滑鼠右鍵按一下**傳送埠群組**，指向 **新增**，然後按一下 **傳送埠群組**。</span><span class="sxs-lookup"><span data-stu-id="752c1-115">Right-click **Send Port Groups**, point to **New**, and then click **Send Port Group**.</span></span>  
  
4.  <span data-ttu-id="752c1-116">在**名稱**方塊中，輸入傳送埠群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="752c1-116">In the **Name** box, type a name for the send port group.</span></span>  
  
5.  <span data-ttu-id="752c1-117">在**傳送埠**，按一下底下的下拉式清單**名稱**，然後按一下要新增傳送埠至傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="752c1-117">In **Send ports**, click the drop-down list under **Name**, and click the send port to add to the send port group.</span></span> <span data-ttu-id="752c1-118">請為每個要新增至群組的傳送埠執行同樣的步驟。</span><span class="sxs-lookup"><span data-stu-id="752c1-118">Repeat for each send port you want to add to the group.</span></span> <span data-ttu-id="752c1-119">若要建立新的傳送埠，並將它加入，請按一下**\<新傳送埠...>** ，然後依照中的指示[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。</span><span class="sxs-lookup"><span data-stu-id="752c1-119">To create a new send port and add it, click **\<New send port…>** and then follow the instructions in [How to Create a Send Port](../core/how-to-create-a-send-port2.md).</span></span>  
  
6.  <span data-ttu-id="752c1-120">完成新增傳送埠至傳送埠群組，請按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="752c1-120">When finished adding send ports to the send port group, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="752c1-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="752c1-121">See Also</span></span>  
 [<span data-ttu-id="752c1-122">建立和設定傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="752c1-122">Creating and Configuring Send Port Groups</span></span>](../core/creating-and-configuring-send-port-groups.md)