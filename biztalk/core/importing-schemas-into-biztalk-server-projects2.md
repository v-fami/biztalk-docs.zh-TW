---
title: "結構描述匯入到 BizTalk Server Projects2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing schemas
- schemas, importing into BizTalk Server projects
ms.assetid: 640d5884-953a-46b6-b9dc-b931392a3059
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ebb0a39850029adec06986da5ddad1fc44c33ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="importing-schemas-into-biztalk-server-projects"></a><span data-ttu-id="8b6ad-102">結構描述匯入至 BizTalk Server 專案</span><span class="sxs-lookup"><span data-stu-id="8b6ad-102">Importing Schemas into BizTalk Server Projects</span></span>
<span data-ttu-id="8b6ad-103">本節討論瀏覽 JD Edwards EnterpriseOne 伺服器，以及將結構描述匯入 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-103">This section discusses browsing a JD Edwards EnterpriseOne server and importing the schemas into a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b6ad-104">您必須確定您已設定引數清單。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-104">You must ensure that you set the arglist.</span></span> <span data-ttu-id="8b6ad-105">在協調流程中產生結構描述之前，您必須先更新 jdearglist.txt。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-105">You must update jdearglist.txt before you generate the schemas in the orchestration.</span></span> <span data-ttu-id="8b6ad-106">如需詳細資訊，請參閱[處理字串值](../core/handling-string-values2.md)。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-106">For more information, see [Handling String Values](../core/handling-string-values2.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b6ad-107">每次變更 jdearglist 時，都必須為該商務物件重新產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-107">Each time that you change the jdearglist, you must regenerate the schemas for that business object.</span></span>  
  
 <span data-ttu-id="8b6ad-108">在建立 JD Edwards EnterpriseOne 連接埠後，您可以從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案啟動 Microsoft 配接器精靈，以瀏覽 JD Edwards EnterpriseOne。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-108">After creating the JD Edwards EnterpriseOne port, you can browse JD Edwards EnterpriseOne by launching the Microsoft Adapter Wizard from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span>  
  
### <a name="to-import-schemas-into-a-biztalk-server-project"></a><span data-ttu-id="8b6ad-109">將結構描述匯入 BizTalk Server 專案</span><span class="sxs-lookup"><span data-stu-id="8b6ad-109">To import schemas into a BizTalk Server project</span></span>  
  
1.  <span data-ttu-id="8b6ad-110">開啟 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-110">Open [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="8b6ad-111">以滑鼠右鍵按一下名稱[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案，指向**新增**，然後選取**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-111">Right-click the name of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project, point to **Add**, and select **Add Generated Items**.</span></span>  
  
3.  <span data-ttu-id="8b6ad-112">按一下**新增**開啟**新增配接器精靈**。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-112">Click **Add** to open the **Add Adapter Wizard**.</span></span>  
  
4.  <span data-ttu-id="8b6ad-113">在**選取配接器**頁面上，選取您要匯入結構描述的配接器名稱 (例如， **JDEEnterpriseOne**)。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-113">On the **Select Adapter** page, select the name of the adapter for which you want to import schemas (for example, **JDEEnterpriseOne**).</span></span>  
  
5.  <span data-ttu-id="8b6ad-114">在**SQL Server**方塊中，選取 SQL server。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-114">In the **SQL Server** box, select a SQL server.</span></span>  
  
6.  <span data-ttu-id="8b6ad-115">在**資料庫**方塊中，選取資料庫。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-115">In the **Database** box, select a database.</span></span>  
  
     <span data-ttu-id="8b6ad-116">預設的資料庫和 SQL Server 的相同。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-116">The default database is the same one as your SQL server.</span></span>  
  
7.  <span data-ttu-id="8b6ad-117">在**連接埠**，選取 SQL server，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-117">In the **Port** box, select a SQL server, and then click **Next**.</span></span>  
  
     <span data-ttu-id="8b6ad-118">JD Edwards EnterpriseOne 系統就會顯示在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-118">The JD Edwards EnterpriseOne system displays in the browser.</span></span>  
  
8.  <span data-ttu-id="8b6ad-119">繼續下一個程序。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-119">Continue with the next procedure below.</span></span>  
  
 <span data-ttu-id="8b6ad-120">「新增配接器精靈」會顯示含有所有已定義系統的樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-120">The Add Adapter Wizard displays a tree of all of the defined systems.</span></span> <span data-ttu-id="8b6ad-121">JD Edwards EnterpriseOne 有許多模組。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-121">JD Edwards EnterpriseOne has many modules.</span></span> <span data-ttu-id="8b6ad-122">模組會依據名稱中的前三個字元分組。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-122">The modules are grouped together according to the first three characters of their name.</span></span>  
  
