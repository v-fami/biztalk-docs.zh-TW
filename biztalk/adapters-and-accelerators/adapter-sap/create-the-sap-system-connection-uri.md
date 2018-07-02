---
title: 建立 SAP 系統連線 URI |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connection URI
- how to, connect using connection URI
- connecting using connection URI
- connecting to SAP, using the connection URI
ms.assetid: e41ed488-07a7-4fb7-97c0-6d626e041e95
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1a54dc12b4bca6418cea1ea4ae63c6c63dcba6e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969487"
---
# <a name="create-the-sap-system-connection-uri"></a>建立 SAP 系統連線 URI
[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]連線 URI 包含配接器用來連接到 SAP 系統的屬性。  

> [!IMPORTANT]
>  根據預設，SAP 用戶端程式庫 (librfc32u.dll) 最多可支援 100 個連線到 SAP 系統。 如果您超過此連線的數目，將會擲回例外狀況。 基於這個理由，您應該設定**MaxConnectionsPerSystem**繫結屬性來限制連線數目，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會嘗試開啟 SAP 系統，或將 CPIC_MAX_CONV 環境變數設定為增加 SAP 用戶端程式庫所支援的連線數目。 如果您變更 CPIC_MAX_CONV 時，您必須重新啟動您的電腦，變更才會生效。 如需詳細資訊[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結屬性，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  

 本主題會提供 SAP 連線 URI 的相關資訊，並也會提供說明如何在不同的程式設計案例中，指定連線 URI 的其他主題的連結。  

## <a name="connection-uri-for-the-sap-adapter"></a>SAP 配接器的連線 URI  
 一般[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]端點位址 URI 表示，如下所示：  

```  
scheme://userinfoparams@hostinfoparams?query_string  
```  

 端點位址 URI 包含下列元件：  

- 配置為配置名稱。  

- userinfoparams 是由端點所需進行使用者驗證的參數名稱 / 值集合。  

- hostinfoparams 是連線到主機; 所需的資訊例如，路徑。  

- query_string 是以問號 （？） 分隔的參數的選擇性名稱 / 值集合。  

  端點位址 URI， [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] SAP 系統的使用由使用 SAP 連線的 URI。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]實作此連線 URI，如下所示：  

```  
sap://user=[USER_NAME];passwd=[PASSWORD];Client=[CLIENT];lang=[LANGUAGE];[UseSnc]=[True|False]@connectiontype/conndetail1/conndetail2?GwHost=[GWHOST]?GwServ=[GWSERV]?MsServ=[MSSERV]?Group=[GROUP]?ListenerDest=[LISTENERDEST]?ListenerGwHost=[LISTENERGWHOST]?ListenerGwServ=[LISTENERGWSERV]?ListenerProgramId=[LISTENERPROGRAMID]?RfcSdkTrace=[true/false]?AbapDebug=[true/false]  
```  

 下列各節說明連線 URI 的元件。  

### <a name="the-sap-connection-uri-scheme"></a>SAP 連線的 URI 配置  
 SAP 連線 URI 的配置是 「 sap 」。  

### <a name="user-information-in-the-sap-connection-uri"></a>在 SAP 連接 URI 中的使用者資訊  
 SAP 連線的 URI 以使用者驗證、 用戶端識別碼和語言規格所需的參數名稱 / 值集合中的使用者資訊 (userinfoparams)。 下表描述這些參數。  


| 屬性 |                                                                                                                                                                                                                                                                                                                                                                                                          描述                                                                                                                                                                                                                                                                                                                                                                                                          |
|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   使用者   |                                                                                                                                                                                                            SAP 系統; 上的使用者名稱這個值會區分大小寫。 您必須設定**AcceptCredentialsInUri**屬性來繫結 **，則為 true**連線 URI 中指定的使用者名稱和密碼。 **注意︰** [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]保留開啟 SAP 系統上的連線時，您輸入使用者名稱值的大小寫。                                                                                                                                                                                                             |
|  Passwd  |                                                                                                                                                                                                       SAP 系統; 上使用者的密碼這個值會區分大小寫。 您必須設定**AcceptCredentialsInUri**屬性來繫結 **，則為 true**連線 URI 中指定的使用者名稱和密碼。 **注意︰** [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]保留開啟 SAP 系統上的連線時，您輸入的密碼值的大小寫。                                                                                                                                                                                                       |
|  用戶端  |                                                                                                                                                                                                                                                                                                                                                                                                   SAP 系統用戶端識別碼。                                                                                                                                                                                                                                                                                                                                                                                                   |
| 語言 |                                                                                                                                                                                                                                                                                                                                                                                                           語言。                                                                                                                                                                                                                                                                                                                                                                                                           |
|  UseSnc  | 選擇性參數，指定是否要啟用 SAP 安全網路通訊 (SNC)。 此值可以是 True 或 False。如果為 True，則會啟用 SNC。 預設值為 False<br /><br /> 當您啟用 SNC 時，您也必須設定**SncPartnerName**並**SncLibrary**繫結屬性。 如需詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。<br /><br /> 如果已啟用 SNC 連線 URI 包含認證，配接器會擲回例外狀況。 **注意：** UseSnc 連線參數則僅適用於連線類型 A 和 b。本主題稍後的詳細說明是不同連接類型和其意義。 |

