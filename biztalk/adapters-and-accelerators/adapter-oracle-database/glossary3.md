---
title: BizTalk Adapter for Oracle 資料庫在 BizTalk 中的詞彙 |Microsoft 文件
description: 常見的詞彙和定義 Oracle 資料庫配接器在 BizTalk Adapter pack (BAP) 中使用
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d386cd36-d8e4-4e5e-806e-0d02e042344f
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fe04f43afa5701afe408c82c4044e6af876f86e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216310"
---
# <a name="glossary"></a><span data-ttu-id="e8b98-103">詞彙</span><span class="sxs-lookup"><span data-stu-id="e8b98-103">Glossary</span></span>
<span data-ttu-id="e8b98-104">下列詞彙和定義會用於[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e8b98-104">The following terms and definitions are used in [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].</span></span>    
  
## <a name="a"></a><span data-ttu-id="e8b98-105">只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，</span><span class="sxs-lookup"><span data-stu-id="e8b98-105">A</span></span>  
  
<span data-ttu-id="e8b98-106">**配接器**</span><span class="sxs-lookup"><span data-stu-id="e8b98-106">**adapter**</span></span>  
<span data-ttu-id="e8b98-107">WCF 架構的元件，可協助 exchange 應用程式 （例如，特定業務系統） 之間的訊息和 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="e8b98-107">A WCF-based component that helps exchange messages between applications (for example, a line-of-business system) and BizTalk Server.</span></span> <span data-ttu-id="e8b98-108">配協器由設計階段元件和執行階段元件組成，進行接收和傳送的作業。</span><span class="sxs-lookup"><span data-stu-id="e8b98-108">The adapter consists of design-time components and run-time components for receive and send operations.</span></span>

<span data-ttu-id="e8b98-109">**配接器用戶端**</span><span class="sxs-lookup"><span data-stu-id="e8b98-109">**adapter client**</span></span>  
<span data-ttu-id="e8b98-110">應用程式透過配接器的特定業務 (LOB) 系統進行互動。</span><span class="sxs-lookup"><span data-stu-id="e8b98-110">An application that interacts with a line-of-business (LOB) system through the adapter.</span></span>  
  
## <a name="b"></a><span data-ttu-id="e8b98-111">B</span><span class="sxs-lookup"><span data-stu-id="e8b98-111">B</span></span>  
  
<span data-ttu-id="e8b98-112">**BFILE**</span><span class="sxs-lookup"><span data-stu-id="e8b98-112">**BFILE**</span></span>  
<span data-ttu-id="e8b98-113">Oracle 資料類型可讓您存取二進位檔案會儲存在檔案系統外部到 Oracle 資料庫中的 Lob。</span><span class="sxs-lookup"><span data-stu-id="e8b98-113">An Oracle data type that enables access to binary file LOBs that are stored in file systems external to the Oracle database.</span></span> <span data-ttu-id="e8b98-114">BFILE 資料行儲存 BFILE 定位器，代表的目錄名稱和檔案名稱，其中包含伺服器檔案系統上的資料。</span><span class="sxs-lookup"><span data-stu-id="e8b98-114">A BFILE column stores a BFILE locator, which represents the directory name and file name that contains the data on the server file system.</span></span>

<span data-ttu-id="e8b98-115">**二進位大型物件**</span><span class="sxs-lookup"><span data-stu-id="e8b98-115">**binary large object**</span></span>  
1.  <span data-ttu-id="e8b98-116">大型資料片段的例如點陣圖、 大型的欄位值、 無法預測資料表大小和是從應用程式的觀點來看不規則的資料特性。</span><span class="sxs-lookup"><span data-stu-id="e8b98-116">A large piece of data, such as a bitmap, characterized by large field values, an unpredictable table size, and data that is formless from the perspective of an application.</span></span>
2.  <span data-ttu-id="e8b98-117">關鍵字指定 BLOB 結構，其中包含的資料區塊的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e8b98-117">A keyword that designates the BLOB structure that contains information about a block of data.</span></span>

<span data-ttu-id="e8b98-118">**繫結**</span><span class="sxs-lookup"><span data-stu-id="e8b98-118">**binding**</span></span>  
<span data-ttu-id="e8b98-119">軟體元件與軟體層連結在一起的程序。</span><span class="sxs-lookup"><span data-stu-id="e8b98-119">A process by which software components and layers are linked together.</span></span> <span data-ttu-id="e8b98-120">安裝網路元件時，便會建立元件的繫結關聯性與相依性。</span><span class="sxs-lookup"><span data-stu-id="e8b98-120">When a network component is installed, the binding relationships and dependencies for the components are established.</span></span> <span data-ttu-id="e8b98-121">繫結使元件得以彼此通訊。</span><span class="sxs-lookup"><span data-stu-id="e8b98-121">Binding allows components to communicate with each other.</span></span> <span data-ttu-id="e8b98-122">在 BizTalk Server 中，此為協調流程配接器-不特定結束點 (連接埠或角色連結) 與實體配接器-特定結束點 (傳送埠/接收埠或合作對象) 之間的已建立對應。</span><span class="sxs-lookup"><span data-stu-id="e8b98-122">In BizTalk Server, an established mapping between an orchestration adapter-agnostic endpoint (port or role link) and physical adapter-specific endpoints (send/receive ports or party).</span></span>

<span data-ttu-id="e8b98-123">**BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="e8b98-123">**BizTalk Server**</span></span>  
<span data-ttu-id="e8b98-124">連接各種不同的軟體。</span><span class="sxs-lookup"><span data-stu-id="e8b98-124">Connects diverse software.</span></span> <span data-ttu-id="e8b98-125">BizTalk Server 可讓您建立和修改處理程序邏輯會使用該軟體。</span><span class="sxs-lookup"><span data-stu-id="e8b98-125">BizTalk Server enables you to create and modify process logic that uses that software.</span></span> <span data-ttu-id="e8b98-126">BizTalk Server 也可讓資訊工作者監控執行中的處理程序、與企業合作夥伴互動並執行其他業務相關工作。</span><span class="sxs-lookup"><span data-stu-id="e8b98-126">BizTalk Server also enables information workers to monitor running processes, interact with trading partners, and perform other business-oriented tasks.</span></span>
  
## <a name="c"></a><span data-ttu-id="e8b98-127">C</span><span class="sxs-lookup"><span data-stu-id="e8b98-127">C</span></span>  
  
<span data-ttu-id="e8b98-128">**通道**</span><span class="sxs-lookup"><span data-stu-id="e8b98-128">**channel**</span></span>  
<span data-ttu-id="e8b98-129">繫結項目的實體實作。</span><span class="sxs-lookup"><span data-stu-id="e8b98-129">A concrete implementation of a binding element.</span></span> <span data-ttu-id="e8b98-130">繫結表示組態，通道則是與該組態相關聯的實作。</span><span class="sxs-lookup"><span data-stu-id="e8b98-130">The binding represents the configuration, and the channel is the implementation associated with that configuration.</span></span> <span data-ttu-id="e8b98-131">因此，沒有與每個繫結項目相關聯的通道。</span><span class="sxs-lookup"><span data-stu-id="e8b98-131">Therefore, there is a channel associated with each binding element.</span></span> <span data-ttu-id="e8b98-132">通道堆疊在彼此的上方來建立繫結的實體實作： 通道堆疊。</span><span class="sxs-lookup"><span data-stu-id="e8b98-132">Channels stack on top of each other to create the concrete implementation of the binding: the channel stack.</span></span>

<span data-ttu-id="e8b98-133">**連線 URI**</span><span class="sxs-lookup"><span data-stu-id="e8b98-133">**connection URI**</span></span>  
<span data-ttu-id="e8b98-134">識別分散式環境中的資源字串。</span><span class="sxs-lookup"><span data-stu-id="e8b98-134">A string that identifies a resource in a distributed environment.</span></span> <span data-ttu-id="e8b98-135">配接器使用的連接統一資源識別元 (URI)，其中包含建立與 LOB 系統的連線所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="e8b98-135">Adapters use a connection Uniform Resource Identifier (URI) that contains the information necessary to establish a connection with the LOB system.</span></span>

<span data-ttu-id="e8b98-136">**合約**</span><span class="sxs-lookup"><span data-stu-id="e8b98-136">**contract**</span></span>  
<span data-ttu-id="e8b98-137">指定集合與存取服務所提供的作業所需的訊息結構。</span><span class="sxs-lookup"><span data-stu-id="e8b98-137">Specifies the collection and structure of messages required to access the operations offered by the service.</span></span>  
  
## <a name="d"></a><span data-ttu-id="e8b98-138">D</span><span class="sxs-lookup"><span data-stu-id="e8b98-138">D</span></span>  
  
<span data-ttu-id="e8b98-139">**資料操作語言 (DML)**</span><span class="sxs-lookup"><span data-stu-id="e8b98-139">**data manipulation language (DML)**</span></span>  
<span data-ttu-id="e8b98-140">用於擷取和操作資料的 SQL 陳述式子集。</span><span class="sxs-lookup"><span data-stu-id="e8b98-140">The subset of SQL statements that is used to retrieve and manipulate data.</span></span> <span data-ttu-id="e8b98-141">此外，DML 陳述式通常會以 SELECT、 INSERT、 UPDATE 或 DELETE 開頭。</span><span class="sxs-lookup"><span data-stu-id="e8b98-141">DML statements typically start with SELECT, INSERT, UPDATE, or DELETE.</span></span>

<span data-ttu-id="e8b98-142">**設計階段經驗**</span><span class="sxs-lookup"><span data-stu-id="e8b98-142">**design-time experience**</span></span>  
<span data-ttu-id="e8b98-143">程序和開發人員在設計階段; 可以執行的作業例如，使用取用配接器服務 BizTalk 專案增益集來擷取訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="e8b98-143">Procedures and operations that a developer performs during design time; for example, using the Consume Adapter Service BizTalk Project Add-in to retrieve message schemas.</span></span>  
  
## <a name="e"></a><span data-ttu-id="e8b98-144">E</span><span class="sxs-lookup"><span data-stu-id="e8b98-144">E</span></span>  
  
<span data-ttu-id="e8b98-145">**端點位址**</span><span class="sxs-lookup"><span data-stu-id="e8b98-145">**endpoint address**</span></span>  
<span data-ttu-id="e8b98-146">網路位址，用於識別 Windows Communication Foundation (WCF) 服務端點的位置。</span><span class="sxs-lookup"><span data-stu-id="e8b98-146">A network address that identifies the location of a Windows Communication Foundation (WCF) service endpoint.</span></span> <span data-ttu-id="e8b98-147">配接器，表示端點位址做為統一資源識別元 (URI) 包含參數的位置和連接的連接。</span><span class="sxs-lookup"><span data-stu-id="e8b98-147">For an adapter, the endpoint address is expressed as a connection Uniform Resource Identifier (URI) that contains location and connection parameters.</span></span> <span data-ttu-id="e8b98-148">配接器可以使用它們來連接到基礎的特定業務 (LOB) 系統。</span><span class="sxs-lookup"><span data-stu-id="e8b98-148">The adapter can use these to establish a connection to the underlying line-of-business (LOB) system.</span></span>

<span data-ttu-id="e8b98-149">**企業單一登入系統 (SSO)**</span><span class="sxs-lookup"><span data-stu-id="e8b98-149">**Enterprise Single Sign-on system (SSO)**</span></span>  
<span data-ttu-id="e8b98-150">SSO 資料庫、主要密碼伺服器以及一或多個企業單一登入 (SSO) 伺服器。</span><span class="sxs-lookup"><span data-stu-id="e8b98-150">An SSO database, a master secret server, and one or more Enterprise Single Sign-On (SSO) servers.</span></span> <span data-ttu-id="e8b98-151">這些伺服器會在 Windows 與非 Windows 認證間進行對應，在 SSO 資料庫中尋找認證，然後用來管理 SSO 系統。</span><span class="sxs-lookup"><span data-stu-id="e8b98-151">These servers do the mapping between the Windows and non-Windows credentials, look up the credentials in the SSO database, and are used for administering the SSO system.</span></span> <span data-ttu-id="e8b98-152">SSO 資料庫也做為組態存放區，保留配接器的自訂組態資料。</span><span class="sxs-lookup"><span data-stu-id="e8b98-152">The SSO database is also used as a configuration store to hold custom configuration data for adapters.</span></span>

<span data-ttu-id="e8b98-153">**可延伸標記語言 (XML)**</span><span class="sxs-lookup"><span data-stu-id="e8b98-153">**Extensible Markup Language (XML)**</span></span>  
<span data-ttu-id="e8b98-154">標記語言，設計用來描述資料。</span><span class="sxs-lookup"><span data-stu-id="e8b98-154">A markup language designed to describe data.</span></span> <span data-ttu-id="e8b98-155">不會預先定義的 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="e8b98-155">XML tags are not predefined.</span></span>  
  
## <a name="g"></a><span data-ttu-id="e8b98-156">G</span><span class="sxs-lookup"><span data-stu-id="e8b98-156">G</span></span>  
  
<span data-ttu-id="e8b98-157">**全域組件快取 (GAC)**</span><span class="sxs-lookup"><span data-stu-id="e8b98-157">**global assembly cache (GAC)**</span></span>  
<span data-ttu-id="e8b98-158">整個電腦的程式碼快取，它會存放供電腦上多個應用程式共用而特別安裝的組件。</span><span class="sxs-lookup"><span data-stu-id="e8b98-158">A machine-wide code cache that stores assemblies specifically installed to be shared by many applications on the computer.</span></span> <span data-ttu-id="e8b98-159">在全域組件快取中部署的應用程式必須具有強式名稱。</span><span class="sxs-lookup"><span data-stu-id="e8b98-159">Applications deployed in the global assembly cache must have a strong name.</span></span>
  
## <a name="i"></a><span data-ttu-id="e8b98-160">I</span><span class="sxs-lookup"><span data-stu-id="e8b98-160">I</span></span>  
  
<span data-ttu-id="e8b98-161">**輸入的作業**</span><span class="sxs-lookup"><span data-stu-id="e8b98-161">**inbound operation**</span></span>  
<span data-ttu-id="e8b98-162">介面卡上的特定業務 (LOB) 系統所叫用作業。</span><span class="sxs-lookup"><span data-stu-id="e8b98-162">An operation that is invoked by a line-of-business (LOB) system on the adapter.</span></span>  
  
## <a name="l"></a><span data-ttu-id="e8b98-163">L</span><span class="sxs-lookup"><span data-stu-id="e8b98-163">L</span></span>  
  
<span data-ttu-id="e8b98-164">**區域命名方法**</span><span class="sxs-lookup"><span data-stu-id="e8b98-164">**local naming method**</span></span>  
<span data-ttu-id="e8b98-165">Oracle 命名 Oracle 資料庫配接器所支援的方法。</span><span class="sxs-lookup"><span data-stu-id="e8b98-165">The Oracle naming method that is supported by the Oracle Database adapter.</span></span> <span data-ttu-id="e8b98-166">在這個命名方法，對 Oracle 用戶端的網路服務名稱解析本機 tnsnames.ora 檔案中的項目。</span><span class="sxs-lookup"><span data-stu-id="e8b98-166">In this naming method, the Oracle client resolves the net service name to an entry in the local tnsnames.ora file.</span></span>  
  
## <a name="m"></a><span data-ttu-id="e8b98-167">M</span><span class="sxs-lookup"><span data-stu-id="e8b98-167">M</span></span>  
  
<span data-ttu-id="e8b98-168">**中繼資料**</span><span class="sxs-lookup"><span data-stu-id="e8b98-168">**metadata**</span></span>  
<span data-ttu-id="e8b98-169">在 WCF 中，指的服務所公開的合約描述。</span><span class="sxs-lookup"><span data-stu-id="e8b98-169">In WCF, refers to a description of the contract exposed by a service.</span></span> <span data-ttu-id="e8b98-170">這就所謂的服務描述，並表示 WSDL 文件中。</span><span class="sxs-lookup"><span data-stu-id="e8b98-170">This is known as the service description and is expressed in a WSDL document.</span></span> <span data-ttu-id="e8b98-171">配接器所公開的中繼資料描述 （介面），它可以在基礎 LOB 系統上執行的作業。</span><span class="sxs-lookup"><span data-stu-id="e8b98-171">The metadata exposed by an adapter describes the (interface to) the operations that it can perform on the underlying LOB system.</span></span>

**[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]**  
<span data-ttu-id="e8b98-172">建置 BizTalk 配接器使用 Web 服務為基礎的開放式標準規格。</span><span class="sxs-lookup"><span data-stu-id="e8b98-172">The specifications for building BizTalk adapters using open standards based on Web services.</span></span>  
  
## <a name="n"></a><span data-ttu-id="e8b98-173">N</span><span class="sxs-lookup"><span data-stu-id="e8b98-173">N</span></span>  
  
<span data-ttu-id="e8b98-174">**命名的方法**</span><span class="sxs-lookup"><span data-stu-id="e8b98-174">**naming method**</span></span>  
<span data-ttu-id="e8b98-175">Oracle 命名的方法會決定對 Oracle 用戶端如何取得 Oracle 資料庫服務 （執行個體） 的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="e8b98-175">Oracle naming methods determine how the Oracle client obtains connection information for an Oracle database service (instance).</span></span> <span data-ttu-id="e8b98-176">您可以設定 Oracle 用戶端使用特定的命名方法，方法是使用 Oracle Net Configuration Assistant。</span><span class="sxs-lookup"><span data-stu-id="e8b98-176">You can configure the Oracle client to use specific naming methods by using the Oracle Net Configuration Assistant.</span></span> <span data-ttu-id="e8b98-177">Oracle 資料庫配接器支援本機命名的方法。</span><span class="sxs-lookup"><span data-stu-id="e8b98-177">The Oracle Database adapter supports the Local Naming method.</span></span>

<span data-ttu-id="e8b98-178">**網路服務名稱**</span><span class="sxs-lookup"><span data-stu-id="e8b98-178">**net service name**</span></span>  
<span data-ttu-id="e8b98-179">別名由 Oracle 用戶端用來取得 Oracle 資料庫的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="e8b98-179">An alias used by the Oracle client to obtain connection information for the Oracle database.</span></span> <span data-ttu-id="e8b98-180">您可以提供網路服務名稱做為其中一個連線 URI 的連線屬性。</span><span class="sxs-lookup"><span data-stu-id="e8b98-180">You supply a net service name as one of the connection properties in the connection URI.</span></span>  
  
## <a name="o"></a><span data-ttu-id="e8b98-181">O</span><span class="sxs-lookup"><span data-stu-id="e8b98-181">O</span></span>  
  
<span data-ttu-id="e8b98-182">**單向**</span><span class="sxs-lookup"><span data-stu-id="e8b98-182">**one-way**</span></span>  
<span data-ttu-id="e8b98-183">寄件者會傳送一則訊息，但沒有回應的訊息交換模式 (MEP) 會傳回收件者。</span><span class="sxs-lookup"><span data-stu-id="e8b98-183">A message exchange pattern (MEP) in which the sender sends a message, but no response is returned by the receiver.</span></span> <span data-ttu-id="e8b98-184">在 BizTalk Server 中，Mep 稱為通訊模式。</span><span class="sxs-lookup"><span data-stu-id="e8b98-184">In BizTalk Server, MEPs are referred to as communication patterns.</span></span>

<span data-ttu-id="e8b98-185">**輸出作業**</span><span class="sxs-lookup"><span data-stu-id="e8b98-185">**outbound operation**</span></span>  
<span data-ttu-id="e8b98-186">作業的特定業務系統 (LOB) 配接器所叫用。</span><span class="sxs-lookup"><span data-stu-id="e8b98-186">An operation that is invoked by the adapter on the line-of-business system (LOB).</span></span>

<span data-ttu-id="e8b98-187">**output.cs**</span><span class="sxs-lookup"><span data-stu-id="e8b98-187">**output.cs**</span></span>  
<span data-ttu-id="e8b98-188">ServiceModel Metadata Utility 工具 (svcutil.exe) 所建立之預設輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="e8b98-188">The default output file created by the ServiceModel Metadata Utility tool (svcutil.exe).</span></span>  
  
## <a name="p"></a><span data-ttu-id="e8b98-189">P</span><span class="sxs-lookup"><span data-stu-id="e8b98-189">P</span></span>  
  
<span data-ttu-id="e8b98-190">**輪詢**</span><span class="sxs-lookup"><span data-stu-id="e8b98-190">**polling**</span></span>  
<span data-ttu-id="e8b98-191">裝置驅動程式用來找出從多個裝置它們是否包含資料傳輸技術。</span><span class="sxs-lookup"><span data-stu-id="e8b98-191">A technique that device drivers use to find out from multiple devices whether they contain data to transmit.</span></span> <span data-ttu-id="e8b98-192">裝置會輪詢一次一個。</span><span class="sxs-lookup"><span data-stu-id="e8b98-192">The devices are polled one at a time.</span></span>

<span data-ttu-id="e8b98-193">**proxy**</span><span class="sxs-lookup"><span data-stu-id="e8b98-193">**proxy**</span></span>  
<span data-ttu-id="e8b98-194">在 WCF 中，是指實作服務所公開的服務合約的 managed 程式碼物件。</span><span class="sxs-lookup"><span data-stu-id="e8b98-194">In WCF, refers to a managed-code object that implements the service contract exposed by a service.</span></span> <span data-ttu-id="e8b98-195">WCF 服務模型根據使用這類的 proxy。</span><span class="sxs-lookup"><span data-stu-id="e8b98-195">The WCF service model is based on the use of such proxies.</span></span> <span data-ttu-id="e8b98-196">在 WCF 服務模型中，.NET 介面來表示服務合約。</span><span class="sxs-lookup"><span data-stu-id="e8b98-196">In the WCF service model, the service contract is expressed as a .NET interface.</span></span>
  
## <a name="r"></a><span data-ttu-id="e8b98-197">R</span><span class="sxs-lookup"><span data-stu-id="e8b98-197">R</span></span>  
  
<span data-ttu-id="e8b98-198">**REF CURSOR**</span><span class="sxs-lookup"><span data-stu-id="e8b98-198">**REF CURSOR**</span></span>  
<span data-ttu-id="e8b98-199">Oracle 的 PL/SQL 資料類型表示的結果集的 Oracle 資料庫中的指標。</span><span class="sxs-lookup"><span data-stu-id="e8b98-199">An Oracle PL/SQL data type that represents a pointer to a result set in the Oracle database.</span></span> <span data-ttu-id="e8b98-200">REF CURSOR 類型啟用輸入和輸出資料流的資料，而且適合用來傳輸大量資料的 PL/SQL 程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="e8b98-200">A REF CURSOR type enables input and output streaming of data, and is ideal for transferring large amounts of data to and from a PL/SQL code block.</span></span>

<span data-ttu-id="e8b98-201">**要求-回應**</span><span class="sxs-lookup"><span data-stu-id="e8b98-201">**request-response**</span></span>  
<span data-ttu-id="e8b98-202">訊息交換模式 (MEP) 寄件者傳送要求訊息與預期來自接收者的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="e8b98-202">A message exchange pattern (MEP) in which the sender sends a request message and expects a response message from the receiver.</span></span> <span data-ttu-id="e8b98-203">在 BizTalk Server 中，Mep 稱為通訊模式。</span><span class="sxs-lookup"><span data-stu-id="e8b98-203">In BizTalk Server, MEPs are referred to as communication patterns.</span></span> <span data-ttu-id="e8b98-204">根據訊息的技術和 （輸入或輸出） 的要求訊息的方向，此模式也稱為要求-回覆或請求-回應。</span><span class="sxs-lookup"><span data-stu-id="e8b98-204">Depending on the messaging technology and the direction of the request message (inbound or outbound), this pattern is also called request-reply or solicit-response.</span></span>

<span data-ttu-id="e8b98-205">**執行階段體驗**</span><span class="sxs-lookup"><span data-stu-id="e8b98-205">**run-time experience**</span></span>  
<span data-ttu-id="e8b98-206">程序和執行階段期間或部署解決方案; 時，開發人員所執行的作業例如，從 BizTalk Server 管理主控台建立實體連接埠繫結。</span><span class="sxs-lookup"><span data-stu-id="e8b98-206">Procedures and operations performed by a developer during run time or when deploying a solution; for example, creating a physical port binding from the BizTalk Server Administration console.</span></span>  
  
## <a name="s"></a><span data-ttu-id="e8b98-207">S</span><span class="sxs-lookup"><span data-stu-id="e8b98-207">S</span></span>  
  
<span data-ttu-id="e8b98-208">**結構描述**</span><span class="sxs-lookup"><span data-stu-id="e8b98-208">**schema**</span></span>  
<span data-ttu-id="e8b98-209">訊息的結構。</span><span class="sxs-lookup"><span data-stu-id="e8b98-209">The structure for a message.</span></span> <span data-ttu-id="e8b98-210">結構描述可以包含多個 ubschema。</span><span class="sxs-lookup"><span data-stu-id="e8b98-210">A schema can contain multiple subschema.</span></span>

<span data-ttu-id="e8b98-211">**ServiceModel Metadata Utility Tool (svcutil.exe)**</span><span class="sxs-lookup"><span data-stu-id="e8b98-211">**ServiceModel Metadata Utility Tool (svcutil.exe)**</span></span>  
<span data-ttu-id="e8b98-212">命令列公用程式所包含的 WCF。</span><span class="sxs-lookup"><span data-stu-id="e8b98-212">A command-line utility that is included with WCF.</span></span> <span data-ttu-id="e8b98-213">它用來建立服務模型 proxy 程式碼，例如配接器的 WCF 服務所公開的服務描述 （中繼資料）。</span><span class="sxs-lookup"><span data-stu-id="e8b98-213">It is used to create service model proxy code from the service description (metadata) that is exposed by a WCF service such as an adapter.</span></span> <span data-ttu-id="e8b98-214">若為輸出的作業，此工具會建立 WCF 用戶端類別和協助程式程式碼;輸入的作業，此工具會建立 WCF 服務合約和協助程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="e8b98-214">For outbound operations, the tool creates a WCF client class and helper code; for inbound operations, the tool creates a WCF service contract and helper code.</span></span>

<span data-ttu-id="e8b98-215">**SOAP （簡易物件存取通訊協定）**</span><span class="sxs-lookup"><span data-stu-id="e8b98-215">**SOAP (Simple Object Access Protocol)**</span></span>  
<span data-ttu-id="e8b98-216">簡單、 以 XML 為基礎的通訊協定，交換結構化，和在分散式環境中輸入資訊。</span><span class="sxs-lookup"><span data-stu-id="e8b98-216">A simple, XML-based protocol for exchanging structured and type information in decentralized, distributed environments.</span></span> <span data-ttu-id="e8b98-217">WCF 為基礎的用戶端和服務來叫用作業，並傳回結果之間的 SOAP 訊息交換。</span><span class="sxs-lookup"><span data-stu-id="e8b98-217">WCF is based on the exchange of SOAP messages between clients and services to invoke operations and return results.</span></span>

<span data-ttu-id="e8b98-218">**SOAP 訊息**</span><span class="sxs-lookup"><span data-stu-id="e8b98-218">**SOAP message**</span></span>  
<span data-ttu-id="e8b98-219">格式正確的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="e8b98-219">A well-formed XML document.</span></span> <span data-ttu-id="e8b98-220">此文件應使用 SOAP 信封和 SOAP 編碼命名空間，且包含選擇性 XML 宣告，後面接著由選擇性 SOAP 標頭與 SOAP 訊息內文所構成的 SOAP 信封 (根項目)。</span><span class="sxs-lookup"><span data-stu-id="e8b98-220">It should use the SOAP envelope and SOAP encoding namespaces and include an optional XML declaration, followed by a SOAP envelope (the root element), which is made up of an optional SOAP header and a SOAP message body.</span></span>

<span data-ttu-id="e8b98-221">**SQL Server Integration Services (SSIS)**</span><span class="sxs-lookup"><span data-stu-id="e8b98-221">**SQL Server Integration Services (SSIS)**</span></span>  
<span data-ttu-id="e8b98-222">此元件可用於匯入、 匯出及轉換來自不同資料來源的資料。</span><span class="sxs-lookup"><span data-stu-id="e8b98-222">A component that is used to import, export, and transform data from different data sources.</span></span> <span data-ttu-id="e8b98-223">先前稱為資料轉換服務 (DTS)。</span><span class="sxs-lookup"><span data-stu-id="e8b98-223">Previously called data transformation service (DTS).</span></span>

<span data-ttu-id="e8b98-224">**強型別資料**</span><span class="sxs-lookup"><span data-stu-id="e8b98-224">**strongly-typed data**</span></span>  
<span data-ttu-id="e8b98-225">資料集或結果集繫結至基礎的物件型別。</span><span class="sxs-lookup"><span data-stu-id="e8b98-225">A data set or result set that is bound to an underlying object type.</span></span> <span data-ttu-id="e8b98-226">強型別 XML 資料集的每個資料列被由型別，名為基礎的物件類型的欄位對應的項目。</span><span class="sxs-lookup"><span data-stu-id="e8b98-226">Each row in a strongly-typed XML data set is composed of typed, named elements that correspond to fields of the underlying object type.</span></span>  
 
## <a name="w"></a><span data-ttu-id="e8b98-227">W</span><span class="sxs-lookup"><span data-stu-id="e8b98-227">W</span></span>  
<span data-ttu-id="e8b98-228">**WCF 通道模型**</span><span class="sxs-lookup"><span data-stu-id="e8b98-228">**WCF channel model**</span></span>  
<span data-ttu-id="e8b98-229">程式設計模型依賴多個介面和其他類型。</span><span class="sxs-lookup"><span data-stu-id="e8b98-229">A programming model that relies on several interfaces and other types.</span></span> <span data-ttu-id="e8b98-230">通道會提供低階的程式設計模型，來傳送和接收訊息。</span><span class="sxs-lookup"><span data-stu-id="e8b98-230">Channels provide a low-level programming model for sending and receiving messages.</span></span>

<span data-ttu-id="e8b98-231">**WCF 用戶端**</span><span class="sxs-lookup"><span data-stu-id="e8b98-231">**WCF client**</span></span>  
<span data-ttu-id="e8b98-232">用戶端應用程式建構，可公開為方法的服務作業。</span><span class="sxs-lookup"><span data-stu-id="e8b98-232">A client-application construct that exposes the service operations as methods.</span></span> <span data-ttu-id="e8b98-233">您可以使用 新增配接器服務參考 Visual Studio 外掛程式或 ServiceModel Metadata Utility Tool 從配接器所公開的中繼資料產生 WCF 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="e8b98-233">You can use the Add Adapter Service Reference Visual Studio Plug-in or the ServiceModel Metadata Utility Tool to generate a WCF client class from the metadata exposed by an adapter.</span></span>

<span data-ttu-id="e8b98-234">**WCF 服務合約**</span><span class="sxs-lookup"><span data-stu-id="e8b98-234">**WCF service contract**</span></span>  
<span data-ttu-id="e8b98-235">服務合約的 managed 程式碼表示法。</span><span class="sxs-lookup"><span data-stu-id="e8b98-235">A managed-code representation of the service contract.</span></span> <span data-ttu-id="e8b98-236">這會表示為介面中的類別和方法的屬性會設定來定義服務、 作業、 訊息，以及用來與服務通訊的資料合約。</span><span class="sxs-lookup"><span data-stu-id="e8b98-236">It is expressed as an interface in which classes and methods are attributed to define the service, operation, message, and data contracts used to communicate with a service.</span></span> <span data-ttu-id="e8b98-237">您可以使用 ServiceModel 中繼資料公用程式工具 」 或 「 新增配接器服務參考 Visual Studio 外掛程式，從配接器所公開的中繼資料產生 WCF 服務合約。</span><span class="sxs-lookup"><span data-stu-id="e8b98-237">You can use the ServiceModel Metadata Utility tool or the Add Adapter Service Reference Visual Studio Plug-in to generate a WCF service contract from the metadata exposed by an adapter.</span></span> <span data-ttu-id="e8b98-238">您實作 WCF 服務合約以接收來自 LOB 系統的作業。</span><span class="sxs-lookup"><span data-stu-id="e8b98-238">You implement the WCF service contract to receive operations from an LOB system.</span></span>

<span data-ttu-id="e8b98-239">**WCF 服務模型**</span><span class="sxs-lookup"><span data-stu-id="e8b98-239">**WCF service model**</span></span>  
<span data-ttu-id="e8b98-240">WCF 程式撰寫模型，服務以 managed 程式碼物件。</span><span class="sxs-lookup"><span data-stu-id="e8b98-240">A WCF programming model in which a service is represented as a managed code object.</span></span> <span data-ttu-id="e8b98-241">服務所公開的作業會表示為具有強型別資料的方法。</span><span class="sxs-lookup"><span data-stu-id="e8b98-241">The operations exposed by the service are represented as methods with strongly-typed data.</span></span>

<span data-ttu-id="e8b98-242">**弱型別資料**</span><span class="sxs-lookup"><span data-stu-id="e8b98-242">**weakly-typed data**</span></span>  
<span data-ttu-id="e8b98-243">資料集或未繫結至基礎的物件類型的結果集。</span><span class="sxs-lookup"><span data-stu-id="e8b98-243">A data set or result set that is not bound to an underlying object type.</span></span> <span data-ttu-id="e8b98-244">弱型別 XML 資料集的每個資料列所組成的屬性描述的名稱和每個項目類型的泛型資料行集合。</span><span class="sxs-lookup"><span data-stu-id="e8b98-244">Each row in a weakly-typed XML data set is composed of a collection of generic columns in which attributes describe the name and type of each element.</span></span>

<span data-ttu-id="e8b98-245">**Web 服務**</span><span class="sxs-lookup"><span data-stu-id="e8b98-245">**Web services**</span></span>  
<span data-ttu-id="e8b98-246">應用程式邏輯單元，對其他應用程式提供資料和服務。</span><span class="sxs-lookup"><span data-stu-id="e8b98-246">A unit of application logic providing data and services to other applications.</span></span> <span data-ttu-id="e8b98-247">應用程式使用標準 Web 通訊協定和資料格式 (如 HTTP、XML 和 SOAP) 存取 XML Web 服務，與每個 XML Web 服務實作的方式無關。</span><span class="sxs-lookup"><span data-stu-id="e8b98-247">Applications access XML Web services using standard Web protocols and data formats such as HTTP, XML, and SOAP, independent of how each XML Web service is implemented.</span></span> <span data-ttu-id="e8b98-248">XML Web 服務結合元件基礎開發和 Web 的最佳層面，是 .NET 程式開發模型的基石。</span><span class="sxs-lookup"><span data-stu-id="e8b98-248">XML Web services combine the best aspects of component-based development and the Web, and are a cornerstone of the Microsoft .NET programming model.</span></span>

<span data-ttu-id="e8b98-249">**Web 服務描述語言 (WSDL)**</span><span class="sxs-lookup"><span data-stu-id="e8b98-249">**Web Services Description Language (WSDL)**</span></span>  
<span data-ttu-id="e8b98-250">XML 架構語言描述為一組端點運作的服務，在訊息上。</span><span class="sxs-lookup"><span data-stu-id="e8b98-250">An XML-based language that describes a service as a set of endpoints that operate on messages.</span></span> <span data-ttu-id="e8b98-251">WSDL 文件描述服務合約、 作業合約、 訊息合約和用戶端必須使用的資料合約與服務的介面。</span><span class="sxs-lookup"><span data-stu-id="e8b98-251">The WSDL document describes the service contract, operation contracts, message contracts, and data contracts that a client must use to interface with the service.</span></span>

<span data-ttu-id="e8b98-252">**Windows Communication Foundation (WCF)**</span><span class="sxs-lookup"><span data-stu-id="e8b98-252">**Windows Communication Foundation (WCF)**</span></span>  
<span data-ttu-id="e8b98-253">Microsoft 服務導向的通訊基礎結構。</span><span class="sxs-lookup"><span data-stu-id="e8b98-253">A Microsoft service-oriented communication infrastructure.</span></span> <span data-ttu-id="e8b98-254">原本就是，架構會提供用戶端與服務程式設計模型和程式設計模型進行更細微的控制訊息交換的通道。</span><span class="sxs-lookup"><span data-stu-id="e8b98-254">The framework inherently provides clients with a service programming model and a channel programming model for finer control of message exchanges.</span></span>

<span data-ttu-id="e8b98-255">**WS 中繼資料交換 (MEX) 端點**</span><span class="sxs-lookup"><span data-stu-id="e8b98-255">**WS-Metadata Exchange (MEX) endpoint**</span></span>  
<span data-ttu-id="e8b98-256">它會實作 WCF 服務，例如配接器，所公開的端點**IMetadataExchange**介面。</span><span class="sxs-lookup"><span data-stu-id="e8b98-256">An endpoint exposed by a WCF service, such as an adapter, that implements the **IMetadataExchange** interface.</span></span> <span data-ttu-id="e8b98-257">WS 中繼資料交換端點可用來擷取服務描述 (WSDL) 的目標系統上的配接器所公開的作業。</span><span class="sxs-lookup"><span data-stu-id="e8b98-257">A WS-Metadata Exchange endpoint can be used to retrieve a service description (WSDL) for operations exposed by an adapter on the target system.</span></span>
  
## <a name="x"></a><span data-ttu-id="e8b98-258">X</span><span class="sxs-lookup"><span data-stu-id="e8b98-258">X</span></span>  
  
<span data-ttu-id="e8b98-259">**XML 結構描述定義語言 (XSD)**</span><span class="sxs-lookup"><span data-stu-id="e8b98-259">**XML Schema definition language (XSD)**</span></span>  
<span data-ttu-id="e8b98-260">結構描述語言。</span><span class="sxs-lookup"><span data-stu-id="e8b98-260">A schema language.</span></span> <span data-ttu-id="e8b98-261">XML 結構描述定義元素、 屬性和資料類型符合全球資訊網協會 (W3C) XML 結構描述第 1 部分： 結構建議事項，XML 結構描述定義語言。</span><span class="sxs-lookup"><span data-stu-id="e8b98-261">An XML Schema defines the elements, attributes, and data types that comply with the World Wide Web Consortium (W3C) XML Schema Part 1: Structures Recommendation for the XML Schema Definition Language.</span></span> <span data-ttu-id="e8b98-262">「W3C XML Schema Part 2: Datatypes Recommendation」則針對定義 XML 結構描述中所使用的資料類型提供建議。</span><span class="sxs-lookup"><span data-stu-id="e8b98-262">The W3C XML Schema Part 2: Datatypes Recommendation is the recommendation for defining data types that are used in XML schemas.</span></span> <span data-ttu-id="e8b98-263">XML 結構描述定義語言讓您定義 XML 訊息的結構和資料類型。</span><span class="sxs-lookup"><span data-stu-id="e8b98-263">The XML Schema definition language enables you to define the structure and data types for XML messages.</span></span>