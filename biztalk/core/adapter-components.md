---
title: 配接器元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 383e8bcb-2b4d-40f9-9e98-f49e8d6f30f7
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2a5f2a78a9ea555d22f585c0aa50eda65b6c287
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225326"
---
# <a name="adapter-components"></a><span data-ttu-id="fc388-102">配接器元件</span><span class="sxs-lookup"><span data-stu-id="fc388-102">Adapter Components</span></span>
<span data-ttu-id="fc388-103">自訂配接器共用由原生配接器所使用的標準化組態、管理和設定機制。</span><span class="sxs-lookup"><span data-stu-id="fc388-103">A custom adapter shares the standardized configuration, management, and setup mechanisms used by the native adapters.</span></span> <span data-ttu-id="fc388-104">運用配接器架構的標準化，自訂配接器的管理藉由使用 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 進行。</span><span class="sxs-lookup"><span data-stu-id="fc388-104">With the standardization to the Adapter Framework, a custom adapter is managed by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="fc388-105">下圖顯示自訂配接器的主要元件： 配接器登錄檔、 配接器設計階段元件，以及配接器執行階段元件。</span><span class="sxs-lookup"><span data-stu-id="fc388-105">The following figure shows the main components of a custom adapter: the adapter registry file, the adapter design-time component, and the adapter run-time component.</span></span>  
  
 ![](../core/media/elementsofanadapter.gif "ElementsOfAnAdapter")  
  
## <a name="adapter-registry-file"></a><span data-ttu-id="fc388-106">配接器登錄檔</span><span class="sxs-lookup"><span data-stu-id="fc388-106">Adapter Registry File</span></span>  
 <span data-ttu-id="fc388-107">配接器的特定資訊必須在登錄和 BizTalk 管理資料庫中註冊。</span><span class="sxs-lookup"><span data-stu-id="fc388-107">Certain information about adapters must be registered in the registry and the BizTalk Management database.</span></span> <span data-ttu-id="fc388-108">配接器的別名、接收處理常式、接收位置和傳輸類型一類的資訊，都稱為中繼資料。</span><span class="sxs-lookup"><span data-stu-id="fc388-108">Information such as an adapter's alias, receive hander, receive location, and transport type is called metadata.</span></span> <span data-ttu-id="fc388-109">這些中繼資料項目，都是在使用 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 手動進行配接器註冊期間所建立的。</span><span class="sxs-lookup"><span data-stu-id="fc388-109">These metadata entries are created during manual adapter registration using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="fc388-110">或者，您可以執行 [配接器登錄精靈] (AdapterRegistryWizard.exe) SDK 公用程式為自訂配接器產生登錄檔。</span><span class="sxs-lookup"><span data-stu-id="fc388-110">Alternatively, you can run the Adapter Registry Wizard (AdapterRegistryWizard.exe) SDK utility to generate a registry file for your custom adapter.</span></span> <span data-ttu-id="fc388-111">按兩下這個登錄檔，或按一下**匯入**上**檔案**功能表使用登錄編輯程式 (regedit32.exe) 會將中繼資料寫入登錄。</span><span class="sxs-lookup"><span data-stu-id="fc388-111">Double-clicking this registry file or clicking **Import** on the **File** menu using the registry editor (regedit32.exe) writes the metadata into the registry.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc388-112">執行此登錄檔並不會將配接器資訊新增至 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="fc388-112">Running this registry file does not add adapter information to the BizTalk Management database.</span></span> <span data-ttu-id="fc388-113">您必須使用 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台]，以手動方式進行。</span><span class="sxs-lookup"><span data-stu-id="fc388-113">You must do this manually by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
