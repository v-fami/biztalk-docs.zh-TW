---
title: 挑選清單欄位使用 BizTalk Server 和 Siebel 配接器具有的商務元件執行作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- how to, perform operations with picklist fields by using BizTalk Server
- business components, performing operations with picklist fields by using BizTalk Server
ms.assetid: b62d32fa-903a-442b-951b-2343ef719bd0
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c722caaad6e1474ac80a14843171550aa53b9d77
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986079"
---
# <a name="run-operations-on-business-components-with-picklist-fields-using-biztalk-server-and-the-siebel-adapter"></a>挑選清單欄位使用 BizTalk Server 和 Siebel 配接器具有的商務元件執行作業
Siebel 挑選清單欄位型別構成的可能值集合從用戶端可以指定要傳遞到 Siebel 系統的特定值。 換句話說，挑選清單欄位包含欄位的接受值的清單。 如需有關挑選清單和其類型的詳細資訊，請參閱 Siebel 文件。 如需有關如何[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]支援作業對商務元件與挑選清單欄位，請參閱[在 Siebel 商務元件作業](../../adapters-and-accelerators/adapter-siebel/operations-on-business-components-in-siebel.md)。  
  
 當您產生包含靜態繫結的挑選清單欄位 （挑選清單的類型） 的商務元件的中繼資料時，並也會將接受的挑選清單值發佈中繼資料的一部分。 如果您要插入值的挑選清單欄位，您必須指定發行的中繼資料中的值。  
  
## <a name="how-to-perform-operations-on-business-components-with-picklist-fields"></a>如何執行在挑選清單欄位的商務元件上的作業？  
 使用 Siebel 系統上執行運算[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及中所述的程序性工作[來建立與 Siebel 配接器的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)。 
 
 若要完成與挑選清單欄位的商務元件上的作業，這些工作如下：  
  
1. 建立 BizTalk 專案，並產生包含挑選清單欄位的商務元件上執行作業的結構描述。  
  
2. 建立傳送和接收來自 Siebel 系統的訊息的 BizTalk 專案中的訊息。  
  
3. 建立 Siebel 系統中叫用作業的協調流程。  
  
4. 建置和部署 BizTalk 專案。  
  
5. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
6. 啟動 BizTalk 應用程式。  
  
   本主題提供執行這些工作的指示。  
  
## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 ，SiebelPicklist，根據本主題也提供了範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱 < [Siebel 配接器的範例](../../adapters-and-accelerators/adapter-siebel/samples-for-the-siebel-adapter.md)。  
  
## <a name="generating-schema"></a>產生結構描述  
 本主題中，我們也會在示範如何使用挑選清單欄位的商務元件上叫用作業產生結構描述**插入**作業**帳戶**商務元件。 **帳號**商務元件有靜態的挑選清單中，*問卷類型*。  
  
 請參閱[擷取 Siebel 作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)如需有關如何產生結構描述。  
  
 當您產生的插入作業的中繼資料**帳戶**商務元件，取得包含挑選清單欄位，以及其可能值的另一個.xsd 檔案。 請注意，.xsd 僅能包含值的靜態的挑選清單，包括*問卷類型*。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是一個變數，要為其類型會定義對應的結構。 您必須連結您的第一個步驟中的訊息從產生的 BizTalk 專案的 [協調流程] 檢視的結構描述。  
  
 本主題中，您必須建立兩個訊息，一個用來將要求傳送至 Siebel 系統，另一個用於接收的回應。  
  
 執行下列步驟來建立訊息，並將它們連結至結構描述：  
  
#### <a name="to-create-messages-and-link-to-schema"></a>若要建立訊息，並連結至結構描述  
  
1.  開啟協調流程檢視 BizTalk 專案中，如果未開啟。 按一下 **檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  
  
2.  在 **協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  
  
3.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  
  
4.  在 [**屬性**] 窗格**Message_1**，執行下列動作：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|型別**要求**。|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*SiebelPicklist.SiebelBindingSchema.Insert*，其中*SiebelPicklist*是 BizTalk 專案的名稱。 *SiebelBindingSchema*會叫用所產生的結構描述*插入*上的作業*帳戶*商務元件。|  
  
5.  重複上述步驟來建立新的訊息。 在 **屬性**窗格中的新訊息，執行下列動作：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|型別**回應**。|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*SiebelPicklist.SiebelBindingSchema.InsertResponse*。|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行插入作業的挑選清單欄位的 Siebel 商務元件上。 在此協調流程中，卸除在要求訊息定義的接收位置。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]會取用這個訊息，並將它傳遞到 Siebel 系統。 來自 Siebel 系統的回應會儲存到另一個位置。 用於在 Siebel 商務元件上執行作業的一般協調流程會包含：  
  
