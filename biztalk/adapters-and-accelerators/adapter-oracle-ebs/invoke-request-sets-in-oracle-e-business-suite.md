---
title: 叫用 Oracle E-business Suite 中的要求集 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a79bff63-325d-4745-ab0e-839e00476ab1
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b00fd382bb46df9de740b2308ad87c28720165a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967772"
---
# <a name="invoke-request-sets-in-oracle-e-business-suite"></a>叫用要求集 Oracle E-business Suite 中
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]可讓您執行 Oracle E-business Suite 中要求集合。 要求集劃分為一個或多個階段，而且每個階段包含一組報表和並行程式。 如需有關如何配接器支援要求的詳細資訊，請參閱[上設定要求的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-request-sets.md)。 叫用要求集，訊息的 SOAP 結構的相關資訊，請參閱[的設定要求訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-request-sets.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您必須先完成中的步驟[建立 Oracle E-business Suite 應用程式的必要條件](../../adapters-and-accelerators/adapter-oracle-ebs/prerequisites-to-create-oracle-e-business-suite-applications.md)。  
  
## <a name="how-to-invoke-request-sets-in-oracle-e-business-suite"></a>Oracle E-business Suite 中設定如何叫用要求  
 執行的作業，使用 Oracle E-business Suite[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[建立 Oracle E-business Suite 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)。 要叫用要求設定，這些工作：  
  
-   建立 BizTalk 專案，並產生您想要叫用要求集結構描述。  
  
-   Oracle E-business Suite 中傳送和接收訊息的 BizTalk 專案中建立訊息。  
  
-   建立協調流程叫用要求集。  
  
-   建置和部署 BizTalk 專案。  
  
-   設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
-   啟動 BizTalk 應用程式。  
  
 本主題提供執行這些工作的指示。  
  
## <a name="generating-schema"></a>產生結構描述  
 本主題示範如何叫用來叫用要求集**函式的安全性報告**（好記名稱） 要求設定從**應用程式物件程式庫**應用程式。 要求設定的實際名稱是**FNDRSSUB43**。 使用預設 Oracle E-business Suite 應用程式與這個要求的集合。 此要求設定傳回要求識別碼。  
  
 因此，本主題中，我們要產生結構描述的**FNDRSSUB43**要求集。 請參閱[擷取 Oracle E-business Suite 作業在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)如需有關如何產生結構描述。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。 訊息通常是為其型別由對應的結構描述所定義的變數。 您現在必須建立訊息的協調流程，並將它們連結至您在上一個步驟中產生的結構描述。  
  
 在此協調流程中，您必須建立兩個訊息，其中將訊息傳送至叫用要求集，而另一個收到的回應要求集。  
  
#### <a name="to-create-messages-and-link-to-schema"></a>建立訊息，以及連結至結構描述  
  
1.  BizTalk 專案中新增協調流程。 從 方案總管 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下 **新項目**。 輸入 BizTalk 協調流程的名稱，然後按一下**新增**。  
  
2.  如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。 若要這樣做，請按一下**檢視**，指向 **其他視窗**，然後按一下 **協調流程檢視**。  
  
3.  在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。  
  
4.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  
  
5.  在**屬性**窗格**Message_1**，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|輸入 `Request`|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*RequestSet.OracleEBSBindingRequestSets_FND。FNDRSSUB43*RequestSet 所在的 BizTalk 專案的名稱。 OracleEBSBindingRequestSets 是叫用所產生的結構描述**FNDRSSUB43**要求集。|  
  
6.  重複步驟 3 建立的訊息。 在**屬性**窗格新訊息中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |回應|*RequestSet.OracleEBSBindingRequestSets_FND。FNDRSSUB43Response*|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]叫用 Oracle E-business Suite 中的要求集合。 在此協調流程，您將會卸除要求訊息已定義的接收位置。 協調流程會取用這個訊息，並將它傳遞到叫用 Oracle E-business Suite **FNDRSSUB43**要求集。 要求組的回應從 Oracle 接收並儲存在另一個位置。 典型的協調流程叫用要求集就會包含：  
  
-   傳送和接收圖形以將訊息傳送給 Oracle E-business Suite，並接收回應。  
  
-   單向接收埠以接收要求訊息傳送給 Oracle E-business Suite。  
  
-   雙向傳送埠以將要求訊息傳送到 Oracle E-business Suite 的資訊，並接收回應。  
  
-   單向傳送埠，以便從 Oracle E-business Suite 傳送回應到資料夾。  
  
 範例協調流程叫用要求集如下所示：  
  
 ![協調流程叫用要求集](../../adapters-and-accelerators/adapter-oracle-ebs/media/ea161292-8613-4c0b-ac24-2f26c54bf3a3.gif "ea161292-8613-4c0b-ac24-2f26c54bf3a3")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 針對每個訊息 圖形中指定下列屬性。 所列的名稱*圖形*資料行名稱就是訊息圖形顯示在上述的協調流程中。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveMessage|Receive|-設定**名稱**至*ReceiveMessage*<br />-設定**啟動**至 *，則為 True*|  
|SendMessage|Send|-設定**名稱**至*SendMessage*|  
|ReceiveResponse|Receive|-設定**名稱**至*ReceiveResponse*<br />-設定**啟動**至*False*|  
|SendResponse|Send|-設定**名稱**至*SendResponse*|  
  
### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠指定下列屬性。 所列的名稱*連接埠*資料行是連接埠的名稱，顯示在 協調流程中。  
  
|通訊埠|屬性|  
|----------|----------------|  
|MessageIn|-設定**識別碼**至*MessageIn*<br />-設定**類型**至*MessageInType*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*接收*|  
|LOBPort|-設定**識別碼**至*LOBPort*<br />-設定**類型**至*LOBPortType*<br />-設定**通訊模式**至*要求-回應*<br />-設定**通訊方向**至*傳送接收*|  
|ResponseOut|-設定**識別碼**至*ResponseOut*<br />-設定**類型**至*ResponseOutType*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*傳送*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>指定動作圖形訊息並連接至連接埠  
 下表指定屬性和其值設為指定的動作圖形，並將它們連結至連接埠的訊息。 所列的名稱*圖形*資料行名稱就是訊息圖形顯示在上一個協調流程中。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveMessage|-設定**訊息**至*要求*<br />-設定**作業**至*MessageIn.RequestSet.Request*|  
|SendMessage|-設定**訊息**至*要求*<br />-設定**作業**至*LOBPort.RequestSet.Request*|  
|ReceiveResponse|-設定**訊息**至*回應*<br />-設定**作業**至*LOBPort.RequestSet.Response*|  
|SendResponse|-設定**訊息**至*回應*<br />-設定**作業**至*ResponseOut.RequestSet.Request*|  
  
 您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。  
  
 您必須現在可以建置 BizTalk 方案，然後再將它部署至 BizTalk Server。 如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。  
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 在 [協調流程] 窗格中您已部署的 BizTalk 專案後，會列出您稍早建立的協調流程[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。 如需有關如何設定應用程式的詳細資訊，請參閱[逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。  
  
 設定應用程式包括：  
  
-   選取應用程式的主機。  
  
-   對應至實體連接埠在協調流程中建立的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 此協調流程中，您必須：  
  
    -   定義位置上的硬碟和對應的檔案連接埠，您將在此置放要求訊息。 BizTalk 協調流程會使用要求訊息，並將它傳送給 Oracle E-business Suite。  
  
    -   定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含從 Oracle E-business Suite 回應的回應訊息。  
  
    -   定義將訊息傳送至 Oracle E-business Suite 實體 Wcf-custom 或 Wcf-oracleebs 傳送埠。 您也必須在傳送埠中指定的動作。 如需如何建立傳送埠相關資訊，請參閱[手動設定的實體連接埠的繫結至 Oracle E-business 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)。  
  
         要叫用要求設定使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您必須設定正確的應用程式內容，叫用作業。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]提供特定的繫結屬性，以指定應用程式內容的任何作業。 您必須使用叫用要求集的 Wcf-custom 或 Wcf-oracleebs 連接埠上設定這些繫結屬性。  
  
        -   如果**ClientCredentialType**繫結屬性設定為**資料庫**，接著，您必須指定下列繫結屬性來設定應用程式內容。  
  
            |繫結屬性|值|  
            |----------------------|-----------|  
            |**OracleUserName**|指定 Oracle E-business Suite 使用者的名稱。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不會保留您輸入的值的大小寫**OracleUserName**連接到 Oracle E-business Suite 時，繫結屬性。 使用者名稱傳遞至 Oracle E-business Suite 使用標準的規則的 SQL * Plus。 不過，如果您想要保留的使用者名稱的大小寫，或您想要輸入含有特殊字元的使用者名稱，您必須指定雙引號括住的值。|  
            |**OraclePassword**|Oracle E-business Suite 使用者的密碼。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不會保留您輸入的值的大小寫**OraclePassword**連接到 Oracle E-business Suite 時，繫結屬性。 密碼會傳遞至 Oracle E-business Suite 使用標準的規則的 SQL * Plus。 不過，如果您想要保留的密碼的大小寫，或您想要輸入包含特殊字元的密碼，您必須指定雙引號括住的值。|  
            |**OracleEBSResponsibilityName**|Oracle E-business Suite 使用者相關聯的責任。|  
  
        -   如果**ClientCredentialType**繫結屬性設定為**EBusiness**，您必須已指定 Oracle E-business 認證建立連線時。 在這種情況下您必須只指定值**OracleEBSResponsibilityName**繫結屬性。  
  
         如需不同的繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。 如需有關配接器支援設定的應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
        > [!NOTE]
        >  指定的繫結屬性，或設定訊息內容屬性所公開，您可以設定應用程式內容[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 如需有關如何設定繫結屬性的指示，請參閱[for Oracle E-business Suite 設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md)。 如需有關如何設定應用程式內容使用訊息內容屬性的指示，請參閱[Oracle E-business Suite 中設定應用程式內容使用訊息內容屬性](../../adapters-and-accelerators/adapter-oracle-ebs/configure-application-context-using-message-context-properties-in-oracle-ebs.md)。  
  
        > [!NOTE]
        >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠的設定動作的相關資訊的繫結檔案。 您可以從這個繫結檔案匯[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 （適用於傳出呼叫） 的傳送埠或接收埠 （用於進行傳入呼叫時）。 如需詳細資訊，請參閱[設定實體連接埠繫結使用連接埠繫結檔案至 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md)。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式叫用要求集。 如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。  
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   Wcf-custom 或 Wcf-oracleebs 傳送埠以叫用**FNDRSSUB43**要求組正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須卸除要求訊息，並叫用的結構描述符合**FNDRSSUB43**要求集。 例如，要叫用的要求訊息**FNDRSSUB43**要求集是：  
  
```  
<FNDRSSUB43 xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSets/FND">  
  <StartTime></ StartTime>  
  <All_x0020_Requests_x0020_in_x0020_the_x0020_Set_STAGE10>  
    <FNDMNNAV xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSetStage/FND/FNDRSSUB43">  
      <Responsibility xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSetConcurrentProgram/FND/FNDRSSUB43/STAGE10/FND">System Administrator</Responsibility>  
      <ns3:Application xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSetConcurrentProgram/FND/FNDRSSUB43/STAGE10/FND"></ns3:Application>  
    </ns2:FNDMNNAV>  
    <ns2:FNDMNMNU xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSetStage/FND/FNDRSSUB43">  
      <ns3:Responsibility xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSetConcurrentProgram/FND/FNDRSSUB43/STAGE10/FND">System Administrator</ns3:Responsibility>  
      <ns3:Application xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSetConcurrentProgram/FND/FNDRSSUB43/STAGE10/FND"></ns3:Application>  
    </ns2:FNDMNMNU>  
    <ns2:FNDMNFUN xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSetStage/FND/FNDRSSUB43">  
      <ns3:Responsibility xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSetConcurrentProgram/FND/FNDRSSUB43/STAGE10/FND">System Administrator</ns3:Responsibility>  
      <ns3:Application xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSetConcurrentProgram/FND/FNDRSSUB43/STAGE10/FND"></ns3:Application>  
    </ns2:FNDMNFUN>  
  </ns0:All_x0020_Requests_x0020_in_x0020_the_x0020_Set_STAGE10>  
</ns0:FNDRSSUB43>  
```  
  
> [!NOTE]
>  要求訊息來叫用要求集需要一些選擇性的參數，例如 SetRelClassOptions、 SetPrintOptions、 SetRepeatOptions 和 SetNlsOptions。 此處提供的要求訊息不包含這些選擇性的參數。 如需完整的要求訊息，包括選擇性的參數，請參閱[的要求訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-request-sets.md)。  
  
 協調流程取用訊息、 將它傳遞至 Oracle E-business Suite 中，並接收回應。 回應訊息會儲存在其他協調流程中指定的檔案位置。 對於回應**FNDRSSUB43**要求設定類似如下所示：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<FNDRSSUB43Response xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSets/FND">  
  <FNDRSSUB43Result>2543208</FNDRSSUB43Result>  
</FNDRSSUB43Response>  
```  
  
 從 Oracle E-business Suite，回應會包含要求的識別碼。 要求識別碼 '0' 表示最終提交設定失敗要求的作業。 在這種情況下，您可以指定要求訊息，例如 ContinueOnFail，找出失敗的原因及進一步偵錯中的其他選擇性參數。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。 一旦產生繫結檔案時，可以組態設定匯入檔案，使您不需要建立項目，例如傳送埠和接收相同的協調流程連接埠。 如需繫結檔案的詳細資訊，請參閱[重複使用配接器繫結與 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md)。  
  
## <a name="see-also"></a>請參閱  
[開發 BizTalk 應用程式使用 Oracle E-business Suite 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)