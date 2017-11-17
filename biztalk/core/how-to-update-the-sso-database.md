---
title: "如何更新 SSO 資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tickets [SSO], modifying
- managing [SSO], modifying Credential cache timeout
- tickets [SSO], timeouts
- modifying, SSO database
- managing [SSO], modifying ticket timeouts
- SSO database, modifying
ms.assetid: 45eb6a77-d91a-44a8-b26d-05508c288c36
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1381ee4e5c2b90a96c52b59d125ec3121af02a4e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-the-sso-database"></a><span data-ttu-id="3cdb6-102">如何更新 SSO 資料庫</span><span class="sxs-lookup"><span data-stu-id="3cdb6-102">How to Update the SSO Database</span></span>
<span data-ttu-id="3cdb6-103">使用 MMC 嵌入式管理單元或命令列，可以變更 SSO 資料庫中的全域資訊，像是主要密碼伺服器識別碼、帳戶名稱、資料庫中的稽核、票證逾時以及認證快取逾時。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-103">You can change the global information in the SSO database, such as the master secret server identification, the account names, auditing in the database, ticket timeout, and credential cache timeout, by using either the MMC Snap-In or the command line.</span></span>  
  
## <a name="changing-timeouts-for-the-sso-system"></a><span data-ttu-id="3cdb6-104">變更 SSO 系統的逾時</span><span class="sxs-lookup"><span data-stu-id="3cdb6-104">Changing timeouts for the SSO System</span></span>  
 <span data-ttu-id="3cdb6-105">您可以修改「企業單一登入」(SSO) 系統層級上的兩個逾時：</span><span class="sxs-lookup"><span data-stu-id="3cdb6-105">You can modify two timeouts at the Enterprise Single Sign-On (SSO) system level:</span></span>  
  
 <span data-ttu-id="3cdb6-106">**票證逾時。**</span><span class="sxs-lookup"><span data-stu-id="3cdb6-106">**Ticket timeout.**</span></span> <span data-ttu-id="3cdb6-107">。此屬性指定 SSO 核發之票證的有效時間長度。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-107">This property specifies the length of time for which a ticket SSO issues is valid.</span></span> <span data-ttu-id="3cdb6-108">為了滿足使用 SSO 的企業中大部分實例，預設的票證逾時為 2 分鐘。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-108">To satisfy most of the scenarios in an enterprise that use SSO, the default ticket timeout is 2 minutes.</span></span> <span data-ttu-id="3cdb6-109">SSO 系統管理員可以根據應用程式需求變更此值。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-109">The SSO administrator can change this based on the application requirements.</span></span>  
  
 <span data-ttu-id="3cdb6-110">**認證快取逾時。**</span><span class="sxs-lookup"><span data-stu-id="3cdb6-110">**Credential Cache timeout.**</span></span> <span data-ttu-id="3cdb6-111">。此屬性指定所有 SSO 伺服器的認證快取逾時。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-111">This property specifies the credential cache timeout for all SSO Servers.</span></span> <span data-ttu-id="3cdb6-112">SSO 伺服器在第一次尋查之後會快取認證。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-112">SSO Servers cache the credentials after the first lookup.</span></span> <span data-ttu-id="3cdb6-113">依照預設，認證快取逾時為 60 分鐘。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-113">By default, the credential cache timeout is 60 minutes.</span></span> <span data-ttu-id="3cdb6-114">SSO 系統管理員可以根據安全性需求，將此變更為適當的值。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-114">The SSO administrator can change this to a suitable value based on the security requirements.</span></span>  
  
 <span data-ttu-id="3cdb6-115">更新 SSO 資料庫即可變更這兩種逾時。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-115">You change both of these timeouts by updating the SSO database.</span></span>  
  
 <span data-ttu-id="3cdb6-116">更新 SSO 資料庫的範例 XML 檔案為：</span><span class="sxs-lookup"><span data-stu-id="3cdb6-116">A sample XML file for updating the SSO database is:</span></span>  
  
```  
<sso>  
<globalInfo>  
<ssoAdminAccount>Domain\Accountname</ssoAdminAccount>  
<ssoAffiliateAdminAccount>Domain\Accountname</ssoAffiliateAdminAccount>  
<secretServer>ComputerA</secretServer>  
<auditDeletedApps>1000</auditDeletedApps>  
<auditDeletedMappings>1000</auditDeletedMappings>  
<auditCredentialLookups>1000</auditCredentialLookups>  
<ticketTimeout>2</ticketTimeout>  
<credCacheTimeout>60</credCacheTimeout>  
</globalInfo>  
</sso>  
  
```  
  
#### <a name="to-change-timeouts-using-the-mmc-snap-in"></a><span data-ttu-id="3cdb6-117">使用 MMC 嵌入式管理單元變更逾時</span><span class="sxs-lookup"><span data-stu-id="3cdb6-117">To change timeouts using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="3cdb6-118">在 **[開始]** 功能表上，依序按一下 **[所有程式]**及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-118">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="3cdb6-119">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-119">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="3cdb6-120">使用滑鼠右鍵按一下 **[系統]**，然後按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-120">Right-click **System**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="3cdb6-121">在 [SSO 系統屬性]  對話方塊中，按一下 [一般]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-121">On the **System Properties** dialog box, click the **General** tab.</span></span>  
  
5.  <span data-ttu-id="3cdb6-122">輸入適當的設定，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-122">Enter the appropriate settings, and click **OK**.</span></span>  
  
#### <a name="to-update-the-sso-database-using-the-mmc-snap-in"></a><span data-ttu-id="3cdb6-123">若要使用 MMC 嵌入式管理單元更新 SSO 資料庫</span><span class="sxs-lookup"><span data-stu-id="3cdb6-123">To update the SSO database using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="3cdb6-124">在 **[開始]** 功能表上，依序按一下 **[所有程式]**及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-124">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="3cdb6-125">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-125">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="3cdb6-126">在 [系統] 上按一下滑鼠右鍵，然後按一下 [升級資料庫] 。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-126">Right-click **System**, and then click **Upgrade Database**.</span></span>  
  
#### <a name="to-update-the-sso-database-using-the-command-line"></a><span data-ttu-id="3cdb6-127">使用命令列更新 SSO 資料庫</span><span class="sxs-lookup"><span data-stu-id="3cdb6-127">To update the SSO database using the command line</span></span>  
  
1.  <span data-ttu-id="3cdb6-128">依序按一下 **[開始]**及 **[執行]**，然後輸入 **cmd**。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-128">Click **Start**, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="3cdb6-129">在命令列提示字元中，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-129">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="3cdb6-130">預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-130">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="3cdb6-131">型別**ssomanage – updatedb\<更新檔案 >**，其中**\<更新檔案 >**路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-131">Type **ssomanage –updatedb \<update file>**, where **\<update file>** is the path and name of the file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3cdb6-132">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="3cdb6-132">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cdb6-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cdb6-133">See Also</span></span>  
 <span data-ttu-id="3cdb6-134">[如何設定 SSO 票證](../core/how-to-configure-the-sso-tickets.md) </span><span class="sxs-lookup"><span data-stu-id="3cdb6-134">[How to Configure the SSO Tickets](../core/how-to-configure-the-sso-tickets.md) </span></span>  
 [<span data-ttu-id="3cdb6-135">使用 SSO</span><span class="sxs-lookup"><span data-stu-id="3cdb6-135">Using SSO</span></span>](../core/using-sso.md)