- 傳送和接收圖形以將訊息傳送到 Siebel 並接收回應。  
  
- 單向接收埠以接收要求訊息傳送到 Siebel。  
  
- 雙向傳送埠以將要求訊息傳送到 Siebel 並接收回應。  
  
- 單向傳送埠以從 Siebel 的回應傳送到資料夾。  
  
  範例協調流程，如*插入*上的作業*帳戶*商務元件如下所示：  
  
  ![插入 Siebel 挑選清單值的協調流程](../../adapters-and-accelerators/adapter-siebel/media/c981fbf9-9a1f-40a5-9ccb-5e146589f2d3.gif "c981fbf9-9a1f-40a5-9ccb-5e146589f2d3")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息 圖形中指定下列屬性。 所列的名稱*圖形*資料行是訊息 圖形的名稱，上述協調流程中所示。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveXML|Receive|-設定**名稱**到*ReceiveXML*<br />-設定**啟用**到 *，則為 True*|  
|SendToLOB|Send|-設定**名稱**到*SendToLOB*|  
|ReceiveResponse|Receive|-設定**名稱**到*ReceiveResponse*<br />-設定**啟用**到*False*|  
|SendResponse|Send|-設定**名稱**到*SendResponse*|  
  
### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠中指定下列屬性。 所列的名稱*連接埠*資料行名稱就是連接埠在協調流程中所示。  
  
|通訊埠|屬性|  
|----------|----------------|  
|FileIn|-設定**識別碼**到*FileIn*<br />-設定**型別**到*FileInType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*接收*|  
|LOBPort|-設定**識別碼**到*LOBPort*<br />-設定**型別**到*LOBPortType*<br />-設定**通訊模式**到*要求-回應*<br />-設定**通訊方向**到*傳送接收*|  
|SaveResponse|-設定**識別碼**到*SaveResponse*<br />-設定**型別**到*SaveResponseType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*傳送*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>為動作圖形指定訊息，並連接到連接埠  
 下表指定之屬性和其值設為指定的動作圖形，並將它們連結至連接埠的訊息。 所列的名稱*圖形*資料行是訊息 圖形的名稱，上述協調流程中所示。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveXml|-設定**訊息**到*要求*<br />-設定**作業**到*FileIn.Picklist.Request*|  
