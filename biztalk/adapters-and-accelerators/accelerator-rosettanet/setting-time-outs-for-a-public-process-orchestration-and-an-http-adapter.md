---
title: 設定逾時設定公開程序協調流程和 HTTP 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- public processes, HTTP adapters
- public processes, orchestrations
- orchestrations, time-outs
- public processes, time-outs
- orchestrations, public-process orchestrations
- HTTP adapters, public processes
- HTTP adapters, time-outs
ms.assetid: 82fd64ac-6191-410c-94b3-8a3d1ff2611f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e0977589e310746e2c75c1f89fdd2c41ecb86aa
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976711"
---
# <a name="setting-time-outs-for-a-public-process-orchestration-and-an-http-adapter"></a><span data-ttu-id="8765b-102">設定逾時設定公開程序協調流程和 HTTP 配接器</span><span class="sxs-lookup"><span data-stu-id="8765b-102">Setting Time-Outs for a Public-Process Orchestration and an HTTP Adapter</span></span>
<span data-ttu-id="8765b-103">當您在同步實例中，與 HTTP 配接器搭配使用公開程序協調流程時，必須分別為它們設定逾時設定。</span><span class="sxs-lookup"><span data-stu-id="8765b-103">When you use a public-process orchestration with an HTTP adapter in a synchronous scenario, you must set the time-outs for each appropriately.</span></span> <span data-ttu-id="8765b-104">協調流程的逾時設定 (執行時間) 必須小於 HTTP 配接器的逾時設定 (要求逾時)。</span><span class="sxs-lookup"><span data-stu-id="8765b-104">The time-out setting for the orchestration (Time to Perform) must be smaller than the time-out for the HTTP adapter (Request Timeout).</span></span> <span data-ttu-id="8765b-105">這是因為如果 HTTP 配接器的逾時設定比較小，配接器可能早在協調流程之前就逾時了。</span><span class="sxs-lookup"><span data-stu-id="8765b-105">This is because if the setting for the HTTP adapter is smaller, the adapter could time out before the orchestration.</span></span> <span data-ttu-id="8765b-106">這等於是給予配接器該程序的控制權。</span><span class="sxs-lookup"><span data-stu-id="8765b-106">This gives the adapter control of the process.</span></span> <span data-ttu-id="8765b-107">但是協調流程必須要在該程序中掌握控制權，所以它的逾時設定必須比較小。</span><span class="sxs-lookup"><span data-stu-id="8765b-107">The orchestration must be in control of the process; therefore, its time-out setting must be smaller.</span></span>  
  
### <a name="to-set-the-time-out-setting-for-the-http-adapter"></a><span data-ttu-id="8765b-108">設定 HTTP 配接器的逾時設定</span><span class="sxs-lookup"><span data-stu-id="8765b-108">To set the time-out setting for the HTTP adapter</span></span>  
  
1.  <span data-ttu-id="8765b-109">在 [BizTalk 總管] 中，展開**傳送埠**，然後按兩下與公開程序協調流程搭配使用 HTTP 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="8765b-109">In BizTalk Explorer, expand **Send ports**, and then double-click the HTTP send port used with the public-process orchestration.</span></span>  
  
2.  <span data-ttu-id="8765b-110">在 傳送埠屬性 視窗中，按一下 省略符號按鈕 (**...**) 的**位址 (URI)**。</span><span class="sxs-lookup"><span data-stu-id="8765b-110">In the Send Port Properties window, click the ellipsis button (**...**) for **Address (URI)**.</span></span>  
  
3.  <span data-ttu-id="8765b-111">在 [HTTP 傳輸屬性] 視窗中，在 [一般] 窗格中，在**要求逾時 （秒）** 方塊中，輸入適當的值，表示逾時值。此值必須大於**執行時間**設定 「 相關交易夥伴介面程序 (PIP)。</span><span class="sxs-lookup"><span data-stu-id="8765b-111">In the HTTP Transport Properties window, in the General pane, in the **Request timeout (sec.)** box, type an appropriate value for the time-out. This value must be larger than the **Time to Perform** setting for the relevant Partner Interface Process (PIP).</span></span>  
  
4.  <span data-ttu-id="8765b-112">按一下  **確定**，然後按一下**確定**一次。</span><span class="sxs-lookup"><span data-stu-id="8765b-112">Click **OK**, and then click **OK** again.</span></span>  
  
### <a name="to-set-the-time-out-setting-for-the-public-process-orchestration"></a><span data-ttu-id="8765b-113">若要設定公開程序協調流程的逾時設定</span><span class="sxs-lookup"><span data-stu-id="8765b-113">To set the time-out setting for the public-process orchestration</span></span>  
  
1. <span data-ttu-id="8765b-114">按一下 **開始**，指向**所有程式**，指向**Microsoft BizTalk\<版本\>Accelerator for RosettaNet**，然後按一下**BizTalk Accelerator for RosettaNet 管理主控台**。</span><span class="sxs-lookup"><span data-stu-id="8765b-114">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for RosettaNet**, and then click  **BizTalk Accelerator for RosettaNet Management Console**.</span></span>  
  
2. <span data-ttu-id="8765b-115">依序展開[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下**程序組態設定**。</span><span class="sxs-lookup"><span data-stu-id="8765b-115">Expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click **Process Configuration Settings**.</span></span>  
  
3. <span data-ttu-id="8765b-116">以滑鼠右鍵按一下您想要設定的逾時設定，PIP，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="8765b-116">Right-click the PIP that you want to set the time-out setting for, and then click **Properties**.</span></span>  
  
4. <span data-ttu-id="8765b-117">在 [內容] 對話方塊中，在**活動**索引標籤中，於**執行時間**方塊中輸入適當的值小於 HTTP 配接器逾時設定，然後再按一下 **[確定]**.</span><span class="sxs-lookup"><span data-stu-id="8765b-117">In theProperties dialog box, on the **Activity** tab, in the **Time to Perform** box, type an appropriate value that is smaller than the HTTP adapter time-out setting, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8765b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8765b-118">See Also</span></span>  
 [<span data-ttu-id="8765b-119">程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8765b-119">Programming Guide</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)