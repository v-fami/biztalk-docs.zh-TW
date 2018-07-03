---
title: 使用 BizTalk 配接器的 ServiceModel Metadata Utility Tool for Siebel eBusiness 應用程式 |Microsoft Docs
description: 使用 svcutil.exe，非預設繫結，或使用 Siebel 配接器-BizTalk 配接器組件 (BAP) 中建立的 WCF 用戶端類別或 WCF 服務合約
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03d16481-cc8b-4e28-a33c-92e48a9a7e8f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9741b970873b97401968f7b87ee76ac853c60ae4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987383"
---
# <a name="using-the-servicemodel-metadata-utility-tool-with-the-biztalk-adapter-for-siebel-ebusiness-applications"></a><span data-ttu-id="07d2b-103">使用 BizTalk 配接器的 ServiceModel Metadata Utility Tool for Siebel eBusiness 應用程式</span><span class="sxs-lookup"><span data-stu-id="07d2b-103">Using the ServiceModel Metadata Utility Tool with the BizTalk Adapter for Siebel eBusiness Applications</span></span>
<span data-ttu-id="07d2b-104">您可以使用 ServiceModel Metadata Utility Tool (svcutil.exe)，以產生 WCF 用戶端類別的作業，[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]公開 （expose)。</span><span class="sxs-lookup"><span data-stu-id="07d2b-104">You can use the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF client class for operations that the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] exposes.</span></span> <span data-ttu-id="07d2b-105">執行 svcutil.exe 以產生 WCF 用戶端類別之後，您可以在程式碼中包含所產生的檔案，並建立 Siebel 系統上執行作業的 WCF 用戶端類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="07d2b-105">After you run svcutil.exe to generate a WCF client class, you can include the generated file in your code and create instances of the WCF client class to perform operations on the Siebel system.</span></span>  
  
 <span data-ttu-id="07d2b-106">使用 svcutil.exe 要求您提供的連接 URI，其中包含的認證。</span><span class="sxs-lookup"><span data-stu-id="07d2b-106">Using svcutil.exe requires you to supply a connection URI that contains credentials.</span></span> <span data-ttu-id="07d2b-107">因為根據預設，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]停用認證的連線 URI，在中，您必須設定要使用的非預設繫結的 svcutil.exe [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="07d2b-107">Because, by default, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] disables credentials in the connection URI, you must configure svcutil.exe to use a non-default binding for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="07d2b-108">您也可以在非預設繫結中設定其他繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="07d2b-108">You can also configure other binding properties in the non-default binding.</span></span>  
  
 <span data-ttu-id="07d2b-109">下列各節說明如何設定 svcutil.exe 以及如何使用 svcutil.exe 產生 WCF 用戶端程式碼與[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="07d2b-109">The following sections show you how to configure svcutil.exe and how to use svcutil.exe to generate WCF client code with the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
##  <a name="BKMK_ConfigureSvcutil"></a><span data-ttu-id="07d2b-110">設定非預設繫結的 svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="07d2b-110">Configure svcutil.exe for a non-default binding</span></span>   
 <span data-ttu-id="07d2b-111">若要設定為使用非預設繫結的 svcutil.exe，您必須建立本機的 svcutil.exe 複本，然後建立或修改 svcutil.exe.config 組態檔的本機副本。</span><span class="sxs-lookup"><span data-stu-id="07d2b-111">To configure svcutil.exe to use a non-default binding, you must create a local copy of svcutil.exe and then create or modify a local copy of the svcutil.exe.config configuration file.</span></span>  
  
 
1.  <span data-ttu-id="07d2b-112">建立資料夾，並將 svcutil.exe 複製到新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="07d2b-112">Create a folder, and copy svcutil.exe into the new folder.</span></span> <span data-ttu-id="07d2b-113">您通常可以找到 svcutil.exe 在 Windows SDK 安裝位置，特別是，C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin。</span><span class="sxs-lookup"><span data-stu-id="07d2b-113">You can typically find svcutil.exe at the Windows SDK installation location, specifically, C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.</span></span>  
  
2.  <span data-ttu-id="07d2b-114">建立名為 svcutil.exe.config 的新資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="07d2b-114">Create a file named svcutil.exe.config in the new folder.</span></span>  
  
3.  <span data-ttu-id="07d2b-115">將繫結和用戶端端點新增至 svcutil.exe.config 檔中。</span><span class="sxs-lookup"><span data-stu-id="07d2b-115">Add a binding and a client endpoint to the svcutil.exe.config file.</span></span> <span data-ttu-id="07d2b-116">您必須從新的資料夾，以確定正確的組態，用來執行 svcutil.exe。</span><span class="sxs-lookup"><span data-stu-id="07d2b-116">You must run svcutil.exe from the new folder to ensure that the correct configuration is used.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="07d2b-117">用戶端端點的名稱屬性必須指定連線 URI 中使用的配置。</span><span class="sxs-lookup"><span data-stu-id="07d2b-117">The name attribute of the client endpoint must specify the scheme used in the connection URI.</span></span> <span data-ttu-id="07d2b-118">此值區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="07d2b-118">This value is case-sensitive.</span></span>  
  
    ```  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <!-- the name should match the required scheme of the Metadata Exchange endpoint   
          and the contract should be "IMetadataExchange" -->  
          <endpoint name="siebel"  
            binding="siebelBinding"  
            bindingConfiguration="SiebelBinding"  
            contract="IMetadataExchange" />  
        </client>  
        <bindings>  
          <siebelBinding>  
            <binding name="SiebelBinding" acceptCredentialsInUri="true" />  
          </siebelBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="07d2b-119">您可以設定的任何繫結屬性的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結組態中。</span><span class="sxs-lookup"><span data-stu-id="07d2b-119">You can set any of the binding properties of the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] in the binding configuration.</span></span>  
  
 <span data-ttu-id="07d2b-120">如需有關如何設定非預設繫結 svcutil.exe 的詳細資訊，請參閱 「 自訂安全中繼資料端點 」 主題中的 WCF 文件[ http://go.microsoft.com/fwlink/?LinkId=96077 ](http://go.microsoft.com/fwlink/?LinkId=96077)。</span><span class="sxs-lookup"><span data-stu-id="07d2b-120">For more information about configuring a non-default binding for svcutil.exe, see the "Custom Secure Metadata Endpoint" topic in the WCF documentation at [http://go.microsoft.com/fwlink/?LinkId=96077](http://go.microsoft.com/fwlink/?LinkId=96077).</span></span>  
  
## <a name="creating-a-wcf-client-class-with-svcutilexe"></a><span data-ttu-id="07d2b-121">使用 svcutil.exe 建立 WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="07d2b-121">Creating a WCF Client Class with svcutil.exe</span></span>  
 <span data-ttu-id="07d2b-122">若要使用 svcutil.exe 產生 WCF 用戶端程式碼[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，您必須提供的連線 URI，指定**IMetadataExchange** (mex) 端點和作業或作業要為其產生的 svcutil.exe程式碼。</span><span class="sxs-lookup"><span data-stu-id="07d2b-122">To use svcutil.exe to generate WCF client code for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], you must supply a connection URI that specifies an **IMetadataExchange** (mex) endpoint and the operation or operations for which you want svcutil.exe to generate code.</span></span> <span data-ttu-id="07d2b-123">您也必須指定連線 URI Siebel 系統的連線認證。</span><span class="sxs-lookup"><span data-stu-id="07d2b-123">You must also specify connection credentials for the Siebel system in the connection URI.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07d2b-124">您可以使用具有 svcutil.exe 之前[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，您必須將它設定為使用非預設繫結，如需如何這麼做，請參閱[Siebel 配接器設定 svcutil.exe](#BKMK_ConfigureSvcutil)。</span><span class="sxs-lookup"><span data-stu-id="07d2b-124">Before you can use svcutil.exe with the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], you must configure it to use a non-default binding; for information about how to do this, see [Configuring svcutil.exe for the Siebel Adapter](#BKMK_ConfigureSvcutil).</span></span>  
  
 <span data-ttu-id="07d2b-125">您指定 mex 端點和目標作業在[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]連線 URI，以下列方式：</span><span class="sxs-lookup"><span data-stu-id="07d2b-125">You specify a mex endpoint and target operations in the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] connection URI in the following manner:</span></span>  
  
- <span data-ttu-id="07d2b-126">您必須納入 query_string"wsdl 」 參數。</span><span class="sxs-lookup"><span data-stu-id="07d2b-126">You must include the "wsdl" parameter in the query_string.</span></span> <span data-ttu-id="07d2b-127">如果是 query_string 的第一個參數，指定只在問號 （？） 之後。</span><span class="sxs-lookup"><span data-stu-id="07d2b-127">If it is the first parameter in the query_string, it is specified just after the question mark (?).</span></span> <span data-ttu-id="07d2b-128">如果不是第一個參數，它應該前面加上連字號 (&)。</span><span class="sxs-lookup"><span data-stu-id="07d2b-128">If it is not the first parameter, it should be preceded with an ampersand (&).</span></span>  
  
- <span data-ttu-id="07d2b-129">您必須遵循一或多個"op"參數"wsdl 」 的參數。</span><span class="sxs-lookup"><span data-stu-id="07d2b-129">You must follow the "wsdl" parameter by one or more "op" parameters.</span></span> <span data-ttu-id="07d2b-130">每個 「 操作 」 前面加上連字號 (&)，並指定目標作業的節點識別碼。</span><span class="sxs-lookup"><span data-stu-id="07d2b-130">Each "op" parameter is preceded by an ampersand (&) and specifies the node ID of a target operation.</span></span>  
  
  <span data-ttu-id="07d2b-131">下列兩個範例示範如何使用 svcutil.exe 針對各種作業。</span><span class="sxs-lookup"><span data-stu-id="07d2b-131">The following two examples show how to target various operations by using svcutil.exe.</span></span>  
  
  <span data-ttu-id="07d2b-132">這個範例會建立 WCF 用戶端類別 ACCOUNT\ACCOUNT 商務物件上插入作業。</span><span class="sxs-lookup"><span data-stu-id="07d2b-132">This example creates a WCF client class for an insert operation on the ACCOUNT\ACCOUNT Business Object.</span></span>  
  
  <span data-ttu-id="07d2b-133">**.\svcutil "siebel://Username=YourUserName;Password=YourPassword@Siebel_server:1234?SiebelEnterpriseServer=ent_server&SiebelObjectManager=obj_mgr&Language=enu&wsdl&op=http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert"**</span><span class="sxs-lookup"><span data-stu-id="07d2b-133">**.\svcutil "siebel://Username=YourUserName;Password=YourPassword@Siebel_server:1234?SiebelEnterpriseServer=ent_server&SiebelObjectManager=obj_mgr&Language=enu&wsdl&op=http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert"**</span></span>  
  
  <span data-ttu-id="07d2b-134">這個範例會建立 WCF 用戶端類別的插入作業和 ACCOUNT\ACCOUNT 商務物件上的刪除作業。</span><span class="sxs-lookup"><span data-stu-id="07d2b-134">This example creates a WCF client class for both an insert operation and a delete operation on the ACCOUNT\ACCOUNT Business Object.</span></span>  
  
  <span data-ttu-id="07d2b-135">**.\svcutil " siebel://Username=YourUserName;Password=YourPassword@Siebel_server:1234?SiebelEnterpriseServer=ent_server&SiebelObjectManager=obj_mgr&Language=enu&wsdl&op=http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert&op=http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Delete"**</span><span class="sxs-lookup"><span data-stu-id="07d2b-135">**.\svcutil " siebel://Username=YourUserName;Password=YourPassword@Siebel_server:1234?SiebelEnterpriseServer=ent_server&SiebelObjectManager=obj_mgr&Language=enu&wsdl&op=http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert&op=http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Delete"**</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="07d2b-136">您必須將連線 URI 放在引號內，在命令列上。</span><span class="sxs-lookup"><span data-stu-id="07d2b-136">You must place the connection URI in quotation marks on the command line.</span></span> <span data-ttu-id="07d2b-137">否則，svcutil.exe 嘗試擷取作業的中繼資料，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不支援。</span><span class="sxs-lookup"><span data-stu-id="07d2b-137">Otherwise, svcutil.exe attempts to retrieve metadata for operations that the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] does not support.</span></span> <span data-ttu-id="07d2b-138">這類嘗試的結果為未定義。</span><span class="sxs-lookup"><span data-stu-id="07d2b-138">The results of such an attempt are undefined.</span></span>  
  
 <span data-ttu-id="07d2b-139">根據預設，svcutil.exe 會將產生的程式碼 output.cs 檔案;不過，您可以變更輸出檔案的名稱和許多其他選項，svcutil.exe 會使用設定的命令列參數。</span><span class="sxs-lookup"><span data-stu-id="07d2b-139">By default, svcutil.exe places the generated code in the output.cs file; however, you can change the name of the output file and many other options that svcutil.exe uses by setting command-line switches.</span></span>  
  
 <span data-ttu-id="07d2b-140">Svcutil.exe 不提供搜尋作業 （例如，藉由使用萬用字元） 的功能。</span><span class="sxs-lookup"><span data-stu-id="07d2b-140">Svcutil.exe does not provide the capability to search for operations (for example, by using wildcard characters).</span></span> <span data-ttu-id="07d2b-141">您必須明確指定您想要為目標的特定作業的節點識別碼。</span><span class="sxs-lookup"><span data-stu-id="07d2b-141">You must explicitly specify node IDs for the specific operations you want to target.</span></span> <span data-ttu-id="07d2b-142">您無法指定節點只會參考類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="07d2b-142">You cannot specify node IDs that refer only to categories.</span></span> <span data-ttu-id="07d2b-143">如需有關節點識別碼所[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]介面，請參閱[中繼資料節點識別碼](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md)。</span><span class="sxs-lookup"><span data-stu-id="07d2b-143">For more information about the node IDs that the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md).</span></span>  
  
 <span data-ttu-id="07d2b-144">[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]提供進階的瀏覽和搜尋功能，可大幅簡化產生 WCF 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="07d2b-144">The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] provides advanced browse and search capabilities that can greatly simplify generating a WCF client class.</span></span> <span data-ttu-id="07d2b-145">如需詳細資訊[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱 <<c2> [ 產生 WCF 用戶端或 Siebel 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="07d2b-145">For more information about the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], see [Generate a WCF client or a WCF service contract for Siebel solution artifacts](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md).</span></span>  
  
