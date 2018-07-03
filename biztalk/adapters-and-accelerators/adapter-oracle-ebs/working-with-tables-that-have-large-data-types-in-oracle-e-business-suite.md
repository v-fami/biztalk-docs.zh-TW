---
title: 使用 Oracle E-business Suite 中有大型的資料類型的資料表 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 501aa302-0f82-4221-b99f-423bc8621a6a
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf03c256ed525274c808c75704ce252728dc2aa2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971647"
---
# <a name="working-with-tables-that-have-large-data-types-in-oracle-e-business-suite"></a>使用 Oracle E-business Suite 中有大型的資料類型的資料表
[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可讓配接器用戶端來執行大型資料類型，例如 BLOB、 CLOB、 NCLOB、 和 BFILE 介面資料表和檢視表上的作業。  
  
- 類型的資料行 BLOB、 CLOB、 和 NCLOB 配接器，可讓用戶端讀取，以及更新資料。 配接器會公開 Read_\<LOBColName\>和 Update_\<LOBColName\>作業來讀取和更新資料，其中\<LOBColName\>是具有大型資料行名稱資料型別。 如果沒有單一的介面資料表中的大型資料類型的多個資料行，配接器會公開為許多讀取和更新該介面資料表的作業。  
  
- 型別 BFILE 資料行，配接器用戶端只能讀取資料。 配接器會公開 Read_\<LOBColName\> BFILE 類型的資料行中讀取資料的作業。 如果沒有單一的介面資料表中的大型資料類型的多個資料行，配接器會公開為許多讀取作業的介面資料表。  
  
  如需有關這些作業的詳細資訊，請參閱 < [Interface Table、 介面檢視、 資料表和檢視表，包含 LOB 資料的作業](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md)。 如需執行這些作業的訊息結構描述資訊，請參閱[特殊 LOB 作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-special-lob-operations1.md)。  
  
## <a name="how-to-perform-operations-on-columns-with-large-data-types"></a>如何在大型資料類型的資料行上執行作業  
 使用執行 Oracle E-business Suite 作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及中所述的程序性工作[建立 Oracle E-business Suite 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)。 若要執行包含大型資料類型的 Oracle E-business Suite 介面資料表和介面檢視上的作業，這些工作如下：  
  
1. 建立 BizTalk 專案，並產生作業的結構描述 (Read_\<LOBColName\>或 Update_\<LOBColName\>) 您想要在資料表或檢視表上叫用。  
  
2. 建立傳送和接收訊息，從 Oracle E-business Suite 的 BizTalk 專案中的訊息。  
  
3. 建立協調流程叫用在介面資料表或檢視表上的作業。  
  
4. 建置和部署 BizTalk 專案。  
  
5. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
6. 啟動 BizTalk 應用程式。  
  
   本主題提供執行這些工作的指示。  
  
## <a name="how-this-topic-demonstrates-reading-and-writing-data-into-columns-of-large-data-types"></a>本主題示範如何讀取和寫入大型資料類型的資料行中的資料  
 為了示範讀取和寫入大型資料類型的資料行中的資料，本主題會提供指示來建立的協調流程，會執行下列作業：  
  
- 更新 （的 BLOB 資料類型） 的客戶資料表的 PHOTO 資料行。  
  
- 讀取已更新資料錄的 PHOTO 資料行的值。  
  
  此協調流程是一種您只提供更新作業在執行階段的要求訊息。 在作業中，將會建構讀取作業的訊息。  
  
> [!NOTE]
>  本主題中的協調流程讀取，並建立執行範例所提供的指令碼從 CUSTOMER 資料表中，這是基底資料庫資料表的更新資料。 本主題，以執行讀取或更新任何介面資料表或介面檢視上的作業中所述，您必須執行類似的程序。  
  
## <a name="generating-schema"></a>產生結構描述  
 本主題示範如何執行基本的讀取和更新的相片資料行上 （BLOB 資料類型） CUSTOMER 資料表中的作業。 執行提供的範例指令碼會建立此資料表。  
  
 為了示範如何讀取及寫入大型資料類型的資料行中的資料，用於產生結構描述**Update_PHOTO**並**Read_PHOTO** CUSTOMER 資料表中的作業。 您必須建立 BizTalk 專案，並使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生結構描述。 請參閱[擷取 Oracle E-business Suite 作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)如需有關如何產生結構描述。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是一個變數，要為其類型會定義對應的結構。 現在，您必須建立協調流程的訊息，並將它們連結至您在上一個步驟中產生的結構描述。  
  
 在此協調流程中，您必須建立四個訊息，設定一個接收回應**Update_PHOTO**為設定作業與其他接收回應**Read_PHOTO**作業。  
  
#### <a name="to-create-messages-and-link-to-schema"></a>若要建立訊息，並連結至結構描述  
  
1.  BizTalk 專案中新增協調流程。 從 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下**新項目**。 輸入 BizTalk 協調流程的名稱，然後按一下**新增**。  
  
2.  如果它尚未開啟，請開啟 BizTalk 專案，[協調流程檢視] 視窗。 若要這樣做，請按一下**檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  
  
3.  在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  
  
4.  以滑鼠右鍵按一下新建立的訊息，然後按**屬性 視窗**。  
  
5.  在 [**屬性**] 窗格**Message_1**，執行下列動作：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|輸入 `UpdateMessage`|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*LOBOperations.OracleEBSBinding.Update_PHOTO*LOBOperations 所在的 BizTalk 專案的名稱。 OracleEBSBindingSchema 是叫用所產生的結構描述**Update_PHOTO** CUSTOMER 資料表上的作業。|  
  
6.  重複步驟 3 以建立三個新的訊息。 在 **屬性**窗格中的新訊息，執行下列動作：  
  
    |若要設定識別項|若要設定訊息類型|  
    |-----------------------|-------------------------|  
    |UpdateResponse|*LOBOperations.OracleEBSBinding.Update_PHOTOResponse*|  
    |ReadMessage|*LOBOperations.OracleEBSBinding1.Read_PHOTO*|  
    |ReadResponse|*LOBOperations.OracleEBSBinding1.Read_PHOTOResponse*|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 在此協調流程中，配接器會接收要求訊息給 Update_PHOTO 上執行作業的客戶資料表。 檔案位置就會收到通知訊息。 配接器會取用這個訊息，並將它傳遞到 Oracle 資料庫。 Oracle 資料庫的回應會儲存在另一個位置。 一旦收到回應時，協調流程會建構要叫用 Read_PHOTO 作業，它會讀取 Update_PHOTO 作業更新 PHOTO 資料行值的訊息。 此訊息的回應也就會收到相同的檔案位置。  
  
 因此，您的協調流程必須包含下列各項：  
  
- FILE 接收埠，卸除的要求訊息**Update_PHOTO**作業。  
  
- 雙向 Wcf-custom 或 Wcf-oracleebs 傳送埠以傳送訊息至執行**Update_PHOTO**作業。  
  
- 雙向 Wcf-custom 或 Wcf-oracleebs 傳送埠以傳送訊息至執行**Read_PHOTO**作業。 您也可以執行這兩**Read_PHOTO**並**Update_PHOTO**使用相同的 Wcf-custom 或 Wcf-oracleebs 傳送埠。 本主題中，您將這兩個作業使用單一傳送埠。  
  
- A**建構訊息**圖形，在協調流程中的訊息。  
  
- 檔案傳送至儲存的回應訊息的連接埠**Update_PHOTO**並**Read_PHOTO**作業。  
  
- 接收和傳送圖形。  
  
  範例協調流程如下所示。  
  
  ![處理大型資料類型資料行的協調流程](../../adapters-and-accelerators/adapter-oracle-ebs/media/1976ab27-94c3-4039-a1ca-8790e8897ad5.gif "1976ab27-94c3-4039-a1ca-8790e8897ad5")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息 圖形中指定下列屬性。 剛剛提到的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveUpdateMessage|Receive|-設定**名稱**到*ReceiveUpdateMessage*<br />-設定**啟用**到 *，則為 True*|  
|SendUpdateMessage|Send|-設定**名稱**到*SendUpdateMessage*|  
|ReceiveUpdateResponse|Receive|-設定**名稱**到*ReceiveUpdateResponse*|  
|SendUpdateResponse|Receive|-設定**名稱**到*SendUpdateResponse*|  
|SendReadMessage|Send|-設定**名稱**到*SendReadMessage*|  
|ReceiveReadResponse|Receive|-設定**名稱**到*ReceiveReadResponse*|  
|SaveReadResponse|Send|-設定**名稱**到*SaveReadResponse*|  
  
### <a name="adding-construct-message-shape"></a>新增 建構訊息圖形  
 您可以使用**建構的訊息**產生要求訊息的協調流程內執行的圖形**Read_PHOTO**作業。 若要這樣做，您必須加入**建構的訊息**圖形，並在其中**訊息指派**圖形至協調流程。 此範例中，如**訊息指派**圖形叫用可產生的訊息，傳送到 Oracle E-business Suite 來執行程式碼**Read_PHOTO**作業。 **訊息指派**圖形也會將訊息傳送至 Oracle E-business Suite 的動作。  
  
 針對 「 建構訊息 」 圖形中，設定**建構的訊息**屬性設**ReadMessage**。  
  
 若要產生回應的程式碼可以是相同的 Visual Studio 方案，為您的 BizTalk 專案的一部分。 產生回應訊息的範例程式碼看起來像這樣。  
  
```  
namespace MessageCreator  
{  
    public class MessageCreator  
    {  
        private static XmlDocument Message;  
        private static string XmlFileLocation;  
        private static string ResponseDoc;  
  
        public static XmlDocument XMLMessageCreator()  
        {  
            XmlFileLocation = "C:\\TestLocation\\MessageIn";  
            try  
            {  
                ResponseDoc = (Directory.GetFiles(XmlFileLocation, "*.xml", SearchOption.TopDirectoryOnly))[0];  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Trying to get XML from: " + XmlFileLocation);  
                Console.WriteLine("EXCEPTION: " + ex.ToString());  
                throw ex;  
            }  
            //Create Message From XML  
            Message = new XmlDocument();  
            Message.PreserveWhitespace = true;  
            Message.Load(ResponseDoc);  
            return Message;  
        }   
    }  
}  
```  
  
 針對上述的程式碼摘錄能夠產生要求訊息中，您必須擁有 XML 要求訊息 (如**Read_PHOTO**作業) 中指定的位置`XmlFileLocation`變數。  
  
> [!NOTE]
>  建置專案之後，就會建立 MessageCreator.dll 專案目錄中。 您必須將此 DLL 加入全域組件快取 (GAC)。 此外，您必須新增 MessageCreator.dll 做為 BizTalk 專案中的參考。  
  
 加入下列運算式來叫用此程式碼**訊息指派**圖形，並設定訊息的動作。 若要新增運算式，請按兩下**訊息指派**圖形以開啟 運算式編輯器。  
  
```  
ReadMessage = MessageCreator.MessageCreator.XMLMessageCreator();  
ReadMessage(WCF.Action) = "Tables/ReadLOB/SCOTT/CUSTOMER/PHOTO ";  
```  
  
### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠中指定下列屬性。 協調流程中所示，連接埠資料行中所列的名稱會是連接埠的名稱。  
  
|通訊埠|屬性|  
|----------|----------------|  
|MessageIn|-設定**識別碼**到*MessageIn*<br />-設定**型別**到*MessageInType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*接收*|  
|LOBPort|-設定**識別碼**到*LOBPort*<br />-設定**型別**到*LOBPortType*<br />-設定**通訊模式**到*要求-回應*<br />-設定**通訊方向**到*傳送接收*<br />-建立作業*Read_LOB*。 這項作業的訊息用於讀取大型資料類型資料行的值。<br />-建立作業*Update_LOB*。 這項作業的訊息用於更新大型資料類型資料行的值。|  
|ResponseOut|-設定**識別碼**到*ResponseOut*<br />-設定**型別**到*ResponseOutType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*傳送*<br />-建立作業*Read_LOB*。 這項作業的訊息用於讀取大型資料類型資料行的值。<br />-建立作業*Update_LOB*。 這項作業的訊息用於更新大型資料類型資料行的值。|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>為動作圖形指定訊息，並連接到連接埠  
 下表指定的屬性和屬性來指定動作圖形的訊息，以及連結至連接埠的訊息，您應該設定的值。 先前所述的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveUpdateMessage|-設定**訊息**到*UpdateMessage*<br />-設定**作業**到*MessageIn.Update_LOB。要求*|  
|SendUpdateMessage|-設定**訊息**到*UpdateMessage*<br />-設定**作業**到*LOBPort.Update_LOB。要求*|  
|ReceiveUpdateResponse|-設定**訊息**到*UpdateResponse*<br />-設定**作業**到*LOBPort.Update_LOB。回應*|  
|SendUpdateResponse|-設定**訊息**到*UpdateResponse*<br />-設定**作業**到*ResponseOut.Update_LOB。要求*|  
|SendReadMessage|-設定**訊息**到*ReadMessage*<br />-設定**作業**到*LOBPort.Read_LOB。要求*|  
|ReceiveReadResponse|-設定**訊息**到*ReadResponse*<br />-設定**作業**到*LOBPort.Read_LOB。回應*|  
|SendReadResponse|-設定**訊息**到*ReadResponse*<br />-設定**作業**到*ResponseOut.Read_LOB。要求*|  
  
 您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並將其部署至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。  
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在 [協調流程] 窗格底下[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。 如需逐步解說，請參閱 <<c0> [ 逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。
  
 設定應用程式包含：  
  
- 選取應用程式主機。  
  
- 對應至實體連接埠在協調流程中建立的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 此協調流程中，您必須：  
  
  - 定義位置上的硬碟和對應的檔案連接埠，您將會卸除要求訊息。 BizTalk 協調流程將會取用的要求訊息，並將它傳送到 Oracle 資料庫。  
  
  - 定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含從 Oracle 資料庫回應的回應訊息。  
  
  - 定義實體的 Wcf-custom 或 Wcf-oracleebs 傳送埠將訊息傳送至 Oracle 資料庫。 您也必須在傳送埠中指定的動作。 如需有關如何建立連接埠的資訊，請參閱 <<c0> [ 手動設定實體連接埠繫結來 Oracle E-business 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)。 您必須考量下列事項時設定 Wcf-custom 或 Wcf-oracleebs 傳送埠。  
  
    -   `Update_<LOBColName>`作業必須執行交易的一部分。 為了確保功效， **UseAmbientTransaction**繫結屬性必須設定為 **，則為 True**。  
  
    -   因為 Wcf-oracleebs 的 WCF 自訂傳送連接埠傳送和接收訊息符合多個結構描述，並執行兩項作業，您必須設定兩個作業的動態動作。 如需有關動作的詳細資訊，請參閱[for Oracle E-business Suite 中設定 SOAP 動作](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-soap-action-for-oracle-e-business-suite.md)。 此協調流程中，動作應該依下列方式設定：  
  
        ```  
        <BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
          <Operation Name="Update_LOB" Action="Tables/UpdateBlob/SCOTT/CUSTOMER/PHOTO" />  
          <Operation Name="Read_LOB" Action="Tables/ReadLOB/SCOTT/CUSTOMER/PHOTO" />  
        </BtsActionMapping>  
        ```  
  
        > [!IMPORTANT]
        >  請注意，動態動作中的作業名稱必須與您的邏輯連接埠所建立 BizTalk 協調流程時指定的作業名稱相同。  
  
    > [!NOTE]
    >  在介面資料表或介面檢視上執行作業，您也必須設定應用程式內容。 如需有關配接器支援設定的應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。 指定的繫結屬性，或設定訊息內容屬性所公開，您可以設定應用程式內容[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 如需有關如何設定繫結屬性的指示，請參閱 < [for Oracle E-business Suite 中設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md)。 如需有關如何設定使用訊息內容屬性的應用程式內容的相關指示，請參閱[Oracle E-business Suite 中設定應用程式內容使用訊息內容屬性](../../adapters-and-accelerators/adapter-oracle-ebs/configure-application-context-using-message-context-properties-in-oracle-ebs.md)。  
    > 
    > [!NOTE]
    >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立繫結檔案，其中包含連接埠與那些連接埠設定動作的相關資訊。 您可以將從這個繫結檔案匯入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 （適用於輸出的呼叫） 的傳送埠或接收埠 （適用於輸入的呼叫）。 如需詳細資訊，請參閱 <<c0> [ 實體連接埠繫結使用的連接埠繫結檔設定到 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md)。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 開始之前，BizTalk 協調流程，請確定要求 XML 來叫用**Read_PHOTO**作業將會位於 C:\TestLocation\MessageIn。 要求 XML 必須如下所示：  
  
```  
<Read_PHOTO xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/SCOTT/CUSTOMER">  
  <FILTER>WHERE NAME='Mindy Martin'</FILTER>  
</Read_PHOTO>  
```  
  
> [!NOTE]
>  要求訊息會具有特定名稱篩選器因為中的要求訊息**Update_PHOTO** PHOTO 資料行的值的作業會更新相同的名稱。 因此，讀取的作業會讀取相同的值，您將使用更新作業。  
  
 現在，您必須啟動 BizTalk 應用程式，用於讀取和寫入大型資料類型的值從 Oracle 資料庫。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。  
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程正在執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   Wcf-oracleebs 的 Wcf-custom 傳送埠將訊息傳送至 Oracle 資料庫執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 啟動應用程式，您必須先卸除後檔案的要求訊息的接收位置。 要求訊息的結構描述必須符合的結構描述**Update_PHOTO**您稍早產生的作業。 例如，要求訊息，以更新客戶資料表的 PHOTO 資料行如下所示：  
  
```  
<Update_PHOTO xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/SCOTT/CUSTOMER">  
  <FILTER>WHERE Name='Mindy Martin'</FILTER>  
  <DATA>U2FtcGxlIERhdGE=</DATA>  
</Update_PHOTO>  
```  
  
> [!NOTE]
>  在更新 BLOB 資料行，資料元素必須永遠包含 base64 編碼值。 CLOB 和 NCLOB，資料元素可以有字串值。  
  
 上述的要求訊息更新符合 WHERE 子句之資料錄 PHOTO 資料行中的值。 請參閱適用於大型的資料型別上之要求訊息結構描述，使用大型資料類型上執行作業的詳細資訊的作業的訊息結構描述[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  
  
 協調流程取用訊息，並將它傳送到 Oracle 資料庫。 Oracle 資料庫的回應會儲存在其他定義的協調流程一部分的檔案位置。 例如，上述的要求訊息的 Oracle 資料庫的回應如下所示：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<Update_PHOTOResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/SCOTT/CUSTOMER" />  
```  
  
 現在的協調流程會建構的要求訊息**Read_PHOTO**藉由在 C:\TestLocation\MessageIn 使用可用的要求訊息的作業。 要求訊息傳送至 Oracle 資料庫，並回應儲存在相同的檔案位置。 PHOTO 資料行的讀取作業的回應如下所示：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<Read_PHOTOResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/SCOTT/CUSTOMER">  
  <Read_PHOTOResult>U2FtcGxlIERhdGE=</Read_PHOTOResult>  
</Read_PHOTOResponse>  
```  
  
> [!NOTE]
>  請注意，回應會包含您傳入 PHOTO 資料行的相同值**Update_PHOTO**作業。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 一旦您產生繫結檔案時，您可以匯入的組態設定檔案，，讓您不需要建立項目，例如傳送埠和接收相同的協調流程的連接埠。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用與 Oracle E-business Suite 配接器繫結](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md)。  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式使用 Oracle E-business Suite 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)