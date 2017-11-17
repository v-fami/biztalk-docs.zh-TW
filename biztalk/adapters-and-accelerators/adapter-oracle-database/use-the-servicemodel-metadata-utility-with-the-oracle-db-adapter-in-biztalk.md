---
title: "BizTalk Server 中的 Oracle 資料庫與 BizTalk 配接器使用 ServiceModel 中繼資料公用程式工具 |Microsoft 文件"
description: "使用 svcutil.exe，非預設繫結，或建立 WCF 用戶端類別或 WCF 服務合約與 Oracle 資料庫配接器-BizTalk 配接器組件 (BAP)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8660014-da04-4692-89e8-f14fcb419496
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 143fefc3a35f70e08a9e1288cc019fe6561c2bb1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-servicemodel-metadata-utility-tool-with-the-biztalk-adapter-for-oracle-database"></a><span data-ttu-id="9ac99-103">ServiceModel 中繼資料公用程式工具與 BizTalk Adapter 用於 Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="9ac99-103">Using the ServiceModel Metadata Utility Tool with the BizTalk Adapter for Oracle Database</span></span>
<span data-ttu-id="9ac99-104">您可以使用 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別或作業的 WCF 服務合約 （介面），[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]公開。</span><span class="sxs-lookup"><span data-stu-id="9ac99-104">You can use the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF client class or a WCF service contract (interface) for operations that the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] exposes.</span></span> <span data-ttu-id="9ac99-105">執行 svcutil.exe 產生 WCF 用戶端類別或 WCF 服務合約之後，在您的程式碼中包含所產生的檔案並建立產生之類別的執行個體或實作在 Oracle 上執行作業的合約的 WCF 服務資料庫。</span><span class="sxs-lookup"><span data-stu-id="9ac99-105">After you run svcutil.exe to generate either a WCF client class or a WCF service contract, you can include the generated file in your code and create instances of the generated class or implement a WCF service from the contract to perform operations on the Oracle database.</span></span>  
  
 <span data-ttu-id="9ac99-106">使用 svcutil.exe 會要求您提供的連接，包含憑證的 URI。</span><span class="sxs-lookup"><span data-stu-id="9ac99-106">Using svcutil.exe requires you to supply a connection URI that contains credentials.</span></span> <span data-ttu-id="9ac99-107">因為根據預設，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]停用認證連線 URI，在中，您必須設定使用非預設繫結的 svcutil.exe [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9ac99-107">Because, by default, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] disables credentials in the connection URI, you must configure svcutil.exe to use a non-default binding for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
 <span data-ttu-id="9ac99-108">下列各節說明如何設定 svcutil.exe 以及如何使用 svcutil.exe 產生 WCF 用戶端程式碼或 WCF 服務合約有[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9ac99-108">The following sections show you how to configure svcutil.exe and how to use svcutil.exe to generate WCF client code or a WCF service contract with the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
##  <span data-ttu-id="9ac99-109"><a name="BKMK_ConfigureSvcutil"></a>設定非預設繫結的 svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="9ac99-109"><a name="BKMK_ConfigureSvcutil"></a> Configure svcutil.exe for a non-default binding</span></span>   
 <span data-ttu-id="9ac99-110">若要設定為使用非預設繫結的 svcutil.exe，您必須建立 svcutil.exe 的本機副本，然後建立或修改 svcutil.exe.config 組態檔的本機副本。</span><span class="sxs-lookup"><span data-stu-id="9ac99-110">To configure svcutil.exe to use a non-default binding, you must create a local copy of svcutil.exe and then create or modify a local copy of the svcutil.exe.config configuration file.</span></span>  
  
1.  <span data-ttu-id="9ac99-111">建立資料夾，並將 svcutil.exe 複製到新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="9ac99-111">Create a folder, and copy svcutil.exe into the new folder.</span></span> <span data-ttu-id="9ac99-112">您通常可以找到 svcutil.exe 在 Windows SDK 安裝位置，特別是，C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin。</span><span class="sxs-lookup"><span data-stu-id="9ac99-112">You can typically find svcutil.exe at the Windows SDK installation location, specifically, C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.</span></span>  
  
2.  <span data-ttu-id="9ac99-113">建立名為 svcutil.exe.config 的新資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="9ac99-113">Create a file named svcutil.exe.config in the new folder.</span></span>  
  
3.  <span data-ttu-id="9ac99-114">加入的其他 svcutil.exe.config 檔與用戶端端點的繫結。</span><span class="sxs-lookup"><span data-stu-id="9ac99-114">Add a binding and a client endpoint to the svcutil.exe.config file.</span></span> <span data-ttu-id="9ac99-115">您必須執行 svcutil.exe 從新的資料夾，以確保使用正確的組態。</span><span class="sxs-lookup"><span data-stu-id="9ac99-115">You must run svcutil.exe from the new folder to ensure that the correct configuration is used.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="9ac99-116">用戶端端點的名稱屬性必須指定連線 URI 中使用的配置。</span><span class="sxs-lookup"><span data-stu-id="9ac99-116">The name attribute of the client endpoint must specify the scheme used in the connection URI.</span></span> <span data-ttu-id="9ac99-117">此值區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="9ac99-117">This value is case-sensitive.</span></span>  
  
    ```  
    <configuration>  
      \<system.serviceModel>  
        <client>  
          \<!-- the name should match the required scheme of the WS-Metadata Exchange endpoint   
          and the contract should be "IMetadataExchange" -->  
          <endpoint name="oracledb"  
                    binding="oracleDBBinding"  
                    bindingConfiguration="OracleDBBinding"  
                    contract="IMetadataExchange" />  
        </client>  
        <bindings>  
            <oracleDBBinding>  
                <binding name="OracleDBBinding" acceptCredentialsInUri="true" />  
            </oracleDBBinding>  
        </bindings>  
  
      \</system.serviceModel>  
  
    </configuration>  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="9ac99-118">您可以設定的任何繫結屬性的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結組態中。</span><span class="sxs-lookup"><span data-stu-id="9ac99-118">You can set any of the binding properties of the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] in the binding configuration.</span></span>  
  
 <span data-ttu-id="9ac99-119">如需有關設定非預設繫結 svcutil.exe 的詳細資訊，請參閱 「 自訂安全中繼資料端點 」 中的主題 WCF 文件，網址[http://go.microsoft.com/fwlink/?LinkId=96077](http://go.microsoft.com/fwlink/?LinkId=96077)。</span><span class="sxs-lookup"><span data-stu-id="9ac99-119">For more information about configuring a non-default binding for svcutil.exe, see the "Custom Secure Metadata Endpoint" topic in the WCF documentation at [http://go.microsoft.com/fwlink/?LinkId=96077](http://go.microsoft.com/fwlink/?LinkId=96077).</span></span>  
  
### <a name="configure-a-non-default-binding-for-the-pollingstmt-operation"></a><span data-ttu-id="9ac99-120">設定非預設繫結 POLLINGSTMT 作業</span><span class="sxs-lookup"><span data-stu-id="9ac99-120">Configure a Non-Default Binding for the POLLINGSTMT Operation</span></span>  
 <span data-ttu-id="9ac99-121">若要使用 svcutil.exe 建立 WCF 服務合約 POLLINGSTMT 作業，您必須設定非預設繫結包含**pollingStatement**屬性，除了**acceptCredentialsInUri**.</span><span class="sxs-lookup"><span data-stu-id="9ac99-121">To use svcutil.exe to create a WCF service contract for the POLLINGSTMT operation, you must configure the non-default binding to include the **pollingStatement** property, in addition to **acceptCredentialsInUri**.</span></span> <span data-ttu-id="9ac99-122">**PollingStatement**必須包含目標資料表的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="9ac99-122">The **pollingStatement** must contain the SELECT statement that targets the table.</span></span> <span data-ttu-id="9ac99-123">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會使用這個屬性，以產生類別，表示強型別結果設定 POLLINGSTMT 作業傳回。</span><span class="sxs-lookup"><span data-stu-id="9ac99-123">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses this property to generate the class that represents the strongly-typed result set that the POLLINGSTMT operation returns.</span></span> <span data-ttu-id="9ac99-124">下列範例會示範用來產生 WCF 服務合約 POLLINGSTMT 作業為目標的繫結組態 /SCOTT/EMP 資料表。</span><span class="sxs-lookup"><span data-stu-id="9ac99-124">The following example shows a binding configuration that is used to generate a WCF service contract for a POLLINGSTMT operation that targets the /SCOTT/EMP table.</span></span>  
  
```  
<bindings>  
    <oracleDBBinding>  
        <binding name="OracleDBBinding" acceptCredentialsInUri="true"   
                                   pollingStatement="SELECT * FROM EMP FOR UPDATE" />  
    </oracleDBBinding>  
</bindings>  
```  
  
## <a name="create-a-wcf-client-class-or-wcf-service-contract-with-svcutilexe"></a><span data-ttu-id="9ac99-125">使用 svcutil.exe 建立 WCF 用戶端類別或 WCF 服務合約</span><span class="sxs-lookup"><span data-stu-id="9ac99-125">Create a WCF Client Class or WCF Service Contract with svcutil.exe</span></span>  
 <span data-ttu-id="9ac99-126">若要使用 svcutil.exe 產生 WCF 用戶端程式碼或 WCF 服務合約 （介面），如[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，您必須提供連線 URI，指定 WS 中繼資料交換 (MEX) 端點和作業或想要的 svcutil.exe 作業產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="9ac99-126">To use svcutil.exe to generate WCF client code or a WCF service contract (interface) for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], you must supply a connection URI that specifies an WS-Metadata Exchange (MEX) endpoint and the operation or operations for which you want svcutil.exe to generate code.</span></span> <span data-ttu-id="9ac99-127">您也必須指定連線 URI 中的 Oracle 資料庫的連接認證。</span><span class="sxs-lookup"><span data-stu-id="9ac99-127">You must also specify connection credentials for the Oracle database in the connection URI.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ac99-128">您可以使用具有 svcutil.exe 之前[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，您必須將它設定為使用非預設繫結，如需如何這麼做，請參閱[設定 Oracle 資料庫配接器的 svcutil.exe](#BKMK_ConfigureSvcutil)。</span><span class="sxs-lookup"><span data-stu-id="9ac99-128">Before you can use svcutil.exe with the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], you must configure it to use a non-default binding; for information about how to do this, see [Configuring svcutil.exe for the Oracle Database Adapter](#BKMK_ConfigureSvcutil).</span></span>  
  
 <span data-ttu-id="9ac99-129">您指定 MEX 端點和目標作業中的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]連線 URI 如下：</span><span class="sxs-lookup"><span data-stu-id="9ac99-129">You specify a MEX endpoint and target operations in the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] connection URI in the following manner:</span></span>  
  
-   <span data-ttu-id="9ac99-130">您必須納入 query_string"wsdl 」 參數。</span><span class="sxs-lookup"><span data-stu-id="9ac99-130">You must include the "wsdl" parameter in the query_string.</span></span> <span data-ttu-id="9ac99-131">如果是 query_string 的第一個參數，後方問號 （？） 會指定它。</span><span class="sxs-lookup"><span data-stu-id="9ac99-131">If it is the first parameter in the query_string, it is specified just after the question mark (?).</span></span> <span data-ttu-id="9ac99-132">如果不是第一個參數，它應該在前面加上連字號 (&)。</span><span class="sxs-lookup"><span data-stu-id="9ac99-132">If it is not the first parameter, it should be preceded with an ampersand (&).</span></span>  
  
-   <span data-ttu-id="9ac99-133">您必須遵循一或多個"op"參數"wsdl 」 的參數。</span><span class="sxs-lookup"><span data-stu-id="9ac99-133">You must follow the "wsdl" parameter by one or more "op" parameters.</span></span> <span data-ttu-id="9ac99-134">每個"op"參數加上連字號 (&)，並指定目標作業的節點識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ac99-134">Each "op" parameter is preceded by an ampersand (&) and specifies the node ID of a target operation.</span></span>  
  
 <span data-ttu-id="9ac99-135">下列三個範例示範如何使用 svcutil.exe 以不同的作業為目標。</span><span class="sxs-lookup"><span data-stu-id="9ac99-135">The following three examples show how to target various operations by using svcutil.exe.</span></span>  
  
 <span data-ttu-id="9ac99-136">這個範例會建立 /SCOTT/EMP 資料表上的插入作業的 WCF 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="9ac99-136">This example creates a WCF client class for an Insert operation on the /SCOTT/EMP table.</span></span>  
  
 <span data-ttu-id="9ac99-137">**.\svcutil "oracledb://User=SCOTT;密碼=TIGER@ADAPTER?wsdl&op=http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert"**</span><span class="sxs-lookup"><span data-stu-id="9ac99-137">**.\svcutil "oracledb://User=SCOTT;Password=TIGER@ADAPTER?wsdl&op=http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert"**</span></span>  
  
 <span data-ttu-id="9ac99-138">此範例會建立 WCF 用戶端類別的插入和刪除作業 /SCOTT/EMP 資料表上。</span><span class="sxs-lookup"><span data-stu-id="9ac99-138">This example creates a WCF client class for the Insert and the Delete operations on the /SCOTT/EMP table.</span></span>  
  
 <span data-ttu-id="9ac99-139">**.\svcutil "oracledb://User=SCOTT;密碼=TIGER@ADAPTER?wsdl&op=http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert&op=http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete"**</span><span class="sxs-lookup"><span data-stu-id="9ac99-139">**.\svcutil "oracledb://User=SCOTT;Password=TIGER@ADAPTER?wsdl&op=http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert&op=http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete"**</span></span>  
  
 <span data-ttu-id="9ac99-140">這個範例會建立 WCF 服務合約 POLLLINGSTMT 作業。</span><span class="sxs-lookup"><span data-stu-id="9ac99-140">This example creates a WCF service contract for the POLLLINGSTMT operation.</span></span> <span data-ttu-id="9ac99-141">（若要使用 svcutil.exe 產生 WCF 服務合約 POLLINGSTMT 作業，您必須設定非預設繫結包含輪詢陳述式的 svcutil.exe）。</span><span class="sxs-lookup"><span data-stu-id="9ac99-141">(To use svcutil.exe to generate a WCF service contract for the POLLINGSTMT operation, you must configure a non-default binding for svcutil.exe that includes a polling statement.)</span></span>  
  
 <span data-ttu-id="9ac99-142">**.\svcutil "oracledb://User=SCOTT;密碼=TIGER@ADAPTER?wsdl&op=http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMT"**</span><span class="sxs-lookup"><span data-stu-id="9ac99-142">**.\svcutil "oracledb://User=SCOTT;Password=TIGER@ADAPTER?wsdl&op=http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMT"**</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9ac99-143">您必須在引號內，在命令列上放置連線 URI。</span><span class="sxs-lookup"><span data-stu-id="9ac99-143">You must place the connection URI in quotation marks on the command line.</span></span> <span data-ttu-id="9ac99-144">否則，svcutil.exe 會嘗試擷取作業的中繼資料，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援。</span><span class="sxs-lookup"><span data-stu-id="9ac99-144">Otherwise, svcutil.exe attempts to retrieve metadata for operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support.</span></span> <span data-ttu-id="9ac99-145">這類的嘗試結果便未定義。</span><span class="sxs-lookup"><span data-stu-id="9ac99-145">The results of such an attempt are undefined.</span></span>  
  
 <span data-ttu-id="9ac99-146">根據預設，svcutil.exe 會將產生的程式碼 output.cs 檔案;不過，您可以變更輸出檔的名稱和許多其他選項，svcutil.exe 會使用藉由設定命令列參數。</span><span class="sxs-lookup"><span data-stu-id="9ac99-146">By default, svcutil.exe places the generated code in the output.cs file; however, you can change the name of the output file and many other options that svcutil.exe uses by setting command-line switches.</span></span> <span data-ttu-id="9ac99-147">該 svcutil.exe 支援的選項的詳細資訊，請參閱 < ServiceModel 中繼資料公用程式工具 (Svcutil.exe) > 中的主題 WCF 文件，網址[http://go.microsoft.com/fwlink/?LinkId=72777](http://go.microsoft.com/fwlink/?LinkId=72777)。</span><span class="sxs-lookup"><span data-stu-id="9ac99-147">For more information about the options that svcutil.exe supports, see the "ServiceModel Metadata Utility Tool (Svcutil.exe)" topic in the WCF documentation at [http://go.microsoft.com/fwlink/?LinkId=72777](http://go.microsoft.com/fwlink/?LinkId=72777).</span></span>  
  
 <span data-ttu-id="9ac99-148">Svcutil.exe 不提供的功能來搜尋作業 （例如，透過使用萬用字元）。</span><span class="sxs-lookup"><span data-stu-id="9ac99-148">Svcutil.exe does not provide the capability to search for operations (for example, by using wildcard characters).</span></span> <span data-ttu-id="9ac99-149">您必須明確指定您要當做目標的特定作業的節點識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ac99-149">You must explicitly specify node IDs for the specific operations you want to target.</span></span> <span data-ttu-id="9ac99-150">您無法指定節點只會參考類別目錄的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ac99-150">You cannot specify node IDs that refer only to categories.</span></span> <span data-ttu-id="9ac99-151">如需有關節點識別碼，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]介面，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md)。</span><span class="sxs-lookup"><span data-stu-id="9ac99-151">For more information about the node IDs that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md).</span></span>  
  
 <span data-ttu-id="9ac99-152">[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]提供進階的瀏覽和搜尋功能，可大幅簡化產生 WCF 用戶端類別和 WCF 服務合約。</span><span class="sxs-lookup"><span data-stu-id="9ac99-152">The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] provides advanced browse and search capabilities that can greatly simplify generating a WCF client class and WCF service contract.</span></span> <span data-ttu-id="9ac99-153">如需有關[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[產生的 Oracle 資料庫方案成品 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="9ac99-153">For more information about the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], see [Generating a WCF Client or a WCF Service Contract for Oracle Database Solution Artifacts](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ac99-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ac99-154">See Also</span></span>  
 [<span data-ttu-id="9ac99-155">訊息和訊息結構描述，BizTalk adapter for Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="9ac99-155">Messages and Message Schemas for BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)