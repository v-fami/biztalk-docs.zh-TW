---
title: "設定 FRR 延遲逾時 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FIN Response Reconciliation, configuring delay time-out
ms.assetid: 62209bf6-56c8-483a-96d5-328bffc8b680
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fbf4c08984876627c0f11f935b0be3e32769b5f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="setting-the-frr-delay-time-out"></a><span data-ttu-id="05e7f-102">設定 FRR 延遲逾時</span><span class="sxs-lookup"><span data-stu-id="05e7f-102">Setting the FRR Delay Time-Out</span></span>
<span data-ttu-id="05e7f-103">您必須設定 FRR 協調流程的逾時時間後一些持續時間，因此它不會等待 FNN 回應無限期。</span><span class="sxs-lookup"><span data-stu-id="05e7f-103">You must configure the FRR orchestration to time out after some duration, so it will not wait for the FNN response indefinitely.</span></span> <span data-ttu-id="05e7f-104">如果逾時期間到期，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]發行至自訂的逾時的處理常式逾時訊息。</span><span class="sxs-lookup"><span data-stu-id="05e7f-104">If the time-out duration expires, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] publishes the timed-out messages to a custom time-out handler.</span></span>  
  
### <a name="to-set-the-frr-delay-time-out"></a><span data-ttu-id="05e7f-105">若要設定 FRR 延遲逾時</span><span class="sxs-lookup"><span data-stu-id="05e7f-105">To set the FRR delay time-out</span></span>  
  
1.  <span data-ttu-id="05e7f-106">按一下**啟動**，按一下 **執行**，型別**regedit**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="05e7f-106">Click **Start**, click **Run**, type **regedit**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="05e7f-107">在左窗格的登錄編輯程式中，移至 我的電腦/HKEY_LOCAL_MACHINE/軟體/Microsoft/BizTalk Accelerator for SWIFT/FRR。</span><span class="sxs-lookup"><span data-stu-id="05e7f-107">In the left pane of the Registry Editor, move to My Computer/HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/BizTalk Accelerator for SWIFT/FRR.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="05e7f-108">在 [角色] 節點中所定義的工作流程中的位置，將會加入角色。</span><span class="sxs-lookup"><span data-stu-id="05e7f-108">The role will be added in the position in the workflow that is defined in the Roles node.</span></span> <span data-ttu-id="05e7f-109">若要變更該位置，您需要執行步驟 8，變更順序的 [角色] 節點中的角色。</span><span class="sxs-lookup"><span data-stu-id="05e7f-109">To change that position, you need to perform step 8 to change the order of the roles in the Roles node.</span></span>  
  
3.  <span data-ttu-id="05e7f-110">在右窗格的登錄編輯程式中，按兩下**DelayTimeout**。</span><span class="sxs-lookup"><span data-stu-id="05e7f-110">In the right pane of the Registry Editor, double-click **DelayTimeout**.</span></span>  
  
4.  <span data-ttu-id="05e7f-111">在**編輯 DWORD 值**對話方塊中，於**數值資料**方塊中，以十六進位格式輸入逾時期間。</span><span class="sxs-lookup"><span data-stu-id="05e7f-111">In the **Edit DWORD Value** dialog box, in the **Value data** box, type the time-out duration in hexadecimal format.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="05e7f-112">預設值為**FRR DelayTimeout**屬性為 600 秒 （258 十六進位）。</span><span class="sxs-lookup"><span data-stu-id="05e7f-112">The default value for the **FRR DelayTimeout** property is 600 seconds (258 Hexadecimal).</span></span>  
  
5.  <span data-ttu-id="05e7f-113">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="05e7f-113">Click **OK**.</span></span>