---
title: "使用 Oracle E-business Suite 中具有大型資料類型的資料表，|Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 501aa302-0f82-4221-b99f-423bc8621a6a
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6cc357809ecc446c0c282f6a4f8fa46ad7392a53
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="working-with-tables-that-have-large-data-types-in-oracle-e-business-suite"></a>使用 Oracle E-business Suite 中具有大型資料類型的資料表
[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可讓配接器用戶端執行具有大型資料類型，例如 BLOB、 CLOB、 NCLOB、 和 BFILE 介面資料表和檢視表上的作業。  
  
-   類型的資料行 BLOB、 CLOB、 和 NCLOB 配接器，可讓用戶端讀取，以及更新的資料。 配接器會公開 Read_\<LOBColName > 和 Update_\<LOBColName > 作業來讀取和更新資料，其中\<LOBColName > 是大型的資料類型資料行的名稱。 如果沒有與單一介面資料表中的大型資料類型的多個資料行，配接器會公開為許多的讀取和更新該介面資料表的作業。  
  
-   型別 BFILE 資料行，配接器用戶端可以只讀取資料。 配接器會公開 Read_\<LOBColName > BFILE 類型的資料行中讀取資料的作業。 如果沒有與單一介面資料表中的大型資料類型的多個資料行，配接器會公開為許多讀取介面資料表的作業。  
  
 如需有關這些作業的詳細資訊，請參閱[介面資料表、 介面檢視、 資料表和檢視表，包含 LOB 資料的作業](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md)。 如需執行這些作業的訊息結構描述資訊，請參閱[特殊 LOB 作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-special-lob-operations1.md)。  
  
## <a name="how-to-perform-operations-on-columns-with-large-data-types"></a>如何在大型資料類型的資料行上執行作業  
 執行 Oracle E-business suite 作業使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[建立 Oracle E-business Suite 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)。 若要執行 Oracle E-business Suite 包含大型的資料類型的介面資料表和檢視介面上的作業，這些工作包括：  
  
1.  建立 BizTalk 專案，並產生作業的結構描述 (Read_\<LOBColName > 或 Update_\<LOBColName >) 您想要在資料表或檢視表上叫用。  
  
2.  建立傳送和接收訊息，從 Oracle E-business Suite 的 BizTalk 專案中的訊息。  
  
3.  建立協調流程叫用的介面資料表或檢視上的作業。  
  
4.  建置和部署 BizTalk 專案。  
  
5.  設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
6.  啟動 BizTalk 應用程式。  
  
 本主題提供執行這些工作的指示。  
  
## <a name="how-this-topic-demonstrates-reading-and-writing-data-into-columns-of-large-data-types"></a>本主題示範如何讀取和寫入資料到大型資料類型的資料行  
 為了示範讀取和寫入資料到大型資料類型的資料行，本主題會提供指示來建立的協調流程，會執行下列作業：  
  
-   更新 （的 BLOB 資料類型） 客戶資料表的 PHOTO 資料行。  
  
-   讀取更新記錄照片資料行的值。  
  
 此協調流程被設計您只提供在執行階段更新作業的要求訊息的方式。 在作業中，會在建構讀取作業的訊息。  
  
> [!NOTE]
>  本主題中的協調流程會讀取，CUSTOMER 資料表，也就是基底資料庫資料表的更新資料來建立執行範例所提供的指令碼。 本主題，以執行讀取或更新任何介面資料表或介面檢視上的作業中所述，您必須執行類似的程序。  
  
## <a name="generating-schema"></a>產生結構描述  
 本主題示範如何執行基本的讀取和更新作業相片 （BLOB 資料類型資料行） CUSTOMER 資料表中。 此資料表會建立執行範例所提供的指令碼。  
  
 若要示範如何讀取和寫入資料到大型資料類型的資料行，如產生結構描述**Update_PHOTO**和**Read_PHOTO** CUSTOMER 資料表的作業。 您必須建立 BizTalk 專案，並使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生結構描述。 請參閱[擷取 Oracle E-business Suite 作業在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)如需有關如何產生結構描述。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。 訊息通常是為其型別由對應的結構描述所定義的變數。 您現在必須建立訊息的協調流程，並將它們連結至您在上一個步驟中產生的結構描述。  
  
 在此協調流程中，您必須建立四個訊息，設定一個接收回應**Update_PHOTO**設定作業和其他接收回應**Read_PHOTO**作業。  
  
#### <a name="to-create-messages-and-link-to-schema"></a>建立訊息，以及連結至結構描述  
  
1.  BizTalk 專案中新增協調流程。 從 方案總管 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下 **新項目**。 輸入 BizTalk 協調流程的名稱，然後按一下**新增**。  
  
2.  如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。 若要這樣做，請按一下**檢視**，指向 **其他視窗**，然後按一下 **協調流程檢視**。  
  
3.  在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。  
  
4.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  
  
5.  在**屬性**窗格**Message_1**，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|輸入 `UpdateMessage`|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*LOBOperations.OracleEBSBinding.Update_PHOTO*LOBOperations 所在的 BizTalk 專案的名稱。 OracleEBSBindingSchema 是叫用所產生的結構描述**Update_PHOTO** CUSTOMER 資料表上的作業。|  
  
6.  重複步驟 3 以建立三個新的訊息。 在**屬性**窗格新訊息中，執行下列動作：  
  
    |若要設定識別項|若要設定訊息類型|  
    |-----------------------|-------------------------|  
    |UpdateResponse|*LOBOperations.OracleEBSBinding.Update_PHOTOResponse*|  
    |ReadMessage|*LOBOperations.OracleEBSBinding1.Read_PHOTO*|  
    |ReadResponse|*LOBOperations.OracleEBSBinding1.Read_PHOTOResponse*|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 在此協調流程中，配接器會接收要求訊息來執行客戶資料表 Update_PHOTO 運算。 檔案位置接收通知訊息。 配接器會取用這個訊息，並將它傳遞到 Oracle 資料庫。 從 Oracle 資料庫的回應會儲存在另一個位置。 一旦收到回應時，協調流程會建構要叫用 Read_PHOTO 作業，它會讀取 Update_PHOTO 作業更新將 PHOTO 資料值的訊息。 在相同的檔案位置也收到這個訊息的回應。  
  
 因此，您的協調流程必須包含下列各項：  
  
-   FILE 接收埠，卸除的要求訊息**Update_PHOTO**作業。  
  
-   雙向 Wcf-custom 或 Wcf-oracleebs 傳送埠以傳送訊息至執行**Update_PHOTO**作業。  
  
-   雙向 Wcf-custom 或 Wcf-oracleebs 傳送埠以傳送訊息至執行**Read_PHOTO**作業。 您也可以執行兩者**Read_PHOTO**和**Update_PHOTO**使用相同的 Wcf-custom 或 Wcf-oracleebs 傳送埠。 本主題中，您將這兩個作業使用單一傳送埠。  
  
-   A**建構訊息**圖形來建構在協調流程中的訊息。  
  
-   檔案傳送埠以將儲存的回應訊息**Update_PHOTO**和**Read_PHOTO**作業。  
  
-   接收和傳送圖形。  
  
 範例協調流程如下。  
  
 ![處理大型資料類型資料行的協調流程](../../adapters-and-accelerators/adapter-oracle-ebs/media/1976ab27-94c3-4039-a1ca-8790e8897ad5.gif "1976ab27-94c3-4039-a1ca-8790e8897ad5")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息圖形指定下列屬性。 圖形資料行中所列的名稱是訊息 圖形的名稱，為顯示在剛才提及的協調流程中。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveUpdateMessage|Receive|-設定**名稱**至*ReceiveUpdateMessage*<br />-設定**啟動**至*，則為 True*|  
|SendUpdateMessage|Send|-設定**名稱**至*SendUpdateMessage*|  
|ReceiveUpdateResponse|Receive|-設定**名稱**至*ReceiveUpdateResponse*|  
|SendUpdateResponse|Receive|-設定**名稱**至*SendUpdateResponse*|  
|SendReadMessage|Send|-設定**名稱**至*SendReadMessage*|  
|ReceiveReadResponse|Receive|-設定**名稱**至*ReceiveReadResponse*|  
|SaveReadResponse|Send|-設定**名稱**至*SaveReadResponse*|  
  
### <a name="adding-construct-message-shape"></a>新增 建構訊息圖形  
 您可以使用**建構訊息**產生要求訊息的協調流程內執行的圖形**Read_PHOTO**作業。 若要這樣做，您必須新增**建構訊息**圖形，並在其中**訊息指派**圖形至協調流程。 例如，**訊息指派**圖形叫用會產生一個訊息傳送給 Oracle E-business Suite 來執行的程式碼**Read_PHOTO**作業。 **訊息指派**圖形也會設定要傳送給 Oracle E-business Suite 訊息的動作。  
  
 對於 「 建構訊息 」 圖形，設定**建構訊息**屬性**ReadMessage**。  
  
 產生回應的程式碼可能是您的 BizTalk 專案相同的 Visual Studio 方案的一部分。 產生回應訊息的範例程式碼看起來像這樣。  
  
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
  
 針對上述的程式碼摘錄無法產生要求訊息中，您必須擁有 XML 要求訊息 (如**Read_PHOTO**操作) 中所指定的位置`XmlFileLocation`變數。  
  
> [!NOTE]
>  建置專案之後，會建立 MessageCreator.dll 專案目錄中。 您必須將此 DLL 加入全域組件快取 (GAC)。 此外，您必須加入 MessageCreator.dll 當做 BizTalk 專案中的參考。  
  
 加入下列運算式來叫用此程式碼從**訊息指派**圖形，並設定訊息的動作。 若要新增運算式，請按兩下**訊息指派**圖形以開啟 運算式編輯器。  
  
```  
ReadMessage = MessageCreator.MessageCreator.XMLMessageCreator();  
ReadMessage(WCF.Action) = "Tables/ReadLOB/SCOTT/CUSTOMER/PHOTO ";  
```  
  
### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠指定下列屬性。 連接埠資料行中所列的名稱是連接埠的名稱，為顯示協調流程中。  
  
|通訊埠|屬性|  
|----------|----------------|  
|MessageIn|-設定**識別碼**至*MessageIn*<br />-設定**類型**至*MessageInType*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*接收*|  
|LOBPort|-設定**識別碼**至*LOBPort*<br />-設定**類型**至*LOBPortType*<br />-設定**通訊模式**至*要求-回應*<br />-設定**通訊方向**至*傳送接收*<br />建立作業*Read_LOB*。 這項作業的訊息用於讀取大型資料類型資料行的值。<br />建立作業*Update_LOB*。 這項作業的訊息用於更新大型資料類型資料行中的值。|  
|ResponseOut|-設定**識別碼**至*ResponseOut*<br />-設定**類型**至*ResponseOutType*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*傳送*<br />建立作業*Read_LOB*。 這項作業的訊息用於讀取大型資料類型資料行的值。<br />建立作業*Update_LOB*。 這項作業的訊息用於更新大型資料類型資料行中的值。|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>指定動作圖形訊息並連接至連接埠  
 下表指定屬性和其值，您應該設定來指定動作圖形的訊息，以及連結至連接埠的訊息。 圖形資料行中所列的名稱是 「 訊息 」 圖形的名稱，為顯示在協調流程中先前所述。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveUpdateMessage|-設定**訊息**至*UpdateMessage*<br />-設定**作業**至*MessageIn.Update_LOB。要求*|  
|SendUpdateMessage|-設定**訊息**至*UpdateMessage*<br />-設定**作業**至*LOBPort.Update_LOB。要求*|  
|ReceiveUpdateResponse|-設定**訊息**至*UpdateResponse*<br />-設定**作業**至*LOBPort.Update_LOB。回應*|  
|SendUpdateResponse|-設定**訊息**至*UpdateResponse*<br />-設定**作業**至*ResponseOut.Update_LOB。要求*|  
|SendReadMessage|-設定**訊息**至*ReadMessage*<br />-設定**作業**至*LOBPort.Read_LOB。要求*|  
|ReceiveReadResponse|-設定**訊息**至*ReadResponse*<br />-設定**作業**至*LOBPort.Read_LOB。回應*|  
|SendReadResponse|-設定**訊息**至*ReadResponse*<br />-設定**作業**至*ResponseOut.Read_LOB。要求*|  
  
 您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。  
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 在 [協調流程] 窗格中您已部署的 BizTalk 專案後，會列出您稍早建立的協調流程[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。 如需逐步解說，請參閱[逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。
  
 設定應用程式包括：  
  
-   選取應用程式的主機。  
  
-   對應至實體連接埠在協調流程中建立的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 此協調流程中，您必須：  
  
    -   定義位置上的硬碟和對應的檔案連接埠，您將在此置放要求訊息。 BizTalk 協調流程會使用要求訊息，並將它傳送給 Oracle 資料庫。  
  
    -   定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含從 Oracle 資料庫回應的回應訊息。  
  
    -   定義實體 Wcf-custom 或 Wcf-oracleebs 傳送埠將訊息傳送至 Oracle 資料庫。 您也必須在傳送埠中指定的動作。 如需如何建立連接埠相關資訊，請參閱[手動設定的實體連接埠的繫結至 Oracle E-business 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)。 您必須考量下列事項時設定 Wcf-custom 或 Wcf-oracleebs 傳送埠。  
  
        -   `Update_<LOBColName>`必須執行作業，因為交易的一部分。 若要確保這點， **UseAmbientTransaction**繫結屬性必須設定為**True**。  
  
        -   因為 Wcf-oracleebs 的 WCF 自訂傳送連接埠傳送和接收符合一個以上的結構描述的訊息，執行兩項作業，您必須設定這兩個作業的動態動作。 如需動作的詳細資訊，請參閱[for Oracle E-business Suite 中設定 SOAP 動作](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-soap-action-for-oracle-e-business-suite.md)。 此協調流程，此動作應該如下所示設定：  
  
            ```  
            \<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
              <Operation Name="Update_LOB" Action="Tables/UpdateBlob/SCOTT/CUSTOMER/PHOTO" />  
              <Operation Name="Read_LOB" Action="Tables/ReadLOB/SCOTT/CUSTOMER/PHOTO" />  
            </BtsActionMapping>  
            ```  
  
            > [!IMPORTANT]
            >  請注意，動態動作中的作業名稱必須與您建立 BizTalk 協調流程時，邏輯連接埠指定的作業名稱相同。  
  
        > [!NOTE]
        >  您也必須設定應用程式內容的介面資料表或檢視介面上執行作業。 如需有關配接器支援設定的應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。 指定的繫結屬性，或設定訊息內容屬性所公開，您可以設定應用程式內容[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 如需有關如何設定繫結屬性的指示，請參閱[for Oracle E-business Suite 中設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md)。 如需有關如何設定應用程式內容使用訊息內容屬性的指示，請參閱[Oracle E-business Suite 中設定應用程式內容使用訊息內容屬性](../../adapters-and-accelerators/adapter-oracle-ebs/configure-application-context-using-message-context-properties-in-oracle-ebs.md)。  
  
        > [!NOTE]
        >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠的設定動作的相關資訊的繫結檔案。 您可以從這個繫結檔案匯[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 （適用於傳出呼叫） 的傳送埠或接收埠 （用於進行傳入呼叫時）。 如需詳細資訊，請參閱[設定實體連接埠繫結使用連接埠繫結檔案至 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md)。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 開始之前，BizTalk 協調流程，請確定要叫用 XML 要求**Read_PHOTO**作業將會位於 C:\TestLocation\MessageIn。 要求 XML 必須如下所示：  
  
```  
<Read_PHOTO xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/SCOTT/CUSTOMER">  
  <FILTER>WHERE NAME='Mindy Martin'</FILTER>  
</Read_PHOTO>  
```  
  
> [!NOTE]
>  要求訊息篩選器上具有特定名稱因為中的要求訊息**Update_PHOTO**相片的資料行的值的作業會更新相同的名稱。 因此，在讀取的作業會讀取相同的值，您將使用更新作業。  
  
 您現在必須啟動 BizTalk 應用程式進行讀取和寫入從 Oracle 資料庫的大型資料類型的值。 如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。  
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   Wcf-custom 或 Wcf-oracleebs 傳送埠將訊息傳送至 Oracle 資料庫執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 啟動應用程式，您必須卸除後檔案的要求訊息的接收位置。 要求訊息的結構描述必須符合的結構描述**Update_PHOTO**您先前產生的作業。 比方說，更新客戶資料表的 PHOTO 欄的要求訊息，如下所示：  
  
```  
<Update_PHOTO xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/SCOTT/CUSTOMER">  
  <FILTER>WHERE Name='Mindy Martin'</FILTER>  
  <DATA>U2FtcGxlIERhdGE=</DATA>  
</Update_PHOTO>  
```  
  
> [!NOTE]
>  當更新 BLOB 資料行，資料元素必須永遠包含 base64 編碼值。 如需 CLOB 和 NCLOB，資料元素可以有字串值。  
  
 先前的要求訊息更新 PHOTO 欄的記錄符合 WHERE 子句中的值。 如需有關使用大型資料類型上執行作業的要求訊息結構描述在大型的資料類型上作業的訊息結構描述請參閱 < [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  
  
 協調流程取用訊息，並將它傳送到 Oracle 資料庫。 從 Oracle 資料庫的回應會儲存在其他的協調流程中定義的檔案位置。 例如，從先前的要求訊息的 Oracle 資料庫回應如下所示：  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<Update_PHOTOResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/SCOTT/CUSTOMER" />  
```  
  
 現在的協調流程會建構的要求訊息**Read_PHOTO**藉由在 C:\TestLocation\MessageIn 使用可用的要求訊息的作業。 要求訊息傳送至 Oracle 資料庫，而回應則儲存在相同的檔案位置。 相片的資料行上的讀取作業的回應如下所示：  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<Read_PHOTOResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/SCOTT/CUSTOMER">  
  <Read_PHOTOResult>U2FtcGxlIERhdGE=</Read_PHOTOResult>  
</Read_PHOTOResponse>  
```  
  
> [!NOTE]
>  請注意，回應會包含您傳入相片資料行的相同值**Update_PHOTO**作業。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。 一旦產生繫結檔案時，可以組態設定匯入檔案，使您不需要建立項目，例如傳送埠和接收相同的協調流程連接埠。 如需繫結檔案的詳細資訊，請參閱[重複使用配接器繫結與 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md)。  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式使用 Oracle E-business Suite 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)