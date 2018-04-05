---
title: 商務程序管理解決方案的檔案庫存 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, file inventory
ms.assetid: 3efb7495-9543-4fe0-8f4b-26c19b3b6db9
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4cc187a96e7252fad7edacba10b7a3dcc39c1b33
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="file-inventory-for-the-business-process-management-solution"></a>商務程序管理解決方案的檔案庫存
本節列出商務程序管理解決方案的子目錄和原始程式檔。 「商務程序管理」方案原始程式檔的預設安裝目錄是 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios\BPM。 下表會取代此路徑與之前的描述\<安裝目錄\>。  
  
 中的檔案\<安裝目錄\>  
  
|檔案|Description|  
|----------|-----------------|  
|Microsoft.Samples.BizTalk.SouthridgeVideo.sln|Visual Studio 方案檔。|  
|readme.html|解決方案的讀我檔案。|  
|ReplacePKToken.vbs|在建立解決方案時，會修正解決方案檔案中公開金鑰 Token 的 VBScript。|  
|ReplacePKToken.wsf|用於 ReplacePKToken VBScript 的 Windows 指令碼檔案。|  
|SetupBPM.bat|建立公開金鑰、更新公開金鑰的參考，以及編譯解決方案。 如需部署解決方案的資訊，請參閱[部署商務程序管理解決方案](../core/deploying-the-business-process-management-solution.md)。|  
  
 中的檔案\<安裝目錄\>\BAM  
  
|檔案|Description|  
|----------|-----------------|  
|BAMServiceOrder.xls|用於 BAM 資料的 Excel 試算表。|  
|BAMServiceOrder.xml|定義 BAM 資料項目類型的結構描述。|  
  
 中的檔案\<安裝目錄\>\Bindings  
  
|檔案|Description|  
|----------|-----------------|  
|CableOrderAppBindings-test.xml|繫結檔案的測試版本**CableOrderApp**應用程式。|  
|CableOrderAppBindings.xml|繫結檔案**CableOrderAPP**應用程式。|  
|MessagingAppBindings-test.xml|繫結檔案的測試版本**MessagingApp**應用程式。|  
|MessagingAppBindings.xml|繫結檔案**MessagingApp**應用程式。|  
|OrderBrokerAppBindings-test.xml|繫結檔案的測試版本**OrderBrokerApp**應用程式。|  
|OrderBrokerAppBindings.xml|繫結檔案**OrderBrokerApp**應用程式。|  
  
 中的檔案\<安裝目錄\>\CableProvisioningSystemClient  
  
|檔案|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|模擬訂單系統的元件用戶端之組件檔案。|  
|CableProvisioningSystemClient.csproj|C# 專案檔。|  
|CPSClient.cs|用戶端的來源。 包含**OrderHandlerWrapper**類別程式碼。|  
|OrderException.cs|C# 類別定義檔**OrderException**。|  
  
 中的檔案\<安裝目錄\>\CableProvisioningSystemServer  
  
|檔案|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|模擬訂單系統的元件伺服器端之組件檔案。|  
|CableProvisioningSystemServer.csproj|C# 專案檔。|  
|CableProvisioningSystemServer.csproj.user|Visual Studio 專案使用者選項檔|  
|CPSServer.cs|伺服器的來源。|  
  
 中的檔案\<安裝目錄\>\CSRWebApp  
  
|檔案|Description|  
|----------|-----------------|  
|CSRMainForm.aspx|客戶服務輸入 ASP 表單。|  
|CSRMainForm.aspx.cs|表單背後的 C# 程式碼。|  
|Web.Config|表單的組態檔。|  
  
 中的檔案\<安裝目錄\>\CSRWebApp\App_WebReferences\SouthridgeVideo_OrderBroker  
  
|檔案|Description|  
|----------|-----------------|  
|orderbrokerorch_orderport.disco|Disco 檔案**OrderBroker**呈現為 web 服務。|  
|orderbrokerorch_orderport.discomap|產生的檔案。|  
|orderbrokerorch_orderport.wsdl|WSDL 檔案**OrderBroker**呈現為 web 服務。|  
  
 中的檔案\<安裝目錄\>\FacilitiesSimulator  
  
