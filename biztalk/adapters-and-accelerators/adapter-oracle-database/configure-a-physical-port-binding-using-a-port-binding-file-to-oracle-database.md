---
title: 設定使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- physical port binding, configuring by using a port binding file
ms.assetid: 154d219e-c6f3-4f70-9ac5-d9345f5260e9
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 716688ab3cbc2431c6058fee17f9dae42ca96ded
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214886"
---
# <a name="configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database"></a>設定使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結
當您使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]產生中繼資料的 Oracle 資料庫成品以外的結構描述檔案，[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]也會產生連接埠繫結檔案。 您可以將此繫結檔案匯 BizTalk 應用程式來建立實體傳送或接收埠。 如需匯入繫結檔案的指示，請參閱[重複使用的 Oracle 資料庫配接器繫結](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md)。 如果您匯入此繫結檔案，您不必手動建立實體傳送或接收埠。  
  
> [!IMPORTANT]
>  同時使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，如果您未指定類型字串的繫結屬性的值，且其預設值為 null 然後繫結屬性將不會使用繫結檔案中。 您必須以手動方式繫結屬性和其值在繫結檔案中，視需要新增。  
  
 建立永遠使用連接埠繫結檔案的連接埠建立雙向傳送或接收埠。 如果您想要建立單向傳送或接收埠，您可以建立它以手動方式中所述的程序[手動設定 Oracle 資料庫配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md)。 或者，您可以依照因應措施若要修改連接埠繫結檔案，若要建立單向傳送或接收埠本主題所述。  
  
 以下是一些您必須了解相對於所產生的繫結檔案的關鍵點[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]:  
  
-   使用特定的命名慣例，會建立檔案。 如果產生的中繼資料輸出的作業，將訊息傳送至 Oracle 資料庫，則檔案的名稱會是 WcfSendPort_OracleDBBinding_Custom.bindinginfo.xml。  
  
     如果產生的中繼資料的輸入作業，從 Oracle 資料庫接收訊息，則檔案的名稱會是 WcfReceivePort_OracleDBBinding_Custom.bindinginfo.xml。  
  
-   檔案包含的繫結組態、 繫結型別、 端點的 URI 和產生的中繼資料的作業為基礎的連接埠動作相關資訊。 當您匯入此繫結檔案，以建立連接埠時，才能設定實體連接埠的相關資訊會自動設定的連接埠上。  
  
    > [!IMPORTANT]
    >  根據預設，傳送埠上的動作會為您產生中繼資料的作業名稱對應。 例如，如果您產生 ACCOUNTACTIVITY 資料表上的選取作業的中繼資料，通訊埠上的動作設定為`<Operation Name="Select" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select" />`。 不過，您在 BizTalk 協調流程中建立邏輯傳送連接埠上的作業名稱可能不能相同。 您必須確定邏輯連接埠 （在 BizTalk 協調流程中） 與實體傳送埠 （在 BizTalk Server 管理主控台） 中的作業名稱都相同。 如果沒有，您會收到錯誤時將訊息傳送至傳送埠透過 Oracle 資料庫。  
  
-   您只需要提供認證來連接到 Oracle 資料庫的連接埠。 繫結檔案並保留用來連接的使用者名稱，同時基於安全性的繫結檔案不包含密碼。  
  
## <a name="key-considerations-for-using-the-port-binding-file"></a>使用連接埠繫結檔案的重要考量  
  
-   當您匯入繫結檔案時，您可能會看到對話方塊通知訊息的繫結檔案中的 BizTalk 應用程式名稱不符合您要匯入繫結檔案的應用程式名稱。 您可以安全地忽略此訊息，並繼續。  
  
-   繫結檔案也包含名稱的連接埠和接收位置。 如果您要匯入繫結檔案的 BizTalk 應用程式建立連接埠或接收位置具有相同名稱做為相同的 BizTalk 應用程式中現有的連接埠，您會收到錯誤。 您必須手動編輯繫結檔案來指定唯一的名稱，連接埠或接收位置。  
  
