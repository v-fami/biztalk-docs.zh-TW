---
title: 使用 ServiceModel Metadata Utility Tool 與 BizTalk Adapter mySAP Business Suite |Microsoft Docs
description: 使用 svcutil.exe，非預設繫結，或使用 SAP 配接器-BizTalk 配接器組件 (BAP) 中建立的 WCF 用戶端類別或 WCF 服務合約
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ServiceModel Metadata Utility Tool, creating a WCF Client Class or a WCF service contract with the tool
- ServiceModel Metadata Utility Tool, configuring the tool for the adapter
ms.assetid: 7ac08012-bb12-4983-9402-be84fe3997d8
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a8bdbf2a3b3a3c359a4c3e4912e2b6e18928023
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003175"
---
# <a name="using-the-servicemodel-metadata-utility-tool-with-the-biztalk-adapter-for-mysap-business-suite"></a>使用 ServiceModel Metadata Utility Tool 與 BizTalk Adapter mySAP Business Suite
您可以使用 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別或作業的 WCF 服務合約 （介面），[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]公開 （expose)。 執行 svcutil.exe 產生 WCF 用戶端類別或 WCF 服務合約之後，您可以納入您的程式碼產生的檔案和建立所產生之類別的執行個體或實作的 WCF 服務，從產生的介面上的 SAP 執行作業系統。  
  
 使用 svcutil.exe 要求您提供的連接 URI，其中包含的認證。 因為根據預設，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]停用認證的連線 URI，在中，您必須設定要使用的非預設繫結的 svcutil.exe [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 您也可以設定其他繫結屬性中的非預設繫結;例如，若要建立 BAPI 作業的 WCF 用戶端，您必須設定**EnableSafeTyping**屬性來繫結 **，則為 true**。  
  
 下列各節說明如何設定 svcutil.exe 以及如何使用 svcutil.exe 產生 WCF 用戶端程式碼或 WCF 服務合約與[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
##  <a name="BKMK_ConfigureSvcutil"></a> SAP 配接器的設定 svcutil.exe  
 若要設定為使用非預設繫結的 svcutil.exe，您必須建立本機的 svcutil.exe 複本，然後建立或修改 svcutil.exe.config 組態檔的本機副本。  
  
1. 建立資料夾，並將 svcutil.exe 複製到新的資料夾。 您通常可以找到 svcutil.exe 在 Windows SDK 安裝位置，特別是，C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin。  
  
2. 建立名為 svcutil.exe.config 的新資料夾中的檔案。  
  
3. 將繫結和用戶端端點新增至 svcutil.exe.config 檔中。 您必須從新的資料夾，以確定正確的組態，用來執行 svcutil.exe。  
  
   > [!IMPORTANT]
   >  用戶端端點的名稱屬性必須指定連線 URI 中使用的配置。 此值區分大小寫。  
  
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
  
   您可以設定的任何繫結屬性的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結組態中。 比方說，您可以指定要使用 svcutil.exe 產生 WCF 用戶端 BAPI 作業的下列非預設繫結。  
  
```  
<bindings>  
  <sapBinding>  
    <binding name="SAPBinding" acceptCredentialsInUri="true"/>  
  </sapBinding>  
</bindings>  
```  
  
 如需有關如何設定非預設繫結 svcutil.exe 的詳細資訊，請參閱 <<c0> [ 自訂安全中繼資料端點](https://msdn.microsoft.com/library/aa395212.aspx)。
  
## <a name="creating-a-wcf-client-class-or-a-wcf-service-contract-with-svcutilexe"></a>使用 svcutil.exe 建立的 WCF 用戶端類別或 WCF 服務合約  
 若要使用 svcutil.exe 來產生 WCF 用戶端程式碼或 WCF 服務合約 （介面），如[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，您必須提供的連線 URI，指定的 WS-中繼資料交換 (MEX) 端點的作業或想要的 svcutil.exe 作業產生程式碼。 您也必須指定連線 URI 中的 SAP 系統的連線認證。  
  
> [!NOTE]
>  您可以使用具有 svcutil.exe 之前[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，您必須將它設定為使用非預設繫結，如需如何這麼做，請參閱[SAP 配接器的設定 svcutil.exe](#BKMK_ConfigureSvcutil)。  
  
 您指定 MEX 端點和目標作業在[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]連線 URI，以下列方式：  
  
- 您必須在查詢字串中包含"wsdl 」 參數。 如果是查詢字串中的第一個參數，則會將它指定後方問號 （？）。 如果不是第一個參數，它應該前面加上連字號 (&)。  
  
- 您必須遵循一或多個"op"參數"wsdl 」 的參數。 每個 「 操作 」 前面加上連字號 (&)，並指定目標作業的節點識別碼。  
  
  下列三個範例示範如何使用 svcutil.exe 針對各種作業。  
  
  這個範例會建立 RFC_CALCULATE_TAXES WCF 用戶端類別。  
  
  **.\svcutil "sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?wsdl&op=http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CALCULATE_TAXES"**  
  
  此範例會建立 WCF 用戶端類別 SALESORDER_CREATEFROMDAT201 和 SALESORDER_CREATEFROMDAT202 IDOC。  
  
  **.\svcutil "sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?wsdl&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT201//620/Send&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT202//620/Send"**  
  
  這個範例會建立 WCF 服務合約，以便從 SAP 系統接收 SALESORDER_CREATEFROMDAT201 IDOC。 節點識別碼會指定接收作業。 此範例中處理擷取中繼資料，因為沒有需要在 連線 URI query_string 指定接聽程式參數。  
  
  **.\svcutil "sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?wsdl&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT201//620/Receive"**  
  
> [!IMPORTANT]
>  您必須將連線 URI 放在引號內，在命令列上。 否則，svcutil.exe 嘗試擷取作業的中繼資料，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援。 這類嘗試的結果為未定義。  
  
 根據預設，svcutil.exe 會將產生的程式碼 output.cs 檔案;不過，您可以變更輸出檔案的名稱和許多其他選項，svcutil.exe 會使用設定的命令列參數。 如需選項的詳細資訊，svcutil.exe 支援，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx)。
  
 Svcutil.exe 不提供搜尋作業 （例如，藉由使用萬用字元） 的功能。 您必須明確指定您想要為目標的特定作業的節點識別碼。 作業的節點識別碼等於其訊息動作字串。 您無法指定節點只會參考類別的識別碼。 如需有關節點識別碼所[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]介面，請參閱[中繼資料節點識別碼](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md)。  
  
 [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]提供進階的瀏覽和搜尋功能，可大幅簡化在產生 WCF 用戶端類別和 WCF 服務合約。 如需詳細資訊[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱 <<c2> [ 產生 WCF 用戶端或 SAP 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。  
  
