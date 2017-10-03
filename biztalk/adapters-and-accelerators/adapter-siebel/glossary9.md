---
title: "BizTalk Adapter for Siebel 電子商務應用程式，在 BizTalk 中的詞彙 |Microsoft 文件"
description: "常見的詞彙和定義 Siebel 配接器在 BizTalk Adapter pack (BAP) 中使用"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75c74760-53b6-45c3-bacc-bb7ab4fb5b4b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54cb0b66bc7cb4b7477160ab2673ec06165ee6c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="terms-and-definitions-for-the-siebel-adapter"></a><span data-ttu-id="bc12f-103">詞彙和定義 Siebel 配接器</span><span class="sxs-lookup"><span data-stu-id="bc12f-103">Terms and definitions for the Siebel adapter</span></span>
<span data-ttu-id="bc12f-104">下列詞彙和定義會用於[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bc12f-104">The following terms and definitions are used in [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].</span></span>  
  
 
## <a name="a"></a><span data-ttu-id="bc12f-105">只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，</span><span class="sxs-lookup"><span data-stu-id="bc12f-105">A</span></span>  

<span data-ttu-id="bc12f-106">**配接器**</span><span class="sxs-lookup"><span data-stu-id="bc12f-106">**adapter**</span></span>  
<span data-ttu-id="bc12f-107">WCF 架構的元件，可協助 exchange 應用程式 （例如，特定業務系統） 之間的訊息和 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="bc12f-107">A WCF-based component that helps exchange messages between applications (for example, a line-of-business system) and BizTalk Server.</span></span> <span data-ttu-id="bc12f-108">配協器由設計階段元件和執行階段元件組成，進行接收和傳送的作業。</span><span class="sxs-lookup"><span data-stu-id="bc12f-108">The adapter consists of design-time components and run-time components for receive and send operations.</span></span>

<span data-ttu-id="bc12f-109">**配接器用戶端**</span><span class="sxs-lookup"><span data-stu-id="bc12f-109">**adapter client**</span></span>  
<span data-ttu-id="bc12f-110">應用程式透過配接器的特定業務 (LOB) 系統進行互動。</span><span class="sxs-lookup"><span data-stu-id="bc12f-110">An application that interacts with a line-of-business (LOB) system through the adapter.</span></span>  

  
## <a name="b"></a><span data-ttu-id="bc12f-111">B</span><span class="sxs-lookup"><span data-stu-id="bc12f-111">B</span></span>
  
<span data-ttu-id="bc12f-112">**繫結**</span><span class="sxs-lookup"><span data-stu-id="bc12f-112">**binding**</span></span>  
<span data-ttu-id="bc12f-113">軟體元件與軟體層連結在一起的程序。</span><span class="sxs-lookup"><span data-stu-id="bc12f-113">A process by which software components and layers are linked together.</span></span> <span data-ttu-id="bc12f-114">安裝網路元件時，便會建立元件的繫結關聯性與相依性。</span><span class="sxs-lookup"><span data-stu-id="bc12f-114">When a network component is installed, the binding relationships and dependencies for the components are established.</span></span> <span data-ttu-id="bc12f-115">繫結使元件得以彼此通訊。</span><span class="sxs-lookup"><span data-stu-id="bc12f-115">Binding allows components to communicate with each other.</span></span> <span data-ttu-id="bc12f-116">在 BizTalk Server 中，此為協調流程配接器-不特定結束點 (連接埠或角色連結) 與實體配接器-特定結束點 (傳送埠/接收埠或合作對象) 之間的已建立對應。</span><span class="sxs-lookup"><span data-stu-id="bc12f-116">In BizTalk Server, an established mapping between an orchestration adapter-agnostic endpoint (port or role link) and physical adapter-specific endpoints (send/receive ports or party).</span></span>

<span data-ttu-id="bc12f-117">**BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="bc12f-117">**BizTalk Server**</span></span>  
<span data-ttu-id="bc12f-118">連接各種不同的軟體。</span><span class="sxs-lookup"><span data-stu-id="bc12f-118">Connects diverse software.</span></span> <span data-ttu-id="bc12f-119">BizTalk Server 可讓您建立和修改處理程序邏輯會使用該軟體。</span><span class="sxs-lookup"><span data-stu-id="bc12f-119">BizTalk Server enables you to create and modify process logic that uses that software.</span></span> <span data-ttu-id="bc12f-120">BizTalk Server 也可讓資訊工作者監控執行中的處理程序、與企業合作夥伴互動並執行其他業務相關工作。</span><span class="sxs-lookup"><span data-stu-id="bc12f-120">BizTalk Server also enables information workers to monitor running processes, interact with trading partners, and perform other business-oriented tasks.</span></span>

 
## <a name="c"></a><span data-ttu-id="bc12f-121">C</span><span class="sxs-lookup"><span data-stu-id="bc12f-121">C</span></span>
  
<span data-ttu-id="bc12f-122">**通道**</span><span class="sxs-lookup"><span data-stu-id="bc12f-122">**channel**</span></span>  
<span data-ttu-id="bc12f-123">繫結項目的實體實作。</span><span class="sxs-lookup"><span data-stu-id="bc12f-123">A concrete implementation of a binding element.</span></span> <span data-ttu-id="bc12f-124">繫結表示組態，通道則是與該組態相關聯的實作。</span><span class="sxs-lookup"><span data-stu-id="bc12f-124">The binding represents the configuration, and the channel is the implementation associated with that configuration.</span></span> <span data-ttu-id="bc12f-125">因此，沒有與每個繫結項目相關聯的通道。</span><span class="sxs-lookup"><span data-stu-id="bc12f-125">Therefore, there is a channel associated with each binding element.</span></span> <span data-ttu-id="bc12f-126">通道堆疊在彼此的上方來建立繫結的實體實作： 通道堆疊。</span><span class="sxs-lookup"><span data-stu-id="bc12f-126">Channels stack on top of each other to create the concrete implementation of the binding: the channel stack.</span></span>

<span data-ttu-id="bc12f-127">**連線 URI**</span><span class="sxs-lookup"><span data-stu-id="bc12f-127">**connection URI**</span></span>  
<span data-ttu-id="bc12f-128">識別分散式環境中的資源字串。</span><span class="sxs-lookup"><span data-stu-id="bc12f-128">A string that identifies a resource in a distributed environment.</span></span> <span data-ttu-id="bc12f-129">配接器使用的連接統一資源識別元 (URI)，其中包含建立與 LOB 系統的連線所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="bc12f-129">Adapters use a connection Uniform Resource Identifier (URI) that contains the information necessary to establish a connection with the LOB system.</span></span>

<span data-ttu-id="bc12f-130">**合約**</span><span class="sxs-lookup"><span data-stu-id="bc12f-130">**contract**</span></span>  
<span data-ttu-id="bc12f-131">指定集合與存取服務所提供的作業所需的訊息結構。</span><span class="sxs-lookup"><span data-stu-id="bc12f-131">Specifies the collection and structure of messages required to access the operations offered by the service.</span></span>  
  
## <a name="d"></a><span data-ttu-id="bc12f-132">D</span><span class="sxs-lookup"><span data-stu-id="bc12f-132">D</span></span>
  
<span data-ttu-id="bc12f-133">**設計階段經驗**</span><span class="sxs-lookup"><span data-stu-id="bc12f-133">**design-time experience**</span></span>  
<span data-ttu-id="bc12f-134">程序和開發人員在設計階段; 可以執行的作業例如，使用取用配接器服務 BizTalk 專案增益集來擷取訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="bc12f-134">Procedures and operations that a developer performs during design time; for example, using the Consume Adapter Service BizTalk Project Add-in to retrieve message schemas.</span></span> 

 
## <a name="e"></a><span data-ttu-id="bc12f-135">E</span><span class="sxs-lookup"><span data-stu-id="bc12f-135">E</span></span> 
  
<span data-ttu-id="bc12f-136">**端點位址**</span><span class="sxs-lookup"><span data-stu-id="bc12f-136">**endpoint address**</span></span>  
<span data-ttu-id="bc12f-137">網路位址，用於識別 Windows Communication Foundation (WCF) 服務端點的位置。</span><span class="sxs-lookup"><span data-stu-id="bc12f-137">A network address that identifies the location of a Windows Communication Foundation (WCF) service endpoint.</span></span> <span data-ttu-id="bc12f-138">配接器，表示端點位址做為統一資源識別元 (URI) 包含參數的位置和連接的連接。</span><span class="sxs-lookup"><span data-stu-id="bc12f-138">For an adapter, the endpoint address is expressed as a connection Uniform Resource Identifier (URI) that contains location and connection parameters.</span></span> <span data-ttu-id="bc12f-139">配接器可以使用它們來連接到基礎的特定業務 (LOB) 系統。</span><span class="sxs-lookup"><span data-stu-id="bc12f-139">The adapter can use these to establish a connection to the underlying line-of-business (LOB) system.</span></span>

<span data-ttu-id="bc12f-140">**企業單一登入系統 (SSO)**</span><span class="sxs-lookup"><span data-stu-id="bc12f-140">**Enterprise Single Sign-on system (SSO)**</span></span>  
<span data-ttu-id="bc12f-141">SSO 資料庫、主要密碼伺服器以及一或多個企業單一登入 (SSO) 伺服器。</span><span class="sxs-lookup"><span data-stu-id="bc12f-141">An SSO database, a master secret server, and one or more Enterprise Single Sign-On (SSO) servers.</span></span> <span data-ttu-id="bc12f-142">這些伺服器會在 Windows 與非 Windows 認證間進行對應，在 SSO 資料庫中尋找認證，然後用來管理 SSO 系統。</span><span class="sxs-lookup"><span data-stu-id="bc12f-142">These servers do the mapping between the Windows and non-Windows credentials, look up the credentials in the SSO database, and are used for administering the SSO system.</span></span> <span data-ttu-id="bc12f-143">SSO 資料庫也做為組態存放區，保留配接器的自訂組態資料。</span><span class="sxs-lookup"><span data-stu-id="bc12f-143">The SSO database is also used as a configuration store to hold custom configuration data for adapters.</span></span>

<span data-ttu-id="bc12f-144">**可延伸標記語言 (XML)**</span><span class="sxs-lookup"><span data-stu-id="bc12f-144">**Extensible Markup Language (XML)**</span></span>  
<span data-ttu-id="bc12f-145">標記語言，設計用來描述資料。</span><span class="sxs-lookup"><span data-stu-id="bc12f-145">A markup language designed to describe data.</span></span> <span data-ttu-id="bc12f-146">不會預先定義的 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="bc12f-146">XML tags are not predefined.</span></span>  
 
 
## <a name="g"></a><span data-ttu-id="bc12f-147">G</span><span class="sxs-lookup"><span data-stu-id="bc12f-147">G</span></span>
  
<span data-ttu-id="bc12f-148">**全域組件快取 (GAC)**</span><span class="sxs-lookup"><span data-stu-id="bc12f-148">**global assembly cache (GAC)**</span></span>  
<span data-ttu-id="bc12f-149">整個電腦的程式碼快取，它會存放供電腦上多個應用程式共用而特別安裝的組件。</span><span class="sxs-lookup"><span data-stu-id="bc12f-149">A machine-wide code cache that stores assemblies specifically installed to be shared by many applications on the computer.</span></span> <span data-ttu-id="bc12f-150">在全域組件快取中部署的應用程式必須具有強式名稱。</span><span class="sxs-lookup"><span data-stu-id="bc12f-150">Applications deployed in the global assembly cache must have a strong name.</span></span>
  
 
## <a name="i"></a><span data-ttu-id="bc12f-151">I</span><span class="sxs-lookup"><span data-stu-id="bc12f-151">I</span></span>
  
<span data-ttu-id="bc12f-152">**輸入的作業**</span><span class="sxs-lookup"><span data-stu-id="bc12f-152">**inbound operation**</span></span>  
<span data-ttu-id="bc12f-153">介面卡上的特定業務 (LOB) 系統所叫用作業。</span><span class="sxs-lookup"><span data-stu-id="bc12f-153">An operation that is invoked by a line-of-business (LOB) system on the adapter.</span></span>  
  
## <a name="m"></a><span data-ttu-id="bc12f-154">M</span><span class="sxs-lookup"><span data-stu-id="bc12f-154">M</span></span>
  
<span data-ttu-id="bc12f-155">**中繼資料**</span><span class="sxs-lookup"><span data-stu-id="bc12f-155">**metadata**</span></span>  
<span data-ttu-id="bc12f-156">在 WCF 中，指的服務所公開的合約描述。</span><span class="sxs-lookup"><span data-stu-id="bc12f-156">In WCF, refers to a description of the contract exposed by a service.</span></span> <span data-ttu-id="bc12f-157">這就所謂的服務描述，並表示 WSDL 文件中。</span><span class="sxs-lookup"><span data-stu-id="bc12f-157">This is known as the service description and is expressed in a WSDL document.</span></span> <span data-ttu-id="bc12f-158">配接器所公開的中繼資料描述 （介面），它可以在基礎 LOB 系統上執行的作業。</span><span class="sxs-lookup"><span data-stu-id="bc12f-158">The metadata exposed by an adapter describes the (interface to) the operations that it can perform on the underlying LOB system.</span></span> <span data-ttu-id="bc12f-159">如位置、時間、訊息大小和 (或) 例外資訊等資訊。</span><span class="sxs-lookup"><span data-stu-id="bc12f-159">Information, such as location, time, message size, and/or exception information.</span></span>


**[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]**  
<span data-ttu-id="bc12f-160">建置 BizTalk 配接器使用 Web 服務為基礎的開放式標準規格。</span><span class="sxs-lookup"><span data-stu-id="bc12f-160">The specifications for building BizTalk adapters using open standards based on Web services.</span></span>  
  
## <a name="o"></a><span data-ttu-id="bc12f-161">O</span><span class="sxs-lookup"><span data-stu-id="bc12f-161">O</span></span>
  
<span data-ttu-id="bc12f-162">**單向**</span><span class="sxs-lookup"><span data-stu-id="bc12f-162">**one-way**</span></span>  
<span data-ttu-id="bc12f-163">寄件者會傳送一則訊息，但沒有回應的訊息交換模式 (MEP) 會傳回收件者。</span><span class="sxs-lookup"><span data-stu-id="bc12f-163">A message exchange pattern (MEP) in which the sender sends a message, but no response is returned by the receiver.</span></span> <span data-ttu-id="bc12f-164">在 BizTalk Server 中，Mep 稱為通訊模式。</span><span class="sxs-lookup"><span data-stu-id="bc12f-164">In BizTalk Server, MEPs are referred to as communication patterns.</span></span>

<span data-ttu-id="bc12f-165">**輸出作業**</span><span class="sxs-lookup"><span data-stu-id="bc12f-165">**outbound operation**</span></span>  
<span data-ttu-id="bc12f-166">作業的特定業務系統 (LOB) 配接器所叫用。</span><span class="sxs-lookup"><span data-stu-id="bc12f-166">An operation that is invoked by the adapter on the line-of-business system (LOB).</span></span>

<span data-ttu-id="bc12f-167">**output.cs**</span><span class="sxs-lookup"><span data-stu-id="bc12f-167">**output.cs**</span></span>  
<span data-ttu-id="bc12f-168">ServiceModel Metadata Utility 工具 (svcutil.exe) 所建立之預設輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="bc12f-168">The default output file created by the ServiceModel Metadata Utility tool (svcutil.exe).</span></span>  
 
## <a name="p"></a><span data-ttu-id="bc12f-169">P</span><span class="sxs-lookup"><span data-stu-id="bc12f-169">P</span></span>
  
<span data-ttu-id="bc12f-170">**挑選清單**</span><span class="sxs-lookup"><span data-stu-id="bc12f-170">**picklist**</span></span>  
<span data-ttu-id="bc12f-171">其值通常限制為一組值 （類似於列舉型別） 的其中一個商務元件中的欄位。</span><span class="sxs-lookup"><span data-stu-id="bc12f-171">A field in a business component whose value is typically constrained to one of a set of values (akin to enumeration).</span></span>

<span data-ttu-id="bc12f-172">**proxy**</span><span class="sxs-lookup"><span data-stu-id="bc12f-172">**proxy**</span></span>  
<span data-ttu-id="bc12f-173">在 WCF 中，是指實作服務所公開的服務合約的 managed 程式碼物件。</span><span class="sxs-lookup"><span data-stu-id="bc12f-173">In WCF, refers to a managed-code object that implements the service contract exposed by a service.</span></span> <span data-ttu-id="bc12f-174">WCF 服務模型根據使用這類的 proxy。</span><span class="sxs-lookup"><span data-stu-id="bc12f-174">The WCF service model is based on the use of such proxies.</span></span> <span data-ttu-id="bc12f-175">在 WCF 服務模型中，.NET 介面來表示服務合約。</span><span class="sxs-lookup"><span data-stu-id="bc12f-175">In the WCF service model, the service contract is expressed as a .NET interface.</span></span>
  
## <a name="r"></a><span data-ttu-id="bc12f-176">R</span><span class="sxs-lookup"><span data-stu-id="bc12f-176">R</span></span>
  
<span data-ttu-id="bc12f-177">**要求-回應**</span><span class="sxs-lookup"><span data-stu-id="bc12f-177">**request-response**</span></span>  
<span data-ttu-id="bc12f-178">訊息交換模式 (MEP) 寄件者傳送要求訊息與預期來自接收者的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="bc12f-178">A message exchange pattern (MEP) in which the sender sends a request message and expects a response message from the receiver.</span></span> <span data-ttu-id="bc12f-179">在 BizTalk Server 中，Mep 稱為通訊模式。</span><span class="sxs-lookup"><span data-stu-id="bc12f-179">In BizTalk Server, MEPs are referred to as communication patterns.</span></span> <span data-ttu-id="bc12f-180">根據訊息的技術和 （輸入或輸出） 的要求訊息的方向，此模式也稱為要求-回覆或請求-回應。</span><span class="sxs-lookup"><span data-stu-id="bc12f-180">Depending on the messaging technology and the direction of the request message (inbound or outbound), this pattern is also called request-reply or solicit-response.</span></span>

<span data-ttu-id="bc12f-181">**執行階段體驗**</span><span class="sxs-lookup"><span data-stu-id="bc12f-181">**run-time experience**</span></span>  
<span data-ttu-id="bc12f-182">程序和執行階段期間或部署解決方案; 時，開發人員所執行的作業例如，從 BizTalk Server 管理主控台建立實體連接埠繫結。</span><span class="sxs-lookup"><span data-stu-id="bc12f-182">Procedures and operations performed by a developer during run time or when deploying a solution; for example, creating a physical port binding from the BizTalk Server Administration console.</span></span>  


## <a name="s"></a><span data-ttu-id="bc12f-183">S</span><span class="sxs-lookup"><span data-stu-id="bc12f-183">S</span></span>
  
<span data-ttu-id="bc12f-184">**結構描述**</span><span class="sxs-lookup"><span data-stu-id="bc12f-184">**schema**</span></span>  
<span data-ttu-id="bc12f-185">訊息的結構。</span><span class="sxs-lookup"><span data-stu-id="bc12f-185">The structure for a message.</span></span> <span data-ttu-id="bc12f-186">結構描述可以包含多個 ubschema。</span><span class="sxs-lookup"><span data-stu-id="bc12f-186">A schema can contain multiple subschema.</span></span>

<span data-ttu-id="bc12f-187">**ServiceModel Metadata Utility Tool (svcutil.exe)**</span><span class="sxs-lookup"><span data-stu-id="bc12f-187">**ServiceModel Metadata Utility Tool (svcutil.exe)**</span></span>  
<span data-ttu-id="bc12f-188">命令列公用程式所包含的 WCF。</span><span class="sxs-lookup"><span data-stu-id="bc12f-188">A command-line utility that is included with WCF.</span></span> <span data-ttu-id="bc12f-189">它用來建立服務模型 proxy 程式碼，例如配接器的 WCF 服務所公開的服務描述 （中繼資料）。</span><span class="sxs-lookup"><span data-stu-id="bc12f-189">It is used to create service model proxy code from the service description (metadata) that is exposed by a WCF service such as an adapter.</span></span> <span data-ttu-id="bc12f-190">若為輸出的作業，此工具會建立 WCF 用戶端類別和協助程式程式碼;輸入的作業，此工具會建立 WCF 服務合約和協助程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="bc12f-190">For outbound operations, the tool creates a WCF client class and helper code; for inbound operations, the tool creates a WCF service contract and helper code.</span></span>

<span data-ttu-id="bc12f-191">**Siebel 商務元件**</span><span class="sxs-lookup"><span data-stu-id="bc12f-191">**Siebel business component**</span></span>  
<span data-ttu-id="bc12f-192">關聯邏輯上相關的資料行從一個或多個資料表成單一結構。</span><span class="sxs-lookup"><span data-stu-id="bc12f-192">Associates logically related columns from one or more tables into a single structure.</span></span>

<span data-ttu-id="bc12f-193">**Siebel 商務物件**</span><span class="sxs-lookup"><span data-stu-id="bc12f-193">**Siebel business object**</span></span>  
<span data-ttu-id="bc12f-194">代表商務元件的邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="bc12f-194">Represents a logical grouping of business components.</span></span>
  
<span data-ttu-id="bc12f-195">**Siebel 商務服務**</span><span class="sxs-lookup"><span data-stu-id="bc12f-195">**Siebel business service**</span></span>  
<span data-ttu-id="bc12f-196">商務服務方法或可以在 Siebel 系統中直接叫用的函式的集合。</span><span class="sxs-lookup"><span data-stu-id="bc12f-196">A collection of business service methods or functions that can be directly invoked in the Siebel system.</span></span>
  
<span data-ttu-id="bc12f-197">**Siebel COM 資料控制項程式庫**</span><span class="sxs-lookup"><span data-stu-id="bc12f-197">**Siebel COM Data Control library**</span></span>  
<span data-ttu-id="bc12f-198">包含介面，可讓外部用戶端類似 Siebel 配接器連線並通訊以 Siebel 應用程式物件管理員 Siebel 伺服器上。</span><span class="sxs-lookup"><span data-stu-id="bc12f-198">Contains interfaces that enable an external client like the Siebel adapter to connect and communicate with a Siebel Application Object Manager on a Siebel server.</span></span>

<span data-ttu-id="bc12f-199">**SOAP （簡易物件存取通訊協定）**</span><span class="sxs-lookup"><span data-stu-id="bc12f-199">**SOAP (Simple Object Access Protocol)**</span></span>  
<span data-ttu-id="bc12f-200">簡單、 以 XML 為基礎的通訊協定，交換結構化，和在分散式環境中輸入資訊。</span><span class="sxs-lookup"><span data-stu-id="bc12f-200">A simple, XML-based protocol for exchanging structured and type information in decentralized, distributed environments.</span></span> <span data-ttu-id="bc12f-201">WCF 為基礎的用戶端和服務來叫用作業，並傳回結果之間的 SOAP 訊息交換。</span><span class="sxs-lookup"><span data-stu-id="bc12f-201">WCF is based on the exchange of SOAP messages between clients and services to invoke operations and return results.</span></span>

<span data-ttu-id="bc12f-202">**SOAP 訊息**</span><span class="sxs-lookup"><span data-stu-id="bc12f-202">**SOAP message**</span></span>  
<span data-ttu-id="bc12f-203">格式正確的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="bc12f-203">A well-formed XML document.</span></span> <span data-ttu-id="bc12f-204">此文件應使用 SOAP 信封和 SOAP 編碼命名空間，且包含選擇性 XML 宣告，後面接著由選擇性 SOAP 標頭與 SOAP 訊息內文所構成的 SOAP 信封 (根項目)。</span><span class="sxs-lookup"><span data-stu-id="bc12f-204">It should use the SOAP envelope and SOAP encoding namespaces and include an optional XML declaration, followed by a SOAP envelope (the root element), which is made up of an optional SOAP header and a SOAP message body.</span></span>

<span data-ttu-id="bc12f-205">**SQL Server Integration Services (SSIS)**</span><span class="sxs-lookup"><span data-stu-id="bc12f-205">**SQL Server Integration Services (SSIS)**</span></span>  
<span data-ttu-id="bc12f-206">此元件可用於匯入、 匯出及轉換來自不同資料來源的資料。</span><span class="sxs-lookup"><span data-stu-id="bc12f-206">A component that is used to import, export, and transform data from different data sources.</span></span> <span data-ttu-id="bc12f-207">先前稱為資料轉換服務 (DTS)。</span><span class="sxs-lookup"><span data-stu-id="bc12f-207">Previously called data transformation service (DTS).</span></span>

<span data-ttu-id="bc12f-208">**強型別資料**</span><span class="sxs-lookup"><span data-stu-id="bc12f-208">**strongly-typed data**</span></span>  
<span data-ttu-id="bc12f-209">資料集或結果集繫結至基礎的物件型別。</span><span class="sxs-lookup"><span data-stu-id="bc12f-209">A data set or result set that is bound to an underlying object type.</span></span> <span data-ttu-id="bc12f-210">強型別 XML 資料集的每個資料列被由型別，名為基礎的物件類型的欄位對應的項目。</span><span class="sxs-lookup"><span data-stu-id="bc12f-210">Each row in a strongly-typed XML data set is composed of typed, named elements that correspond to fields of the underlying object type.</span></span>  
  
## <a name="w"></a><span data-ttu-id="bc12f-211">W</span><span class="sxs-lookup"><span data-stu-id="bc12f-211">W</span></span>
  
<span data-ttu-id="bc12f-212">**WCF 通道模型**</span><span class="sxs-lookup"><span data-stu-id="bc12f-212">**WCF channel model**</span></span>  
<span data-ttu-id="bc12f-213">程式設計模型依賴多個介面和其他類型。</span><span class="sxs-lookup"><span data-stu-id="bc12f-213">A programming model that relies on several interfaces and other types.</span></span> <span data-ttu-id="bc12f-214">通道會提供低階的程式設計模型，來傳送和接收訊息。</span><span class="sxs-lookup"><span data-stu-id="bc12f-214">Channels provide a low-level programming model for sending and receiving messages.</span></span>
  
<span data-ttu-id="bc12f-215">**WCF 用戶端**</span><span class="sxs-lookup"><span data-stu-id="bc12f-215">**WCF client**</span></span>  
<span data-ttu-id="bc12f-216">用戶端應用程式建構，可公開為方法的服務作業。</span><span class="sxs-lookup"><span data-stu-id="bc12f-216">A client-application construct that exposes the service operations as methods.</span></span> <span data-ttu-id="bc12f-217">您可以使用 新增配接器服務參考 Visual Studio 外掛程式或 ServiceModel Metadata Utility Tool 從配接器所公開的中繼資料產生 WCF 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="bc12f-217">You can use the Add Adapter Service Reference Visual Studio Plug-in or the ServiceModel Metadata Utility Tool to generate a WCF client class from the metadata exposed by an adapter.</span></span>

<span data-ttu-id="bc12f-218">**WCF 服務合約**</span><span class="sxs-lookup"><span data-stu-id="bc12f-218">**WCF service contract**</span></span>  
<span data-ttu-id="bc12f-219">服務合約的 managed 程式碼表示法。</span><span class="sxs-lookup"><span data-stu-id="bc12f-219">A managed-code representation of the service contract.</span></span> <span data-ttu-id="bc12f-220">這會表示為介面中的類別和方法的屬性會設定來定義服務、 作業、 訊息，以及用來與服務通訊的資料合約。</span><span class="sxs-lookup"><span data-stu-id="bc12f-220">It is expressed as an interface in which classes and methods are attributed to define the service, operation, message, and data contracts used to communicate with a service.</span></span> <span data-ttu-id="bc12f-221">您可以使用 ServiceModel 中繼資料公用程式工具 」 或 「 新增配接器服務參考 Visual Studio 外掛程式，從配接器所公開的中繼資料產生 WCF 服務合約。</span><span class="sxs-lookup"><span data-stu-id="bc12f-221">You can use the ServiceModel Metadata Utility tool or the Add Adapter Service Reference Visual Studio Plug-in to generate a WCF service contract from the metadata exposed by an adapter.</span></span> <span data-ttu-id="bc12f-222">您實作 WCF 服務合約以接收來自 LOB 系統的作業。</span><span class="sxs-lookup"><span data-stu-id="bc12f-222">You implement the WCF service contract to receive operations from an LOB system.</span></span>

<span data-ttu-id="bc12f-223">**WCF 服務模型**</span><span class="sxs-lookup"><span data-stu-id="bc12f-223">**WCF service model**</span></span>  
<span data-ttu-id="bc12f-224">WCF 程式撰寫模型，服務以 managed 程式碼物件。</span><span class="sxs-lookup"><span data-stu-id="bc12f-224">A WCF programming model in which a service is represented as a managed code object.</span></span> <span data-ttu-id="bc12f-225">服務所公開的作業會表示為具有強型別資料的方法。</span><span class="sxs-lookup"><span data-stu-id="bc12f-225">The operations exposed by the service are represented as methods with strongly-typed data.</span></span>

<span data-ttu-id="bc12f-226">**弱型別資料**</span><span class="sxs-lookup"><span data-stu-id="bc12f-226">**weakly-typed data**</span></span>  
<span data-ttu-id="bc12f-227">資料集或未繫結至基礎的物件類型的結果集。</span><span class="sxs-lookup"><span data-stu-id="bc12f-227">A data set or result set that is not bound to an underlying object type.</span></span> <span data-ttu-id="bc12f-228">弱型別 XML 資料集的每個資料列所組成的屬性描述的名稱和每個項目類型的泛型資料行集合。</span><span class="sxs-lookup"><span data-stu-id="bc12f-228">Each row in a weakly-typed XML data set is composed of a collection of generic columns in which attributes describe the name and type of each element.</span></span>

<span data-ttu-id="bc12f-229">**web 服務**</span><span class="sxs-lookup"><span data-stu-id="bc12f-229">**web services**</span></span>  
<span data-ttu-id="bc12f-230">應用程式邏輯單元，對其他應用程式提供資料和服務。</span><span class="sxs-lookup"><span data-stu-id="bc12f-230">A unit of application logic providing data and services to other applications.</span></span> <span data-ttu-id="bc12f-231">應用程式使用標準 Web 通訊協定和資料格式 (如 HTTP、XML 和 SOAP) 存取 XML Web 服務，與每個 XML Web 服務實作的方式無關。</span><span class="sxs-lookup"><span data-stu-id="bc12f-231">Applications access XML Web services using standard Web protocols and data formats such as HTTP, XML, and SOAP, independent of how each XML Web service is implemented.</span></span> <span data-ttu-id="bc12f-232">XML Web 服務結合元件基礎開發和 Web 的最佳層面，是 .NET 程式開發模型的基石。</span><span class="sxs-lookup"><span data-stu-id="bc12f-232">XML Web services combine the best aspects of component-based development and the Web, and are a cornerstone of the Microsoft .NET programming model.</span></span>

<span data-ttu-id="bc12f-233">**Web 服務描述語言**</span><span class="sxs-lookup"><span data-stu-id="bc12f-233">**Web Services Description Language**</span></span>  
<span data-ttu-id="bc12f-234">XML 架構語言描述為一組端點運作的服務，在訊息上。</span><span class="sxs-lookup"><span data-stu-id="bc12f-234">An XML-based language that describes a service as a set of endpoints that operate on messages.</span></span> <span data-ttu-id="bc12f-235">WSDL 文件描述服務合約、 作業合約、 訊息合約和用戶端必須使用的資料合約與服務的介面。</span><span class="sxs-lookup"><span data-stu-id="bc12f-235">The WSDL document describes the service contract, operation contracts, message contracts, and data contracts that a client must use to interface with the service.</span></span>

<span data-ttu-id="bc12f-236">**Windows Communication Foundation (WCF)**</span><span class="sxs-lookup"><span data-stu-id="bc12f-236">**Windows Communication Foundation (WCF)**</span></span>  
<span data-ttu-id="bc12f-237">Microsoft 服務導向的通訊基礎結構。</span><span class="sxs-lookup"><span data-stu-id="bc12f-237">A Microsoft service-oriented communication infrastructure.</span></span> <span data-ttu-id="bc12f-238">原本就是，架構會提供用戶端與服務程式設計模型和程式設計模型進行更細微的控制訊息交換的通道。</span><span class="sxs-lookup"><span data-stu-id="bc12f-238">The framework inherently provides clients with a service programming model and a channel programming model for finer control of message exchanges.</span></span>

<span data-ttu-id="bc12f-239">**WS 中繼資料交換 (MEX) 端點**</span><span class="sxs-lookup"><span data-stu-id="bc12f-239">**WS-Metadata Exchange (MEX) endpoint**</span></span>  
<span data-ttu-id="bc12f-240">它會實作 WCF 服務，例如配接器，所公開的端點**IMetadataExchange**介面。</span><span class="sxs-lookup"><span data-stu-id="bc12f-240">An endpoint exposed by a WCF service, such as an adapter, that implements the **IMetadataExchange** interface.</span></span> <span data-ttu-id="bc12f-241">WS 中繼資料交換端點可用來擷取服務描述 (WSDL) 中的目標系統上的配接器所公開的作業。 |</span><span class="sxs-lookup"><span data-stu-id="bc12f-241">A WS-Metadata Exchange endpoint can be used to retrieve a service description (WSDL) for operations exposed by an adapter on the target system.|</span></span>  
  
## <a name="x"></a><span data-ttu-id="bc12f-242">X</span><span class="sxs-lookup"><span data-stu-id="bc12f-242">X</span></span>
<span data-ttu-id="bc12f-243">**XML 結構描述定義語言 (XSD)**</span><span class="sxs-lookup"><span data-stu-id="bc12f-243">**XML Schema definition language (XSD)**</span></span>  
<span data-ttu-id="bc12f-244">結構描述語言。</span><span class="sxs-lookup"><span data-stu-id="bc12f-244">A schema language.</span></span> <span data-ttu-id="bc12f-245">XML 結構描述定義元素、 屬性和資料類型符合全球資訊網協會 (W3C) XML 結構描述第 1 部分： 結構建議事項，XML 結構描述定義語言。</span><span class="sxs-lookup"><span data-stu-id="bc12f-245">An XML Schema defines the elements, attributes, and data types that comply with the World Wide Web Consortium (W3C) XML Schema Part 1: Structures Recommendation for the XML Schema Definition Language.</span></span> <span data-ttu-id="bc12f-246">「W3C XML Schema Part 2: Datatypes Recommendation」則針對定義 XML 結構描述中所使用的資料類型提供建議。</span><span class="sxs-lookup"><span data-stu-id="bc12f-246">The W3C XML Schema Part 2: Datatypes Recommendation is the recommendation for defining data types that are used in XML schemas.</span></span> <span data-ttu-id="bc12f-247">XML 結構描述定義語言讓您定義 XML 訊息的結構和資料類型。</span><span class="sxs-lookup"><span data-stu-id="bc12f-247">The XML Schema definition language enables you to define the structure and data types for XML messages.</span></span>
