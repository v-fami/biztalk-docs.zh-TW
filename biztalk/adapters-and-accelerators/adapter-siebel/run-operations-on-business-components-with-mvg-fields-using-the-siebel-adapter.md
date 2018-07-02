---
title: 具有 MVG 欄位使用 BizTalk Server 和 Siebel 配接器的商務元件執行作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c5db211-76a2-4c27-97f4-382302c722da
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35ec36bd9dd0949289a8799be8844721cd5bb8ef
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979991"
---
# <a name="run-operations-on-business-components-with-mvg-fields-using-biztalk-server-and-the-siebel-adapter"></a>具有 MVG 欄位使用 BizTalk Server 和 Siebel 配接器的商務元件執行作業
本章節將提供包含多重值欄位的商務元件上執行作業的指示。 為了示範這類商務元件上的端對端作業，您需要執行：  
  
- 上層業務元件上插入作業  
  
- 插入作業上的下層業務元件  
  
- 多重值連結的父和子系的業務元件之間的關聯作業  
  
- 上層業務元件 Query_ [MVG_Child_Business_Comp] 作業記錄  
  
  如需有關如何[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]支援的作業對商務元件，請參閱[對商務元件作業](../../adapters-and-accelerators/adapter-siebel/operations-on-business-components-in-siebel.md)。 如需結構的 SOAP 訊息執行這些作業，請參閱[商務元件作業的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md)。  
  
## <a name="how-to-perform-operations-on-a-business-component-with-multi-value-fields"></a>如何使用多重值欄位的商務元件上執行作業？  
 使用 Siebel 系統上執行運算[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及中所述的程序性工作[建立 Siebel 應用程式的建置組塊](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)。 若要執行的商務元件上的作業，這些工作如下：  
  
1. 建立 BizTalk 專案，並產生您想要叫用商務元件上的所有作業的結構描述。 如先前所述，執行具有多重值欄位，在商務元件上的作業您必須在父系和子系的商務元件上的插入作業產生結構描述，關聯的父和子系之間的多重值連結上的作業商務元件和上層業務元件上的查詢作業。  
  
2. 建立傳送和接收來自 Siebel 系統的訊息的 BizTalk 專案中的訊息。  
  
3. 建立協調流程叫用在 Siebel 系統的不同的作業。  
  
4. 建置和部署 BizTalk 專案。  
  
5. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
6. 啟動 BizTalk 應用程式。  
  
   本主題提供執行這些工作的指示。  
  
## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 ，MVLDemo，根據本主題也提供了範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱 < [Siebel 配接器的範例](../../adapters-and-accelerators/adapter-siebel/samples-for-the-siebel-adapter.md)。  
  
## <a name="generating-schema"></a>產生結構描述  
 本主題中，以示範如何建立關聯的上層業務元件中，**帳號**下層業務元件中，以**連絡人**，我們將會產生下列的結構描述：  
  
- 在插入作業**帳戶**商務元件。 請參閱[對商務元件使用 BizTalk Server 和 Siebel 配接器的 執行作業](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-using-the-siebel-adapter-in-biztalk.md)。  
  
- 在插入作業**連絡人**商務元件。  
  
- 在關聯的作業**帳戶**商務元件。  
  
- QUERY_CONTACT 作業**帳戶**商務元件。  
  
  請參閱[取得 Siebel 作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)如需有關如何產生結構描述。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是一個變數，要為其類型會定義對應的結構。 您必須連結您的第一個步驟中的訊息從產生的 BizTalk 專案的 [協調流程] 檢視的結構描述。  
  
 本主題中，您必須建立四組的要求和回應訊息，一個用於您將會叫用 Siebel 系統每個作業。 每一組必須有一個要求訊息和回應訊息。 例如，下列程序會提供指示來建立關聯的作業的要求和回應訊息。 您必須執行類似的步驟，若要建立其他作業的訊息。  
  
 執行下列步驟來建立訊息，並將它們連結至結構描述：  
  
### <a name="create-messages-and-link-to-schema"></a>建立訊息，並連結至結構描述  
  
1.  開啟協調流程檢視 BizTalk 專案中，如果未開啟。 按一下 **檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  
  
2.  在 **協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  
  
3.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  
  
4.  在 [**屬性**] 窗格**Message_1**，執行下列動作：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|型別**AccountAssociate_Request**。|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*MVLDemo.SiebelBindingSchema.Associate*，其中*MVLDemo*是 BizTalk 專案的名稱。 *SiebelBindingSchema*會叫用所產生的結構描述*建立關聯*上的作業*帳戶*商務元件。|  
  
5.  重複上述步驟來建立新的訊息。 在 **屬性**窗格中的新訊息，執行下列動作：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|型別**AccountAssociate_Response**。|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*MVLDemo.SiebelBindingSchema.AssociateResponse*。|  
  
## <a name="set-up-the-orchestrations"></a>設定協調流程  
 您必須現在設定協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]帳戶和連絡商務元件上執行作業。  
  
