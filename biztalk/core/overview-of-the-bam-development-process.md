---
title: BAM 開發程序的概觀 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 098db3f6-2a61-4cc8-88c7-2299c2e2a55e
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78ae5f1c61f2a00359e88acd75c093e2b6c2fb91
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "25972500"
---
# <a name="overview-of-the-bam-development-process"></a><span data-ttu-id="0f6b3-102">BAM 開發程序概觀</span><span class="sxs-lookup"><span data-stu-id="0f6b3-102">Overview of the BAM Development Process</span></span>
<span data-ttu-id="0f6b3-103">本主題描述開發程序和用來存放 BAM 資料的資料庫與資料表。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-103">This topic describes the development process and the database and tables that store BAM data.</span></span>  
  
## <a name="prerequisites-for-developing-with-bam"></a><span data-ttu-id="0f6b3-104">開發 BAM 的必要條件</span><span class="sxs-lookup"><span data-stu-id="0f6b3-104">Prerequisites for Developing with BAM</span></span>  
 <span data-ttu-id="0f6b3-105">開始開發 BAM 之前，請注意下列必要條件：</span><span class="sxs-lookup"><span data-stu-id="0f6b3-105">Note the following prerequisites before you begin developing with BAM:</span></span>  
  
-   <span data-ttu-id="0f6b3-106">為了檢測應用程式，您必須已經部署活動。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-106">To instrument an application you must have an activity deployed.</span></span>  
  
-   <span data-ttu-id="0f6b3-107">您必須具有 SQL Server 資料庫的 DBO 權限，並且是「BAM 事件寫入器角色」資訊安全內容的成員。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-107">You must have DBO rights to the SQL Server databases and be a member of the BAM Event Writer Role security context.</span></span>  
  
-   <span data-ttu-id="0f6b3-108">您必須使用 Microsoft .NET 4 來開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-108">You must use Microsoft .NET 4 to develop your application.</span></span> <span data-ttu-id="0f6b3-109">雖然建議使用 C#，您還是可以使用任何 .NET 語言。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-109">You can use any .NET language, although we recommend that you use C#.</span></span>  
  
