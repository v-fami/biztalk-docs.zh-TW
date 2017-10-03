---
title: "JD Edwards OneWorld 結構描述匯入至 BizTalk Server 專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generating schemas
- importing schemas
- schemas, generating
- schemas, importing into BizTalk Server projects
ms.assetid: 5bcaa276-8c76-4212-b373-de86e3008a69
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35b0d7fec5acc991ae6c141f57297b7511281be3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="importing-jd-edwards-oneworld-schemas-into-biztalk-server-projects"></a><span data-ttu-id="1f28e-102">將 JD Edwards OneWorld 結構描述匯入至 BizTalk Server 專案</span><span class="sxs-lookup"><span data-stu-id="1f28e-102">Importing JD Edwards OneWorld Schemas into BizTalk Server Projects</span></span>
<span data-ttu-id="1f28e-103">本主題討論瀏覽 JD Edwards OneWorld 伺服器，以及將結構描述匯入 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="1f28e-103">This topic discusses browsing a JD Edwards OneWorld server and importing the schemas into a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f28e-104">您必須確定您已設定引數清單。</span><span class="sxs-lookup"><span data-stu-id="1f28e-104">You must ensure that you set the arglist.</span></span> <span data-ttu-id="1f28e-105">在協調流程中產生結構描述之前，您必須先更新 jdearglist.txt。</span><span class="sxs-lookup"><span data-stu-id="1f28e-105">You must update the jdearglist.txt before you generate the schemas in the orchestration.</span></span> <span data-ttu-id="1f28e-106">如需詳細資訊，請參閱[處理字串值](../core/handling-string-values1.md)。</span><span class="sxs-lookup"><span data-stu-id="1f28e-106">For more information, see [Handling String Values](../core/handling-string-values1.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f28e-107">每次變更 jdearglist 時，都必須為該商務物件重新產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="1f28e-107">Each time that you change the jdearglist, you must regenerate the schemas for that business object.</span></span>  
  
 <span data-ttu-id="1f28e-108">在建立 JD Edwards OneWorld 邏輯系統後，您可以從 BizTalk Server 專案開啟 Microsoft 配接器精靈，以瀏覽 JD Edwards OneWorld。</span><span class="sxs-lookup"><span data-stu-id="1f28e-108">After creating the JD Edwards OneWorld logical system, you can browse JD Edwards OneWorld by opening the Microsoft Adapter Wizard from a BizTalk Server project.</span></span>  
  
### <a name="to-import-schemas"></a><span data-ttu-id="1f28e-109">若要匯入結構描述</span><span class="sxs-lookup"><span data-stu-id="1f28e-109">To import schemas</span></span>  
  
1.  <span data-ttu-id="1f28e-110">開啟 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1f28e-110">Open [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="1f28e-111">以滑鼠右鍵按一下[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案，指向**新增**，然後選取**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="1f28e-111">Right-click the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project, point to **Add**, and select **Add Generated Items**.</span></span>  
  
3.  <span data-ttu-id="1f28e-112">按一下**新增配接器**，然後選取**開啟**。</span><span class="sxs-lookup"><span data-stu-id="1f28e-112">Click **Add adapter**, and select **Open**.</span></span>  
  
4.  <span data-ttu-id="1f28e-113">選取配接器，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="1f28e-113">Select the adapter, and click **Next**.</span></span>  
  
     <span data-ttu-id="1f28e-114">JD.</span><span class="sxs-lookup"><span data-stu-id="1f28e-114">The JD.</span></span> <span data-ttu-id="1f28e-115">Edwards OneWorld XE 系統就會顯示在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="1f28e-115">Edwards OneWorld XE system appears in the browser.</span></span>  
  
     ![](../core/media/jdedadapter-04-jdebrowse.gif "JDEdAdapter_04_JDEBrowse")  
  
     <span data-ttu-id="1f28e-116">配接器精靈會顯示含有所有已定義系統的樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="1f28e-116">The Adapter Wizard displays a tree of all of the defined systems.</span></span> <span data-ttu-id="1f28e-117">JD Edwards OneWorld 的模組太多，無法在一個長清單中顯示。</span><span class="sxs-lookup"><span data-stu-id="1f28e-117">JD Edwards OneWorld has too many modules to show in one long list.</span></span> <span data-ttu-id="1f28e-118">模組會依據名稱中的前三個字元分組。</span><span class="sxs-lookup"><span data-stu-id="1f28e-118">The modules are grouped together according to the first three characters of their name.</span></span>  
  
    -   <span data-ttu-id="1f28e-119">階層的第一層是模組名稱所有三個字元的首碼清單。</span><span class="sxs-lookup"><span data-stu-id="1f28e-119">The first level of the hierarchy is the list of all three-character prefixes for the module names.</span></span>  
  
    -   <span data-ttu-id="1f28e-120">第二層列示共用相同的三個字元首碼的所有模組。</span><span class="sxs-lookup"><span data-stu-id="1f28e-120">The second level lists all the modules that share the same three-character prefix.</span></span>  
  
    -   <span data-ttu-id="1f28e-121">最後一層列示屬於模組的商務功能。</span><span class="sxs-lookup"><span data-stu-id="1f28e-121">The last level lists the business functions belonging to a module.</span></span> <span data-ttu-id="1f28e-122">當您展開服務圖示時，就能檢視它的作業。</span><span class="sxs-lookup"><span data-stu-id="1f28e-122">When you expand the services icon you can view its operations.</span></span>  
  
     <span data-ttu-id="1f28e-123">展開作業會顯示輸入/輸出引數。</span><span class="sxs-lookup"><span data-stu-id="1f28e-123">Expanding an operation displays the input/output arguments.</span></span>  
  
     <span data-ttu-id="1f28e-124">您可以展開輸入/輸出引數以檢視引數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="1f28e-124">You can expand the input/output arguments to view the data types of the arguments.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1f28e-125">如果伺服器物件定義變更，您必須重新產生結構描述以重新整理其中包含的資料。</span><span class="sxs-lookup"><span data-stu-id="1f28e-125">If the server object definitions change, you must regenerate the schema to refresh the data it contains.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1f28e-126">如果您在產生結構描述後變更 jdearglist.txt，您必須重新產生結構描述以重新整理所包含的資料。</span><span class="sxs-lookup"><span data-stu-id="1f28e-126">If you change jdearglist.txt after generating your schema, you must regenerate the schema to refresh the data it contains.</span></span> <span data-ttu-id="1f28e-127">如需 jdearglist.txt 的相關資訊，請參閱[處理字串值](../core/handling-string-values1.md)。</span><span class="sxs-lookup"><span data-stu-id="1f28e-127">For information on jdearglist.txt, see to [Handling String Values](../core/handling-string-values1.md).</span></span>  
  
