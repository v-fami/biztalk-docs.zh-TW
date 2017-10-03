---
title: "如何移動 BAM 分析 Database2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- migrating, Analysis database [BAM]
- Analysis database [BAM], migrating
ms.assetid: b0320273-4840-4573-bb82-bba95021535e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f9ae627dffd36ceca78e7da0b9e8e516845691a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-the-bam-analysis-database"></a><span data-ttu-id="faca9-102">如何移動 BAM 分析資料庫</span><span class="sxs-lookup"><span data-stu-id="faca9-102">How to Move the BAM Analysis Database</span></span>
<span data-ttu-id="faca9-103">您可以使用這個程序，將 BAM 分析資料庫移動到其他伺服器。</span><span class="sxs-lookup"><span data-stu-id="faca9-103">You can use this procedure to move the BAM Analysis database to another server.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="faca9-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="faca9-104">Prerequisites</span></span>  
 <span data-ttu-id="faca9-105">您必須以 SQL Server 系統管理員 (sysadmin) 固定伺服器角色成員的帳戶登入來執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="faca9-105">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-move-the-bam-analysis-database"></a><span data-ttu-id="faca9-106">移動 BAM 分析資料庫</span><span class="sxs-lookup"><span data-stu-id="faca9-106">To move the BAM Analysis database</span></span>  
  
1.  <span data-ttu-id="faca9-107">取得用來還原 BAM 的 .xml 檔案複本：</span><span class="sxs-lookup"><span data-stu-id="faca9-107">Get a copy of the .xml file used for restoring BAM:</span></span>  
  
    1.  <span data-ttu-id="faca9-108">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="faca9-108">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="faca9-109">在命令提示字元中，瀏覽至下列目錄：</span><span class="sxs-lookup"><span data-stu-id="faca9-109">At the command prompt, navigate to the following directory:</span></span>  
  
         [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="faca9-110">Tracking</span><span class="sxs-lookup"><span data-stu-id="faca9-110">Tracking</span></span>  
  
    3.  <span data-ttu-id="faca9-111">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="faca9-111">At the command prompt, type:</span></span>  
  
        ```  
        Bm.exe get-config –filename:BAMConfiguration.xml  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="faca9-112">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="faca9-112">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
2.  <span data-ttu-id="faca9-113">依照《SQL Server 線上叢書》中關於如何在舊伺服器上備份資料庫的指示執行。</span><span class="sxs-lookup"><span data-stu-id="faca9-113">Follow the instructions in SQL Server Books Online on how to back up the database on the old server.</span></span>  
  
3.  <span data-ttu-id="faca9-114">將 BAM 分析資料庫複製到新的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="faca9-114">Copy the BAM Analysis database to the new SQL Server.</span></span>  
  
4.  <span data-ttu-id="faca9-115">依照《SQL Server 線上叢書》中關於如何在新伺服器上還原資料庫的指示執行。</span><span class="sxs-lookup"><span data-stu-id="faca9-115">Follow the instructions in SQL Server Books Online on how to restore the database on the new server.</span></span>  
  
5.  <span data-ttu-id="faca9-116">編輯 BAMConfiguration.xml 檔案，並將 AnalysisDatabase DeploymentUnit 區段中的 ServerName 變更為新的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="faca9-116">Edit the BAMConfiguration.xml file and change the ServerName in the AnalysisDatabase DeploymentUnit section to the new server name.</span></span>  
  
6.  <span data-ttu-id="faca9-117">儲存並關閉 BAMConfiguration.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="faca9-117">Save and close the BAMConfiguration.xml file.</span></span>  
  
7.  <span data-ttu-id="faca9-118">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="faca9-118">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="faca9-119">在命令提示字元中，瀏覽至下列目錄：</span><span class="sxs-lookup"><span data-stu-id="faca9-119">At the command prompt, navigate to the following directory:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="faca9-120">Tracking</span><span class="sxs-lookup"><span data-stu-id="faca9-120">Tracking</span></span>  
  
9. <span data-ttu-id="faca9-121">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="faca9-121">At the command prompt, type:</span></span>  
  
    ```  
    bm.exe update-config -FileName:BAMConfiguration.xml  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="faca9-122">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="faca9-122">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faca9-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="faca9-123">See Also</span></span>  
 [<span data-ttu-id="faca9-124">移動 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="faca9-124">Moving BizTalk Server Databases</span></span>](../core/moving-biztalk-server-databases.md)