-   <span data-ttu-id="8b6ad-123">階層的第一層是模組名稱所有三個字元的首碼清單。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-123">The first level of the hierarchy is the list of all three-character prefixes for the module names.</span></span>  
  
-   <span data-ttu-id="8b6ad-124">第二層列示共用相同的三個字元首碼的所有模組。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-124">The second level lists all the modules that share the same three-character prefix.</span></span>  
  
-   <span data-ttu-id="8b6ad-125">最後一層列示屬於模組的商務功能。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-125">The last level lists the business functions belonging to a module.</span></span> <span data-ttu-id="8b6ad-126">當您展開服務圖示時，就能檢視它的作業。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-126">When you expand the services icon, you can view its operations.</span></span>  
  
 <span data-ttu-id="8b6ad-127">展開作業會顯示輸入/輸出引數。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-127">Expanding an operation displays the input/output arguments.</span></span> <span data-ttu-id="8b6ad-128">您可以展開輸入/輸出引數以檢視引數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-128">You can expand the input/output arguments to view the data types of the arguments.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b6ad-129">如果伺服器物件定義變更，您必須重新產生結構描述以重新整理其中包含的資料。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-129">If the server object definitions change, you must regenerate the schema to refresh the data it contains.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b6ad-130">如果您在產生結構描述後變更 jdearglist.txt，您必須重新產生結構描述以重新整理所包含的資料。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-130">If you change jdearglist.txt after generating your schema, you must regenerate the schema to refresh the data it contains.</span></span> <span data-ttu-id="8b6ad-131">如需 jdearglist.txt 的相關詳細資訊，請參閱[處理字串值](../core/handling-string-values2.md)。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-131">For more information on jdearglist.txt, see [Handling String Values](../core/handling-string-values2.md).</span></span>  
  
### <a name="to-select-the-schemas"></a><span data-ttu-id="8b6ad-132">選取結構描述</span><span class="sxs-lookup"><span data-stu-id="8b6ad-132">To select the schemas</span></span>  
  
1.  <span data-ttu-id="8b6ad-133">在**選取要匯入服務**頁面上，展開最上層節點**商務物件**節點或**商務服務**節點。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-133">In the **Select Services to Import** page, expand the top level node of the **Business Objects** node or the **Business Services** node.</span></span>  
  
2.  <span data-ttu-id="8b6ad-134">選取您想要匯入，然後按一下的項目旁的核取方塊**確定**。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-134">Select the check box next to the items that you want to import, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="8b6ad-135">針對所選 JD Edwards EnterpriseOne 項目產生的結構描述就會匯入 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-135">Schemas generated for the selected JD Edwards EnterpriseOne items are imported into your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b6ad-136">使用 AddressBook (N0100041) 時，欄位名稱為**cActionCode**。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-136">When using AddressBook (N0100041) the field name is **cActionCode**.</span></span> <span data-ttu-id="8b6ad-137">動作是 XML 檔案本身的一部分。</span><span class="sxs-lookup"><span data-stu-id="8b6ad-137">The action is part of the XML file itself.</span></span> <span data-ttu-id="8b6ad-138">程式碼為：</span><span class="sxs-lookup"><span data-stu-id="8b6ad-138">The codes are:</span></span>  
  
-   <span data-ttu-id="8b6ad-139">A 表示新增</span><span class="sxs-lookup"><span data-stu-id="8b6ad-139">A for Add</span></span>  
  
-   <span data-ttu-id="8b6ad-140">C 表示變更</span><span class="sxs-lookup"><span data-stu-id="8b6ad-140">C for Change</span></span>  
  
-   <span data-ttu-id="8b6ad-141">D 表示刪除</span><span class="sxs-lookup"><span data-stu-id="8b6ad-141">D for Delete</span></span>  
  
-   <span data-ttu-id="8b6ad-142">I 表示查詢</span><span class="sxs-lookup"><span data-stu-id="8b6ad-142">I for Inquiry</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b6ad-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b6ad-143">See Also</span></span>  
 [<span data-ttu-id="8b6ad-144">建立 JD Edwards EnterpriseOne 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="8b6ad-144">Creating JD Edwards EnterpriseOne Send Handlers</span></span>](../core/creating-jd-edwards-enterpriseone-send-handlers.md)