---
title: ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業中使用 BizTalk Server 的 SQL |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d8def133-cbe1-4648-ae41-6b8ce6640cb3
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e71913a2787a9940127f11e331c176a09717b694
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994551"
---
# <a name="executereader-executescalar-or-executenonquery-operations-in-sql-using-biztalk-server"></a>ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業中使用 BizTalk Server 的 SQL
[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會公開一般的 SQL Server 作業時，這類**ExecuteNonQuery**， **ExecuteReader**，和**ExecuteScalar**。 您可以使用這些作業上的 SQL Server 資料庫執行任何 SQL 陳述式。 這些作業根據回應您取得 SQL 陳述式的類型而有所不同。 如需配接器如何支援這些作業的詳細資訊，請參閱[支援 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)。  
  
 本主題示範如何執行**ExecuteReader**作業使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 您可以依照程序中執行本主題所述的同一組**ExecuteNonQuery**並**ExecuteScalar**作業。  
  
## <a name="prerequisites"></a>必要條件  
  
- 建立[強式名稱金鑰檔案，並了解工具](prerequisites-to-create-sql-applications-using-the-sql-adapter.md)
  
- [設定 MSDTC](configure-msdtc-on-sql-server-and-adapter-client.md)上執行的電腦[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]和 SQL Server。
  
## <a name="invoke-the-executereader-operation-on-a-sql-server-database"></a>叫用 ExecuteReader 作業上的 SQL Server 資料庫  
 使用執行 SQL Server 資料庫上的作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及中所述的程序性工作[開發使用 SQL 配接器的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)。 若要叫用**ExecuteReader** SQL Server 中的作業，這些工作是：  
  
1. 建立 BizTalk 專案，並產生結構描述**ExecuteReader**作業。  
  
2. 建立傳送和接收訊息，從 SQL Server 的 BizTalk 專案中的訊息。  
  
3. 建立協調流程叫用 SQL Server 上的作業。  
  
4. 建置和部署 BizTalk 專案。  
  
5. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
6. 啟動 BizTalk 應用程式。  
  
   本主題提供執行這些工作的指示。  
  
## <a name="generate-schema"></a>產生結構描述  
 本主題示範如何叫用**ExecuteReader**在 SQL Server 中使用的作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 **ExecuteReader**作業會採用任何 SQL 陳述式，做為參數，並傳回結果集中的資料集做為陣列的作業。 本主題說明如何執行 ADD_EMP_DETAILS 預存程序使用**ExecuteReader**作業。 這個預存程序會將記錄加入 Employee 資料表，並傳回新加入的員工識別碼。 執行提供的範例指令碼會建立資料表和預存程序 > 主題中使用。 如需有關此指令碼的詳細資訊，請參閱[SQL 配接器的範例](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md)。  
  
 若要示範如何叫用**ExecuteReader**作業，會產生結構描述**ExecuteReader**作業。 您必須建立 BizTalk 專案，並使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生結構描述。 請參閱[擷取使用 SQL 配接器的 Visual Studio 中的 SQL Server 作業的中繼資料](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)如需有關如何產生結構描述。  
  
## <a name="define-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是一個變數，要為其類型會定義對應的結構。 現在，建立協調流程的訊息，並將它們連結至您在上一個步驟中產生的結構描述。  
  
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
  
## <a name="set-up-the-orchestration"></a>設定協調流程  
 建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行 SQL Server 上的作業。 在此協調流程中，卸除在要求訊息定義的接收位置。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會取用這個訊息，並將它傳遞到 SQL Server。 從 SQL Server 的回應會儲存到另一個位置。 您必須包含傳送和接收圖形，將訊息傳送至 SQL Server，並接收回應，分別。 範例協調流程叫用**ExecuteReader**作業如下所示：  
  
 ![若要叫用 ExecuteReader 操作的協調流程](../../adapters-and-accelerators/adapter-sql/media/2ac8dc12-918a-4077-a95c-f66b1c0ef4f0.gif "2ac8dc12-918a-4077-a95c-f66b1c0ef4f0")  
  
### <a name="add-message-shapes"></a>新增訊息圖形  
 輸入下列屬性的每個訊息 圖形。 剛剛提到的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveMessage|Receive|-設定**名稱**到*ReceiveMessage*<br />-設定**啟用**到 *，則為 True*|  
|SendMessage|Send|-設定**名稱**到*SendMessage*|  
|ReceiveResponse|Receive|-設定**名稱**到*ReceiveResponse*<br />-設定**啟用**到*False*|  
|SendResponse|Send|-設定**名稱**到*SendResponse*|  
  
### <a name="add-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠中指定下列屬性。 協調流程中所示，連接埠資料行中所列的名稱會是連接埠的名稱。  
  
|通訊埠|屬性|  
|----------|----------------|  
|MessageIn|-設定**識別碼**到*MessageIn*<br />-設定**型別**到*MessageInType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*接收*|  
|LOBPort|-設定**識別碼**到*LOBPort*<br />-設定**型別**到*LOBPortType*<br />-設定**通訊模式**到*要求-回應*<br />-設定**通訊方向**到*傳送接收*|  
|ResponseOut|-設定**識別碼**到*ResponseOut*<br />-設定**型別**到*ResponseOutType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*傳送*|  
  
### <a name="enter-messages-for-action-shapes-and-connect-them-to-ports"></a>輸入訊息的動作圖形，並將其連接至連接埠  
 下表指定的屬性和屬性來指定動作圖形的訊息，以及連結至連接埠的訊息，您應該設定的值。 先前所述的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveMessage|-設定**訊息**到*要求*<br />-設定**作業**到*MessageIn.ExecuteReader.Request*|  
|SendMessage|-設定**訊息**到*要求*<br />-設定**作業**到*LOBPort.ExecuteReader.Request*|  
|ReceiveResponse|-設定**訊息**到*回應*<br />-設定**作業**到*LOBPort.ExecuteReader.Response*|  
|SendResponse|-設定**訊息**到*回應*<br />-設定**作業**到*ResponseOut.ExecuteReader.Request*|  
  
 指定這些屬性之後，訊息 圖形和連接埠都連接，且您的協調流程完成。  
  
 現在，您必須建置 BizTalk 方案，並將它部署到 BizTalk Server。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。
  
## <a name="configure-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在 [協調流程] 窗格底下[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。 如需有關如何設定應用程式的詳細資訊，請參閱 <<c0> [ 逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。
  
 設定應用程式包含：  
  
- 選取應用程式主機。  
  
- 對應至實體連接埠在協調流程中建立的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 此協調流程中，您必須：  
  
  - 定義位置上的硬碟和對應的檔案連接埠，您將會卸除要求訊息。 BizTalk 協調流程將會取用的要求訊息，並將它傳送到 SQL Server 資料庫。  
  
  - 定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含從 SQL Server 資料庫回應的回應訊息。  
  
  - 定義實體 Wcf-custom 或 WCF SQL 傳送埠將訊息傳送至 SQL Server 資料庫。 您也必須在傳送埠中指定的動作。 如需有關如何建立連接埠的資訊，請參閱 <<c0> [ 手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。
  
    > [!NOTE]
    >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立繫結檔案，其中包含連接埠與那些連接埠設定動作的相關資訊。 您可以將從這個繫結檔案匯入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 （適用於輸出的呼叫） 的傳送埠或接收埠 （適用於輸入的呼叫）。 如需詳細資訊，請參閱 <<c0> [ 設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。
  
## <a name="start-the-application"></a>啟動應用程式  
 啟動 BizTalk 應用程式叫用**ExecuteReader** SQL Server 資料庫中的作業。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程正在執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   WCF 自訂] 或 [WCF-SQL 傳送埠將訊息傳送至 SQL Server 資料庫正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="execute-the-operation"></a>執行作業  
 執行應用程式之後，您必須先卸除要求訊息至檔案接收位置。 要求訊息的結構描述必須符合的結構描述**ExecuteReader**您稍早產生的作業。 例如，要求訊息來叫用使用 ADD_EMP_DETAILS **ExecuteReader**作業：  
  
```  
<ExecuteReader xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">  
  <Query>EXEC ADD_EMP_DETAILS Tom,Manager,100000</Query>  
</ExecuteReader>  
```  
  
 請參閱[ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/executenonquery-executereader-and-executescalar-message-schemas-in-sql.md)如需叫用的要求訊息結構描述**ExecuteReader**作業使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
> [!NOTE]
>  內`<Query>`標記，您可以指定多個以分號分隔的 SQL 陳述式。  
  
 協調流程取用訊息，並將它傳送到 SQL Server 資料庫。 從 SQL Server 資料庫的回應會儲存在其他定義的協調流程一部分的檔案位置。 回應**ExecuteReader**作業包含結果集，做為資料集的陣列。 例如，從先前的要求訊息的 SQL Server 資料庫的回應是：  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<ExecuteReaderResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">  
  <ExecuteReaderResult>  
    <DataSet xmlns="http://schemas.datacontract.org/2004/07/System.Data">  
      <xs:schema id="NewDataSet" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
        <xs:element msdata:IsDataSet="true" name="NewDataSet">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element minOccurs="0" maxOccurs="unbounded" name="NewTable">  
                <xs:complexType>  
                  <xs:sequence>  
                    <xs:element minOccurs="0" name="Employee_ID" type="xs:int" />   
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
            <Employee_ID>10767</Employee_ID>   
          </NewTable>  
        </NewDataSet>  
      </diffgr:diffgram>  
    </DataSet>  
  </ExecuteReaderResult>  
</ExecuteReaderResponse>  
```  
  
 在回應中，10767 會是員工的新建立識別碼。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 一旦您產生繫結檔案時，您可以匯入的組態設定檔案，，讓您不需要建立項目，例如傳送埠和接收相同的協調流程的連接埠。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用配接器繫結](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)。
  
## <a name="see-also"></a>另請參閱  
[使用 SQL 配接器開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)