|SendToLOB|-設定**訊息**到*要求*<br />-設定**作業**到*LOBPort.Picklist.Request*|  
|ReceiveResponse|-設定**訊息**到*回應*<br />-設定**作業**到*LOBPort.Picklist.Response*|  
|SendResponse|-設定**訊息**到*回應*<br />-設定**作業**到*SaveResponse.Picklist.Request*|  
  
 您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並將其部署至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 建置協調流程如何](../../core/how-to-build-orchestrations.md)並[從 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。 
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在下**協調流程**在 BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需有關如何設定應用程式的詳細資訊，請參閱 <<c0> [ 如何建立應用程式](../../core/how-to-create-an-application.md)。  
  
 設定應用程式包含：  
  
- 選取應用程式主機。  
  
- 對應您在您在 BizTalk Server 管理主控台中的實體連接埠的協調流程中建立的連接埠。 此協調流程中，您必須：  
  
  - 定義位置上的硬碟和對應的檔案連接埠，您將會卸除要求訊息。 BizTalk 協調流程將會取用的要求訊息，並將它傳送至 Siebel 系統。  
  
  - 定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含來自 Siebel 系統的回應的回應訊息。  
  
  - 定義將訊息傳送至 Siebel 系統實體 Wcf-custom 或 Wcf-siebel 傳送埠。 您也必須在傳送埠中指定的動作。 如需有關如何建立連接埠的資訊，請參閱 <<c0> [ 手動設定 Siebel 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-siebel/manually-configure-a-physical-port-binding-to-the-siebel-adapter.md)。
  
    > [!NOTE]
    >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠設定動作的相關資訊的繫結檔案。 您可以從 BizTalk 管理主控台建立傳送埠 （適用於輸出的呼叫），以匯入此繫結檔案。 如需詳細資訊，請參閱 <<c0> [ 設定的實體連接埠繫結使用的連接埠繫結檔案至 siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-physical-port-binding-using-a-port-binding-file-to-siebel.md)。
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式來執行*插入*上的作業*帳戶*在 Siebel 商務元件。 如需有關啟動 BizTalk 應用程式的指示，請參閱[啟動 BizTalk 應用程式](../../core/how-to-start-and-stop-a-biztalk-application.md)或是[啟動協調流程](../../core/how-to-start-an-orchestration.md)。
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程正在執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   WCF 自訂] 或 [Wcf-siebel 傳送埠將訊息傳送至 Siebel 系統正在執行  
  
-   在執行作業的 BizTalk 協調流程  
  
## <a name="executing-the-operation"></a>執行作業  
 您必須先要求訊息卸除檔案接收位置。 要求訊息的結構描述必須符合您稍早在本主題中所產生的結構描述。 請參閱[商務元件作業的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md)取得的要求訊息的結構描述的詳細資訊。  
  
 若要插入至挑選清單欄位的值，請查看產生的結構描述，以判斷可接受的值清單的挑選清單。 請確認要求訊息具有項目插入至挑選清單欄位的值。 例如，要求訊息必須包含下列項目插入至值*問卷類型*挑選清單。  
  
 `<Survey_x0020_Type>1</Survey_x0020_Type>`  
  
 在這裡，"1"是種問卷挑選清單的可接受值。  
  
 範例要求訊息包含挑選清單的參數如下：  
  
```  
<Insert xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Operation">  
  <ArrayOfAccountInsertRecord>  
    <AccountInsertRecord xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects">  
      <Currency_x0020_Code>usd</Currency_x0020_Code>  
      <Current_x0020_Volume>9</Current_x0020_Volume>  
      <Customer_x0020_Account_x0020_Group>Sold-To Party</Customer_x0020_Account_x0020_Group>  
      <Location>Location_1</Location>  
      <Main_x0020_Phone_x0020_Number>4256543212</Main_x0020_Phone_x0020_Number>  
      <Name>Name_Surname</Name>  
      <Party_x0020_Name>test_party</Party_x0020_Name>  
      <Primary_x0020_Address_x0020_Id>1212 street</Primary_x0020_Address_x0020_Id>  
      <Survey_x0020_Type>1</Survey_x0020_Type>  
    </AccountInsertRecord>  
  </ArrayOfAccountInsertRecord>  
</Insert>  
```  
  
 協調流程會使用要求訊息，並將它傳遞至 Siebel 系統。 來自 Siebel 系統的回應會儲存在其他定義的協調流程一部分的檔案位置。  
  
> [!NOTE]
>  您也可以嘗試插入無效的值為挑選清單。 在此情況下，您必須取得`TargetSystemException`。  
  
## <a name="possible-exceptions"></a>可能的例外狀況  
 可能會遇到與使用的挑選清單欄位執行商務元件上的作業時的例外狀況的相關資訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 例外狀況和錯誤處理與 Siebel 配接器](../../adapters-and-accelerators/adapter-siebel/exceptions-and-error-handling-with-the-siebel-adapter.md)。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 之後產生的繫結檔案時，您可以匯入的組態設定從檔案，讓您不需要建立傳送埠、 接收連接埠、 相同的協調流程等。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用 Siebel 配接器中的配接器繫結](../../adapters-and-accelerators/adapter-siebel/reuse-adapter-bindings-in-the-siebel-adapter.md)。
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式使用 Siebel 配接器](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md)