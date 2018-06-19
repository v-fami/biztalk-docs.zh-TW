---
title: 停用 BAM 追蹤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FIN Response Reconciliation, disabling BAM tracking
- BAM tracking
ms.assetid: ea5fef0e-7a96-46f5-81d8-9b1d8a5d24d2
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4e734bd31147ecacc8bbbe98d98297edfb4f0de
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209046"
---
# <a name="disabling-bam-tracking"></a><span data-ttu-id="86d38-102">停用 BAM 追蹤</span><span class="sxs-lookup"><span data-stu-id="86d38-102">Disabling BAM Tracking</span></span>
<span data-ttu-id="86d38-103">根據預設，已啟用 BAM 追蹤 FIN 回應調整。</span><span class="sxs-lookup"><span data-stu-id="86d38-103">By default, BAM tracking is enabled for FIN Response Reconciliation.</span></span> <span data-ttu-id="86d38-104">您可以停用它，如下所示。</span><span class="sxs-lookup"><span data-stu-id="86d38-104">You can disable it as follows.</span></span>  
  
### <a name="to-disable-bam-tracking-for-frr"></a><span data-ttu-id="86d38-105">若要停用 BAM 追蹤 FRR</span><span class="sxs-lookup"><span data-stu-id="86d38-105">To disable BAM tracking for FRR</span></span>  
  
1.  <span data-ttu-id="86d38-106">按一下**啟動**，按一下 **執行**，型別**regedit**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="86d38-106">Click **Start**, click **Run**, type **regedit**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="86d38-107">在左窗格的登錄編輯程式中，移至 我的電腦/HKEY_LOCAL_MACHINE/軟體/Microsoft/BizTalk Accelerator for SWIFT/FRR。</span><span class="sxs-lookup"><span data-stu-id="86d38-107">In the left pane of the Registry Editor, move to My Computer/HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/BizTalk Accelerator for SWIFT/FRR.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="86d38-108">每一部電腦上執行 FIN 回應對帳必須修改此登錄項目。</span><span class="sxs-lookup"><span data-stu-id="86d38-108">This registry entry must be modified on each computer that FIN Response Reconciliation is running on.</span></span>  
  
3.  <span data-ttu-id="86d38-109">在右窗格的登錄編輯程式中，按兩下**BAMTrackingEnabled**。</span><span class="sxs-lookup"><span data-stu-id="86d38-109">In the right pane of the Registry Editor, double-click **BAMTrackingEnabled**.</span></span>  
  
4.  <span data-ttu-id="86d38-110">在**編輯 DWORD 值**對話方塊中，於**數值資料**方塊中，輸入**0**停用 BAM 追蹤。</span><span class="sxs-lookup"><span data-stu-id="86d38-110">In the **Edit DWORD Value** dialog box, in the **Value data** box, type **0** to disable BAM tracking.</span></span>  
  
5.  <span data-ttu-id="86d38-111">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="86d38-111">Click **OK**.</span></span>