---
title: 插入、 更新、 刪除或 interface table 和 Oracle E-business Suite 與介面檢視上選取 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85f42431-80fb-49be-86d1-bb21eee5e4f5
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: adc837fb72c0e18370d28450bf40f162f9849230
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968012"
---
# <a name="insert-update-delete-or-select-on-interface-tables-and-interface-views-with-oracle-e-business-suite"></a>插入、 更新、 刪除或 interface table 和 Oracle E-business Suite 與介面檢視上選取
[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]介面一組標準的作業，例如 Insert、 Update、 Delete 介面上的選取資料表和檢視。 本主題提供有關如何執行這些作業使用配接器的指示。 如需配接器如何支援這些作業的詳細資訊，請參閱[介面資料表和檢視介面上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md)。 這些作業的 SOAP 訊息結構的相關資訊，請參閱[Insert、 Update、 Delete 和選取作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md)。  
  
> [!NOTE]
>  配接器也會公開資料表和包含大型資料類型，例如 BLOB、 CLOB、 NCLOB、 和 BFILE 的檢視表的特定作業。 如需這類作業的詳細資訊，請參閱[介面資料表、 介面檢視、 資料表和檢視表，包含 LOB 資料的作業](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md)。 如需有關如何執行作業的資料表和資料行上使用 BizTalk Server 的大型資料類型的指示，請參閱[完成 Oracle E-business Suite 使用 WCF 服務模型中的大型資料類型的資料表作業](../../adapters-and-accelerators/adapter-oracle-ebs/run-table-operations-with-large-data-types-in-oracle-ebs-using-a-wcf-service.md)。  
  
## <a name="how-to-perform-basic-operations-on-oracle-e-business-suite"></a>如何執行 Oracle E-business Suite 的基本作業  
 執行 Oracle E-business suite 作業使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[建立 Oracle E-business Suite 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)。 若要執行 Oracle E-business Suite 中的 Insert、 Update、 Delete 或 Select 作業在資料表和檢視表上的，這些工作包括：  
  
1.  建立 BizTalk 專案，並產生您想要叫用的介面資料表或檢視表上作業的結構描述。  
  
2.  建立傳送和接收訊息，從 Oracle E-business Suite 的 BizTalk 專案中的訊息。  
  
3.  建立協調流程叫用的介面資料表或檢視上的作業。  
  
4.  建置和部署 BizTalk 專案。  
  
5.  設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
6.  啟動 BizTalk 應用程式。  
  
 本主題提供執行這些工作的指示。  
  
## <a name="generating-schema"></a>產生結構描述  
 本主題示範如何藉由將記錄插入 Oracle E-business Suite 中 AR_ARCHIVE_PURGE_INTERIM 介面資料表中執行基本 Insert、 Update、 Delete 或 Select 作業。 此介面資料表位於**應收帳款**Oracle E-business Suite 中的應用程式。  
  
 若要示範如何插入記錄，AR_ARCHIVE_PURGE_INTERIM 資料表的插入作業產生結構描述。 您必須建立 BizTalk 專案，並使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生結構描述。 請參閱[擷取 Oracle E-business Suite 作業在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)如需有關如何產生結構描述。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。 訊息通常是針對的類型定義所對應的結構描述的變數。 您現在必須建立協調流程的訊息，並將它們連結至您在上一個步驟中產生的結構描述。  
  
#### <a name="to-create-messages-and-link-to-schema"></a>建立訊息，以及連結至結構描述  
  
1.  BizTalk 專案中新增協調流程。 從 方案總管 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下 **新項目**。 輸入 BizTalk 協調流程的名稱，然後按一下**新增**。  
  
2.  如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。 若要這樣做，請按一下**檢視**，指向 **其他視窗**，然後按一下 **協調流程檢視**。  
  
3.  在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。  
  
4.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  
  
5.  在**屬性**窗格**Message_1**，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|輸入 `Request`|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*InsertInterfaceTable.OracleEBSBinding.Insert*InsertInterfaceTable 所在的 BizTalk 專案的名稱。 OracleEBSBinding 是 AR_ARCHIVE_PURGE_INTERIM 資料表的插入作業所產生的結構描述。|  
  
6.  重複步驟 2 來建立新的訊息。 在**屬性**窗格新訊息中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|輸入 `Response`|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*InsertInterfaceTable.OracleEBSBinding.InsertResponse*。|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]for Oracle E-business Suite 上執行操作。 在此協調流程中，卸除要求訊息已定義的接收位置。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會取用這個訊息，並將它傳遞到 Oracle E-business Suite。 Oracle E-business Suite 的回應會儲存到另一個位置。 典型的協調流程執行的 Oracle 資料庫上的基本資料表作業就會包含：  
  
-   傳送和接收圖形以將訊息傳送至 Oracle 資料庫，並接收回應。  
  
