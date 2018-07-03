---
title: 使用 ServiceModel Metadata Utility Tool 與 BizTalk 配接器在 BizTalk Server 中的 Oracle 資料庫 |Microsoft Docs
description: 使用 svcutil.exe，非預設繫結，或使用 Oracle DB 配接器-BizTalk 配接器組件 (BAP) 中建立的 WCF 用戶端類別或 WCF 服務合約
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f8660014-da04-4692-89e8-f14fcb419496
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0fe432c9cf7e586269f85beb5f584bbe2aa37210
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999359"
---
# <a name="using-the-servicemodel-metadata-utility-tool-with-the-biztalk-adapter-for-oracle-database"></a>使用 ServiceModel Metadata Utility Tool 與 BizTalk Adapter Oracle 資料庫
您可以使用 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別或作業的 WCF 服務合約 （介面），[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]公開 （expose)。 執行 svcutil.exe 產生 WCF 用戶端類別或 WCF 服務合約之後，您可以納入您的程式碼產生的檔案和建立所產生之類別的執行個體或實作在 Oracle 上執行作業的合約的 WCF 服務資料庫。  
  
 使用 svcutil.exe 要求您提供的連接 URI，其中包含的認證。 因為根據預設，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]停用認證的連線 URI，在中，您必須設定要使用的非預設繫結的 svcutil.exe [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
 下列各節說明如何設定 svcutil.exe 以及如何使用 svcutil.exe 產生 WCF 用戶端程式碼或 WCF 服務合約與[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
##  <a name="BKMK_ConfigureSvcutil"></a> 設定非預設繫結的 svcutil.exe   
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
          <!-- the name should match the required scheme of the WS-Metadata Exchange endpoint   
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
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
> [!NOTE]
>  您可以設定的任何繫結屬性的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結組態中。  
  
 如需有關如何設定非預設繫結 svcutil.exe 的詳細資訊，請參閱 「 自訂安全中繼資料端點 」 主題中的 WCF 文件[ http://go.microsoft.com/fwlink/?LinkId=96077 ](http://go.microsoft.com/fwlink/?LinkId=96077)。  
  
### <a name="configure-a-non-default-binding-for-the-pollingstmt-operation"></a>設定非預設 POLLINGSTMT 作業繫結  
 若要使用 svcutil.exe 建立 WCF 服務合約 POLLINGSTMT 作業，您必須設定要包含的非預設繫結**pollingStatement**屬性，除了**acceptCredentialsInUri**. **PollingStatement**必須包含目標資料表的 SELECT 陳述式。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會使用這個屬性，以產生類別，表示強型別結果設定 POLLINGSTMT 作業傳回。 下列範例顯示用來產生 WCF 服務合約 POLLINGSTMT 作業目標的繫結組態的 /SCOTT/EMP 資料表。  
  
```  
<bindings>  
    <oracleDBBinding>  
        <binding name="OracleDBBinding" acceptCredentialsInUri="true"   
                                   pollingStatement="SELECT * FROM EMP FOR UPDATE" />  
    </oracleDBBinding>  
</bindings>  
```  
  
## <a name="create-a-wcf-client-class-or-wcf-service-contract-with-svcutilexe"></a>使用 svcutil.exe 建立的 WCF 用戶端類別或 WCF 服務合約  
 若要使用 svcutil.exe 來產生 WCF 用戶端程式碼或 WCF 服務合約 （介面），如[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，您必須提供的連線 URI，指定 WS-中繼資料交換 (MEX) 端點的作業或您想要的 svcutil.exe 的作業產生程式碼。 您也必須指定連線 URI 的 Oracle 資料庫的連接認證。  
  
> [!NOTE]
>  您可以使用具有 svcutil.exe 之前[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，您必須將它設定為使用非預設繫結，如需如何這麼做，請參閱[Oracle 資料庫配接器設定 svcutil.exe](#BKMK_ConfigureSvcutil)。  
  
 您指定 MEX 端點和目標作業在[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]連線 URI，以下列方式：  
  
- 您必須納入 query_string"wsdl 」 參數。 如果是 query_string 的第一個參數，指定只在問號 （？） 之後。 如果不是第一個參數，它應該前面加上連字號 (&)。  
  
- 您必須遵循一或多個"op"參數"wsdl 」 的參數。 每個 「 操作 」 前面加上連字號 (&)，並指定目標作業的節點識別碼。  
  
  下列三個範例示範如何使用 svcutil.exe 針對各種作業。  
  
  這個範例會建立插入作業 /SCOTT/EMP 資料表上的 WCF 用戶端類別。  
  
  **。 \svcutil"oracledb://User=SCOTT;密碼 =TIGER@ADAPTER？ wsdl & op =http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert"**  
  
  這個範例會插入和刪除作業 /SCOTT/EMP 資料表上的建立的 WCF 用戶端類別。  
  
  **。 \svcutil"oracledb://User=SCOTT;密碼 =TIGER@ADAPTER？ wsdl & op =http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert&op=http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete"**  
  
  這個範例會建立 WCF 服務合約 POLLLINGSTMT 作業。 （若要使用 svcutil.exe 產生 WCF 服務合約 POLLINGSTMT 作業，您必須設定非預設繫結包含輪詢陳述式的 svcutil.exe）。  
  
  **。 \svcutil"oracledb://User=SCOTT;密碼 =TIGER@ADAPTER？ wsdl & op =http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMT"**  
  
> [!IMPORTANT]
>  您必須將連線 URI 放在引號內，在命令列上。 否則，svcutil.exe 嘗試擷取作業的中繼資料，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援。 這類嘗試的結果為未定義。  
  
 根據預設，svcutil.exe 會將產生的程式碼 output.cs 檔案;不過，您可以變更輸出檔案的名稱和許多其他選項，svcutil.exe 會使用設定的命令列參數。 如需選項的詳細資訊，svcutil.exe 支援，請參閱 「 ServiceModel Metadata Utility 工具 (Svcutil.exe) > 主題中的 WCF 文件，網址[ http://go.microsoft.com/fwlink/?LinkId=72777 ](http://go.microsoft.com/fwlink/?LinkId=72777)。  
  
 Svcutil.exe 不提供搜尋作業 （例如，藉由使用萬用字元） 的功能。 您必須明確指定您想要為目標的特定作業的節點識別碼。 您無法指定節點只會參考類別的識別碼。 如需有關節點識別碼所[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]介面，請參閱[中繼資料節點識別碼](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md)。  
  
 [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]提供進階的瀏覽和搜尋功能，可大幅簡化在產生 WCF 用戶端類別和 WCF 服務合約。 如需詳細資訊[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱 < [Oracle 資料庫解決方案成品產生 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for Oracle Database 的訊息和訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)