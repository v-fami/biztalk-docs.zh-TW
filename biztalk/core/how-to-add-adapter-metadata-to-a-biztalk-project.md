---
title: "如何將配接器中繼資料新增至 BizTalk 專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e439e5bf-94b3-4582-bacc-b058e6eb8e17
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b343ff085cee7049ea916a38fe1216e097200fbf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-adapter-metadata-to-a-biztalk-project"></a><span data-ttu-id="70d50-102">如何將配接器中繼資料新增至 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="70d50-102">How to Add Adapter Metadata to a BizTalk Project</span></span>
<span data-ttu-id="70d50-103">「新增配接器中繼資料精靈」可讓您新增配接器中繼資料到 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="70d50-103">The Add Adapter Metadata Wizard enables you to add adapter metadata to a BizTalk project.</span></span> <span data-ttu-id="70d50-104">這項資料包含從協調流程與配接器通訊所需的配置、訊息類型以及連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="70d50-104">This data includes schemas, message types, and port types needed to communicate with an adapter from an orchestration.</span></span> <span data-ttu-id="70d50-105">對 應用程式配接器 (例如 FTP) 使用 「 新增配接器中繼資料精靈 」 ，可將這些應用程式配接器的對應結構描述提取至系統中 。</span><span class="sxs-lookup"><span data-stu-id="70d50-105">Use the Add Adapter Metadata Wizard with application adapters, such as FTP, to pull schemas corresponding to these application adapters into the system.</span></span> <span data-ttu-id="70d50-106">請注意，一般而言，HTTP 之類的傳輸配接器並不會使用結構描述。</span><span class="sxs-lookup"><span data-stu-id="70d50-106">Note that transport adapters such as HTTP do not typically use schemas.</span></span>  
  
 <span data-ttu-id="70d50-107">下列程序帶您執行新增配接器中繼資料的一般步驟。</span><span class="sxs-lookup"><span data-stu-id="70d50-107">The following procedure walks you through the generic steps to add metadata for an adapter.</span></span>  
  
### <a name="to-add-adapter-metadata-to-a-biztalk-project"></a><span data-ttu-id="70d50-108">將配接器中繼資料新增至 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="70d50-108">To add adapter metadata to a BizTalk project</span></span>  
  
1.  <span data-ttu-id="70d50-109">在您[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案，在 [方案總管] 中，以滑鼠右鍵按一下您的專案中，按一下**新增**，然後按一下 **新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="70d50-109">In your [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, in Solution Explorer, right-click your project, click **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="70d50-110">在**新增產生的項目- \<** *專案名稱* **>** 對話方塊中，於**範本**] 區段中，選取**新增配接器**，然後按一下 [**開啟**。</span><span class="sxs-lookup"><span data-stu-id="70d50-110">In the **Add Generated Items - \<***Project name***>** dialog box, in the **Templates** section, select **Add Adapter**, and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="70d50-111">在 新增配接器中繼資料精靈，在**選取配接器**頁面上，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="70d50-111">In the Add Adapter Metadata Wizard, on the **Select Adapter** page, do the following.</span></span>  
  
    |<span data-ttu-id="70d50-112">使用</span><span class="sxs-lookup"><span data-stu-id="70d50-112">Use this</span></span>|<span data-ttu-id="70d50-113">動作</span><span class="sxs-lookup"><span data-stu-id="70d50-113">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="70d50-114">配接器清單方塊</span><span class="sxs-lookup"><span data-stu-id="70d50-114">Adapter list box</span></span>|<span data-ttu-id="70d50-115">選取要新增至專案的已註冊配接器。</span><span class="sxs-lookup"><span data-stu-id="70d50-115">Select the registered adapter to add to the project.</span></span>|  
    |<span data-ttu-id="70d50-116">SQL Server</span><span class="sxs-lookup"><span data-stu-id="70d50-116">SQL Server</span></span>|<span data-ttu-id="70d50-117">輸入 BizTalk 資料庫伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="70d50-117">Enter the BizTalk database server name.</span></span>|  
    |<span data-ttu-id="70d50-118">資料庫</span><span class="sxs-lookup"><span data-stu-id="70d50-118">Database</span></span>|<span data-ttu-id="70d50-119">顯示所選取伺服器的「BizTalk 管理」資料庫清單。</span><span class="sxs-lookup"><span data-stu-id="70d50-119">Displays the list of BizTalk Management databases for the chosen server.</span></span>|  
    |<span data-ttu-id="70d50-120">通訊埠</span><span class="sxs-lookup"><span data-stu-id="70d50-120">Port</span></span>|<span data-ttu-id="70d50-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="70d50-121">Optional.</span></span> <span data-ttu-id="70d50-122">顯示先前建立並儲存在「BizTalk 管理」資料庫中的連接埠清單。</span><span class="sxs-lookup"><span data-stu-id="70d50-122">Displays the list of ports created and stored in the BizTalk Management database.</span></span> <span data-ttu-id="70d50-123">只有設定為使用所選取配接器的連接埠才會顯示。</span><span class="sxs-lookup"><span data-stu-id="70d50-123">Only ports configured to work with the selected adapter are shown.</span></span>|  
  
     <span data-ttu-id="70d50-124">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="70d50-124">Click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="70d50-125">嘗試加入產生的結構描述包含的字元之**System.XML.XMLConvert**類別不支援結果導致編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="70d50-125">Attempting to add generated schemas that contain characters that the **System.XML.XMLConvert** class does not support results in a compilation error.</span></span>  
  
4.  <span data-ttu-id="70d50-126">如果您在使用靜態配接器，**選取要匯入服務**頁面上，從樹狀檢視中，選取一組可用的服務，然後按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="70d50-126">If you are using a static adapter, on the **Select Services to Import** page, select a set of available services from the tree view, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="70d50-127">（或者）</span><span class="sxs-lookup"><span data-stu-id="70d50-127">–Or–</span></span>  
  
     <span data-ttu-id="70d50-128">如果要使用動態的配接器，請遵循自訂使用者介面中的步驟來完成精靈。</span><span class="sxs-lookup"><span data-stu-id="70d50-128">If you are using a dynamic adapter, follow the steps in the custom user interface to complete the wizard.</span></span>  
  
 <span data-ttu-id="70d50-129">在完成精靈之後，[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 就會在方案總管中列出 .odx 和 .xsd 檔案。</span><span class="sxs-lookup"><span data-stu-id="70d50-129">After you complete the wizard, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] lists the .odx and .xsd files in Solution Explorer.</span></span>