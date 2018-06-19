---
title: 如何設定傳送埠備份傳輸選項 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, send ports
- managing [send ports], configuring
- configuring, backing up [send ports]
- managing [send ports], backup options
- send ports, configuring
- send ports, backup options
ms.assetid: f05f57a6-e62b-4640-a6e2-cb73e9de2a14
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ff8b1354772290ce9e04742a6130a6f6f2df627
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248374"
---
# <a name="how-to-configure-backup-transport-options-for-a-send-port"></a><span data-ttu-id="01488-102">如何設定傳送埠的備份傳輸選項</span><span class="sxs-lookup"><span data-stu-id="01488-102">How to Configure Backup Transport Options for a Send Port</span></span>
<span data-ttu-id="01488-103">本主題描述如何使用 BizTalk Server 管理主控台來設定傳送埠的備份傳輸選項。</span><span class="sxs-lookup"><span data-stu-id="01488-103">This topic describes how to use the BizTalk Server Administration console to configure backup transport options for a send port.</span></span> <span data-ttu-id="01488-104">您指定的備份傳輸會在主要傳輸無法運作時生效。</span><span class="sxs-lookup"><span data-stu-id="01488-104">The backup transport that you specify takes effect in the event the primary transport fails to function.</span></span> <span data-ttu-id="01488-105">設定主要傳輸所述[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。</span><span class="sxs-lookup"><span data-stu-id="01488-105">Configuring the primary transport is described in [How to Create a Send Port](../core/how-to-create-a-send-port2.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01488-106">因為傳輸選項是在執行階段自動決定的，動態連接埠沒有可供設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="01488-106">For dynamic ports, there are not properties available to configure because transport options are automatically determined at run time.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="01488-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="01488-107">Prerequisites</span></span>  
 <span data-ttu-id="01488-108">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="01488-108">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="01488-109">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="01488-109">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-specify-transport-options-for-a-send-port"></a><span data-ttu-id="01488-110">指定傳送埠的傳輸選項</span><span class="sxs-lookup"><span data-stu-id="01488-110">To specify transport options for a send port</span></span>  
  
1.  <span data-ttu-id="01488-111">按一下**啟動**，按一下 **程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="01488-111">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="01488-112">在主控台樹狀結構中，展開您要為其設定傳送埠備份傳輸選項的 BizTalk 群組與 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="01488-112">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure backup transport options for a send port.</span></span>  
  
3.  <span data-ttu-id="01488-113">展開**傳送埠**，以滑鼠右鍵按一下傳送埠設定，請按一下**屬性**，然後按一下 **備份傳輸**。</span><span class="sxs-lookup"><span data-stu-id="01488-113">Expand **Send Ports**, right-click the send port to configure, click **Properties**, and then click **Backup Transport**.</span></span>  
  
4.  <span data-ttu-id="01488-114">下表中所述，設定備份傳輸選項，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="01488-114">Configure backup transport properties as described in the following table, and then click **OK**.</span></span>  
  
    |<span data-ttu-id="01488-115">使用</span><span class="sxs-lookup"><span data-stu-id="01488-115">Use this</span></span>|<span data-ttu-id="01488-116">動作</span><span class="sxs-lookup"><span data-stu-id="01488-116">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="01488-117">**型別**</span><span class="sxs-lookup"><span data-stu-id="01488-117">**Type**</span></span>|<span data-ttu-id="01488-118">從下拉式清單選取適當的備份傳輸類型或傳輸通訊協定。</span><span class="sxs-lookup"><span data-stu-id="01488-118">From the drop-down list, select the appropriate backup transport type, or transport protocol.</span></span> <span data-ttu-id="01488-119">若連接埠是請求-回應連接埠，則清單中只會顯示支援請求-回應的傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="01488-119">If the port is a solicit-response port, only transport types that support solicit-response are available in the list.</span></span>|  
    |<span data-ttu-id="01488-120">**設定**</span><span class="sxs-lookup"><span data-stu-id="01488-120">**Configure**</span></span>|<span data-ttu-id="01488-121">選取備份傳輸類型後，按一下**設定**，然後設定 傳輸屬性。</span><span class="sxs-lookup"><span data-stu-id="01488-121">After you select the backup transport type, click **Configure**, and then configure transport properties.</span></span> <span data-ttu-id="01488-122">如需有關如何設定屬性的詳細資訊，請按一下**協助**。</span><span class="sxs-lookup"><span data-stu-id="01488-122">For more information about configuring the properties, click **Help**.</span></span>|  
    |<span data-ttu-id="01488-123">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="01488-123">**Send handler**</span></span>|<span data-ttu-id="01488-124">從下拉式清單選取傳送配接器執行所在的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="01488-124">From the drop-down list, select the host instance on which the send adapter is running.</span></span>|  
    |<span data-ttu-id="01488-125">**重試計數**</span><span class="sxs-lookup"><span data-stu-id="01488-125">**Retry count**</span></span>|<span data-ttu-id="01488-126">指定傳送埠在訊息失敗時重新傳送訊息的次數。</span><span class="sxs-lookup"><span data-stu-id="01488-126">Specify the number of times for the send port to resend a message on message failure.</span></span> <span data-ttu-id="01488-127">預設值為 3；允許的範圍由 0 至 1,000。</span><span class="sxs-lookup"><span data-stu-id="01488-127">The default is 3; the allowed range is from 0 to 1,000.</span></span>|  
    |<span data-ttu-id="01488-128">**重試間隔**</span><span class="sxs-lookup"><span data-stu-id="01488-128">**Retry interval**</span></span>|<span data-ttu-id="01488-129">以分鐘為單位指定重新傳送訊息嘗試之間的間隔。</span><span class="sxs-lookup"><span data-stu-id="01488-129">Specify the interval in minutes between message resend attempts.</span></span> <span data-ttu-id="01488-130">預設值是 5;允許的範圍是從 0 到 525600。</span><span class="sxs-lookup"><span data-stu-id="01488-130">The default is 5; the allowed range is from 0 to 525,600.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="01488-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01488-131">See Also</span></span>  
 [<span data-ttu-id="01488-132">建立和設定傳送埠</span><span class="sxs-lookup"><span data-stu-id="01488-132">Creating and Configuring Send Ports</span></span>](../core/creating-and-configuring-send-ports.md)