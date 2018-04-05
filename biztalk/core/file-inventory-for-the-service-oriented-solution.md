---
title: 檔案庫存服務導向解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service solution tutorial, file inventory
ms.assetid: 32c25372-31e1-4059-b4ed-f12e62f315d5
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 39d18b32e1b499009e7559a68d7e60e6ba43f28c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="file-inventory-for-the-service-oriented-solution"></a>檔案庫存服務導向解決方案
本節列出服務導向解決方案的子目錄與原始程式檔。 Service Oriented 方案原始程式檔的預設安裝目錄是 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios\SO。 下表會取代此路徑與之前的描述\<安裝目錄\>。  
  
 中的檔案\<安裝目錄\>\BTSSoln  
  
|檔案|Description|  
|----------|-----------------|  
|Microsoft.Samples.BizTalk.WoodgroveBank.sln|Visual Studio 方案檔。|  
|ReplacePKToken.vbs|在建立解決方案時，會修正解決方案檔案中公開金鑰 Token 的 VBScript。|  
|ReplacePKToken.wsf|用於 ReplacePKToken VBScript 的 Windows 指令碼檔案。|  
|SetupBTSSoln.bat|建立公開金鑰、更新公開金鑰的參考，以及編譯解決方案。 如需部署解決方案的資訊，請參閱[部署服務導向解決方案](../core/deploying-the-service-oriented-solution.md)。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\BAM  
  
|檔案|Description|  
|----------|-----------------|  
|ServiceLevelTracking.xls|用於 BAM 資料的 Excel 試算表。|  
|ServiceLevelTracking.xml|定義 BAM 資料項目類型的結構描述。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\Bindings  
  
|檔案|Description|  
|----------|-----------------|  
|AdapterSOAOrchBindings.xml|解決方案之配接器版本的繫結檔案。|  
|InlineSOAOrchBindings.xml|解決方案之內嵌版本的繫結檔案。|  
|StubSOAOrchBindings.xml|解決方案之虛設常式版本的繫結檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\ConfigHelper  
  
|檔案|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|組件資訊檔。|  
|ConfigHelper.csproj|C# 專案檔。|  
|ConfigParameters.cs|用於 SSO 組態協助程式方法的 C# 程式碼檔案。|  
|ConfigPropertyBag.cs|用於 SSO 組態協助程式方法所使用之屬性包的 C# 程式碼檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\ErrorHelper  
  
|檔案|Description|  
|----------|-----------------|  
|CustomerServiceErrors.cs|用於客戶服務錯誤的 C# 程式碼檔案。|  
|ErrorHelper.csproj|C# 專案檔。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\InPipeline  
  
|檔案|Description|  
|----------|-----------------|  
|InPipeline.btp|將 SSO 票證新增至訊息的接收管線。|  
|InPipeline.btproj|BizTalk 專案檔。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\InPipelineComp  
  
|檔案|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|組件資訊檔。|  
|InPipelineComp.csproj|C# 專案檔。|  
|SSOTicketIssuer.cs|用於發行 SSO 票證之管線元件的 C# 程式碼檔案。|  
|SSOTicketIssuer.resx|資源檔。|  
|SSOTicketIssuerIcon.bmp|用於管線元件的圖示檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\Maps  
  
