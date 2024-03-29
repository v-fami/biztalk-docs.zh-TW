---
title: 叫用 Oracle E-business Suite 中的並行程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85c55a35-bee4-4b50-8b00-e4198ad4c2af
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bdd5b182267009a6b2591ffb06f5ba75db1b7e3e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969687"
---
# <a name="invoke-concurrent-programs-in-oracle-e-business-suite"></a>叫用 Oracle E-business Suite 中的並行程式
Oracle E-business Suite 會公開您可以執行特定作業在 Oracle 應用程式上的執行的並行處理程式。 每個 Oracle 應用程式有一組標準的並行程式 （可在所有作業，都是相同） 和 Oracle 應用程式專屬特定並行程式。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開所有的並行程式做為配接器用戶端可以叫用的作業。 如需有關配接器如何支援同時執行的程式的詳細資訊，請參閱[並行程式的相關作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md)。 叫用同時執行的程式，訊息的 SOAP 結構的相關資訊，請參閱[並行程式的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-concurrent-programs.md)。  

> [!NOTE]
>  並行程式不會公開其中繼資料、 Oracle E-business 配接器會公開這些並行程式的每個 100 的選擇性參數。 已成功叫用這些並行程式，使用者必須請參閱 Oracle E-business Suite 文件，找出需要值，並行處理程式的參數，且然後將其指定。 這類並行程式的範例**日誌匯入**(實際名稱： **GLLEZL**) 中**一般分類帳**應用程式。  

## <a name="prerequisites"></a>必要條件  
 您必須先完成中的步驟[要建立 Oracle E-business Suite 應用程式的必要條件](../../adapters-and-accelerators/adapter-oracle-ebs/prerequisites-to-create-oracle-e-business-suite-applications.md)。

