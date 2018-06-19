---
title: 如何判斷和設定活動事件寫入者角色 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73bfe8ff-167a-4bf0-ab87-3926290d52d8
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc9fa663d395fc36205e137da374f17cb9470521
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249862"
---
# <a name="how-to-determine-and-set-event-writer-roles-for-activities"></a><span data-ttu-id="c4088-102">如何判斷和設定活動的事件寫入者角色</span><span class="sxs-lookup"><span data-stu-id="c4088-102">How to Determine and Set Event Writer Roles for Activities</span></span>
<span data-ttu-id="c4088-103">在寫入活動的事件時，BAM 提供兩種安全性模式。</span><span class="sxs-lookup"><span data-stu-id="c4088-103">BAM provides two modes of security when writing events on activities.</span></span> <span data-ttu-id="c4088-104">您可以授與個別活動的寫入事件權限，或授與所有已部署活動的寫入事件權限。</span><span class="sxs-lookup"><span data-stu-id="c4088-104">You can grant permissions to write events on individual activities or you can grant permissions to write events on all deployed activities.</span></span>  
  
 <span data-ttu-id="c4088-105">活動層級的安全性是由活動事件寫入者角色提供，當您部署 BAM 定義時可建立這些角色。</span><span class="sxs-lookup"><span data-stu-id="c4088-105">Activity-level security is provided by activity event writer roles that are created when you deploy a BAM definition.</span></span> <span data-ttu-id="c4088-106">例如，如果您針對名為 CreditCard 的活動部署定義，BAM 就會建立名為 bam_CreditCard_EventWriter 的事件寫入者角色。</span><span class="sxs-lookup"><span data-stu-id="c4088-106">For example, if you deploy a definition for an activity named CreditCard, BAM creates an event writer role named bam_CreditCard_EventWriter.</span></span> <span data-ttu-id="c4088-107">這個角色有寫入此活動之事件的權限。</span><span class="sxs-lookup"><span data-stu-id="c4088-107">This role has permissions to write events for the activity.</span></span> <span data-ttu-id="c4088-108">若要授與使用者寫入此活動之事件的權限，您可以將使用者加入至此角色。</span><span class="sxs-lookup"><span data-stu-id="c4088-108">To grant a user permissions to write events for the activity, you add the user to the role.</span></span>  
  
 <span data-ttu-id="c4088-109">或者，您可以授與使用者的寫入權限 eve2nts 所有活動新增到超級角色 BAM_EVENT_WRITER，已寫入所有活動的權限。</span><span class="sxs-lookup"><span data-stu-id="c4088-109">Alternatively, you can grant users rights to write eve2nts to all activities by adding them to the super role BAM_EVENT_WRITER, which has permissions to write to all activities.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c4088-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="c4088-110">Prerequisites</span></span>  
 <span data-ttu-id="c4088-111">若要執行此程序，您必須有下列項目：</span><span class="sxs-lookup"><span data-stu-id="c4088-111">To perform this procedure, you must have the following:</span></span>  
  
-   <span data-ttu-id="c4088-112">連線到已部署活動的 BAMPrimaryImportDb。</span><span class="sxs-lookup"><span data-stu-id="c4088-112">A connection to BAMPrimaryImportDb on which the activity is deployed.</span></span>  
  
-   <span data-ttu-id="c4088-113">在資料庫上的 DBO 權限。</span><span class="sxs-lookup"><span data-stu-id="c4088-113">DBO permissions on the database.</span></span>  
  
### <a name="to-add-a-user-to-an-event-writer-role"></a><span data-ttu-id="c4088-114">若要將使用者加入至事件寫入者角色</span><span class="sxs-lookup"><span data-stu-id="c4088-114">To add a user to an event writer role</span></span>  
  
1.  <span data-ttu-id="c4088-115">按一下**啟動**，指向 **所有程式**，按一下  **Microsoft SQL Server 2008**，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="c4088-115">Click **Start**, point to **All Programs**, click **Microsoft SQL Server 2008**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="c4088-116">在**連接到 SQL Server**對話方塊中，選取 SQL Server 和適當的驗證方法，，然後按一下**連接**。</span><span class="sxs-lookup"><span data-stu-id="c4088-116">In the **Connect to SQL Server** dialog box, select the SQL Server and the appropriate authentication method, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="c4088-117">在**物件總管 中**窗格中展開**資料庫**，然後選取 BAM 主要匯入資料庫。</span><span class="sxs-lookup"><span data-stu-id="c4088-117">In the **Object Explorer** pane expand **Databases**, and then select the BAM Primary Import database.</span></span>  
  
