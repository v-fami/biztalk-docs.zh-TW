---
title: 如何使用 BAM 管理公用程式的 BAM 資料庫的設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 801338f4-b363-4f8e-b248-9c628065ded2
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6878e6aa3874384bd17f340c62421c432182f637
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001311"
---
# <a name="how-to-set-up-the-bam-databases-using-the-bam-management-utility"></a><span data-ttu-id="0148a-102">如何使用 BAM 管理公用程式安裝 BAM 資料庫</span><span class="sxs-lookup"><span data-stu-id="0148a-102">How to Set Up the BAM Databases Using the BAM Management Utility</span></span>
<span data-ttu-id="0148a-103">一般而言，系統管理員會使用 BizTalk Server 組態公用程式安裝 BAM 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0148a-103">Administrators typically use the BizTalk Server configuration utility to set up the BAM databases.</span></span> <span data-ttu-id="0148a-104">您可以用另一種方法，也就是使用 BAM 管理公用程式 (bm.exe) 來安裝資料庫。</span><span class="sxs-lookup"><span data-stu-id="0148a-104">You can use the BAM Management utility (bm.exe) as an alternate method to set up the databases.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0148a-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="0148a-105">Prerequisites</span></span>  
 <span data-ttu-id="0148a-106">以下是執行此主題中之程序的必要條件：</span><span class="sxs-lookup"><span data-stu-id="0148a-106">The following are prerequisites for performing the procedure in this topic:</span></span>  
  
-   <span data-ttu-id="0148a-107">您必須擁有裝載 BAMPrimaryImport、BAMStarSchema 和 BAMArchive 資料庫之 SQL 伺服器的系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="0148a-107">You must have administrator permissions on the SQL server hosting the BAMPrimaryImport, BAMStarSchema, and BAMArchive databases.</span></span>  
  
-   <span data-ttu-id="0148a-108">若要安裝 SQL Notification Services 資料庫，您必須擁有系統管理員權限，並且隸屬於本機系統管理員群組及任何其他已設定的系統管理員群組 (例如 BTS Admins 群組)。</span><span class="sxs-lookup"><span data-stu-id="0148a-108">To set up the SQL Notification Services databases, you must have administrator permission and be a member of the local administrators group, as well as be a member of any additional administrator groups that have been configured, such as the BTS Admins group.</span></span>  
  
-   <span data-ttu-id="0148a-109">您必須擁有包含 XML 資料的 BAM 組態檔案，以便用來安裝建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="0148a-109">You must have a BAM configuration file containing XML data from which to set up the databases.</span></span>  
  
### <a name="to-set-up-the-bam-databases-using-the-bam-management-utility"></a><span data-ttu-id="0148a-110">使用 BAM 管理公用程式安裝 BAM 資料庫</span><span class="sxs-lookup"><span data-stu-id="0148a-110">To set up the BAM databases using the BAM Management utility</span></span>  
  
1. <span data-ttu-id="0148a-111">開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="0148a-111">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="0148a-112">瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="0148a-112">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3. <span data-ttu-id="0148a-113">在命令提示字元輸入下列命令： **bm 設定-資料庫-ConfigFile:\<組態檔\>**，其中\<*組態檔*\>會取代您的 BAM 組態檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="0148a-113">Type the following at the command line prompt: **bm setup-databases -ConfigFile:\<configuration file\>**, where \<*configuration file*\> is replaced by the name of your BAM configuration file.</span></span> <span data-ttu-id="0148a-114">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="0148a-114">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0148a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0148a-115">See Also</span></span>  
 [<span data-ttu-id="0148a-116">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="0148a-116">BAM Management Utility</span></span>](../core/bam-management-utility.md)