|檔案|Description|  
|----------|-----------------|  
|Aggregate_To_CustomerServiceResponse.btm|用來將這三個來自後端系統的回應之彙總轉換為單一回應訊息的對應。|  
|Aggregate_To_ErrorResponse.btm|在錯誤發生時，用來將這三個回應的彙總轉換為單一錯誤回應的對應。|  
|CustomerServiceRequest_To_CreditLimiRequest.btm|用來將客戶服務要求轉換為訊息以要求信用限制的對應。|  
|CustomerServiceRequest_To_CreditLimitResponse.btm|用來將客戶服務要求轉換為訊息，以信用限制來回應的對應。|  
|CustomerServiceRequest_To_CustomerServiceResponseDenied.btm|用來將客戶服務要求轉換為拒絕要求訊息的對應。|  
|CustomerServiceRequest_To_LastPaymentRequest.btm|用來將客戶服務要求轉換為訊息，以要求上次付款資訊的對應。|  
|CustomerServiceRequest_To_LastPaymentResponseTimeout.btm|用來將客戶服務要求轉換為上次付款回應訊息的對應。|  
|CustomerServiceRequest_To_PendingTransactionResponse.btm|用來將客戶服務要求轉換為擱置交易回應訊息的對應。|  
|CustomerServiceRequest_To_PendingTransactionsRequest.btm|用來將客戶服務要求轉換為訊息，以要求擱置交易資訊的對應。|  
|Maps.btproj|BizTalk 專案檔。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\Orchestrations\Adapter  
  
|檔案|Description|  
|----------|-----------------|  
|CustomerService.odx|配接器版本**CustomerService**協調流程。|  
|CustomerServiceNativeRequestResponse.odx|服務的前端協調流程的配接器版本**CustomerService**協調流程。|  
|CustomerServiceReceiveSend.odx|服務的前端協調流程的配接器版本**CustomerService**協調流程。|  
|Orchestrations.Adapter.btproj|BizTalk 專案檔。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\Orchestrations\Adapter\Web References\PendTransWS  
  
|檔案|Description|  
|----------|-----------------|  
|PendTransWS.disco|產生的檔案。|  
|PendTransWS.wsdl|產生的檔案。|  
|Reference.map|產生的檔案。|  
|Reference.map.cs|產生的檔案|  
|Reference.odx|產生的檔案。|  
|Reference.xsd|產生的檔案。|  
|Reference1.xsd|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\Orchestrations\Adapter\Web References\StubSAPWS  
  
|檔案|Description|  
|----------|-----------------|  
|Reference.map|產生的檔案。|  
|Reference.map.cs|產生的檔案。|  
|Reference.odx|產生的檔案。|  
|Reference.xsd|產生的檔案。|  
|StubSAPWS.disco|產生的檔案。|  
|StubSAPWS.wsdl|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\Orchestrations\Inline  
  
|檔案|Description|  
|----------|-----------------|  
|CustomerService.odx|內嵌版本**CustomerService**協調流程。|  
|CustomerServiceNativeRequestResponse.odx|服務的前端協調流程的內嵌版本**CustomerService**協調流程。|  
|CustomerServiceReceiveSend.odx|服務的前端協調流程的內嵌版本**CustomerService**協調流程。|  
|Orchestrations.Inline.btproj|BizTalk 專案檔。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\Orchestrations\Stub  
  
|檔案|Description|  
|----------|-----------------|  
|CustomerService.odx|虛設常式版本**CustomerService**協調流程。|  
|CustomerServiceNativeRequestResponse.odx|服務的前端協調流程的虛設常式版本**CustomerService**協調流程。|  
|Orchestrations.Stub.btproj|BizTalk 專案檔。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\Orchestrations\Stub\Web References\StubPendTransWS  
  
|檔案|Description|  
|----------|-----------------|  
|Reference.map|產生的檔案。|  
|Reference.map.cs|產生的檔案。|  
|Reference.odx|產生的檔案。|  
|Reference.xsd|產生的檔案。|  
|Reference1.xsd|產生的檔案。|  
|StubPendTransWS.disco|產生的檔案。|  
|StubPendTransWS.wsdl|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\Orchestrations\Stub\Web References\StubPmntTrckWS  
  
|檔案|Description|  
|----------|-----------------|  
|Reference.map|產生的檔案。|  
|Reference.map.cs|產生的檔案。|  
|Reference.odx|產生的檔案。|  
|Reference.xsd|產生的檔案。|  
|Reference1.xsd|產生的檔案。|  
|StubPmntTrckWS.disco|產生的檔案。|  
|StubPmntTrckWS.wsdl|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\Orchestrations\Stub\Web References\StubSAPWS  
  
