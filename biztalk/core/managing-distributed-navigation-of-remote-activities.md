---
title: "管理遠端活動的分散式的導覽 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7cf6e0c2-ea72-4621-9ca7-fa43e404ec46
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bb21de97643d864a47d93a2ddd31e08bdd30532
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="managing-distributed-navigation-of-remote-activities"></a><span data-ttu-id="a63ee-102">管理遠端活動的分散式導覽</span><span class="sxs-lookup"><span data-stu-id="a63ee-102">Managing Distributed Navigation of Remote Activities</span></span>
<span data-ttu-id="a63ee-103">遠端活動的分散式導覽是商務使用者導覽及檢視存在於不同 BAM 資料庫中之活動的程序。</span><span class="sxs-lookup"><span data-stu-id="a63ee-103">Distributed navigation of remote activities is the process by which a business user navigates to and views activities that exist in separate BAM databases.</span></span> <span data-ttu-id="a63ee-104">當您設定 BAM 基礎結構提供分散式導覽時，BAM 入口網站中的商務使用者就可存取遠端活動。</span><span class="sxs-lookup"><span data-stu-id="a63ee-104">When you configure the BAM infrastructure to provide distributed navigation, the remote activity is accessible to the business user in the BAM portal.</span></span> <span data-ttu-id="a63ee-105">當使用者按一下活動時，該活動就會在遠端 BAM 入口網站上開啟。</span><span class="sxs-lookup"><span data-stu-id="a63ee-105">When the user clicks the activity, the activity is opened on the remote BAM portal.</span></span> <span data-ttu-id="a63ee-106">此時使用者已被順利轉換到遠端 BAM 入口網站，可以瀏覽活動搜尋、彙總以及活動的警示管理，就好像活動是在使用者的本機資料存放區一樣。</span><span class="sxs-lookup"><span data-stu-id="a63ee-106">At this point the user has been transferred in a transparent and seamless manner to the remote BAM portal and can navigate to the activity search, aggregations, and alert management for the activity as if the activity existed on the user's home data store.</span></span>  
  
## <a name="why-use-distributed-navigation-of-activities-and-documents"></a><span data-ttu-id="a63ee-107">為何要使用活動和文件的分散式導覽？</span><span class="sxs-lookup"><span data-stu-id="a63ee-107">Why Use Distributed Navigation of Activities and Documents?</span></span>  
 <span data-ttu-id="a63ee-108">分散式的導覽可讓組織保有對部門 BAM 資料庫的控制項而不需要同意的單一位置的活動。</span><span class="sxs-lookup"><span data-stu-id="a63ee-108">Distributed navigation allows organizations to retain control of departmental BAM databases without having to agree on a single location for the activities.</span></span> <span data-ttu-id="a63ee-109">這也允許更佳的效能提高 BAM 資料庫的系統負載，在整個環境的活動。</span><span class="sxs-lookup"><span data-stu-id="a63ee-109">This also allows for better performance from your BAM databases by distributing the system load of the activities throughout your environment.</span></span>  
  
 <span data-ttu-id="a63ee-110">下圖說明分散式導覽解決商務使用者需求的實例，讓他們可以輕鬆存取由公司不同部門所管理的活動。</span><span class="sxs-lookup"><span data-stu-id="a63ee-110">The following figure illustrates a scenario in which distributed navigation addresses the needs of the business user to have easy access to activities that are managed by separate departments in a company.</span></span> <span data-ttu-id="a63ee-111">這些部門的系統管理員保有針對該部門之商務程序的控制。</span><span class="sxs-lookup"><span data-stu-id="a63ee-111">The administrators in those departments maintain control of the business processes specific to that department.</span></span>  
  
 <span data-ttu-id="a63ee-112">在此實例中，包含下列相關人員：</span><span class="sxs-lookup"><span data-stu-id="a63ee-112">In this scenario there are the following stakeholders:</span></span>  
  
