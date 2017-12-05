---
title: "如何將傳送埠新增至傳送埠群組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [send port groups], adding send ports
- managing [send ports], adding to send port groups
- send port groups, send ports
- send ports, send port groups
- adding, send ports
ms.assetid: a61b3b32-c05e-40b9-abf1-09b7065fb6a2
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3e10a16b31f5cc112e814faf119dc424c99ba67
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-add-a-send-port-to-a-send-port-group"></a><span data-ttu-id="8e54c-102">如何新增傳送埠至傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="8e54c-102">How to Add a Send Port to a Send Port Group</span></span>
<span data-ttu-id="8e54c-103">本主題描述如何使用 BizTalk Server 管理主控台，將一個或多個傳送埠新增至傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="8e54c-103">This topic describes how to use the BizTalk Server Administration console to add one or more send ports to a send port group.</span></span> <span data-ttu-id="8e54c-104">您只能在傳送埠群組中新增單向靜態傳送埠。</span><span class="sxs-lookup"><span data-stu-id="8e54c-104">You can only add one-way static send ports to a send port group.</span></span>  
  
 <span data-ttu-id="8e54c-105">您可以新增存在於不同應用程式的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="8e54c-105">You can add a send port that exists in a different application.</span></span> <span data-ttu-id="8e54c-106">如果您這麼做，則必須從包含傳送埠群組的應用程式將參考新增到包含傳送埠的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8e54c-106">If you do this, you must add a reference from the application containing the send port group to the application containing the send port.</span></span> <span data-ttu-id="8e54c-107">如需指示，請參閱[如何加入另一個應用程式的參考](../core/how-to-add-a-reference-to-another-application.md)。</span><span class="sxs-lookup"><span data-stu-id="8e54c-107">For instructions, see [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8e54c-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="8e54c-108">Prerequisites</span></span>  
 <span data-ttu-id="8e54c-109">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="8e54c-109">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="8e54c-110">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="8e54c-110">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-add-a-send-port-to-a-send-port-group"></a><span data-ttu-id="8e54c-111">在傳送埠群組新增傳送埠</span><span class="sxs-lookup"><span data-stu-id="8e54c-111">To add a send port to a send port group</span></span>  
  
1.  <span data-ttu-id="8e54c-112">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="8e54c-112">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="8e54c-113">在主控台樹狀結構中，展開您要在其中將傳送埠新增至埠群組的 BizTalk 群組和 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8e54c-113">In the console tree, expand the BizTalk group and the BizTalk application in which you want to add a send port to a send port group.</span></span>  
  
3.  <span data-ttu-id="8e54c-114">按一下**傳送埠群組**，以滑鼠右鍵按一下傳送埠群組，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="8e54c-114">Click **Send Port Groups**, right-click the send port group, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="8e54c-115">在**傳送埠**，按一下底下的下拉式清單**名稱**，然後按一下要新增傳送埠至傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="8e54c-115">In **Send ports**, click the drop-down list under **Name**, and click the send port to add to the send port group.</span></span> <span data-ttu-id="8e54c-116">請為每個要新增至群組的傳送埠執行同樣的步驟。</span><span class="sxs-lookup"><span data-stu-id="8e54c-116">Repeat for each send port you want to add to the group.</span></span> <span data-ttu-id="8e54c-117">若要建立新的傳送埠，並將它加入，請按一下**\<新傳送埠...\>**  ，然後依照中的指示[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。</span><span class="sxs-lookup"><span data-stu-id="8e54c-117">To create a new send port and add it, click **\<New send port…\>** and then follow the instructions in [How to Create a Send Port](../core/how-to-create-a-send-port2.md).</span></span>  
  
5.  <span data-ttu-id="8e54c-118">完成新增傳送埠至傳送埠群組，請按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="8e54c-118">When finished adding send ports to the send port group, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e54c-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="8e54c-119">See Also</span></span>  
 <span data-ttu-id="8e54c-120">[建立和設定傳送埠群組](../core/creating-and-configuring-send-port-groups.md) </span><span class="sxs-lookup"><span data-stu-id="8e54c-120">[Creating and Configuring Send Port Groups](../core/creating-and-configuring-send-port-groups.md) </span></span>  
 [<span data-ttu-id="8e54c-121">建立和設定傳送埠</span><span class="sxs-lookup"><span data-stu-id="8e54c-121">Creating and Configuring Send Ports</span></span>](../core/creating-and-configuring-send-ports.md)