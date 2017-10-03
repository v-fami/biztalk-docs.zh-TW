---
title: "考量使用 WCF 服務使用 WCF 傳送配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- consuming, WCF services
- best practices, WCF services
- WCF services, best practices
- consuming, best practices
- WCF services, consuming
ms.assetid: 8bbcfd99-3495-458d-bd7a-6d170a29dde2
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2bb1e512b8a13c3d91b87bbfc410c3d21f334fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-when-consuming-wcf-services-with-the-wcf-send-adapters"></a>利用 WCF 傳送配接器使用 WCF 服務的考量
本主題提供您利用 WCF 配接器使用 Web 服務時應該納入之考量的相關資訊。  
  
## <a name="use-the-template----content-specified-by-template-option-when-sending-non-xml-content-as-solicit-messages"></a>傳送非 XML 內容為請求訊息時，使用範本 -- 由範本指定的內容選項  
 WCF 配接器與**內文--BizTalk 回應訊息內文**（預設值） 選項不允許傳送非 XML 訊息，例如字元資料和點陣圖影像。 您可以使用**範本--由範本指定內容**WCF 配接器傳送非 XML 訊息的選項。 如需如何使用範本的詳細資訊，請參閱[考量時發佈 WCF 服務使用 WCF 接收配接器](../core/considerations-when-publishing-wcf-services-with-the-wcf-receive-adapters.md)。  
  
## <a name="the-wcf-basichttp-and-wcf-wshttp-send-ports-always-ignore-the-proxy-if-the-service-address-begins-with-httplocalhost"></a>若服務位址開頭為 http://localhost，WCF-BasicHttp 和 WCF-WSHttp 傳送埠永遠會略過 Proxy  
 Wcf-basichttp 和 Wcf-wshttp 傳送埠永遠略過 proxy，如果服務位址是以 http://localhost 開頭，無論 proxy 設定在**Proxy**的傳送埠 索引標籤或**Proxy**  索引標籤傳送處理常式。 若您希望用戶端與同一部電腦的服務進行通訊時是透過 Proxy，就應該使用主控件名稱 (不要使用 localhost)。  
  
## <a name="the-wcf-basichttp-and-wcf-wshttp-send-adapters-suspend-the-messages-if-the-proxy-setting-is-not-correctly-configured"></a>若 Proxy 設定不正確，WCF-BasicHttp 和 WCF-WSHttp 傳送配接器會擱置訊息  
 您可以指定的 proxy 設定 Wcf-basichttp 和 Wcf-wshttp 傳送配接器**Proxy**的傳送埠 索引標籤或**Proxy**傳送處理常式 索引標籤。 若 Proxy 設定不正確，WCF 配接器會擱置訊息，而且事件日誌會接收到錯誤訊息「沒有任何接聽的端點可以接受該訊息」。  
  
## <a name="setting-up-the-permissions-for-a-wcf-send-port-with-the-wcf-netmsmq-adapter"></a>設定具 WCF-NetMsmq 配接器之 WCF 傳送埠的權限  
 當具 WCF-NetMsmq 配接器的 WCF 傳送埠傳送訊息至使用 NetMsmqBinding 所發佈的 WCF 服務時，會將訊息定址至目標佇列 (由服務佇列管理員管理的佇列)。 用戶端的佇列管理員會將訊息傳送至傳輸 (或外寄) 佇列。 傳輸佇列是用戶端的佇列管理員，會儲存傳輸至目標佇列的訊息。  
  
 針對定址至服務之所有目標佇列的訊息，服務的佇列管理員會接受並加以儲存。 接著，服務會要求讀取目標佇列，佇列管理員再將訊息傳遞至服務。 因此，裝載傳送埠的 BizTalk 主控件執行個體服務帳戶，應擁有寫入傳輸佇列的權限。  
  
## <a name="use-an-empty-xpath-expression-to-receive-a-soap-message-with-character-data-in-the-content-of-the-soap-body-element"></a>使用空 XPath 運算式接收 SOAP 訊息，其 SOAP Body 項目內容中含字元資料  
 請求-回應 WCF 傳送埠可接收 WCF 訊息做為回應訊息。 若要建立 BizTalk 訊息內送回應訊息的 soap 內容中含字元資料從**主體**如下列範例所示的項目，您應該保留**XPath 運算式**文字方塊空的**訊息**WCF 配接器傳輸屬性對話方塊中的索引標籤。  
  
```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      ...  
    </s:Header>  
    <s:Body>Contoso</s:Body>  
</s:Envelope>  
```  
  
 如果您選取**信封**或**主體**選項，配接器不會建立 BizTalk 訊息的內送訊息。 訊息不會遭擱置，因為輸入 SOAP 封送處理時失敗的訊息不會遭擱置。 如需有關如何使用 XPath 運算式，在**訊息**索引標籤上，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。  
  
> [!NOTE]
>  設定 BTSNTSvc.exe.config. 檔，即可使用 Windows SDK 內的 TraceViewer 工具 (SvcTraceViewer.exe)。 如需 Windows SDK 的詳細資訊，請參閱 < 什麼是 Windows SDK 中的 新增 >，網址[http://go.microsoft.com/fwlink/?LinkId=75219](http://go.microsoft.com/fwlink/?LinkId=75219)。 TraceViewer 工具的詳細資訊，請參閱 < TraceViewer 工具 (SvcTraceViewer.exe) >，網址[http://go.microsoft.com/fwlink/?LinkId=75218](http://go.microsoft.com/fwlink/?LinkId=75218)。  
  
## <a name="biztalk-server-does-not-use-multi-part-message-types-and-root-elements-describing-custom-soap-headers"></a>BizTalk Server 不使用多部分訊息類型和描述自訂 SOAP 標頭的根項目  
 若您對中繼資料執行 [BizTalk WCF 服務使用精靈]，而其中的自訂 SOAP 標頭已定義，精靈會在產生的結構描述中產生根項目，代表自訂 SOAP 標頭。 精靈也會為自訂 SOAP 標頭在協調流程中建立多部分訊息類型。 BizTalk Server。 然而，BizTalk Server 不使用多部分訊息類型和根項目來處理自訂 SOAP 標頭。  
  
 若要存取自訂 SOAP 標頭，您應該使用**InboundHeaders**屬性。 如需接收自訂 SOAP 標頭的詳細資訊，請參閱[SOAP 標頭與已發佈 WCF 服務](../core/soap-headers-with-published-wcf-services.md)。 若要使用自訂 SOAP 標頭，您應該使用**OutboundCustomHeaders**屬性。 如需傳送自訂 SOAP 標頭的詳細資訊，請參閱[取用 WCF 服務使用的 SOAP 標頭](../core/soap-headers-with-consumed-wcf-services.md)。  
  
## <a name="create-separate-host-instances-for-send-ports-that-use-different-proxy-addresses-andor-proxy-credentials"></a>為使用不同 Proxy 位址和/或 Proxy 認證的傳送埠，建立個別的主控件執行個體  
 若要讓 WCF 傳送配接器達到可能的最佳效能，建議您為使用不同 Proxy 位址和/或 Proxy 認證的傳送埠，建立個別的主控件執行個體。 如此可避免爭用 Proxy 設定。  
  
## <a name="see-also"></a>另請參閱  
 [BTSNTSvc.exe.config 檔案](../core/btsntsvc-exe-config-file.md)