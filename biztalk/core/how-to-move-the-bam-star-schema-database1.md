---
title: "如何移動 BAM 星狀結構描述 Database1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Star Schema database [BAM], migrating
- migrating, Star Schema database [BAM]
ms.assetid: b4a5f8fc-0dc4-4987-b96f-ecd49bd4dba3
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6661a9ae315988a5348198fa463e24ea508cf50f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-the-bam-star-schema-database"></a><span data-ttu-id="5a74a-102">如何移動 BAM 星狀結構描述資料庫</span><span class="sxs-lookup"><span data-stu-id="5a74a-102">How to Move the BAM Star Schema Database</span></span>
<span data-ttu-id="5a74a-103">您可以使用這個程序將「BAM 星狀結構描述」資料庫移動到其他伺服器。</span><span class="sxs-lookup"><span data-stu-id="5a74a-103">You can use this procedure to move the BAM Star Schema database to another server.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5a74a-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="5a74a-104">Prerequisites</span></span>  
 <span data-ttu-id="5a74a-105">您必須以 SQL Server 系統管理員 (sysadmin) 固定伺服器角色成員的帳戶登入來執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="5a74a-105">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-move-the-bam-star-schema-database"></a><span data-ttu-id="5a74a-106">移動 BAM 星狀結構描述資料庫</span><span class="sxs-lookup"><span data-stu-id="5a74a-106">To move the BAM Star Schema database</span></span>  
  
1.  <span data-ttu-id="5a74a-107">取得用來還原 BAM 的 .xml 檔案複本：</span><span class="sxs-lookup"><span data-stu-id="5a74a-107">Get a copy of the .xml file used for restoring BAM:</span></span>  
  
    1.  <span data-ttu-id="5a74a-108">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="5a74a-108">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="5a74a-109">在命令提示字元中，瀏覽至下列目錄：</span><span class="sxs-lookup"><span data-stu-id="5a74a-109">At the command prompt, navigate to the following directory:</span></span>  
  
         [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="5a74a-110">Tracking</span><span class="sxs-lookup"><span data-stu-id="5a74a-110">Tracking</span></span>  
  
    3.  <span data-ttu-id="5a74a-111">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="5a74a-111">At the command prompt, type:</span></span>  
  
        ```  
        Bm.exe get-config –filename:BAMConfiguration.xml  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="5a74a-112">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="5a74a-112">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
2.  <span data-ttu-id="5a74a-113">依照《SQL Server 線上叢書》中關於如何在舊伺服器上備份資料庫的指示執行。</span><span class="sxs-lookup"><span data-stu-id="5a74a-113">Follow the instructions in SQL Server Books Online on how to back up the database on the old server.</span></span>  
  
3.  <span data-ttu-id="5a74a-114">將「BAM 星狀結構描述」資料庫複製到新的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="5a74a-114">Copy the BAM Star Schema database to the new SQL Server.</span></span>  
  
4.  <span data-ttu-id="5a74a-115">依照《SQL Server 線上叢書》中關於如何在新伺服器上還原資料庫的指示執行。</span><span class="sxs-lookup"><span data-stu-id="5a74a-115">Follow the instructions in SQL Server Books Online on how to restore the database on the new server.</span></span>  
  
5.  <span data-ttu-id="5a74a-116">編輯 BAMConfiguration.xml 檔案，並將 StarSchemaDatabase DeploymentUnit 區段中的 ServerName 變更為新的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="5a74a-116">Edit the BAMConfiguration.xml file and change the ServerName in the StarSchemaDatabase DeploymentUnit section to the new server name.</span></span>  
  
6.  <span data-ttu-id="5a74a-117">儲存並關閉 BAMConfiguration.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="5a74a-117">Save and close the BAMConfiguration.xml file.</span></span>  
  
7.  <span data-ttu-id="5a74a-118">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="5a74a-118">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="5a74a-119">在命令提示字元中，瀏覽至下列目錄：</span><span class="sxs-lookup"><span data-stu-id="5a74a-119">At the command prompt, navigate to the following directory:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="5a74a-120">Tracking</span><span class="sxs-lookup"><span data-stu-id="5a74a-120">Tracking</span></span>  
  
9. <span data-ttu-id="5a74a-121">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="5a74a-121">At the command prompt, type:</span></span>  
  
    ```  
    bm.exe update-config -FileName:BAMConfiguration.xml  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="5a74a-122">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="5a74a-122">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
10. <span data-ttu-id="5a74a-123">依照下列步驟，更新 SQL 連線 2 以變更所有 BAM 分析 DTS 封裝中的伺服器及資料庫名稱 (這些名稱以 "BAM_AN_" 作為前置詞)：</span><span class="sxs-lookup"><span data-stu-id="5a74a-123">Update SQL Connection 2 to change the server and database name in all BAM analysis DTS packages, which are prefixed with "BAM_AN_", by following these steps:</span></span>  
  
    1.  <span data-ttu-id="5a74a-124">使用 SQL Server Management Studio，開啟裝載 BAM 的伺服器。</span><span class="sxs-lookup"><span data-stu-id="5a74a-124">Using SQL Server Management Studio, open the server hosting BAM.</span></span>  
  
    2.  <span data-ttu-id="5a74a-125">開啟**Data Transformation Services**資料夾。</span><span class="sxs-lookup"><span data-stu-id="5a74a-125">Open the **Data Transformation Services** folder.</span></span>  
  
    3.  <span data-ttu-id="5a74a-126">開啟**本機封裝**資料夾。</span><span class="sxs-lookup"><span data-stu-id="5a74a-126">Open the **Local Packages** folder.</span></span>  
  
    4.  <span data-ttu-id="5a74a-127">開啟 DTS 封裝，然後再連按兩下**連線 2**來開啟連接。</span><span class="sxs-lookup"><span data-stu-id="5a74a-127">Open the DTS package, and then double-click **Connection 2** to open the connection.</span></span>  
  
    5.  <span data-ttu-id="5a74a-128">選取下拉式方塊中的新伺服器及資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="5a74a-128">Select the new server and database name in the drop-down box.</span></span>  
  
11. <span data-ttu-id="5a74a-129">更新 BAM 分析資料庫中的資料來源，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5a74a-129">Update the data source in the BAM Analysis database as follows:</span></span>  
  
    1.  <span data-ttu-id="5a74a-130">使用 SQL Server 分析管理員，開啟裝載 BAM 分析資料庫的伺服器。</span><span class="sxs-lookup"><span data-stu-id="5a74a-130">Using SQL Server Analysis Manager, open the server hosting the BAM Analysis database.</span></span>  
  
    2.  <span data-ttu-id="5a74a-131">開啟**資料來源**資料夾。</span><span class="sxs-lookup"><span data-stu-id="5a74a-131">Open the **Data Sources** folder.</span></span>  
  
    3.  <span data-ttu-id="5a74a-132">以滑鼠右鍵按一下 cube 的資料來源，然後按一下**編輯**。</span><span class="sxs-lookup"><span data-stu-id="5a74a-132">Right-click the data source for the cube, and then click **Edit**.</span></span>  
  
    4.  <span data-ttu-id="5a74a-133">在**連接**索引標籤上，輸入新的伺服器名稱和 BAM 星狀結構描述資料庫的資料庫名稱，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="5a74a-133">On the **Connection** tab, type the new server name and database name for the BAM Star Schema database, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a74a-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a74a-134">See Also</span></span>  
 [<span data-ttu-id="5a74a-135">移動 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="5a74a-135">Moving BizTalk Server Databases</span></span>](../core/moving-biztalk-server-databases.md)