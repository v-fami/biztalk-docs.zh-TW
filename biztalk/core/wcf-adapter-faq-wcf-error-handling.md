---
title: "WCF 配接器 FAQ: WCF 錯誤處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fdbd1ea6-4898-415c-ac5e-f804565759a8
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efbac0b7aaffd6121cba406031a8330cfd5bbf2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-adapter-faq-wcf-error-handling"></a>WCF 配接器 FAQ: WCF 錯誤處理
## <a name="how-do-the-wcf-adapters-handle-errors-and-soap-faults-during-message-processing"></a>WCF 配接器如何處理錯誤和 SOAP 錯誤訊息處理期間？  
 針對接收位置，您可以設定下的兩個錯誤處理選項的其中一個**錯誤處理**區段**訊息**索引標籤中**傳輸屬性**對話方塊方塊。  
  
 如果**擱置失敗的要求訊息**選取選項，則會擱置內送要求訊息是否應該有接收管線中的處理失敗或路由訊息的失敗。 這可讓寄件者的訊息至 BizTalk Server 傳輸成功與接收通知 (ACK) 訊息。 BizTalk Server 會擱置訊息和記錄的失敗訊息的完整的錯誤記錄。 不過，它也不會傳送訊息的例外狀況傳回給傳送者在此情況下。 這適用於單向連接埠，並且會傳送通知，如果選取此選項，如果未選取將 NACK。 雙向連接埠，如果處理失敗，BizTalk 將會永遠收到 NACK。  
  
 不過，如果用戶端必須能夠存取失敗的例外狀況中，選取**錯誤中包含例外狀況詳細資料**選項。 選取時，這會傳回 SOAP 錯誤給呼叫者發生處理錯誤。 這等同於"IncludeExceptionDetailsInFaults"serviceDebug 行為指定為 True 上**行為**Wcf-custom 或 Wcf-customisolated 配接器 索引標籤。 詳細的例外狀況現在傳送到用戶端。 這個選項會更實際且安全的作法是在比生產環境中的應用程式的開發期間使用，因為內部錯誤訊息最有可能不應傳送給服務的呼叫端。  
  
 針對雙向傳送埠，您可以選擇是否要透過將轉送入原始呼叫端的 SOAP 錯誤訊息為請求-回應傳送埠選取**傳播錯誤訊息**。 如果未選取此選項，將第一次，產生的 NACK BizTalk Server，然後再擱置訊息。 如果已選取，BizTalk Server 會將視為有效的 WCF 回應訊息的訊息從外部服務，將會暫止的回應訊息，因為它會傳播。  
  
## <a name="how-do-the-wcf-adapters-handle-message-transmission-timing-issues"></a>WCF 配接器如何處理訊息傳輸的時間問題？  
 您可以使用來控制 WCF 配接器的時間問題**繫結**索引標籤中**傳輸屬性** 對話方塊。 這些設定**開啟**，**傳送**，和**關閉等候逾時**。 （還有您可以使用自訂配接器設定的接收逾時。）這些值分別為開啟、 傳送的通道和通道關閉 （和接收的自訂） 的時間才能完成作業。 所有三個預設，為一分鐘的最小到最大 23:59 之間的期間。