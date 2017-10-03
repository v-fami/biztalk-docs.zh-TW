---
title: "如何顯示 SSO 資料庫資訊 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO], viewing SSO database
- SSO database, viewing
- viewing, SSO database
ms.assetid: 0ebadd2e-6ea5-460c-b0a8-f48589e6bf1c
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1328e6066af0d19c68657728f8dc7777ba62f12d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-display-the-sso-database-information"></a><span data-ttu-id="cd709-102">如何顯示 SSO 資料庫資訊</span><span class="sxs-lookup"><span data-stu-id="cd709-102">How to Display the SSO Database Information</span></span>
<span data-ttu-id="cd709-103">您可以使用 MMC 嵌入式管理單元或是命令列 (ssomanage) 公用程式，以檢視 SSO 資料庫資訊。</span><span class="sxs-lookup"><span data-stu-id="cd709-103">You can view SSO database information by using the MMC Snap-In or the command line (ssomanage) utility.</span></span>  
  
### <a name="to-display-the-sso-database-information-using-the-mmc-snap-in"></a><span data-ttu-id="cd709-104">若要使用 MMC 嵌入式管理單元顯示 SSO 資料庫資訊</span><span class="sxs-lookup"><span data-stu-id="cd709-104">To display the SSO database information using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="cd709-105">在 **[開始]** 功能表上，依序按一下 **[所有程式]**及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。</span><span class="sxs-lookup"><span data-stu-id="cd709-105">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="cd709-106">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="cd709-106">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="cd709-107">使用滑鼠右鍵按一下 **[系統]**，然後按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="cd709-107">Right-click **System**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="cd709-108">按一下索引標籤上**系統屬性**對話方塊以檢視 SSO 資料庫資訊。</span><span class="sxs-lookup"><span data-stu-id="cd709-108">Click the tabs on the  **System Properties** dialog box to view SSO database information.</span></span>  
  
### <a name="to-display-the-sso-database-information-using-the-command-line"></a><span data-ttu-id="cd709-109">使用命令列顯示 SSO 資料庫資訊</span><span class="sxs-lookup"><span data-stu-id="cd709-109">To display the SSO database information using the command line</span></span>  
  
1.  <span data-ttu-id="cd709-110">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="cd709-110">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="cd709-111">在命令列提示字元中，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="cd709-111">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="cd709-112">預設安裝目錄是**\<磁碟機 >**: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="cd709-112">The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="cd709-113">型別**ssomanage – displaydb**。</span><span class="sxs-lookup"><span data-stu-id="cd709-113">Type **ssomanage –displaydb**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cd709-114">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="cd709-114">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-display-the-sso-database-the-sso-server-is-connected-to-using-the-command-line"></a><span data-ttu-id="cd709-115">使用命令列顯示 SSO 伺服器連接的 SSO 資料庫</span><span class="sxs-lookup"><span data-stu-id="cd709-115">To display the SSO database the SSO Server is connected to using the command line</span></span>  
  
1.  <span data-ttu-id="cd709-116">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="cd709-116">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="cd709-117">在命令列提示字元中，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="cd709-117">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="cd709-118">預設安裝目錄是**\<磁碟機 >**: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="cd709-118">The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="cd709-119">型別**ssomanage – showdb**。</span><span class="sxs-lookup"><span data-stu-id="cd709-119">Type **ssomanage –showdb**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cd709-120">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="cd709-120">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
 <span data-ttu-id="cd709-121">下表說明這些程序顯示的值。</span><span class="sxs-lookup"><span data-stu-id="cd709-121">The following table describes the values displayed by these procedures.</span></span>  
  
