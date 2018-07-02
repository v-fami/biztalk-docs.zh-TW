---
title: 如何列出所有被參考資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f6166dd-6228-45c2-98ef-4de2a4345189
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76a953933d72803b718353f7d0456317585b1458
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968471"
---
# <a name="how-to-list-all-referenced-databases"></a><span data-ttu-id="3bb66-102">如何列出所有被參考資料庫</span><span class="sxs-lookup"><span data-stu-id="3bb66-102">How to List All Referenced Databases</span></span>
<span data-ttu-id="3bb66-103">系統管理員可以使用**取得參考**來列出本機 BAM 主要匯入資料庫的參考會提供其他 BizTalk 伺服器上的 BAM 主要匯入資料庫的所有命令。</span><span class="sxs-lookup"><span data-stu-id="3bb66-103">Administrators use the **get-references** command to list all of the BAM Primary Import databases on other BizTalk servers that have been given references to the local BAM Primary Import database.</span></span>  
  
### <a name="to-list-all-referenced-databases"></a><span data-ttu-id="3bb66-104">列出所有參考資料庫</span><span class="sxs-lookup"><span data-stu-id="3bb66-104">To list all referenced databases</span></span>  
  
1. <span data-ttu-id="3bb66-105">開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="3bb66-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="3bb66-106">瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="3bb66-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3. <span data-ttu-id="3bb66-107">在命令提示字元輸入下列命令： **bm.exe get 參考**。</span><span class="sxs-lookup"><span data-stu-id="3bb66-107">Type the following at the command line prompt: **bm.exe get-references**.</span></span> <span data-ttu-id="3bb66-108">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="3bb66-108">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bb66-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bb66-109">See Also</span></span>  
 [<span data-ttu-id="3bb66-110">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="3bb66-110">BAM Management Utility</span></span>](../core/bam-management-utility.md)