|檔案|Description|  
|----------|-----------------|  
|FacilitiesSimulator.csproj|功能模擬器的 C# 專案檔。|  
|FacilitiesSimulator.csproj.user|Visual Studio 專案使用者選項檔|  
|FacilitiesSimulatorForm.cs|功能模擬器的 C# 程式碼。|  
|FacilitiesSimulatorForm.resx|資源檔。|  
  
 中的檔案\<安裝目錄\>\HistoryDB  
  
|檔案|Description|  
|----------|-----------------|  
|CreateDatabase.cmd|驅動建立歷程記錄資料庫的 SQL 檔案之檔案。|  
|SouthridgeVideoHistory.sql|建立歷程記錄資料庫的 SQL 命令。|  
  
 中的檔案\<安裝目錄\>\IOperationsSystem  
  
|檔案|Description|  
|----------|-----------------|  
|IOperationsSystem.cs|作業系統的介面定義。|  
|IOperationsSystem.csproj|C# 專案檔。|  
|IOperationsSystem.csproj.user|Visual Studio 專案使用者選項檔|  
  
 中的檔案\<安裝目錄\>\IOrderHandler  
  
|檔案|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|組件資訊檔。|  
|IOrderHandler.cs|介面定義**OrderHandler**。|  
|IOrderHandler.csproj|C# 專案檔。|  
  
 中的檔案\<安裝目錄\>\Maps  
  
|檔案|Description|  
|----------|-----------------|  
|Maps.btproj|BizTalk 專案檔。|  
|Order_To_SQLUpdateStatus.btm|用來將訂單轉換為訊息以更新狀態的對應。|  
  
 中的檔案\<安裝目錄\>\MessagingSchemas  
  
|檔案|Description|  
|----------|-----------------|  
|ErrorEnvelope.xsd|定義錯誤訊息的信封之結構描述。|  
|MessagingSchemas.btproj|BizTalk 專案檔。|  
|OrderEnvelope.xsd|定義訂單的信封之結構描述。|  
|OrderStatusEnvelope.xsd|定義訂單狀態訊息的信封之結構描述。|  
|SQLUpdateStatus.xsd|定義 SQL 狀態更新訊息的信封之結構描述。|  
  
 中的檔案\<安裝目錄\>\OperationsClient  
  
|檔案|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|組件資訊檔。|  
|OperationsClient.csproj|作業用戶端的 C# 專案。|  
|OpsClient.cs|作業用戶端的 C# 程式碼。|  
|OpsExceptions.cs|定義作業例外狀況的 C# 程式碼。|  
  
 中的檔案\<安裝目錄\>\OperationsHandler  
  
|檔案|Description|  
|----------|-----------------|  
|OperationsHandler.csproj|作業處理常式的 C# 專案檔。|  
|OpsHandler.cs|C# 程式碼**OpsHandler**。 使用**OpsClient**提出要求的操作系統。|  
  
 中的檔案\<安裝目錄\>\OperationsServer  
  
|檔案|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|組件資訊檔。|  
|OperationsServer.csproj|作業伺服器的 C# 專案檔。|  
|OpsServer.cs|C# 程式碼提供的執行個體的作業伺服器**OpsHandler**物件。|  
  
 中的檔案\<安裝目錄\>\OpsAdapter  
  
|檔案|Description|  
|----------|-----------------|  
|OpsAdapter.sln|Ops 配接器的 Visual Studio 解決方案。|  
|Register_Ops_Adapter.vbs|註冊 Ops 配接器的 VBScript。|  
|SetupOpsAdapter.bat|安裝 Ops 配接器的批次檔。|  
  
 中的檔案\<安裝目錄\>\OpsAdapter\IOpsAIC  
  
|檔案|Description|  
|----------|-----------------|  
|IOpsAIC.cs|C# 程式碼檔案的介面定義**初始化**和**Execute** Ops 配接器所呼叫的方法。|  
|IOpsAIC.csproj|C# 專案檔。|  
  
 中的檔案\<安裝目錄\>\OpsAdapter\OpsAdapterMgmt  
  
