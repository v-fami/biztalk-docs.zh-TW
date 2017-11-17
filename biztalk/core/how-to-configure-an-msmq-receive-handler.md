---
title: "如何設定 MSMQ 接收處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive handlers, MSMQ adapters
- configuring [MSMQ adapters], receive handlers
- MSMQ adapters, receive handlers
ms.assetid: d6d82098-3a73-44e2-80d5-143f77e919cc
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f34e1b3f399c93bd92aa9c4e07f6e0082d25204
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-an-msmq-receive-handler"></a><span data-ttu-id="52a35-102">如何設定 MSMQ 接收處理常式</span><span class="sxs-lookup"><span data-stu-id="52a35-102">How to Configure an MSMQ Receive Handler</span></span>
<span data-ttu-id="52a35-103">使用下列程序，變更 MSMQ 接收處理常式關聯的主控件。</span><span class="sxs-lookup"><span data-stu-id="52a35-103">Use the following procedure to change the host with which the MSMQ receive handler is associated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52a35-104">每個主控件只可和一個接收處理常式建立關聯。</span><span class="sxs-lookup"><span data-stu-id="52a35-104">Each host can associate with only one receive handler.</span></span>  
  
### <a name="to-change-the-host-with-which-the-msmq-receive-handler-is-associated"></a><span data-ttu-id="52a35-105">變更 MSMQ 接收處理常式關聯的主控件</span><span class="sxs-lookup"><span data-stu-id="52a35-105">To change the host with which the MSMQ receive handler is associated</span></span>  
  
1.  <span data-ttu-id="52a35-106">在 BizTalk Server 管理主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開  **配接器**。</span><span class="sxs-lookup"><span data-stu-id="52a35-106">In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="52a35-107">在展開的配接器清單中，按一下  **MSMQ**，在右窗格，以滑鼠右鍵按一下您想要設定的接收處理常式，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="52a35-107">In the expanded adapter list, click **MSMQ**, in the right pane, right-click the receive handler that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="52a35-108">在**配接器處理常式屬性**對話方塊**一般**索引標籤的**主機名稱**清單中，選取與其相關聯的接收處理常式的主機。</span><span class="sxs-lookup"><span data-stu-id="52a35-108">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated.</span></span>  
  
4.  <span data-ttu-id="52a35-109">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="52a35-109">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52a35-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52a35-110">See Also</span></span>  
 [<span data-ttu-id="52a35-111">設定 MSMQ 配接器</span><span class="sxs-lookup"><span data-stu-id="52a35-111">Configuring the MSMQ Adapter</span></span>](../core/configuring-the-msmq-adapter.md)