|檔案|Description|  
|----------|-----------------|  
|Reference.map|產生的檔案。|  
|Reference.map.cs|產生的檔案。|  
|Reference.odx|產生的檔案。|  
|Reference.xsd|產生的檔案。|  
|StubSAPWS.disco|產生的檔案。|  
|StubSAPWS.wsdl|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\OrchProxy\Adapter  
  
|檔案|Description|  
|----------|-----------------|  
|CustomerServicePort.asmx|產生的檔案。|  
|Global.asax|產生的檔案。|  
|Global.asax.resx|產生的檔案。|  
|OrchProxy.Adapter.csproj.webinfo|產生的檔案。|  
|TraceExtension.cs|產生的檔案。|  
|Web.config|產生的檔案。|  
|WsdlExtension.cs|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\OrchProxy\Adapter\app_code  
  
|檔案|Description|  
|----------|-----------------|  
|assemblyinfo.cs|產生的檔案。|  
|customerserviceport.asmx.cs|產生的檔案。|  
|datatypes.cs|產生的檔案。|  
|global.asax.cs|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\OrchProxy\Inline  
  
|檔案|Description|  
|----------|-----------------|  
|CustomerServicePort.asmx|產生的檔案。|  
|Global.asax|產生的檔案。|  
|Global.asax.resx|產生的檔案。|  
|OrchProxy.Inline.csproj.webinfo|產生的檔案。|  
|TraceExtension.cs|產生的檔案。|  
|Web.config|產生的檔案。|  
|WsdlExtension.cs|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\OrchProxy\Inline\app_code  
  
|檔案|Description|  
|----------|-----------------|  
|assemblyinfo.cs|產生的檔案。|  
|customerserviceport.asmx.cs|產生的檔案。|  
|datatypes.cs|產生的檔案。|  
|global.asax.cs|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\OrchProxy\Stub  
  
|檔案|Description|  
|----------|-----------------|  
|CustomerServicePort.asmx|產生的檔案。|  
|Global.asax|產生的檔案。|  
|Global.asax.resx|產生的檔案。|  
|OrchProxy.Stub.csproj.webinfo|產生的檔案。|  
|TraceExtension.cs|產生的檔案。|  
|Web.config|產生的檔案。|  
|WsdlExtension.cs|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\OrchProxy\Stub\app_code  
  
|檔案|Description|  
|----------|-----------------|  
|assemblyinfo.cs|產生的檔案。|  
|customerserviceport.asmx.cs|產生的檔案。|  
|datatypes.cs|產生的檔案。|  
|global.asax.cs|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\PaymentTracker  
  
|檔案|Description|  
|----------|-----------------|  
|App.ico|用於付款追蹤程式模擬器的圖示檔案。|  
|AssemblyInfo.cs|組件資訊檔。|  
|MessageProcessor.cs|用於處理付款追蹤程式訊息並傳回適當回應之類別的 C# 程式碼。|  
|PaymentTracker.cs|用於模擬付款追蹤程式系統之類別的 C# 程式碼。|  
|PaymentTracker.csproj|C# 專案檔。|  
|PaymentTrackerSimulator.cs|用於付款追蹤程式模擬器之伺服器的 C# 程式碼。|  
|runit.cmd|可啟動付款追蹤程式模擬器的命令檔。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\PaymentTrackerCall  
  
|檔案|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|組件資訊檔。|  
|Exceptions.cs|定義付款追蹤系統例外狀況的 C# 程式碼。|  
|PaymentTrackerCall.csproj|C# 專案檔。|  
|PaymentTrackerCaller.cs|用於從協調流程內呼叫付款追蹤系統的 C# 程式碼。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\PendTransCall  
  
