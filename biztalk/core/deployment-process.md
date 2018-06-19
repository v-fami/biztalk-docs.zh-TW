---
title: 部署程序 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSO, deploying
- deploying, SSO
- LogonExternalUser test [SSO]
- security, SSO
- SSO, LogonExternalUser test
- SSO, security
ms.assetid: 7dd4c022-c70b-467a-bf94-dc4ac6029f81
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21be32ec58c90c1fb95134a002bee82ef5d78fa5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240662"
---
# <a name="deployment-process"></a><span data-ttu-id="53ef9-102">部署程序</span><span class="sxs-lookup"><span data-stu-id="53ef9-102">Deployment Process</span></span>
<span data-ttu-id="53ef9-103">下列步驟提供安全部署「企業單一登入」的高層級概觀。</span><span class="sxs-lookup"><span data-stu-id="53ef9-103">The following steps give a high-level overview of secure deployment of Enterprise Single Sign-On.</span></span> <span data-ttu-id="53ef9-104">如需在 SQL Server 中執行之動作的詳細程序，請參閱您的 SQL Server 手冊。</span><span class="sxs-lookup"><span data-stu-id="53ef9-104">For detailed procedures on the actions to take in SQL Server, see your SQL Server documentation.</span></span>  
  
1.  <span data-ttu-id="53ef9-105">在 SQL Server 網域控制站，使用「新增信任精靈」建立包含以下屬性的信任：</span><span class="sxs-lookup"><span data-stu-id="53ef9-105">On the SQL Server domain controller, use the New Trust Wizard to create a trust with the following properties:</span></span>  
  
    -   <span data-ttu-id="53ef9-106">**名稱：** ORCH.com</span><span class="sxs-lookup"><span data-stu-id="53ef9-106">**Name:** ORCH.com</span></span>  
  
    -   <span data-ttu-id="53ef9-107">**方向：** 雙向</span><span class="sxs-lookup"><span data-stu-id="53ef9-107">**Direction:** Two-way</span></span>  
  
    -   <span data-ttu-id="53ef9-108">**側邊：** 僅此網域</span><span class="sxs-lookup"><span data-stu-id="53ef9-108">**Sides:** This domain only</span></span>  
  
    -   <span data-ttu-id="53ef9-109">**連出信任驗證等級-本機網域：** 選擇性驗證</span><span class="sxs-lookup"><span data-stu-id="53ef9-109">**Outgoing Trust Authentication Level - Local Domain:** Selective authentication</span></span>  
  
    -   <span data-ttu-id="53ef9-110">**密碼：** 選擇的密碼</span><span class="sxs-lookup"><span data-stu-id="53ef9-110">**Password:** Choose a password</span></span>  
  
    -   <span data-ttu-id="53ef9-111">**確認連出信任：** [是]</span><span class="sxs-lookup"><span data-stu-id="53ef9-111">**Confirm Outgoing Trust:** Yes</span></span>  
  
    -   <span data-ttu-id="53ef9-112">**確認連入信任：** 否</span><span class="sxs-lookup"><span data-stu-id="53ef9-112">**Confirm Incoming Trust:** No</span></span>  
  
2.  <span data-ttu-id="53ef9-113">在 ORCH.com 網域控制站，使用「新增信任精靈」建立包含以下屬性的信任：</span><span class="sxs-lookup"><span data-stu-id="53ef9-113">On the ORCH.com domain controller, use the New Trust Wizard to create a trust with the following properties:</span></span>  
  
    -   <span data-ttu-id="53ef9-114">**名稱：** SQL.com</span><span class="sxs-lookup"><span data-stu-id="53ef9-114">**Name:** SQL.com</span></span>  
  
    -   <span data-ttu-id="53ef9-115">**方向：** 雙向</span><span class="sxs-lookup"><span data-stu-id="53ef9-115">**Direction:** Two-way</span></span>  
  
    -   <span data-ttu-id="53ef9-116">**側邊：** 僅此網域</span><span class="sxs-lookup"><span data-stu-id="53ef9-116">**Sides:** This domain only</span></span>  
  
    -   <span data-ttu-id="53ef9-117">**連出信任驗證等級-本機網域：** 選擇性驗證</span><span class="sxs-lookup"><span data-stu-id="53ef9-117">**Outgoing Trust Authentication Level - Local Domain:** Selective authentication</span></span>  
  
    -   <span data-ttu-id="53ef9-118">**密碼：** 必須是 ORCH.com 的密碼相同</span><span class="sxs-lookup"><span data-stu-id="53ef9-118">**Password:** Must be the same as password for ORCH.com</span></span>  
  
    -   <span data-ttu-id="53ef9-119">**確認連出信任：** [是]</span><span class="sxs-lookup"><span data-stu-id="53ef9-119">**Confirm Outgoing Trust:** Yes</span></span>  
  
    -   <span data-ttu-id="53ef9-120">**確認連入信任：** 否</span><span class="sxs-lookup"><span data-stu-id="53ef9-120">**Confirm Incoming Trust:** No</span></span>  
  
