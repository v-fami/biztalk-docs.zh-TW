---
title: 叫用要求集，在 Oracle E-business Suite |Microsoft Docs
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
ms.openlocfilehash: da52668f0e94da23afdd8246f0acb0ca89d1c36a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014119"
---
# <a name="invoke-request-sets-in-oracle-e-business-suite"></a>叫用 Oracle E-business Suite 中的要求集
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] 可讓您執行 Oracle E-business Suite 中的要求。 要求集劃分為一或多個階段，且每個階段包含一組報表 」 和 「 同時執行的程式。 如需有關配接器如何支援要求集的詳細資訊，請參閱[上設定要求的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-request-sets.md)。 叫用要求集，訊息的 SOAP 結構的相關資訊，請參閱[的設定要求訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-request-sets.md)。  

## <a name="prerequisites"></a>必要條件  
 您必須先完成中的步驟[要建立 Oracle E-business Suite 應用程式的必要條件](../../adapters-and-accelerators/adapter-oracle-ebs/prerequisites-to-create-oracle-e-business-suite-applications.md)。  

## <a name="how-to-invoke-request-sets-in-oracle-e-business-suite"></a>如何叫用要求集 Oracle E-business Suite 中  
 執行的作業上使用 Oracle E-business Suite[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及中所述的程序性工作[建立 Oracle E-business Suite 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)。 若要叫用要求集，這些工作：  

- 建立 BizTalk 專案，並產生您想要叫用要求集的結構描述。  

- 在 Oracle E-business Suite 中傳送和接收訊息的 BizTalk 專案中的訊息。  

- 建立協調流程叫用要求集。  

- 建置和部署 BizTalk 專案。  

- 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  

- 啟動 BizTalk 應用程式。  

  本主題提供執行這些工作的指示。  

## <a name="generating-schema"></a>產生結構描述  
 本主題示範如何叫用要求集，藉由叫用**函式的安全性報告**（好記的名稱） 要求設定從**應用程式物件程式庫**應用程式。 要求集的實際名稱是**FNDRSSUB43**。 此要求集適用於預設的 Oracle E-business Suite 應用程式。 此要求設定則會傳回要求識別碼。  

 因此，如本主題中，我們可以產生結構描述**FNDRSSUB43**要求集。 請參閱[擷取 Oracle E-business Suite 作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)如需有關如何產生結構描述。  

## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是一個變數，要為其類型會定義對應的結構。 現在，您必須建立協調流程的訊息，並將它們連結至您在上一個步驟中產生的結構描述。  

 在此協調流程中，您必須建立兩個訊息，一個用來將訊息傳送至叫用要求集，而另一個接收要求集的回應。  

#### <a name="to-create-messages-and-link-to-schema"></a>若要建立訊息，並連結至結構描述  

1.  BizTalk 專案中新增協調流程。 從 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下**新項目**。 輸入 BizTalk 協調流程的名稱，然後按一下**新增**。  

2.  如果它尚未開啟，請開啟 BizTalk 專案，[協調流程檢視] 視窗。 若要這樣做，請按一下**檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  

3.  在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  

4.  以滑鼠右鍵按一下新建立的訊息，然後按**屬性 視窗**。  

5.  在 [**屬性**] 窗格**Message_1**，執行下列動作：  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|輸入 `Request`|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取  *RequestSet.OracleEBSBindingRequestSets_FND。FNDRSSUB43*RequestSet 所在的 BizTalk 專案的名稱。 OracleEBSBindingRequestSets 是叫用所產生的結構描述**FNDRSSUB43**要求集。|  

6.  重複步驟 3 以建立訊息。 在 **屬性**窗格中的新訊息，執行下列動作：  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |回應|*RequestSet.OracleEBSBindingRequestSets_FND。FNDRSSUB43Response*|  

## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]叫用 Oracle E-business Suite 中的要求集。 在此協調流程中，您將會卸除在要求訊息定義的接收位置。 協調流程會取用這個訊息，並將其傳遞至叫用 Oracle E-business Suite **FNDRSSUB43**要求集。 要求集回應從 Oracle 接收，且會儲存在另一個位置。 要叫用要求集的一般協調流程會包含：  

- 傳送和接收圖形以將訊息傳送至 Oracle E-business Suite，並接收回應。  

- 單向接收埠以接收要求訊息傳送到 Oracle E-business Suite。  

- 雙向傳送埠以將要求訊息傳送至 Oracle E-business Suite，並接收回應。  

- 若要從 Oracle E-business Suite 的回應傳送到資料夾的單向傳送埠。  

  範例協調流程叫用要求集，如下所示：  

  ![若要叫用要求集的協調流程](../../adapters-and-accelerators/adapter-oracle-ebs/media/ea161292-8613-4c0b-ac24-2f26c54bf3a3.gif "ea161292-8613-4c0b-ac24-2f26c54bf3a3")  

### <a name="adding-message-shapes"></a>新增訊息圖形  
 針對每個訊息 圖形中指定下列屬性。 所列的名稱*圖形*資料行是訊息 圖形的名稱，上述協調流程中所示。  

|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveMessage|Receive|-設定**名稱**到*ReceiveMessage*<br />-設定**啟用**到 *，則為 True*|  
|SendMessage|Send|-設定**名稱**到*SendMessage*|  
|ReceiveResponse|Receive|-設定**名稱**到*ReceiveResponse*<br />-設定**啟用**到*False*|  
|SendResponse|Send|-設定**名稱**到*SendResponse*|  

### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠中指定下列屬性。 所列的名稱*連接埠*資料行名稱就是連接埠在協調流程中所示。  

|通訊埠|屬性|  
|----------|----------------|  
|MessageIn|-設定**識別碼**到*MessageIn*<br />-設定**型別**到*MessageInType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*接收*|  
|LOBPort|-設定**識別碼**到*LOBPort*<br />-設定**型別**到*LOBPortType*<br />-設定**通訊模式**到*要求-回應*<br />-設定**通訊方向**到*傳送接收*|  
|ResponseOut|-設定**識別碼**到*ResponseOut*<br />-設定**型別**到*ResponseOutType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*傳送*|  

### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>為動作圖形指定訊息，並連接到連接埠  
 下表指定之屬性和其值設為指定的動作圖形，並將它們連結至連接埠的訊息。 所列的名稱*圖形*資料行名稱就是訊息 圖形上的協調流程中所示。  

|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveMessage|-設定**訊息**到*要求*<br />-設定**作業**到*MessageIn.RequestSet.Request*|  
|SendMessage|-設定**訊息**到*要求*<br />-設定**作業**到*LOBPort.RequestSet.Request*|  
|ReceiveResponse|-設定**訊息**到*回應*<br />-設定**作業**到*LOBPort.RequestSet.Response*|  
|SendResponse|-設定**訊息**到*回應*<br />-設定**作業**到*ResponseOut.RequestSet.Request*|  

 您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。  

 您必須立即建置 BizTalk 方案，並再將它部署到 BizTalk Server。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。  

## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在 [協調流程] 窗格底下[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。 如需有關如何設定應用程式的詳細資訊，請參閱 <<c0> [ 逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。  

 設定應用程式包含：  

- 選取應用程式主機。  

- 對應至實體連接埠在協調流程中建立的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 此協調流程中，您必須：  

  - 定義位置上的硬碟和對應的檔案連接埠，您將會卸除要求訊息。 BizTalk 協調流程將會取用的要求訊息，並將它傳送給 Oracle E-business Suite。  

  - 定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含來自 Oracle E-business Suite 的回應的回應訊息。  

  - 定義實體的 Wcf-custom 或 Wcf-oracleebs 傳送埠將訊息傳送至 Oracle E-business Suite。 您也必須在傳送埠中指定的動作。 如需有關如何建立傳送埠的資訊，請參閱 <<c0> [ 手動設定實體連接埠繫結來 Oracle E-business 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)。  

     使用叫用要求集[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您必須設定正確的應用程式內容，叫用作業。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]提供特定的繫結屬性，以指定應用程式內容的任何作業。 您必須在用於叫用要求集的 Wcf-custom 或 Wcf-oracleebs 連接埠上設定這些繫結屬性。  

    - 如果**ClientCredentialType**繫結屬性設定為**資料庫**，則您必須指定下列繫結屬性來設定應用程式內容。  


      |        繫結屬性         |                                                                                                                                                                                                                                                                                     ReplTest1                                                                                                                                                                                                                                                                                     |
      |---------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |       **OracleUserName**        | 指定 Oracle E-business Suite 使用者的名稱。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不會保留您輸入的值的大小寫**OracleUserName**連接到 Oracle E-business Suite 時，繫結屬性。 使用者名稱會傳遞到 Oracle E-business Suite 使用 SQL 的標準規則\*加上。 不過，如果您想要保留的使用者名稱的大小寫，或您想要輸入使用者名稱包含特殊字元，您必須指定雙引號括住的值。 |
      |       **OraclePassword**        |   Oracle E-business Suite 使用者的密碼。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不會保留您輸入的值的大小寫**OraclePassword**連接到 Oracle E-business Suite 時，繫結屬性。 密碼會傳遞至 Oracle E-business Suite 使用 SQL 的標準規則\*加上。 不過，如果您想要保留密碼的情況，或您想要輸入包含特殊字元的密碼，您必須指定雙引號括住的值。    |
      | **OracleEBSResponsibilityName** |                                                                                                                                                                                                                                                     Oracle E-business Suite 使用者相關聯責任。                                                                                                                                                                                                                                                      |


    - 如果**ClientCredentialType**繫結屬性設定為**EBusiness**，您必須已指定 Oracle E-business 認證建立連線時。 在此情況下您必須僅指定值**OracleEBSResponsibilityName**繫結屬性。  

      如需不同的繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。 如需有關配接器支援設定的應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  

    > [!NOTE]
    >  指定的繫結屬性，或設定訊息內容屬性所公開，您可以設定應用程式內容[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 如需有關如何設定繫結屬性的指示，請參閱 <<c0> [ 設定的 Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md)。 如需有關如何設定使用訊息內容屬性的應用程式內容的相關指示，請參閱[Oracle E-business Suite 中設定應用程式內容使用訊息內容屬性](../../adapters-and-accelerators/adapter-oracle-ebs/configure-application-context-using-message-context-properties-in-oracle-ebs.md)。  
    > 
    > [!NOTE]
    >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立繫結檔案，其中包含連接埠與那些連接埠設定動作的相關資訊。 您可以將從這個繫結檔案匯入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 （適用於輸出的呼叫） 的傳送埠或接收埠 （適用於輸入的呼叫）。 如需詳細資訊，請參閱 <<c0> [ 實體連接埠繫結使用的連接埠繫結檔設定到 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md)。  

## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式，來叫用要求集。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。  

 在這個階段，請確定：  

-   FILE 接收埠以接收要求訊息的協調流程正在執行。  

-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  

-   Wcf-oracleebs 的 Wcf-custom 傳送埠以叫用**FNDRSSUB43**要求組正在執行。  

-   BizTalk 協調流程的作業正在執行。  

## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須卸除要求訊息來叫用的結構描述符合**FNDRSSUB43**要求集。 例如，要求訊息來叫用**FNDRSSUB43**要求集：  

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
>  叫用要求集的要求訊息需要一些選擇性的參數，例如 SetRelClassOptions、 SetPrintOptions、 SetRepeatOptions 和 SetNlsOptions。 此處提供的要求訊息不包含這些選擇性的參數。 如需完整的要求訊息，包括選擇性的參數，請參閱[的要求訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-request-sets.md)。  

 協調流程會取用訊息、 將它傳遞到 Oracle E-business Suite 中，並接收回應。 回應訊息會儲存在其他協調流程中指定的檔案位置。 回應**FNDRSSUB43**組如下所示的要求：  

```  
<?xml version="1.0" encoding="utf-8"?>  
<FNDRSSUB43Response xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSets/FND">  
  <FNDRSSUB43Result>2543208</FNDRSSUB43Result>  
</FNDRSSUB43Response>  
```  

 Oracle E-business Suite 的回應包含要求識別碼。 要求識別碼為 '0' 表示最終送出的設定失敗要求的作業。 在此情況下，您可以指定要求訊息，例如 ContinueOnFail，找出失敗的原因及進一步偵錯中的其他選擇性參數。  

## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 一旦您產生繫結檔案時，您可以匯入的組態設定檔案，，讓您不需要建立項目，例如傳送埠和接收相同的協調流程的連接埠。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用與 Oracle E-business Suite 配接器繫結](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md)。  

## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式使用 Oracle E-business Suite 配接器 ](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)