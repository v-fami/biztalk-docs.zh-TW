---
title: 延伸路線設計工具 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f26b825b-ebab-4dac-b7ed-0608c79e146a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fbe9e24560f8f00f4b3d806c76ebc326240add5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980743"
---
# <a name="extending-the-itinerary-designer"></a><span data-ttu-id="5dbed-102">延伸路線設計工具</span><span class="sxs-lookup"><span data-stu-id="5dbed-102">Extending the Itinerary Designer</span></span>
<span data-ttu-id="5dbed-103">在路線設計工具是視覺化的特定領域語言 (DSL) for Microsoft Visual Studio，可讓用於路線的圖形化模型[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5dbed-103">The Itinerary Designer is a visual domain-specific language (DSL) for Microsoft Visual Studio that enables the graphical modeling of itineraries for use with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span> <span data-ttu-id="5dbed-104">設計工具會公開各種不同的開發人員可以撰寫自訂的延伸模組，以啟用新功能及/或新的組態選項的擴充點。</span><span class="sxs-lookup"><span data-stu-id="5dbed-104">The designer exposes various extension points for which developers can write custom extensions to enable new functionality and/or new configuration options.</span></span>  
  

  
 <span data-ttu-id="5dbed-105">**建立自訂路線匯出工具**</span><span class="sxs-lookup"><span data-stu-id="5dbed-105">**Creating a Custom Itinerary Exporter**</span></span>  
  
 <span data-ttu-id="5dbed-106">在路線設計工具的架構可讓您建立的自訂模型匯出工具會序列化並將保存路線模型中的資料。</span><span class="sxs-lookup"><span data-stu-id="5dbed-106">The architecture of the Itinerary Designer allows for the creation of custom model exporters that serialize and persist the data in an Itinerary model.</span></span>  
  
 <span data-ttu-id="5dbed-107">**建立自訂擴充項的訊息服務**</span><span class="sxs-lookup"><span data-stu-id="5dbed-107">**Creating a Custom Extender for a Messaging Service**</span></span>  
  
 <span data-ttu-id="5dbed-108">在路線設計工具的架構可讓您建立自訂路線服務模型項目可以訊息處理服務用來將屬性加入至使用的屬性包 extender。</span><span class="sxs-lookup"><span data-stu-id="5dbed-108">The architecture of the Itinerary Designer allows you to create custom extenders for Itinerary Service model elements that can be used to add properties to the property bag for use by Messaging Services.</span></span>  
  
 <span data-ttu-id="5dbed-109">如需如何建立這類擴充性的範例，請參閱 <<c0> [ 安裝和執行設計工具擴充性範例](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="5dbed-109">For a sample of how to create such an extender, see [Installing and Running the Designer Extensibility Sample](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md).</span></span>  
  
 <span data-ttu-id="5dbed-110">**建立自訂的擴充性的協調流程為基礎的路線服務**</span><span class="sxs-lookup"><span data-stu-id="5dbed-110">**Creating a Custom Extender for an Orchestration-Based Itinerary Service**</span></span>  
  
 <span data-ttu-id="5dbed-111">在路線設計工具的架構可讓您建立自訂路線服務模型項目可以用來將屬性加入至使用的屬性包，協調流程路線服務的 extender。</span><span class="sxs-lookup"><span data-stu-id="5dbed-111">The architecture of the Itinerary Designer allows you to create custom extenders for Itinerary Service model elements that can be used to add properties to the property bag for use by orchestration-based itinerary services.</span></span>  
  
 <span data-ttu-id="5dbed-112">如需如何建立這類擴充性的範例，請參閱 <<c0> [ 安裝和執行設計工具擴充性範例](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="5dbed-112">For a sample of how to create such an extender, see [Installing and Running the Designer Extensibility Sample](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md).</span></span>  
  
 <span data-ttu-id="5dbed-113">**建立自訂解析程式擴充項**</span><span class="sxs-lookup"><span data-stu-id="5dbed-113">**Creating a Custom Resolver Extender**</span></span>  
  
 <span data-ttu-id="5dbed-114">在路線設計工具的架構可讓您建立之設定的自訂解析程式的自訂擴充項。</span><span class="sxs-lookup"><span data-stu-id="5dbed-114">The architecture of the Itinerary Designer allows you to create custom extenders for the configuration of custom resolvers.</span></span> <span data-ttu-id="5dbed-115">這些擴充項提供圖形化介面設定的名稱 / 值組在解析程式的連接字串中，對應到特定的解析程式擴充項類別中的屬性。</span><span class="sxs-lookup"><span data-stu-id="5dbed-115">These extenders provide a graphical interface for configuring the name-value pairs in the resolver connection string, which map to properties in the specific resolver extender class.</span></span>  
  
 <span data-ttu-id="5dbed-116">如需如何建立這類擴充性的範例，請參閱 <<c0> [ 安裝和執行設計工具擴充性範例](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="5dbed-116">For a sample of how to create such an extender, see [Installing and Running the Designer Extensibility Sample](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md).</span></span>  
  
 <span data-ttu-id="5dbed-117">**建立自訂的配接器屬性的資訊清單檔案**</span><span class="sxs-lookup"><span data-stu-id="5dbed-117">**Creating a Manifest File for Custom Adapter Properties**</span></span>  
  
 <span data-ttu-id="5dbed-118">在建立自訂配接器提供者時，您必須也提供設計工具支援配接器提供者，這些會顯示端點的組態屬性的解析程式擴充項。</span><span class="sxs-lookup"><span data-stu-id="5dbed-118">When creating a custom adapter provider, you must also provide designer support for the adapter provider to those resolver extenders that display an endpoint configuration property.</span></span> <span data-ttu-id="5dbed-119">若要啟用設計工具支援，就必須建立配接器提供者資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="5dbed-119">To enable designer support, it is necessary to create an adapter provider manifest file.</span></span>  
  
 <span data-ttu-id="5dbed-120">配接器提供者資訊清單檔會定義與特定配接器提供者、 其類型、 描述，以及在其中可以找到這些組件相關聯的屬性。</span><span class="sxs-lookup"><span data-stu-id="5dbed-120">The adapter provider manifest file defines the properties associated with a specific adapter provider, their types, descriptions, and the assembly in which they can be found.</span></span> <span data-ttu-id="5dbed-121">這些資訊清單檔應該放在路線設計工具二進位檔 (例如 Microsoft.Practices.Itineary.DslPackage.dll) 的唯一名稱 (例如 FTPPropertyManifest.xml) 相同的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="5dbed-121">These manifest files should be placed in the same folder as the Itinerary Designer binaries (for example, Microsoft.Practices.Itineary.DslPackage.dll) with a unique name (for example, FTPPropertyManifest.xml).</span></span>  
  
 <span data-ttu-id="5dbed-122">以下是配接器提供者資訊清單檔案; 的參考執行個體同樣地應該結構化自訂資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="5dbed-122">The following is a reference instance of an adapter provider manifest file; custom manifest files should be structured likewise.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
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
  
 <span data-ttu-id="5dbed-123">**建立自訂篩選器擴充項**</span><span class="sxs-lookup"><span data-stu-id="5dbed-123">**Creating a Custom Filter Extender**</span></span>  
  
 <span data-ttu-id="5dbed-124">在路線設計工具的架構可讓您建立自訂的擴充項自訂篩選器的組態。</span><span class="sxs-lookup"><span data-stu-id="5dbed-124">The architecture of the Itinerary Designer allows you to create custom extenders for the configuration of custom filters.</span></span> <span data-ttu-id="5dbed-125">這些擴充項提供圖形化介面設定名稱 / 值組在篩選器連接字串中，對應到特定的篩選器擴充項類別中的屬性。</span><span class="sxs-lookup"><span data-stu-id="5dbed-125">These extenders provide a graphical interface for configuring the name-value pairs in the filter connection string, which map to properties in the specific filter extender class.</span></span>  
  
- <span data-ttu-id="5dbed-126">/ 範例/設計工具擴充性 Samples/Extenders.Itinerary.OrchestrationSample/Extenders.Itinerary.OrchestrationSample/Extenders.Itinerary.OrchestrationSample</span><span class="sxs-lookup"><span data-stu-id="5dbed-126">/Samples/Designer Extensibility Samples/Extenders.Itinerary.OrchestrationSample/Extenders.Itinerary.OrchestrationSample/Extenders.Itinerary.OrchestrationSample</span></span>  
  
- <span data-ttu-id="5dbed-127">/ 範例/設計工具擴充性 Samples/Extenders.Resolvers.ResolverSample/Extenders.Resolvers.ResolverSample</span><span class="sxs-lookup"><span data-stu-id="5dbed-127">/Samples/Designer Extensibility Samples/Extenders.Resolvers.ResolverSample/Extenders.Resolvers.ResolverSample</span></span>  
  
  <span data-ttu-id="5dbed-128">**建立自訂驗證規則**</span><span class="sxs-lookup"><span data-stu-id="5dbed-128">**Creating Custom Validation Rules**</span></span>  
  
  <span data-ttu-id="5dbed-129">路線設計工具所導入的最後一個重要延伸模組是一種驗證機制，可讓您可在外部，相對於特定領域語言 (DSL)，指定並實作模型驗證規則。</span><span class="sxs-lookup"><span data-stu-id="5dbed-129">The last significant extension introduced by the Itinerary Designer is a validation mechanism that allows you to externally, with respect to a domain-specific language (DSL), specify and implement the model validation rules.</span></span> <span data-ttu-id="5dbed-130">機制 」 連結到 「 DSL 驗證架構，以及當使用者按一下 啟動**Validate**或是**驗證所有**模型的快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="5dbed-130">The mechanism "hooks into" the DSL validation framework and is activated when the user clicks **Validate** or **Validate all** on the shortcut menu of a model.</span></span> <span data-ttu-id="5dbed-131">這樣會叫用 DSL 架構**DslCommandSet**物件，接著，呼叫在路線設計工具中的 驗證引擎。</span><span class="sxs-lookup"><span data-stu-id="5dbed-131">This invokes the DSL framework's **DslCommandSet** object that, in turn, calls the validation engine in the Itinerary Designer.</span></span>  
  
  <span data-ttu-id="5dbed-132">**ValidationEngine**類別會執行使用企業程式庫驗證應用程式區塊的項目模型驗證，並記錄到 Microsoft Visual Studio IDE 中的 錯誤清單 視窗的 驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="5dbed-132">The **ValidationEngine** class performs the model element validation using the Enterprise Library Validation Application Block and logs the validation errors to the Error List window in Microsoft Visual Studio IDE.</span></span> <span data-ttu-id="5dbed-133">Enterprise Library 組態檔中定義的驗證，應該執行的每一種模型中的項目。</span><span class="sxs-lookup"><span data-stu-id="5dbed-133">The validation that should be performed for each type of element in a model is defined in the Enterprise Library configuration file.</span></span> <span data-ttu-id="5dbed-134">檔案命名為 Ruleset.config，且位於 [二進位] 資料夾，所有的路線設計工具二進位檔的所在位置。</span><span class="sxs-lookup"><span data-stu-id="5dbed-134">The file is named Ruleset.config and is located in the binary folder where all the Itinerary Designer binaries are located.</span></span> <span data-ttu-id="5dbed-135">下列範例是組態檔片段，並包含兩個驗證規則 （名為驗證程式） **UddiResolver**擴充性、 適合**ServerUrl**屬性，另一個用於**ServiceKey**屬性。</span><span class="sxs-lookup"><span data-stu-id="5dbed-135">The following example is a fragment of the configuration file and includes two validation rules (named validators) for the **UddiResolver** extender, one for the **ServerUrl** property and one for the **ServiceKey** property.</span></span>  
  
```  
<!--   
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
  
 <span data-ttu-id="5dbed-136">每個規則會識別的驗證程式實作的規則。</span><span class="sxs-lookup"><span data-stu-id="5dbed-136">Each rule identifies the validator that implements the rule.</span></span> <span data-ttu-id="5dbed-137">在路線設計工具隨附大量的驗證程式類別。</span><span class="sxs-lookup"><span data-stu-id="5dbed-137">The Itinerary Designer comes with a large set of validator classes.</span></span> <span data-ttu-id="5dbed-138">它們都放在 Microsoft.Practices.Modeling.Validation 資料夾中的專案設計工具二進位。</span><span class="sxs-lookup"><span data-stu-id="5dbed-138">They are all in the Microsoft.Practices.Modeling.Validation project in the Designer binary folder.</span></span>  
  
 <span data-ttu-id="5dbed-139">使用此驗證機制的最終結果是使用者可以藉由變更所提供的規則和驗證程式，或藉由新增自己的規則和驗證程式的模型驗證如何修改該路線設計工具。</span><span class="sxs-lookup"><span data-stu-id="5dbed-139">The final result of using this validation mechanism is that Itinerary Designer users can modify how the models are validated by changing the provided rules and validators or by adding their own rules and validators.</span></span> <span data-ttu-id="5dbed-140">這可以完成而不需要開啟、 修改、 重建和重新部署的 Dsl，藉由執行下列兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="5dbed-140">This can be done without opening, modifying, rebuilding, and re-deploying the DSLs by performing the following two steps:</span></span>  
  
1.  <span data-ttu-id="5dbed-141">建立驗證程式類別，並將它放在二進位資料夾內的文件庫中何處**Microsoft.Practices.Modeling.Validation.dll**位於程式庫。</span><span class="sxs-lookup"><span data-stu-id="5dbed-141">Create a validator class and put it in a library inside the binary folder where the **Microsoft.Practices.Modeling.Validation.dll** library is located.</span></span>  
  
2.  <span data-ttu-id="5dbed-142">將項目加入 Rules.config 檔案來定義應套用的驗證程式的模型項目類別的哪些屬性。</span><span class="sxs-lookup"><span data-stu-id="5dbed-142">Add entries to the Rules.config file to define what property of what model element class the validator should be applied.</span></span>