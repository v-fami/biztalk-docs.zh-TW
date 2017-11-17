---
title: "如何移除 BAM 定義 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- definitions [BAM], deleting
- deleting, definitions [BAM]
- managing [BAM definitions], deleting definitions
- Remove-All command
ms.assetid: a905f54b-7c55-49b8-809b-030ad65f3e46
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bce5454528b3dc1cf0feb54a52eae2008e607811
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-bam-definitions"></a><span data-ttu-id="4c1b9-102">如何移除 BAM 定義</span><span class="sxs-lookup"><span data-stu-id="4c1b9-102">How to Remove BAM Definitions</span></span>
<span data-ttu-id="4c1b9-103">系統管理員使用**移除 all** BAM 管理公用程式移除所有的檢視及基礎活動表特定 BAM 定義檔案所需的命令。</span><span class="sxs-lookup"><span data-stu-id="4c1b9-103">Administrators use the **remove-all** command of the BAM Management utility to remove all views and underlying activity tables for a particular BAM definition file.</span></span>  
  
### <a name="to-remove-bam-definitions"></a><span data-ttu-id="4c1b9-104">移除 BAM 定義</span><span class="sxs-lookup"><span data-stu-id="4c1b9-104">To Remove BAM definitions</span></span>  
  
1.  <span data-ttu-id="4c1b9-105">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="4c1b9-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="4c1b9-106">瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="4c1b9-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="4c1b9-107">型別**bm 移除 all DefinitionFile:\<def 檔 >**。</span><span class="sxs-lookup"><span data-stu-id="4c1b9-107">Type **bm remove-all DefinitionFile:\<def file>**.</span></span>  
  
4.  <span data-ttu-id="4c1b9-108">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="4c1b9-108">Press ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c1b9-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c1b9-109">See Also</span></span>  
 <span data-ttu-id="4c1b9-110">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="4c1b9-110">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 [<span data-ttu-id="4c1b9-111">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="4c1b9-111">BAM Management Utility</span></span>](../core/bam-management-utility.md)