-   <span data-ttu-id="a63ee-113">負責業務部門基礎結構的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="a63ee-113">An administrator who owns the infrastructure for the sales department.</span></span> <span data-ttu-id="a63ee-114">該系統管理員只負責部門資料的可用性及安全性。</span><span class="sxs-lookup"><span data-stu-id="a63ee-114">The administrator is solely responsible for the availability and security of the department’s data.</span></span>  
  
-   <span data-ttu-id="a63ee-115">擁有出貨部門基礎結構的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="a63ee-115">An administrator who owns the infrastructure for the shipping department.</span></span> <span data-ttu-id="a63ee-116">他負責滿足業務需求。</span><span class="sxs-lookup"><span data-stu-id="a63ee-116">He is responsible for meeting the needs of the sales.</span></span>  
  
-   <span data-ttu-id="a63ee-117">業務部門的商務使用者。</span><span class="sxs-lookup"><span data-stu-id="a63ee-117">A business user in the sales department.</span></span> <span data-ttu-id="a63ee-118">商務使用者可查看先前加入到檢視中的業務資料子集。</span><span class="sxs-lookup"><span data-stu-id="a63ee-118">The business user sees subsets of the sales data that are included in the views to which the user has been added.</span></span> <span data-ttu-id="a63ee-119">這些檢視是由授與商務使用者檢視存取權的系統管理員所建立。</span><span class="sxs-lookup"><span data-stu-id="a63ee-119">The views are created by the administrator who grants the business user access to the view.</span></span> <span data-ttu-id="a63ee-120">商務使用者的主要商務檢視為其所參與的「訂單」活動。</span><span class="sxs-lookup"><span data-stu-id="a63ee-120">The business user's primary view of the business is the Purchase Order activity in which she participates.</span></span> <span data-ttu-id="a63ee-121">會將該使用者設定為檢視業務部門系統管理員所維護之 BAM 入口網站的首頁。</span><span class="sxs-lookup"><span data-stu-id="a63ee-121">This user is set up to view the home page of the BAM portal maintained by the administrator of the sales department.</span></span>  
  
 <span data-ttu-id="a63ee-122">**在 BAM 中使用分散式的導覽**</span><span class="sxs-lookup"><span data-stu-id="a63ee-122">**Using Distributed Navigation in BAM**</span></span>  
  
 <span data-ttu-id="a63ee-123">![分散式導覽實例。] (../core/media/bcd-distrbuted-nav-scenario.gif "bcd_distrbuted_nav_scenario")</span><span class="sxs-lookup"><span data-stu-id="a63ee-123">![Distrbuted navigation scenario.](../core/media/bcd-distrbuted-nav-scenario.gif "bcd_distrbuted_nav_scenario")</span></span>  
  
 <span data-ttu-id="a63ee-124">系統管理員會想要將其伺服器盡可能設為彼此獨立，如以下說明：</span><span class="sxs-lookup"><span data-stu-id="a63ee-124">The administrators want to configure their servers to be as independent as possible, as follows:</span></span>  
  
-   <span data-ttu-id="a63ee-125">業務部門的系統管理員不希望在出貨部門基礎結構當機時，確認訂單作業就無法進行，或是其商務使用者的查詢功能受到影響。</span><span class="sxs-lookup"><span data-stu-id="a63ee-125">The sales department administrator does not want the acceptance of the orders to stop or the query functionality for his business users to be affected if the shipping department infrastructure is down.</span></span>  
  