3.  <span data-ttu-id="53ef9-121">在 ORCH.com 網域控制站，設定從 SQL.COM 連入的網域整體信任。</span><span class="sxs-lookup"><span data-stu-id="53ef9-121">On the ORCH.com domain controller, set the domain wide trust for Incoming from SQL.COM.</span></span>  
  
4.  <span data-ttu-id="53ef9-122">在 SQL.com 網域控制站，設定從 ORCH.COM 連出的網域整體信任。</span><span class="sxs-lookup"><span data-stu-id="53ef9-122">On the SQL.com domain controller, set the domain wide trust for Outgoing from ORCH.COM.</span></span>  
  
5.  <span data-ttu-id="53ef9-123">在 ORCH.com 網域控制站，將網域功能等級提升至 Windows Server 2008 SP2 或 Windows Server 2008 R2。</span><span class="sxs-lookup"><span data-stu-id="53ef9-123">On the ORCH.com domain controller, raise the domain functional level to Windows Server 2008 SP2 or Windows Server 2008 R2.</span></span>  
  
6.  <span data-ttu-id="53ef9-124">在 ORCH 網域，建立下列新使用者：</span><span class="sxs-lookup"><span data-stu-id="53ef9-124">In the ORCH domain, create the following new users:</span></span>  
  
    -   <span data-ttu-id="53ef9-125">ORCH\SSOSvcUser</span><span class="sxs-lookup"><span data-stu-id="53ef9-125">ORCH\SSOSvcUser</span></span>  
  
    -   <span data-ttu-id="53ef9-126">ORCH\TestAppUser</span><span class="sxs-lookup"><span data-stu-id="53ef9-126">ORCH\TestAppUser</span></span>  
  
    -   <span data-ttu-id="53ef9-127">ORCH\AffAppUser</span><span class="sxs-lookup"><span data-stu-id="53ef9-127">ORCH\AffAppUser</span></span>  
  
7.  <span data-ttu-id="53ef9-128">新增**做為作業系統的一部分**至 SSOSvcUser 和 TestAppUser。</span><span class="sxs-lookup"><span data-stu-id="53ef9-128">Add **Act as part of the operating system** to SSOSvcUser and TestAppUser.</span></span>  
  
8.  <span data-ttu-id="53ef9-129">新增**允許驗證**ORCH\TestAdmin 權限。</span><span class="sxs-lookup"><span data-stu-id="53ef9-129">Add **Allowed to Authenticate** privilege to ORCH\TestAdmin.</span></span>  
  
9. <span data-ttu-id="53ef9-130">將 ORCH\SSOSvcUser 新增至 SQL 網域的 SQL2。</span><span class="sxs-lookup"><span data-stu-id="53ef9-130">Add ORCH\SSOSvcUser to SQL2 in the SQL domain.</span></span> <span data-ttu-id="53ef9-131">(此步驟需要使用 Active Directory MMC 的「進階檢視」)。</span><span class="sxs-lookup"><span data-stu-id="53ef9-131">(This step requires using Advanced View in Active Directory MMC.)</span></span>  
  
10. <span data-ttu-id="53ef9-132">在 SQL2 電腦，建立下列兩個新登入：</span><span class="sxs-lookup"><span data-stu-id="53ef9-132">On the SQL2 computer, create the following two new logins:</span></span>  
  
    -   <span data-ttu-id="53ef9-133">ORCH\TestAdmin</span><span class="sxs-lookup"><span data-stu-id="53ef9-133">ORCH\TestAdmin</span></span>  
  
    -   <span data-ttu-id="53ef9-134">ORCH\SSOSvcUser</span><span class="sxs-lookup"><span data-stu-id="53ef9-134">ORCH\SSOSvcUser</span></span>  
  
