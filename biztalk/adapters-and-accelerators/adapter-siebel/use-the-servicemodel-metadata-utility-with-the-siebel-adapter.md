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
# <a name="using-the-servicemodel-metadata-utility-tool-with-the-biztalk-adapter-for-siebel-ebusiness-applications"></a>使用 BizTalk 配接器的 ServiceModel Metadata Utility Tool for Siebel eBusiness 應用程式
您可以使用 ServiceModel Metadata Utility Tool (svcutil.exe)，以產生 WCF 用戶端類別的作業，[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]公開 （expose)。 執行 svcutil.exe 以產生 WCF 用戶端類別之後，您可以在程式碼中包含所產生的檔案，並建立 Siebel 系統上執行作業的 WCF 用戶端類別的執行個體。  
  
 使用 svcutil.exe 要求您提供的連接 URI，其中包含的認證。 因為根據預設，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]停用認證的連線 URI，在中，您必須設定要使用的非預設繫結的 svcutil.exe [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 您也可以在非預設繫結中設定其他繫結屬性。  
  
 下列各節說明如何設定 svcutil.exe 以及如何使用 svcutil.exe 產生 WCF 用戶端程式碼與[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
##  <a name="BKMK_ConfigureSvcutil"></a>設定非預設繫結的 svcutil.exe   
 若要設定為使用非預設繫結的 svcutil.exe，您必須建立本機的 svcutil.exe 複本，然後建立或修改 svcutil.exe.config 組態檔的本機副本。  
  
 
1.  建立資料夾，並將 svcutil.exe 複製到新的資料夾。 您通常可以找到 svcutil.exe 在 Windows SDK 安裝位置，特別是，C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin。  
  
2.  建立名為 svcutil.exe.config 的新資料夾中的檔案。  
  
3.  將繫結和用戶端端點新增至 svcutil.exe.config 檔中。 您必須從新的資料夾，以確定正確的組態，用來執行 svcutil.exe。  
  
    > [!IMPORTANT]
    >  用戶端端點的名稱屬性必須指定連線 URI 中使用的配置。 此值區分大小寫。  
  
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
>  您可以設定的任何繫結屬性的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結組態中。  
  
 如需有關如何設定非預設繫結 svcutil.exe 的詳細資訊，請參閱 「 自訂安全中繼資料端點 」 主題中的 WCF 文件[ http://go.microsoft.com/fwlink/?LinkId=96077 ](http://go.microsoft.com/fwlink/?LinkId=96077)。  
  
## <a name="creating-a-wcf-client-class-with-svcutilexe"></a>使用 svcutil.exe 建立 WCF 用戶端類別  
 若要使用 svcutil.exe 產生 WCF 用戶端程式碼[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，您必須提供的連線 URI，指定**IMetadataExchange** (mex) 端點和作業或作業要為其產生的 svcutil.exe程式碼。 您也必須指定連線 URI Siebel 系統的連線認證。  
  
> [!NOTE]
>  您可以使用具有 svcutil.exe 之前[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，您必須將它設定為使用非預設繫結，如需如何這麼做，請參閱[Siebel 配接器設定 svcutil.exe](#BKMK_ConfigureSvcutil)。  
  
 您指定 mex 端點和目標作業在[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]連線 URI，以下列方式：  
  
- 您必須納入 query_string"wsdl 」 參數。 如果是 query_string 的第一個參數，指定只在問號 （？） 之後。 如果不是第一個參數，它應該前面加上連字號 (&)。  
  
- 您必須遵循一或多個"op"參數"wsdl 」 的參數。 每個 「 操作 」 前面加上連字號 (&)，並指定目標作業的節點識別碼。  
  
  下列兩個範例示範如何使用 svcutil.exe 針對各種作業。  
  
  這個範例會建立 WCF 用戶端類別 ACCOUNT\ACCOUNT 商務物件上插入作業。  
  
  **.\svcutil "siebel://Username=YourUserName;Password=YourPassword@Siebel_server:1234?SiebelEnterpriseServer=ent_server&SiebelObjectManager=obj_mgr&Language=enu&wsdl&op=http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert"**  
  
  這個範例會建立 WCF 用戶端類別的插入作業和 ACCOUNT\ACCOUNT 商務物件上的刪除作業。  
  
  **.\svcutil " siebel://Username=YourUserName;Password=YourPassword@Siebel_server:1234?SiebelEnterpriseServer=ent_server&SiebelObjectManager=obj_mgr&Language=enu&wsdl&op=http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert&op=http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Delete"**  
  
> [!IMPORTANT]
>  您必須將連線 URI 放在引號內，在命令列上。 否則，svcutil.exe 嘗試擷取作業的中繼資料，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不支援。 這類嘗試的結果為未定義。  
  
 根據預設，svcutil.exe 會將產生的程式碼 output.cs 檔案;不過，您可以變更輸出檔案的名稱和許多其他選項，svcutil.exe 會使用設定的命令列參數。  
  
 Svcutil.exe 不提供搜尋作業 （例如，藉由使用萬用字元） 的功能。 您必須明確指定您想要為目標的特定作業的節點識別碼。 您無法指定節點只會參考類別的識別碼。 如需有關節點識別碼所[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]介面，請參閱[中繼資料節點識別碼](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md)。  
  
 [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]提供進階的瀏覽和搜尋功能，可大幅簡化產生 WCF 用戶端類別。 如需詳細資訊[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱 <<c2> [ 產生 WCF 用戶端或 Siebel 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)。  
  
