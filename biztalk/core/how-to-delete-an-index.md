---
title: 如何刪除索引 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- indexes [BAM], deleting
- Get-Index command [BAM]
- aggregations [BAM], indexes
ms.assetid: 5f9c7989-3357-451f-8565-1d4b01c1d16a
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9934c333699b853a3e10a0e5ecf212acf17fa6c6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25970468"
---
# <a name="how-to-delete-an-index"></a><span data-ttu-id="5ff20-102">如何刪除索引</span><span class="sxs-lookup"><span data-stu-id="5ff20-102">How to Delete an Index</span></span>
<span data-ttu-id="5ff20-103">系統管理員使用**刪除索引**命令來刪除指定的活動，在指定的檢查點的索引。</span><span class="sxs-lookup"><span data-stu-id="5ff20-103">Administrators use the **delete-index** command to delete an index on the specified activity at the specified checkpoints.</span></span>  
  
### <a name="to-delete-an-index-on-an-activity"></a><span data-ttu-id="5ff20-104">刪除活動的索引</span><span class="sxs-lookup"><span data-stu-id="5ff20-104">To delete an index on an activity</span></span>  
  
1.  <span data-ttu-id="5ff20-105">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="5ff20-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="5ff20-106">在命令提示字元中，輸入 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking，以瀏覽至追蹤資料夾。</span><span class="sxs-lookup"><span data-stu-id="5ff20-106">Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt.</span></span> <span data-ttu-id="5ff20-107">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="5ff20-107">Press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="5ff20-108">型別**bm delete-IndexName:\<索引名稱\>-活動：\<活動名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="5ff20-108">Type **bm delete-index -IndexName:\<index name\> -Activity:\<activity name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5ff20-109">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="5ff20-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="5ff20-110">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="5ff20-110">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ff20-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="5ff20-111">See Also</span></span>  
 <span data-ttu-id="5ff20-112">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="5ff20-112">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="5ff20-113">[BAM 管理公用程式](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="5ff20-113">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 <span data-ttu-id="5ff20-114">[如何刪除索引](../core/how-to-delete-an-index.md) </span><span class="sxs-lookup"><span data-stu-id="5ff20-114">[How to Delete an Index](../core/how-to-delete-an-index.md) </span></span>  
 [<span data-ttu-id="5ff20-115">如何取得彙總的索引清單</span><span class="sxs-lookup"><span data-stu-id="5ff20-115">How to Get a List of Indexes on an Aggregation</span></span>](../core/how-to-get-a-list-of-indexes-on-an-aggregation.md)