## <a name="design-time-component"></a><span data-ttu-id="fc388-114">設計階段元件</span><span class="sxs-lookup"><span data-stu-id="fc388-114">Design-Time Component</span></span>  
 <span data-ttu-id="fc388-115">自訂配接器的使用者介面 (UI) 是使用配接器架構實作的。</span><span class="sxs-lookup"><span data-stu-id="fc388-115">The user interface (UI) for a custom adapter is implemented by using the Adapter Framework.</span></span> <span data-ttu-id="fc388-116">這對 UI 開發是具有生產力的方法，因為 UI 是從提供做為配接器組件一部分的 XML 結構描述轉譯的。</span><span class="sxs-lookup"><span data-stu-id="fc388-116">This is a productive approach to UI development because the UI is rendered from an XML schema provided as part of the adapter's assembly.</span></span> <span data-ttu-id="fc388-117">您需要小量的程式碼，才能將結構描述的內容轉換成 UI 以設定配接器的屬性。</span><span class="sxs-lookup"><span data-stu-id="fc388-117">A small amount of code is required to transform the contents of the schema into a UI to configure the adapter's properties.</span></span>  
  
 <span data-ttu-id="fc388-118">如需讓協調流程與應用程式配接器通訊 (例如 SQL 配接器)，[新增配接器中繼資料精靈] 可讓您將配接器中繼資料，例如結構描述、訊息類型及連接埠類型，新增到 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="fc388-118">For an orchestration needing to communicate with an application adapter such as the SQL adapter, the Add Adapter Metadata Wizard enables you to add adapter metadata, such as schemas, message types, and port types, to a BizTalk project.</span></span> <span data-ttu-id="fc388-119">搭配應用程式配接器使用 [新增配接器中繼資料精靈]，即可將對應的結構描述提取至系統中。</span><span class="sxs-lookup"><span data-stu-id="fc388-119">Use the Add Adapter Metadata Wizard with application adapters to pull corresponding schemas into the system.</span></span> <span data-ttu-id="fc388-120">要叫用這個精靈從 BizTalk （非配接器） 專案中的，以滑鼠右鍵按一下專案，指向**新增產生的項目**，按一下 **新增配接器中繼資料**然後從清單中選取登錄若要匯入配接器中繼資料的介面卡。</span><span class="sxs-lookup"><span data-stu-id="fc388-120">To invoke this wizard from within a BizTalk (non-adapter) project, right-click the project, point to **Add Generated Items**, click **Add Adapter Metadata** and then select from the list of registered adapters to import the adapter metadata.</span></span>  
  
## <a name="run-time-component"></a><span data-ttu-id="fc388-121">執行階段元件</span><span class="sxs-lookup"><span data-stu-id="fc388-121">Run-Time Component</span></span>  
 <span data-ttu-id="fc388-122">配接器通常兩個公用的執行階段元件所組成： 實作訊息接收者和實作訊息傳送者元件的元件。</span><span class="sxs-lookup"><span data-stu-id="fc388-122">Typically an adapter consists of two public run-time components: the component that implements the message receiver and the component that implements the message sender.</span></span> <span data-ttu-id="fc388-123">這些元件可能會在相同的組件中部署，或是在兩個不同的組件中部署。</span><span class="sxs-lookup"><span data-stu-id="fc388-123">These components may be deployed in the same assembly or in two different assemblies.</span></span>  
  
#### <a name="receive-adapter"></a><span data-ttu-id="fc388-124">接收配接器</span><span class="sxs-lookup"><span data-stu-id="fc388-124">Receive Adapter</span></span>  
 <span data-ttu-id="fc388-125">接收配接器負責將網路/資料來源資料流附加到訊息內文，以建立新的 BizTalk 訊息。</span><span class="sxs-lookup"><span data-stu-id="fc388-125">A receive adapter is responsible for creating a new BizTalk message by attaching the network/data source stream to the message body.</span></span> <span data-ttu-id="fc388-126">它也會新增與接收資料的端點有關的任何中繼資料，然後將該訊息提交至傳訊引擎。</span><span class="sxs-lookup"><span data-stu-id="fc388-126">It also adds any metadata pertinent to the endpoint over which the data was received, and then submits that message to the Messaging Engine.</span></span> <span data-ttu-id="fc388-127">配接器會將接收端點的資料刪除，或是將適當的認可訊息傳送到用戶端，以表示 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 已接受資料。</span><span class="sxs-lookup"><span data-stu-id="fc388-127">The adapter deletes the data from the receive endpoint or sends the appropriate acknowledgment message to the client indicating that the data was accepted into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
#### <a name="send-adapter"></a><span data-ttu-id="fc388-128">傳送配接器</span><span class="sxs-lookup"><span data-stu-id="fc388-128">Send Adapter</span></span>  
 <span data-ttu-id="fc388-129">傳送配接器負責使用其特定的傳輸通訊協定，將 BizTalk 訊息傳送到指定的端點。</span><span class="sxs-lookup"><span data-stu-id="fc388-129">A send adapter is responsible for sending a BizTalk message to the specified endpoint using its specific transport protocol.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc388-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc388-130">See Also</span></span>  
 [<span data-ttu-id="fc388-131">什麼是配接器架構？</span><span class="sxs-lookup"><span data-stu-id="fc388-131">What Is the Adapter Framework?</span></span>](../core/what-is-the-adapter-framework.md)