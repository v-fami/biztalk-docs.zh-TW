---
title: "如何設定 SOAP 接收處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [SOAP adapters], receive handlers
- SOAP adapters, receive handlers
- receive handlers, SOAP adapters
ms.assetid: e1174381-f36c-4131-83b7-26bfa879802e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4054635a8ffa4e019f7db9513e5e20e997f7e291
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-soap-receive-handler"></a><span data-ttu-id="2f259-102">如何設定 SOAP 接收處理常式</span><span class="sxs-lookup"><span data-stu-id="2f259-102">How to Configure a SOAP Receive Handler</span></span>
<span data-ttu-id="2f259-103">使用 BizTalk Server 管理主控台，可以設定 SOAP 接收處理常式設定。</span><span class="sxs-lookup"><span data-stu-id="2f259-103">You can configure the SOAP receive handler settings by using the BizTalk Server Administration Console.</span></span> <span data-ttu-id="2f259-104">若使用 BizTalk Server 管理主控台 設定配接器，則不需在 BizTalk 總管 中設定處理常式覆寫屬性。</span><span class="sxs-lookup"><span data-stu-id="2f259-104">If you configure the adapter using the BizTalk Server Administration Console, the handler override properties do not need to be set in BizTalk Explorer.</span></span>  
  
### <a name="to-change-global-variables-for-the-soap-receive-handler"></a><span data-ttu-id="2f259-105">變更 SOAP 接收處理常式的全域變數</span><span class="sxs-lookup"><span data-stu-id="2f259-105">To change global variables for the SOAP receive handler</span></span>  
  
1.  <span data-ttu-id="2f259-106">在 BizTalk Server 管理主控台中，依序展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開 **配接器**。</span><span class="sxs-lookup"><span data-stu-id="2f259-106">In the BizTalk Server Administration Console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="2f259-107">在展開的配接器清單中，按一下  **SOAP**，在右窗格，以滑鼠右鍵按一下您想要設定的接收處理常式，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="2f259-107">In the expanded adapter list, click **SOAP**, in the right pane, right-click the receive handler that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="2f259-108">在**配接器處理常式屬性**對話方塊**一般**索引標籤的**主機名稱**清單中，選取與其相關聯，接收處理常式的主機，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="2f259-108">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f259-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f259-109">See Also</span></span>  
 <span data-ttu-id="2f259-110">[設定 SOAP 配接器](../core/configuring-the-soap-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="2f259-110">[Configuring the SOAP Adapter](../core/configuring-the-soap-adapter.md) </span></span>  
 [<span data-ttu-id="2f259-111">使用 Web 服務</span><span class="sxs-lookup"><span data-stu-id="2f259-111">Consuming Web Services</span></span>](../core/consuming-web-services.md)