---
title: "如何將帳戶新增至 檢視 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Excel add-in [BAM], security
- Add-Account command [BAM]
- managing [BAM], adding accounts to views
ms.assetid: 0875796c-82a4-4165-9bed-88e8ba466548
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc8d369eb24d1a239f1c305ab74230eab0f32d67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-accounts-to-a-view"></a><span data-ttu-id="e7938-102">如何新增帳戶至檢視</span><span class="sxs-lookup"><span data-stu-id="e7938-102">How to Add Accounts to a View</span></span>
<span data-ttu-id="e7938-103">系統管理員使用**新增帳戶**命令以將使用者與 BAM 檢視產生關聯，並保護 BAM Excel 試算表檢視不會未經授權的存取。</span><span class="sxs-lookup"><span data-stu-id="e7938-103">Administrators use the **add-account** command to associate users with BAM views and protect BAM Excel Spreadsheet views from unauthorized access.</span></span> <span data-ttu-id="e7938-104">當使用者儲存 BAM 檢視時，檢視會參照隱藏在活頁簿內的 SQL 連接字串。</span><span class="sxs-lookup"><span data-stu-id="e7938-104">When users save BAM views, the views reference a SQL connection string that is hidden within the workbook.</span></span> <span data-ttu-id="e7938-105">活頁簿已受到保護，但是您必須確保文件也受到保護。</span><span class="sxs-lookup"><span data-stu-id="e7938-105">The workbook is protected, but you must ensure that the document is protected.</span></span>  
  
 <span data-ttu-id="e7938-106">當使用者與 BAM 檢視產生關聯時，便只有您授與存取權限的使用者和群組，才能存取檢視。</span><span class="sxs-lookup"><span data-stu-id="e7938-106">When you associate users with BAM views, you restrict access to the views to only the users or groups to whom you grant access.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e7938-107">如果您使用即時彙總 (Rta)，使用者會新增與**新增帳戶**不會自動授與執行 SQL Server 的電腦登入權限。</span><span class="sxs-lookup"><span data-stu-id="e7938-107">If you are using real-time aggregations (RTAs), users added with **add-account** are not automatically granted logon rights to the computer running SQL Server.</span></span> <span data-ttu-id="e7938-108">如果您使用 RTA，請考慮建立一個 Windows 使用者群組，並在該群組中加入所有需要查看 RTA 檢視的使用者。</span><span class="sxs-lookup"><span data-stu-id="e7938-108">If you are using RTAs, consider establishing a Windows user group that contains all of the users that need to see views of the RTAs.</span></span> <span data-ttu-id="e7938-109">然後，將裝載 BAM 主要匯入資料庫之 SQL Server 的 SQL Server 登入權限，明確授與該群組。</span><span class="sxs-lookup"><span data-stu-id="e7938-109">Grant that group explicit SQL Server logon rights on the SQL server hosting the BAM Primary Import database.</span></span>  
  
 <span data-ttu-id="e7938-110">如需檢視 BAM 檢視的相關資訊，請參閱[如何列出 BAM 檢視](../core/how-to-list-bam-views.md)。</span><span class="sxs-lookup"><span data-stu-id="e7938-110">For information about viewing BAM views, see [How to List BAM Views](../core/how-to-list-bam-views.md).</span></span>  
  
### <a name="to-add-an-account-to-a-view"></a><span data-ttu-id="e7938-111">將帳戶新增至檢視</span><span class="sxs-lookup"><span data-stu-id="e7938-111">To add an account to a view</span></span>  
  
1.  <span data-ttu-id="e7938-112">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="e7938-112">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="e7938-113">在命令提示字元中，輸入 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking，以瀏覽至追蹤資料夾。</span><span class="sxs-lookup"><span data-stu-id="e7938-113">Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt.</span></span> <span data-ttu-id="e7938-114">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="e7938-114">Press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="e7938-115">型別**bm 新增帳戶-AccountName:\<帳戶名稱 >-檢視：\<檢視名稱 >**。</span><span class="sxs-lookup"><span data-stu-id="e7938-115">Type **bm add-account -AccountName:\<account name> -View:\<view name>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e7938-116">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="e7938-116">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="e7938-117">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="e7938-117">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7938-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7938-118">See Also</span></span>  
 <span data-ttu-id="e7938-119">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="e7938-119">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 [<span data-ttu-id="e7938-120">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="e7938-120">BAM Management Utility</span></span>](../core/bam-management-utility.md)