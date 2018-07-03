---
title: Samples3 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SDK samples
- examples, developing
- developing, examples
ms.assetid: b940111e-4f71-494b-b7a3-d2e8310bea51
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f509668bb8da8021b14a7252a3902cb01da9fd5a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006111"
---
# <a name="samples"></a>範例
這一節中包含範例說明 Microsoft®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]軟體開發套件 (SDK)。 並提供有關每個範例的詳細資訊，包括如何建置範例、如何執行範例以及可預期的結果。  

 這些範例包含在\<*磁碟機*\>: \Program Files\\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\ 資料夾。  

## <a name="in-this-section"></a>本節內容  

- 配接器範例資料夾  

  -   [ApplicationAdapter](../../adapters-and-accelerators/accelerator-rosettanet/applicationadapter.md)。 示範如何包含訊息通知機制。  

  -   [ValidationAdapter](../../adapters-and-accelerators/accelerator-rosettanet/validationadapter.md)。 示範如何在訊息上執行特殊驗證規則。  

- 傳訊範例資料夾  

  -   [FileTransport 範例](../../adapters-and-accelerators/accelerator-rosettanet/filetransport-sample.md)。 示範如何設定 BTARN 使用「檔案」傳輸埠。  

  -   [GetMessages 範例](../../adapters-and-accelerators/accelerator-rosettanet/getmessages-sample.md)。 示範如何從其中一個不可否認性資料表或商務營運系統 (LOB) 資料表擷取訊息。  

  -   [訊息提交 ASPX 範例](../../adapters-and-accelerators/accelerator-rosettanet/message-submission-aspx-sample.md)。 提供範例 .aspx 程式碼，以便將服務內容提交到私用程序， 同時提供 HTML，提交交易夥伴介面程序 (PIP) 動作訊息到該服務內容。  

  -   [追蹤範例](../../adapters-and-accelerators/accelerator-rosettanet/tracking-sample.md)。 提供範例 .aspx 程式碼，以檢視使用 BTARN 傳送和接收之訊息的狀態。  

- 協調流程範例資料夾  

  -   [使用商務規則的 3A4 私用回應者協調流程](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)。 示範如何使用將要求訊息轉換為回應訊息的對應來自動化涉及 PIP 的商務處理程序。  

  -   [雙向動作 PIPAutomation 協調流程](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md)。 示範如何以根據內送訊息類型自動決定回應訊息類型來自動化商務處理程序。  

  -   [3A2 要求至 3A2 回應的對應範例](../../adapters-and-accelerators/accelerator-rosettanet/3a2-request-to-3a2-response-map-sample.md)。 示範如何將 3A2 Request 結構描述對應到 3A2 Response 結構描述。  

  -   [3A4 要求至 3A4 回應的對應範例](../../adapters-and-accelerators/accelerator-rosettanet/3a4-request-to-3a4-response-map-sample.md)。 示範如何將 3A4 Request 結構描述對應到 3A4 Response 結構描述。  

  -   [PrivateInitiator 範例](../../adapters-and-accelerators/accelerator-rosettanet/privateinitiator-sample.md)。 示範如何建立啟動者私用程序的協調流程。  

  -   [PrivateResponder 範例](../../adapters-and-accelerators/accelerator-rosettanet/privateresponder-sample.md)。 示範如何建立回應者私用程序的協調流程。  

  -   [HubScenario 範例](../../adapters-and-accelerators/accelerator-rosettanet/hubscenario-sample.md)。 示範如何將傳送到中繼集線器的訊息轉換成要傳送給最後收件者的訊息。  

- 管線範例資料夾  

  - [傳送管線](../../adapters-and-accelerators/accelerator-rosettanet/send-pipeline.md)。 示範如何使用 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 管線將外送 XML 訊息處理成相等的 RNIF 訊息。  

  - [接收管線](../../adapters-and-accelerators/accelerator-rosettanet/receive-pipeline.md)。 示範如何使用 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 管線將內送 RNIF 訊息處理成相等的 XML 訊息。  

  - [訊息編輯器管線範例](../../adapters-and-accelerators/accelerator-rosettanet/message-editor-pipeline-sample.md)。 示範如何建立自訂管線元件來編輯內送訊息。  

- 結構描述範例資料夾  

  -   [結構描述範例](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md)。 描述 SDK 中所提供的範例結構描述，包括 PIP XML 結構描述、RosettaNet 下一代結構描述及 RNIF 結構描述。 包括使用者些結構描述之程序的指標。  

- Web 應用程式範例資料夾  

  -   [RNIFSend](../../adapters-and-accelerators/accelerator-rosettanet/rnifsend.md)。 示範如何自訂將 RNIF 訊息從啟動者傳送到回應者的 ASPX 頁面。  

  -   [RNIFReceive](../../adapters-and-accelerators/accelerator-rosettanet/rnifreceive.md)。 示範如何自訂在回應者接收 RNIF 訊息的 ASPX 頁面。  

- [停止和啟動協調流程、 傳送埠和接收位置，以程式設計方式](../../adapters-and-accelerators/accelerator-rosettanet/code-to-stop-and-start-orchestrations-send-ports-and-receive-locations.md)。 示範如何以群組或個別方式停止和啟動所有協調流程、傳送埠和接收位置。
