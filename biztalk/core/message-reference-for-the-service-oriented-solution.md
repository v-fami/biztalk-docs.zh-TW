---
title: "訊息參考服務導向解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: service solution tutorial, message reference
ms.assetid: 47b56d83-799d-444d-b7ef-c2db56a0e470
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d970b34874d893b9c110f360abc27336c4cba80d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-reference-for-the-service-oriented-solution"></a>服務導向解決方案的訊息參考
本節列出解決方案中每個協調流程所用的訊息與訊息類型。 依應用程式版本列出訊息與類型。  
  
## <a name="adapter-version"></a>配接器版本  
 在資料表中， \<SolutionPrefix > 取代 Microsoft.Samples.BizTalk.WoodgroveBank，以協助格式化表格。  
  
 協調流程、訊息及類型如下：  
  
|協調流程|訊息|訊息類型|  
|-------------------|-------------|------------------|  
|CustomerService.odx|LastPaymentRequest|\<SolutionPrefix >。Schemas.LastPaymentRequest|  
|CustomerService.odx|LastPaymentResponse|\<SolutionPrefix >。Schemas.LastPaymentResponse|  
|CustomerService.odx|PendingTransactionsWSRequest|\<SolutionPrefix >。Orchestrations.Adapter.PendTransWS.PendingTransactionsWebService_。GetPendingTransactions_request|  
|CustomerService.odx|PendingTransactionsWSResponse|\<SolutionPrefix >。Orchestrations.Adapter.PendTransWS.PendingTransactionsWebService_。GetPendingTransactions_response|  
|CustomerService.odx|CreditLimitRequest|\<SolutionPrefix >。Schemas.BAPI_BANKACCT_GET_DETAIL。BAPI_BANKACCT_GET_DETAIL_Request|  
|CustomerService.odx|CreditLimitResponse|\<SolutionPrefix >。Schemas.BAPI_BANKACCT_GET_DETAIL。BAPI_BANKACCT_GET_DETAIL_Response|  
|CustomerService.odx|PendingTransactionsRequest|\<SolutionPrefix >。Schemas.PendingTransactionsRequest|  
|CustomerService.odx|PendingTransactionsResponse|\<SolutionPrefix >。Schemas.PendingTransactionsResponse|  
|CustomerService.odx|StubSAPWebServiceRequest|\<SolutionPrefix >。Orchestrations.Adapter.StubSAPWS.StubSAPWS_。GetAccountDetails_request|  
|CustomerService.odx|StubSAPWebServiceResponse|\<SolutionPrefix >。Orchestrations.Adapter.StubSAPWS.StubSAPWS_。GetAccountDetails_response|  
|CustomerService.odx|CustomerServiceRequest|\<SolutionPrefix >。Schemas.CustomerServiceRequest|  
|CustomerService.odx|CustomerServiceResponse|\<SolutionPrefix >。Schemas.CustomerServiceResponse|  
|CustomerServiceNativeRequestResponse.odx|CustomerServiceRequest|\<SolutionPrefix >。Schemas.CustomerServiceRequest|  
|CustomerServiceNativeRequestResponse.odx|CustomerServiceResponse|\<SolutionPrefix >。Schemas.CustomerServiceResponse|  
|CustomerServiceReceiveSend.odx|CustomerServiceResponse2|\<SolutionPrefix >。Schemas.CustomerServiceResponse|  
|CustomerServiceReceiveSend.odx|CustomerServiceResponse|\<SolutionPrefix >。Schemas.CustomerServiceResponse|  
|CustomerServiceReceiveSend.odx|CustomerServiceRequest|\<SolutionPrefix >。Schemas.CustomerServiceRequest|  
  
## <a name="adapter-with-sap-version"></a>含有 SAP 版本的配接器  
 在資料表中， \<SolutionPrefix > 取代 Microsoft.Samples.BizTalk.WoodgroveBank，以協助格式化表格。  
  
 協調流程、訊息及類型如下：  
  
|協調流程|訊息|訊息類型|  
|-------------------|-------------|------------------|  
|CustomerService.odx|LastPaymentRequest|\<SolutionPrefix >。Schemas.LastPaymentRequest|  
|CustomerService.odx|LastPaymentResponse|\<SolutionPrefix >。Schemas.LastPaymentResponse|  
|CustomerService.odx|PendingTransactionsWSRequest|\<SolutionPrefix >。Orchestrations.Adapter.PendTransWS.PendingTransactionsWebService_。GetPendingTransactions_request|  
|CustomerService.odx|PendingTransactionsWSResponse|\<SolutionPrefix >。Orchestrations.Adapter.PendTransWS.PendingTransactionsWebService_。GetPendingTransactions_response|  
|CustomerService.odx|CreditLimitRequest|\<SolutionPrefix >。Schemas.BAPI_BANKACCT_GET_DETAIL。BAPI_BANKACCT_GET_DETAIL_Request|  
|CustomerService.odx|CreditLimitResponse|\<SolutionPrefix >。Schemas.BAPI_BANKACCT_GET_DETAIL。BAPI_BANKACCT_GET_DETAIL_Response|  
|CustomerService.odx|PendingTransactionsRequest|\<SolutionPrefix >。Schemas.PendingTransactionsRequest|  
|CustomerService.odx|PendingTransactionsResponse|\<SolutionPrefix >。Schemas.PendingTransactionsResponse|  
|CustomerService.odx|CustomerServiceRequest|\<SolutionPrefix >。Schemas.CustomerServiceRequest|  
|CustomerService.odx|CustomerServiceResponse|\<SolutionPrefix >。Schemas.CustomerServiceResponse|  
  