-   <span data-ttu-id="0f6b3-110">您必須在電腦上安裝 Microsoft.BizTalk.BAM.EventObservation.dll。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-110">You must have the Microsoft.BizTalk.BAM.EventObservation.dll installed on your computer.</span></span> <span data-ttu-id="0f6b3-111">您可以使用兩種方法來取得 DLL。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-111">You can obtain the DLL in two ways:</span></span>  
  
    -   <span data-ttu-id="0f6b3-112">使用 BizTalk Server 組態管理員來安裝 BAM 工具。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-112">Use the BizTalk Server Configuration Manager to install the BAM tools.</span></span> <span data-ttu-id="0f6b3-113">建議您使用「組態管理員」，是因為它會置入有助於升級的適當登錄。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-113">We recommend that you use the Configuration Manager because it places appropriate entries in the registry that facilitate upgrades.</span></span> <span data-ttu-id="0f6b3-114">如需有關如何設定 BAM 的詳細資訊，請參閱[使用組態管理員設定 BAM 工具](http://go.microsoft.com/fwlink/?LinkId=70561)(http://go.microsoft.com/fwlink/?LinkId=70561)。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-114">For more information about configuring BAM, see [Configuring BAM Tools Using the Configuration Manager](http://go.microsoft.com/fwlink/?LinkId=70561) (http://go.microsoft.com/fwlink/?LinkId=70561).</span></span>  
  
    -   <span data-ttu-id="0f6b3-115">從已經安裝這些 DLL 的電腦中複製它們。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-115">Copy the DLL from a computer on which they have already been installed.</span></span> <span data-ttu-id="0f6b3-116">DLL 位於 Microsoft BizTalk Server\<版本\>\Tracking 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-116">The DLL resides in the Microsoft BizTalk Server \<version\>\Tracking folder.</span></span>  
  
## <a name="bam-development-process"></a><span data-ttu-id="0f6b3-117">BAM 開發程序</span><span class="sxs-lookup"><span data-stu-id="0f6b3-117">BAM Development Process</span></span>  
 <span data-ttu-id="0f6b3-118">下圖描述 BAM 開發流程。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-118">The following figure describes the BAM development flow.</span></span>  
  
 <span data-ttu-id="0f6b3-119">![BAM 開發工作流程](../core/media/dwb-bamdevelopmentflowc.gif "dwb_bamdevelopmentflowc")</span><span class="sxs-lookup"><span data-stu-id="0f6b3-119">![BAM development work flow](../core/media/dwb-bamdevelopmentflowc.gif "dwb_bamdevelopmentflowc")</span></span>  
  
 <span data-ttu-id="0f6b3-120">下列程序列出開發 BAM 解決方案的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-120">The following procedure lists the basic steps for developing a solution with BAM.</span></span>  
  
#### <a name="to-develop-a-bam-enabled-solution"></a><span data-ttu-id="0f6b3-121">開發啟用 BAM 功能的解決方案</span><span class="sxs-lookup"><span data-stu-id="0f6b3-121">To develop a BAM-enabled solution</span></span>  
  
1.  <span data-ttu-id="0f6b3-122">使用 Excel 的 BAM 增益集建立 BAM 觀察模型。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-122">Create an observation model with the BAM Add-in for Excel.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0f6b3-123">可以在 BAM API （BizTalk Server 範例） 中找到此程序中所述的步驟的範例[ http://go.microsoft.com/fwlink/?LinkId=69968 ](http://go.microsoft.com/fwlink/?LinkId=69968)。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-123">Examples of the steps noted in this procedure can be found in the BAM API (BizTalk Server sample) at [http://go.microsoft.com/fwlink/?LinkId=69968](http://go.microsoft.com/fwlink/?LinkId=69968).</span></span>  
  
2.  <span data-ttu-id="0f6b3-124">使用 BAM 管理公用程式，將活動部署至 PID。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-124">Use the BAM Management utility to deploy the activity to the PID.</span></span>  
  
3.  <span data-ttu-id="0f6b3-125">加入 BAM EventStream 程式碼以檢測應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-125">Instrument the application by adding your BAM EventStream code.</span></span>  
  
4.  <span data-ttu-id="0f6b3-126">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-126">Run the application.</span></span> <span data-ttu-id="0f6b3-127">當您這麼做時，程式碼將會：</span><span class="sxs-lookup"><span data-stu-id="0f6b3-127">When you do this, the code will:</span></span>  
  
    -   <span data-ttu-id="0f6b3-128">新增預留位置記錄至 BAM_<\<*活動名稱*\>_Active 資料表。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-128">Add a placeholder record to the BAM_\<*activity name*\>_Active table.</span></span>  
  
    -   <span data-ttu-id="0f6b3-129">更新記錄中的資料項目。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-129">Update the data items in the record.</span></span>  
  
    -   <span data-ttu-id="0f6b3-130">結束活動並將記錄移到 BAM_\<\* 活動名稱 \* \*\>_completed 資料表。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-130">End the activity and move the record to the BAM_\<\*activity name\*\*\>_completed table.</span></span>  
  
## <a name="where-bam-data-is-stored"></a><span data-ttu-id="0f6b3-131">儲存 BAM 資料的位置</span><span class="sxs-lookup"><span data-stu-id="0f6b3-131">Where BAM Data Is Stored</span></span>  
 <span data-ttu-id="0f6b3-132">BAM 提供 EventObservation 命名空間，其中包含可用來處理 BAM 事件的 EventStream 類別。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-132">BAM provides the EventObservation namespace that contains the EventStream classes that are used to handle BAM events.</span></span>  
  
 <span data-ttu-id="0f6b3-133">BAM 追蹤資料會儲存在 BAM 主要匯入資料庫 (PID) 中。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-133">BAM tracking data is stored in the BAM Primary Import database (PID).</span></span> <span data-ttu-id="0f6b3-134">當您使用 BAM 管理公用程式部署觀察模型時，會在 PID 中建立下列五個資料表。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-134">When you deploy an observation model using the BAM Management utility, the following five tables are created in the PID.</span></span>  
  
|<span data-ttu-id="0f6b3-135">名稱</span><span class="sxs-lookup"><span data-stu-id="0f6b3-135">Name</span></span>|<span data-ttu-id="0f6b3-136">Description</span><span class="sxs-lookup"><span data-stu-id="0f6b3-136">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="0f6b3-137">作用中資料表</span><span class="sxs-lookup"><span data-stu-id="0f6b3-137">Active table</span></span>|<span data-ttu-id="0f6b3-138">名為 bam_<\<*活動名稱*\>（_a），此資料表會保存此類型的活動尚未完成的。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-138">Named bam_\<*activity name*\>_Active, this table holds the activities of this type that have not yet completed.</span></span>|  
|<span data-ttu-id="0f6b3-139">作用中關係資料表</span><span class="sxs-lookup"><span data-stu-id="0f6b3-139">Active relationships table</span></span>|<span data-ttu-id="0f6b3-140">名為 bam_<\<*活動名稱*\>_ActiveRelationships，此資料表包含活動的相關的活動尚未完成。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-140">Named bam_\<*activity name*\>_ActiveRelationships, this table contains the related activities for the activity that have not yet completed.</span></span>|  
|<span data-ttu-id="0f6b3-141">接續資料表</span><span class="sxs-lookup"><span data-stu-id="0f6b3-141">Continuations table</span></span>|<span data-ttu-id="0f6b3-142">名為 bam_<\<*活動名稱*\>_continuations，此資料表列出活動之活動的接續。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-142">Named bam_\<*activity name*\>_continuations, this table lists the continuations activities for the activity.</span></span>|  
|<span data-ttu-id="0f6b3-143">完成的資料表</span><span class="sxs-lookup"><span data-stu-id="0f6b3-143">Completed table</span></span>|<span data-ttu-id="0f6b3-144">名為 bam_<\<*活動名稱*\>_completed。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-144">Named bam_\<*activity name*\>_completed.</span></span>|  
|<span data-ttu-id="0f6b3-145">完成的關係資料表</span><span class="sxs-lookup"><span data-stu-id="0f6b3-145">Completed Relationships table</span></span>|<span data-ttu-id="0f6b3-146">名為 bam_<\<*活動名稱*\>_CompletedRelationships，此資料表包含活動的已完成相關的活動。</span><span class="sxs-lookup"><span data-stu-id="0f6b3-146">Named bam_\<*activity name*\>_CompletedRelationships, this table contains the completed related activities for the activity.</span></span>|  
  
 <span data-ttu-id="0f6b3-147">您可以在 BAM 活動中擷取四種類型的資料：</span><span class="sxs-lookup"><span data-stu-id="0f6b3-147">You capture four types of data in a BAM activity:</span></span>  
  
-   <span data-ttu-id="0f6b3-148">字串</span><span class="sxs-lookup"><span data-stu-id="0f6b3-148">String</span></span>  
  
-   <span data-ttu-id="0f6b3-149">日期/時間 (一般稱為里程碑)</span><span class="sxs-lookup"><span data-stu-id="0f6b3-149">Data/Time (commonly referred to as milestones)</span></span>  
  
-   <span data-ttu-id="0f6b3-150">Integer</span><span class="sxs-lookup"><span data-stu-id="0f6b3-150">Integer</span></span>  
  
-   <span data-ttu-id="0f6b3-151">Float</span><span class="sxs-lookup"><span data-stu-id="0f6b3-151">Float</span></span>