> [!NOTE]
>  在 SAP 連接 URI，您必須指定用戶端和語言。  

 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]表面**AcceptCredentialsinUri**繫結屬性，以便您可以控制是否可以在 連線 URI 中指定 SAP 系統的認證。 這是因為認證以純文字中的連線 URI，以及這對造成固有的安全性風險。 根據預設， **AcceptCredentialsInUri**繫結屬性為 false，而且如果在 連線 URI 中指定認證，則配接器擲回例外狀況。  

 某些情況下，它是必要的連線 URI; 中指定認證比方說，若要從 SAP 接收輸入的操作系統時，您可以使用 WCF 服務的 WCF 通道模型。 您可以設定**AcceptCredentialsInUri**屬性設為 true，針對這些案例。 它是最佳作法，不過，為了避免直接在 連線 URI 中的認證。 如需如何更安全的方式提供認證以取得 SAP 連線的詳細資訊，請參閱[保護您的 SAP 應用程式](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md)。  

> [!IMPORTANT]
>  如果您啟用安全網路通訊 (SNC) UseSnc 參數設定為 true 時，配接器會擲回例外狀況。  

### <a name="host-information-in-the-sap-connection-uri"></a>在 SAP 連線 URI 的主機資訊  
 SAP 主機資訊 (hostinfoparams) 由 SAP 連線 URI 中的下列元素： `connectiontype/conndetail1/conndetail2`。 這些參數會指定用戶端連接到 SAP 系統的詳細資訊。 SAP 用戶端連線相關的其他詳細資料，以及連接到 SAP RFC 目的地的接聽程式的詳細資料，都可以指定在 query_string。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] SAP 連線 URI 中支援下列用戶端連線類型：  

- 答： 應用程式主機型連線 URI 中指定透過此應用程式伺服器的連接[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]連接到 SAP。  

- B： 使用負載平衡的連線 URI 中指定透過它的訊息伺服器的連線[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]連接到 SAP。  

- D： 目的地型連線所在的連線 URI 會指定包含適用於 SAP 的連線參數 saprfc.ini 檔案中的目的地。  

  > [!NOTE]
  > 類型 B 連接僅適用於傳送埠。  設定接收位置時，選擇連線類型 A 或 d。

  下表描述如何在 SAP 連接 URI 中指定這些連接。  

|連接類型|Conndetail1|Conndetail2|描述|  
|---------------------|-----------------|-----------------|-----------------|  
|只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，|ASHOST （應用程式伺服器主控件）|SYSNR （SAP 系統編號）|指定應用程式的主機型連接。 Query_string 中可以指定選擇性的閘道器主機和閘道服務的應用程式主機型連線。|  
|B|MSHOST （郵件伺服器主機）|R3NAME （SAP R3 名稱）|指定負載平衡透過郵件伺服器的連線。 Query_string 中可以指定選用的伺服器群組和訊息服務的負載平衡連線。|  
|D|目的地 （包含 saprfc.ini 檔案中的連線參數的目的）|--|指定的目的地型連線。 SAP 連接參數會包含在 saprfc.ini 檔案中指定的目的地。 目的地中，可以指定只有 A 和 B 類型的連線。|  

> [!NOTE]
>  如果您 saprfc.ini 檔案中指定連接值，請確定該檔案位於相同的資料夾存取檔案的.exe 或所需的 SAP 系統的標準位置中。 如需詳細資訊，請參閱 SAP 文件。  

### <a name="query-information-in-the-sap-connection-uri"></a>在 SAP 連線 URI 的查詢資訊  
 在 SAP 連線 URI 的查詢資訊 (query_string) 包含選擇性的參數可以包含指定下列項目：  

- 應用程式主機型連接 (A) 的其他連接詳細資料。  

- 其他的連線詳細資料的負載平衡連線 (B)。  

