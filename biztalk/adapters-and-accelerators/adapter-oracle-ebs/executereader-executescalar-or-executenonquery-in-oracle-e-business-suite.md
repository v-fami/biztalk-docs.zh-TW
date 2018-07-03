---
title: Oracle E-business Suite 中的 ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1e2d377d-60a2-45fe-8458-433e6f4f6619
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00f511ec8a49981e1db2c8346a5cf17b030ebe5a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989655"
---
# <a name="executereader-executescalar-or-executenonquery-operations-in-oracle-e-business-suite"></a>Oracle E-business Suite 中的 ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業
[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會公開一般作業時，這類**ExecuteNonQuery**， **ExecuteReader**，和**ExecuteScalar**。 Oracle 資料庫上執行任何 SQL 陳述式，您可以使用這些作業。 這些作業根據回應您取得 SQL 陳述式的類型而有所不同。 如需配接器如何支援這些作業的詳細資訊，請參閱[支援 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)。  
  
 本主題示範如何執行**ExecuteReader**作業使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 您可以依照程序中執行本主題所述的同一組**ExecuteNonQuery**並**ExecuteScalar**作業。  
  
## <a name="how-to-invoke-executereader-operation-on-oracle-database"></a>如何在 Oracle Database 上的叫用 ExecuteReader 操作  
 執行所使用的 Oracle 資料庫上的作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及中所述的程序性工作[建立 Oracle E-business Suite 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)。 若要叫用**ExecuteReader** Oracle 資料庫上的作業，這些工作是：  
  
1. 建立 BizTalk 專案，並產生結構描述**ExecuteReader**作業。  
  
2. 建立傳送和接收訊息，從 Oracle 資料庫的 BizTalk 專案中的訊息。  
  
3. 建立協調流程叫用 Oracle 資料庫的作業。  
  
4. 建置和部署 BizTalk 專案。  
  
5. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
6. 啟動 BizTalk 應用程式。  
  
   本主題提供執行這些工作的指示。  
  
## <a name="generating-schema"></a>產生結構描述  
 本主題示範如何叫用**ExecuteReader** Oracle 資料庫使用的作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 **ExecuteReader**作業會採用任何 SQL 陳述式，做為參數，並傳回結果集中的資料集做為陣列的作業。 本主題中，執行 SELECT 陳述式上使用 ACCOUNTACTIVITY 表**ExecuteReader**作業。 ACCOUNTACTIVITY 資料表會建立執行範例所提供的指令碼。 如需有關此指令碼的詳細資訊，請參閱[範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。  
  
 若要示範如何叫用**ExecuteReader**作業，會產生結構描述**ExecuteReader**作業。 您必須建立 BizTalk 專案，並使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生結構描述。 如需如何產生結構描述的詳細資訊，請參閱[擷取 Oracle E-business Suite 作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)。  
  
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
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*Execute_Reader.GenericOperation.ExecuteReader*Execute_Reader 所在的 BizTalk 專案的名稱。 *GenericOperation*是針對產生的結構描述**ExecuteReader**作業。|  
  
6.  重複步驟 2 來建立新的訊息。 在 **屬性**窗格中的新訊息，執行下列動作：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|輸入 `Response`|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*Execute_Reader.GenericOperation.ExecuteReaderResponse*。|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]的 Oracle 資料庫上執行運算。 在此協調流程中，卸除在要求訊息定義的接收位置。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會取用這個訊息，並將它傳遞到 Oracle 資料庫。 Oracle 資料庫的回應會儲存到另一個位置。 典型的協調流程，例如叫用泛型作業**ExecuteReader**會包含：  
  
- 傳送和接收圖形，來傳送和接收訊息，從 Oracle 資料庫。  
  
- 雙向接收埠以傳送和接收訊息，從 Oracle 資料庫。  
  
- 若要從 Oracle 資料庫的回應傳送到資料夾的單向傳送埠。  
  
  範例協調流程叫用**ExecuteReader**作業如下所示：  
  
  ![若要叫用 ExecuteReader 操作的協調流程](../../adapters-and-accelerators/adapter-oracle-ebs/media/37b63331-76b7-47a2-b9d3-0c60e165d993.gif "37b63331-76b7-47a2-b9d3-0c60e165d993")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 您需要針對每個訊息 圖形中設定下列屬性。 圖形資料行中所列的名稱對應至訊息 圖形的名稱，剛剛提到的協調流程中所示。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveMessage|Receive|-設定**名稱**到*ReceiveMessage*<br />-設定**啟用**到 *，則為 True*|  
|SendMessage|Send|-設定**名稱**到*SendMessage*|  
|ReceiveResponse|Receive|-設定**名稱**到*ReceiveResponse*<br />-設定**啟用**到*False*|  
|SendResponse|Send|-設定**名稱**到*SendResponse*|  
  
### <a name="adding-ports"></a>新增連接埠  
 針對每個邏輯連接埠，請在下表中設定的屬性。 協調流程中所示，連接埠資料行中所列的名稱會對應至連接埠的名稱。  
  
|通訊埠|屬性|  
|----------|----------------|  
|MessageIn|-設定**識別碼**到*MessageIn*<br />-設定**型別**到*MessageInType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*接收*|  
|LOBPort|-設定**識別碼**到*LOBPort*<br />-設定**型別**到*LOBPortType*<br />-設定**通訊模式**到*要求-回應*<br />-設定**通訊方向**到*傳送接收*|  
|ResponseOut|-設定**識別碼**到*ResponseOut*<br />-設定**型別**到*ResponseOutType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*傳送*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a>為動作圖形指定訊息，並將其連接至連接埠  
 下表指定的屬性值來指定動作圖形的訊息，以及連結至連接埠的訊息。 所列的名稱**圖形**資料行對應至訊息 圖形的名稱，如稍早在協調流程圖中顯示。  
  
 您已設定這些屬性之後，連線的訊息 圖形和連接埠，和您的協調流程已完成。  
  
 然後，您現在必須建置 BizTalk 方案，並將它部署到 BizTalk Server。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveMessage|-設定**訊息**到*要求*<br />-設定**作業**到*MessageIn.Exec_Reader.Request*|  
|SendMessage|-設定**訊息**到*要求*<br />-設定**作業**到*LOBPort.Exec_Reader.Request*|  
|ReceiveResponse|-設定**訊息**到*回應*<br />-設定**作業**到*LOBPort.Exec_Reader.Response*|  
|SendResponse|-設定**訊息**到*回應*<br />-設定**作業**到*ResponseOut.Exec_Reader.Request*|  
  
 指定這些屬性之後，訊息 圖形和連接埠都連接，且您的協調流程完成。  
  
 現在，您必須建置 BizTalk 方案，並將它部署到 BizTalk Server。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。  
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在下**協調流程** 窗格中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。 如需逐步解說，請參閱 <<c0> [ 逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。  
  
 設定應用程式包含：  
  
- 選取應用程式主機。  
  
- 對應至實體連接埠在協調流程中建立的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 此協調流程中，您必須：  
  
  - 定義位置上的硬碟和對應的檔案連接埠，您將會卸除要求訊息。 BizTalk 協調流程將會取用的要求訊息，並將它傳送到 Oracle 資料庫。  
  
  - 定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含從 Oracle 資料庫回應的回應訊息。  
  
  - 定義實體的 Wcf-custom 或 Wcf-oracleebs 傳送埠將訊息傳送至 Oracle 資料庫。 您也必須在傳送埠中指定的動作。 如需有關如何建立傳送埠的資訊，請參閱 <<c0> [ 手動設定實體連接埠繫結來 Oracle E-business 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)。  
  
    > [!IMPORTANT]
    >  在一般作業，如果您執行作業的物件，例如預存程序、 函數、 介面資料表或隸屬於 Oracle E-business Suite 應用程式的介面檢視，您必須藉由指定設定應用程式內容必要的繫結屬性。 如需設定應用程式內容的詳細資訊，請參閱 <<c0> [ 設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
    > 
    >  指定的繫結屬性，或設定訊息內容屬性所公開，您可以設定應用程式內容[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 如需有關如何設定繫結屬性的指示，請參閱 < [for Oracle E-business Suite 中設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md)。 如需有關如何設定使用訊息內容屬性的應用程式內容的相關指示，請參閱[Oracle E-business Suite 中設定應用程式內容使用訊息內容屬性](../../adapters-and-accelerators/adapter-oracle-ebs/configure-application-context-using-message-context-properties-in-oracle-ebs.md)。  
    > 
    > [!NOTE]
    >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立繫結檔案，其中包含連接埠與那些連接埠設定動作的相關資訊。 您可以將從這個繫結檔案匯入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 （適用於輸出的呼叫） 的傳送埠或接收埠 （適用於輸入的呼叫）。 如需詳細資訊，請參閱 <<c0> [ 實體連接埠繫結使用的連接埠繫結檔設定到 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md)。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式，然後再叫用**ExecuteReader** Oracle 資料庫上的作業。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。  
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程正在執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   Wcf-oracleebs 的 Wcf-custom 傳送埠將訊息傳送至 Oracle 資料庫執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須先卸除要求訊息至檔案接收位置。 要求訊息的結構描述必須符合的結構描述**ExecuteReader**您稍早產生的作業。 比方說，要執行的 SELECT 陳述式使用的要求訊息**ExecuteReader**作業：  
  
```  
<ExecuteReader xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/">  
  <Query>SELECT * FROM ACCOUNTACTIVITY</Query>  
</ExecuteReader>  
```  
  
 如 ExecuteReader、 ExecuteScalar 及 ExecuteNonQuery 作業叫用的要求訊息結構描述的詳細資訊，請參閱訊息結構描述**ExecuteReader**作業使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  
  
 協調流程取用訊息，並將它傳送到 Oracle 資料庫。 從 Oracle 資料庫的回應會儲存在其他定義的協調流程一部分的檔案位置。 回應**ExecuteReader**作業包含結果集，做為資料集。 例如，從先前的要求訊息的 Oracle 資料庫的回應是：  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<ExecuteReaderResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/">  
  <ExecuteReaderResult>  
    <xs:schema id="NewDataSet" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
      <xs:element msdata:IsDataSet="true" name="NewDataSet">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element minOccurs="0" maxOccurs="unbounded" name="NewTable">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element minOccurs="0" name="TID" type="xs:decimal" />   
                  <xs:element minOccurs="0" name="ACCOUNT" type="xs:decimal" />   
                  <xs:element minOccurs="0" name="AMOUNT" type="xs:decimal" />   
                  <xs:element minOccurs="0" name="DESCRIPTION" type="xs:string" />   
                  <xs:element minOccurs="0" name="TRANSDATE" type="xs:dateTime" />   
                  <xs:element minOccurs="0" name="PROCESSED" type="xs:string" />   
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:schema>  
    <diffgr:diffgram xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
      <NewDataSet xmlns="">  
        <NewTable>  
          <TID>1</TID>   
          <ACCOUNT>100001</ACCOUNT>   
          <AMOUNT>500</AMOUNT>   
          <DESCRIPTION />   
          <TRANSDATE>2008-08-04T13:04:20</TRANSDATE>   
          <PROCESSED>n</PROCESSED>   
        </NewTable>  
        <NewTable>  
          ......  
          ......  
        </NewTable>  
        ......  
        ......  
      </NewDataSet>  
    </diffgr:diffgram>  
  </ExecuteReaderResult>  
</ExecuteReaderResponse>  
```  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 產生繫結檔案之後，您可以匯入的組態設定檔案，使您不需要建立項目，例如傳送埠和接收相同的協調流程的連接埠。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用與 Oracle E-business Suite 配接器繫結](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md)。  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式使用 Oracle E-business Suite 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)