|檔案|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|組件資訊檔。|  
|Exceptions.cs|定義擱置交易系統例外狀況的 C# 程式碼。|  
|PendingTransactionsCaller.cs|用於從協調流程內呼叫擱置交易系統的 C# 程式碼。|  
|PendingTransactionsWebService.disco|產生的檔案。|  
|PendingTransactionsWebService.wsdl|產生的檔案。|  
|PendTransCall.csproj|C# 專案檔。|  
|WebServiceReference.cs|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\PmTrkPipeline  
  
|檔案|Description|  
|----------|-----------------|  
|PaymentTrackerReceivePipeline.btp|用於付款追蹤系統的接收管線。|  
|PaymentTrackerSendPipeline.btp|用於付款追蹤系統的傳送管線。|  
|PmTrkPipeline.btproj|BizTalk 專案檔。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\PmTrkPipelineComp  
  
|檔案|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|組件資訊檔。|  
|MQSeriesHeaderSetter.cs|C# 程式碼來處理前往或來自付款追蹤系統的訊息部分 MQSeries 訊息標頭設定的管線元件...|  
|MQSeriesHeaderSetter.resx|資源檔。|  
|PmTrkPipelineComp.csproj|C# 專案檔。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\SchemaClasses  
  
|檔案|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|組件資訊檔。|  
|BAPI_BANKACCT_GET_DETAIL.cs|從對應的結構描述 (.xsd) 檔案產生。|  
|CustomerServiceRequest.cs|從對應的結構描述 (.xsd) 檔案產生。|  
|CustomerServiceResponse.cs|從對應的結構描述 (.xsd) 檔案產生。|  
|LastPaymentRequest.cs|從對應的結構描述 (.xsd) 檔案產生。|  
|LastPaymentResponse.cs|從對應的結構描述 (.xsd) 檔案產生。|  
|PendingTransactionsRequest.cs|從對應的結構描述 (.xsd) 檔案產生。|  
|PendingTransactionsResponse.cs|從對應的結構描述 (.xsd) 檔案產生。|  
|SchemaClasses.csproj|C# 專案檔。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\Schemas  
  
|檔案|Description|  
|----------|-----------------|  
|BAPI_BANKACCT_GET_DETAIL.xsd|用於 SAP 要求與回應訊息的結構描述。|  
|CustomerServiceRequest.xsd|用於客戶服務要求訊息的結構描述。|  
|CustomerServiceResponse.xsd|用於客戶服務回應訊息的結構描述。|  
|genClasses.cmd|從結構描述產生 C# 類別的命令檔。|  
|LastPaymentRequest.xsd|用於上次付款要求訊息的結構描述。|  
|LastPaymentResponse.xsd|用於上次付款回應訊息的結構描述。|  
|PendingTransactionsRequest.xsd|暫止的交易要求訊息的結構描述。|  
|PendingTransactionsResponse.xsd|用於擱置交易回應訊息的結構描述。|  
|Schemas.btproj|BizTalk 專案檔。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\Scripts  
  
|檔案|Description|  
|----------|-----------------|  
|ConfigStoreApp.xml|定義 SSO 組態值的 XML 檔案。|  
|CreateInitialConfigInSSO.cmd|建立初始 SSO 組態值的命令檔。|  
|DeployAllBinding.cmd|部署所有組件的命令檔。|  
|DeployStubBinding.cmd|部署組件之虛設常式版本的命令檔。|  
|PendTransAffApp.xml|定義擱置交易分支機構應用程式之值的 XML 檔案。|  
|PendTransUserMap.xml|為擱置交易分支機構應用程式的使用者，定義認證對應的 XML 檔案。|  
|PmntTrckAffApp.xml|定義擱置交易分支機構應用程式之值的 XML 檔案。|  
|PmntTrckUserMap.xml|為付款追蹤分支機構應用程式的使用者，定義認證對應的 XML 檔案。|  
|RemoveReceivePort.vbs|移除接收埠的一般 VBScript。|  
|RemoveSendPort.vbs|移除傳送埠的一般 VBScript。|  
|SetConfigValuesInSSO.cmd|在 SSO 中設定組態值的命令檔。|  
|StartAll.vbs|登錄並啟動所有協調流程的命令檔。|  
|StartStub.vbs|登錄並啟動協調流程之虛設常式版本的命令檔。|  
|UndeployAll.cmd|取消部署所有組件的命令檔。|  
|UndeployStub.cmd|取消部署組件之虛設常式版本的命令檔。|  
|UnEnlistAll.vbs|取消登錄所有協調流程的命令檔。|  
|UnEnlistStub.vbs|取消登錄協調流程之虛設常式版本的命令檔。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\ServiceLevelTracking  
  
