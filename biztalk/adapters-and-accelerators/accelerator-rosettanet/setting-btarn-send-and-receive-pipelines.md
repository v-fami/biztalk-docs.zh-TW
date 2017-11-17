---
title: "設定 BTARN 傳送和接收管線 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send pipelines, modifying
- modifying, send pipelines
- receive pipelines, modifying
- modifying, receive pipelines
ms.assetid: 00960de0-3763-40aa-9e4b-1fedc7f1eea6
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47f2f12629965c3b01df8cc2f2fd7b1a7ea58a47
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="setting-btarn-send-and-receive-pipelines"></a><span data-ttu-id="8ad8f-102">設定 BTARN 傳送和接收管線</span><span class="sxs-lookup"><span data-stu-id="8ad8f-102">Setting BTARN Send and Receive Pipelines</span></span>
<span data-ttu-id="8ad8f-103">根據預設， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]使用標準[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]傳送管線 (Microsoft.Solutions.BTARN.Pipelines.Send) 和標準[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]接收管線 (Microsoft.Solutions.BTARN.Pipelines.Receive)，當您建立交易夥伴傳送埠。</span><span class="sxs-lookup"><span data-stu-id="8ad8f-103">By default, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] uses the standard [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] send pipeline (Microsoft.Solutions.BTARN.Pipelines.Send) and the standard [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] receive pipeline (Microsoft.Solutions.BTARN.Pipelines.Receive) when you create partner send ports.</span></span> <span data-ttu-id="8ad8f-104">不過，您可以變更 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 組態，改為使用現有的 BizTalk 管線或您建立的自訂管線。</span><span class="sxs-lookup"><span data-stu-id="8ad8f-104">However, you can change the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] configuration to use an existing BizTalk pipeline or a custom pipeline that you have created.</span></span> <span data-ttu-id="8ad8f-105">所有的交易夥伴協議，以及所有的交易夥伴和主要組織，都會使用相同的傳送管線與相同的接收管線。</span><span class="sxs-lookup"><span data-stu-id="8ad8f-105">All trading partner agreements, and all partners and home organizations, use the same send pipeline and the same receive pipeline.</span></span>  
  
 <span data-ttu-id="8ad8f-106">當您初次建立夥伴，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]建立兩個傳送埠供交易夥伴使用非同步的其中一個，而另一個同步： \<*夥伴名稱*>。非同步傳送埠和\<*夥伴名稱*>。同步傳送埠。</span><span class="sxs-lookup"><span data-stu-id="8ad8f-106">When you first create a partner, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] creates two send ports for that partner to use, one asynchronous and one synchronous: \<*partner name*>.Async send port and \<*partner name*>.Sync send port.</span></span> <span data-ttu-id="8ad8f-107">這些傳送埠預設使用標準的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 傳送管線，而同步傳送埠接收管線預設會使用標準的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 接收管線。</span><span class="sxs-lookup"><span data-stu-id="8ad8f-107">These send ports default to the standard [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] send pipeline, and the sync send port receive pipeline defaults to the standard [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] receive pipeline.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ad8f-108">在 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台中變更 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管線，可能會重設您直接在 [BizTalk 總管] 中變更的屬性。</span><span class="sxs-lookup"><span data-stu-id="8ad8f-108">Changing the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] pipeline in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console might reset properties that you changed directly in BizTalk Explorer.</span></span>  
  
### <a name="to-change-the-send-or-receive-pipeline-that-btarn-uses"></a><span data-ttu-id="8ad8f-109">變更 BTARN 使用的傳送管線和接收管線</span><span class="sxs-lookup"><span data-stu-id="8ad8f-109">To change the send or receive pipeline that BTARN uses</span></span>  
  
1.  <span data-ttu-id="8ad8f-110">按一下**啟動**，指向 **程式**，指向  **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]**管理主控台**.</span><span class="sxs-lookup"><span data-stu-id="8ad8f-110">Click **Start**, point to **Programs**, point to **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.</span></span>  
  
2.  <span data-ttu-id="8ad8f-111">在 BTARN 管理主控台中，以滑鼠右鍵按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]節點，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="8ad8f-111">In the BTARN Management Console, right-click the [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] node, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="8ad8f-112">在全域屬性] 對話方塊中，從下拉式清單中，選取不同的管線，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="8ad8f-112">In the Global Properties dialog box, select a different pipeline from the drop-down list, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="8ad8f-113">在**主控件執行個體**節點下的[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]**管理** 節點，停止並重新啟動主機。</span><span class="sxs-lookup"><span data-stu-id="8ad8f-113">In the **Host Instances** node under the [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]**Administration** node, stop and then restart the host.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8ad8f-114">只有當您重新啟動 BizTalk Server 後，管線的變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="8ad8f-114">The changes to the pipelines will only take effect if you restart the BizTalk Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ad8f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ad8f-115">See Also</span></span>  
 <span data-ttu-id="8ad8f-116">[管理設定、 憑證、 資料庫和安全性](manage-configuration-certificates-databases-security.md) </span><span class="sxs-lookup"><span data-stu-id="8ad8f-116">[Manage configuration, certificates, databases, and security](manage-configuration-certificates-databases-security.md) </span></span>  
 [<span data-ttu-id="8ad8f-117">啟用 BAM 追蹤</span><span class="sxs-lookup"><span data-stu-id="8ad8f-117">Enabling BAM Tracking</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/enabling-bam-tracking.md)