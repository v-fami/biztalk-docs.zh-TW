---
title: 如何設定 Windows SharePoint Services 傳送處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [Windows SharePoint Services adapters], send handlers
- send handlers, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, send handlers
ms.assetid: 457767d9-6e39-4553-9bbe-212fcb7c04bc
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90ac23759558549122f31a793852b479b67744d4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988551"
---
# <a name="how-to-configure-a-windows-sharepoint-services-send-handler"></a><span data-ttu-id="74207-102">如何設定 Windows SharePoint Services 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="74207-102">How to Configure a Windows SharePoint Services Send Handler</span></span>
<span data-ttu-id="74207-103">使用下列程序，變更與 Windows SharePoint Services 傳送處理常式關聯的主控件。</span><span class="sxs-lookup"><span data-stu-id="74207-103">Use the following procedure to change the host with which the Windows SharePoint Services send handler is associated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74207-104">每個主控件只可和一個傳送處理常式建立關聯。</span><span class="sxs-lookup"><span data-stu-id="74207-104">Each host can have only one send handler associated with it.</span></span>  
  
### <a name="to-change-global-variables-for-a-windows-sharepoint-services-send-handler"></a><span data-ttu-id="74207-105">變更 Windows SharePoint Services 傳送處理常式的全域變數</span><span class="sxs-lookup"><span data-stu-id="74207-105">To change global variables for a Windows SharePoint Services send handler</span></span>  
  
1. <span data-ttu-id="74207-106">在 BizTalk Server 管理主控台中，按一下以展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**，然後按一下以展開**BizTalk 群組 [\<servername\>:\<管理資料庫\>]**，按一下以展開**平台設定**，然後按一下以展開**配接器**。</span><span class="sxs-lookup"><span data-stu-id="74207-106">In the BizTalk Server Administration console, click to expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, and then click to expand **BizTalk Group [\<servername\>:\<management database\>]**, click to expand **Platform Settings**, and then click to expand **Adapters**.</span></span> <span data-ttu-id="74207-107">配接器清單會出現在資料夾下。</span><span class="sxs-lookup"><span data-stu-id="74207-107">The list of adapters appears under the folder.</span></span>  
  
2. <span data-ttu-id="74207-108">按一下  **Windows SharePoint Services**，在右窗格中，以滑鼠右鍵按一下您想要設定，然後按一下 傳送處理常式**屬性**。</span><span class="sxs-lookup"><span data-stu-id="74207-108">Click **Windows SharePoint Services**, and in the right pane, right-click the send handler that you want to configure, and then click **Properties**.</span></span>  
  
3. <span data-ttu-id="74207-109">在 **配接器處理常式屬性**對話方塊的 **一般**索引標籤**主機名稱**清單中，選取與其相關聯的傳送處理常式的主控。</span><span class="sxs-lookup"><span data-stu-id="74207-109">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the send handler will be associated.</span></span>  
  
4. <span data-ttu-id="74207-110">在 **一般**索引標籤上，按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="74207-110">On the **General** tab, click **Properties**.</span></span>  
  
5. <span data-ttu-id="74207-111">在  **Windows SharePoint Services 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="74207-111">In the **Windows SharePoint Services Transport Properties** dialog box, do the following:</span></span>  
  
   |<span data-ttu-id="74207-112">使用</span><span class="sxs-lookup"><span data-stu-id="74207-112">Use this</span></span>|<span data-ttu-id="74207-113">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="74207-113">To do this</span></span>|  
   |--------------|----------------|  
   |<span data-ttu-id="74207-114">傳送批次大小</span><span class="sxs-lookup"><span data-stu-id="74207-114">Send Batch Size</span></span>|<span data-ttu-id="74207-115">Windows SharePoint Services Web 服務視為一個批次進行處理的文件數目上限。</span><span class="sxs-lookup"><span data-stu-id="74207-115">The maximum number of documents that the Windows SharePoint Services Web service will process as a batch.</span></span> <span data-ttu-id="74207-116">預設值是 20。</span><span class="sxs-lookup"><span data-stu-id="74207-116">The default is 20.</span></span> <span data-ttu-id="74207-117">**注意：** 的最小值為 1。</span><span class="sxs-lookup"><span data-stu-id="74207-117">**Note:**  The minimum value is 1.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="74207-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74207-118">See Also</span></span>  
 <span data-ttu-id="74207-119">[如何設定 Windows SharePoint Services 接收位置](../core/how-to-configure-a-windows-sharepoint-services-receive-location.md) </span><span class="sxs-lookup"><span data-stu-id="74207-119">[How to Configure a Windows SharePoint Services Receive Location](../core/how-to-configure-a-windows-sharepoint-services-receive-location.md) </span></span>  
 <span data-ttu-id="74207-120">[如何設定 Windows SharePoint Services 傳送埠](../core/how-to-configure-a-windows-sharepoint-services-send-port.md) </span><span class="sxs-lookup"><span data-stu-id="74207-120">[How to Configure a Windows SharePoint Services Send Port](../core/how-to-configure-a-windows-sharepoint-services-send-port.md) </span></span>  
 <span data-ttu-id="74207-121">[如何建立傳送埠](../core/how-to-create-a-send-port2.md) </span><span class="sxs-lookup"><span data-stu-id="74207-121">[How to Create a Send Port](../core/how-to-create-a-send-port2.md) </span></span>  
 <span data-ttu-id="74207-122">[Windows SharePoint Services 配接器屬性參考](../core/windows-sharepoint-services-adapter-properties-reference.md) </span><span class="sxs-lookup"><span data-stu-id="74207-122">[Windows SharePoint Services Adapter Properties Reference](../core/windows-sharepoint-services-adapter-properties-reference.md) </span></span>  
 <span data-ttu-id="74207-123">[Windows SharePoint Services 配接器運算式](../core/windows-sharepoint-services-adapter-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="74207-123">[Windows SharePoint Services Adapter Expressions](../core/windows-sharepoint-services-adapter-expressions.md) </span></span>  
 [<span data-ttu-id="74207-124">支援的 Windows SharePoint Services 資料行類型</span><span class="sxs-lookup"><span data-stu-id="74207-124">Supported Windows SharePoint Services Column Types</span></span>](../core/supported-windows-sharepoint-services-column-types.md)