---
title: "考量發佈 WCF 服務使用 WCF 接收配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing, WCF services
- WCF adapters, best practices
- WCF adapters, receive adapters
- WCF services, publishing
- best practices, WCF adapters
ms.assetid: 797b7ffd-534c-4f09-9738-fb17b208bc96
caps.latest.revision: "34"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30175e7966d565306c45820f1a6c2e22e4611876
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="considerations-when-publishing-wcf-services-with-the-wcf-receive-adapters"></a>利用 WCF 接收配接器發佈 WCF 服務的考量
本主題將提供您利用 WCF 接收配接器來發佈 WCF 服務時應該納入考量的相關資訊。  使用 WCF 配接器發佈服務後，WCF 用戶端將能夠把該服務當成一般 WCF 服務來呼叫。  
  
## <a name="in-process-hosting"></a>內含式裝載  
 裝載接收位置內[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理序空間，btsntsvc.exe，允許簡化的開發和部署的優點。 此外，它會建立比利用高可用性和負載平衡功能的 IIS 中裝載的多個主控件執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  中的外部裝載資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在 IIS 中的程序是指[外掛式 WCF 接收配接器設定的 IIS](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md)。  
  
## <a name="set-the-isoneway-property-of-wcf-services-published-with-the-wcf-adapters-except-for-the-wcf-netmsmq-receive-adapter-to-false"></a>設定 WCF 配接器 （除了 Wcf-netmsmq 接收配接器） 為 false 發佈 WCF 服務的 IsOneWay 屬性  
 **System.ServiceModel.OperationContractAttribute.IsOneWay** WCF 配接器發佈的 WCF 服務的屬性，除了 Wcf-netmsmq 接收配接器設定為 **true** — 設為 **false** 即使是單向接收位置。 如果 **IsOneWay** 屬性設定為 **false**, ，甚至是方法的傳回 **void** 產生回覆訊息。 在這種情況下，基礎結構會建立並傳送空白訊息，向呼叫者指示該方法已經傳回。 使用這種方法時，基礎結構就會將服務作業擲出的例外狀況傳回給用戶端。  
  
 若要使用 WCF 配接器 （除了 Wcf-netmsmq 接收配接器） 發行的 WCF 服務中 **IsOneWay** 是 **false**, 、 **IsOneWay** 用戶端上的屬性必須設定為 **false** ，如下所示︰  
  
```  
[ServiceContract(Namespace="Microsoft.WCF.Documentation")]  
  public interface ISampleService{  
    [OperationContract(IsOneWay=false, ReplyAction="*",Action="…"]  
    string SampleMethod(string msg);  
}  
```  
  
> [!NOTE]
>  因為預設值的 **IsOneWay** 屬性是 **false**, ，您就不必在程式碼中指定的屬性。  
  
## <a name="the-replyaction-property-of-the-operationcontractattribute-on-the-client-side-should-be-set-to--an-asterisk-when-consuming-wcf-services-published-with-one-way-receive-locations"></a>若是在使用透過單向接收位置發佈的 WCF 服務，用戶端上 OperationContractAttribute 的 ReplyAction 屬性應該要設為 "*" (星號)。  
 **System.servicemodel.operationcontractattribute** 屬性 **System.servicemodel.operationcontractattribute.replyaction** 可以在用戶端用來指定從 WCF 服務的回應訊息的 SOAP 動作值。  
  
 除了指定回覆訊息的動作標頭的特定值 (通知用戶端，這是回覆和要採取的動作)，您也可以指定字串"*"（星號）。 在用戶端應用程式中指定星號，就會指示該用戶端不要驗證該服務所傳送回應訊息中的回覆動作。  
  
 若要取用 WCF 服務發佈單向接收位置，proxy 方法的 WCF 服務必須傳回 **void**, ，在此情況下 proxy 方法會預期 WCF 服務會傳送給呼叫者指出方法已傳回空的訊息。 Proxy 方法來接收此空白訊息， **ReplyAction** 屬性 **OperationContractAttribute** 應設為"*"（星號），如下所示︰  
  
```  
[ServiceContract(Namespace="Microsoft.WCF.Documentation")]  
  public interface ISampleService{  
    [OperationContract(IsOneWay=false, ReplyAction="*",Action="…"]  
    string SampleMethod(string msg);  
}  
```  
  
> [!NOTE]
>  您沒有設定 **ReplyAction** 屬性 」\*"（星號） Wcf-netmsmq 配接器，因為 Wcf-netmsmq 配接器需要 WCF 用戶端設定 **IsOneWay** 屬性 **true**。  
  
## <a name="an-isolated-host-instance-can-run-only-one-adapter"></a>外掛式主控件執行個體只能執行一個配接器：  
 外掛式主控件執行個體只能執行一個配接器。 若是使用單一外掛式主控件設定多個隔離之配接器 (例如，HTTP 和 SOAP 和 WCF 配接器) 的接收處理常式，您就必須建立多個應用程式集區，讓每個配接器使用一個應用程式集區。 如需 BizTalk 外掛式主控件的詳細資訊，請參閱[啟用 Web 服務](../core/enabling-web-services.md)。  
  
## <a name="use-the-template----content-specified-by-template-option-when-sending-non-xml-content-as-response-messages"></a>傳送非 XML 內容為回應訊息時，使用範本 -- 由範本指定的內容選項  
 WCF 配接器與 **內文--BizTalk 回應訊息內文** （預設值） 選項不允許傳送非 XML 訊息，例如字元資料和點陣圖影像。 您可以使用 **範本--由範本指定內容** WCF 配接器傳送非 XML 訊息的選項。 如需如何使用範本的詳細資訊，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。  
  
## <a name="setting-up-the-permissions-for-a-wcf-service-published-with-the-wcf-service-publishing-wizard"></a>設定透過 WCF 服務發佈精靈所發佈 WCF 服務的權限  
 當使用 ASP.NET 應用程式上使用 WCF 服務發佈精靈建立[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]平台，與 WCF 服務引動過程期間存取 Dll 可能會發生錯誤。 這些錯誤通常與預設的 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 和 [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] 安全性問題有關。 如需這些錯誤的詳細資訊，請參閱 Microsoft 說明及支援的發行項在說明及支援 」 網站上名為 「 您收到"System.IO.FileNotFoundException"錯誤時用戶端應用程式呼叫 Web 服務 」 [http://go.microsoft.com/fwlink/?LinkId=43659](http://go.microsoft.com/fwlink/?LinkId=43659)。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]需要執行的 WCF 服務的程序授與適當的權限是否內含式主控件，或外掛式主控件執行服務。 在下[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]和[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]外掛式主控件的預設 Windows 群組是外掛式主控件使用者群組，因此將權限加入外掛式主控件使用者群組應該解決此問題。  
  
#### <a name="to-add-the-permissions-to-the-isolated-host-users-group"></a>若要加入外掛式主控件使用者群組的權限  
  
1.  在 [Microsoft Windows 檔案總管] 中，找出 %windir%\temp 目錄。  
  
2.  Windir%\temp，以滑鼠右鍵按一下，然後按一下 **屬性**。  
  
3.  在 **屬性** 對話方塊中，按一下 [ **安全性** ] 索引標籤。  
  
4.  按一下  **新增**, ，請選取 **外掛式主控件使用者群組**, ，然後按一下  **確定**。  
  
## <a name="setting-up-the-permissions-for-a-wcf-receive-location-with-the-wcf-netmsmq-adapter"></a>設定具 WCF-NetMsmq 配接器之 WCF 接收位置的權限  
 當使用 NetMsmqBinding 的 WCF 用戶端將訊息傳送到透過 WCF-NetMsmq 配接器所發佈 WCF 服務時，該用戶端會將訊息定址至目標佇列，也就是由服務佇列管理員管理的佇列。 用戶端的佇列管理員會將訊息傳送至傳輸 (或外寄) 佇列。 傳輸佇列是用戶端的佇列管理員，會儲存傳輸至目標佇列的訊息。  
  
 針對定址至服務之所有目標佇列的訊息，服務的佇列管理員會接受並加以儲存。 接著，服務會要求讀取目標佇列，佇列管理員再將訊息傳遞至服務。 因此，裝載接收位置的 BizTalk 主控件執行個體服務帳戶，應擁有從目標佇列進行讀取的權限。  
  
## <a name="use-an-empty-body-path-expression-to-receive-a-soap-message-with-character-data-in-the-content-of-the-soap-body-element"></a>使用空白內文路徑運算式接收 SOAP 訊息，其 SOAP Body 項目內容中含字元資料  
 WCF 接收配接器從 SOAP 的內容中含字元資料的內送回應訊息建立 BizTalk 訊息 **主體** 項目，如所示，在下列範例中，您應該保留 **內文路徑運算式** 文字方塊空白 **訊息** WCF 配接器傳輸屬性對話方塊中的索引標籤。  
  
```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      ...  
    </s:Header>  
    <s:Body>Contoso</s:Body>  
</s:Envelope>  
```  
  
 如果您選取 **信封** 或 **主體** 選項，配接器無法建立 BizTalk 訊息的前一個內送訊息。 訊息不會遭擱置，因為輸入 SOAP 封送處理時失敗的訊息不會遭擱置。 如需有關如何使用內文路徑運算式上**訊息**索引標籤上，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。  
  
> [!NOTE]
>  設定 BTSNTSvc.exe.config. 檔，即可使用 Windows SDK 內的 TraceViewer 工具 (SvcTraceViewer.exe)。 如需 Windows SDK 的詳細資訊，請參閱 「 什麼是 Windows SDK 中的 新增 」，在 [http://go.microsoft.com/fwlink/?LinkId=75219](http://go.microsoft.com/fwlink/?LinkId=75219)。 TraceViewer 工具的詳細資訊，請參閱 < TraceViewer 工具 (SvcTraceViewer.exe) >，網址 [http://go.microsoft.com/fwlink/?LinkId=75218](http://go.microsoft.com/fwlink/?LinkId=75218)。  
  
## <a name="using-schemas-that-reference-other-schemas"></a>使用參考其他結構描述的結構描述  
 您可以使用 **重新定義**, ，**包括**, ，和 **匯入** 項目時您的結構描述變大變複雜，或當代表您不同類型的執行個體訊息的結構描述的共通部分。 將較小的結構描述，組合成最後會定義打算用來與交易夥伴交換之執行個體訊息之結構的結構描述，是一種很有用的做法。 您可以使用「BizTalk WCF 服務發佈精靈」，將這些結構描述發佈為 WCF 服務。  
  
 您應該使用「BizTalk WCF 服務使用精靈」，建立從 BizTalk 專案中使用 WCF 服務時所需要的 BizTalk 成品。 若要從 .NET 應用程式使用 WCF 服務，您應該要使用 ServiceModel Metadata Utility 工具 (Svcutil.exe)，建立該 WCF 服務適用的 Proxy 類別。 如需如何使用參考其他結構描述的結構描述的詳細資訊，請參閱[，使用其他結構描述](../core/schemas-that-use-other-schemas.md)和[如何建立可使用其他結構描述](../core/how-to-create-schemas-that-use-other-schemas.md)。 需 Svcutil.exe 的詳細資訊，請參閱 「 服務模型中繼資料公用程式工具 （Svcutil.exe) >，網址 [http://go.microsoft.com/fwlink/?LinkID=74696](http://go.microsoft.com/fwlink/?LinkID=74696)。  
  
 下表針對配合會應用到其他結構描述之結構描述所發佈的 WCF 服務，列出這類服務在使用時要注意到的限制和考量。  
  
|XML 結構描述項目|使用透過 BizTalk WCF 服務發佈精靈所發佈的 WCF 服務|使用 .NET 應用程式所裝載的 WCF 服務|  
|------------------------|-------------------------------------------------------------------------------------|--------------------------------------------------------|  
|\<import\>|BizTalk WCF 服務使用精靈和 Svcutil.exe 皆支援|BizTalk WCF 服務使用精靈和 Svcutil.exe 皆支援|  
|\<include\>|支援使用 BizTalk WCF 服務使用精靈和 Svcutil.exe **附註︰**  Svcutil.exe 建立 proxy 類別時，可能會發出警告訊息。|支援使用 BizTalk WCF 服務使用精靈和 Svcutil.exe **附註︰**  Svcutil.exe 建立 proxy 類別時，可能會發出警告訊息。|  
|\<redefine\>|支援使用 BizTalk WCF 服務使用精靈<br />-Svcutil.exe 支援有限 **附註︰**  Svcutil.exe 有相同的限制 **重新定義** xsd.exe 的項目。|支援使用 BizTalk WCF 服務使用精靈和 Svcutil.exe **附註︰**  Svcutil.exe 建立 proxy 類別時，可能會發出警告訊息。|  
  
> [!NOTE]
>  對已發佈的 BizTalk WCF 服務的 proxy 類別建立與使用的結構描述時，Svcutil.exe 可能會發出警告訊息 **包括** 和 **重新定義** 項目。 例如，「已經宣告全域項目」。  
  
## <a name="ensure-that-an-in-process-wcf-receive-location-is-not-disabled-after-you-change-the-computer-name-part-in-its-service-endpoint-address"></a>確定在您變更服務端點位址中的電腦名稱部分之後，內含式 WCF 接收位置未遭停用  
 如果您變更電腦名稱部分 **位址 (URI)** 文字方塊執行內含式 WCF 接收位置，我們建議您，使用 BizTalk 管理主控台，來檢查是否仍然正在執行的接收位置。 例如，如果您變更服務端點位址使用 Wcf-nettcp 接收配接器， **net.tcp://\<***您的電腦名稱***\>/samplepath**至**net.tcp://localhost/samplepath**，接收位置可能會停用與**Service.InvalidOperationException**。 如果您只變更服務端點位址的電腦名稱部分而不修改路徑部分，請確定該接收位置未遭停用，並在必要情況下啟用該位置。  
  
## <a name="set-the-appropriate-msdtc-security-configuration-options-on-client-computers-communicating-with-remote-wcf-receive-locations-through-a-transaction-protocol"></a>在透過交易通訊協定和遠端 WCF 接收位置通訊的用戶端電腦上設定適當的 MSDTC 安全性組態選項  
 Wcf-nettcp、 Wcf-wshttp 和 Wcf-netnamedpipe 接收配接器使用 WCF 用戶端管理的交易式協調程序可以參與 **Ws-atomictransaction** 和 **OleTransaction** 交易通訊協定。 在交易內容中使用這些交易通訊協定，即可將訊息傳輸到目的接收位置，以及從 MessageBox 資料庫中加以刪除。  
  
 與遠端 WCF 接收位置所使用的交易通訊協定，您必須適當地設定 MSDTC **安全性設定** WCF 用戶端電腦上的選項。 下表列出 MSDTC 中可用的選項的必要的值 **安全性設定**  對話方塊中︰  
  
|組態選項|預設值|建議值|  
|--------------------------|-------------------|-----------------------|  
|網路 DTC 存取|Disabled|已啟用|  
|允許輸出|Disabled|已啟用|  
|需要相互驗證|已啟用|如果對應的遠端接收位置正在執行 Windows Server 2003 SP1 或 SP2，並且設定為啟用 **需要相互驗證**。|  
|要求對連入呼叫者驗證|已停用|如果在叢集上執行 MSDTC，則為「已啟用」。|  
  
 在套用這些變更後，您必須重新啟動 MSDTC 服務。  
  
 若要存取 MSDTC **安全性設定** 對話方塊方塊中，請遵循下列步驟︰  
  
1.  按一下  **啟動**, ，按一下 **執行**, ，然後輸入 **dcomcnfg** 啟動 **元件服務** 管理主控台。  
  
2.  展開 **元件服務**, ，依序展開 **電腦**, ，以滑鼠右鍵按一下 **我的電腦**, ，然後按一下  **屬性**。  
  
3.  在 **我的電腦內容** 對話方塊中，按一下  **MSDTC** 索引標籤，然後按一下 **安全性設定** 顯示 **安全性設定** 對話方塊。  
  
## <a name="explanation-of-the-soap-wrapper-when-using-the-biztalk-wcf-service-publishing-wizard"></a>使用 BizTalk WCF 服務發佈精靈時之 SOAP 包裝函式的說明  
 使用 [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] 服務發佈精靈將協調流程公開為 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 服務時，會產生包裝函式。 這個包裝函式會使用的連接埠傳送訊息的 XML 訊息中的方法名稱。 這個包裝函式是 Microsoft SOAP 封套中的預設值。 它可讓[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]包裝一個配接器傳送給端點的 WCF 訊息中的多部分 SOAP 訊息。  
  
 最佳做法，傳送者應使用包裝函式和接收者應該預期，或寄件者不應該使用包裝函式，而且收件者應該預期的原始[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]訊息。 事先同意的是否要使用包裝函式失敗，可能會導致傳送和接收的內容之間的不相容性問題。