|檔案|Description|  
|----------|-----------------|  
|AdapterManagement.cs|Ops 配接器的 C# 原始程式檔。|  
|AssemblyInfo.cs|組件資訊檔。|  
|OpsAdapterMgmt.csproj|Ops 配接器的 C# 原始程式檔。|  
|TransmitHandler.xsd|Ops 配接器的 C# 原始程式檔。|  
|TransmitLocation.xsd|Ops 配接器的 C# 原始程式檔。|  
  
 中的檔案\<安裝目錄\>\OpsAdapter\OpsTxAdapter  
  
|檔案|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|組件資訊檔。|  
|OpsAdapterExceptions.cs|Ops 配接器的 C# 原始程式檔。|  
|OpsAdapterProperties.cs|Ops 配接器的 C# 原始程式檔。|  
|OpsTransmitAdapterBatch.cs|Ops 配接器的 C# 原始程式檔。|  
|OpsTransmitter.cs|Ops 配接器的 C# 原始程式檔。|  
|OpsTxAdapter.csproj|C# 專案檔。|  
  
 中的檔案\<安裝目錄\>\Orchestrations\CableOrderActions  
  
|檔案|Description|  
|----------|-----------------|  
|Activate.odx|**Activate**使用訂單處理階段協調流程。|  
|Analyze.odx|**分析**使用訂單處理階段協調流程。|  
|CableOrderActions.btproj|BizTalk 專案檔。|  
|Cancel.odx|**取消**使用訂單處理階段協調流程。|  
|Change.odx|**變更**使用訂單處理階段協調流程。|  
|Complete.odx|**完成**使用訂單處理階段協調流程。|  
|Validate.odx|**驗證**使用訂單處理階段協調流程。|  
  
 中的檔案\<安裝目錄\>\Orchestrations\CableOrderStage1  
  
|檔案|Description|  
|----------|-----------------|  
|CableOrder1.odx|第一個訂單處理階段的協調流程。|  
|CableOrderStage1.btproj|BizTalk 專案檔。|  
  
 中的檔案\<安裝目錄\>\Orchestrations\CableOrderStage2  
  
|檔案|Description|  
|----------|-----------------|  
|CableOrder2.odx|第二個訂單處理階段的協調流程。|  
|CableOrderStage2.btproj|BizTalk 專案檔。|  
  
 中的檔案\<安裝目錄\>\Orchestrations\OrderBroker  
  
|檔案|Description|  
|----------|-----------------|  
|OrderBroker.btproj|BizTalk 專案檔。|  
|OrderBroker.odx|**OrderBroker**協調流程。|  
  
 中的檔案\<安裝目錄\>\Orchestrations\OrderManager  
  
|檔案|Description|  
|----------|-----------------|  
|CheckInterrupt.odx|**CheckInterrupt**協調流程。|  
|ErrorHandler.odx|**ErrorHandler**協調流程。|  
|ExceptionHandler.odx|**ExceptionHandler**協調流程。|  
|Interrupter.odx|**Interrupter**協調流程。|  
|OrderManager.btproj|BizTalk 專案檔。|  
|OrderManager.odx|**OrderManager**協調流程。|  
  
 中的檔案\<安裝目錄\>\OrderBrokerMaps  
  
|檔案|Description|  
|----------|-----------------|  
|CSR_OrderRequest_To_Order.btm|用來將客戶服務訂單要求轉換為訂單訊息的對應。|  
|CSR_OrderRequest_To_Servicing_OrderRequest.btm|用來將客戶服務訂單要求轉換為提供給服務的訊息之對應|  
|CSR_OrderRequest_To_SQLHistoryInsert.btm|用來將客戶服務訂單要求轉換為歷程記錄更新訊息的對應。|  
|OrderBrokerMaps.btproj|BizTalk 專案檔。|  
|Order_To_CSR_OrderRequest.btm|用來將訂單訊息轉換為客戶服務訂單要求的對應。|  
  
 中的檔案\<安裝目錄\>\OrderBrokerSchemas  
  
|檔案|Description|  
|----------|-----------------|  
|CSR_OrderRequest.xsd|客戶服務要求的結構描述。|  
|OrderBrokerSchemas.btproj|BizTalk 專案檔。|  
|Servicing_OrderRequest.xsd|定義傳送至服務系統的訊息之結構描述。|  
|SQLHistoryInsert.xsd|SQL 歷程記錄訊息的結構描述。|  
  
 中的檔案\<安裝目錄\>\OrderBroker_Proxy  
  
