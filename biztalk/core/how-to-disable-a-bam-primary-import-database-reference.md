---
title: 如何停用 BAM 主要匯入資料庫參考 |Microsoft 文件
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
ms.openlocfilehash: fc9afef7bdcfad84f105abda158c5ed5c6461619
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968892"
---
# <a name="how-to-disable-a-bam-primary-import-database-reference"></a><span data-ttu-id="86bec-102">如何停用 BAM 主要匯入資料庫參考</span><span class="sxs-lookup"><span data-stu-id="86bec-102">How to Disable a BAM Primary Import Database Reference</span></span>
<span data-ttu-id="86bec-103">系統管理員使用**停用參考**命令以停用指定的 BAM 主要匯入資料庫的參考。</span><span class="sxs-lookup"><span data-stu-id="86bec-103">Administrators use the **disable-reference** command to disable a reference to a specified BAM Primary Import database.</span></span>  
  
### <a name="to-disable-a-reference-to-a-bam-primary-import-database"></a><span data-ttu-id="86bec-104">停用 BAM 主要匯入資料庫的參考</span><span class="sxs-lookup"><span data-stu-id="86bec-104">To disable a reference to a BAM Primary Import database</span></span>  
  
1.  <span data-ttu-id="86bec-105">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="86bec-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="86bec-106">瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="86bec-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="86bec-107">在命令提示字元輸入下列命令： **bm 停用參考 TargetServer:\<目標伺服器\>-TargetDatabase:\<目標資料庫\>[-Server:\<伺服器\> ][-Database:\<資料庫\>]**，其中 **\<** *目標伺服器* **\>** 會以所指定的目標 BAM 主要匯入資料庫的 SQL server 名稱取代\<*目標資料庫*\>所在。</span><span class="sxs-lookup"><span data-stu-id="86bec-107">Type the following at the command line prompt: **bm disable-reference -TargetServer:\<target server\> -TargetDatabase:\<target database\>[ -Server:\<server\> ][ -Database:\<database\> ]**, where **\<***target server***\>** is replaced by the name of the SQL server on which the target BAM Primary Import database specified by \<*target database*\> resides.</span></span> <span data-ttu-id="86bec-108">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="86bec-108">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86bec-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="86bec-109">See Also</span></span>  
 [<span data-ttu-id="86bec-110">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="86bec-110">BAM Management Utility</span></span>](../core/bam-management-utility.md)