11. <span data-ttu-id="53ef9-135">在 SQL2 網域，建立兩個網域全域群組：</span><span class="sxs-lookup"><span data-stu-id="53ef9-135">On the SQL2 domain, create two domain global groups:</span></span>  
  
    -   <span data-ttu-id="53ef9-136">ORCH\SSOAdminGroup</span><span class="sxs-lookup"><span data-stu-id="53ef9-136">ORCH\SSOAdminGroup</span></span>  
  
    -   <span data-ttu-id="53ef9-137">ORCH\SSOAffAdminGroup</span><span class="sxs-lookup"><span data-stu-id="53ef9-137">ORCH\SSOAffAdminGroup</span></span>  
  
12. <span data-ttu-id="53ef9-138">新增**允許驗證**新增至 ORCH\SSOAdminGroup 群組的權限。</span><span class="sxs-lookup"><span data-stu-id="53ef9-138">Add **Allowed to Authenticate** privilege to the ORCH\SSOAdminGroup group.</span></span>  
  
13. <span data-ttu-id="53ef9-139">在 SQL2 資料庫，建立下列新登入：</span><span class="sxs-lookup"><span data-stu-id="53ef9-139">On the SQL2 database, create the following new login:</span></span>  
  
    -   <span data-ttu-id="53ef9-140">ORCH\SSOAdminGroup</span><span class="sxs-lookup"><span data-stu-id="53ef9-140">ORCH\SSOAdminGroup</span></span>  
  
14. <span data-ttu-id="53ef9-141">按照以下步驟安裝「主要密碼伺服器」：</span><span class="sxs-lookup"><span data-stu-id="53ef9-141">Install the Master Secret Server as follows:</span></span>  
  
    -   <span data-ttu-id="53ef9-142">使用 ORCH\TestAdmin 登入 NTS5。</span><span class="sxs-lookup"><span data-stu-id="53ef9-142">Log on to NTS5 using ORCH\TestAdmin.</span></span>  
  
    -   <span data-ttu-id="53ef9-143">使用 SQL2 當成「主要密碼伺服器」來安裝 ESSO。</span><span class="sxs-lookup"><span data-stu-id="53ef9-143">Install ESSO, using SQL2 as the Master Secret Server.</span></span>  
  
15. <span data-ttu-id="53ef9-144">使用 ORCH\TestAdmin 登入 HIS1，然後安裝「企業單一登入」。</span><span class="sxs-lookup"><span data-stu-id="53ef9-144">Log onto HIS1 using ORCH\TestAdmin, and install Enterprise Single Sign-On.</span></span> <span data-ttu-id="53ef9-145">使用資料庫伺服器名稱 SQL2，將 ESSO 設定為 SSO 聯結 HIS2。</span><span class="sxs-lookup"><span data-stu-id="53ef9-145">Configure ESSO as SSO join HIS2, using database server name SQL2.</span></span>  
  
16. <span data-ttu-id="53ef9-146">使用 ORCH\TestAdmin，在 HIS3 安裝「企業單一登入管理」公用程式。</span><span class="sxs-lookup"><span data-stu-id="53ef9-146">Install the Enterprise Single Sign-On Admin utility on HIS3 using ORCH\TestAdmin.</span></span>  
  
17. <span data-ttu-id="53ef9-147">將下列使用者新增至以下群組：</span><span class="sxs-lookup"><span data-stu-id="53ef9-147">Add the following users to the following groups:</span></span>  
  
    -   <span data-ttu-id="53ef9-148">將 ORCH\TestAppUser 新增至 ORCH\SSOAdminGroup</span><span class="sxs-lookup"><span data-stu-id="53ef9-148">Add ORCH\TestAppUser to ORCH\SSOAdminGroup</span></span>  
  
    -   <span data-ttu-id="53ef9-149">將 ORCH\AffAppUser 新增至 ORCH\TestAffUserGroup</span><span class="sxs-lookup"><span data-stu-id="53ef9-149">Add ORCH\AffAppUser to ORCH\TestAffUserGroup</span></span>  
  
18. <span data-ttu-id="53ef9-150">在 HIS3 上安裝 SQL Server Enterprise Edition，然後新增登入 ORCH\AffAppUser。</span><span class="sxs-lookup"><span data-stu-id="53ef9-150">Install SQL Server Enterprise Edition on HIS3, and add login ORCH\AffAppUser.</span></span>  
  
