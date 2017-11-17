---
title: "如何稽核 SSO |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO], auditing
- SSO, auditing
- auditing [SSO]
- SSO database, auditing
ms.assetid: dc6d0726-fc31-4af2-9a23-8df9e3fc5836
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: abea3028c2ec9fd2131b8fd17247476b6fdfa6f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-audit-sso"></a><span data-ttu-id="0eac7-102">如何稽核 SSO</span><span class="sxs-lookup"><span data-stu-id="0eac7-102">How to Audit SSO</span></span>
<span data-ttu-id="0eac7-103">您可以使用 MMC 嵌入式管理單元或命令列，以設定正負兩種稽核層次。</span><span class="sxs-lookup"><span data-stu-id="0eac7-103">You can use the MMC Snap-In or the command line to set both the positive and negative auditing levels.</span></span> <span data-ttu-id="0eac7-104">稽核的結果會儲存在資料庫的事件日誌和稽核日誌。</span><span class="sxs-lookup"><span data-stu-id="0eac7-104">Results of the auditing are stored in both the event logs and the audit logs of the database.</span></span>  
  
 <span data-ttu-id="0eac7-105">SSO 系統管理員可設定符合公司政策的正面和負面稽核層級。</span><span class="sxs-lookup"><span data-stu-id="0eac7-105">SSO administrators can set the positive and negative audit levels that suit their corporate policies.</span></span> <span data-ttu-id="0eac7-106">您可以在下列層級的其中一個設定正面和負面稽核：</span><span class="sxs-lookup"><span data-stu-id="0eac7-106">You can set positive and negative audits to one of the following levels:</span></span>  
  
 <span data-ttu-id="0eac7-107">0 = 無</span><span class="sxs-lookup"><span data-stu-id="0eac7-107">0 = None</span></span>  
  
 <span data-ttu-id="0eac7-108">1 = 低</span><span class="sxs-lookup"><span data-stu-id="0eac7-108">1 = Low</span></span>  
  
 <span data-ttu-id="0eac7-109">2 = 中</span><span class="sxs-lookup"><span data-stu-id="0eac7-109">2 = Medium</span></span>  
  
 <span data-ttu-id="0eac7-110">3 = 高。</span><span class="sxs-lookup"><span data-stu-id="0eac7-110">3 = High.</span></span> <span data-ttu-id="0eac7-111">此層級會儘可能發出最多的稽核訊息。</span><span class="sxs-lookup"><span data-stu-id="0eac7-111">This level issues as many audit messages as possible.</span></span>  
  
 <span data-ttu-id="0eac7-112">正面稽核的預設值是 0 (無)，負面稽核的預設值是 1 (低)。</span><span class="sxs-lookup"><span data-stu-id="0eac7-112">The default value for positive auditing is 0 (none), and the default value for negative auditing is 1(low).</span></span>  
  
 <span data-ttu-id="0eac7-113">若要變更資料庫稽核層次，必須使用 XML 檔案更新 SSO 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0eac7-113">To change the database level auditing, you must update the SSO database using an XML file.</span></span> <span data-ttu-id="0eac7-114">更新 SSO 資料庫的範例 XML 檔案為：</span><span class="sxs-lookup"><span data-stu-id="0eac7-114">A sample XML file for updating the SSO database is:</span></span>  
  
```  
<sso>  
<globalnfo>  
<auditDeletedApps>1000</auditDeletedApps>  
<auditDeletedMappings>1000</auditDeletedMappings>  
<auditCredentialLookups>1000</auditCredentialLookups>  
</globalInfo>  
</sso>  
  
```  
  
### <a name="to-audit-single-sign-on-using-the-mmc-snap-in"></a><span data-ttu-id="0eac7-115">使用 MMC 嵌入式管理單元稽核單一登入</span><span class="sxs-lookup"><span data-stu-id="0eac7-115">To audit Single Sign-On using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="0eac7-116">在 **[開始]** 功能表上，依序按一下 **[所有程式]**及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。</span><span class="sxs-lookup"><span data-stu-id="0eac7-116">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="0eac7-117">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="0eac7-117">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="0eac7-118">使用滑鼠右鍵按一下 **[系統]**，然後按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="0eac7-118">Right-click **System**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="0eac7-119">在**系統屬性**對話方塊中，按一下 [**稽核**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0eac7-119">On the  **System Properties** dialog box, click the **Audits** tab.</span></span>  
  
5.  <span data-ttu-id="0eac7-120">輸入適當的設定，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="0eac7-120">Enter the appropriate settings, and click **OK**.</span></span>  
  
### <a name="to-audit-single-sign-on-using-the-command-line"></a><span data-ttu-id="0eac7-121">若要稽核單一登入使用命令列</span><span class="sxs-lookup"><span data-stu-id="0eac7-121">To audit Single Sign-On using the command line</span></span>  
  
1.  <span data-ttu-id="0eac7-122">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="0eac7-122">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="0eac7-123">在命令列提示字元中，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="0eac7-123">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="0eac7-124">預設安裝目錄是**\<磁碟機 >**: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="0eac7-124">The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="0eac7-125">型別**ssoconfig – auditlevel\<正數 >\<負 >**，其中**\<正數 >**是層級的稽核動作成功時, 和**\<負 >**是動作失敗時的稽核層級。</span><span class="sxs-lookup"><span data-stu-id="0eac7-125">Type **ssoconfig –auditlevel \<positive>\<negative>**, where **\<positive>** is the level of auditing when actions succeed, and **\<negative>** is the level of auditing when actions fail.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0eac7-126">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="0eac7-126">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-audit-the-sso-database"></a><span data-ttu-id="0eac7-127">稽核 SSO 資料庫</span><span class="sxs-lookup"><span data-stu-id="0eac7-127">To audit the SSO database</span></span>  
  
1.  <span data-ttu-id="0eac7-128">依序按一下 **[開始]**及 **[執行]**，然後輸入 **cmd**。</span><span class="sxs-lookup"><span data-stu-id="0eac7-128">Click **Start**, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="0eac7-129">在命令列提示字元中，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="0eac7-129">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="0eac7-130">預設安裝目錄是**\<磁碟機 >**: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="0eac7-130">The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="0eac7-131">型別**ssomanage – updatedb\<更新檔案 >**，其中**\<更新檔案 >**路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="0eac7-131">Type **ssomanage –updatedb \<update file>**, where **\<update file>**is the path and name of the file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0eac7-132">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="0eac7-132">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eac7-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0eac7-133">See Also</span></span>  
 <span data-ttu-id="0eac7-134">[如何更新 SSO 資料庫](../core/how-to-update-the-sso-database.md) </span><span class="sxs-lookup"><span data-stu-id="0eac7-134">[How to Update the SSO Database](../core/how-to-update-the-sso-database.md) </span></span>  
 [<span data-ttu-id="0eac7-135">使用 SSO</span><span class="sxs-lookup"><span data-stu-id="0eac7-135">Using SSO</span></span>](../core/using-sso.md)