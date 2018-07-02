---
title: 插入、 更新、 刪除或選取在介面資料表和介面檢視使用 Oracle E-business Suite |Microsoft Docs
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
ms.openlocfilehash: f9baefe803a7ab239a978c934a62dc5d0218ca4d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982991"
---
# <a name="insert-update-delete-or-select-on-interface-tables-and-interface-views-with-oracle-e-business-suite"></a>插入、 更新、 刪除或選取在介面資料表和介面檢視使用 Oracle E-business Suite
[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]一組標準的作業，例如插入的介面，介面上的 Update、 Delete，選取資料表和檢視。 本主題提供有關如何使用配接器執行這些作業的指示。 如需配接器如何支援這些作業的詳細資訊，請參閱[介面資料表和介面檢視上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md)。 這些作業的 SOAP 訊息結構的相關資訊，請參閱[插入、 更新、 刪除和選取作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md)。  

> [!NOTE]
>  配接器也會公開資料表和檢視表包含大型的資料類型，例如 BLOB、 CLOB、 NCLOB、 和 BFILE 的特定作業。 如需有關這類作業的詳細資訊，請參閱[Interface Table、 介面檢視、 資料表和檢視表，包含 LOB 資料的作業](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md)。 如需有關如何執行與使用 BizTalk Server 的大型資料類型的資料表和資料行上作業的指示，請參閱[完成 Oracle E-business Suite 使用 WCF 服務模型中的大型資料類型的資料表作業](../../adapters-and-accelerators/adapter-oracle-ebs/run-table-operations-with-large-data-types-in-oracle-ebs-using-a-wcf-service.md)。  

## <a name="how-to-perform-basic-operations-on-oracle-e-business-suite"></a>如何執行 Oracle E-business Suite 的基本作業  
 使用執行 Oracle E-business Suite 作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及中所述的程序性工作[建立 Oracle E-business Suite 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)。 若要執行 Oracle E-business Suite 中的 Insert、 Update、 Delete 或資料表和檢視表的 Select 作業，這些工作如下：  

1. 建立 BizTalk 專案，並產生您想要在介面資料表或檢視表上叫用作業的結構描述。  

2. 建立傳送和接收訊息，從 Oracle E-business Suite 的 BizTalk 專案中的訊息。  

3. 建立協調流程叫用在介面資料表或檢視表上的作業。  

4. 建置和部署 BizTalk 專案。  

5. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  

6. 啟動 BizTalk 應用程式。  

   本主題提供執行這些工作的指示。  

## <a name="generating-schema"></a>產生結構描述  
 本主題示範如何執行基本的 Insert、 Update、 Delete 或 Select 作業，在 Oracle E-business Suite 中的 AR_ARCHIVE_PURGE_INTERIM 介面資料表中插入記錄。 此介面資料表位於**應收帳款**Oracle E-business Suite 中的應用程式。  

 為了示範如何插入記錄，AR_ARCHIVE_PURGE_INTERIM 資料表的插入作業產生結構描述。 您必須建立 BizTalk 專案，並使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生結構描述。 請參閱[擷取 Oracle E-business Suite 作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)如需有關如何產生結構描述。  

## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是的變數，其對應的結構描述所定義的型別。 現在，您必須建立協調流程的訊息，並將它們連結至您在上一個步驟中產生的結構描述。  

#### <a name="to-create-messages-and-link-to-schema"></a>若要建立訊息，並連結至結構描述  

1.  BizTalk 專案中新增協調流程。 從 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下**新項目**。 輸入 BizTalk 協調流程的名稱，然後按一下**新增**。  

2.  如果它尚未開啟，請開啟 BizTalk 專案，[協調流程檢視] 視窗。 若要這樣做，請按一下**檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  

3.  在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  

4.  以滑鼠右鍵按一下新建立的訊息，然後按**屬性 視窗**。  

5.  在 [**屬性**] 窗格**Message_1**，執行下列動作：  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|輸入 `Request`|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*InsertInterfaceTable.OracleEBSBinding.Insert*InsertInterfaceTable 所在的 BizTalk 專案的名稱。 OracleEBSBinding 是 AR_ARCHIVE_PURGE_INTERIM 資料表上的插入作業所產生的結構描述。|  

6.  重複步驟 2 來建立新的訊息。 在 **屬性**窗格中的新訊息，執行下列動作：  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|輸入 `Response`|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*InsertInterfaceTable.OracleEBSBinding.InsertResponse*。|  

## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]for Oracle E-business Suite 上執行運算。 在此協調流程中，卸除在要求訊息定義的接收位置。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會取用這個訊息，並將它傳遞到 Oracle E-business Suite。 Oracle E-business Suite 的回應會儲存到另一個位置。 用於執行 Oracle 資料庫上的基本資料表作業的一般協調流程會包含：  

- 傳送和接收圖形以將訊息傳送至 Oracle 資料庫，並接收回應。  

- 單向接收埠以接收要求訊息傳送到 Oracle 資料庫。  

- 雙向傳送埠以傳送要求訊息到 Oracle 資料庫，並接收回應。  

- 若要從 Oracle 資料庫的回應傳送到資料夾的單向傳送埠。  

  選取作業的範例協調流程如下所示：  

  ![若要將資料插入介面資料表的協調流程](../../adapters-and-accelerators/adapter-oracle-ebs/media/8a4508c5-9949-4043-9de5-d1226db8117b.gif "8a4508c5-9949-4043-9de5-d1226db8117b")  

### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息 圖形中指定下列屬性。 剛剛提到的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。  

|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveMessage|Receive|-設定**名稱**到*ReceiveMessage*<br />-設定**啟用**到 *，則為 True*|  
|SendMessage|Send|-設定**名稱**到*SendMessage*|  
|ReceiveResponse|Receive|-設定**名稱**到*ReceiveResponse*<br />-設定**啟用**到*False*|  
|SendResponse|Send|-設定**名稱**到*SendResponse*|  

### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠中指定下列屬性。 協調流程中所示，連接埠資料行中所列的名稱會是連接埠的名稱。  

|通訊埠|屬性|  
|----------|----------------|  
|MessageIn|-設定**識別碼**到*MessageIn*<br />-設定**型別**到*MessageInType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*接收*|  
|LOBPort|-設定**識別碼**到*LOBPort*<br />-設定**型別**到*LOBPortType*<br />-設定**通訊模式**到*要求-回應*<br />-設定**通訊方向**到*傳送接收*|  
|ResponseOut|-設定**識別碼**到*ResponseOut*<br />-設定**型別**到*ResponseOutType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*傳送*|  

### <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a>為動作圖形指定訊息，並將其連接至連接埠  
 下表指定的屬性和屬性來指定動作圖形的訊息，以及連結至連接埠的訊息，您應該設定的值。 先前所述的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。  

|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveMessage|-設定**訊息**到*要求*<br />-設定**作業**到*MessageIn.Insert.Request*|  
|SendMessage|-設定**訊息**到*要求*<br />-設定**作業**到*LOBPort.Insert.Request*|  
|ReceiveResponse|-設定**訊息**到*回應*<br />-設定**作業**到*LOBPort.Insert.Response*|  
|SendResponse|-設定**訊息**到*回應*<br />-設定**作業**到*ResponseOut.Insert.Request*|  

 指定這些屬性之後，訊息 圖形和連接埠都連接，且您的協調流程完成。  

 現在，您必須建置 BizTalk 方案，並將它部署到 BizTalk Server。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。  

## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在 [協調流程] 窗格底下[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。 如需逐步解說，請參閱 <<c0> [ 逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。  

 設定應用程式包含：  

- 選取應用程式主機。  

