---
title: "使用 MVG 欄位使用 BizTalk Server 和 Siebel 配接器執行商務元件上的作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c5db211-76a2-4c27-97f4-382302c722da
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f2e1f867ba4f7759afa67a271bc6523b93e9a67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="run-operations-on-business-components-with-mvg-fields-using-biztalk-server-and-the-siebel-adapter"></a>使用 MVG 欄位使用 BizTalk Server 和 Siebel 配接器執行商務元件上的作業
本節將提供包含多重值欄位的商務元件上執行操作的指示。 若要示範這類商務元件上的端對端作業，您必須執行：  
  
-   上層業務元件 INSERT 作業  
  
-   下層業務元件 INSERT 作業  
  
-   多重值之間的連結父和子商務元件關聯作業  
  
-   上層業務元件的記錄 Query_ [MVG_Child_Business_Comp] 作業  
  
 如需有關如何[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]支援作業在商務元件，請參閱[商務元件上的作業](../../adapters-and-accelerators/adapter-siebel/operations-on-business-components-in-siebel.md)。 執行這些作業，訊息的 SOAP 結構的詳細資訊，請參閱[商務元件操作的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md)。  
  
## <a name="how-to-perform-operations-on-a-business-component-with-multi-value-fields"></a>如何在使用多重值欄位的商務元件上執行作業？  
 使用 Siebel 系統上執行操作[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[建立 Siebel 應用程式的建置組塊](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)。 若要執行的商務元件上的作業，這些工作包括：  
  
1.  建立 BizTalk 專案，並產生您想要叫用商務元件上的所有作業的結構描述。 如先前所述，在多重值欄位的商務元件上執行作業您必須在父系和子系的商務元件上的 Insert 作業產生結構描述，關聯的多重值連結，父系和子系之間的作業商務元件和上層業務元件上的查詢作業。  
  
2.  建立傳送和接收來自 Siebel 系統訊息的 BizTalk 專案中的訊息。  
  
3.  建立協調流程叫用在 Siebel 系統的不同作業。  
  
4.  建置和部署 BizTalk 專案。  
  
5.  設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
6.  啟動 BizTalk 應用程式。  
  
 本主題提供執行這些工作的指示。  
  
## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 基礎的範例，MVLDemo，本主題也會提供[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱[Siebel 配接器的範例](../../adapters-and-accelerators/adapter-siebel/samples-for-the-siebel-adapter.md)。  
  
## <a name="generating-schema"></a>產生結構描述  
 本主題中，以示範如何建立關聯上層業務元件中，**帳戶**下層業務元件中，以**連絡人**，我們將會產生下列的結構描述：  
  
-   INSERT 作業**帳戶**商務元件。 請參閱[商務元件使用 BizTalk Server 和 Siebel 配接器上執行的作業](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-using-the-siebel-adapter-in-biztalk.md)。  
  
-   INSERT 作業**連絡人**商務元件。  
  
-   關聯的作業上**帳戶**商務元件。  
  
-   QUERY_CONTACT 作業**帳戶**商務元件。  
  
 請參閱[取得 Visual Studio 中的 Siebel 作業的中繼資料](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)如需有關如何產生結構描述。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。 訊息通常是為其型別由對應的結構描述所定義的變數。 您必須連結產生的結構描述您在第一個步驟中的訊息從 BizTalk 專案的協調流程檢視。  
  
 本主題中，您必須建立四組要求和回應訊息，一個用於您將在 Siebel 系統叫用每個作業。 每個集必須具有要求訊息和回應訊息。 例如，下列程序會提供指示來建立關聯的作業要求和回應訊息。 您必須執行類似的步驟來建立其他作業的訊息。  
  
 執行下列步驟來建立訊息，並將其連結至結構描述：  
  
### <a name="create-messages-and-link-to-schema"></a>建立訊息並連結到結構描述  
  
1.  開啟協調流程檢視 BizTalk 專案中，如果未開啟。 按一下**檢視**，指向 **其他視窗**，然後按一下**協調流程檢視**。  
  
2.  在**協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。  
  
3.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  
  
4.  在**屬性**窗格**Message_1**，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|型別**AccountAssociate_Request**。|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*MVLDemo.SiebelBindingSchema.Associate*，其中*MVLDemo*是您的 BizTalk 專案的名稱。 *SiebelBindingSchema*是叫用所產生的結構描述*關聯*作業*帳戶*商務元件。|  
  
5.  重複上述步驟，建立新的訊息。 在**屬性**窗格新訊息中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|型別**AccountAssociate_Response**。|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*MVLDemo.SiebelBindingSchema.AssociateResponse*。|  
  
## <a name="set-up-the-orchestrations"></a>設定協調流程  
 您必須立即設定協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行帳戶和連絡商務元件上的作業。  
  
-   設定協調流程上執行插入作業**帳戶**商務元件。 請參閱[商務元件使用 BizTalk Server 和 Siebel 配接器上執行的作業](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-using-the-siebel-adapter-in-biztalk.md)。  
  
-   設定協調流程上執行插入作業**連絡人**商務元件。 這是類似的 INSERT 作業**帳戶**商務元件。  
  
-   設定協調流程，對執行關聯作業**帳戶**商務元件。  
  
-   設定協調流程，對執行 QUERY_CONTACT 作業**帳戶**商務元件。  
  
 本主題將示範如何設定協調流程關聯的作業上**帳戶**商務元件。 您必須執行設定其餘的協調流程也有類似的工作。  
  
 關聯帳戶商務元件操作的協調流程看起來像：  
  
 ![用於處理 Siebel 中 mvl 的協調流程](../../adapters-and-accelerators/adapter-siebel/media/6c7d548d-dc80-490f-89fe-12aff10fa3cf.gif "6c7d548d-dc80-490f-89fe-12aff10fa3cf")  
  
 下節提供如何設定此協調流程所卸除訊息圖形，連接埠，連結的訊息結構描述等資訊。您必須執行設定的其他協調流程也有類似的工作。  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息圖形指定下列屬性。 所列的名稱*圖形*資料行名稱就是訊息圖形上述協調流程中所示。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|AccountAssociateXML|Receive|-設定**名稱**至*AccountAssociateXML*<br />-設定**啟動**至*，則為 True*|  
|SendToLOB|Send|-設定**名稱**至*SendToLOB*|  
|ReceiveResponse|Receive|-設定**名稱**至*ReceiveResponse*<br />-設定**啟動**至*False*|  
|SendResponse|Send|-設定**名稱**至*SendResponse*|  
  
### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠指定下列屬性。 所列的名稱*連接埠*資料行是連接埠的名稱，顯示在 協調流程中。  
  
|通訊埠|屬性|  
|----------|----------------|  
|FileIn_AccountAssociate|-設定**識別碼**至*FileIn_AccountAssociate*<br />-設定**類型**至*FileInAccountAssociateType*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*接收*|  
|LOBPort_AccountAssociate|-設定**識別碼**至*LOBPort_AccountAssociate*<br />-設定**類型**至*LOBPortAccountAssociateType*<br />-設定**通訊模式**至*要求-回應*<br />-設定**通訊方向**至*傳送接收*|  
|SaveResponse_AccountAssociate|-設定**識別碼**至*SaveResponse_AccountAssociate*<br />-設定**類型**至*SaveResponseAccountAssociateType*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*傳送*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>指定動作圖形訊息並連接至連接埠  
 下表指定屬性和其值設為指定的動作圖形，並將它們連結至連接埠的訊息。 所列的名稱*圖形*資料行名稱就是訊息圖形上述協調流程中所示。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|AccountAssociateXML|-設定**訊息**至*AccountAssociate_Request*<br />-設定**作業**至*FileIn_AccountAssociate.Associate.Request*|  
|SendToLOB|-設定**訊息**至*AccountAssociate_Request*<br />-設定**作業**至*LOBPort_AccountAssociate.Associate.Request*|  
|ReceiveResponse|-設定**訊息**至*AccountAssociate_Response*<br />-設定**作業**至*LOBPort_AccountAssociate.Associate.Response*|  
|SendResponse|-設定**訊息**至*回應*<br />-設定**作業**至*SaveResponse_AccountAssociate.Associate.Request*|  
  
 您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱[如何建置協調流程](../../core/how-to-build-orchestrations.md)和[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。  
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 部署 BizTalk 專案之後，您稍早建立的協調流程會列在**協調流程**BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需有關如何設定應用程式的詳細資訊，請參閱[如何建立應用程式](../../core/how-to-create-an-application.md)。  
  
 設定應用程式包括：  
  
-   選取應用程式的主機。  
  
-   對應至 BizTalk Server 管理主控台中的實體連接埠在協調流程中建立的連接埠。 此協調流程中，您必須：  
  
    -   定義位置上的硬碟和對應的檔案連接埠，您將在此置放要求訊息。 BizTalk 協調流程會使用要求訊息，並將它傳送至 Siebel 系統。 您可以擁有所有四個協調流程的相同連接埠。  
  
    -   定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含來自 Siebel 系統的回應的回應訊息。 您可以擁有所有四個協調流程的相同連接埠。  
  
    -   定義實體 Wcf-custom 或 Wcf-siebel 傳送埠將訊息傳送至 Siebel 系統。 您也必須在傳送埠中指定的動作。 如需如何建立連接埠相關資訊，請參閱[手動設定在 Siebel 介面卡的實體連接埠繫結](../../adapters-and-accelerators/adapter-siebel/manually-configure-a-physical-port-binding-to-the-siebel-adapter.md)。 您必須擁有所有四個協調流程的不同連接埠。  
  
        > [!NOTE]
        >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠的設定動作的相關資訊的繫結檔案。 您可以從 BizTalk 管理主控台建立傳送埠 （適用於傳出呼叫） 來匯入此繫結檔案。 如需詳細資訊，請參閱[設定實體連接埠繫結使用連接埠繫結檔案至 Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-physical-port-binding-using-a-port-binding-file-to-siebel.md)。
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式相關聯的下層業務元件到上層業務元件。 如需啟動 BizTalk 應用程式的指示，請參閱[啟動 BizTalk 應用程式](../../core/how-to-start-and-stop-a-biztalk-application.md)或[啟動協調流程](../../core/how-to-start-an-orchestration.md)。  
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   四個 WCF 自訂 」 或 「 Wcf-siebel 傳送埠，各自負責將訊息傳送至 Siebel 系統中，執行  
  
-   執行不同作業的四個 BizTalk 協調流程  
  
## <a name="executing-the-operation"></a>執行作業  
 您必須卸除要求訊息到檔案接收埠。 要求訊息的結構描述必須符合您稍早在本主題中所產生的結構描述。 請參閱[商務元件操作的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md)如需有關不同作業的要求訊息的結構描述。 您必須依下列順序來卸除要求訊息：  
  
-   卸除要求訊息插入至資料錄**帳戶**商務元件。 要求訊息會將記錄插入帳戶商務元件 > 主題中的已卸除類似[商務元件使用 BizTalk Server 和 Siebel 配接器上執行的作業](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-using-the-siebel-adapter-in-biztalk.md)。 協調流程取用訊息，並將它傳送至 Siebel 系統。 來自 Siebel 系統的回應會儲存在其他的協調流程中定義的檔案位置。  
  
-   卸除要求訊息插入至資料錄**連絡人**商務元件。 要求訊息會將記錄插入帳戶商務元件 > 主題中的已卸除類似[商務元件使用 BizTalk Server 和 Siebel 配接器上執行的作業](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-using-the-siebel-adapter-in-biztalk.md)。 協調流程取用訊息，並將它傳送至 Siebel 系統。 來自 Siebel 系統的回應會儲存在其他的協調流程中定義的檔案位置。  
  
-   卸除要求訊息上執行關聯作業**帳戶**商務元件。 這會將根據搜尋運算式和您在輸入 XML 中指定的多重值欄位名稱的父和下層業務元件產生關聯。 請注意：  
  
    -   父搜尋運算式中關聯作業必須符合父資料表中唯一的記錄。  
  
    -   子搜尋運算式中關聯作業必須符合子資料表中唯一的記錄。  
  
     例如，要執行帳戶商務元件關聯作業的要求訊息是：  
  
    ```  
    <Associate xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Operation">  
      <ViewMode>3</ViewMode>  
      <ParentSearchExpr>[Name] LIKE "SampleName1"</ns0:ParentSearchExpr>   
      <ParentMVGField>Bill To First Name</ns0:ParentMVGField>   
      <ChildSearchExpr>[First Name] LIKE "SampleName2"</ns0:ChildSearchExpr>   
    </Associate>  
    ```  
  
     協調流程取用訊息，並將它傳送至 Siebel 系統。 來自 Siebel 系統的回應會儲存在其他的協調流程中定義的檔案位置。 例如，上述的要求訊息的回應是：  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <AssociateResponse xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Operation">  
      <AssociateResult>  
        <ChildID xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects">1-8AO09</ChildID>  
        <ParentID xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects">1-8ANZ5</ParentID>  
      </AssociateResult>  
    </AssociateResponse>  
    ```  
  
-   卸除要求訊息上執行 QUERY_CONTACT 作業**帳戶**商務元件。 例如，QUERY_CONTACT 作業的要求訊息是：  
  
    ```  
    <Query_Contact xmlns ="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Operation">  
      <ViewMode>3</ViewMode>   
      <ParentSearchExpr>[Name] LIKE "SampleName1"</ParentSearchExpr>   
      <ParentMVGField>Bill To First Name</ParentMVGField>   
      <ContactQueryInputRecord>  
        <SearchExpr xmlns:ns1="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects">[Id] LIKE '*'</SearchExpr>   
      </ContactQueryInputRecord>  
    </Query_Contact>  
    ```  
  
     協調流程取用訊息，並將它傳送至 Siebel 系統。 來自 Siebel 系統的回應會儲存在其他的協調流程中定義的檔案位置。  
  
 請參閱[商務元件操作的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md)如需有關要求訊息的結構描述。  
  
## <a name="possible-exceptions"></a>可能的例外狀況  
 例外狀況的資訊可能會遇到執行商務元件上的作業使用的多重值欄位時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[例外狀況和錯誤處理](../../adapters-and-accelerators/adapter-siebel/exceptions-and-error-handling-with-the-siebel-adapter.md)。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。 一旦產生繫結檔案時，您可以匯入組態設定從檔案，因此您不需要建立傳送埠、 接收埠，等。 針對相同的協調流程。 如需繫結檔案的詳細資訊，請參閱[重複使用配接器繫結](../../adapters-and-accelerators/adapter-siebel/reuse-adapter-bindings-in-the-siebel-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md)