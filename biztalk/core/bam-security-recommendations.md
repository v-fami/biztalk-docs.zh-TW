---
title: "BAM 安全性建議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, BAM
- managing [BAM], security
- BAM, security
ms.assetid: 73613123-c1ed-477a-9f5c-342b2573c975
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f26cd3051dd296cc2849cb9c8ba7f8aa1d7ac6a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bam-security-recommendations"></a><span data-ttu-id="6c312-102">BAM 安全性建議</span><span class="sxs-lookup"><span data-stu-id="6c312-102">BAM Security Recommendations</span></span>
<span data-ttu-id="6c312-103">建議您依照下列則保護與部署您環境中的 BAM：</span><span class="sxs-lookup"><span data-stu-id="6c312-103">We recommend that you follow these guidelines for securing and deploying BAM in your environment:</span></span>  
  
-   <span data-ttu-id="6c312-104">如果您使用 [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)]，管理電腦必須安裝下列軟體才能部署 BAM：</span><span class="sxs-lookup"><span data-stu-id="6c312-104">If you are using [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)], the administration computer must have the following software installed to deploy BAM:</span></span>  
  
    -   [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)]  
  
    -   [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)]<span data-ttu-id="6c312-105"> 用戶端工具</span><span class="sxs-lookup"><span data-stu-id="6c312-105"> client tools</span></span>  
  
    -   [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)]<span data-ttu-id="6c312-106">Integration Services</span><span class="sxs-lookup"><span data-stu-id="6c312-106"> Integration Services</span></span>  
  
    -   [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)]<span data-ttu-id="6c312-107"> Analysis Services</span><span class="sxs-lookup"><span data-stu-id="6c312-107"> Analysis Services</span></span>  
  
    -   [!INCLUDE[SQLServer2005_SP3_long](../includes/sqlserver2005-sp3-long-md.md)]<span data-ttu-id="6c312-108"> (如果您要使用 BAM 警示)</span><span class="sxs-lookup"><span data-stu-id="6c312-108">, if you will be using BAM alerts</span></span>  
  
        > [!NOTE]
        >  [!INCLUDE[SQLServer2005_SP3_short](../includes/sqlserver2005-sp3-short-md.md)]<span data-ttu-id="6c312-109"> 含有 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 適用的 [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)] Notification Services。</span><span class="sxs-lookup"><span data-stu-id="6c312-109"> contains [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Notification Services for [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c312-110">執行分析 DTS 封裝的使用者內容，必須是 BAM 主要匯入資料庫和 BAM 星狀結構描述資料庫 db_owner [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 角色的成員。</span><span class="sxs-lookup"><span data-stu-id="6c312-110">The user context under which the analysis DTS package runs must be a member of the db_owner [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] role of the BAM Primary Import and BAM Star Schema databases.</span></span> <span data-ttu-id="6c312-111">此外，執行 Analysis Services 的服務帳戶必須是 OLAP 系統管理員，且必須是 BAM 星狀結構描述資料庫的 db_owner。</span><span class="sxs-lookup"><span data-stu-id="6c312-111">In addition, the service account under which Analysis Services runs must be an OLAP administrator and must be a db_owner of the BAM Star Schema database.</span></span> <span data-ttu-id="6c312-112">如需詳細資訊，請參閱 「 Microsoft 說明及支援 」 網站，網址[http://go.microsoft.com/fwlink/?LinkId=22781](http://go.microsoft.com/fwlink/?LinkId=22781)。</span><span class="sxs-lookup"><span data-stu-id="6c312-112">For more information, see the Microsoft Help and Support Web site at [http://go.microsoft.com/fwlink/?LinkId=22781](http://go.microsoft.com/fwlink/?LinkId=22781).</span></span>  
  
-   <span data-ttu-id="6c312-113">多個使用者需要存取即時和封存資料： 銷售人員、 商務經理人，以及其他等等。</span><span class="sxs-lookup"><span data-stu-id="6c312-113">Multiple users need access to the live and archived data: salespeople, business managers, and others.</span></span> <span data-ttu-id="6c312-114">這些使用者必須擁有 BAM 主要匯入資料庫與 BAM 分析資料庫所在網域 (企業網域) 的網域帳戶，但是他們的帳戶不需具備存取 BizTalk 資源的權限。</span><span class="sxs-lookup"><span data-stu-id="6c312-114">These users must have domain accounts in the domain where the BAM Primary Import and BAM Analysis databases are (corporate domain), but their accounts do not need to have access to BizTalk resources.</span></span>  
  
-   <span data-ttu-id="6c312-115">若要讓使用者能夠存取 BAM 資料的檢視，您必須使用 BAM 管理公用程式 (BM.exe) 授與使用者檢視的權限，並且使用者必須擁有 SQL 登入權限。</span><span class="sxs-lookup"><span data-stu-id="6c312-115">For users to access views of the BAM data, you must use the BAM management utility (BM.exe) to grant the users permissions to the views, and the users must have SQL logins.</span></span> <span data-ttu-id="6c312-116">如需 BAM 管理公用程式的詳細資訊，請參閱[BAM 管理公用程式](../core/bam-management-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="6c312-116">For more information about the BAM management utility, see [BAM Management Utility](../core/bam-management-utility.md).</span></span>  
  
-   <span data-ttu-id="6c312-117">若要將使用者新增至具有 BAM 分析資料庫中 Cube 存取權限的角色，您必須擁有位於與 BAM 資料庫相同網域的管理電腦。</span><span class="sxs-lookup"><span data-stu-id="6c312-117">To add users to roles that have access to the cubes in the BAM Analysis database, you must have an administration computer in the same domain as the BAM databases.</span></span>  
  
-   <span data-ttu-id="6c312-118">管理 BAM 的人員必須是 BAM 主要匯入資料庫、星狀結構描述資料庫以及 BAM 封存資料庫的 db_owner，</span><span class="sxs-lookup"><span data-stu-id="6c312-118">The person administering BAM must be db_owner for the BAM Primary Import, Star Schema, and BAM Archive databases.</span></span> <span data-ttu-id="6c312-119">該人員同時必須是 BAM 分析資料庫的 OLAP 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="6c312-119">That person must also be an OLAP administrator for the BAM Analysis database.</span></span>  
  
-   <span data-ttu-id="6c312-120">如果您正在部署 Microsoft Office Excel 活頁簿 (.xls 檔案)，Excel 必須安裝於管理電腦上。</span><span class="sxs-lookup"><span data-stu-id="6c312-120">If you are deploying Microsoft Office Excel workbooks (.xls files), Excel must be installed on the administration computer.</span></span> <span data-ttu-id="6c312-121">在部署活頁簿之前，請先開啟活頁簿，確定巨集安全性設定為「高」，而且沒有出現任何警告。</span><span class="sxs-lookup"><span data-stu-id="6c312-121">Before you deploy a workbook, open it and ensure that the macro security is set to high, and that there are no warnings.</span></span>  
  
-   <span data-ttu-id="6c312-122">如果沒有任何商務需要傳遞給連接實際資料的使用者 BAM Excel 活頁簿，建議您使用 XML 檔案部署活頁簿。</span><span class="sxs-lookup"><span data-stu-id="6c312-122">If there is no business need to distribute to the users BAM Excel workbooks that connect to the real data, we recommend that you deploy the workbooks by using XML files.</span></span> <span data-ttu-id="6c312-123">這樣就不需要在管理電腦上安裝 Excel 和需要檢查巨集安全性層級。</span><span class="sxs-lookup"><span data-stu-id="6c312-123">This eliminates the need to install Excel on the administration computer, and the need to verify the macro security level.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="6c312-124">當您移除使用者的檢視權限時，也必須記得刪除使用者設定的任何警示訂閱。</span><span class="sxs-lookup"><span data-stu-id="6c312-124">When you remove a user's permissions on a view, you must also remember to eliminate any subscriptions to alerts that the user has set.</span></span> <span data-ttu-id="6c312-125">如需有關如何從警示移除訂閱者的詳細資訊，請參閱[如何從警示移除訂閱者](../core/how-to-remove-subscribers-from-an-alert.md)。</span><span class="sxs-lookup"><span data-stu-id="6c312-125">For more information about removing subscribers from an alert, see [How to Remove Subscribers from an Alert](../core/how-to-remove-subscribers-from-an-alert.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c312-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c312-126">See Also</span></span>  
 <span data-ttu-id="6c312-127">[最低安全性使用者權限](../core/minimum-security-user-rights.md) </span><span class="sxs-lookup"><span data-stu-id="6c312-127">[Minimum Security User Rights](../core/minimum-security-user-rights.md) </span></span>  
 [<span data-ttu-id="6c312-128">BizTalk Server 部署的安全性建議</span><span class="sxs-lookup"><span data-stu-id="6c312-128">Security Recommendations for a BizTalk Server Deployment</span></span>](../core/security-recommendations-for-a-biztalk-server-deployment.md)