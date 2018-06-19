---
title: 啟用 BAM 追蹤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAM tracking, enabling
- BAM tracking, disabling
ms.assetid: 3fee3315-fba7-4eea-89f3-6a061b450bb8
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90fae70edf7f748de3790aeaa9e13e3381c44c48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22210054"
---
# <a name="enabling-bam-tracking"></a><span data-ttu-id="bc511-102">啟用 BAM 追蹤</span><span class="sxs-lookup"><span data-stu-id="bc511-102">Enabling BAM Tracking</span></span>
[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]<span data-ttu-id="bc511-103"> 支援使用商務活動監控 (BAM) 的進階追蹤。</span><span class="sxs-lookup"><span data-stu-id="bc511-103"> supports enhanced tracking using BizTalk Activity Monitoring (BAM).</span></span> <span data-ttu-id="bc511-104">您可以在 BTARN 組態的全域屬性中啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="bc511-104">You enable tracking as part of the global properties of the BTARN configuration.</span></span> <span data-ttu-id="bc511-105">啟用追蹤後，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 將追蹤全部協議的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="bc511-105">After you enable tracking, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] tracks all messages for all agreements.</span></span> <span data-ttu-id="bc511-106">根據預設，會啟用追蹤功能。</span><span class="sxs-lookup"><span data-stu-id="bc511-106">By default, tracking is enabled.</span></span>  
  
 <span data-ttu-id="bc511-107">如需有關追蹤的詳細資訊，請參閱[增強追蹤](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md)。</span><span class="sxs-lookup"><span data-stu-id="bc511-107">For more information about tracking, see [Enhanced Tracking](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md).</span></span>  
  
### <a name="to-enable-or-disable-bam-tracking"></a><span data-ttu-id="bc511-108">啟用或停用 BAM 追蹤</span><span class="sxs-lookup"><span data-stu-id="bc511-108">To enable or disable BAM tracking</span></span>  
  
1.  <span data-ttu-id="bc511-109">按一下**啟動**，指向 **程式**，指向  **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]**管理主控台**.</span><span class="sxs-lookup"><span data-stu-id="bc511-109">Click **Start**, point to **Programs**, point to **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.</span></span>  
  
2.  <span data-ttu-id="bc511-110">以滑鼠右鍵按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]節點在範圍窗格中，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="bc511-110">Right-click the [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] node in the scope pane, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="bc511-111">在**全域屬性**對話方塊中，選取**啟用 BAM 追蹤**以啟用追蹤，或清除此選項可將它停用。</span><span class="sxs-lookup"><span data-stu-id="bc511-111">In the **Global Properties** dialog box, select **Enable BAM Tracking** to enable tracking, or clear this option to disable it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bc511-112">每當您變更啟用旗標以啟用或停用追蹤時，都必須重新啟動公開程序與 HTTP 配接器執行所在的全部服務。</span><span class="sxs-lookup"><span data-stu-id="bc511-112">Whenever you change the enable flag to enable or disable tracking, you have to restart all services on which the public processes and the HTTP adapter are running.</span></span> <span data-ttu-id="bc511-113">這包括主機服務和外掛式主控的件服務。</span><span class="sxs-lookup"><span data-stu-id="bc511-113">This includes the host service and the isolated host service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc511-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc511-114">See Also</span></span>  
 <span data-ttu-id="bc511-115">[管理設定、 憑證、 資料庫和安全性](manage-configuration-certificates-databases-security.md) </span><span class="sxs-lookup"><span data-stu-id="bc511-115">[Manage configuration, certificates, databases, and security](manage-configuration-certificates-databases-security.md) </span></span>  
 <span data-ttu-id="bc511-116">[增強的追蹤](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md) </span><span class="sxs-lookup"><span data-stu-id="bc511-116">[Enhanced Tracking](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md) </span></span>  
 [<span data-ttu-id="bc511-117">管理 BTARN 組態</span><span class="sxs-lookup"><span data-stu-id="bc511-117">Administering the BTARN Configuration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/administering-the-btarn-configuration.md)