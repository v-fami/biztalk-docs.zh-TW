---
title: "建立 SAP 系統連接 URI |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection URI
- how to, connect using connection URI
- connecting using connection URI
- connecting to SAP, using the connection URI
ms.assetid: e41ed488-07a7-4fb7-97c0-6d626e041e95
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f9c224eb7a219cf3e5bb81f31ef8382c555295b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="create-the-sap-system-connection-uri"></a>建立 SAP 系統連線 URI
[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]連線 URI 包含用來連接到 SAP 系統的配接器屬性。  
  
> [!IMPORTANT]
>  根據預設，SAP 用戶端程式庫 (librfc32u.dll) 最多可支援 100 個連接至 SAP 系統。 如果超過此連線的數目，就會擲回例外狀況。 基於這個理由，您應該設定**MaxConnectionsPerSystem**內容繫結至限制連線數目，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會嘗試開啟 SAP 系統中，或將 CPIC_MAX_CONV 環境變數設定為增加 SAP 用戶端程式庫所支援的連接數目。 如果您變更 CPIC_MAX_CONV，您必須重新啟動電腦，變更才會生效。 如需有關[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結屬性，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
 本主題提供 SAP 連線 URI 的相關資訊，並同時也提供其他主題，說明如何在不同的程式設計案例中指定連線 URI 的連結。  
  
## <a name="connection-uri-for-the-sap-adapter"></a>SAP 配接器的連線 URI  
 一般[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]端點位址 URI 表示，如下所示：  
  
```  
scheme://userinfoparams@hostinfoparams?query_string  
```  
  
 端點位址 URI 包含下列元件：  
  
-   配置是配置名稱。  
  
-   userinfoparams 是由端點所需的使用者驗證參數的名稱 / 值集合。  
  
-   hostinfoparams 是連線到主機; 所需的資訊例如，路徑。  
  
-   query_string 是選擇性的問號 （？） 字元分隔的參數名稱 / 值集合。  
  
 端點位址 URI， [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] SAP 系統的用途使用 SAP 連線 URI 所指定。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]實作此連線 URI，如下所示：  
  
```  
sap://user=[USER_NAME];passwd=[PASSWORD];Client=[CLIENT];lang=[LANGUAGE];[UseSnc]=[True|False]@connectiontype/conndetail1/conndetail2?GwHost=[GWHOST]?GwServ=[GWSERV]?MsServ=[MSSERV]?Group=[GROUP]?ListenerDest=[LISTENERDEST]?ListenerGwHost=[LISTENERGWHOST]?ListenerGwServ=[LISTENERGWSERV]?ListenerProgramId=[LISTENERPROGRAMID]?RfcSdkTrace=[true/false]?AbapDebug=[true/false]  
```  
  
 下列各節中說明的連線 URI 元件。  
  
### <a name="the-sap-connection-uri-scheme"></a>SAP 連線 URI 配置  
 SAP 連線 URI 的配置是 「 sap 」。  
  
### <a name="user-information-in-the-sap-connection-uri"></a>SAP 連線 URI 中的使用者資訊  
 SAP 連線 URI 以使用者驗證、 用戶端識別碼和語言規格所需的參數名稱 / 值集合中的使用者資訊 (userinfoparams)。 下表描述這些參數。  
  
|屬性|Description|  
|--------------|-----------------|  
|使用者|SAP 系統; 上的使用者名稱這個值會區分大小寫。 您必須設定**AcceptCredentialsInUri**內容繫結至**true**連線 URI 中指定的使用者名稱和密碼。 **注意：** [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]保留開啟 SAP 系統上的連線時，您輸入使用者名稱值的大小寫。|  
|Passwd|SAP 系統; 上使用者的密碼這個值會區分大小寫。 您必須設定**AcceptCredentialsInUri**內容繫結至**true**連線 URI 中指定的使用者名稱和密碼。 **注意：** [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]保留開啟 SAP 系統上的連線時，您輸入的密碼值的大小寫。|  
|用戶端|SAP 系統用戶端識別碼。|  
|語言|語言。|  
|UseSnc|選擇性參數，指定是否啟用 SAP 安全網路通訊 (SNC)。 這個值可以是 True 或 False。如果為 True，則會啟用 SNC。 預設值為 False<br /><br /> 當您啟用 SNC 時，您也必須設定**SncPartnerName**和**SncLibrary**繫結屬性。 如需詳細資訊，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。<br /><br /> 如果已啟用 SNC 連線 URI 包含認證，配接器會擲回例外狀況。 **注意：** UseSnc 連接參數是只適用於連線類型 A 和 b。本主題稍後的詳細說明不同的連線類型和其重要性。|  
  
