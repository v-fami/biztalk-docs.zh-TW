---
title: "BAM 管理公用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c55aabe2-f38b-4917-863c-b408a4eef98e
caps.latest.revision: "50"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5374ba63ba8eb4193c3ef4990e8c169646a3528b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="bam-management-utility"></a><span data-ttu-id="712a1-102">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="712a1-102">BAM Management Utility</span></span>
<span data-ttu-id="712a1-103">商務活動監控 (BAM) 定義的管理員可使用 BAM 管理公用程式，來管理和維護 BAM 基礎結構的所有層面。</span><span class="sxs-lookup"><span data-stu-id="712a1-103">Administrators of Business Activity Monitoring (BAM) definitions use the BAM Management utility to manage and maintain all aspects of the BAM infrastructure.</span></span>  
  
 <span data-ttu-id="712a1-104">您可以使用 BAM 公用程式執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="712a1-104">You can use the BAM utility to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="712a1-105">使用 BAM 定義以及 BAM 組態 XML 做為輸入項。</span><span class="sxs-lookup"><span data-stu-id="712a1-105">Consume BAM definition and BAM configuration XML as input.</span></span> <span data-ttu-id="712a1-106">BAM 定義 XML 或 XLS 檔案定義所要追蹤和彙總的資料，以及追蹤資料的商務使用者檢視。</span><span class="sxs-lookup"><span data-stu-id="712a1-106">The BAM definition XML or XLS files define the data to track and aggregate, as well as the business end user's view on the tracking data.</span></span> <span data-ttu-id="712a1-107">BAM 組態 XML 則指定部署基礎結構的地點，例如伺服器名稱、資料庫名稱和資料庫的其他設定。</span><span class="sxs-lookup"><span data-stu-id="712a1-107">The BAM configuration XML mandates where to deploy the infrastructure, such as the server name, database name, and other database settings.</span></span>  
  
-   <span data-ttu-id="712a1-108">在伺服器上部署執行階段基礎結構，包括 BAM 主要匯入資料庫、BAM 星狀結構描述資料庫、BAM 分析資料庫以及對應的 Data Transformation Services (DTS) 封裝。</span><span class="sxs-lookup"><span data-stu-id="712a1-108">Deploy the run-time infrastructure on the server, which includes the BAM Primary Import database, BAM Star Schema database, BAM Analysis database, and corresponding Data Transformation Services (DTS) packages.</span></span> <span data-ttu-id="712a1-109">執行此步驟時會建立下列項目：</span><span class="sxs-lookup"><span data-stu-id="712a1-109">The following items are created during this step:</span></span>  
  
    -   <span data-ttu-id="712a1-110">BAM 主要匯入資料庫</span><span class="sxs-lookup"><span data-stu-id="712a1-110">BAM Primary Import database</span></span>  
  
    -   <span data-ttu-id="712a1-111">BAM 星狀結構描述資料庫</span><span class="sxs-lookup"><span data-stu-id="712a1-111">BAM Star Schema database</span></span>  
  
    -   <span data-ttu-id="712a1-112">BAM 封存資料庫</span><span class="sxs-lookup"><span data-stu-id="712a1-112">BAM Archive database</span></span>  
  
    -   <span data-ttu-id="712a1-113">BAM 分析資料庫</span><span class="sxs-lookup"><span data-stu-id="712a1-113">BAM Analysis database</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="712a1-114">執行 BAM 管理公用程式的電腦，其地區設定必須與建立 BAM 定義以進行部署所使用的地區設定相同，BAM 命令才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="712a1-114">The locale setting of the computer running the BAM Management utility must be the same as the locale used to create the BAM definition being deployed in order for the BAM commands to work properly.</span></span> <span data-ttu-id="712a1-115">例如，如果您執行**get 檢視**命令設定的電腦上採用英文地區設定比對資料庫使用法文地區設定的電腦上您將無法使用傳回的檢視名稱，除非您重設您電腦為法文的地區設定。</span><span class="sxs-lookup"><span data-stu-id="712a1-115">For example, if you execute the **get-views** command on a computer configured with an English locale setting against a database on a computer with a French locale you will not be able to use the returned view name unless you reset your computer locale to French.</span></span>  
  
 <span data-ttu-id="712a1-116">您可以使用 BAM 管理公用程式在伺服器上產生並部署追蹤組態。</span><span class="sxs-lookup"><span data-stu-id="712a1-116">You can use the BAM Management utility to generate and deploy your tracking configuration on a server.</span></span> <span data-ttu-id="712a1-117">BAM 管理公用程式是命令列工具位於\<*安裝路徑*\>\Program Files\Microsoft BizTalk Server\<版本\>\Tracking\BM.exe。</span><span class="sxs-lookup"><span data-stu-id="712a1-117">The BAM Management utility is a command-line tool located at \<*installation path*\>\Program Files\Microsoft BizTalk Server \<version\>\Tracking\BM.exe.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="712a1-118">若要執行 BAM 管理公用程式，您必須是成員**db_owner** BAM 主要匯入、 BAM 星狀結構描述和 BAM 封存資料庫中的 SQL Server 資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="712a1-118">To run the BAM management utility, you must be member of the **db_owner** SQL Server Database role in the BAM Primary Import, BAM Star Schema, and BAM Archive databases.</span></span> <span data-ttu-id="712a1-119">您也必須擁有 BAM 警示資料庫上 sysadmin 權限，如果進行與 BAM 警示相關的任何更新。</span><span class="sxs-lookup"><span data-stu-id="712a1-119">You must also have sysadmin permissions on the BAM Alerts databases if making any updates related to BAM Alerts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="712a1-120">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="712a1-120">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="712a1-121">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="712a1-121">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
