---
title: "如何參考其他 BAM 主要匯入資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea80b32c-f2cb-4aca-89f4-d5b72e1ba021
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fca916339e48f6bce053753111f4467a4c9ae7d5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-reference-additional-bam-primary-import-databases"></a><span data-ttu-id="17cab-102">如何參考其他 BAM 主要匯入資料庫</span><span class="sxs-lookup"><span data-stu-id="17cab-102">How to Reference Additional BAM Primary Import Databases</span></span>
<span data-ttu-id="17cab-103">系統管理員使用**啟用參考**命令參考其他 BAM 主要匯入資料庫。</span><span class="sxs-lookup"><span data-stu-id="17cab-103">Administrators use the **enable-reference** command to reference additional BAM Primary Import databases.</span></span> <span data-ttu-id="17cab-104">參考多個 BAM 主要匯入資料庫有助於檢視分散式 BAM 活動。</span><span class="sxs-lookup"><span data-stu-id="17cab-104">You reference multiple BAM Primary Import databases to facilitate viewing distributed BAM activities.</span></span>  
  
### <a name="to-enable-a-reference-to-an-additional-bam-primary-import-database"></a><span data-ttu-id="17cab-105">啟用參考其他 BAM 主要匯入資料庫</span><span class="sxs-lookup"><span data-stu-id="17cab-105">To enable a reference to an additional BAM Primary Import database</span></span>  
  
1.  <span data-ttu-id="17cab-106">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="17cab-106">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="17cab-107">瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="17cab-107">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="17cab-108">在命令提示字元輸入下列命令： **bm 啟用參考 TargetServer:\<目標伺服器\>-TargetDatabase:\<目標資料庫\>**，其中\<*目標伺服器*\>會以所指定的目標 BAM 主要匯入資料庫的 SQL server 名稱取代\<目標資料庫\>所在。</span><span class="sxs-lookup"><span data-stu-id="17cab-108">Type the following at the command line prompt: **bm enable-reference -TargetServer:\<target server\> -TargetDatabase:\<target database\>**, where \<*target server*\> is replaced by the name of the SQL server on which the target BAM Primary Import database specified by \<target database\> resides.</span></span> <span data-ttu-id="17cab-109">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="17cab-109">Press ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17cab-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="17cab-110">See Also</span></span>  
 [<span data-ttu-id="17cab-111">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="17cab-111">BAM Management Utility</span></span>](../core/bam-management-utility.md)