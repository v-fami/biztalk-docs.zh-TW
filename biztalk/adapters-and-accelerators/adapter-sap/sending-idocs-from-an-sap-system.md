---
title: "從 SAP 系統在 BizTalk 中使用 mySAP 配接器傳送 Idoc |Microsoft 文件"
description: 
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aea8a5e9-d775-4d52-a434-c2908b53cd2d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63f7d1ccdaa8cb6a4ee12ad1cc4263c487a164c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sending-idocs-from-an-sap-system"></a>從 SAP 系統傳送 Idoc
SAP 系統從 SAP 系統傳送 IDOC 至外部應用程式上完成的高階工作。 連絡您的 SAP 系統管理員執行這些工作，或請參閱 SAP 指引。  
  
## <a name="send-an-idoc-from-sap"></a>從 SAP 傳送 IDOC  
  
1.  啟動 SAP GUI。  
  
2.  建立使用 BD54 交易的邏輯系統。  
  
3.  在 TCP/IP 連線使用 SM59 交易建立 RFC 目的地。  
  
4.  建立使用 WE21 交易的連接埠，並將它附加到最後一個步驟中建立的 RFC 目的地。  
  
5.  建立具有必要的訊息類型和 IDOC 類型使用 WE20 交易夥伴設定檔，並將其附加到最後一個步驟中建立的連接埠。  
  
6.  連接至使用銷售交易的連接埠的訊息類型，藉此維持分散式的模型。  
  
7.  產生內 SAP IDOC。 例如，使用 BD10 交易來觸發 MATMAS IDOC。 如需有關其他觸發程序特定的 Idoc 的交易資訊，請連絡 SAP 系統管理員。  

## <a name="view-transaction-ids-in-sap"></a>檢視 SAP 中的交易識別碼
當[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]tRFC 會叫用，或傳送 IDOC 到 SAP 系統，SAP 系統暫存器的交易識別碼 (TID) 回應。 在某些情況下，您可能需要知道已向 SAP 系統，以回應從呼叫 TID [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 例如，您可以疑難排解問題的 SAP 系統上識別工作 (LUW) 的邏輯單元。  
  
 若要檢視 TIDs SAP 系統中，您必須使用 SM58 交易。 請連絡您的 SAP 系統管理員，或請參閱 SAP 指引，如需有關此交易。 

## <a name="view-details-about-idocs-sent-and-received-from-sap"></a>檢視傳送和從 SAP 接收 Idoc 的詳細資料
使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，您可以傳送 IDOC 至 SAP 系統，或從 SAP 系統接收 IDOC。 若要追蹤的 SAP 系統的狀態和傳送或接收的 IDOC 資料的檢視，您可以使用 WE02 交易。 請連絡您的 SAP 系統管理員，或參閱 SAP 指引，如需有關此交易。  

  
## <a name="see-also"></a>另請參閱  
 [使用特定 SAP 配接器實例的 SAP GUI 執行工作](performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)