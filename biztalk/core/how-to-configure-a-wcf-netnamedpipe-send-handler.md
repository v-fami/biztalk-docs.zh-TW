---
title: 如何設定 Wcf-netnamedpipe 傳送處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-NetNamedPipe adapters, global adapters
- configuring [WCF-NetNamedPipe adapters], global adapters
- send handlers, WCF-NetNamedPipe adapters
- configuring [WCF-NetNamedPipe adapters], send handlers
ms.assetid: 1f281649-d09f-44eb-8af5-1f83233fab60
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fc9ef8086ae0cda04da3ecdc7eacbfcb6d01f14
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970223"
---
# <a name="how-to-configure-a-wcf-netnamedpipe-send-handler"></a><span data-ttu-id="48bee-102">如何設定 WCF-NetNamedPipe 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="48bee-102">How to Configure a WCF-NetNamedPipe Send Handler</span></span>
<span data-ttu-id="48bee-103">請使用下列程序設定 WCF-NetNamedPipe 傳送處理常式。</span><span class="sxs-lookup"><span data-stu-id="48bee-103">Use the following procedure to configure a WCF-NetNamedPipe send handler.</span></span>  

### <a name="to-change-global-variables-for-a-wcf-netnamedpipe-send-handler"></a><span data-ttu-id="48bee-104">若要變更 WCF-NetNamedPipe 傳送處理常式的全域變數</span><span class="sxs-lookup"><span data-stu-id="48bee-104">To change global variables for a WCF-NetNamedPipe send handler</span></span>  

1. <span data-ttu-id="48bee-105">在 BizTalk Server 管理主控台中，依序展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**，展開**BizTalk 群組**，依序展開**平台設定**，然後展開  **配接器**。</span><span class="sxs-lookup"><span data-stu-id="48bee-105">In the BizTalk Server Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  

2. <span data-ttu-id="48bee-106">在展開的配接器清單中，按一下**Wcf-netnamedpipe**，在右窗格以滑鼠右鍵按一下您想要設定的傳送處理常式，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="48bee-106">In the expanded adapter list, click **WCF-NetNamedPipe**, in the right pane, right-click the send handler that you want to configure, and then click **Properties**.</span></span>  

3. <span data-ttu-id="48bee-107">在 **配接器處理常式屬性**對話方塊的 **一般**索引標籤**主機名稱**清單中，選取與其相關聯的傳送處理常式的主控。</span><span class="sxs-lookup"><span data-stu-id="48bee-107">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the send handler will be associated.</span></span>  

4. <span data-ttu-id="48bee-108">在 **一般**索引標籤上，按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="48bee-108">In the **General** tab, click **Properties**.</span></span> <span data-ttu-id="48bee-109">在 **傳送處理常式**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="48bee-109">On the **Send handler** tab, do the following:</span></span>  


   |        <span data-ttu-id="48bee-110">使用</span><span class="sxs-lookup"><span data-stu-id="48bee-110">Use this</span></span>         |                                                                                                                                                                                                                                                                             <span data-ttu-id="48bee-111">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="48bee-111">To do this</span></span>                                                                                                                                                                                                                                                                             |
   |-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | <span data-ttu-id="48bee-112">**連線數目上限**</span><span class="sxs-lookup"><span data-stu-id="48bee-112">**Maximum connections**</span></span> | <span data-ttu-id="48bee-113">指定快取在連接集區中的每個端點之輸出連線最大數目。</span><span class="sxs-lookup"><span data-stu-id="48bee-113">Specify the maximum number of outbound connections for each endpoint that is cached in the connection pool.</span></span> <span data-ttu-id="48bee-114">這會限制每個唯一遠端端點快取中的連線數目。</span><span class="sxs-lookup"><span data-stu-id="48bee-114">This limits the number of connections that are cached for each unique remote endpoint.</span></span> <span data-ttu-id="48bee-115">您應該將這個值設定為大於您預計要為任何特定遠端端點快取存放的最大連線數。</span><span class="sxs-lookup"><span data-stu-id="48bee-115">You should set this value to be greater than the maximum number of connections that you expect to be cached for any unique remote endpoint.</span></span> <span data-ttu-id="48bee-116">如果作用中輸出連線數目超過這個最大值，則對於在此傳送處理常式下執行的 WCF-NetNamedPipe 傳送埠，服務可能會顯得反應遲緩。</span><span class="sxs-lookup"><span data-stu-id="48bee-116">If the number of active outbound connections exceeds this maximum value, then the service may appear unresponsive to the WCF-NetNamedPipe send ports running under this send hander.</span></span><br /><br /> <span data-ttu-id="48bee-117">預設值是 10。</span><span class="sxs-lookup"><span data-stu-id="48bee-117">The default is 10.</span></span> |


5. <span data-ttu-id="48bee-118">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="48bee-118">Click **OK**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="48bee-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48bee-119">See Also</span></span>  
 <span data-ttu-id="48bee-120">[使用 WCF 服務](../core/consuming-wcf-services.md) </span><span class="sxs-lookup"><span data-stu-id="48bee-120">[Consuming WCF Services](../core/consuming-wcf-services.md) </span></span>  
 [<span data-ttu-id="48bee-121">設定 WCF-NetNamedPipe 配接器</span><span class="sxs-lookup"><span data-stu-id="48bee-121">Configuring the WCF-NetNamedPipe Adapter</span></span>](../core/configuring-the-wcf-netnamedpipe-adapter.md)