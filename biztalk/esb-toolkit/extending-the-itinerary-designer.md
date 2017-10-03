---
title: "擴充路線設計工具 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f26b825b-ebab-4dac-b7ed-0608c79e146a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb44c851258cc623cf991a0b2be5c18d58e59770
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="extending-the-itinerary-designer"></a><span data-ttu-id="ca48a-102">擴充路線設計工具</span><span class="sxs-lookup"><span data-stu-id="ca48a-102">Extending the Itinerary Designer</span></span>
<span data-ttu-id="ca48a-103">路線設計工具是 visual 的特定領域語言 (DSL) for Microsoft Visual Studio 可讓旅搭配使用圖形化模型[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ca48a-103">The Itinerary Designer is a visual domain-specific language (DSL) for Microsoft Visual Studio that enables the graphical modeling of itineraries for use with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span> <span data-ttu-id="ca48a-104">在設計工具會公開各種擴充點，開發人員可以撰寫自訂延伸模組，以啟用新功能及/或新的組態選項。</span><span class="sxs-lookup"><span data-stu-id="ca48a-104">The designer exposes various extension points for which developers can write custom extensions to enable new functionality and/or new configuration options.</span></span>  
  

  
 <span data-ttu-id="ca48a-105">**建立自訂的路線匯出工具**</span><span class="sxs-lookup"><span data-stu-id="ca48a-105">**Creating a Custom Itinerary Exporter**</span></span>  
  
 <span data-ttu-id="ca48a-106">路線設計工具的架構可以建立自訂模型匯入程式會序列化並將保存路線模型中的資料。</span><span class="sxs-lookup"><span data-stu-id="ca48a-106">The architecture of the Itinerary Designer allows for the creation of custom model exporters that serialize and persist the data in an Itinerary model.</span></span>  
  
 <span data-ttu-id="ca48a-107">**為訊息的服務建立自訂的擴充性**</span><span class="sxs-lookup"><span data-stu-id="ca48a-107">**Creating a Custom Extender for a Messaging Service**</span></span>  
  
 <span data-ttu-id="ca48a-108">在路線設計工具的架構可讓您建立可用來將屬性加入至使用的屬性包傳訊服務路線服務模型項目的自訂擴充項。</span><span class="sxs-lookup"><span data-stu-id="ca48a-108">The architecture of the Itinerary Designer allows you to create custom extenders for Itinerary Service model elements that can be used to add properties to the property bag for use by Messaging Services.</span></span>  
  
 <span data-ttu-id="ca48a-109">如需如何建立這類擴充性的範例，請參閱[安裝及執行設計工具擴充性範例](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="ca48a-109">For a sample of how to create such an extender, see [Installing and Running the Designer Extensibility Sample](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md).</span></span>  
  
 <span data-ttu-id="ca48a-110">**建立協調流程為基礎的路線服務的自訂擴充性**</span><span class="sxs-lookup"><span data-stu-id="ca48a-110">**Creating a Custom Extender for an Orchestration-Based Itinerary Service**</span></span>  
  
 <span data-ttu-id="ca48a-111">在路線設計工具的架構可讓您建立自訂的行程服務模型項目可以用來將屬性加入至使用的屬性包，協調流程為基礎的路線服務的擴充項。</span><span class="sxs-lookup"><span data-stu-id="ca48a-111">The architecture of the Itinerary Designer allows you to create custom extenders for Itinerary Service model elements that can be used to add properties to the property bag for use by orchestration-based itinerary services.</span></span>  
  
 <span data-ttu-id="ca48a-112">如需如何建立這類擴充性的範例，請參閱[安裝及執行設計工具擴充性範例](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="ca48a-112">For a sample of how to create such an extender, see [Installing and Running the Designer Extensibility Sample](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md).</span></span>  
  
 <span data-ttu-id="ca48a-113">**建立自訂解析程式擴充性**</span><span class="sxs-lookup"><span data-stu-id="ca48a-113">**Creating a Custom Resolver Extender**</span></span>  
  
 <span data-ttu-id="ca48a-114">在路線設計工具的架構可讓您建立自訂的擴充項的自訂解析程式的組態。</span><span class="sxs-lookup"><span data-stu-id="ca48a-114">The architecture of the Itinerary Designer allows you to create custom extenders for the configuration of custom resolvers.</span></span> <span data-ttu-id="ca48a-115">這些擴充項提供圖形化介面中解析程式的連接字串中，設定名稱 / 值組的對應到特定的解析程式擴充項類別中的屬性。</span><span class="sxs-lookup"><span data-stu-id="ca48a-115">These extenders provide a graphical interface for configuring the name-value pairs in the resolver connection string, which map to properties in the specific resolver extender class.</span></span>  
  
 <span data-ttu-id="ca48a-116">如需如何建立這類擴充性的範例，請參閱[安裝及執行設計工具擴充性範例](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="ca48a-116">For a sample of how to create such an extender, see [Installing and Running the Designer Extensibility Sample](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md).</span></span>  
  
 <span data-ttu-id="ca48a-117">**建立自訂配接器屬性的資訊清單檔案**</span><span class="sxs-lookup"><span data-stu-id="ca48a-117">**Creating a Manifest File for Custom Adapter Properties**</span></span>  
  
 <span data-ttu-id="ca48a-118">在建立自訂配接器提供者，則您也必須提供設計工具支援配接器提供者顯示的端點設定屬性的解析程式擴充項。</span><span class="sxs-lookup"><span data-stu-id="ca48a-118">When creating a custom adapter provider, you must also provide designer support for the adapter provider to those resolver extenders that display an endpoint configuration property.</span></span> <span data-ttu-id="ca48a-119">若要啟用設計工具支援，就必須建立配接器提供者資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="ca48a-119">To enable designer support, it is necessary to create an adapter provider manifest file.</span></span>  
  
 <span data-ttu-id="ca48a-120">配接器提供者資訊清單檔案會定義特定的配接器提供者、 其類型、 描述和組件中可以找到它們與相關聯的屬性。</span><span class="sxs-lookup"><span data-stu-id="ca48a-120">The adapter provider manifest file defines the properties associated with a specific adapter provider, their types, descriptions, and the assembly in which they can be found.</span></span> <span data-ttu-id="ca48a-121">這些資訊清單檔案應該置於具有唯一的名稱 (例如，FTPPropertyManifest.xml) 路線設計工具二進位檔 (例如，Microsoft.Practices.Itineary.DslPackage.dll) 相同的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ca48a-121">These manifest files should be placed in the same folder as the Itinerary Designer binaries (for example, Microsoft.Practices.Itineary.DslPackage.dll) with a unique name (for example, FTPPropertyManifest.xml).</span></span>  
  
 <span data-ttu-id="ca48a-122">以下是配接器提供者資訊清單檔案的參考執行個體同樣地應該結構化自訂資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="ca48a-122">The following is a reference instance of an adapter provider manifest file; custom manifest files should be structured likewise.</span></span>  
  
```xml  
\<?xml version="1.0" encoding="utf-8" ?>  
<adapterPropertyManifest adapterName="FTP">  
     <aliases>  
          <alias name="globalPropertySchemas" value="Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
     </aliases>  
     <properties>  
          <property name="UserName" type="FTP.UserName" description="The user name for the connection." encrypted="true" assembly="globalPropertySchemas" />  
          <property name="Password" type="FTP.Password" description="The password for the conection." encrypted="true" assembly="globalPropertySchemas" />  
          <property name="MaxConnections" type="FTP.MaxConnections" description="The maximun number of connections." assembly="globalPropertySchemas" />  
          <property name="EventArgs" type="System.EventArgs" assembly="mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
     </properties>  
</adapterPropertyManifest>  
```  
  
 <span data-ttu-id="ca48a-123">**建立自訂篩選器擴充項**</span><span class="sxs-lookup"><span data-stu-id="ca48a-123">**Creating a Custom Filter Extender**</span></span>  
  
 <span data-ttu-id="ca48a-124">在路線設計工具的架構可讓您建立的自訂篩選器設定的自訂擴充項。</span><span class="sxs-lookup"><span data-stu-id="ca48a-124">The architecture of the Itinerary Designer allows you to create custom extenders for the configuration of custom filters.</span></span> <span data-ttu-id="ca48a-125">這些擴充項提供圖形化介面來設定篩選連接字串中的名稱 / 值組對應到特定篩選器 extender 類別中的屬性。</span><span class="sxs-lookup"><span data-stu-id="ca48a-125">These extenders provide a graphical interface for configuring the name-value pairs in the filter connection string, which map to properties in the specific filter extender class.</span></span>  
  
-   <span data-ttu-id="ca48a-126">/ 範例/設計工具擴充性 Samples/Extenders.Itinerary.OrchestrationSample/Extenders.Itinerary.OrchestrationSample/Extenders.Itinerary.OrchestrationSample</span><span class="sxs-lookup"><span data-stu-id="ca48a-126">/Samples/Designer Extensibility Samples/Extenders.Itinerary.OrchestrationSample/Extenders.Itinerary.OrchestrationSample/Extenders.Itinerary.OrchestrationSample</span></span>  
  
-   <span data-ttu-id="ca48a-127">/ 範例/設計工具擴充性 Samples/Extenders.Resolvers.ResolverSample/Extenders.Resolvers.ResolverSample</span><span class="sxs-lookup"><span data-stu-id="ca48a-127">/Samples/Designer Extensibility Samples/Extenders.Resolvers.ResolverSample/Extenders.Resolvers.ResolverSample</span></span>  
  
 <span data-ttu-id="ca48a-128">**建立自訂驗證規則**</span><span class="sxs-lookup"><span data-stu-id="ca48a-128">**Creating Custom Validation Rules**</span></span>  
  
 <span data-ttu-id="ca48a-129">路線設計工具所導入的最後一個重要延伸模組是一種驗證機制，可讓您可在外部，相對於特定領域語言 (DSL)，指定並實作模型的驗證規則。</span><span class="sxs-lookup"><span data-stu-id="ca48a-129">The last significant extension introduced by the Itinerary Designer is a validation mechanism that allows you to externally, with respect to a domain-specific language (DSL), specify and implement the model validation rules.</span></span> <span data-ttu-id="ca48a-130">機制"連結到"DSL 驗證架構，並在使用者按一下，就會啟用**驗證**或**驗證所有**模型的快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="ca48a-130">The mechanism "hooks into" the DSL validation framework and is activated when the user clicks **Validate** or **Validate all** on the shortcut menu of a model.</span></span> <span data-ttu-id="ca48a-131">這樣會叫用 DSL 架構**DslCommandSet** ，又呼叫驗證引擎在路線設計工具中的物件。</span><span class="sxs-lookup"><span data-stu-id="ca48a-131">This invokes the DSL framework's **DslCommandSet** object that, in turn, calls the validation engine in the Itinerary Designer.</span></span>  
  
 <span data-ttu-id="ca48a-132">**ValidationEngine**類別執行使用企業程式庫驗證應用程式區塊模型項目驗證，並將驗證錯誤記錄到 Microsoft Visual Studio IDE 中的 [錯誤清單] 視窗。</span><span class="sxs-lookup"><span data-stu-id="ca48a-132">The **ValidationEngine** class performs the model element validation using the Enterprise Library Validation Application Block and logs the validation errors to the Error List window in Microsoft Visual Studio IDE.</span></span> <span data-ttu-id="ca48a-133">企業程式庫組態檔中定義的驗證，應執行的每種類型的模型中的項目。</span><span class="sxs-lookup"><span data-stu-id="ca48a-133">The validation that should be performed for each type of element in a model is defined in the Enterprise Library configuration file.</span></span> <span data-ttu-id="ca48a-134">檔名為 Ruleset.config 和二進位路線設計工具二進位檔的所在位置的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="ca48a-134">The file is named Ruleset.config and is located in the binary folder where all the Itinerary Designer binaries are located.</span></span> <span data-ttu-id="ca48a-135">下列範例是組態檔片段，而且包含兩個驗證規則 （名稱為驗證） **UddiResolver** extender，一個用於**ServerUrl**屬性，另一個用於**ServiceKey**屬性。</span><span class="sxs-lookup"><span data-stu-id="ca48a-135">The following example is a fragment of the configuration file and includes two validation rules (named validators) for the **UddiResolver** extender, one for the **ServerUrl** property and one for the **ServiceKey** property.</span></span>  
  
```  
\<!--   
UddiResolver  
-->  
<type assemblyName="Microsoft.Practices.Services.Extenders.Resolvers.UDDI"  
 name="Microsoft.Practices.Services.Extenders.Resolvers.UDDI.UddiResolver">  
<ruleset name="Menu">  
<properties>  
<property name="ServerUrl">  
<validator type="Microsoft.Practices.Modeling.Validation.NotEmptyStringValidator, Microsoft.Practices.Modeling.Validation"  
          messageTemplate="The '{1}' property value should not be empty or null."  
          name="UddiResolver.ServerUrl not null validator"/>  
</property>  
<property name="ServiceKey">  
<validator type="Microsoft.Practices.Modeling.Validation.NotEmptyStringValidator, Microsoft.Practices.Modeling.Validation"  
          messageTemplate="The '{1}' property value should not be empty or null."  
          name="UddiResolver.ServiceKey not null validator"/>  
</property>  
</properties>  
</ruleset>  
</type>  
```  
  
 <span data-ttu-id="ca48a-136">每個規則會識別驗證器實作的規則。</span><span class="sxs-lookup"><span data-stu-id="ca48a-136">Each rule identifies the validator that implements the rule.</span></span> <span data-ttu-id="ca48a-137">路線設計工具隨附一組大型驗證程式類別。</span><span class="sxs-lookup"><span data-stu-id="ca48a-137">The Itinerary Designer comes with a large set of validator classes.</span></span> <span data-ttu-id="ca48a-138">它們都放在 Microsoft.Practices.Modeling.Validation 資料夾中的專案設計工具二進位。</span><span class="sxs-lookup"><span data-stu-id="ca48a-138">They are all in the Microsoft.Practices.Modeling.Validation project in the Designer binary folder.</span></span>  
  
 <span data-ttu-id="ca48a-139">使用此驗證機制的最終結果是使用者可以修改提供的規則和驗證程式變更或新增自己的規則和驗證程式的模型驗證如何該路線設計工具。</span><span class="sxs-lookup"><span data-stu-id="ca48a-139">The final result of using this validation mechanism is that Itinerary Designer users can modify how the models are validated by changing the provided rules and validators or by adding their own rules and validators.</span></span> <span data-ttu-id="ca48a-140">這可以完成而不開啟、 修改、 重建和重新部署 Dsl 藉由執行下列兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="ca48a-140">This can be done without opening, modifying, rebuilding, and re-deploying the DSLs by performing the following two steps:</span></span>  
  
1.  <span data-ttu-id="ca48a-141">建立驗證程式類別，並將其放在二進位資料夾內的程式庫位置**Microsoft.Practices.Modeling.Validation.dll**位於程式庫。</span><span class="sxs-lookup"><span data-stu-id="ca48a-141">Create a validator class and put it in a library inside the binary folder where the **Microsoft.Practices.Modeling.Validation.dll** library is located.</span></span>  
  
2.  <span data-ttu-id="ca48a-142">將項目加入至 Rules.config 檔案，以定義應該套用的驗證程式哪些模型項目類別的哪些屬性。</span><span class="sxs-lookup"><span data-stu-id="ca48a-142">Add entries to the Rules.config file to define what property of what model element class the validator should be applied.</span></span>