|檔案|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|組件資訊檔。|  
|ServiceLevelTracking.cs|用於服務層級 BAM 追蹤的 C# 協助程式函式。|  
|ServiceLevelTracking.csproj|C# 專案檔。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\SimpleClient  
  
|檔案|Description|  
|----------|-----------------|  
|AdapterCustomerServicePort.disco|產生的檔案。|  
|AdapterCustomerServicePort.wsdl|產生的檔案。|  
|App.ico|用於簡單用戶端應用程式的圖示檔案。|  
|AssemblyInfo.cs|組件資訊檔。|  
|InlineCustomerServicePort.disco|產生的檔案。|  
|InlineCustomerServicePort.wsdl|產生的檔案。|  
|SimpleClient.cs|用於產生要求的簡單 Windows Forms 應用程式。|  
|SimpleClient.csproj|C# 專案檔。|  
|SimpleClient.resx|資源檔。|  
|WebServiceReferences.cs|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\StubWebServices\PaymentTrack  
  
|檔案|Description|  
|----------|-----------------|  
|Global.asax|產生的檔案。|  
|Global.asax.resx|產生的檔案。|  
|StubPmntTrck.csproj.webinfo|產生的檔案。|  
|StubPmntTrckWS.asmx|產生的檔案。|  
|StubPmntTrckWS.asmx.resx|產生的檔案。|  
|Web.config|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\StubWebServices\PaymentTrack\app_code  
  
|檔案|Description|  
|----------|-----------------|  
|assemblyinfo.cs|組件資訊檔。|  
|global.asax.cs|產生的檔案。|  
|StubPmntTrckWS.asmx.cs|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\StubWebServices\PendingTrans  
  
|檔案|Description|  
|----------|-----------------|  
|Global.asax|產生的檔案。|  
|Global.asax.resx|產生的檔案。|  
|StubPendTransWS.asmx|產生的檔案。|  
|StubPendTransWS.asmx.resx|產生的檔案。|  
|StubPendTransWS.csproj.webinfo|產生的檔案。|  
|Web.config|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\StubWebServices\PendingTrans\app_code  
  
|檔案|Description|  
|----------|-----------------|  
|assemblyinfo.cs|產生的檔案。|  
|global.asax.cs|產生的檔案。|  
|StubPendTransWS.asmx.cs|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\StubWebServices\SAP  
  
|檔案|Description|  
|----------|-----------------|  
|Global.asax|產生的檔案。|  
|Global.asax.resx|產生的檔案。|  
|StubSAP.csproj.webinfo|產生的檔案。|  
|StubSAPWS.asmx|產生的檔案。|  
|StubSAPWS.asmx.resx|產生的檔案。|  
|Web.config|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\StubWebServices\SAP\app_code  
  
|檔案|Description|  
|----------|-----------------|  
|assemblyinfo.cs|組件資訊檔。|  
|global.asax.cs|產生的檔案。|  
|stubsapws.asmx.cs|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\StubWebServices\StubSAPCall  
  
