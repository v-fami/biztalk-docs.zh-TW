---
title: 設定 ASPX 頁面的連線逾時 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ASPX pages, connection time-out
- connections, time-out
ms.assetid: 61d9c996-caf4-48bd-bda7-52f2797a941b
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83e083b9f2f0262095e58b4ed9842627888773dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22207190"
---
# <a name="setting-the-connection-time-out-for-an-aspx-page"></a><span data-ttu-id="61c27-102">設定 ASPX 頁面的連線逾時</span><span class="sxs-lookup"><span data-stu-id="61c27-102">Setting the Connection Time-Out for an ASPX Page</span></span>
<span data-ttu-id="61c27-103">當您使用 ASPX 頁面來處理同步訊息時，必須要增加 ASPX 頁面的連線逾時，如此它才有足夠時間等待預期的訊息。</span><span class="sxs-lookup"><span data-stu-id="61c27-103">When you use an ASPX page for synchronous messages, you must increase the connection time-out for the ASPX page so that it can wait for the expected message.</span></span>  
  
 <span data-ttu-id="61c27-104">增加 ASPX 頁面的連線逾時可能會發生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="61c27-104">Increasing the connection time-out for the ASPX page can have unintended consequences.</span></span> <span data-ttu-id="61c27-105">首先，遭到拒絕服務攻擊的風險會增加，而且耗盡執行緒集區的威脅也會增加。</span><span class="sxs-lookup"><span data-stu-id="61c27-105">First, it increases the risk of a denial-of-service attack and the threat of exhausting the thread pool.</span></span> <span data-ttu-id="61c27-106">再來就是，如果這個 ASPX 頁面上有太多的同步連線，系統便會鎖死這些連線。</span><span class="sxs-lookup"><span data-stu-id="61c27-106">Second, if there are too many synchronous connections on the ASPX page, the system can lock up.</span></span> <span data-ttu-id="61c27-107">所以，當您必須要增加連線逾時的時候，請注意不要增加太多。</span><span class="sxs-lookup"><span data-stu-id="61c27-107">Therefore, while you must increase the connection time-out, be careful not to increase it too much.</span></span>  
  
 <span data-ttu-id="61c27-108">將連線逾時設定為 RosettaNet 組織允許的最小值。</span><span class="sxs-lookup"><span data-stu-id="61c27-108">Set the connection time-out to the minimum allowed by the RosettaNet organization.</span></span> <span data-ttu-id="61c27-109">如需 RosettaNet PIP 規格的「交易夥伴介面程序 (PIP)」中，有關時序參數的詳細資訊，請參閱表 4-3：訊息交換控制項。</span><span class="sxs-lookup"><span data-stu-id="61c27-109">For more information about the timing parameters for a Partner Interface Process (PIP), see Table 4-3: Message Exchange Controls, in the RosettaNet PIP Specification.</span></span>  
  
### <a name="to-set-the-connection-time-out-for-the-aspx-page"></a><span data-ttu-id="61c27-110">設定 ASPX 頁面的連線逾時</span><span class="sxs-lookup"><span data-stu-id="61c27-110">To set the connection time-out for the ASPX page</span></span>  
  
1.  <span data-ttu-id="61c27-111">按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，然後按一下**網際網路資訊服務 (IIS) 管理員**.</span><span class="sxs-lookup"><span data-stu-id="61c27-111">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="61c27-112">在 [IIS 管理員] 中，展開本機電腦的節點，然後展開**網站**。</span><span class="sxs-lookup"><span data-stu-id="61c27-112">In IIS Manager, expand the node for the local computer, and then expand **Web Sites**.</span></span>  
  
3.  <span data-ttu-id="61c27-113">以滑鼠右鍵按一下 **[預設網站]**，然後按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="61c27-113">Right-click **Default Web Site**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="61c27-114">在 [預設的網站內容] 對話方塊上**網站**索引標籤的**連接逾時**方塊中輸入適當的值，然後再按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="61c27-114">In the Default Web Site Properties dialog box, on the **Web Site** tab, in the **Connection Timeout** box, type an appropriate value, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61c27-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61c27-115">See Also</span></span>  
 [<span data-ttu-id="61c27-116">程式設計指南</span><span class="sxs-lookup"><span data-stu-id="61c27-116">Programming Guide</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)