-   單向接收埠以接收要求訊息傳送到 Oracle 資料庫。  
  
-   雙向傳送埠以傳送要求訊息到 Oracle 資料庫，並接收回應。  
  
-   單向傳送埠，以便從 Oracle 資料庫的回應傳送到資料夾。  
  
 選取作業的範例協調流程如下所示：  
  
 ![若要將資料插入介面資料表的協調流程](../../adapters-and-accelerators/adapter-oracle-ebs/media/8a4508c5-9949-4043-9de5-d1226db8117b.gif "8a4508c5-9949-4043-9de5-d1226db8117b")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息圖形指定下列屬性。 圖形資料行中所列的名稱是訊息 圖形的名稱，為顯示在剛才提及的協調流程中。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveMessage|Receive|-設定**名稱**至*ReceiveMessage*<br />-設定**啟動**至 *，則為 True*|  
|SendMessage|Send|-設定**名稱**至*SendMessage*|  
|ReceiveResponse|Receive|-設定**名稱**至*ReceiveResponse*<br />-設定**啟動**至*False*|  
|SendResponse|Send|-設定**名稱**至*SendResponse*|  
  
### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠指定下列屬性。 連接埠資料行中所列的名稱是連接埠的名稱，為顯示協調流程中。  
  
|通訊埠|屬性|  
|----------|----------------|  
|MessageIn|-設定**識別碼**至*MessageIn*<br />-設定**類型**至*MessageInType*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*接收*|  
|LOBPort|-設定**識別碼**至*LOBPort*<br />-設定**類型**至*LOBPortType*<br />-設定**通訊模式**至*要求-回應*<br />-設定**通訊方向**至*傳送接收*|  
|ResponseOut|-設定**識別碼**至*ResponseOut*<br />-設定**類型**至*ResponseOutType*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*傳送*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a>指定訊息的動作圖形，並將它們連接至連接埠  
 下表指定屬性和其值，您應該設定來指定動作圖形的訊息，以及連結至連接埠的訊息。 圖形資料行中所列的名稱是 「 訊息 」 圖形的名稱，為顯示在協調流程中先前所述。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveMessage|-設定**訊息**至*要求*<br />-設定**作業**至*MessageIn.Insert.Request*|  