|<span data-ttu-id="cd709-122">屬性</span><span class="sxs-lookup"><span data-stu-id="cd709-122">Property</span></span>|<span data-ttu-id="cd709-123">值</span><span class="sxs-lookup"><span data-stu-id="cd709-123">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="cd709-124">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cd709-124">SQL Server</span></span>|<span data-ttu-id="cd709-125">**\<SQL Server 名稱 >**</span><span class="sxs-lookup"><span data-stu-id="cd709-125">**\<SQL Server name>**</span></span>|  
|<span data-ttu-id="cd709-126">單一登入資料庫</span><span class="sxs-lookup"><span data-stu-id="cd709-126">Single Sign-On database</span></span>|<span data-ttu-id="cd709-127">**\<SQL Server 資料庫名稱 >**</span><span class="sxs-lookup"><span data-stu-id="cd709-127">**\<SQL Server database name>**</span></span>|  
|<span data-ttu-id="cd709-128">單一登入密碼伺服器名稱</span><span class="sxs-lookup"><span data-stu-id="cd709-128">Single Sign-On Secret Server name</span></span>|<span data-ttu-id="cd709-129">**\<單一登入伺服器名稱 >**</span><span class="sxs-lookup"><span data-stu-id="cd709-129">**\<Single Sign-On Server name>**</span></span>|  
|<span data-ttu-id="cd709-130">單一登入系統管理員帳戶</span><span class="sxs-lookup"><span data-stu-id="cd709-130">Single Sign-On Administrators account</span></span>|<span data-ttu-id="cd709-131">網域\帳戶名稱</span><span class="sxs-lookup"><span data-stu-id="cd709-131">Domain\account name</span></span>|  
|<span data-ttu-id="cd709-132">單一登入分支機構系統管理員帳戶</span><span class="sxs-lookup"><span data-stu-id="cd709-132">Single Sign-On Affiliate Administrators account</span></span>|<span data-ttu-id="cd709-133">網域\帳戶名稱</span><span class="sxs-lookup"><span data-stu-id="cd709-133">Domain\account name</span></span>|  
|<span data-ttu-id="cd709-134">已刪除應用程式的稽核表格大小 (稽核項目的數目)</span><span class="sxs-lookup"><span data-stu-id="cd709-134">Size of audit table for deleted applications (number of audit entries)</span></span>|<span data-ttu-id="cd709-135">1000 （預設值）</span><span class="sxs-lookup"><span data-stu-id="cd709-135">1,000 (default)</span></span>|  
|<span data-ttu-id="cd709-136">已刪除使用者對應的稽核表格大小 (稽核項目的數目)</span><span class="sxs-lookup"><span data-stu-id="cd709-136">Size of audit table for deleted user mappings (number of audit entries)</span></span>|<span data-ttu-id="cd709-137">1000 （預設值）</span><span class="sxs-lookup"><span data-stu-id="cd709-137">1,000 (default)</span></span>|  
|<span data-ttu-id="cd709-138">外部認證查詢的稽核表格大小 (稽核項目的數目)</span><span class="sxs-lookup"><span data-stu-id="cd709-138">Size of audit table for external credential lookups (number of audit entries)</span></span>|<span data-ttu-id="cd709-139">1000 （預設值）</span><span class="sxs-lookup"><span data-stu-id="cd709-139">1,000 (default)</span></span>|  
|<span data-ttu-id="cd709-140">票證逾時 (分鐘)</span><span class="sxs-lookup"><span data-stu-id="cd709-140">Ticket timeout (in minutes)</span></span>|<span data-ttu-id="cd709-141">2 （預設值）</span><span class="sxs-lookup"><span data-stu-id="cd709-141">2 (default)</span></span><br /><br /> <span data-ttu-id="cd709-142">這個值可以是 1 到 525,600 的整數</span><span class="sxs-lookup"><span data-stu-id="cd709-142">This value can be an integer from1 through 525,600</span></span>|  
|<span data-ttu-id="cd709-143">認證快取逾時 (分鐘)</span><span class="sxs-lookup"><span data-stu-id="cd709-143">Credential cache timeout (in minutes)</span></span>|<span data-ttu-id="cd709-144">60 （預設值）</span><span class="sxs-lookup"><span data-stu-id="cd709-144">60 (default)</span></span>|  
|<span data-ttu-id="cd709-145">單一登入狀態</span><span class="sxs-lookup"><span data-stu-id="cd709-145">Single Sign-On Status</span></span>|<span data-ttu-id="cd709-146">已啟用/已停用</span><span class="sxs-lookup"><span data-stu-id="cd709-146">Enabled/disabled</span></span>|  
|<span data-ttu-id="cd709-147">允許票證</span><span class="sxs-lookup"><span data-stu-id="cd709-147">Tickets allowed</span></span>|<span data-ttu-id="cd709-148">是/否 (預設值)</span><span class="sxs-lookup"><span data-stu-id="cd709-148">Yes/no (default)</span></span>|  
|<span data-ttu-id="cd709-149">驗證票證</span><span class="sxs-lookup"><span data-stu-id="cd709-149">Validate tickets</span></span>|<span data-ttu-id="cd709-150">是 (預設值)/否</span><span class="sxs-lookup"><span data-stu-id="cd709-150">Yes (default)/no</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd709-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd709-151">See Also</span></span>  
 <span data-ttu-id="cd709-152">[如何設定 SSO 票證](../core/how-to-configure-the-sso-tickets.md) </span><span class="sxs-lookup"><span data-stu-id="cd709-152">[How to Configure the SSO Tickets](../core/how-to-configure-the-sso-tickets.md) </span></span>  
 [<span data-ttu-id="cd709-153">使用 SSO</span><span class="sxs-lookup"><span data-stu-id="cd709-153">Using SSO</span></span>](../core/using-sso.md)