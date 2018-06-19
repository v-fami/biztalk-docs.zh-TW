---
title: 如何從檢視移除帳戶 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Excel add-in [BAM], security
- managing [BAM], deleting accounts from views
- Remove-Account command [BAM]
ms.assetid: b74a64a0-ddb3-45d2-add7-6261c31be0f0
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e598dc13abb40a4b15d0624d68280c8f5279630a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971340"
---
# <a name="how-to-remove-accounts-from-a-view"></a><span data-ttu-id="1cb9a-102">如何從檢視移除帳戶</span><span class="sxs-lookup"><span data-stu-id="1cb9a-102">How to Remove Accounts from a View</span></span>
<span data-ttu-id="1cb9a-103">系統管理員使用**移除帳戶**命令移除 BAM 檢視中的使用者，並保護 BAM Excel 試算表檢視不會未經授權的存取。</span><span class="sxs-lookup"><span data-stu-id="1cb9a-103">Administrators use the **remove-account** command to remove users from BAM views and protect BAM Excel Spreadsheet views from unauthorized access.</span></span>  
  
 <span data-ttu-id="1cb9a-104">如需檢視 BAM 檢視的相關資訊，請參閱[如何列出 BAM 檢視](../core/how-to-list-bam-views.md)。</span><span class="sxs-lookup"><span data-stu-id="1cb9a-104">For information about viewing BAM views, see [How to List BAM Views](../core/how-to-list-bam-views.md).</span></span>  
  
### <a name="to-remove-an-account-from-a-view"></a><span data-ttu-id="1cb9a-105">從檢視移除帳戶</span><span class="sxs-lookup"><span data-stu-id="1cb9a-105">To remove an account from a view</span></span>  
  
1.  <span data-ttu-id="1cb9a-106">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="1cb9a-106">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="1cb9a-107">瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]追蹤</span><span class="sxs-lookup"><span data-stu-id="1cb9a-107">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking</span></span>  
  
3.  <span data-ttu-id="1cb9a-108">型別**bm 移除帳戶-AccountName:\<帳戶名稱\>-檢視：\<檢視名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="1cb9a-108">Type **bm remove-account -AccountName:\<account name\> -View:\<view name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1cb9a-109">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="1cb9a-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="1cb9a-110">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="1cb9a-110">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cb9a-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="1cb9a-111">See Also</span></span>  
 <span data-ttu-id="1cb9a-112">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="1cb9a-112">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 [<span data-ttu-id="1cb9a-113">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="1cb9a-113">BAM Management Utility</span></span>](../core/bam-management-utility.md)