- 對應至實體連接埠在協調流程中建立的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 此協調流程中，您必須：  

  - 定義位置上的硬碟和對應的檔案連接埠，您將會卸除要求訊息。 BizTalk 協調流程將會取用的要求訊息，並將它傳送給 Oracle E-business Suite。  

  - 定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含來自 Oracle E-business Suite 的回應的回應訊息。  

  - 定義實體的 Wcf-custom 或 Wcf-oracleebs 傳送埠將訊息傳送至 Oracle E-business Suite。 您也必須在傳送埠中指定的動作。 如需有關如何建立連接埠的資訊，請參閱[手動設定實體連接埠繫結來 Oracle E-business 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)  

     在介面資料表或介面上執行作業檢視 使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您必須設定正確的應用程式內容，叫用作業。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]提供特定的繫結屬性，以指定應用程式內容的任何作業。 您必須使用在介面資料表上執行作業的 Wcf-custom 或 Wcf-oracleebs 連接埠上設定這些繫結屬性。  

    - 如果**ClientCredentialType**繫結屬性設定為**資料庫**，則您必須指定下列繫結屬性來設定應用程式內容。  


      |        繫結屬性         |                                                                                                                                                                                                                                                                                     ReplTest1                                                                                                                                                                                                                                                                                     |
      |---------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |       **OracleUserName**        | 指定 Oracle E-business Suite 使用者的名稱。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不會保留您輸入的值的大小寫**OracleUserName**連接到 Oracle E-business Suite 時，繫結屬性。 使用者名稱會傳遞到 Oracle E-business Suite 使用 SQL 的標準規則\*加上。 不過，如果您想要保留的使用者名稱的大小寫，或您想要輸入使用者名稱包含特殊字元，您必須指定雙引號括住的值。 |
      |       **OraclePassword**        |   Oracle E-business Suite 使用者的密碼。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不會保留您輸入的值的大小寫**OraclePassword**連接到 Oracle E-business Suite 時，繫結屬性。 密碼會傳遞至 Oracle E-business Suite 使用 SQL 的標準規則\*加上。 不過，如果您想要保留密碼的情況，或您想要輸入包含特殊字元的密碼，您必須指定雙引號括住的值。    |
      | **OracleEBSResponsibilityName** |                                                                                                                                                                                                                                                     Oracle E-business Suite 使用者相關聯責任。                                                                                                                                                                                                                                                      |


    - 如果**ClientCredentialType**繫結屬性設定為**EBusiness**，您必須已指定 Oracle E-business 認證建立連線時。 在此情況下您必須僅指定值**OracleEBSResponsibilityName**繫結屬性。  

      如需不同的繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。 如需有關配接器支援設定的應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  

    > [!NOTE]
    >  指定的繫結屬性，或設定訊息內容屬性所公開，您可以設定應用程式內容[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 如需有關如何設定繫結屬性的指示，請參閱 < [for Oracle E-business Suite 中設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md)。 如需有關如何設定使用訊息內容屬性的應用程式內容的相關指示，請參閱[Oracle E-business Suite 中設定應用程式內容使用訊息內容屬性](../../adapters-and-accelerators/adapter-oracle-ebs/configure-application-context-using-message-context-properties-in-oracle-ebs.md)。  
    > 
    > [!NOTE]
    >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立繫結檔案，其中包含連接埠與那些連接埠設定動作的相關資訊。 您可以將從這個繫結檔案匯入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 （適用於輸出的呼叫） 的傳送埠或接收埠 （適用於輸入的呼叫）。 如需詳細資訊，請參閱 <<c0> [ 實體連接埠繫結使用的連接埠繫結檔設定到 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md)。  

## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 AR_ARCHIVE_PURGE_INTERIM 介面資料表中插入記錄的 BizTalk 應用程式。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。  

 在這個階段，請確定：  

-   FILE 接收埠以接收要求訊息的協調流程正在執行。  

-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  

-   Wcf-custom 或 Wcf-oracleebs 傳送埠以傳送訊息至 Oracle E-business Suite 正在執行。  

-   BizTalk 協調流程的作業正在執行。  

## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須先卸除要求訊息至檔案接收位置。 要求訊息的結構描述必須符合您稍早產生插入作業的結構描述。 例如，要從 AR_ARCHIVE_PURGE_INTERIM 介面資料表中選取 所有記錄的要求訊息是：  

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

 此要求訊息會插入 AR_ARCHIVE_PURGE_INTERIM 介面資料表的記錄。 請參閱[插入、 更新、 刪除和選取作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md)如需有關執行 Oracle E-business Suite 使用基本的 DML 作業的要求訊息結構描述[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  

 針對簡單的資料行，例如在上述的要求訊息中，您也可以使用**InlineValue**屬性。 如需有關 InlineValue 屬性的詳細資訊，請參閱中的插入作業的描述[介面資料表和介面檢視上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md)。  

 例如，內嵌值的上述要求訊息會如下所示：  

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

 在此要求訊息中，從另一個資料表，擷取 TRX_ID 資料行的值。 因此，即使 TRX_ID"001"指定的值，則 InlineValue 屬性指定的 SELECT 陳述式的值會插入至資料表。  

 協調流程取用訊息，並將它傳送至 Oracle E-business Suite。 Oracle E-business Suite 的回應會儲存在其他定義的協調流程一部分的檔案位置。 例如，上述的要求訊息從 Oracle E-business Suite 的回應是：  

```  
<?xml version="1.0" encoding="utf-8" ?>   
<InsertResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/AR/AR/AR_ARCHIVE_PURGE_INTERIM">  
  <InsertResult>1</InsertResult>   
</InsertResponse>  
```  

 回應會包含插入至資料表的資料列數目。  

## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 產生繫結檔案之後，您可以匯入的組態設定檔案，使您不需要建立項目，例如傳送埠和接收相同的協調流程的連接埠。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用與 Oracle E-business Suite 配接器繫結](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md)。  

## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式使用 Oracle E-business Suite 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)