-   <span data-ttu-id="a63ee-126">出貨部門的系統管理員也不想讓其部門被業務部門的效能問題拖累。</span><span class="sxs-lookup"><span data-stu-id="a63ee-126">The shipping department administrator does not want his department to be affected by performance problems in the sales department.</span></span> <span data-ttu-id="a63ee-127">他希望他的商務使用者即使在系統無法提供業務部門資訊時，仍然能夠繼續往下執行出貨流程。</span><span class="sxs-lookup"><span data-stu-id="a63ee-127">He wants his business users to be able to follow the progress of the shipments, even if the sales department is unavailable.</span></span>  
  
 <span data-ttu-id="a63ee-128">分散式導覽的目的，就是讓商務使用者可以存取他們擁有權限的每個檢視。</span><span class="sxs-lookup"><span data-stu-id="a63ee-128">The goal of distributed navigation is to provide the business end user with access to every view to which they have permissions.</span></span>  
  
 <span data-ttu-id="a63ee-129">例如，業務資料庫中定義了檢視 A 和 B。</span><span class="sxs-lookup"><span data-stu-id="a63ee-129">For example, views A and B are defined in the sales database.</span></span> <span data-ttu-id="a63ee-130">出貨部門定義了檢視 C。</span><span class="sxs-lookup"><span data-stu-id="a63ee-130">The shipping department has view C defined.</span></span> <span data-ttu-id="a63ee-131">商務使用者擁有檢視這些檢視的權限，且可存取業務部門專屬的 BAM 入口網站。</span><span class="sxs-lookup"><span data-stu-id="a63ee-131">The business user has permission to view all of these, and accesses the BAM portal specific to the sales department.</span></span> <span data-ttu-id="a63ee-132">讓商務使用者查看檢視 A、 B 和 C 中的**我的檢視**入口網站的框架便可達成建立從業務資料庫對出貨資料庫至少的單向信任。</span><span class="sxs-lookup"><span data-stu-id="a63ee-132">Allowing the business user to see views A, B, and C in the **MyViews** frame of the portal is accomplished by establishing at least a one-way trust from the sales database to the shipping database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a63ee-133">特定類別的商務使用者可以查看指定之資料的權限是由進階商務使用者所定義，例如管理員或分析師。</span><span class="sxs-lookup"><span data-stu-id="a63ee-133">The permissions for the category of business user that can see specified data are defined by the power business user, such as a manager or analyst.</span></span> <span data-ttu-id="a63ee-134">系統管理員只能將使用者新增至現有群組或 BAM 檢視。</span><span class="sxs-lookup"><span data-stu-id="a63ee-134">The administrators only add users to existing groups or BAM views.</span></span>  
  
 <span data-ttu-id="a63ee-135">BAM 活動的分散式導覽也可讓使用者查看和存取分散式活動關係。</span><span class="sxs-lookup"><span data-stu-id="a63ee-135">Distributed navigation of BAM activities also allows the user to see and access distributed activity relationships.</span></span> <span data-ttu-id="a63ee-136">當已使用分散式導覽建立彼此關係的兩個不同 BAM 資料庫上有活動執行個體時，遠端的相關活動就會在本機活動執行個體的活動詳細資料中顯示為相關的活動。</span><span class="sxs-lookup"><span data-stu-id="a63ee-136">When there are activity instances on two different BAM databases that have been related to each other using distributed navigation, the remote related activity is displayed as a related activity in the activity details of the local activity instance.</span></span> <span data-ttu-id="a63ee-137">按一下相關的活動，會開啟遠端入口網站上之活動的活動詳細資料頁面。</span><span class="sxs-lookup"><span data-stu-id="a63ee-137">Clicking the related activity opens the activity details page for the activity on the remote portal.</span></span> <span data-ttu-id="a63ee-138">如需相關活動的活動搜尋結果頁面，在 BAM 入口網站，請參閱[相關活動](../core/related-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="a63ee-138">For more information about the related activities of the activity search results page in the BAM portal, a see [Related Activities](../core/related-activities.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a63ee-139">若要讓每台電腦上的使用者都能看到位在不同 BAM 資料庫的相關活動，您必須在所有 BAM 資料庫之間啟用雙向分散式導覽。</span><span class="sxs-lookup"><span data-stu-id="a63ee-139">For users on each computer to see related activities located in different BAM databases, you must enable two-way distributed navigation between all the BAM databases.</span></span>  
  
 <span data-ttu-id="a63ee-140">若您在設定分散式導覽時，在兩個主要匯入資料庫間啟用單向分散式導覽，使用者在導覽時會經歷不對稱的情況。</span><span class="sxs-lookup"><span data-stu-id="a63ee-140">If you enable one-way distributed navigation between two Primary Import databases when you configure distributed navigation, users will have an asymmetrical experience during the navigation.</span></span>  
  
 <span data-ttu-id="a63ee-141">在此情況下，使用者會看到不同的活動；但是當使用者向內切入執行個體層級資料時，顯示相關執行個體的區段會是空的。</span><span class="sxs-lookup"><span data-stu-id="a63ee-141">The user experience will be such that the user will see the different activities; however, when the user drills into the instance-level data, the section where related instances are displayed will be empty.</span></span> <span data-ttu-id="a63ee-142">若要解決這個問題，您必須將分散式導覽路徑設回使用者的主機 BAM 入口網站伺服器。</span><span class="sxs-lookup"><span data-stu-id="a63ee-142">To resolve this issue, you must configure the distributed navigation path back to the home BAM portal server for the user.</span></span>  
  
 <span data-ttu-id="a63ee-143">例如，考慮下列實例：</span><span class="sxs-lookup"><span data-stu-id="a63ee-143">For example, consider the following scenario:</span></span>  
  
-   <span data-ttu-id="a63ee-144">您在「電腦 1」上有一個名為「訂單」的活動以及一個名為 SalesManager 的檢視。</span><span class="sxs-lookup"><span data-stu-id="a63ee-144">You have Computer 1 on which you have an activity called Purchase Order and a view called SalesManager.</span></span>  
  
-   <span data-ttu-id="a63ee-145">您在「電腦 2」上有一個名為「送貨單」的活動以及一個名為 SalesManager 的檢視。</span><span class="sxs-lookup"><span data-stu-id="a63ee-145">You have Computer 2 on which you have an activity called Shipping Order and a view called SalesManager</span></span>  
  
-   <span data-ttu-id="a63ee-146">您將名為 PO_1 的活動新增至「電腦 1」上的「訂單」</span><span class="sxs-lookup"><span data-stu-id="a63ee-146">You add an activity called PO_1 to Purchase Order on Computer 1</span></span>  
  
-   <span data-ttu-id="a63ee-147">您將名為 SO_1 的活動新增至「電腦 2」上的「送貨單」</span><span class="sxs-lookup"><span data-stu-id="a63ee-147">You add an activity called SO_1 to Shipping Order on Computer 2</span></span>  
  
-   <span data-ttu-id="a63ee-148">在「電腦 2」上，您在「送貨單」上新增 SO_1 與「訂單」PO_1 活動的關係</span><span class="sxs-lookup"><span data-stu-id="a63ee-148">On Computer 2 you add the relationship,  SO_1 to the PurchaseOrder PO_1 Activity on Shipping Order</span></span>  
  
-   <span data-ttu-id="a63ee-149">當使用者從「電腦 1」向下切入 SO_1 活動時，SO_1 活動是可搜尋的</span><span class="sxs-lookup"><span data-stu-id="a63ee-149">When a user drills down into the SO_1 activity from Computer 1 the SO_1 activity is discoverable</span></span>  
  
-   <span data-ttu-id="a63ee-150">如果使用者在「電腦 2」上向下切入 SO_1，則看不到 PO_1 活動</span><span class="sxs-lookup"><span data-stu-id="a63ee-150">If the user drills down the SO_1 on Computer 2, the PO_1 activity is not visible</span></span>  
  
 <span data-ttu-id="a63ee-151">若要修正這個問題，您必須在「電腦 1」上新增關係。</span><span class="sxs-lookup"><span data-stu-id="a63ee-151">To rectify this, you will need to add the relationship on Computer 1.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a63ee-152">本節內容</span><span class="sxs-lookup"><span data-stu-id="a63ee-152">In This Section</span></span>  
  
-   [<span data-ttu-id="a63ee-153">如何設定分散式活動之間的巡覽</span><span class="sxs-lookup"><span data-stu-id="a63ee-153">How to Configure Navigation Between Distributed Activities</span></span>](../core/how-to-configure-navigation-between-distributed-activities.md)  
  
## <a name="see-also"></a><span data-ttu-id="a63ee-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a63ee-154">See Also</span></span>  
 [<span data-ttu-id="a63ee-155">管理 BAM</span><span class="sxs-lookup"><span data-stu-id="a63ee-155">Managing BAM</span></span>](../core/managing-bam.md)