---
title: 如何移動 BAM Notification Services Databases2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Notification Services Application database [BAM]
- Notification Services Instance database [BAM]
- migrating, Notification Services database [BAM]
ms.assetid: 4b7f3397-65c9-4c71-8374-8764f4c2e2e3
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 639a326878cd425a951581711c08a0a53127035b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254262"
---
# <a name="how-to-move-the-bam-notification-services-databases"></a><span data-ttu-id="3694e-102">如何移動 BAM Notification Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="3694e-102">How to Move the BAM Notification Services Databases</span></span>
<span data-ttu-id="3694e-103">您可使用這個程序將 BAM Notification Services 資料庫移動到另一個伺服器。</span><span class="sxs-lookup"><span data-stu-id="3694e-103">You can use this procedure to move the BAM Notification Services databases to another server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3694e-104">您必須同時移動 BAM Notification Services 應用程式 (BAMAlertsApplication) 資料庫和 BAM Notification Services 執行個體 (BAMAlertsNSMain) 資料庫。</span><span class="sxs-lookup"><span data-stu-id="3694e-104">You must move the BAM Notification Services Application (BAMAlertsApplication) database and BAM Notification Services Instance (BAMAlertsNSMain) database together.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3694e-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="3694e-105">Prerequisites</span></span>  
 <span data-ttu-id="3694e-106">您必須以 SQL Server 系統管理員 (sysadmin) 固定伺服器角色成員的帳戶登入來執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="3694e-106">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-move-the-bam-notification-services-databases"></a><span data-ttu-id="3694e-107">移動 BAM Notification Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="3694e-107">To move the BAM Notification Services databases</span></span>  
  
1.  <span data-ttu-id="3694e-108">取得用來還原 BAM 的 .xml 檔案複本：</span><span class="sxs-lookup"><span data-stu-id="3694e-108">Get a copy of the .xml file used for restoring BAM:</span></span>  
  
    1.  <span data-ttu-id="3694e-109">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="3694e-109">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="3694e-110">在命令提示字元中，瀏覽至下列目錄：</span><span class="sxs-lookup"><span data-stu-id="3694e-110">At the command prompt, navigate to the following directory:</span></span>  
  
         <span data-ttu-id="3694e-111">**%SystemDrive%\Program Files\Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\Tracking** </span><span class="sxs-lookup"><span data-stu-id="3694e-111">**%SystemDrive%\Program Files\Microsoft**  [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\Tracking**</span></span>  
  
    3.  <span data-ttu-id="3694e-112">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="3694e-112">At the command prompt, type:</span></span>  
  
        ```  
        Bm.exe get-config –filename:BAMConfiguration.xml  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="3694e-113">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="3694e-113">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
2.  <span data-ttu-id="3694e-114">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="3694e-114">At the command prompt, type:</span></span>  
  
    ```  
    Net stop NS$BamAlerts  
    ```  
  
3.  <span data-ttu-id="3694e-115">依照《SQL Server 線上叢書》中關於如何在舊伺服器上備份資料庫的指示執行。</span><span class="sxs-lookup"><span data-stu-id="3694e-115">Follow the instructions in SQL Server Books Online on how to back up the database on the old server.</span></span>  
  
4.  <span data-ttu-id="3694e-116">將 BAM Notification Services 資料庫複製到新的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="3694e-116">Copy the BAM Notification Services databases to the new SQL server.</span></span>  
  
5.  <span data-ttu-id="3694e-117">依照《SQL Server 線上叢書》中關於如何在新伺服器上還原資料庫的指示執行。</span><span class="sxs-lookup"><span data-stu-id="3694e-117">Follow the instructions in SQL Server Books Online on how to restore the database on the new server.</span></span>  
  
6.  <span data-ttu-id="3694e-118">編輯 BAMConfiguration.xml 檔案，並將警示 DeploymentUnit 區段中的 ServerName 變更為新的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="3694e-118">Edit the BAMConfiguration.xml file and change the ServerName in the Alert DeploymentUnit section to the new server name.</span></span>  
  
7.  <span data-ttu-id="3694e-119">儲存並關閉 BAMConfiguration.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="3694e-119">Save and close the BAMConfiguration.xml file.</span></span>  
  
8.  <span data-ttu-id="3694e-120">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="3694e-120">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="3694e-121">在命令提示字元中，瀏覽至下列目錄：</span><span class="sxs-lookup"><span data-stu-id="3694e-121">At the command prompt, navigate to the following directory:</span></span>  
  
     <span data-ttu-id="3694e-122">**%SystemDrive%\Program Files\Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\Tracking** </span><span class="sxs-lookup"><span data-stu-id="3694e-122">**%SystemDrive%\Program Files\Microsoft**  [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\Tracking**</span></span>  
  
10. <span data-ttu-id="3694e-123">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="3694e-123">At the command prompt, type:</span></span>  
  
    ```  
    bm.exe update-config -FileName:BAMConfiguration.xml  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="3694e-124">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="3694e-124">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
11. <span data-ttu-id="3694e-125">更新 BAM Notification Services 資料庫的參考。</span><span class="sxs-lookup"><span data-stu-id="3694e-125">Update references to the BAM Notification Services databases.</span></span> <span data-ttu-id="3694e-126">如需詳細資訊，請參閱[如何更新 BAM Notification Services 資料庫參考](../core/how-to-update-references-to-the-bam-notification-services-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="3694e-126">For more information, see [How to Update References to the BAM Notification Services Databases](../core/how-to-update-references-to-the-bam-notification-services-databases.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3694e-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3694e-127">See Also</span></span>  
 [<span data-ttu-id="3694e-128">移動 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="3694e-128">Moving BizTalk Server Databases</span></span>](../core/moving-biztalk-server-databases.md)