## <a name="generating-schemas"></a><span data-ttu-id="1f28e-128">產生結構描述</span><span class="sxs-lookup"><span data-stu-id="1f28e-128">Generating Schemas</span></span>  
 <span data-ttu-id="1f28e-129">使用下列程序產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="1f28e-129">Use the following procedure to generate schemas.</span></span>  
  
#### <a name="to-generate-schemas"></a><span data-ttu-id="1f28e-130">產生結構描述</span><span class="sxs-lookup"><span data-stu-id="1f28e-130">To generate schemas</span></span>  
  
1.  <span data-ttu-id="1f28e-131">選取要匯入結構描述的項目。</span><span class="sxs-lookup"><span data-stu-id="1f28e-131">Select the item for which you want to import schemas.</span></span>  
  
2.  <span data-ttu-id="1f28e-132">按一下 （或拖曳） 將項目加入**傳輸**窗格 （針對 J.Edwards OneWorld 的輸入呼叫）。</span><span class="sxs-lookup"><span data-stu-id="1f28e-132">Click (or drag) to add the item to the **Transmit** pane (for an inbound to J. Edwards OneWorld call).</span></span>  
  
3.  <span data-ttu-id="1f28e-133">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="1f28e-133">Click **OK**.</span></span>  
  
     <span data-ttu-id="1f28e-134">針對所選 JD Edwards OneWorld 項目產生的結構描述就會匯入 BizTalk Server 專案。</span><span class="sxs-lookup"><span data-stu-id="1f28e-134">Schemas generated for the selected JD Edwards OneWorld item are imported into the BizTalk Server project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f28e-135">使用 AddressBook (N0100041) 時，欄位名稱為**cActionCode**。</span><span class="sxs-lookup"><span data-stu-id="1f28e-135">When using AddressBook (N0100041) the field name is **cActionCode**.</span></span> <span data-ttu-id="1f28e-136">動作是 XML 檔案本身的一部分。</span><span class="sxs-lookup"><span data-stu-id="1f28e-136">The action is part of the XML file itself.</span></span> <span data-ttu-id="1f28e-137">程式碼為：</span><span class="sxs-lookup"><span data-stu-id="1f28e-137">The codes are:</span></span>  
>   
>  <span data-ttu-id="1f28e-138">--A 表示新增</span><span class="sxs-lookup"><span data-stu-id="1f28e-138">--A for Add</span></span>  
>   
>  <span data-ttu-id="1f28e-139">--C 表示變更</span><span class="sxs-lookup"><span data-stu-id="1f28e-139">--C for Change</span></span>  
>   
>  <span data-ttu-id="1f28e-140">--D 表示刪除</span><span class="sxs-lookup"><span data-stu-id="1f28e-140">--D for Delete</span></span>  
>   
>  <span data-ttu-id="1f28e-141">--I 表示查詢</span><span class="sxs-lookup"><span data-stu-id="1f28e-141">--I for Inquiry</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f28e-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f28e-142">See Also</span></span>  
 [<span data-ttu-id="1f28e-143">建立 JD Edwards OneWorld 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="1f28e-143">Creating JD Edwards OneWorld Send Handlers</span></span>](../core/creating-jd-edwards-oneworld-send-handlers.md)