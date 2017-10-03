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
ms.openlocfilehash: ac86d1aa254de81c2778ce1a2c1f0e63c1c1e1ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-servicemodel-metadata-utility-tool-with-the-biztalk-adapter-for-mysap-business-suite"></a>使用 BizTalk adapter 的 ServiceModel Metadata Utility Tool for mySAP Business Suite
您可以使用 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別或作業的 WCF 服務合約 （介面），[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]公開。 執行 svcutil.exe 產生 WCF 用戶端類別或 WCF 服務合約之後，您可以在您的程式碼中包含所產生的檔案和建立所產生類別的執行個體或從實作 WCF 服務產生的介面上的 SAP 執行作業系統。  
  
 使用 svcutil.exe 會要求您提供的連接，包含憑證的 URI。 因為根據預設，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]停用認證連線 URI，在中，您必須設定使用非預設繫結的 svcutil.exe [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 您也可以設定其他繫結屬性中的非預設繫結。例如，若要建立 BAPI 作業的 WCF 用戶端，您必須設定**EnableSafeTyping**內容繫結至**true**。  
  
 下列各節說明如何設定 svcutil.exe 以及如何使用 svcutil.exe 產生 WCF 用戶端程式碼或 WCF 服務合約有[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
##  <a name="BKMK_ConfigureSvcutil"></a>設定 SAP 配接器的 svcutil.exe  
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
          \<!-- the name should match the required scheme of the WS-Metadata Exchange endpoint   
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
  
      \</system.serviceModel>  
  
    </configuration>  
    ```  
  
 您可以設定的任何繫結屬性的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結組態中。 例如，您可以指定要使用 svcutil.exe 產生 WCF 用戶端 BAPI 作業的下列非預設繫結。  
  
```  
<bindings>  
  <sapBinding>  
    <binding name="SAPBinding" acceptCredentialsInUri="true"/>  
  </sapBinding>  
</bindings>  
```  
  
 如需有關設定非預設繫結 svcutil.exe 的詳細資訊，請參閱[自訂安全中繼資料端點](https://msdn.microsoft.com/library/aa395212.aspx)。
  
## <a name="creating-a-wcf-client-class-or-a-wcf-service-contract-with-svcutilexe"></a>使用 svcutil.exe 建立 WCF 用戶端類別或 WCF 服務合約  
 若要使用 svcutil.exe 產生 WCF 用戶端程式碼或 WCF 服務合約 （介面），如[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，您必須提供連線 URI，指定 WS 中繼資料交換 (MEX) 端點和作業或想要的 svcutil.exe 作業產生程式碼。 您也必須指定連線 URI 中的 SAP 系統的連接認證。  
  
> [!NOTE]
>  您可以使用具有 svcutil.exe 之前[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，您必須將它設定為使用非預設繫結，如需如何這麼做，請參閱[SAP 配接器的設定 svcutil.exe](#BKMK_ConfigureSvcutil)。  
  
 您指定 MEX 端點和目標作業中的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]連線 URI 如下：  
  
-   您必須在查詢字串中包含"wsdl 」 參數。 如果查詢字串中的第一個參數，它會指定後方問號 （？）。 如果不是第一個參數，它應該在前面加上連字號 (&)。  
  
-   您必須遵循一或多個"op"參數"wsdl 」 的參數。 每個"op"參數加上連字號 (&)，並指定目標作業的節點識別碼。  
  
 下列三個範例示範如何使用 svcutil.exe 以不同的作業為目標。  
  
 這個範例會針對 RFC_CALCULATE_TAXES 建立 WCF 用戶端類別。  
  
 **。 \svcutil"sap://User=YourUserName;Passwd = YourPassword;用戶端 = 800;Lang = EN;@a/YourSAPHost/00？ wsdl （& s) op = http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CALCULATE_TAXES"**  
  
 此範例會建立 WCF 用戶端類別 SALESORDER_CREATEFROMDAT201 和 SALESORDER_CREATEFROMDAT202 IDOC。  
  
 **。 \svcutil"sap://User=YourUserName;Passwd = YourPassword;用戶端 = 800;Lang = EN;@a/YourSAPHost/00？ wsdl （& s) op = http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT201//620/Send & op = http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT202//620/Send"**  
  
 這個範例會建立從 SAP 系統接收 SALESORDER_CREATEFROMDAT201 IDOC 的 WCF 服務合約。 節點識別碼會指定接收作業。 此範例中處理的擷取中繼資料，因為沒有需要連線 URI query_string 中指定的接聽程式參數。  
  
 **。 \svcutil"sap://User=YourUserName;Passwd = YourPassword;用戶端 = 800;Lang = EN;@a/YourSAPHost/00？ wsdl （& s) op = http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT201//620/Receive"**  
  
> [!IMPORTANT]
>  您必須在引號內，在命令列上放置連線 URI。 否則，svcutil.exe 會嘗試擷取作業的中繼資料，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援。 這類的嘗試結果便未定義。  
  
 根據預設，svcutil.exe 會將產生的程式碼 output.cs 檔案;不過，您可以變更輸出檔的名稱和許多其他選項，svcutil.exe 會使用藉由設定命令列參數。 該 svcutil.exe 支援的選項的詳細資訊，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx)。
  
 Svcutil.exe 不提供的功能來搜尋作業 （例如，透過使用萬用字元）。 您必須明確指定您要當做目標的特定作業的節點識別碼。 作業的節點識別碼就相當於其訊息的動作字串。 您無法指定節點只會參考類別目錄的識別碼。 如需有關節點識別碼，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]介面，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md)。  
  
 [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]提供進階的瀏覽和搜尋功能，可大幅簡化產生 WCF 用戶端類別和 WCF 服務合約。 如需有關[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SAP 方案成品](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。  
  