-   繫結檔案也包含連線 URI 的相關資訊。 如果繫結檔案會建立具有相同的接收 URI 為相同的 BizTalk 應用程式中現有的接收位置的接收位置，您會收到錯誤。 您必須手動編輯繫結檔案來指定唯一的 URI。 您可以指定唯一的 URI 包括輪詢的識別碼。  
  
-   根據預設，連接埠繫結檔案一定會包含定義雙向連接埠 （傳送或接收）。 當您匯入 BizTalk 應用程式中的這個檔案時，它會建立雙向傳送或接收埠。 不過，您可能有協調流程具有單向傳送或接收埠。 因此，當您設定協調流程，並使用 匯入繫結檔案所建立的連接埠，連接埠不在清單中。 這是因為您建立的協調流程一部分的邏輯連接埠是單向連接埠在協調流程中建立的實體通訊埠是雙向的連接埠。 在這種情況下，您可以編輯繫結檔案，進行下列變更：  
  
    |如需|執行方式|  
    |--------------|-------------|  
    |若要編輯連接埠繫結檔案，以設定單向傳送埠|-在下列摘錄中，將值變更**IsTwoWay**屬性設定為 false。 這原本設定為 true。<br /><br /> `<SendPort Name="port_name" IsStatic="true" IsTwoWay="false" BindingOption="0">`<br /><br /> -註解下列區段：<br /><br /> `<ReceivePipeline Name="Microsoft.BizTalk.DefaultPipelines.XMLReceive"    FullyQualifiedName="Microsoft.BizTalk.DefaultPipelines.XMLReceive,    Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral,    PublicKeyToken=token" Type="1" TrackingOption="None" Description=""/>`<br /><br /> `<ReceivePipelineData xsi:nil="true" />`|  
    |若要編輯連接埠繫結檔案，以設定單向接收埠|-在下列摘錄中，將值變更**IsTwoWay**屬性設定為 false。 這原本設定為 true。<br /><br /> `<ReceivePort Name="port_name" IsTwoWay="false" BindingOption="1">`<br /><br /> -註解下列區段：<br /><br /> `<SendPipeline Name="Microsoft.BizTalk.DefaultPipelines.XMLTransmit"    FullyQualifiedName="Microsoft.BizTalk.DefaultPipelines.XMLTransmit,    Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral,    PublicKeyToken=token" Type="2" TrackingOption="None" Description="" />`<br /><br /> `<SendPipelineData xsi:nil="true" />`<br /><br /> `<SendPipelineData xsi:nil="true" />`|  
  
## <a name="configuring-a-wcf-oracledb-port-using-the-port-binding-file-generated-using-consume-adapter-service-add-in"></a>設定使用連接埠繫結檔案使用所產生的 Wcf-oracledb 埠取用配接器服務增益集  
 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] BizTalk Server 管理主控台中建立連接埠繫結檔案，您可以匯入。 您可以使用相同的連接埠繫結檔案，同時在 BizTalk Server 管理主控台建立 BizTalk Wcf-oracledb 連接埠。 不過，在建立 Wcf-oracledb 連接埠之前，您必須執行下列工作來修改連接埠繫結檔案。  
  
1.  在文字編輯器中開啟連接埠繫結檔案。  
  
2.  搜尋並新增 Wcf-oracledb 配接器中的名稱取代 「 WCF 自訂 」[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 例如，如果您新增 Wcf-oracledb 配接器，當做"OracleDBAdapter"，取代 「 WCF 自訂 」 與 「 OracleDBAdapter"。  
  
3.  搜尋"ConfigurationClsid"屬性，並取代現有屬性的值"D7127586-E851-412e-8A8A-2428AEDDC219"。  
  
4.  儲存並關閉繫結檔案。  
  
5.  匯入繫結檔案中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需如何匯入繫結檔案的指示，請參閱[重複使用的 Oracle 資料庫配接器繫結](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md)。  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式與 Oracle 資料庫的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)