---
title: 如何取得彙總的索引清單 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- indexes [BAM], listing indexes
- aggregations [BAM], listing indexes
- Get-Index command [BAM]
ms.assetid: 46a4a2fc-10f8-499c-bf2a-d0a19bb84151
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03c2d898237482550fda5304f9fd4731b6e06200
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37020100"
---
# <a name="how-to-get-a-list-of-indexes-on-an-aggregation"></a><span data-ttu-id="d1549-102">如何取得彙總的索引清單</span><span class="sxs-lookup"><span data-stu-id="d1549-102">How to Get a List of Indexes on an Aggregation</span></span>
<span data-ttu-id="d1549-103">系統管理員可以使用**get 索引**命令，以取得一份所有索引上指定的活動。</span><span class="sxs-lookup"><span data-stu-id="d1549-103">Administrators use the **get-index** command to get a list of all the indexes on the specified activity.</span></span>  
  
### <a name="to-get-a-list-of-indexes-on-an-aggregation"></a><span data-ttu-id="d1549-104">若要取得彙總的索引清單</span><span class="sxs-lookup"><span data-stu-id="d1549-104">To get a list of indexes on an aggregation</span></span>  
  
1. <span data-ttu-id="d1549-105">開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="d1549-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="d1549-106">瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="d1549-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3. <span data-ttu-id="d1549-107">型別**bm get 索引-活動：\<活動名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="d1549-107">Type **bm get-index -Activity:\<activity name\>**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="d1549-108">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="d1549-108">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4. <span data-ttu-id="d1549-109">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="d1549-109">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1549-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1549-110">See Also</span></span>  
 <span data-ttu-id="d1549-111">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="d1549-111">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="d1549-112">[BAM 管理公用程式](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="d1549-112">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 <span data-ttu-id="d1549-113">[如何刪除索引](../core/how-to-delete-an-index.md) </span><span class="sxs-lookup"><span data-stu-id="d1549-113">[How to Delete an Index](../core/how-to-delete-an-index.md) </span></span>  
 [<span data-ttu-id="d1549-114">如何建立索引</span><span class="sxs-lookup"><span data-stu-id="d1549-114">How to Create an Index</span></span>](../core/how-to-create-an-index.md)