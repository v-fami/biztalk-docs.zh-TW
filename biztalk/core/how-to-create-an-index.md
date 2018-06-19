---
title: 如何建立索引 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Create-Index command [BAM]
- indexes [BAM], creating
- indexes [BAM], aggregations
- creating, indexes [BAM]
- aggregations [BAM], indexes
ms.assetid: 456d94e6-2e84-4d12-ad38-49f9eeb103f3
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61c0393beae4883359d71915543b629e41c5f6ec
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25969284"
---
# <a name="how-to-create-an-index"></a><span data-ttu-id="1fff0-102">如何建立索引</span><span class="sxs-lookup"><span data-stu-id="1fff0-102">How to Create an Index</span></span>
<span data-ttu-id="1fff0-103">系統管理員使用**建立索引**命令上指定之檢查點指定的活動建立索引。</span><span class="sxs-lookup"><span data-stu-id="1fff0-103">Administrators use the **create-index** command to create an index on the specified activity at the specified checkpoints.</span></span>  
  
### <a name="to-create-an-index-on-an-activity"></a><span data-ttu-id="1fff0-104">若要建立活動的索引</span><span class="sxs-lookup"><span data-stu-id="1fff0-104">To create an index on an activity</span></span>  
  
1.  <span data-ttu-id="1fff0-105">從命令提示字元，瀏覽至下列目錄：[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]追蹤。</span><span class="sxs-lookup"><span data-stu-id="1fff0-105">From a command prompt, browse to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
2.  <span data-ttu-id="1fff0-106">型別**bm 建立-IndexName:\<索引名稱\>-活動：\<活動名稱\>-檢查點：\<checkpoint1\>**。</span><span class="sxs-lookup"><span data-stu-id="1fff0-106">Type **bm create-index -IndexName:\<index name\> -Activity:\<activity name\> -Checkpoint:\<checkpoint1\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1fff0-107">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="1fff0-107">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
3.  <span data-ttu-id="1fff0-108">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="1fff0-108">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fff0-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="1fff0-109">See Also</span></span>  
 <span data-ttu-id="1fff0-110">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="1fff0-110">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="1fff0-111">[BAM 管理公用程式](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="1fff0-111">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 <span data-ttu-id="1fff0-112">[如何刪除索引](../core/how-to-delete-an-index.md) </span><span class="sxs-lookup"><span data-stu-id="1fff0-112">[How to Delete an Index](../core/how-to-delete-an-index.md) </span></span>  
 [<span data-ttu-id="1fff0-113">如何取得彙總的索引清單</span><span class="sxs-lookup"><span data-stu-id="1fff0-113">How to Get a List of Indexes on an Aggregation</span></span>](../core/how-to-get-a-list-of-indexes-on-an-aggregation.md)