- 設定上執行插入作業的協調流程**帳戶**商務元件。 請參閱[對商務元件使用 BizTalk Server 和 Siebel 配接器的 執行作業](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-using-the-siebel-adapter-in-biztalk.md)。  
  
- 設定上執行插入作業的協調流程**連絡人**商務元件。 這是類似的 INSERT 作業**帳戶**商務元件。  
  
- 設定協調流程，執行相關聯的作業**帳戶**商務元件。  
  
- 設定協調流程執行 QUERY_CONTACT 作業**帳戶**商務元件。  
  
  本主題將示範如何設定協調流程產生關聯的作業上**帳戶**商務元件。 您必須執行設定其餘的協調流程也有類似的工作。  
  
  帳戶商務元件的關聯作業協調流程看起來像：  
  
  ![使用 Siebel 中 MVL 的協調流程](../../adapters-and-accelerators/adapter-siebel/media/6c7d548d-dc80-490f-89fe-12aff10fa3cf.gif "6c7d548d-dc80-490f-89fe-12aff10fa3cf")  
  
  下一節會提供有關如何設定此協調流程，藉由卸除訊息圖形，連接埠，連結的訊息結構描述等資訊。您必須執行設定的其他協調流程也有類似的工作。  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息 圖形中指定下列屬性。 所列的名稱*圖形*資料行是訊息 圖形的名稱，上述協調流程中所示。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|AccountAssociateXML|Receive|-設定**名稱**到*AccountAssociateXML*<br />-設定**啟用**到 *，則為 True*|  
|SendToLOB|Send|-設定**名稱**到*SendToLOB*|  
|ReceiveResponse|Receive|-設定**名稱**到*ReceiveResponse*<br />-設定**啟用**到*False*|  
|SendResponse|Send|-設定**名稱**到*SendResponse*|  
  
### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠中指定下列屬性。 所列的名稱*連接埠*資料行名稱就是連接埠在協調流程中所示。  
  
|通訊埠|屬性|  
|----------|----------------|  
|FileIn_AccountAssociate|-設定**識別碼**到*FileIn_AccountAssociate*<br />-設定**型別**到*FileInAccountAssociateType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*接收*|  
|LOBPort_AccountAssociate|-設定**識別碼**到*LOBPort_AccountAssociate*<br />-設定**型別**到*LOBPortAccountAssociateType*<br />-設定**通訊模式**到*要求-回應*<br />-設定**通訊方向**到*傳送接收*|  
|SaveResponse_AccountAssociate|-設定**識別碼**到*SaveResponse_AccountAssociate*<br />-設定**型別**到*SaveResponseAccountAssociateType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*傳送*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>為動作圖形指定訊息，並連接到連接埠  
 下表指定之屬性和其值設為指定的動作圖形，並將它們連結至連接埠的訊息。 所列的名稱*圖形*資料行是訊息 圖形的名稱，上述協調流程中所示。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|AccountAssociateXML|-設定**訊息**到*AccountAssociate_Request*<br />-設定**作業**到*FileIn_AccountAssociate.Associate.Request*|  