## <a name="how-to-invoke-concurrent-programs-in-oracle-applications"></a>如何叫用 Oracle 應用程式中的並行程式  
 執行的作業上使用 Oracle E-business Suite[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及中所述的程序性工作[建立 Oracle E-business Suite 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)。 要叫用並行處理程式，這些工作如下：  

- 建立 BizTalk 專案，並產生您想要叫用的並行程式的結構描述。  

- 在 Oracle E-business Suite 中傳送和接收訊息的 BizTalk 專案中的訊息。  

- 建立協調流程叫用並行處理程式。  

- 建置和部署 BizTalk 專案。  

- 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  

- 啟動 BizTalk 應用程式。  

  本主題提供執行這些工作的指示。  

## <a name="generating-schema"></a>產生結構描述  
 本主題示範如何叫用**客戶介面**並行處理程式，從**應收帳款**應用程式。 此應用程式可以使用預設的 Oracle E-business Suite 應用程式。 這個並行程式傳回的要求識別碼。 若要檢查的並行處理程式狀態，我們要執行**Get_Status**藉由傳遞的要求識別碼的並行處理程式收到的回應**客戶介面**並行處理程式。  

 本主題中，產生結構描述同時**客戶介面**並**Get_Status**同時執行的程式。 如需如何產生結構描述的詳細資訊，請參閱[擷取 Oracle E-business Suite 作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)。  

## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是一個變數，要為其類型會定義對應的結構。 現在，您必須建立協調流程的訊息，並將它們連結至您在上一個步驟中產生的結構描述。  

 在此協調流程中，您必須建立四個訊息-一個接收回應設定才能叫用**客戶介面**並行處理程式以及其他接收-回應的設定才能叫用**Get_Status**並行處理程式。  

#### <a name="to-create-messages-and-link-to-schema"></a>若要建立訊息，並連結至結構描述  

1. BizTalk 專案中新增協調流程。 從 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下**新項目**。 輸入 BizTalk 協調流程的名稱，然後按一下**新增**。  

2. 如果它尚未開啟，請開啟 BizTalk 專案，[協調流程檢視] 視窗。 若要這樣做，請按一下**檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  

3. 在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  

4. 以滑鼠右鍵按一下新建立的訊息，然後按**屬性 視窗**。  

5. 在 [**屬性**] 窗格**Message_1**，執行下列動作：  


   |   使用   |                                                                                                                                                                                                                                                                                           以進行此動作                                                                                                                                                                                                                                                                                           |
   |--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |  識別碼  |                                                                                                                                                                                                                                                                                         輸入 `Request`                                                                                                                                                                                                                                                                                         |
   | 訊息類型 | 從下拉式清單中，依序展開**結構描述**，然後選取*ConcurrentProgram.OracleEBSBindingSchema.RACUST*ConcurrentProgram 所在的 BizTalk 專案的名稱。 OracleEBSBindingSchema 是叫用所產生的結構描述**客戶介面**並行處理程式。 **注意︰** RACUST 會的實際名稱**客戶介面**並行處理程式。 雖然[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]顯示的易記名稱 (**客戶介面**)，該結構描述包含並行處理程式的實際名稱。 |


6. 重複步驟 3 以建立三個新的訊息。 在 **屬性**窗格中的新訊息，執行下列動作：  

   |若要設定識別項|若要設定訊息類型|  
   |-----------------------|-------------------------|  
   |回應|*ConcurrentProgram.OracleEBSBindingSchema.RACUSTResponse*|  
   |Get_StatusRequest|*ConcurrentProgram.OracleEBSBindingSchema1.GetStatusForConcurrentProgram*|  
   |Get_StatusResponse|*ConcurrentProgram.OracleEBSBindingSchema1.GetStatusForConcurrentProgramResponse*|  

## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]叫用同時執行 Oracle E-business Suite 中的程式。 在此協調流程中，您將會卸除在要求訊息定義的接收位置。 協調流程會取用這個訊息，並將其傳遞至叫用 Oracle E-business Suite**客戶介面**並行處理程式。 並行處理程式的回應從 Oracle 接收，且會儲存在另一個位置。 回應訊息含有要求識別碼。 協調流程包含**建構的訊息**圖形以從回應中擷取的要求識別碼，並建構訊息的結構描述符合**Get_Status**並行處理程式。 要叫用的訊息**Get_Status**並行處理程式會傳送至 Oracle E-business Suite，以做為參數的要求識別碼。 您必須包含傳送和接收圖形、 訊息建構 圖形，以及將訊息傳送至 Oracle，並接收回應的連接埠。  

 通常**客戶介面**並行處理程式將需要一些時間才能執行，您需要在執行之前等待**Get_Status**並行。 您可以新增來自動化這**延遲**圖形。  

 範例協調流程如下所示：  

 ![叫用同時執行的程式協調流程](../../adapters-and-accelerators/adapter-oracle-ebs/media/2a02e9d8-8ea8-4898-8d05-c060761f4feb.gif "2a02e9d8-8ea8-4898-8d05-c060761f4feb")  

### <a name="adding-message-shapes"></a>新增訊息圖形  
 針對每個訊息 圖形中指定下列屬性。 所列的名稱**圖形**資料行對應至訊息的圖形，上述協調流程中所示。  

|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveMessage|Receive|-設定**名稱**到*ReceiveMessage*<br />-設定**啟用**到 *，則為 True*|  
|SendMessage|Send|-設定**名稱**到*SendMessage*|  
|ReceiveResponse|Receive|-設定**名稱**到*ReceiveResponse*<br />-設定**啟用**到*False*|  
|SendResponse|Send|-設定**名稱**到*SendResponse*|  
|SendGetStatus|Send|-設定**名稱**到*SendGetStatus*|  
|ReceiveStatusResponse|Receive|-設定**名稱**到*ReceiveStatusResponse*<br />-設定**啟用**到*False*|  
|SaveStatusResponse|Send|-設定**名稱**到*SaveStatusResponse*|  

### <a name="adding-a-delay-shape"></a>新增 「 延遲 」 圖形  
 如果您想要等待叫用的協調流程**客戶介面**並**Get_Status**同時執行的程式，您必須新增**延遲**圖形至協調流程。 您必須新增**延遲**圖形 協調流程將複製的回應後**客戶介面**並行處理程式的檔案傳送埠。 因此，您必須新增**延遲**圖形之後**SendResponse**圖形。  

 內**延遲**圖形，您可以指定時間間隔，協調流程必須等候之前加入下列程式碼的運算式編輯器**延遲**圖形：  

```  
new System.TimeSpan(0,2,0)  
```  

 藉由新增此程式碼，協調流程會等待兩分鐘後再繼續。 如需有關如何設定**延遲**圖形，請參閱[如何設定延遲圖形](../../core/how-to-configure-the-delay-shape.md)。  

### <a name="adding-the-construct-message-shape"></a>新增 建構訊息圖形  
 從 Oracle E-business Suite for 回應**客戶介面**並行處理程式包含要求識別碼。 若要取得的並行處理程式狀態，您必須傳遞相同的要求 ID，做為參數**Get_Status**並行處理程式。 若要這樣做，請在 協調流程中，您必須包含**建構的訊息**圖形，並在其中**訊息指派**圖形。 目的**建構訊息**圖形是︰  

- 若要從所收到的回應中擷取的要求識別碼**客戶介面**並行處理程式。  

- 若要建構訊息的訊息結構描述符合**Get_Status**並行處理程式。  

  針對**建構的訊息**圖形中，設定**建構的訊息**屬性設**Get_StatusRequest**。  

  針對**訊息指派**圖形中新增下面。 之前加入程式碼，您必須具備：  

```  
XmlDoc = new System.Xml.XmlDocument();  
XmlDoc.LoadXml("<GetStatusForConcurrentProgram xmlns='http://schemas.microsoft.com/OracleEBS/2008/05/ConcurrentPrograms/AR'><RequestId /></GetStatusForConcurrentProgram>");  
Get_StatusRequest = XmlDoc;  
Get_StatusRequest.RequestId = xpath(Response,"string(/*[local-name()='RACUSTResponse']/*[local-name()='RACUSTResult']/text())");  
```  

### <a name="adding-ports"></a>新增連接埠  
 若要設定的連接埠，您可以指定下表列出每個邏輯連接埠的屬性。 所列的名稱*連接埠*資料行對應到協調流程中所顯示的通訊埠的名稱。  

|通訊埠|屬性|  
|----------|----------------|  
|MessageIn|-設定**識別碼**到*MessageIn*<br />-設定**型別**到*MessageInType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*接收*|  
|LOBPort|-設定**識別碼**到*LOBPort*<br />-設定**型別**到*LOBPortType*<br />-設定**通訊模式**到*要求-回應*<br />-設定**通訊方向**到*傳送接收*|  
|ResponseOut|-設定**識別碼**到*ResponseOut*<br />-設定**型別**到*ResponseOutType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*傳送*<br />-建立作業*Cust_Interface*。 此作業可用於**客戶介面**並行處理程式。<br />-建立作業*Get_Status*。 此作業可用於**Get_Status**並行處理程式。|  
|LOBPort_GetStatus|-設定**識別碼**到*LOBPort_GetStatus*<br />-設定**型別**到*LOBPort_GetStatusType*<br />-設定**通訊模式**到*要求-回應*<br />-設定**通訊方向**到*傳送接收*|  

### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>為動作圖形指定訊息，並連接到連接埠  
 下表指定的屬性值來指定動作圖形，並將它們連結至連接埠的訊息。 所列的名稱**圖形**協調流程圖中所示，資料行對應至訊息 圖形的名稱。  

 您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。  

 您必須立即建置 BizTalk 方案，並再將它部署到 BizTalk Server。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。  

|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveMessage|-設定**訊息**到*要求*<br />-設定**作業**到*MessageIn.Cust_Interface.Request*|  
|SendMessage|-設定**訊息**到*要求*<br />-設定**作業**到*LOBport.Cust_Interface.Request*|  
|ReceiveResponse|-設定**訊息**到*回應*<br />-設定**作業**到*LOBport.Cust_Interface.Response*|  
|SendResponse|-設定**訊息**到*回應*<br />-設定**作業**到*ResponseOut.Cust_Interface.Request*|  
|SendGetStatus|-設定**訊息**到*Get_StatusRequest*<br />-設定**作業**到*LOBPort_GetStatus.Get_Status.Request*|  
|ReceiveStatusResponse|-設定**訊息**到*Get_StatusResponse*<br />-設定**作業**到*LOBPort_GetStatus.Get_Status.Response*|  
|SaveStatusResponse|-設定**訊息**到*Get_StatusResponse*<br />-設定**作業**到*ResponseOut.Get_Status.Request*|  

 您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。  

 您必須立即建置 BizTalk 方案，並再將它部署到 BizTalk Server。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。  

## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在下**協調流程** 窗格中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。 如需逐步解說，請參閱 <<c0> [ 逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。  

 設定應用程式包含：  

- 選取應用程式主機。  

- 對應至實體連接埠在協調流程中建立的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 此協調流程中，您必須：  

  - 定義位置上的硬碟和對應的檔案連接埠，您將會卸除要求訊息。 BizTalk 協調流程將會取用的要求訊息，並將它傳送給 Oracle E-business Suite。  

  - 定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含來自 Oracle E-business Suite 的回應的回應訊息。  

  - 定義兩個實體 Wcf-custom 或 Wcf-oracleebs 傳送埠，一個用來將訊息傳送至執行的 Oracle E-business Suite**客戶介面**並行處理程式，另一個用於執行**Get_Status**並行處理程式。 您也必須在傳送埠中指定的動作。 如需有關如何建立連接埠的資訊，請參閱 <<c0> [ 手動設定實體連接埠繫結來 Oracle E-business 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)。  

     若要叫用同時執行的程式使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您必須設定正確的應用程式內容，叫用作業。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]提供特定的繫結屬性，以指定應用程式內容的任何作業。 您必須叫用同時執行的程式使用 Wcf-custom 或 Wcf-oracleebs 連接埠上設定這些繫結屬性。  

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
 您必須啟動 BizTalk 應用程式，然後再叫用同時執行的程式。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。  

 在這個階段，請確定：  

