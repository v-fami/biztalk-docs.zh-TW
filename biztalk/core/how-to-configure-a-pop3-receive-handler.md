---
title: "如何設定 POP3 接收處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive handlers, POP3 adapters
- POP3 adapters, receive handlers
- configuring [POP3 adapters], receive handlers
ms.assetid: 2191c201-545e-4d5a-a1ca-3c38c7b8258d
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8868ce589fa7556da185dcaf4c71b5bfd5cae159
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-pop3-receive-handler"></a><span data-ttu-id="e27af-102">如何設定 POP3 接收處理常式</span><span class="sxs-lookup"><span data-stu-id="e27af-102">How to Configure a POP3 Receive Handler</span></span>
<span data-ttu-id="e27af-103">使用下列程序來變更與 POP3 接收處理常式關聯的主控件。</span><span class="sxs-lookup"><span data-stu-id="e27af-103">Use the following procedure to change the host associated with the POP3 receive handler.</span></span>  
  
### <a name="to-configure-the-general-properties-for-a-pop3-receive-handler"></a><span data-ttu-id="e27af-104">若要設定 POP3 接收處理常式的一般屬性</span><span class="sxs-lookup"><span data-stu-id="e27af-104">To configure the general properties for a POP3 receive handler</span></span>  
  
1.  <span data-ttu-id="e27af-105">在 BizTalk Server 管理主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開  **配接器**。</span><span class="sxs-lookup"><span data-stu-id="e27af-105">In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="e27af-106">在展開的配接器清單中，按一下  **POP3**，在右窗格，以滑鼠右鍵按一下您想要設定的接收處理常式，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="e27af-106">In the expanded adapter list, click **POP3**, in the right pane, right-click the receive handler that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="e27af-107">在**配接器處理常式屬性**對話方塊**一般**索引標籤的**主機名稱**清單中，選取與其相關聯的接收處理常式的主機。</span><span class="sxs-lookup"><span data-stu-id="e27af-107">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated.</span></span>  
  
4.  <span data-ttu-id="e27af-108">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e27af-108">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e27af-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e27af-109">See Also</span></span>  
 [<span data-ttu-id="e27af-110">執行叢集主控件中的配接器處理常式的考量</span><span class="sxs-lookup"><span data-stu-id="e27af-110">Considerations for Running Adapter Handlers within a Clustered Host</span></span>](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)