|SendToLOB|-設定**訊息**到*AccountAssociate_Request*<br />-設定**作業**到*LOBPort_AccountAssociate.Associate.Request*|  
|ReceiveResponse|-設定**訊息**到*AccountAssociate_Response*<br />-設定**作業**到*LOBPort_AccountAssociate.Associate.Response*|  
|SendResponse|-設定**訊息**到*回應*<br />-設定**作業**到*SaveResponse_AccountAssociate.Associate.Request*|  
  
 您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並將其部署至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 建置協調流程如何](../../core/how-to-build-orchestrations.md)並[從 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。  
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在下**協調流程**在 BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需有關如何設定應用程式的詳細資訊，請參閱 <<c0> [ 如何建立應用程式](../../core/how-to-create-an-application.md)。  
  
 設定應用程式包含：  
  
- 選取應用程式主機。  
  
- 對應您在您在 BizTalk Server 管理主控台中的實體連接埠的協調流程中建立的連接埠。 此協調流程中，您必須：  
  
  - 定義位置上的硬碟和對應的檔案連接埠，您將會卸除要求訊息。 BizTalk 協調流程將會取用的要求訊息，並將它傳送至 Siebel 系統。 您可以針對所有四個協調流程相同的連接埠。  
  
  - 定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含來自 Siebel 系統的回應的回應訊息。 您可以針對所有四個協調流程相同的連接埠。  
  
  - 定義實體 Wcf-custom 或 Wcf-siebel 傳送埠將訊息傳送至 Siebel 系統。 您也必須在傳送埠中指定的動作。 如需有關如何建立連接埠的資訊，請參閱 <<c0> [ 手動設定 Siebel 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-siebel/manually-configure-a-physical-port-binding-to-the-siebel-adapter.md)。 您必須擁有所有四個協調流程的不同連接埠。  
  
    > [!NOTE]
    >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠設定動作的相關資訊的繫結檔案。 您可以從 BizTalk 管理主控台建立傳送埠 （適用於輸出的呼叫），以匯入此繫結檔案。 如需詳細資訊，請參閱 <<c0> [ 設定的實體連接埠繫結使用的連接埠繫結檔案至 Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-physical-port-binding-using-a-port-binding-file-to-siebel.md)。
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式關聯到下層業務元件的上層業務元件。 如需有關啟動 BizTalk 應用程式的指示，請參閱[啟動 BizTalk 應用程式](../../core/how-to-start-and-stop-a-biztalk-application.md)或是[啟動協調流程](../../core/how-to-start-an-orchestration.md)。  
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程正在執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   四個 WCF 自訂] 或 [Wcf-siebel 傳送連接埠，分別用於將訊息傳送至 Siebel 系統中，執行  
  
-   四個不同作業的 BizTalk 協調流程執行  
  
## <a name="executing-the-operation"></a>執行作業  
 您必須卸除要求檔案的訊息接收埠。 要求訊息的結構描述必須符合您稍早在本主題中所產生的結構描述。 請參閱[商務元件作業的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md)取得的不同作業的要求訊息的結構描述的詳細資訊。 您必須先將要求訊息卸除順序如下：  
  
- 卸除要求訊息插入至資料錄**帳戶**商務元件。 要求訊息將會類似於已卸除 > 主題中的帳戶業務元件中插入一筆資料錄[對商務元件使用 BizTalk Server 和 Siebel 配接器的 執行作業](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-using-the-siebel-adapter-in-biztalk.md)。 協調流程取用訊息，並將它傳送到 Siebel 系統。 來自 Siebel 系統的回應會儲存在其他定義的協調流程一部分的檔案位置。  
  
- 卸除要求訊息插入至資料錄**連絡人**商務元件。 要求訊息將會類似於已卸除 > 主題中的帳戶業務元件中插入一筆資料錄[對商務元件使用 BizTalk Server 和 Siebel 配接器的 執行作業](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-using-the-siebel-adapter-in-biztalk.md)。 協調流程取用訊息，並將它傳送到 Siebel 系統。 來自 Siebel 系統的回應會儲存在其他定義的協調流程一部分的檔案位置。  
  
- 卸除要求訊息上執行相關聯的作業**帳戶**商務元件。 這會建立關聯的搜尋運算式和您在輸入 XML 中指定的多重值欄位的名稱為基礎的父和子商務元件。 請注意：  
  
  - 父代的搜尋運算式建立關聯的作業必須符合父資料表中唯一的記錄。  
  
  - 子搜尋運算式中的關聯作業必須符合子資料表中唯一的記錄。  
  
    例如，要執行相關聯作業帳戶商務元件上的要求訊息是：  
  
  ```  
  <Associate xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Operation">  
    <ViewMode>3</ViewMode>  
    <ParentSearchExpr>[Name] LIKE "SampleName1"</ns0:ParentSearchExpr>   
    <ParentMVGField>Bill To First Name</ns0:ParentMVGField>   
    <ChildSearchExpr>[First Name] LIKE "SampleName2"</ns0:ChildSearchExpr>   
  </Associate>  
  ```  
  
   協調流程取用訊息，並將它傳送到 Siebel 系統。 來自 Siebel 系統的回應會儲存在其他定義的協調流程一部分的檔案位置。 例如，上述的要求訊息的回應是：  
  
  ```  
  <?xml version="1.0" encoding="utf-8"?>  
  <AssociateResponse xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Operation">  
    <AssociateResult>  
      <ChildID xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects">1-8AO09</ChildID>  
      <ParentID xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects">1-8ANZ5</ParentID>  
    </AssociateResult>  
  </AssociateResponse>  
  ```  
  
- 卸除要求訊息上執行作業 QUERY_CONTACT**帳戶**商務元件。 比方說，QUERY_CONTACT 作業的要求訊息是：  
  
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
  
   協調流程取用訊息，並將它傳送到 Siebel 系統。 來自 Siebel 系統的回應會儲存在其他定義的協調流程一部分的檔案位置。  
  
  請參閱[商務元件作業的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md)取得的要求訊息的結構描述的詳細資訊。  
  
## <a name="possible-exceptions"></a>可能的例外狀況  
 可能會遇到執行使用的多重值欄位的商務元件上的作業時的例外狀況的相關資訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 例外狀況和錯誤處理](../../adapters-and-accelerators/adapter-siebel/exceptions-and-error-handling-with-the-siebel-adapter.md)。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 之後產生的繫結檔案時，您可以匯入的組態設定從檔案，讓您不需要建立傳送埠、 接收連接埠、 相同的協調流程等。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用配接器繫結](../../adapters-and-accelerators/adapter-siebel/reuse-adapter-bindings-in-the-siebel-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md)