## <a name="inline-version"></a>內嵌版本  
 在資料表中， \<SolutionPrefix > 取代 Microsoft.Samples.BizTalk.WoodgroveBank，以協助格式化表格。  
  
 協調流程、訊息及類型如下：  
  
|協調流程|訊息|訊息類型|  
|--------------------|-------------|------------------|  
|CustomerService.odx|LastPaymentRequest|\<SolutionPrefix >。Schemas.LastPaymentRequest|  
|CustomerService.odx|LastPaymentResponse|\<SolutionPrefix >。Schemas.LastPaymentResponse|  
|CustomerService.odx|PendingTransactionsWSRequest|\<SolutionPrefix >。Schemas.PendingTransactionsRequest|  
|CustomerService.odx|PendingTransactionsWSResponse|\<SolutionPrefix >。Schemas.PendingTransactionsResponse|  
|CustomerService.odx|CreditLimitRequest|\<SolutionPrefix >。Schemas.BAPI_BANKACCT_GET_DETAIL。BAPI_BANKACCT_GET_DETAIL_Request|  
|CustomerService.odx|CreditLimitResponse|\<SolutionPrefix >。Schemas.BAPI_BANKACCT_GET_DETAIL。BAPI_BANKACCT_GET_DETAIL_Response|  
|CustomerService.odx|LastPaymentRequestAfterSendPipeline|System.Xml.XmlDocument|  
|CustomerService.odx|LastPaymentResponseBeforeReceivePipeline|System.Xml.XmlDocument|  
|CustomerService.odx|CustomerServiceRequest|\<SolutionPrefix >。Schemas.CustomerServiceRequest|  
|CustomerService.odx|CustomerServiceResponse|\<SolutionPrefix >。Schemas.CustomerServiceResponse|  
|CustomerServiceNativeRequestResponse.odx|CustomerServiceRequest|\<SolutionPrefix >。Schemas.CustomerServiceRequest|  
|CustomerServiceNativeRequestResponse.odx|CustomerServiceResponse|\<SolutionPrefix >。Schemas.CustomerServiceResponse|  
|CustomerServiceReceiveSend.odx|CustomerServiceResponse2|\<SolutionPrefix >。Schemas.CustomerServiceResponse|  
|CustomerServiceReceiveSend.odx|CustomerServiceResponse|\<SolutionPrefix >。Schemas.CustomerServiceResponse|  
|CustomerServiceReceiveSend.odx|CustomerServiceRequest|\<SolutionPrefix >。Schemas.CustomerServiceRequest|  
  
## <a name="stub-version"></a>虛設常式版本  
 在資料表中， \<SolutionPrefix > 取代 Microsoft.Samples.BizTalk.WoodgroveBank，以協助格式化表格。  
  
 協調流程、訊息及類型如下：  
  
|協調流程|訊息|訊息類型|  
|-------------------|-------------|------------------|  
|CustomerService.odx|LastPaymentRequest|\<SolutionPrefix >。Schemas.LastPaymentRequest|  
|CustomerService.odx|LastPaymentResponse|\<SolutionPrefix >。Schemas.LastPaymentResponse|  
|CustomerService.odx|PendingTransactionsWSRequest|\<SolutionPrefix >。Orchestrations.Stubbed.StubPendTransWS.StubPendingTransactionsWebService_。GetPendingTransactions_request|  
|CustomerService.odx|PendingTransactionsWSResponse|\<SolutionPrefix >。Orchestrations.Stubbed.StubPendTransWS.StubPendingTransactionsWebService_。GetPendingTransactions_response|  
|CustomerService.odx|CreditLimitRequest|\<SolutionPrefix >。Schemas.BAPI_BANKACCT_GET_DETAIL。BAPI_BANKACCT_GET_DETAIL_Request|  
|CustomerService.odx|CreditLimitResponse|\<SolutionPrefix >。Schemas.BAPI_BANKACCT_GET_DETAIL。BAPI_BANKACCT_GET_DETAIL_Response|  
|CustomerService.odx|PendingTransactionsRequest|\<SolutionPrefix >。Schemas.PendingTransactionsRequest|  
|CustomerService.odx|PendingTransactionsResponse|\<SolutionPrefix >。Schemas.PendingTransactionsResponse|  
|CustomerService.odx|PaymentTrackerWSRequest|\<SolutionPrefix >。Orchestrations.Stubbed.StubPmntTrckWS.StubPaymentTrackerWebService_。GetLastPayments_request|  
|CustomerService.odx|PaymentTrackerWSResponse|\<SolutionPrefix >。Orchestrations.Stubbed.StubPmntTrckWS.StubPaymentTrackerWebService_。GetLastPayments_response|  
|CustomerService.odx|StubSAPWSRequest|\<SolutionPrefix >。Orchestrations.Stubbed.StubSAPWS.StubSAPWS_。GetAccountDetails_request|  
|CustomerService.odx|StubSAPWSResponse|\<SolutionPrefix >。Orchestrations.Stubbed.StubSAPWS.StubSAPWS_。GetAccountDetails_response|  
|CustomerService.odx|CustomerServiceRequest|\<SolutionPrefix >。Schemas.CustomerServiceRequest|  
|CustomerService.odx|CustomerServiceResponse|\<SolutionPrefix >。Schemas.CustomerServiceResponse|  
|CustomerServiceNativeRequestResponse.odx|CustomerServiceRequest|\<SolutionPrefix >。Schemas.CustomerServiceRequest|  
|CustomerServiceNativeRequestResponse.odx|CustomerServiceResponse|\<SolutionPrefix >。Schemas.CustomerServiceResponse|  
  
## <a name="see-also"></a>另請參閱  
 [服務導向解決方案參考](../core/service-oriented-solution-reference.md)