## <a name="bam-management-utility-commands"></a><span data-ttu-id="712a1-122">BAM 管理公用程式命令</span><span class="sxs-lookup"><span data-stu-id="712a1-122">BAM Management Utility Commands</span></span>  
 <span data-ttu-id="712a1-123">此命令描述使用下列慣例：</span><span class="sxs-lookup"><span data-stu-id="712a1-123">The command descriptions use these conventions:</span></span>  
  
-   <span data-ttu-id="712a1-124">方括弧 ([]) 代表選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="712a1-124">The square brackets ([]) indicate an optional parameter.</span></span>  
  
-   <span data-ttu-id="712a1-125">角括弧 (<>) 代表必要參數。</span><span class="sxs-lookup"><span data-stu-id="712a1-125">The angled brackets (<>) indicate a required parameter.</span></span>  
  
-   <span data-ttu-id="712a1-126">大括弧 ({}) 代表應從列舉清單中選取的項目。</span><span class="sxs-lookup"><span data-stu-id="712a1-126">The braces ({}) indicate that one item should be selected from the enumerated list.</span></span>  
  
-   <span data-ttu-id="712a1-127">安全性帳戶可能是 NT 群組或個別的 NT 使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="712a1-127">A security account can be either an NT group or an individual NT user account.</span></span>  
  
-   <span data-ttu-id="712a1-128">BAM 定義檔案可能是 XML 檔案或 BAM Excel 活頁簿檔案 (.xls)。</span><span class="sxs-lookup"><span data-stu-id="712a1-128">A BAM definition file can be either an XML file or a BAM Excel workbook file (.xls).</span></span>  
  
-   <span data-ttu-id="712a1-129">如果沒有提供 BAM 組態檔，則預設為目前資料夾中的 BamConfiguration.xml。</span><span class="sxs-lookup"><span data-stu-id="712a1-129">If the BAM configuration file is not supplied, it defaults to BamConfiguration.xml in the current folder.</span></span>  
  
 <span data-ttu-id="712a1-130">下列主題包含個別命令的說明：</span><span class="sxs-lookup"><span data-stu-id="712a1-130">The Individual command descriptions are contained in the following topics:</span></span>  
  
