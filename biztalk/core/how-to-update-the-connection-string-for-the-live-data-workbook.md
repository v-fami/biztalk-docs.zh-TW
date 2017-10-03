---
title: "如何更新即時資料活頁簿的連接字串 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d2702fb-637c-46db-8b62-08ae15f983ba
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60de5d1ae904bdefffcf490e3a39d000b28a341d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-the-connection-string-for-the-live-data-workbook"></a><span data-ttu-id="6edbd-102">如何更新即時資料活頁簿的連接字串</span><span class="sxs-lookup"><span data-stu-id="6edbd-102">How to Update the Connection String for the Live Data Workbook</span></span>
<span data-ttu-id="6edbd-103">當您將 BAM 主要匯入資料庫移到另一台伺服器時，BAM 即時資料活頁簿中的連接字串必須更新為指向新的伺服器。</span><span class="sxs-lookup"><span data-stu-id="6edbd-103">When you move the BAM Primary Import database to another server, the connection string in a BAM live data workbook must be updated to point to the new server.</span></span> <span data-ttu-id="6edbd-104">您可使用 BAM 的 Excel 增益集執行這項更新。</span><span class="sxs-lookup"><span data-stu-id="6edbd-104">You use the BAM Add-in for Excel to make this update.</span></span>  
  
### <a name="to-update-the-live-data-workbook-to-point-to-a-new-server"></a><span data-ttu-id="6edbd-105">將即時資料活頁簿更新為指向新的伺服器</span><span class="sxs-lookup"><span data-stu-id="6edbd-105">To update the live data workbook to point to a new server</span></span>  
  
1.  <span data-ttu-id="6edbd-106">按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office**，然後按一下  **Microsoft Office Excel**。</span><span class="sxs-lookup"><span data-stu-id="6edbd-106">Click **Start**, point to **All Programs**, point to **Microsoft Office**, and then click **Microsoft Office Excel**.</span></span>  
  
2.  <span data-ttu-id="6edbd-107">按一下**檔案**功能表，然後再按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="6edbd-107">Click the **File** menu, and then click **Open**.</span></span> <span data-ttu-id="6edbd-108">瀏覽至您的 BAM 即時的資料活頁簿，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="6edbd-108">Navigate to your BAM lived data workbook and click **Open**.</span></span>  
  
3.  <span data-ttu-id="6edbd-109">按一下**BAM**功能表**增益集**索引標籤，然後再按一下**BAM DB 連線**開啟**選取 BAM 資料庫** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6edbd-109">Click the **BAM** menu in the **Add-Ins** tab, and then click **BAM DB Connection** to open the **Select BAM Database** dialog box.</span></span>  
  
4.  <span data-ttu-id="6edbd-110">在**SQL Server**文字方塊中，輸入 SQL server 的 BAM 主要匯入資料庫現在的名稱。</span><span class="sxs-lookup"><span data-stu-id="6edbd-110">In the **SQL Server** text box, type the name of the SQL server on which the BAM Primary Import database now resides.</span></span>  
  
5.  <span data-ttu-id="6edbd-111">選取從 BAM 主要匯入資料庫**資料庫名稱**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="6edbd-111">Select the BAM Primary Import database from the **Database Name** drop-down list.</span></span>  
  
6.  <span data-ttu-id="6edbd-112">按一下 **[確定]** ，關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6edbd-112">Click **OK** to close the dialog box.</span></span>  
  
7.  <span data-ttu-id="6edbd-113">儲存活頁簿。</span><span class="sxs-lookup"><span data-stu-id="6edbd-113">Save the workbook.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6edbd-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6edbd-114">See Also</span></span>  
 <span data-ttu-id="6edbd-115">[管理 BAM](../core/managing-bam.md) </span><span class="sxs-lookup"><span data-stu-id="6edbd-115">[Managing BAM](../core/managing-bam.md) </span></span>  
 [<span data-ttu-id="6edbd-116">適用於 Excel 的 BAM 增益集使用的需求</span><span class="sxs-lookup"><span data-stu-id="6edbd-116">Requirements for Using the BAM Add-In for Excel</span></span>](../core/requirements-for-using-the-bam-add-in-for-excel.md)