4.  <span data-ttu-id="c4088-118">按一下**新查詢**工具列上的圖示。</span><span class="sxs-lookup"><span data-stu-id="c4088-118">Click the **New Query** icon on the toolbar.</span></span>  
  
5.  <span data-ttu-id="c4088-119">複製下列命令並將它們貼入 [查詢視窗]。</span><span class="sxs-lookup"><span data-stu-id="c4088-119">Copy the following commands and paste them into the Query Window.</span></span> <span data-ttu-id="c4088-120">用適當值取代網域名稱、使用者名稱和活動名稱預留位置。</span><span class="sxs-lookup"><span data-stu-id="c4088-120">Replace the domain name, user name, and activity name placeholders with the appropriate values.</span></span>  
  
    ```  
    EXEC sp_grantlogin '<domain name>\<user name>’  
    EXEC sp_grantdbaccess '<domain name>\<user name>', 'ActivityLogin'  
    EXEC sp_addrolemember 'bam_<activity name>_EventWriter', 'SpecialLogin'  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c4088-121">角色名稱區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="c4088-121">Role names are case-sensitive.</span></span> <span data-ttu-id="c4088-122">活動名稱也區分大小寫，也就是說，它們必須符合在部署活動時使用的大小寫。</span><span class="sxs-lookup"><span data-stu-id="c4088-122">Activity names are also case-sensitive, that is, they must match the case used when deploying the activity.</span></span>  
  
6.  <span data-ttu-id="c4088-123">按一下**Execute**圖示的工具列或按 f5 鍵執行命令。</span><span class="sxs-lookup"><span data-stu-id="c4088-123">Click the **Execute** icon on the toolbar or press F5 to run the commands.</span></span>  
  
### <a name="to-add-a-user-to-an-event-writer-super-role"></a><span data-ttu-id="c4088-124">若要將使用者加入至事件寫入者超級角色</span><span class="sxs-lookup"><span data-stu-id="c4088-124">To add a user to an event writer super role</span></span>  
  
1.  <span data-ttu-id="c4088-125">按一下**啟動**，指向 **所有程式**，按一下  **Microsoft SQL Server 2008**，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="c4088-125">Click **Start**, point to **All Programs**, click **Microsoft SQL Server 2008**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="c4088-126">在**連接到 SQL Server**對話方塊中，選取 SQL Server 和適當的驗證方法，，然後按一下**連接**。</span><span class="sxs-lookup"><span data-stu-id="c4088-126">In the **Connect to SQL Server** dialog box, select the SQL Server and the appropriate authentication method, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="c4088-127">在**物件總管 中**窗格中展開**資料庫**，然後選取 BAM 主要匯入資料庫。</span><span class="sxs-lookup"><span data-stu-id="c4088-127">In the **Object Explorer** pane expand **Databases**, and then select the BAM Primary Import database.</span></span>  
  
4.  <span data-ttu-id="c4088-128">按一下**新查詢**工具列上的圖示。</span><span class="sxs-lookup"><span data-stu-id="c4088-128">Click the **New Query** icon on the toolbar.</span></span>  
  
5.  <span data-ttu-id="c4088-129">複製下列命令並將它們貼入 [查詢視窗]。</span><span class="sxs-lookup"><span data-stu-id="c4088-129">Copy the following commands and paste them into the Query Window.</span></span> <span data-ttu-id="c4088-130">用適當的值取代網域名稱和使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="c4088-130">Replace the domain name and user name with the appropriate values.</span></span>  
  
    ```  
    EXEC sp_grantlogin '<domain name>\<user name>’  
    EXEC sp_grantdbaccess '<domain name>\<user name>', 'ActivityLogin'  
    EXEC sp_addrolemember 'BAM_EVENT_WRITER', 'SpecialLogin'  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c4088-131">角色名稱區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="c4088-131">Role names are case sensitive.</span></span> <span data-ttu-id="c4088-132">您必須依照指示來指定事件寫入者角色。</span><span class="sxs-lookup"><span data-stu-id="c4088-132">You must specify the event writer role as specified.</span></span>  
  
6.  <span data-ttu-id="c4088-133">按一下**Execute**圖示的工具列或按 f5 鍵執行命令。</span><span class="sxs-lookup"><span data-stu-id="c4088-133">Click the **Execute** icon on the toolbar or press F5 to run the commands.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4088-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4088-134">See Also</span></span>  
 [<span data-ttu-id="c4088-135">管理 BAM 安全性</span><span class="sxs-lookup"><span data-stu-id="c4088-135">Managing BAM Security</span></span>](../core/managing-bam-security.md)