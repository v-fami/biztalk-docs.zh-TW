---
title: 如何停用 BAM 主要匯入資料庫參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 78d2d644-6ebb-4051-ae59-af7d0fb75753
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b89e9df78d91a6e4737b964223f81983e74dd29
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998191"
---
# <a name="how-to-disable-a-bam-primary-import-database-reference"></a><span data-ttu-id="d93bc-102">如何停用 BAM 主要匯入資料庫參考</span><span class="sxs-lookup"><span data-stu-id="d93bc-102">How to Disable a BAM Primary Import Database Reference</span></span>
<span data-ttu-id="d93bc-103">系統管理員可以使用**停用參考**命令以停用指定的 BAM 主要匯入資料庫的參考。</span><span class="sxs-lookup"><span data-stu-id="d93bc-103">Administrators use the **disable-reference** command to disable a reference to a specified BAM Primary Import database.</span></span>  
  
### <a name="to-disable-a-reference-to-a-bam-primary-import-database"></a><span data-ttu-id="d93bc-104">停用 BAM 主要匯入資料庫的參考</span><span class="sxs-lookup"><span data-stu-id="d93bc-104">To disable a reference to a BAM Primary Import database</span></span>  
  
1. <span data-ttu-id="d93bc-105">開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="d93bc-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="d93bc-106">瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="d93bc-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3. <span data-ttu-id="d93bc-107">在命令提示字元輸入下列命令： **bm 停用參考 TargetServer:\<目標伺服器\>-TargetDatabase:\<目標資料庫\>[-Server:\<伺服器\> ][-Database:\<資料庫\>]**，其中**\<**<em>目標伺服器</em>**\>** 以由目標 BAM 主要匯入資料庫所指定的 SQL server 名稱取代\<*目標資料庫*\>所在。</span><span class="sxs-lookup"><span data-stu-id="d93bc-107">Type the following at the command line prompt: **bm disable-reference -TargetServer:\<target server\> -TargetDatabase:\<target database\>[ -Server:\<server\> ][ -Database:\<database\> ]**, where **\<**<em>target server</em>**\>** is replaced by the name of the SQL server on which the target BAM Primary Import database specified by \<*target database*\> resides.</span></span> <span data-ttu-id="d93bc-108">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="d93bc-108">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d93bc-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d93bc-109">See Also</span></span>  
 [<span data-ttu-id="d93bc-110">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="d93bc-110">BAM Management Utility</span></span>](../core/bam-management-utility.md)