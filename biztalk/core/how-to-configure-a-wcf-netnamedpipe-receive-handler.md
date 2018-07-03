---
title: 如何設定 Wcf-netnamedpipe 接收處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [WCF-NetNamedPipe adapters], global variables
- receive handlers, WCF-NetNamedPipe adapters
- configuring [WCF-NetNamedPipe adapters], receive handlers
- WCF-NetNamedPipe adapters, global variables
ms.assetid: f7ab2228-1049-40f0-87f7-6330a8f40cfe
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2601bcd6e68f8752699474c4d02295d353064083
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022900"
---
# <a name="how-to-configure-a-wcf-netnamedpipe-receive-handler"></a><span data-ttu-id="b1d80-102">如何設定 WCF-NetNamedPipe 接收處理常式</span><span class="sxs-lookup"><span data-stu-id="b1d80-102">How to Configure a WCF-NetNamedPipe Receive Handler</span></span>
<span data-ttu-id="b1d80-103">請使用下列程序設定 WCF-NetNamedPipe 接收處理常式。</span><span class="sxs-lookup"><span data-stu-id="b1d80-103">Use the following procedure to configure a WCF-NetNamedPipe receive handler.</span></span>  

### <a name="to-change-global-variables-for-a-wcf-netnamedpipe-receive-handler"></a><span data-ttu-id="b1d80-104">若要變更 WCF-NetNamedPipe 接收處理常式的全域變數</span><span class="sxs-lookup"><span data-stu-id="b1d80-104">To change global variables for a WCF-NetNamedPipe receive handler</span></span>  

1. <span data-ttu-id="b1d80-105">在 BizTalk 管理主控台中，依序展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**，展開**BizTalk 群組**，依序展開**平台設定**，然後展開**配接器**。</span><span class="sxs-lookup"><span data-stu-id="b1d80-105">In the BizTalk Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  

2. <span data-ttu-id="b1d80-106">在展開的配接器清單中，按一下**Wcf-netnamedpipe**，在右窗格以滑鼠右鍵按一下您想要設定的接收處理常式，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="b1d80-106">In the expanded adapter list, click **WCF-NetNamedPipe**, in the right pane, right-click the receive handler that you want to configure, and then click **Properties**.</span></span>  

3. <span data-ttu-id="b1d80-107">在 **配接器處理常式屬性**對話方塊的 **一般**索引標籤**主機名稱**清單中，選取與其相關聯的接收處理常式的主控。</span><span class="sxs-lookup"><span data-stu-id="b1d80-107">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated.</span></span>  

4. <span data-ttu-id="b1d80-108">在 **一般**索引標籤上，按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="b1d80-108">In the **General** tab, click **Properties**.</span></span> <span data-ttu-id="b1d80-109">在 **接收處理常式**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b1d80-109">On the **Receive handler** tab, do the following:</span></span>  


   |        <span data-ttu-id="b1d80-110">使用</span><span class="sxs-lookup"><span data-stu-id="b1d80-110">Use this</span></span>         |                                                                                                                         <span data-ttu-id="b1d80-111">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="b1d80-111">To do this</span></span>                                                                                                                         |
   |-------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | <span data-ttu-id="b1d80-112">**連線數目上限**</span><span class="sxs-lookup"><span data-stu-id="b1d80-112">**Maximum connections**</span></span> | <span data-ttu-id="b1d80-113">指定待命程式最多可以擁有等待應用程式接受的連線數目。</span><span class="sxs-lookup"><span data-stu-id="b1d80-113">Specify the maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="b1d80-114">超過此配額值時，則會捨棄新的傳入連線，而非等待接受連線。</span><span class="sxs-lookup"><span data-stu-id="b1d80-114">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span><br /><br /> <span data-ttu-id="b1d80-115">預設值是 10。</span><span class="sxs-lookup"><span data-stu-id="b1d80-115">The default is 10.</span></span> |


5. <span data-ttu-id="b1d80-116">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="b1d80-116">Click **OK**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="b1d80-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1d80-117">See Also</span></span>  
 <span data-ttu-id="b1d80-118">[發佈 WCF 服務](../core/publishing-wcf-services.md) </span><span class="sxs-lookup"><span data-stu-id="b1d80-118">[Publishing WCF Services](../core/publishing-wcf-services.md) </span></span>  
 [<span data-ttu-id="b1d80-119">設定 WCF-NetNamedPipe 配接器</span><span class="sxs-lookup"><span data-stu-id="b1d80-119">Configuring the WCF-NetNamedPipe Adapter</span></span>](../core/configuring-the-wcf-netnamedpipe-adapter.md)