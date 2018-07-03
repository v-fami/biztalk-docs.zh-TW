---
title: 如何從檢視移除帳戶 |Microsoft Docs
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
ms.openlocfilehash: 243c7ee549aea06acb199f718c6eef55e578f91f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995391"
---
# <a name="how-to-remove-accounts-from-a-view"></a><span data-ttu-id="18a35-102">如何從檢視移除帳戶</span><span class="sxs-lookup"><span data-stu-id="18a35-102">How to Remove Accounts from a View</span></span>
<span data-ttu-id="18a35-103">系統管理員可以使用**移除帳戶**命令來移除 BAM 檢視中的使用者，並保護 BAM Excel 試算表檢視未經授權的存取。</span><span class="sxs-lookup"><span data-stu-id="18a35-103">Administrators use the **remove-account** command to remove users from BAM views and protect BAM Excel Spreadsheet views from unauthorized access.</span></span>  
  
 <span data-ttu-id="18a35-104">如需檢視 BAM 檢視的資訊，請參閱[如何列出 BAM 檢視](../core/how-to-list-bam-views.md)。</span><span class="sxs-lookup"><span data-stu-id="18a35-104">For information about viewing BAM views, see [How to List BAM Views](../core/how-to-list-bam-views.md).</span></span>  
  
### <a name="to-remove-an-account-from-a-view"></a><span data-ttu-id="18a35-105">從檢視移除帳戶</span><span class="sxs-lookup"><span data-stu-id="18a35-105">To remove an account from a view</span></span>  
  
1. <span data-ttu-id="18a35-106">開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="18a35-106">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="18a35-107">瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]追蹤</span><span class="sxs-lookup"><span data-stu-id="18a35-107">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking</span></span>  
  
3. <span data-ttu-id="18a35-108">型別**bm 移除帳戶-AccountName:\<帳戶名稱\>-檢視：\<檢視表名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="18a35-108">Type **bm remove-account -AccountName:\<account name\> -View:\<view name\>**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="18a35-109">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="18a35-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4. <span data-ttu-id="18a35-110">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="18a35-110">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18a35-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18a35-111">See Also</span></span>  
 <span data-ttu-id="18a35-112">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="18a35-112">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 [<span data-ttu-id="18a35-113">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="18a35-113">BAM Management Utility</span></span>](../core/bam-management-utility.md)