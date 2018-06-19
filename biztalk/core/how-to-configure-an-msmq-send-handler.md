---
title: 如何設定 MSMQ 傳送處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, send handlers
- configuring [MSMQ adapters], send handlers
- send handlers, MSMQ adapters
ms.assetid: 21917596-f27a-473b-859e-186ab5f4cd94
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: feacaec9d2794cf8806fa5156fe64b7290699faa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248262"
---
# <a name="how-to-configure-an-msmq-send-handler"></a><span data-ttu-id="6e2e6-102">如何設定 MSMQ 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="6e2e6-102">How to Configure an MSMQ Send Handler</span></span>
<span data-ttu-id="6e2e6-103">您可以使用下列程序來變更 MSMQ 傳送處理常式的全域變數。</span><span class="sxs-lookup"><span data-stu-id="6e2e6-103">Use the following procedure to change the global variables for an MSMQ send handler.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e2e6-104">每個主控件只可和一個傳送處理常式建立關聯。</span><span class="sxs-lookup"><span data-stu-id="6e2e6-104">Each host can have only one send handler associated with it.</span></span>  
  
### <a name="to-change-global-variables-for-an-msmq-send-handler-by-using-the-biztalk-server-administration-console"></a><span data-ttu-id="6e2e6-105">使用 [BizTalk Server 管理] 主控台變更 MSMQ 傳送處理常式的全域變數</span><span class="sxs-lookup"><span data-stu-id="6e2e6-105">To change global variables for an MSMQ send handler by using the BizTalk Server Administration console</span></span>  
  
1.  <span data-ttu-id="6e2e6-106">在 BizTalk Server 管理主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開  **配接器**。</span><span class="sxs-lookup"><span data-stu-id="6e2e6-106">In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="6e2e6-107">在展開的配接器清單中，按一下  **MSMQ**，在右窗格，以滑鼠右鍵按一下您想要設定的傳送處理常式，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="6e2e6-107">In the expanded adapter list, click **MSMQ**, in the right pane, right-click the send handler that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="6e2e6-108">在**配接器處理常式屬性**對話方塊**一般**索引標籤的**主機名稱**清單中，選取主控件與傳送處理常式將會產生關聯，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="6e2e6-108">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the send handler will be associated, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="6e2e6-109">在**MSMQ 傳輸屬性**對話方塊方塊中，輸入一個值**批次大小**。</span><span class="sxs-lookup"><span data-stu-id="6e2e6-109">In the **MSMQ Transport Properties** dialog box, enter a value for **Batch Size**.</span></span>  
  
     <span data-ttu-id="6e2e6-110">MSMQ 傳送處理常式會將訊息傳送至使用指定的目的地佇列**批次大小**參數。</span><span class="sxs-lookup"><span data-stu-id="6e2e6-110">The MSMQ send handler will send messages to destination queues using the specified **Batch Size** parameter.</span></span> <span data-ttu-id="6e2e6-111">預設值**批次大小**值為 5。</span><span class="sxs-lookup"><span data-stu-id="6e2e6-111">The default **Batch Size** value is 5.</span></span>  
  
5.  <span data-ttu-id="6e2e6-112">按一下**確定**按一下**確定** 以關閉 **配接器處理常式屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6e2e6-112">Click **OK** and click **OK** again to close the **Adapter Handler Properties** dialog box.</span></span>