|檔案|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|組件資訊檔。|  
|Exceptions.cs|定義虛設常式 SAP 呼叫逾時例外狀況的 C# 程式碼。|  
|StubSAPCall.csproj|C# 專案檔。|  
|StubSAPCallHelper.cs|用於呼叫虛設常式 SAP Web 服務之協助程式組件的 C# 程式碼。|  
|StubSAPWSProxy.cs|用於呼叫虛設常式 SAP Web 服務之協助程式組件的 C# 程式碼。|  
  
 中的檔案\<安裝目錄\>\BTSSoln\Utilities  
  
|檔案|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|組件資訊檔。|  
|CustomerServiceHelper.cs|用於協助程式方法與類別的 C# 程式碼。|  
|ReceivePipelineHelper.cs|用於呼叫來自協調流程之管線的協助程式組件的 C# 程式碼。|  
|Utilities.csproj|C# 專案檔。|  
  
 中的檔案\<安裝目錄\>\MFAccess  
  
|檔案|Description|  
|----------|-----------------|  
|Microsoft.Samples.BizTalk.WoodgroveBank.MainframeAccess.sln|Visual Studio 方案檔。|  
|SetupMFAccess.bat|建立解決方案之大型主機存取元件的批次檔。|  
  
 中的檔案\<安裝目錄\>\MFAccess\HISTIComponent  
  
|檔案|Description|  
|----------|-----------------|  
|bizcbl.txt|在大型主機上執行的 COBOL 程式。|  
|HISTIComponent.tiproj|交易整合器專案檔。|  
|MainFrameProgramVTCS2Description.txt|交易整合器匯出檔案。|  
|SOHISTIUsingCOM.TLB|型別程式庫。|  
  
 中的檔案\<安裝目錄\>\MFAccess\HISTISimpleTester  
  
|檔案|Description|  
|----------|-----------------|  
|App.ico|圖示檔案|  
|AssemblyInfo.cs|組件資訊檔。|  
|Form1.cs|測試大型主機連線的 Windows Forms 程式。|  
|Form1.resx|資源檔|  
|HISTISimpleTester.csproj|C# 專案檔。|  
|Interop.SOHISTIUsingCOM.dll.reg|DLL 登錄檔案。|  
  
 中的檔案\<安裝目錄\>\MFAccess\PendingTransactions  
  
|檔案|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|組件資訊檔。|  
|Global.asax|產生的檔案。|  
|Global.asax.cs|產生的檔案。|  
|Global.asax.resx|產生的檔案。|  
|PendingTransactions.csproj|C# 專案檔。|  
|PendingTransactions.csproj.webinfo|產生的檔案。|  
|PendTransWS.asmx|產生的檔案。|  
|PendTransWS.asmx.cs|產生的檔案。|  
|PendTransWS.asmx.resx|產生的檔案。|  
|Web.config|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\MFAccess\SchemaClasses  
  
|檔案|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|組件資訊檔。|  
|BAPI_BANKACCT_GET_DETAIL.cs|從對應的結構描述 (.xsd) 檔案產生的 C# 類別。|  
|CustomerServiceRequest.cs|從對應的結構描述 (.xsd) 檔案產生的 C# 類別。|  
|CustomerServiceResponse.cs|從對應的結構描述 (.xsd) 檔案產生的 C# 類別。|  
|LastPaymentRequest.cs|從對應的結構描述 (.xsd) 檔案產生的 C# 類別。|  
|LastPaymentResponse.cs|從對應的結構描述 (.xsd) 檔案產生的 C# 類別。|  
|PendingTransactionsRequest.cs|從對應的結構描述 (.xsd) 檔案產生的 C# 類別。|  
|PendingTransactionsResponse.cs|從對應的結構描述 (.xsd) 檔案產生的 C# 類別。|  
|SchemaClasses.csproj|C# 專案檔。|  
  
## <a name="see-also"></a>請參閱  
 [元件的服務導向解決方案](../core/components-of-the-service-oriented-solution.md)   
 [服務導向解決方案參考](../core/service-oriented-solution-reference.md)