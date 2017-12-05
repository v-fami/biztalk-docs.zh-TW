---
title: "如何移除 BAM 檢視 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, views
- managing [BAM definitions], deleting views
- Remove-View command [BAM]
ms.assetid: 1a43ec81-20b1-41f7-941f-753132ac9ed2
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc49038c30cc6016c79f8e0d309f93217994327f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-remove-bam-views"></a><span data-ttu-id="2b0b5-102">如何移除 BAM 檢視</span><span class="sxs-lookup"><span data-stu-id="2b0b5-102">How to Remove BAM Views</span></span>
<span data-ttu-id="2b0b5-103">系統管理員使用**移除檢視**命令，從 BAM 主要匯入資料庫移除檢視。</span><span class="sxs-lookup"><span data-stu-id="2b0b5-103">Administrators use the **remove-view** command to remove a view from the BAM Primary Import database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b0b5-104">當您移除檢視時，也會自動移除該檢視所定義的任何警示。</span><span class="sxs-lookup"><span data-stu-id="2b0b5-104">When you remove a view, you also automatically remove any alerts defined for that view.</span></span>  
  
### <a name="to-remove-bam-views"></a><span data-ttu-id="2b0b5-105">若要移除 BAM 檢視</span><span class="sxs-lookup"><span data-stu-id="2b0b5-105">To remove BAM views</span></span>  
  
1.  <span data-ttu-id="2b0b5-106">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="2b0b5-106">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="2b0b5-107">瀏覽至追蹤資料夾，輸入**C:\Program Files\Microsoft BizTalk Server 2009 \tracking**在命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="2b0b5-107">Navigate to the tracking folder by typing **C:\Program Files\Microsoft BizTalk Server 2009\Tracking** at the command prompt.</span></span> <span data-ttu-id="2b0b5-108">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="2b0b5-108">Press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="2b0b5-109">型別**bm 移除檢視的名稱：\<檢視名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="2b0b5-109">Type **bm remove-view -Name:\<view name\>**.</span></span>  
  
4.  <span data-ttu-id="2b0b5-110">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="2b0b5-110">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b0b5-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="2b0b5-111">See Also</span></span>  
 <span data-ttu-id="2b0b5-112">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="2b0b5-112">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="2b0b5-113">[BAM 安全性建議](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="2b0b5-113">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 <span data-ttu-id="2b0b5-114">[BAM 管理公用程式](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="2b0b5-114">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="2b0b5-115">如何移除 BAM 警示</span><span class="sxs-lookup"><span data-stu-id="2b0b5-115">How to Remove BAM Alerts</span></span>](../core/how-to-remove-bam-alerts.md)