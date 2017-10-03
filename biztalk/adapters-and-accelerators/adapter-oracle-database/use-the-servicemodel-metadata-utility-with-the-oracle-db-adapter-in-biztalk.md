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
# <a name="using-the-servicemodel-metadata-utility-tool-with-the-biztalk-adapter-for-oracle-database"></a>ServiceModel 中繼資料公用程式工具與 BizTalk Adapter 用於 Oracle 資料庫
您可以使用 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別或作業的 WCF 服務合約 （介面），[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]公開。 執行 svcutil.exe 產生 WCF 用戶端類別或 WCF 服務合約之後，在您的程式碼中包含所產生的檔案並建立產生之類別的執行個體或實作在 Oracle 上執行作業的合約的 WCF 服務資料庫。  
  
 使用 svcutil.exe 會要求您提供的連接，包含憑證的 URI。 因為根據預設，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]停用認證連線 URI，在中，您必須設定使用非預設繫結的 svcutil.exe [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
 下列各節說明如何設定 svcutil.exe 以及如何使用 svcutil.exe 產生 WCF 用戶端程式碼或 WCF 服務合約有[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
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
>  您可以設定的任何繫結屬性的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結組態中。  
  
 如需有關設定非預設繫結 svcutil.exe 的詳細資訊，請參閱 「 自訂安全中繼資料端點 」 中的主題 WCF 文件，網址[http://go.microsoft.com/fwlink/?LinkId=96077](http://go.microsoft.com/fwlink/?LinkId=96077)。  
  
### <a name="configure-a-non-default-binding-for-the-pollingstmt-operation"></a>設定非預設繫結 POLLINGSTMT 作業  
 若要使用 svcutil.exe 建立 WCF 服務合約 POLLINGSTMT 作業，您必須設定非預設繫結包含**pollingStatement**屬性，除了**acceptCredentialsInUri**. **PollingStatement**必須包含目標資料表的 SELECT 陳述式。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會使用這個屬性，以產生類別，表示強型別結果設定 POLLINGSTMT 作業傳回。 下列範例會示範用來產生 WCF 服務合約 POLLINGSTMT 作業為目標的繫結組態 /SCOTT/EMP 資料表。  
  
```  
<bindings>  
    <oracleDBBinding>  
        <binding name="OracleDBBinding" acceptCredentialsInUri="true"   
                                   pollingStatement="SELECT * FROM EMP FOR UPDATE" />  
    </oracleDBBinding>  
</bindings>  
```  
  
## <a name="create-a-wcf-client-class-or-wcf-service-contract-with-svcutilexe"></a>使用 svcutil.exe 建立 WCF 用戶端類別或 WCF 服務合約  
 若要使用 svcutil.exe 產生 WCF 用戶端程式碼或 WCF 服務合約 （介面），如[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，您必須提供連線 URI，指定 WS 中繼資料交換 (MEX) 端點和作業或想要的 svcutil.exe 作業產生程式碼。 您也必須指定連線 URI 中的 Oracle 資料庫的連接認證。  
  
> [!NOTE]
>  您可以使用具有 svcutil.exe 之前[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，您必須將它設定為使用非預設繫結，如需如何這麼做，請參閱[設定 Oracle 資料庫配接器的 svcutil.exe](#BKMK_ConfigureSvcutil)。  
  
 您指定 MEX 端點和目標作業中的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]連線 URI 如下：  
  
-   您必須納入 query_string"wsdl 」 參數。 如果是 query_string 的第一個參數，後方問號 （？） 會指定它。 如果不是第一個參數，它應該在前面加上連字號 (&)。  
  
-   您必須遵循一或多個"op"參數"wsdl 」 的參數。 每個"op"參數加上連字號 (&)，並指定目標作業的節點識別碼。  
  
 下列三個範例示範如何使用 svcutil.exe 以不同的作業為目標。  
  
 這個範例會建立 /SCOTT/EMP 資料表上的插入作業的 WCF 用戶端類別。  
  
 **。 \svcutil"oracledb://User=SCOTT;密碼 =TIGER@ADAPTER？ wsdl （& s) op = http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert"**  
  
 此範例會建立 WCF 用戶端類別的插入和刪除作業 /SCOTT/EMP 資料表上。  
  
 **。 \svcutil"oracledb://User=SCOTT;密碼 =TIGER@ADAPTER？ wsdl （& s) op = http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert & op = http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete"**  
  
 這個範例會建立 WCF 服務合約 POLLLINGSTMT 作業。 （若要使用 svcutil.exe 產生 WCF 服務合約 POLLINGSTMT 作業，您必須設定非預設繫結包含輪詢陳述式的 svcutil.exe）。  
  
 **。 \svcutil"oracledb://User=SCOTT;密碼 =TIGER@ADAPTER？ wsdl （& s) op = http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMT"**  
  
> [!IMPORTANT]
>  您必須在引號內，在命令列上放置連線 URI。 否則，svcutil.exe 會嘗試擷取作業的中繼資料，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援。 這類的嘗試結果便未定義。  
  
 根據預設，svcutil.exe 會將產生的程式碼 output.cs 檔案;不過，您可以變更輸出檔的名稱和許多其他選項，svcutil.exe 會使用藉由設定命令列參數。 該 svcutil.exe 支援的選項的詳細資訊，請參閱 < ServiceModel 中繼資料公用程式工具 (Svcutil.exe) > 中的主題 WCF 文件，網址[http://go.microsoft.com/fwlink/?LinkId=72777](http://go.microsoft.com/fwlink/?LinkId=72777)。  
  
 Svcutil.exe 不提供的功能來搜尋作業 （例如，透過使用萬用字元）。 您必須明確指定您要當做目標的特定作業的節點識別碼。 您無法指定節點只會參考類別目錄的識別碼。 如需有關節點識別碼，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]介面，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md)。  
  
 [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]提供進階的瀏覽和搜尋功能，可大幅簡化產生 WCF 用戶端類別和 WCF 服務合約。 如需有關[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[產生的 Oracle 資料庫方案成品 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)