-   [<span data-ttu-id="712a1-131">資料庫命令</span><span class="sxs-lookup"><span data-stu-id="712a1-131">Database Commands</span></span>](../core/database-commands.md)  
  
-   [<span data-ttu-id="712a1-132">BAM 定義的部署 (觀察模型) 命令</span><span class="sxs-lookup"><span data-stu-id="712a1-132">Deployment of BAM Definition (Observation Model) Commands</span></span>](../core/deployment-of-bam-definition-observation-model-commands.md)  
  
-   [<span data-ttu-id="712a1-133">基礎結構管理命令</span><span class="sxs-lookup"><span data-stu-id="712a1-133">Infrastructure Management Commands</span></span>](../core/infrastructure-management-commands.md)  
  
-   [<span data-ttu-id="712a1-134">活動管理命令</span><span class="sxs-lookup"><span data-stu-id="712a1-134">Activity Management Commands</span></span>](../core/activity-management-commands.md)  
  
-   [<span data-ttu-id="712a1-135">檢視管理命令</span><span class="sxs-lookup"><span data-stu-id="712a1-135">View Management Commands</span></span>](../core/view-management-commands.md)  
  
-   [<span data-ttu-id="712a1-136">警示管理命令</span><span class="sxs-lookup"><span data-stu-id="712a1-136">Alert Management Commands</span></span>](../core/alert-management-commands.md)  
  
-   [<span data-ttu-id="712a1-137">使用者管理命令</span><span class="sxs-lookup"><span data-stu-id="712a1-137">User Management Commands</span></span>](../core/user-management-commands.md)  
  
-   [<span data-ttu-id="712a1-138">警示訂閱管理命令</span><span class="sxs-lookup"><span data-stu-id="712a1-138">Alert Subscription Management Commands</span></span>](../core/alert-subscription-management-commands.md)  
  
-   [<span data-ttu-id="712a1-139">攔截器管理命令</span><span class="sxs-lookup"><span data-stu-id="712a1-139">Interceptor Management Commands</span></span>](../core/interceptor-management-commands.md)  
  
## <a name="displaying-the-bam-management-utility-help"></a><span data-ttu-id="712a1-140">顯示 BAM 管理公用程式說明</span><span class="sxs-lookup"><span data-stu-id="712a1-140">Displaying the BAM Management Utility Help</span></span>  
 <span data-ttu-id="712a1-141">您使用**/？**</span><span class="sxs-lookup"><span data-stu-id="712a1-141">You use the **/?**</span></span> <span data-ttu-id="712a1-142">或**協助 BAM 管理公用程式**命令，以顯示 BAM 管理公用程式的說明檔。</span><span class="sxs-lookup"><span data-stu-id="712a1-142">or the **help BAM Management utility** command to display the Help file for the BAM Management utility.</span></span>  
  
#### <a name="to-display-the-help-file-for-the-bam-management-utility"></a><span data-ttu-id="712a1-143">若要顯示 BAM 管理公用程式的說明檔</span><span class="sxs-lookup"><span data-stu-id="712a1-143">To display the Help file for the BAM Management utility</span></span>  
  
1.  <span data-ttu-id="712a1-144">從命令提示字元，瀏覽至下列目錄： C:\Program Files\Microsoft BizTalk Server\<版本\>\Tracking\\。</span><span class="sxs-lookup"><span data-stu-id="712a1-144">From a command prompt, browse to the following directory: C:\Program Files\Microsoft BizTalk Server \<version\>\Tracking\\.</span></span>  
  
2.  <span data-ttu-id="712a1-145">型別**bm**或**bm 說明**。</span><span class="sxs-lookup"><span data-stu-id="712a1-145">Type **bm** or **bm help**.</span></span>  
  
3.  <span data-ttu-id="712a1-146">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="712a1-146">Press ENTER.</span></span>