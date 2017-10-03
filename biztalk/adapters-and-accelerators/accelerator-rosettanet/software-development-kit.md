---
title: "RosettaNet 加速器，BizTalk Server 中的軟體開發套件 |Microsoft 文件"
description: "BizTalk Server 的 BTARN SDK 中的公用程式和範例清單"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36a1b283-26e1-407e-afc4-8879ef0d1672
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81bf0f7f0947875540d835ced3726224525f23a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="software-development-kit"></a>軟體開發套件
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]包括軟體開發套件 (SDK) 包含完整程式設計人員參考資料與指南。 此外，SDK 包含可以讓您的營運及後端整合更為容易的公用程式和範例。  
  
## <a name="utilities"></a>公用程式  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 包含下列範例：  
  
|公用程式|使用|  
|-------------|---------|  
|[BtarnClean](../../adapters-and-accelerators/accelerator-rosettanet/btarnclean.md)|從主機電腦的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 群組解除部署所有 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 成品|  
|[BtarnConfig](../../adapters-and-accelerators/accelerator-rosettanet/btarnconfig.md)|匯入或匯出組態資料|  
|[CertWizard](../../adapters-and-accelerators/accelerator-rosettanet/certwizard.md)|匯入憑證|  
|[LOBApplication](../../adapters-and-accelerators/accelerator-rosettanet/lobapplication.md)|提交動作或回應訊息至交易夥伴|  
|[LOBWebApplication](../../adapters-and-accelerators/accelerator-rosettanet/lobwebapplication.md)|從 ASPX 頁面提交動作或回應訊息至交易夥伴|  
|[回送](../../adapters-and-accelerators/accelerator-rosettanet/loopback.md)|產生回送協議，在一台電腦上設定 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]|  
|[訊息編輯器管線元件](../../adapters-and-accelerators/accelerator-rosettanet/message-editor-pipeline-component.md)|自動編輯傳送或接收管線內多部分訊息的任何部分|  
|[訊息偵測器管線元件](../../adapters-and-accelerators/accelerator-rosettanet/message-inspector-pipeline-component.md)|檢查多部分訊息的所有部分及訊息內容|  
|[SchemaValidator](../../adapters-and-accelerators/accelerator-rosettanet/schemavalidator.md)|疑難排解訊息執行個體的問題|  
|[TestCrypto](../../adapters-and-accelerators/accelerator-rosettanet/testcrypto.md)|疑難排解解密訊息時發生的錯誤|  
  
## <a name="samples"></a>範例  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 包含下列範例：  
  
|範例|示範|  
|------------|------------------|  
|[ApplicationAdapter](../../adapters-and-accelerators/accelerator-rosettanet/applicationadapter.md)|訊息到達時如何傳送通知|  
|[ValidationAdapter](../../adapters-and-accelerators/accelerator-rosettanet/validationadapter.md)|如何針對協調流程從交易夥伴接收到的訊息執行特殊驗證規則|  
|[FileTransport 範例](../../adapters-and-accelerators/accelerator-rosettanet/filetransport-sample.md)|如何使用檔案傳輸埠取代 SQL 傳輸埠|  
|[GetMessages 範例](../../adapters-and-accelerators/accelerator-rosettanet/getmessages-sample.md)|如何從可讀取表單的其中一個不可否認性資料表或 LOB 資料表擷取訊息|  
|[訊息提交 ASPX 範例](../../adapters-and-accelerators/accelerator-rosettanet/message-submission-aspx-sample.md)|如何提交服務內容至私用程序|  
|[追蹤範例](../../adapters-and-accelerators/accelerator-rosettanet/tracking-sample.md)|如何顯示訊息及程序的目前狀態|  
|[使用商務規則的 3A4 私用回應者協調流程](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)|如何實作回應者私用程序以整合商務規則|  
|[Double 動作 PIPAutomation 協調流程](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md)|如何實作協調流程自動產生雙向動作交易夥伴介面程序 (PIP) 的回應|  
|[3A2 要求至 3A2 回應的對應範例](../../adapters-and-accelerators/accelerator-rosettanet/3a2-request-to-3a2-response-map-sample.md)|如何對應 3A2 要求至 3A2 回應|  
|[3A4 要求至 3A4 回應的對應範例](../../adapters-and-accelerators/accelerator-rosettanet/3a4-request-to-3a4-response-map-sample.md)|如何對應 3A4 要求至 3A4 回應|  
|[PrivateInitiator 範例](../../adapters-and-accelerators/accelerator-rosettanet/privateinitiator-sample.md)|如何實作啟動者私用程序|  
|[PrivateResponder 範例](../../adapters-and-accelerators/accelerator-rosettanet/privateresponder-sample.md)|如何實作回應者私用程序|  
|[HubScenario 範例](../../adapters-and-accelerators/accelerator-rosettanet/hubscenario-sample.md)|如何管理中樞實例中的訊息傳輸|  
|[傳送管線](../../adapters-and-accelerators/accelerator-rosettanet/send-pipeline.md)|如何實作傳送管線|  
|[接收管線](../../adapters-and-accelerators/accelerator-rosettanet/receive-pipeline.md)|如何實作接收管線|  
|[訊息編輯器管線範例](../../adapters-and-accelerators/accelerator-rosettanet/message-editor-pipeline-sample.md)|如何修改內送訊息的內容|  
|[結構描述範例](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md)|如何修改結構描述|  
|[RNIFSend](../../adapters-and-accelerators/accelerator-rosettanet/rnifsend.md)|如何準備 RNIF 處理所需的訊息，並將訊息傳送至回應者端的 RNIFReceive.aspx 頁面|  
|[RNIFReceive](../../adapters-and-accelerators/accelerator-rosettanet/rnifreceive.md)|如何接收 RNIF 訊息，並準備訊息給 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 公開程序處理|  
|[停止和啟動協調流程、 傳送埠和接收位置，以程式設計的方式](../../adapters-and-accelerators/accelerator-rosettanet/code-to-stop-and-start-orchestrations-send-ports-and-receive-locations.md)|如何動態停止和啟動這些成品|  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Accelerator for RosettaNet 新增至 BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md)   
 [程式設計手冊](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)   
 [公用程式](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)   
 [範例](../../adapters-and-accelerators/accelerator-rosettanet/samples3.md)