19. <span data-ttu-id="53ef9-151">在 HIS1 電腦，開啟命令提示字元，然後使用下列命令來設定限制委派和通訊協定轉換：</span><span class="sxs-lookup"><span data-stu-id="53ef9-151">On the HIS1 computer, open a command prompt and use the following commands to set constrain delegation and protocol transition:</span></span>  
  
    -   <span data-ttu-id="53ef9-152">**setspn-A MSSQLSvc/HIS3.ORCH.com:1433 ORCH\SSOSvcUser**</span><span class="sxs-lookup"><span data-stu-id="53ef9-152">**setspn -A MSSQLSvc/HIS3.ORCH.com:1433 ORCH\SSOSvcUser**</span></span>  
  
    -   <span data-ttu-id="53ef9-153">**setspn-A MSSQLSvc/HIS3.ORCH.com:1433 ORCH\TestAppUser**</span><span class="sxs-lookup"><span data-stu-id="53ef9-153">**setspn -A MSSQLSvc/HIS3.ORCH.com:1433 ORCH\TestAppUser**</span></span>  
  
20. <span data-ttu-id="53ef9-154">在**ORCH\SSOSvcUser**和**ORCH\TestAppUser**屬性頁中，選取下列選項來設定兩個使用者帳戶的適當委派：</span><span class="sxs-lookup"><span data-stu-id="53ef9-154">On the **ORCH\SSOSvcUser** and **ORCH\TestAppUser** property pages, set the proper delegation for both user accounts by selecting the following options:</span></span>  
  
    -   <span data-ttu-id="53ef9-155">**信任這個使用者委派指定的服務**</span><span class="sxs-lookup"><span data-stu-id="53ef9-155">**Trust this user for delegation to specified services only**</span></span>  
  
    -   <span data-ttu-id="53ef9-156">**使用任何驗證通訊協定**</span><span class="sxs-lookup"><span data-stu-id="53ef9-156">**Use any authentication protocol**</span></span>  
  
21. <span data-ttu-id="53ef9-157">在 HIS1 電腦使用 ORCH\TestAdmin，執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="53ef9-157">Using ORCH\TestAdmin on the HIS1 computer, perform the following:</span></span>  
  
    -   <span data-ttu-id="53ef9-158">將 ORCH\TestAppUser 新增至「遠端桌面使用者群組」</span><span class="sxs-lookup"><span data-stu-id="53ef9-158">Add ORCH\TestAppUser to Remote Desktop User Group</span></span>  
  
    -   <span data-ttu-id="53ef9-159">授與**通過驗證後模擬**權限至 ORCH\SSOSvcUser</span><span class="sxs-lookup"><span data-stu-id="53ef9-159">Grant **Impersonate after authenticated** privilege to ORCH\SSOSvcUser</span></span>  
  
    -   <span data-ttu-id="53ef9-160">授與**通過驗證後模擬**權限至 ORCH\TestAppUser</span><span class="sxs-lookup"><span data-stu-id="53ef9-160">Grant **Impersonate after authenticated** privilege to ORCH\TestAppUser</span></span>  
  
22. <span data-ttu-id="53ef9-161">使用 ORCH\TestAppUser 並執行下列應用程式組態，以登入 HIS1 來驗證您的部署：</span><span class="sxs-lookup"><span data-stu-id="53ef9-161">Verify your deployment by logging onto HIS1 using ORCH\TestAppUser and running the following application configuration:</span></span>  
  
     <span data-ttu-id="53ef9-162">執行 LogonExternalUser 測試。</span><span class="sxs-lookup"><span data-stu-id="53ef9-162">Run LogonExternalUser Test.</span></span>  
  
    ```  
    <SSO>  
       <application name="TestApp">  
          <description>An SSO Test Affiliate Application</description>  
          <contact>AffAppUser@ESSOV2.EBiz.Com</contact>  
          <appUserAccount>ORCH\TestAffAdminGroup</appUserAccount>  
          <appAdminAccount>ORCH\TestAffUserGroup</appAdminAccount>  
          <field ordinal="0" label="User ID" masked="no" />  
          <field ordinal="1" label="Password" masked="yes" />  
          <flags   
             groupApp="no"   
             configStoreApp="no"   
             allowTickets="no"   
             validateTickets="yes"   
             allowLocalGroups="yes"   
             ticketTimeout="yes"   
             adminGroupSame="no"   
             enableApp="yes"   
             hostInitiatedSSO="yes"   
             validatePassword="yes"/>  
       </application>  
    </SSO>  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="53ef9-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53ef9-163">See Also</span></span>  
 [<span data-ttu-id="53ef9-164">SSO 部署概觀</span><span class="sxs-lookup"><span data-stu-id="53ef9-164">SSO Deployment Overview</span></span>](../core/sso-deployment-overview.md)