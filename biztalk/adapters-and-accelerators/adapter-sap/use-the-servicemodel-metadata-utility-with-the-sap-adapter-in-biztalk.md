---
title: "使用 BizTalk adapter 的 ServiceModel Metadata Utility Tool for mySAP Business Suite |Microsoft 文件"
description: "使用 svcutil.exe，非預設繫結，或使用 SAP 配接器-BizTalk 配接器組件 (BAP) 來建立 WCF 用戶端類別或 WCF 服務合約"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ServiceModel Metadata Utility Tool, creating a WCF Client Class or a WCF service contract with the tool
- ServiceModel Metadata Utility Tool, configuring the tool for the adapter
ms.assetid: 7ac08012-bb12-4983-9402-be84fe3997d8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15c4612db6e3cde4e46385b1c5d1810fbb00eb70
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="using-the-servicemodel-metadata-utility-tool-with-the-biztalk-adapter-for-mysap-business-suite"></a><span data-ttu-id="ac163-103">使用 BizTalk adapter 的 ServiceModel Metadata Utility Tool for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="ac163-103">Using the ServiceModel Metadata Utility Tool with the BizTalk Adapter for mySAP Business Suite</span></span>
<span data-ttu-id="ac163-104">您可以使用 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別或作業的 WCF 服務合約 （介面），[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]公開。</span><span class="sxs-lookup"><span data-stu-id="ac163-104">You can use the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF client class or a WCF service contract (interface) for operations that the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] exposes.</span></span> <span data-ttu-id="ac163-105">執行 svcutil.exe 產生 WCF 用戶端類別或 WCF 服務合約之後，您可以在您的程式碼中包含所產生的檔案和建立所產生類別的執行個體或從實作 WCF 服務產生的介面上的 SAP 執行作業系統。</span><span class="sxs-lookup"><span data-stu-id="ac163-105">After you run svcutil.exe to generate either a WCF client class or a WCF service contract, you can include the generated file in your code and create instances of the generated class or implement a WCF service from the generated interface to perform operations on the SAP system.</span></span>  
  
 <span data-ttu-id="ac163-106">使用 svcutil.exe 會要求您提供的連接，包含憑證的 URI。</span><span class="sxs-lookup"><span data-stu-id="ac163-106">Using svcutil.exe requires you to supply a connection URI that contains credentials.</span></span> <span data-ttu-id="ac163-107">因為根據預設，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]停用認證連線 URI，在中，您必須設定使用非預設繫結的 svcutil.exe [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ac163-107">Because, by default, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] disables credentials in the connection URI, you must configure svcutil.exe to use a non-default binding for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="ac163-108">您也可以設定其他繫結屬性中的非預設繫結。例如，若要建立 BAPI 作業的 WCF 用戶端，您必須設定**EnableSafeTyping**內容繫結至**true**。</span><span class="sxs-lookup"><span data-stu-id="ac163-108">You can also configure other binding properties in the non-default binding; for example, to create a WCF client for BAPI operations, you must set the **EnableSafeTyping** binding property to **true**.</span></span>  
  
 <span data-ttu-id="ac163-109">下列各節說明如何設定 svcutil.exe 以及如何使用 svcutil.exe 產生 WCF 用戶端程式碼或 WCF 服務合約有[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ac163-109">The following sections show you how to configure svcutil.exe and how to use svcutil.exe to generate WCF client code or a WCF service contract with the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
##  <a name="BKMK_ConfigureSvcutil"></a><span data-ttu-id="ac163-110">設定 SAP 配接器的 svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="ac163-110">Configuring svcutil.exe for the SAP Adapter</span></span>  
 <span data-ttu-id="ac163-111">若要設定為使用非預設繫結的 svcutil.exe，您必須建立 svcutil.exe 的本機副本，然後建立或修改 svcutil.exe.config 組態檔的本機副本。</span><span class="sxs-lookup"><span data-stu-id="ac163-111">To configure svcutil.exe to use a non-default binding, you must create a local copy of svcutil.exe and then create or modify a local copy of the svcutil.exe.config configuration file.</span></span>  
  
1.  <span data-ttu-id="ac163-112">建立資料夾，並將 svcutil.exe 複製到新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ac163-112">Create a folder, and copy svcutil.exe into the new folder.</span></span> <span data-ttu-id="ac163-113">您通常可以找到 svcutil.exe 在 Windows SDK 安裝位置，特別是，C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin。</span><span class="sxs-lookup"><span data-stu-id="ac163-113">You can typically find svcutil.exe at the Windows SDK installation location, specifically, C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.</span></span>  
  
2.  <span data-ttu-id="ac163-114">建立名為 svcutil.exe.config 的新資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="ac163-114">Create a file named svcutil.exe.config in the new folder.</span></span>  
  
3.  <span data-ttu-id="ac163-115">加入的其他 svcutil.exe.config 檔與用戶端端點的繫結。</span><span class="sxs-lookup"><span data-stu-id="ac163-115">Add a binding and a client endpoint to the svcutil.exe.config file.</span></span> <span data-ttu-id="ac163-116">您必須執行 svcutil.exe 從新的資料夾，以確保使用正確的組態。</span><span class="sxs-lookup"><span data-stu-id="ac163-116">You must run svcutil.exe from the new folder to ensure that the correct configuration is used.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="ac163-117">用戶端端點的名稱屬性必須指定連線 URI 中使用的配置。</span><span class="sxs-lookup"><span data-stu-id="ac163-117">The name attribute of the client endpoint must specify the scheme used in the connection URI.</span></span> <span data-ttu-id="ac163-118">此值區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="ac163-118">This value is case-sensitive.</span></span>  
  
    ```  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <!-- the name should match the required scheme of the WS-Metadata Exchange endpoint   
          and the contract should be "IMetadataExchange" -->  
          <endpoint name="sap"  
                    binding="sapBinding"  
                    bindingConfiguration="SAPBinding"  
                    contract="IMetadataExchange" />  
        </client>  
        <bindings>  
          <sapBinding>  
            <binding name="SAPBinding" acceptCredentialsInUri="true"/>  
          </sapBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
 <span data-ttu-id="ac163-119">您可以設定的任何繫結屬性的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結組態中。</span><span class="sxs-lookup"><span data-stu-id="ac163-119">You can set any of the binding properties of the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in the binding configuration.</span></span> <span data-ttu-id="ac163-120">例如，您可以指定要使用 svcutil.exe 產生 WCF 用戶端 BAPI 作業的下列非預設繫結。</span><span class="sxs-lookup"><span data-stu-id="ac163-120">For example, you could specify the following non-default binding to use svcutil.exe to generate a WCF client for BAPI operations.</span></span>  
  
```  
<bindings>  
  <sapBinding>  
    <binding name="SAPBinding" acceptCredentialsInUri="true"/>  
  </sapBinding>  
</bindings>  
```  
  
 <span data-ttu-id="ac163-121">如需有關設定非預設繫結 svcutil.exe 的詳細資訊，請參閱[自訂安全中繼資料端點](https://msdn.microsoft.com/library/aa395212.aspx)。</span><span class="sxs-lookup"><span data-stu-id="ac163-121">For more information about configuring a non-default binding for svcutil.exe, see the [Custom Secure Metadata Endpoint](https://msdn.microsoft.com/library/aa395212.aspx).</span></span>
  
## <a name="creating-a-wcf-client-class-or-a-wcf-service-contract-with-svcutilexe"></a><span data-ttu-id="ac163-122">使用 svcutil.exe 建立 WCF 用戶端類別或 WCF 服務合約</span><span class="sxs-lookup"><span data-stu-id="ac163-122">Creating a WCF Client Class or a WCF Service Contract with svcutil.exe</span></span>  
 <span data-ttu-id="ac163-123">若要使用 svcutil.exe 產生 WCF 用戶端程式碼或 WCF 服務合約 （介面），如[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，您必須提供連線 URI，指定 WS 中繼資料交換 (MEX) 端點和作業或想要的 svcutil.exe 作業產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="ac163-123">To use svcutil.exe to generate WCF client code or a WCF service contract (interface) for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], you must supply a connection URI that specifies a WS-Metadata Exchange (MEX) endpoint and the operation or operations for which you want svcutil.exe to generate code.</span></span> <span data-ttu-id="ac163-124">您也必須指定連線 URI 中的 SAP 系統的連接認證。</span><span class="sxs-lookup"><span data-stu-id="ac163-124">You must also specify connection credentials for the SAP system in the connection URI.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac163-125">您可以使用具有 svcutil.exe 之前[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，您必須將它設定為使用非預設繫結，如需如何這麼做，請參閱[SAP 配接器的設定 svcutil.exe](#BKMK_ConfigureSvcutil)。</span><span class="sxs-lookup"><span data-stu-id="ac163-125">Before you can use svcutil.exe with the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], you must configure it to use a non-default binding; for information about how to do this, see [Configuring svcutil.exe for the SAP Adapter](#BKMK_ConfigureSvcutil).</span></span>  
  
 <span data-ttu-id="ac163-126">您指定 MEX 端點和目標作業中的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]連線 URI 如下：</span><span class="sxs-lookup"><span data-stu-id="ac163-126">You specify a MEX endpoint and target operations in the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] connection URI in the following manner:</span></span>  
  
-   <span data-ttu-id="ac163-127">您必須在查詢字串中包含"wsdl 」 參數。</span><span class="sxs-lookup"><span data-stu-id="ac163-127">You must include the "wsdl" parameter in the query string.</span></span> <span data-ttu-id="ac163-128">如果查詢字串中的第一個參數，它會指定後方問號 （？）。</span><span class="sxs-lookup"><span data-stu-id="ac163-128">If it is the first parameter in the query string, it is specified just after the question mark (?).</span></span> <span data-ttu-id="ac163-129">如果不是第一個參數，它應該在前面加上連字號 (&)。</span><span class="sxs-lookup"><span data-stu-id="ac163-129">If it is not the first parameter, it should be preceded with an ampersand (&).</span></span>  
  
-   <span data-ttu-id="ac163-130">您必須遵循一或多個"op"參數"wsdl 」 的參數。</span><span class="sxs-lookup"><span data-stu-id="ac163-130">You must follow the "wsdl" parameter by one or more "op" parameters.</span></span> <span data-ttu-id="ac163-131">每個"op"參數加上連字號 (&)，並指定目標作業的節點識別碼。</span><span class="sxs-lookup"><span data-stu-id="ac163-131">Each "op" parameter is preceded by an ampersand (&) and specifies the node ID of a target operation.</span></span>  
  
 <span data-ttu-id="ac163-132">下列三個範例示範如何使用 svcutil.exe 以不同的作業為目標。</span><span class="sxs-lookup"><span data-stu-id="ac163-132">The following three examples show how to target various operations by using svcutil.exe.</span></span>  
  
 <span data-ttu-id="ac163-133">這個範例會針對 RFC_CALCULATE_TAXES 建立 WCF 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="ac163-133">This example creates a WCF client class for RFC_CALCULATE_TAXES.</span></span>  
  
 <span data-ttu-id="ac163-134">**。 \svcutil"sap://User=YourUserName;Passwd = YourPassword;用戶端 = 800;Lang = EN;@a/YourSAPHost/00？ wsdl （& s) op = http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CALCULATE_TAXES"**</span><span class="sxs-lookup"><span data-stu-id="ac163-134">**.\svcutil "sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?wsdl&op=http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CALCULATE_TAXES"**</span></span>  
  
 <span data-ttu-id="ac163-135">此範例會建立 WCF 用戶端類別 SALESORDER_CREATEFROMDAT201 和 SALESORDER_CREATEFROMDAT202 IDOC。</span><span class="sxs-lookup"><span data-stu-id="ac163-135">This example creates a WCF client class for both the SALESORDER_CREATEFROMDAT201 and SALESORDER_CREATEFROMDAT202 IDOC.</span></span>  
  
 <span data-ttu-id="ac163-136">**。 \svcutil"sap://User=YourUserName;Passwd = YourPassword;用戶端 = 800;Lang = EN;@a/YourSAPHost/00？ wsdl （& s) op = http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT201//620/Send & op = http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT202//620/Send"**</span><span class="sxs-lookup"><span data-stu-id="ac163-136">**.\svcutil "sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?wsdl&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT201//620/Send&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT202//620/Send"**</span></span>  
  
 <span data-ttu-id="ac163-137">這個範例會建立從 SAP 系統接收 SALESORDER_CREATEFROMDAT201 IDOC 的 WCF 服務合約。</span><span class="sxs-lookup"><span data-stu-id="ac163-137">This example creates a WCF service contract to receive the SALESORDER_CREATEFROMDAT201 IDOC from the SAP system.</span></span> <span data-ttu-id="ac163-138">節點識別碼會指定接收作業。</span><span class="sxs-lookup"><span data-stu-id="ac163-138">The NODE ID specifies a Receive operation.</span></span> <span data-ttu-id="ac163-139">此範例中處理的擷取中繼資料，因為沒有需要連線 URI query_string 中指定的接聽程式參數。</span><span class="sxs-lookup"><span data-stu-id="ac163-139">Because this example deals with retrieving metadata, there is no need to specify the listener parameters in the query_string of the connection URI.</span></span>  
  
 <span data-ttu-id="ac163-140">**。 \svcutil"sap://User=YourUserName;Passwd = YourPassword;用戶端 = 800;Lang = EN;@a/YourSAPHost/00？ wsdl （& s) op = http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT201//620/Receive"**</span><span class="sxs-lookup"><span data-stu-id="ac163-140">**.\svcutil "sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?wsdl&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT201//620/Receive"**</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ac163-141">您必須在引號內，在命令列上放置連線 URI。</span><span class="sxs-lookup"><span data-stu-id="ac163-141">You must place the connection URI in quotation marks on the command line.</span></span> <span data-ttu-id="ac163-142">否則，svcutil.exe 會嘗試擷取作業的中繼資料，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援。</span><span class="sxs-lookup"><span data-stu-id="ac163-142">Otherwise, svcutil.exe attempts to retrieve metadata for operations that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not support.</span></span> <span data-ttu-id="ac163-143">這類的嘗試結果便未定義。</span><span class="sxs-lookup"><span data-stu-id="ac163-143">The results of such an attempt are undefined.</span></span>  
  
 <span data-ttu-id="ac163-144">根據預設，svcutil.exe 會將產生的程式碼 output.cs 檔案;不過，您可以變更輸出檔的名稱和許多其他選項，svcutil.exe 會使用藉由設定命令列參數。</span><span class="sxs-lookup"><span data-stu-id="ac163-144">By default, svcutil.exe places the generated code in the output.cs file; however, you can change the name of the output file and many other options that svcutil.exe uses by setting command-line switches.</span></span> <span data-ttu-id="ac163-145">該 svcutil.exe 支援的選項的詳細資訊，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx)。</span><span class="sxs-lookup"><span data-stu-id="ac163-145">For more information about the options that svcutil.exe supports, see the [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx).</span></span>
  
 <span data-ttu-id="ac163-146">Svcutil.exe 不提供的功能來搜尋作業 （例如，透過使用萬用字元）。</span><span class="sxs-lookup"><span data-stu-id="ac163-146">Svcutil.exe does not provide the capability to search for operations (for example, by using wildcard characters).</span></span> <span data-ttu-id="ac163-147">您必須明確指定您要當做目標的特定作業的節點識別碼。</span><span class="sxs-lookup"><span data-stu-id="ac163-147">You must explicitly specify node IDs for the specific operations you want to target.</span></span> <span data-ttu-id="ac163-148">作業的節點識別碼就相當於其訊息的動作字串。</span><span class="sxs-lookup"><span data-stu-id="ac163-148">The node ID of an operation is equivalent to its message action string.</span></span> <span data-ttu-id="ac163-149">您無法指定節點只會參考類別目錄的識別碼。</span><span class="sxs-lookup"><span data-stu-id="ac163-149">You cannot specify node IDs that refer only to categories.</span></span> <span data-ttu-id="ac163-150">如需有關節點識別碼，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]介面，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md)。</span><span class="sxs-lookup"><span data-stu-id="ac163-150">For more information about the node IDs that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).</span></span>  
  
 <span data-ttu-id="ac163-151">[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]提供進階的瀏覽和搜尋功能，可大幅簡化產生 WCF 用戶端類別和 WCF 服務合約。</span><span class="sxs-lookup"><span data-stu-id="ac163-151">The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] provides advanced browse and search capabilities that can greatly simplify generating a WCF client class and WCF service contract.</span></span> <span data-ttu-id="ac163-152">如需有關[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SAP 方案成品](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="ac163-152">For more information about the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], see [Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span>  
  