> [!NOTE]
>  您必須 SAP 連線 URI 中指定的用戶端和語言。  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]介面**AcceptCredentialsinUri**繫結屬性，因此您可以控制是否可以在 連線 URI 中指定 SAP 系統的認證。 這是因為憑證以純文字格式的連線 URI，這會造成固有的安全性風險。 根據預設， **AcceptCredentialsInUri**繫結屬性為 false，配接器擲回例外狀況，如果未指定連線 URI 中的認證。  
  
 某些情況下，它是必要的連線 URI，指定認證例如，從 SAP 接收輸入的操作系統時，您可以使用 WCF 服務模型或 WCF 通道模型。 您可以設定**AcceptCredentialsInUri**屬性設定為 true，針對這些案例。 最佳作法是，不過，若要避免提供直接在 連線 URI 中的認證。 如需如何為 SAP 連接更安全的方式提供認證的詳細資訊，請參閱[保護您的 SAP 應用程式](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md)。  
  
> [!IMPORTANT]
>  如果您啟用安全網路通訊 (SNC) 的 UseSnc 參數設為 true 時，配接器會擲回例外狀況。  
  
### <a name="host-information-in-the-sap-connection-uri"></a>SAP 連線 URI 中的主機資訊  
 SAP 主機資訊 (hostinfoparams) 由 SAP 連線 URI 中的下列元素： `connectiontype/conndetail1/conndetail2`。 這些參數會指定用戶端連接至 SAP 系統的詳細資訊。 SAP 用戶端連線，以及 SAP RFC 目的地的接聽程式，請指定 query_string 中建立連接的詳細資料有關的其他詳細資料。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] SAP 連線 URI 中支援下列用戶端連線類型：  
  
