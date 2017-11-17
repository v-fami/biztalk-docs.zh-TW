---
title: "如何變更主要密碼伺服器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Master Secret server, promoting
- managing [Master Secret server], promoting servers
- managing [SSO], promoting servers
- SSO, Master Secret server
- modifying, Master Secret server
- Master Secret server, changing
ms.assetid: 44a786ca-4645-44a8-b33e-d0019f0aeca9
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4676db07025b4395d58df7c24252769ba65ecfb4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-change-the-master-secret-server"></a><span data-ttu-id="6ae18-102">如何變更主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="6ae18-102">How to Change the Master Secret Server</span></span>
<span data-ttu-id="6ae18-103">在您安裝主要密碼伺服器並設定 SSO 資料庫之後，若原始主要密碼伺服器故障且無法復原，則可以變更主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="6ae18-103">After you set up the master secret server and configure the SSO database, you can change the master secret server if the original master secret server fails and cannot be recovered.</span></span> <span data-ttu-id="6ae18-104">若要變更主要密碼伺服器，您必須將 SSO 伺服器升級為主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="6ae18-104">To change the master secret server, you need to promote an SSO server to become the master secret server.</span></span>  
  
### <a name="to-change-the-master-secret-server-using-the-mmc-snap-in"></a><span data-ttu-id="6ae18-105">使用 MMC 嵌入式管理單元變更主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="6ae18-105">To change the Master Secret Server using the MMC Snap-in</span></span>  
  
1.  <span data-ttu-id="6ae18-106">在 **[開始]** 功能表上，依序按一下 **[所有程式]**及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。</span><span class="sxs-lookup"><span data-stu-id="6ae18-106">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="6ae18-107">在 領域 窗格中，以滑鼠右鍵按一下**系統**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="6ae18-107">In the scope pane, right click **System**, and then click **Properties**.</span></span> <span data-ttu-id="6ae18-108">主要密碼伺服器會顯示在**一般** 索引標籤**系統屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6ae18-108">The Master secret server is displayed on the **General** tab of the **System Properties** dialog box.</span></span>  
  
3.  <span data-ttu-id="6ae18-109">按一下**變更**選取新的主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="6ae18-109">Click **Change** to select a new Master secret server.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="6ae18-110">當使用 MMC 嵌入式管理單元變更主要密碼伺服器時，必須在主要密碼伺服器上執行作業。</span><span class="sxs-lookup"><span data-stu-id="6ae18-110">When using the MMC Snap-in to change the Master Secret Server, the operation must be performed on the Master Secret Server.</span></span> <span data-ttu-id="6ae18-111">不可能使用非主要密碼伺服器之電腦中的 MMC 嵌入式管理單元來變更主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="6ae18-111">It is not possible to change the Master Secret Server using the MMC Snap-in from a computer that is not the Master Secret Server.</span></span>  
  
4.  <span data-ttu-id="6ae18-112">登入新的主要密碼伺服器，以還原新主要密碼伺服器之登錄的主要密碼。</span><span class="sxs-lookup"><span data-stu-id="6ae18-112">Logon to the new Master secret server to restore the Master secret to the registry of the new Master secret server.</span></span>  
  
5.  <span data-ttu-id="6ae18-113">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="6ae18-113">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
6.  <span data-ttu-id="6ae18-114">在命令列提示字元中，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="6ae18-114">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="6ae18-115">預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="6ae18-115">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
7.  <span data-ttu-id="6ae18-116">重新啟動新的主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="6ae18-116">Restart the new Master Secret Server.</span></span>  
  
8.  <span data-ttu-id="6ae18-117">型別**ssoconfig – restoreSecret\<還原檔案 >**，其中**\<還原檔案 >**是儲存主要密碼的檔案名稱與路徑。</span><span class="sxs-lookup"><span data-stu-id="6ae18-117">Type **ssoconfig –restoreSecret \<restore file>**, where **\<restore file>** is the path and name of the file where the master secret is stored.</span></span>  
  
     <span data-ttu-id="6ae18-118">主要密碼儲存在下列位置的登錄中：</span><span class="sxs-lookup"><span data-stu-id="6ae18-118">The master secret is stored in the registry at the following location:</span></span>  
  
     <span data-ttu-id="6ae18-119">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ENTSSO\SSOSS</span><span class="sxs-lookup"><span data-stu-id="6ae18-119">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ENTSSO\SSOSS</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6ae18-120">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="6ae18-120">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-promote-a-single-sign-on-server-to-master-secret-server-using-the-command-line"></a><span data-ttu-id="6ae18-121">使用命令列將單一登入伺服器升級為主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="6ae18-121">To promote a Single Sign-On Server to master secret server using the command line</span></span>  
  