|SendMessage|-設定**訊息**至*要求*<br />-設定**作業**至*LOBPort.Insert.Request*|  
|ReceiveResponse|-設定**訊息**至*回應*<br />-設定**作業**至*LOBPort.Insert.Response*|  
|SendResponse|-設定**訊息**至*回應*<br />-設定**作業**至*ResponseOut.Insert.Request*|  
  
 您指定這些屬性之後，連線的訊息 圖形和連接埠，和您的協調流程已完成。  
  
 現在，您必須建置 BizTalk 方案，並將它部署到 BizTalk Server。 如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。  
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 在 [協調流程] 窗格中您已部署的 BizTalk 專案後，會列出您稍早建立的協調流程[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。 如需逐步解說，請參閱[逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。  
  
 設定應用程式包括：  
  
-   選取應用程式的主機。  
  
-   對應至實體連接埠在協調流程中建立的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 此協調流程中，您必須：  
  
    -   定義位置上的硬碟和對應的檔案連接埠，您將在此置放要求訊息。 BizTalk 協調流程會使用要求訊息，並將它傳送給 Oracle E-business Suite。  
  
    -   定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含從 Oracle E-business Suite 回應的回應訊息。  
  
    -   定義將訊息傳送至 Oracle E-business Suite 實體 Wcf-custom 或 Wcf-oracleebs 傳送埠。 您也必須在傳送埠中指定的動作。 如需如何建立連接埠相關資訊，請參閱[手動設定的實體連接埠的繫結至 Oracle E-business 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)  
  
         若要執行作業的介面資料表或介面上，檢視使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您必須設定正確的應用程式內容，叫用作業。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]提供特定的繫結屬性，以指定應用程式內容的任何作業。 您必須使用介面資料表上執行作業的 Wcf-custom 或 Wcf-oracleebs 連接埠上設定這些繫結屬性。  
  
        -   如果**ClientCredentialType**繫結屬性設定為**資料庫**，接著，您必須指定下列繫結屬性來設定應用程式內容。  
  
            |繫結屬性|值|  
            |----------------------|-----------|  
            |**OracleUserName**|指定 Oracle E-business Suite 使用者的名稱。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不會保留您輸入的值的大小寫**OracleUserName**連接到 Oracle E-business Suite 時，繫結屬性。 使用者名稱傳遞至 Oracle E-business Suite 使用標準的規則的 SQL * Plus。 不過，如果您想要保留的使用者名稱的大小寫，或您想要輸入含有特殊字元的使用者名稱，您必須指定雙引號括住的值。|  
            |**OraclePassword**|Oracle E-business Suite 使用者的密碼。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不會保留您輸入的值的大小寫**OraclePassword**連接到 Oracle E-business Suite 時，繫結屬性。 密碼會傳遞至 Oracle E-business Suite 使用標準的規則的 SQL * Plus。 不過，如果您想要保留的密碼的大小寫，或您想要輸入包含特殊字元的密碼，您必須指定雙引號括住的值。|  
            |**OracleEBSResponsibilityName**|Oracle E-business Suite 使用者相關聯的責任。|  
  
        -   如果**ClientCredentialType**繫結屬性設定為**EBusiness**，您必須已指定 Oracle E-business 認證建立連線時。 在這種情況下您必須只指定值**OracleEBSResponsibilityName**繫結屬性。  
  
         如需不同的繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。 如需有關配接器支援設定的應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
        > [!NOTE]
        >  指定的繫結屬性，或設定訊息內容屬性所公開，您可以設定應用程式內容[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 如需有關如何設定繫結屬性的指示，請參閱[for Oracle E-business Suite 中設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md)。 如需有關如何設定應用程式內容使用訊息內容屬性的指示，請參閱[Oracle E-business Suite 中設定應用程式內容使用訊息內容屬性](../../adapters-and-accelerators/adapter-oracle-ebs/configure-application-context-using-message-context-properties-in-oracle-ebs.md)。  
  
        > [!NOTE]
        >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠的設定動作的相關資訊的繫結檔案。 您可以從這個繫結檔案匯[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 （適用於傳出呼叫） 的傳送埠或接收埠 （用於進行傳入呼叫時）。 如需詳細資訊，請參閱[設定實體連接埠繫結使用連接埠繫結檔案至 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md)。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 AR_ARCHIVE_PURGE_INTERIM 介面資料表中插入記錄的 BizTalk 應用程式。 如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。  
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   Wcf-custom 或 Wcf-oracleebs 傳送埠以傳送訊息至 Oracle E-business Suite 正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須先卸除要求訊息到檔案接收位置。 要求訊息的結構描述必須符合您先前產生插入作業的結構描述。 例如，要從 AR_ARCHIVE_PURGE_INTERIM 介面資料表中選取所有記錄的要求訊息是：  
  
```  
<Insert xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/AR/AR/AR_ARCHIVE_PURGE_INTERIM">  
  <RECORDSET>  
    <InsertRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableViewRecord/AR/AR_ARCHIVE_PURGE_INTERIM">  
      <TRX_ID>001</TRX_ID>  
      <RELATED_ID>002</RELATED_ID>  
    </InsertRecord>  
  </RECORDSET>    
</Insert>  
```  
  
 此要求訊息會插入 AR_ARCHIVE_PURGE_INTERIM 介面資料表的記錄。 請參閱[Insert、 Update、 Delete 和選取作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md)如需有關執行 Oracle E-business Suite 所使用的基本 DML 作業的要求訊息結構描述[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  
  
 簡單資料的資料行，例如在先前的要求訊息中，您也可以使用**InlineValue**屬性。 如需 InlineValue 屬性的詳細資訊，請參閱中的插入作業描述[介面資料表和檢視介面上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md)。  
  
 例如，先前的要求訊息具有內嵌值將會如下所示：  
  
```  
<Insert xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/AR/AR/AR_ARCHIVE_PURGE_INTERIM">  
  <RECORDSET>  
    <InsertRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableViewRecord/AR/AR_ARCHIVE_PURGE_INTERIM">  
      <TRX_ID InlineValue="(Select TRX_ID FROM table_name)">001</TRX_ID>  
      <RELATED_ID>002</RELATED_ID>  
    </InsertRecord>  
  </RECORDSET>    
</Insert>  
```  
  
 在此要求訊息中，從另一個資料表，擷取 TRX_ID 資料行的值。 因此，即使 TRX_ID"001"指定為值，則 InlineValue 屬性指定的 SELECT 陳述式的值會插入到資料表。  
  
 協調流程取用訊息，並將它傳送給 Oracle E-business Suite。 Oracle E-business Suite 的回應會儲存在其他的協調流程中定義的檔案位置。 例如，先前的要求訊息從 Oracle E-business Suite 的回應是：  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<InsertResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/AR/AR/AR_ARCHIVE_PURGE_INTERIM">  
  <InsertResult>1</InsertResult>   
</InsertResponse>  
```  
  
 回應包含插入至資料表的資料列數目。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。 產生繫結檔案之後，您可以匯入的組態設定從檔案，因此您不需要建立項目，例如傳送埠和接收相同的協調流程連接埠。 如需繫結檔案的詳細資訊，請參閱[重複使用配接器繫結與 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md)。  
  
## <a name="see-also"></a>請參閱  
[開發 BizTalk 應用程式使用 Oracle E-business Suite 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)