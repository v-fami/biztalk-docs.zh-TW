---
title: "使用 BizTalk adapter 的 ServiceModel Metadata Utility Tool for Siebel eBusiness 應用程式 |Microsoft 文件"
description: "使用 svcutil.exe，非預設繫結，或使用 Siebel 配接器-BizTalk 配接器組件 (BAP) 來建立 WCF 用戶端類別或 WCF 服務合約"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03d16481-cc8b-4e28-a33c-92e48a9a7e8f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c0c2c016387f6b70870e04b211b0bdfe047de11d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-servicemodel-metadata-utility-tool-with-the-biztalk-adapter-for-siebel-ebusiness-applications"></a>使用 BizTalk adapter 的 ServiceModel Metadata Utility Tool for Siebel eBusiness 應用程式
您可以使用 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生作業的 WCF 用戶端類別，[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]公開。 執行 svcutil.exe 產生 WCF 用戶端類別之後，您可以在您的程式碼中包含所產生的檔案，並建立 WCF 用戶端類別，在 Siebel 系統上執行作業的執行個體。  
  
 使用 svcutil.exe 會要求您提供的連接，包含憑證的 URI。 因為根據預設，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]停用認證連線 URI，在中，您必須設定使用非預設繫結的 svcutil.exe [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 您也可以設定非預設繫結中的其他繫結屬性。  
  
 下列各節說明如何設定 svcutil.exe 以及如何使用 svcutil.exe 產生 WCF 用戶端程式碼與[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
##  <a name="BKMK_ConfigureSvcutil"></a>設定非預設繫結的 svcutil.exe   
 若要設定為使用非預設繫結的 svcutil.exe，您必須建立 svcutil.exe 的本機副本，然後建立或修改 svcutil.exe.config 組態檔的本機副本。  
  
 
1.  建立資料夾，並將 svcutil.exe 複製到新的資料夾。 您通常可以找到 svcutil.exe 在 Windows SDK 安裝位置，特別是，C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin。  
  
2.  建立名為 svcutil.exe.config 的新資料夾中的檔案。  
  
3.  加入的其他 svcutil.exe.config 檔與用戶端端點的繫結。 您必須執行 svcutil.exe 從新的資料夾，以確保使用正確的組態。  
  
    > [!IMPORTANT]
    >  用戶端端點的名稱屬性必須指定連線 URI 中使用的配置。 此值區分大小寫。  
  
    ```  
    <configuration>  
      \<system.serviceModel>  
        <client>  
          \<!-- the name should match the required scheme of the Metadata Exchange endpoint   
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
  
      \</system.serviceModel>  
  
    </configuration>  
  
    ```  
  
> [!NOTE]
>  您可以設定的任何繫結屬性的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結組態中。  
  
 如需有關設定非預設繫結 svcutil.exe 的詳細資訊，請參閱 「 自訂安全中繼資料端點 」 中的主題 WCF 文件，網址[http://go.microsoft.com/fwlink/?LinkId=96077](http://go.microsoft.com/fwlink/?LinkId=96077)。  
  
## <a name="creating-a-wcf-client-class-with-svcutilexe"></a>使用 svcutil.exe 建立 WCF 用戶端類別  
 若要使用 svcutil.exe 產生 WCF 用戶端程式碼[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，您必須提供連接 URI，指定**IMetadataExchange** (mex) 端點和作業或作業要為其產生 svcutil.exe程式碼。 您也必須在 連線 URI 中指定 Siebel 系統的連接認證。  
  
> [!NOTE]
>  您可以使用具有 svcutil.exe 之前[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，您必須將它設定為使用非預設繫結，如需如何這麼做，請參閱[Siebel 配接器的設定 svcutil.exe](#BKMK_ConfigureSvcutil)。  
  
 您指定 mex 端點和目標作業中的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]連線 URI 如下：  
  
-   您必須納入 query_string"wsdl 」 參數。 如果是 query_string 的第一個參數，後方問號 （？） 會指定它。 如果不是第一個參數，它應該在前面加上連字號 (&)。  
  
-   您必須遵循一或多個"op"參數"wsdl 」 的參數。 每個"op"參數加上連字號 (&)，並指定目標作業的節點識別碼。  
  
 下列兩個範例示範如何使用 svcutil.exe 以不同的作業為目標。  
  
 這個範例會建立 ACCOUNT\ACCOUNT 商務物件上插入作業的 WCF 用戶端類別。  
  
 **。 \svcutil"siebel://Username=YourUserName;密碼 =YourPassword@Siebel_server:1234嗎？SiebelEnterpriseServer = ent_server & SiebelObjectManager = obj_mgr 與語言 = 繁體中文 wsdl & op = http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert"**  
  
 這個範例會建立一個插入作業和刪除作業 ACCOUNT\ACCOUNT 商務物件上的 WCF 用戶端類別。  
  
 **。 \svcutil"siebel://Username=YourUserName;密碼 =YourPassword@Siebel_server:1234嗎？SiebelEnterpriseServer = ent_server & SiebelObjectManager = obj_mgr 與語言 = 繁體中文 wsdl & op = http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert & op = http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Delete"**  
  
> [!IMPORTANT]
>  您必須在引號內，在命令列上放置連線 URI。 否則，svcutil.exe 會嘗試擷取作業的中繼資料，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不支援。 這類的嘗試結果便未定義。  
  
 根據預設，svcutil.exe 會將產生的程式碼 output.cs 檔案;不過，您可以變更輸出檔的名稱和許多其他選項，svcutil.exe 會使用藉由設定命令列參數。  
  
 Svcutil.exe 不提供的功能來搜尋作業 （例如，透過使用萬用字元）。 您必須明確指定您要當做目標的特定作業的節點識別碼。 您無法指定節點只會參考類別目錄的識別碼。 如需有關節點識別碼，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]介面，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md)。  
  
 [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]提供進階的瀏覽和搜尋功能，可大幅簡化產生 WCF 用戶端類別。 如需有關[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[產生 WCF 用戶端或 WCF 服務合約的 Siebel 方案成品](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)。  
  