1.  <span data-ttu-id="6ae18-122">建立包含您要升級為主要密碼伺服器的 SSO 伺服器名稱之 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="6ae18-122">Create an XML file that includes the name of the SSO server you want to promote to master secret server.</span></span> <span data-ttu-id="6ae18-123">例如，</span><span class="sxs-lookup"><span data-stu-id="6ae18-123">For example,</span></span>  
  
    ```  
    <sso>  
      <globalInfo>  
         <secretServer>SSO Server name</secretServer>  
      </globalInfo>  
    </sso>  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="6ae18-124">若要從非主要密碼伺服器的電腦變更主要密碼伺服器，請確認指定的 XML 檔案只包含主要密碼伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="6ae18-124">To change the Master Secret Server from a computer that is not the Master Secret Server make sure that the specified XML file contains only the Master Secret Server name.</span></span> <span data-ttu-id="6ae18-125">具體來說，它應該包含 SSO 系統管理員 XML 標記或**ssomanage-updatedb**作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="6ae18-125">Specifically, it should not contain the SSO Administrators XML tag or the **ssomanage -updatedb** operation will fail.</span></span>  
  
2.  <span data-ttu-id="6ae18-126">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="6ae18-126">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
3.  <span data-ttu-id="6ae18-127">在命令列提示字元中，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="6ae18-127">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="6ae18-128">預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="6ae18-128">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="6ae18-129">型別**ssomanage – updatedb** \<**更新檔案**>，其中\<**更新檔案**> 是您在步驟 1 中建立的 XML 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="6ae18-129">Type **ssomanage –updatedb** \<**update file**>, where \<**update file**> is the name of the XML file you create in step 1.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6ae18-130">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="6ae18-130">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
5.  <span data-ttu-id="6ae18-131">重新啟動主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="6ae18-131">Restart the Master Secret Server.</span></span>  
  
6.  <span data-ttu-id="6ae18-132">型別**ssoconfig – restoresecret\<還原檔案 >**，其中**\<還原檔案 >**是儲存主要密碼的檔案名稱與路徑。</span><span class="sxs-lookup"><span data-stu-id="6ae18-132">Type **ssoconfig –restoresecret \<restore file>**, where **\<restore file>** is the path and name of the file where the master secret is stored.</span></span>  
  
     <span data-ttu-id="6ae18-133">主要密碼儲存在下列位置的登錄中：</span><span class="sxs-lookup"><span data-stu-id="6ae18-133">The master secret is stored in the registry at the following location:</span></span>  
  
     <span data-ttu-id="6ae18-134">HKEY_LOCAL_MACHINESOFTWAREMicrosoftENTSSOSSOSS</span><span class="sxs-lookup"><span data-stu-id="6ae18-134">HKEY_LOCAL_MACHINESOFTWAREMicrosoftENTSSOSSOSS</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6ae18-135">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="6ae18-135">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ae18-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ae18-136">See Also</span></span>  
 <span data-ttu-id="6ae18-137">[主要密碼伺服器](../core/master-secret-server.md) </span><span class="sxs-lookup"><span data-stu-id="6ae18-137">[Master Secret Server](../core/master-secret-server.md) </span></span>  
 <span data-ttu-id="6ae18-138">[如何叢集化主要密碼伺服器](../core/how-to-cluster-the-master-secret-server1.md) </span><span class="sxs-lookup"><span data-stu-id="6ae18-138">[How to Cluster the Master Secret Server](../core/how-to-cluster-the-master-secret-server1.md) </span></span>  
 <span data-ttu-id="6ae18-139">[如何更新 SSO 資料庫](../core/how-to-update-the-sso-database.md) </span><span class="sxs-lookup"><span data-stu-id="6ae18-139">[How to Update the SSO Database](../core/how-to-update-the-sso-database.md) </span></span>  
 [<span data-ttu-id="6ae18-140">使用 SSO</span><span class="sxs-lookup"><span data-stu-id="6ae18-140">Using SSO</span></span>](../core/using-sso.md)