- 接聽程式的詳細資料指定於 SAP 系統可以透過此傳送 Rfc、 Trfc 和 Idoc 至 SAP 系統的 RFC 目的地[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  

- 是否要啟用 SAP 安全網路通訊 (SNC)。  

- 指定偵錯組態的詳細資料。  

  查詢參數都是選擇性的;不過，必須指定接聽程式的詳細資料如[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]做為 RFC 伺服器。  

  下表描述的查詢參數，並指出其有效的 SAP 連接類型。  

|       ReplTest1       | 有效的連接類型 |                                                                                                                                                                                                                                    描述                                                                                                                                                                                                                                     |
|-------------------|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      GwHost       |           只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，           |                                                                                                                                                                                              在應用程式主機型連接中指定選擇性的閘道器主機的名稱。                                                                                                                                                                                               |
|      GwServ       |           只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，           |                                                                                                                                                                                             在應用程式主機型連接中指定選擇性的閘道服務的名稱。                                                                                                                                                                                             |
|      MsServ       |           B           |                                                                                                                                                                                                 負載平衡連接中指定選擇性的訊息服務的名稱。                                                                                                                                                                                                  |
|       群組       |           B           |                                                                                                                                                                                                 負載平衡連接中指定選用的應用程式伺服器群組。                                                                                                                                                                                                 |
|   ListenerDest    |          (R)          |                                                                                                                                                                      Saprfc.ini 檔案中的 rfc 伺服器連接中指定選擇性的目的地。 目的地必須指定 R 類型連線。                                                                                                                                                                      |
|  ListenerGwHost   |          (R)          |                                                                                      指定的 rfc 伺服器連線的閘道主機。 這個參數是選擇性的;不過，如果想要使用 rfc 伺服器連線和 LISTENERDEST 未指定，或沒有閘道器主機由 saprfc.ini 檔案中的目的地，然後 LISTENERGWHOST 必須包含有效的閘道主機。                                                                                      |
|  ListenerGwServ   |          (R)          |                                                                                 指定的 rfc 伺服器連線的閘道服務。 這個參數是選擇性的;不過，如果想要使用 rfc 伺服器連線和 LISTENERDEST 未指定，或沒有閘道器服務由 saprfc.ini 檔案中的目的地，然後 LISTENERGWSERV 必須包含有效的閘道服務。                                                                                  |
| ListenerProgramId |          (R)          |                                                                                  指定的 rfc 伺服器連線的程式識別碼。 這個參數是選擇性的;不過，如果想要使用 rfc 伺服器連線和 LISTENERDEST 未指定，或沒有閘道器服務由 saprfc.ini 檔案中的目的地，然後 LISTENERPROGRAMID 必須包含有效的閘道服務。                                                                                   |
|    RfcSdkTrace    |          All          | 指定是否要啟用 RFC 程式庫追蹤的選擇性參數。 此值可以是 True 或 False。如果為 True，則會啟用 RFC 程式庫的追蹤。 預設值是 False。<br /><br /> 啟用 RfcSdkTrace 參數所追蹤的層級取決於 RFC_TRACE 環境變數。<br /><br /> -如果 RFC_TRACE 不存在，或設為 0，則會啟用追蹤的最低層級。<br />-您可以設定 RFC_TRACE 設為 1 或 2，以增加的追蹤層級。 |
|     AbapDebug     |          All          |                                                                                             選擇性參數，指定是否從偵錯 ABAP[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]已啟用。 此值可以是 True 或 False。如果為 True，將啟用 ABAP 偵錯。 預設值是 False。 如果 AbapDebug 為 True，則會開啟 SAP GUI。                                                                                             |

 查詢字串中的參數是 SAP 參數和其值會定義 sap。 如需這些參數的詳細資訊，請參閱您的 SAP 文件。  

 下圖顯示應用程式主機型連接的範例連接 URI:  

```  
sap://Client=800;lang=EN@A/YourSAPHOST/00  
```  

## <a name="connection-uri-properties-in-the-configure-adapter-dialog-box"></a>中的連接 URI 屬性設定配接器 對話方塊  
 當您連接到 SAP 系統[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]從 URI 參數設定的連接**URI 屬性**索引標籤中**設定配接器** 對話方塊。 下表顯示的 URI 屬性中的顯示方式**URI 屬性**工作表。 （URI 屬性群組中的 URI 屬性工作表中出現的順序列出）。  

|類別目錄|URI 屬性|URI 的組件|  
|--------------|------------------|--------------|  
|應用程式伺服器|應用程式伺服器主機|Conndetail1 （主機資訊連接 A）|  
|應用程式伺服器|閘道器主機|GwHost （查詢字串）|  
|應用程式伺服器|閘道器服務|GwServ （查詢字串）|  
|應用程式伺服器|系統編號|Conndetail2 （主機資訊連接 A）|  
|目的地|目的地名稱|Conndetail1 （主機資訊連接類型 D）|  
|診斷|RFC 追蹤|RfcSdkTrace （查詢字串）|  
|診斷|ABAP 偵錯|AbapDebug （查詢字串）|  
|登入資訊|用戶端|用戶端 (userinfoparams)|  
|登入資訊|語言|語言 (userinfoparams)|  
|訊息伺服器|應用程式伺服器群組名稱|群組 （查詢字串）|  
|訊息伺服器|訊息伺服器主機|Conndetail1 （主機資訊連接類型 B）|  
|訊息伺服器|訊息伺服器服務|MsServ （查詢字串）|  
|訊息伺服器|R/3 系統名稱|Conndetail2 （主機資訊連接類型 B）|  
|其他|連接類型|連線類型 (主機資訊： A、 B 或 D)|  
|RFC 伺服器|目的地名稱|ListenerDest （查詢字串）|  
|RFC 伺服器|閘道器主機|ListenerGwHost （查詢字串）|  
|RFC 伺服器|閘道器服務|ListenerGwServ （查詢字串）|  
|RFC 伺服器|程式識別碼|ListenerProgramId （查詢字串）|  
|SNC|UseSnc|UseSnc （使用者資訊）|  

## <a name="how-to-specify-a-connection-uri-for-rfc-server-connections"></a>如何指定連線 URI RFC 伺服器的連接。  
 若要建立的端點位址，透過此[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可以做為 RFC 伺服器，您必須指定 SAP 程式 id、 SAP 閘道主機，以及對應至 SAP 系統的 RFC 目的地的 SAP 閘道服務。 如需有關如何設定 SAP RFC 目的地的資訊，請參閱[建立 RFC、 RFC 目的地並傳送從 SAP RFC](creating-an-rfc-in-an-sap-system.md)。  

 您可以指定連線 URI 中有兩種程式識別碼、 閘道器主機和閘道服務：  

-   藉由設定 ListenerGwHost、 ListenerGwServ 和 ListenerProgramId 的查詢參數  

-   ListenerDest 查詢參數設為 saprfc.ini 檔案中的目的地，可以指定 R 類型的連接。  

> [!NOTE]
>  如果您指定 saprfc.ini 檔案中的連線值，請確定檔案位在相同的位置存取該檔案的.exe 或所需的 SAP 系統的標準位置。 如需詳細資訊，請參閱 SAP 文件。  

 若要指定的 RFC 伺服器連線的連線 URI 中,，您可以指定規則的用戶端連接以指定在查詢字串中，如下列範例所示的 RFC 目的地：  

```  
sap://Client=800;lang=EN@A/YourSAPHOST/00?ListenerGwHost=YourSAPHOST&ListenerGwServ=SAPGW00&ListenerProgramId=MyProgramId  
```  

 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]用以擷取中繼資料從 SAP 系統的連線 URI 的 userinfoparams 和 hostinfoparams 部分中包含的資訊，並使用查詢字串中的接聽程式參數所提供的資訊，來註冊其本身做為在 SAP RFC 目的地的接聽程式。  

## <a name="using-reserved-characters-in-the-connection-uri"></a>在 連線 URI 中使用保留的字元  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援指定的連線有任何參數值的特殊字元的 URI。 如果連線參數值包含特殊字元，請確定您執行下列其中一項：  

- 如果您要指定在 URI[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，您必須指定為-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。 如果您指定直接在 URI**設定 URI**欄位和連接參數包含保留的字元，您必須指定下列連線參數，使用適當的逸出字元。  

- 如果您指定的 URI 時建立傳送或接收埠中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台和連接參數包含保留的字元，您必須指定下列連線參數，使用適當的逸出字元。  

## <a name="using-the-connection-uri-to-connect-to-the-sap-system"></a>使用連線到 SAP 系統的連線 URI  
 如需如何連接到 SAP 系統時您：  

- 使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)。  

- 設定傳送埠或接收埠 （位置） 中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案，請參閱 <<c2> [ 手動設定 SAP 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md)。  

- 程式設計解決方案中使用的 WCF 通道模型，請參閱 <<c0> [ 建立通道，使用 SAP](../../adapters-and-accelerators/adapter-sap/create-a-channel-using-sap.md)。  

- 程式設計解決方案中使用的 WCF 服務模型，請參閱 <<c0> [ 設定用戶端繫結 SAP 系統的](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md)。  

- 使用 WCF ServiceModel Metadata Utility Tool (svcutil.exe)，請參閱[ServiceModel Metadata Utility Tool 與 BizTalk 配接器用於 mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-servicemodel-metadata-utility-with-the-sap-adapter-in-biztalk.md)。  

## <a name="see-also"></a>另請參閱  
 [建立與 SAP 系統的連線](../../adapters-and-accelerators/adapter-sap/create-a-connection-to-the-sap-system.md)