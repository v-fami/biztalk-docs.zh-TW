---
title: "將 PeopleSoft 結構描述匯入 Visual Studio |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 411f25f4-4431-44e4-84cf-5c515b3e32db
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6af82459f8b51f3dfa73a52593db18d25365c2a
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="import-peoplesoft-schemas-into-biztalk-server-projects"></a><span data-ttu-id="4c015-102">PeopleSoft 結構描述匯入至 BizTalk Server 專案</span><span class="sxs-lookup"><span data-stu-id="4c015-102">Import PeopleSoft Schemas into BizTalk Server Projects</span></span>
<span data-ttu-id="4c015-103">當您建立 PeopleSoft Enterprise 系統後，可以瀏覽伺服器並將結構描述匯入至 BizTalk Server 專案。</span><span class="sxs-lookup"><span data-stu-id="4c015-103">When you have created the PeopleSoft Enterprise system, you can browse the server and import schemas into a BizTalk Server project.</span></span>  
  
## <a name="browse-a-peoplesoft-server-system"></a><span data-ttu-id="4c015-104">瀏覽 PeopleSoft 伺服器系統</span><span class="sxs-lookup"><span data-stu-id="4c015-104">Browse a PeopleSoft Server System</span></span>  
  
1.  <span data-ttu-id="4c015-105">使用滑鼠右鍵按一下 BizTalk Server 專案，然後選取下列其中一個選項。</span><span class="sxs-lookup"><span data-stu-id="4c015-105">Right-click a BizTalk Server project, and select one of the following options.</span></span>  
  
    -   <span data-ttu-id="4c015-106">如果您已經有產生物件的結構描述，選取**新增**，按一下 **新增結構描述**，然後選取 現有的結構描述，將新增至您的協調流程。</span><span class="sxs-lookup"><span data-stu-id="4c015-106">If you already have a schema generated for your object, select **Add**, click **Add Schema,** and then select the existing schema to add to your orchestration,.</span></span>  
  
    -   <span data-ttu-id="4c015-107">如果您沒有為物件產生的結構描述，選取**新增**，然後按一下 **新增產生的項目**，然後選取 配接器。</span><span class="sxs-lookup"><span data-stu-id="4c015-107">If you do not have a schema generated for your object, select **Add**, then click **Add Generated Items**, and then select the adapter.</span></span> <span data-ttu-id="4c015-108">這是相同的名稱中輸入**AdapterProperties**  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4c015-108">This is the same name entered in the **AdapterProperties** dialog box.</span></span> <span data-ttu-id="4c015-109">如需詳細資訊，請參閱 BizTalk 主要說明中的＜配接器屬性對話方塊＞。</span><span class="sxs-lookup"><span data-stu-id="4c015-109">For more information, see "Adapter Properties Dialog Box" in the main BizTalk help.</span></span>  
  
2.  <span data-ttu-id="4c015-110">按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="4c015-110">Click Next.</span></span>  
  
     <span data-ttu-id="4c015-111">PeopleSoft Enterprise 系統就會顯示於瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="4c015-111">The PeopleSoft Enterprise system appears in the browser.</span></span>  
  
     ![](../core/media/psad-psnewadapter-14-browsing-cominterfacess.gif "PSAd_PSNewAdapter_14_Browsing_ComInterfacess")  
  
### <a name="component-interfaces"></a><span data-ttu-id="4c015-112">元件介面</span><span class="sxs-lookup"><span data-stu-id="4c015-112">Component Interfaces</span></span>  
 <span data-ttu-id="4c015-113">在**元件介面**(CI) 資料夾中，您可以檢視所有可用的元件介面，在系統中。</span><span class="sxs-lookup"><span data-stu-id="4c015-113">In the **Component Interfaces** (CI) folder, you can view all the available component interfaces in the system.</span></span> <span data-ttu-id="4c015-114">元件介面會宣告它所支援的方法和屬性集合。</span><span class="sxs-lookup"><span data-stu-id="4c015-114">A component interface declares the set of methods and properties that it supports.</span></span> <span data-ttu-id="4c015-115">元件介面不會實作行為或屬性。</span><span class="sxs-lookup"><span data-stu-id="4c015-115">A component interface does not implement behavior or properties.</span></span> <span data-ttu-id="4c015-116">Microsoft BizTalk Adapter for PeopleSoft Enterprise 公開標準方法，例如 CreateEx、DeleteOnly、Find、Get 與 UpdateEx。</span><span class="sxs-lookup"><span data-stu-id="4c015-116">Microsoft BizTalk Adapter for PeopleSoft Enterprise exposes standard methods, for example, CreateEx, DeleteOnly, Find, Get, and UpdateEx.</span></span> <span data-ttu-id="4c015-117">如需這些方法的說明，請參閱[附錄 a： 元件介面方法](../core/appendix-a-component-interface-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="4c015-117">For a description of these methods, see [Appendix A: Component Interface Methods](../core/appendix-a-component-interface-methods.md).</span></span>  
  
## <a name="generate-schemas"></a><span data-ttu-id="4c015-118">產生結構描述</span><span class="sxs-lookup"><span data-stu-id="4c015-118">Generate Schemas</span></span>  
  
<span data-ttu-id="4c015-119">選取您要匯入結構描述的項目：**訊息**，**查詢**，或**元件介面**。</span><span class="sxs-lookup"><span data-stu-id="4c015-119">Select the item for which you want to import schemas: a **Message**, **Query**, or **Component Interface**.</span></span>  <span data-ttu-id="4c015-120">BizTalk Server 會為選取的項目產生結構描述，並將它們匯入至 BizTalk Server 專案。</span><span class="sxs-lookup"><span data-stu-id="4c015-120">BizTalk Server generates the schemas for the selected item and imports them into a BizTalk Server project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c015-121">如果伺服器物件定義變更，您必須重新產生結構描述以更新其中包含的資料。</span><span class="sxs-lookup"><span data-stu-id="4c015-121">If the server object definitions change, you must regenerate the schema to update the data it contains.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c015-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c015-122">See Also</span></span>  
 [<span data-ttu-id="4c015-123">建立 PeopleSoft 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="4c015-123">Creating PeopleSoft Send Handlers</span></span>](../core/creating-peoplesoft-send-handlers.md)