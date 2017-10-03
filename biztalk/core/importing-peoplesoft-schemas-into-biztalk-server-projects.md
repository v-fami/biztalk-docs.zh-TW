---
title: "PeopleSoft 結構描述匯入至 BizTalk Server 專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generating schemas
- schemas, generating
- schemas, importing into BizTalk Server projects
- component interfaces
- BizTalk Server, schemas [PeopleSoft]
- importing schemas into BizTalk Server
ms.assetid: 411f25f4-4431-44e4-84cf-5c515b3e32db
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b4946b438adc0d1e4d360b35207ff69e85b4e2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="importing-peoplesoft-schemas-into-biztalk-server-projects"></a><span data-ttu-id="de4ae-102">將 PeopleSoft 結構描述匯入至 BizTalk Server 專案</span><span class="sxs-lookup"><span data-stu-id="de4ae-102">Importing PeopleSoft Schemas into BizTalk Server Projects</span></span>
<span data-ttu-id="de4ae-103">當您建立 PeopleSoft Enterprise 系統後，可以瀏覽伺服器並將結構描述匯入至 BizTalk Server 專案。</span><span class="sxs-lookup"><span data-stu-id="de4ae-103">When you have created the PeopleSoft Enterprise system, you can browse the server and import schemas into a BizTalk Server project.</span></span>  
  
## <a name="browsing-a-peoplesoft-server-system"></a><span data-ttu-id="de4ae-104">瀏覽 PeopleSoft Server 系統</span><span class="sxs-lookup"><span data-stu-id="de4ae-104">Browsing a PeopleSoft Server System</span></span>  
 <span data-ttu-id="de4ae-105">使用「配接器精靈」瀏覽 PeopleSoft 伺服器。</span><span class="sxs-lookup"><span data-stu-id="de4ae-105">Use the Adapter Wizard to browse a PeopleSoft server.</span></span>  
  
#### <a name="to-browse-a-peoplesoft-server-system"></a><span data-ttu-id="de4ae-106">瀏覽 PeopleSoft 伺服器系統</span><span class="sxs-lookup"><span data-stu-id="de4ae-106">To browse a PeopleSoft server system</span></span>  
  
1.  <span data-ttu-id="de4ae-107">使用滑鼠右鍵按一下 BizTalk Server 專案，然後選取下列其中一個選項。</span><span class="sxs-lookup"><span data-stu-id="de4ae-107">Right-click a BizTalk Server project, and select one of the following options.</span></span>  
  
    -   <span data-ttu-id="de4ae-108">如果您已經有產生物件的結構描述，選取**新增**，按一下 **新增結構描述**，然後選取 現有的結構描述，將新增至您的協調流程。</span><span class="sxs-lookup"><span data-stu-id="de4ae-108">If you already have a schema generated for your object, select **Add**, click **Add Schema,** and then select the existing schema to add to your orchestration,.</span></span>  
  
    -   <span data-ttu-id="de4ae-109">如果您沒有為物件產生的結構描述，選取**新增**，然後按一下 **新增產生的項目**，然後選取 配接器。</span><span class="sxs-lookup"><span data-stu-id="de4ae-109">If you do not have a schema generated for your object, select **Add**, then click **Add Generated Items**, and then select the adapter.</span></span> <span data-ttu-id="de4ae-110">這是相同的名稱中輸入**AdapterProperties**  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="de4ae-110">This is the same name entered in the **AdapterProperties** dialog box.</span></span> <span data-ttu-id="de4ae-111">如需詳細資訊，請參閱 BizTalk 主要說明中的＜配接器屬性對話方塊＞。</span><span class="sxs-lookup"><span data-stu-id="de4ae-111">For more information, see "Adapter Properties Dialog Box" in the main BizTalk help.</span></span>  
  
2.  <span data-ttu-id="de4ae-112">按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="de4ae-112">Click Next.</span></span>  
  
     <span data-ttu-id="de4ae-113">PeopleSoft Enterprise 系統就會顯示於瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="de4ae-113">The PeopleSoft Enterprise system appears in the browser.</span></span>  
  
     ![](../core/media/psad-psnewadapter-14-browsing-cominterfacess.gif "PSAd_PSNewAdapter_14_Browsing_ComInterfacess")  
  
### <a name="component-interfaces"></a><span data-ttu-id="de4ae-114">元件介面</span><span class="sxs-lookup"><span data-stu-id="de4ae-114">Component Interfaces</span></span>  
 <span data-ttu-id="de4ae-115">在**元件介面**(CI) 資料夾中，您可以檢視所有可用的元件介面，在系統中。</span><span class="sxs-lookup"><span data-stu-id="de4ae-115">In the **Component Interfaces** (CI) folder, you can view all the available component interfaces in the system.</span></span> <span data-ttu-id="de4ae-116">元件介面會宣告它所支援的方法和屬性集合。</span><span class="sxs-lookup"><span data-stu-id="de4ae-116">A component interface declares the set of methods and properties that it supports.</span></span> <span data-ttu-id="de4ae-117">元件介面不會實作行為或屬性。</span><span class="sxs-lookup"><span data-stu-id="de4ae-117">A component interface does not implement behavior or properties.</span></span> <span data-ttu-id="de4ae-118">Microsoft BizTalk Adapter for PeopleSoft Enterprise 公開標準方法，例如 CreateEx、DeleteOnly、Find、Get 與 UpdateEx。</span><span class="sxs-lookup"><span data-stu-id="de4ae-118">Microsoft BizTalk Adapter for PeopleSoft Enterprise exposes standard methods, for example, CreateEx, DeleteOnly, Find, Get, and UpdateEx.</span></span> <span data-ttu-id="de4ae-119">如需這些方法的說明，請參閱[附錄 a： 元件介面方法](../core/appendix-a-component-interface-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="de4ae-119">For a description of these methods, see [Appendix A: Component Interface Methods](../core/appendix-a-component-interface-methods.md).</span></span>  
  
## <a name="generating-schemas"></a><span data-ttu-id="de4ae-120">產生結構描述</span><span class="sxs-lookup"><span data-stu-id="de4ae-120">Generating Schemas</span></span>  
 <span data-ttu-id="de4ae-121">依照下列步驟產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="de4ae-121">Follow these steps to generate schemas.</span></span>  
  
#### <a name="to-generate-the-schemas"></a><span data-ttu-id="de4ae-122">產生結構描述</span><span class="sxs-lookup"><span data-stu-id="de4ae-122">To generate the schemas</span></span>  
  
-   <span data-ttu-id="de4ae-123">選取您要匯入結構描述的項目：**訊息**，**查詢**，或**元件介面**。</span><span class="sxs-lookup"><span data-stu-id="de4ae-123">Select the item for which you want to import schemas: a **Message**, **Query**, or **Component Interface**.</span></span>  
  
     <span data-ttu-id="de4ae-124">BizTalk Server 會為選取的項目產生結構描述，並將它們匯入至 BizTalk Server 專案。</span><span class="sxs-lookup"><span data-stu-id="de4ae-124">BizTalk Server generates the schemas for the selected item and imports them into a BizTalk Server project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="de4ae-125">如果伺服器物件定義變更，您必須重新產生結構描述以更新其中包含的資料。</span><span class="sxs-lookup"><span data-stu-id="de4ae-125">If the server object definitions change, you must regenerate the schema to update the data it contains.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de4ae-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de4ae-126">See Also</span></span>  
 [<span data-ttu-id="de4ae-127">建立 PeopleSoft 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="de4ae-127">Creating PeopleSoft Send Handlers</span></span>](../core/creating-peoplesoft-send-handlers.md)