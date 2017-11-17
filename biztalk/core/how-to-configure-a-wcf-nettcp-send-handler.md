---
title: "如何設定 Wcf-nettcp 傳送處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send handlers, WCF-NetTcp adapters
- configuring [WCF-NetTcp adapters], send handlers
- WCF-NetTcp adapters, global variables
- configuring [WCF-NetTcp adapters], global variables
ms.assetid: c60fe03d-7e11-4e08-9a24-8ff443eee9c1
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02451dba6755e4db0c10d7cce20141468a67694f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-wcf-nettcp-send-handler"></a><span data-ttu-id="4f09d-102">如何設定 WCF-NetTcp 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="4f09d-102">How to Configure a WCF-NetTcp Send Handler</span></span>
<span data-ttu-id="4f09d-103">使用下列程序，定 WCF-NetTcp 傳送處理常式。</span><span class="sxs-lookup"><span data-stu-id="4f09d-103">Use the following procedure to configure a WCF-NetTcp send handler.</span></span>  
  
### <a name="to-change-global-variables-for-a-wcf-nettcp-send-handler"></a><span data-ttu-id="4f09d-104">若要變更 WCF-NetTcp 傳送處理常式的全域變數</span><span class="sxs-lookup"><span data-stu-id="4f09d-104">To change global variables for a WCF-NetTcp send handler</span></span>  
  
1.  <span data-ttu-id="4f09d-105">在 BizTalk 管理主控台中，展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開 **配接器**。</span><span class="sxs-lookup"><span data-stu-id="4f09d-105">In the BizTalk Administration Console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="4f09d-106">在展開的配接器清單中，按一下  **Wcf-nettcp**，在右窗格，以滑鼠右鍵按一下您想要設定的傳送處理常式，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="4f09d-106">In the expanded adapter list, click **WCF-NetTcp**, in the right pane, right-click the send handler that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="4f09d-107">在**配接器處理常式屬性**對話方塊**一般**索引標籤的**主機名稱**清單中，選取與其相關聯的傳送處理常式的主機。</span><span class="sxs-lookup"><span data-stu-id="4f09d-107">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the send handler will be associated.</span></span>  
  
4.  <span data-ttu-id="4f09d-108">在**一般**索引標籤上，按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="4f09d-108">On the **General** tab, click **Properties**.</span></span> <span data-ttu-id="4f09d-109">在**傳送處理常式**索引標籤上，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="4f09d-109">On the **Send handler** tab, do the following.</span></span>  
  
    |<span data-ttu-id="4f09d-110">使用</span><span class="sxs-lookup"><span data-stu-id="4f09d-110">Use this</span></span>|<span data-ttu-id="4f09d-111">動作</span><span class="sxs-lookup"><span data-stu-id="4f09d-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="4f09d-112">**連線數目上限**</span><span class="sxs-lookup"><span data-stu-id="4f09d-112">**Maximum connections**</span></span>|<span data-ttu-id="4f09d-113">指定快取在連接集區中的每個端點之輸出連線最大數目。</span><span class="sxs-lookup"><span data-stu-id="4f09d-113">Specify the maximum number of outbound connections for each endpoint that is cached in the connection pool.</span></span> <span data-ttu-id="4f09d-114">這會限制每個唯一遠端端點快取中的連線數目。</span><span class="sxs-lookup"><span data-stu-id="4f09d-114">This limits the number of connections that are cached for each unique remote endpoint.</span></span> <span data-ttu-id="4f09d-115">您應該將這個值設定為大於您預計要為任何特定遠端端點快取存放的最大連線數。</span><span class="sxs-lookup"><span data-stu-id="4f09d-115">You should set this value to be greater than the maximum number of connections that you expect to be cached for any unique remote endpoint.</span></span> <span data-ttu-id="4f09d-116">如果作用中輸出連線數目超過這個最大值，則服務對於在此傳送處理常式下執行的 WCF-NetTcp 傳送埠，可能顯得反應遲緩。</span><span class="sxs-lookup"><span data-stu-id="4f09d-116">If the number of active outbound connections exceeds this maximum value, then the service may appear unresponsive to the WCF-NetTcp send ports running under this send hander.</span></span><br /><br /> <span data-ttu-id="4f09d-117">預設值是 10。</span><span class="sxs-lookup"><span data-stu-id="4f09d-117">The default is 10.</span></span>|  
  
5.  <span data-ttu-id="4f09d-118">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="4f09d-118">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f09d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f09d-119">See Also</span></span>  
 <span data-ttu-id="4f09d-120">[使用 WCF 服務](../core/consuming-wcf-services.md) </span><span class="sxs-lookup"><span data-stu-id="4f09d-120">[Consuming WCF Services](../core/consuming-wcf-services.md) </span></span>  
 [<span data-ttu-id="4f09d-121">設定 Wcf-nettcp 配接器</span><span class="sxs-lookup"><span data-stu-id="4f09d-121">Configuring the WCF-NetTcp Adapter</span></span>](../core/configuring-the-wcf-nettcp-adapter.md)