-   FILE 接收埠以接收要求訊息的協調流程正在執行。  

-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  

-   Wcf-oracleebs 的 Wcf-custom 傳送埠以叫用**客戶介面**並行處理程式正在執行。  

-   Wcf-oracleebs 的 Wcf-custom 傳送埠以叫用**Get_Status**並行處理程式正在執行。  

-   BizTalk 協調流程的作業正在執行。  

## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須卸除要求訊息來叫用的結構描述符合**客戶介面**並行處理程式。 例如，要求訊息來叫用**客戶介面**並行處理程式為：  

```  
<RACUST xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/ConcurrentPrograms/AR">  
  <Description>Customer Interface Program</Description>  
  <StartTime></StartTime>  
  <CREATE_RECIPROCAL_CUSTOMER>Yes</CREATE_RECIPROCAL_CUSTOMER>  
  <ORG_ID>203</ORG_ID>  
</RACUST>  
```  

> [!NOTE]
>  叫用並行處理程式的要求訊息需要 SetOptions、 SetPrintOptions，等 SetRepeatOptions 一些選用參數。 此處提供的要求訊息不包含這些選擇性的參數。 如需完整的要求訊息，包括選擇性的參數，請參閱[並行程式的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-concurrent-programs.md)。  

 協調流程會取用訊息、 將它傳遞到 Oracle E-business Suite 中，並接收回應。 回應訊息會儲存在其他協調流程中指定的檔案位置。 客戶介面並行處理程式的回應如下所示：  