|檔案|Description|  
|----------|-----------------|  
|Global.asax|產生的檔案。|  
|Index.htm|產生的檔案。|  
|OrderBrokerOrch_OrderPort.asmx|產生的檔案。|  
|Web.config|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\OrderBroker_Proxy\App_Code  
  
|檔案|Description|  
|----------|-----------------|  
|DataTypes.cs|產生的檔案。|  
|OrderBrokerOrch_OrderPort.asmx.cs|產生的檔案。|  
  
 中的檔案\<安裝目錄\>\OrderHandler  
  
|檔案|Description|  
|----------|-----------------|  
|OrderHandler.cs|C# 程式碼**OrderHandler**物件。|  
|OrderHandler.csproj|C# 專案檔。|  
  
 中的檔案\<安裝目錄\>\Rules  
  
|檔案|Description|  
|----------|-----------------|  
|DecodeAndValidateOrderRules.xml|商務規則引擎的規則檔案。|  
  
 中的檔案\<安裝目錄\>\SampleMessages  
  
|檔案|Description|  
|----------|-----------------|  
|CSR_OrderRequest.xml|客戶服務訂單要求範例。|  
|OrderEnvelope.xml|訂單信封範例。|  
  
 中的檔案\<安裝目錄\>\SchemaClasses  
  
|檔案|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|組件資訊檔。|  
|InternalMessages.cs|定義用來在解決方案元件之間通訊的訊息之類別的 C# 程式碼。|  
|SchemaClasses.csproj|C# 專案檔。|  
  
 中的檔案\<安裝目錄\>\Schemas  
  
|檔案|Description|  
|----------|-----------------|  
|Order.xsd|訂單訊息的結構描述。|  
|OrderPropertySchema.xsd|訂單訊息的升級屬性結構描述。|  
|Schemas.btproj|BizTalk 專案檔。|  
  
 中的檔案\<安裝目錄\>\Scripts  
  
|檔案|Description|  
|----------|-----------------|  
|CleanDirs.cmd|用來刪除搭配檔案使用之目錄的命令檔，僅適用於測試版本的解決方案。|  
|CreateAppReferences.vbs|建立應用程式參考的 VBScript。|  
|CreateQueues.vbs|建立 MSMQ 佇列的 VBScript。|  
|CreateSouthridgeVideoApplication.cmd|在 SSO 組態存放區建立組態值的命令檔。|  
|CreateTestDirectories.cmd|建立測試版本解決方案目錄的命令檔。|  
|DeployBPM.cmd|部署解決方案的命令檔。|  
|regac.bat|在全域組件快取 (GAC) 中註冊組件的批次檔。|  
|SouthridgeVideoSSOConfiguration.xml|包含初始 SSO 組態值的檔案。|  
  
 中的檔案\<安裝目錄\>\ServiceLevelTracking  
  
|檔案|Description|  
|----------|-----------------|  
|Activity_CustomerOrderRequest.cs|定義客戶訂單要求 BAM 活動的 C# 程式碼。|  
|Activity_OrderManager.cs|定義訂單管理員 BAM 活動的 C# 程式碼。|  
|Activity_ServiceOrderRequest.cs|定義服務訂單要求 BAM 活動的 C# 程式碼。|  
|ServiceLevelTracking.cs|定義活動之抽象基底類別的 C# 程式碼。|  
|ServiceLevelTracking.csproj|C# 專案檔。|  
  
 中的檔案\<安裝目錄\>\Utilities  
  
|檔案|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|組件資訊檔。|  
|CableOrderException.cs|定義電報訂單例外狀況類別的 C# 程式碼。|  
|Helper.cs|各種協助程式類別與方法的 C# 程式碼。|  
|Recaller.cs|C# 程式碼**Recaller**物件。|  
|SSOConfigHelper.cs|SSO 組態協助程式物件與方法的 C# 程式碼。|  
|Utilities.csproj|C# 專案檔。|  
  
## <a name="see-also"></a>請參閱  
 [商務程序管理解決方案參考](../core/business-process-management-solution-reference.md)   
 [商務程序管理解決方案的元件](../core/components-of-the-business-process-management-solution.md)