-   答： 應用程式主機型連線 URI 中指定透過此應用程式伺服器的連接[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會連接到 SAP。  
  
-   B： 使用負載平衡的連線 URI 中指定的郵件伺服器的連線[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會連接到 SAP。  
  
-   D： 目的地型連線連線 URI 中指定，其中包含適用於 SAP 的連線參數 saprfc.ini 檔案中的目的地。  

    > [!NOTE]
    > 連接類型 B 只適用於傳送埠。  設定接收位置時，選擇 連接類型或 d。
  
 下表描述如何在 SAP 連線 URI 中指定這些連接。  
  
|連接類型|Conndetail1|Conndetail2|Description|  
|---------------------|-----------------|-----------------|-----------------|  
|只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，|ASHOST （應用程式伺服器主控件）|SYSNR （SAP 系統編號）|指定應用程式的主機型連接。 Query_string 中可以指定選擇性的閘道器主機和閘道服務的應用程式主機型連線。|  
|B|MSHOST （郵件伺服器主機）|R3NAME （SAP R3 名稱）|指定負載平衡到郵件伺服器的連線。 Query_string 中可以指定選用的伺服器群組和訊息服務的負載平衡連接。|  
|D|目的地 （包含 saprfc.ini 檔案中的連接參數的目的地）|--|指定目的地型連線。 SAP 連接參數會包含在 saprfc.ini 檔案中指定的目的地。 目的地中，可以指定只有 A 和 B 類型的連線。|  
  
> [!NOTE]
>  如果您指定連接值 saprfc.ini 檔案中，請確定此檔案位於相同的資料夾以存取該檔案的.exe 或所需的 SAP 系統的標準位置。 如需詳細資訊，請參閱 SAP 文件集。  
  
### <a name="query-information-in-the-sap-connection-uri"></a>在 SAP 連線 URI 的查詢資訊  
 查詢中的資訊 (query_string) SAP 連線 URI 包含選擇性參數可以包含指定下列項目：  
  
-   應用程式主機型連接 (A) 的其他連接詳細資料。  
  
-   其他的連線詳細資料會載入平衡連線 (B)。  
  
-   指定透過此 SAP 系統可以傳送 Rfc、 TRFCs 和 Idoc 至 SAP 系統的 RFC 目的地的接聽程式詳細資料[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
-   是否要啟用 SAP 安全網路通訊 (SNC)。  
  
-   指定偵錯組態的詳細資料。  
  
 查詢參數是選擇性的。不過，必須指定接聽程式詳細資料的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]做為 RFC 伺服器。  
  
 下表描述的查詢參數，並指出其皆有效的 SAP 連線類型。  
  
|值|有效的連接類型|Description|  
|-----------|---------------------------|-----------------|  
|GwHost|只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，|應用程式主機型連接中指定選擇性的閘道器主機的名稱。|  
|GwServ|只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，|應用程式主機型連接中指定選擇性的閘道服務的名稱。|  
|MsServ|B|指定在負載平衡連接的選擇性訊息服務的名稱。|  
|群組|B|負載平衡連接中指定選用的應用程式伺服器群組。|  
|ListenerDest|(R)|在 rfc 伺服器連接 saprfc.ini 檔案中指定選擇性的目的地。 目的地必須指定 R 類型連線。|  
|ListenerGwHost|(R)|指定閘道器主機進行 rfc 伺服器連接。 這個參數是選擇性的。不過，如果想要使用的 rfc 伺服器連接和 LISTENERDEST 未指定閘道的主機指定或 saprfc.ini 檔案中的目的地，然後 LISTENERGWHOST 必須包含有效的閘道主機。|  
|ListenerGwServ|(R)|指定的閘道服務進行 rfc 伺服器連接。 這個參數是選擇性的。不過，如果想要使用的 rfc 伺服器連接和 LISTENERDEST 未指定，或沒有閘道服務由 saprfc.ini 檔案中的目的地，然後 LISTENERGWSERV 必須包含有效的閘道服務。|  
|ListenerProgramId|(R)|指定的 rfc 伺服器連接的程式識別碼。 這個參數是選擇性的。不過，如果想要使用的 rfc 伺服器連接和 LISTENERDEST 未指定，或沒有閘道服務由 saprfc.ini 檔案中的目的地，然後 LISTENERPROGRAMID 必須包含有效的閘道服務。|  
|RfcSdkTrace|全部|選擇性參數，指定是否要啟用 RFC 程式庫的追蹤。 這個值可以是 True 或 False。如果為 True，則會啟用 RFC 程式庫追蹤。 預設值是 False。<br /><br /> 啟用 RfcSdkTrace 參數所追蹤的層級取決於 RFC_TRACE 環境變數。<br /><br /> -如果 RFC_TRACE 不存在，或設為 0，會啟用追蹤的最低層級。<br />-您可以設定 RFC_TRACE 為 1 或 2，以增加的追蹤層級。|  
|AbapDebug|全部|選擇性參數，指定是否從偵錯 ABAP[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]已啟用。 這個值可以是 True 或 False。如果為 True，將啟用 ABAP 偵錯。 預設值是 False。 如果 AbapDebug 為 True 時，會開啟 SAP GUI。|  
  
 查詢字串中的參數是 SAP 參數，其值由 SAP 所定義。 如需這些參數的詳細資訊，請參閱您的 SAP 文件。  
  
 下圖顯示範例連線 URI 的應用程式主機型連接：  
  
```  
sap://Client=800;lang=EN@A/YourSAPHOST/00  
```  
  
## <a name="connection-uri-properties-in-the-configure-adapter-dialog-box"></a>連線 URI 屬性中的設定配接器 對話方塊  
 當您連接至 SAP 系統時[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]從 URI 參數設定連接**URI 屬性**索引標籤中**設定配接器** 對話方塊。 下表顯示 URI 屬性會顯示在**URI 屬性**工作表。 （URI 屬性群組中的 URI 屬性工作表中出現的順序列出）。  
  
|類別目錄|URI 屬性|URI 的一部分|  
|--------------|------------------|--------------|  
|應用程式伺服器|應用程式伺服器主機|Conndetail1 （裝載資訊連線 A）|  
|應用程式伺服器|閘道器主機|GwHost （查詢字串）|  
|應用程式伺服器|閘道器服務|GwServ （查詢字串）|  
|應用程式伺服器|系統編號|Conndetail2 （裝載資訊連線 A）|  
|目的地|目的地名稱|Conndetail1 （裝載資訊連線類型 D）|  
|診斷|RFC 追蹤|RfcSdkTrace （查詢字串）|  
|診斷|ABAP 偵錯|AbapDebug （查詢字串）|  
|登入資訊|用戶端|用戶端 (userinfoparams)|  
|登入資訊|語言|語言 (userinfoparams)|  
|訊息伺服器|應用程式伺服器群組名稱|群組 （查詢字串）|  
|訊息伺服器|訊息伺服器主機|Conndetail1 （裝載資訊連線類型 B）|  
|訊息伺服器|訊息伺服器服務|MsServ （查詢字串）|  
|訊息伺服器|/ 3 系統名稱|Conndetail2 （裝載資訊連線類型 B）|  
|其他|連接類型|連接類型 (裝載資訊： A、 B 或 A)|  
|RFC 伺服器|目的地名稱|ListenerDest （查詢字串）|  
|RFC 伺服器|閘道器主機|ListenerGwHost （查詢字串）|  
|RFC 伺服器|閘道器服務|ListenerGwServ （查詢字串）|  
|RFC 伺服器|程式識別碼|ListenerProgramId （查詢字串）|  
|SNC|UseSnc|UseSnc （使用者資訊）|  
  
## <a name="how-to-specify-a-connection-uri-for-rfc-server-connections"></a>如何進行 RFC 伺服器連線指定連線 URI。  
 若要建立透過此端點位址[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可以做為 RFC 伺服器，您必須指定 SAP 程式 id、 SAP 閘道主機，以及對應至 SAP 系統上的 RFC 目的地 SAP 閘道服務。 如需如何設定 SAP RFC 目的地資訊，請參閱[建立 RFC、 RFC 目的地並傳送從 SAP RFC](creating-an-rfc-in-an-sap-system.md)。  
  
 您可以指定連線 URI 中有兩種程式識別碼、 閘道器主機和閘道服務：  
  
-   藉由設定 ListenerGwHost、 ListenerGwServ 和 ListenerProgramId 的查詢參數  
  
-   ListenerDest 查詢參數設為 saprfc.ini 檔案中的目的地，可以指定 R 類型的連接。  
  
> [!NOTE]
>  如果您指定連接值 saprfc.ini 檔案中，請確定檔案是在相同的位置存取該檔案的.exe 或所需的 SAP 系統的標準位置。 如需詳細資訊，請參閱 SAP 文件集。  
  
 若要指定連線 URI 進行 RFC 伺服器連接，您可以指定規則的用戶端連接與查詢字串，如下列範例中指定的 RFC 目的地：  
  
```  
sap://Client=800;lang=EN@A/YourSAPHOST/00?ListenerGwHost=YourSAPHOST&ListenerGwServ=SAPGW00&ListenerProgramId=MyProgramId  
```  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用連線 URI userinfoparams 和 hostinfoparams 部分中所包含的資訊擷取中繼資料從 SAP 系統和登錄它自己做為使用接聽程式參數的查詢字串中所提供的資訊SAP RFC 目的地端的接聽程式。  
  
## <a name="using-reserved-characters-in-the-connection-uri"></a>在 連線 URI 中使用保留的字元  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援指定的連接有任何參數值的特殊字元的 URI。 如果連線參數值包含特殊字元，請確定您執行下列其中一項：  
  
-   如果您要指定中的 URI[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，您必須指定以-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。 如果您指定的 URI 中直接**設定 URI**欄位和連接參數可以包含保留的字元，您必須指定連接參數使用適當的逸出字元。  
  
-   如果您所指定的 URI 時建立傳送或接收埠中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台和連接參數可以包含保留的字元，您必須指定連接參數使用適當的逸出字元。  
  
## <a name="using-the-connection-uri-to-connect-to-the-sap-system"></a>使用連接至 SAP 系統的連線 URI  
 如需如何連接到 SAP 系統時您：  
  
-   使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)。  
  
-   設定傳送埠或接收埠 （位置） 中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案，請參閱[以手動方式設定 SAP 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md)。  
  
-   使用程式設計方案中的 WCF 通道模型，請參閱[建立通道使用 SAP](../../adapters-and-accelerators/adapter-sap/create-a-channel-using-sap.md)。  
  
-   使用 WCF 服務模型程式設計方案中，請參閱[SAP 系統的繫結的用戶端設定](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md)。  
  
-   使用 WCF ServiceModel Metadata Utility Tool (svcutil.exe)，請參閱[mySAP Business Suite 與 BizTalk 配接器使用 ServiceModel Metadata Utility Tool](../../adapters-and-accelerators/adapter-sap/use-the-servicemodel-metadata-utility-with-the-sap-adapter-in-biztalk.md)。  
  
## <a name="see-also"></a>另請參閱  
 [建立 SAP 系統的連線](../../adapters-and-accelerators/adapter-sap/create-a-connection-to-the-sap-system.md)