```  
<?xml version="1.0" encoding="utf-8"?>  
<RACUSTResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/ConcurrentPrograms/AR">  
  <RACUSTResult>2794708</RACUSTResult>  
</RACUSTResponse>  
```  

 Oracle E-business Suite 的回應包含要求識別碼。 協調流程從回應訊息中擷取的要求識別碼、 會建構要叫用訊息**Get_Status**並行處理程式，並將它傳遞給執行 Oracle E-business Suite **Get_Status**並行處理程式。 Th 收到回應後**Get_Status**並行處理程式，它會複製到相同的檔案位置，做為第一個回應。 回應**Get_Status**並行處理程式如下所示：  

```  
<?xml version="1.0" encoding="utf-8" ?>   
<GetStatusForConcurrentProgramResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/ConcurrentPrograms/AR">  
  <GetStatusForConcurrentProgramResult>true</GetStatusForConcurrentProgramResult>   
  <Phase>Pending</Phase>   
  <Status>Standby</Status>   
  <DevPhase>PENDING</DevPhase>   
  <DevStatus>STANDBY</DevStatus>   
  <Message>null</Message>   
</GetStatusForConcurrentProgramResponse>  
```  

## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 之後產生繫結檔案，您可以從檔案匯入的組態設定，使您不需要建立項目這類傳送埠和接收相同的協調流程的連接埠。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用與 Oracle E-business Suite 配接器繫結](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md)。  

## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式使用 Oracle E-business Suite 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)