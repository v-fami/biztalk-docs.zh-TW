---
title: 如何設定 Wcf-nettcp 接收處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-NetTcp adapters, global variables
- receive handlers, WCF-NetTcp adapters
- configuring [WCF-NetTcp adapters], global variables
- configuring [WCF-NetTcp adapters], receive handlers
ms.assetid: a4a283d1-21de-4d6b-9cb5-f2f9f823903b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69598bc1ce0bda41269fa91a0618fb040e741b28
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247518"
---
# <a name="how-to-configure-a-wcf-nettcp-receive-handler"></a><span data-ttu-id="c1127-102">如何設定 WCF-NetTcp 接收處理常式</span><span class="sxs-lookup"><span data-stu-id="c1127-102">How to Configure a WCF-NetTcp Receive Handler</span></span>
<span data-ttu-id="c1127-103">請使用下列程序設定 WCF-NetTcp 接收處理常式。</span><span class="sxs-lookup"><span data-stu-id="c1127-103">Use the following procedure to configure a WCF-NetTcp receive handler.</span></span>  
  
### <a name="to-change-global-variables-for-a-wcf-nettcp-receive-handler"></a><span data-ttu-id="c1127-104">若要變更 WCF-NetTcp 接收處理常式的全域變數</span><span class="sxs-lookup"><span data-stu-id="c1127-104">To change global variables for a WCF-NetTcp receive handler</span></span>  
  
1.  <span data-ttu-id="c1127-105">在 BizTalk 管理主控台中，展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開 **配接器**。</span><span class="sxs-lookup"><span data-stu-id="c1127-105">In the BizTalk Administration Console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="c1127-106">在展開的配接器清單中，按一下  **Wcf-nettcp**，在右窗格，以滑鼠右鍵按一下您想要設定的接收處理常式，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="c1127-106">In the expanded adapter list, click **WCF-NetTcp**, in the right pane, right-click the receive handler that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="c1127-107">在**配接器處理常式屬性**對話方塊**一般**索引標籤的**主機名稱**清單中，選取與其相關聯的接收處理常式的主機。</span><span class="sxs-lookup"><span data-stu-id="c1127-107">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated.</span></span>  
  
4.  <span data-ttu-id="c1127-108">在**一般**索引標籤上，按一下 **屬性**上**接收處理常式**索引標籤上，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="c1127-108">In the **General** tab, click **Properties**, On the **Receive handler** tab, do the following.</span></span>  
  
    |<span data-ttu-id="c1127-109">使用</span><span class="sxs-lookup"><span data-stu-id="c1127-109">Use this</span></span>|<span data-ttu-id="c1127-110">動作</span><span class="sxs-lookup"><span data-stu-id="c1127-110">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="c1127-111">**連線數目上限**</span><span class="sxs-lookup"><span data-stu-id="c1127-111">**Maximum connections**</span></span>|<span data-ttu-id="c1127-112">指定待命程式最多可以擁有等待應用程式接受的連線數目。</span><span class="sxs-lookup"><span data-stu-id="c1127-112">Specify the maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="c1127-113">超過此配額值時，則會捨棄新的傳入連線，而非等待接受連線。</span><span class="sxs-lookup"><span data-stu-id="c1127-113">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span><br /><br /> <span data-ttu-id="c1127-114">預設值是 10。</span><span class="sxs-lookup"><span data-stu-id="c1127-114">The default is 10.</span></span>|  
  
5.  <span data-ttu-id="c1127-115">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="c1127-115">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1127-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1127-116">See Also</span></span>  
 <span data-ttu-id="c1127-117">[設定 Wcf-nettcp 配接器](../core/configuring-the-wcf-nettcp-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="c1127-117">[Configuring the WCF-NetTcp Adapter](../core/configuring-the-wcf-nettcp-adapter.md) </span></span>  
 [<span data-ttu-id="c1127-118">發佈 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="c1127-118">Publishing WCF Services</span></span>](../core/publishing-wcf-services.md)