---
title: "訊息內容屬性來接收 Idoc |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDOCs, message context properties for receiving
ms.assetid: fadb2284-2f55-49c2-bae9-95325f1be539
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca289e37cac15972e75c69d7ad20928b72911963
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-context-properties-for-receiving-idocs"></a>訊息內容屬性，用於接收 Idoc
接收 IDOC 使用 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]、[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援下列的訊息內容屬性。  
  
 **IDOC 控制記錄的屬性。**  
  
-   **TABNAM** -資料表結構的名稱  
  
-   **MANDT** -用戶端  
  
-   **DOCNUM** -IDOC 號碼  
  
-   **DOCREL** -SAP IDOC 版本  
  
-   **狀態**-IDOC 的狀態  
  
-   **直接**-方向  
  
-   **OUTMOD** -輸出模式  
  
-   **表現**-覆寫輸入處理中  
  
-   **測試**-測試旗標  
  
-   **IDOCTYP** -基本類型的名稱  
  
-   **CIMTYP** -擴充功能 （客戶定義）  
  
-   **MESTYP** -訊息類型  
  
-   **MESCOD** -訊息代碼  
  
-   **MESFCT** -訊息函式  
  
-   **STD** -EDI 標準，旗標  
  
-   **STDVRS** -EDI 標準、 版本和版次  
  
-   **STDMES** -EDI 訊息類型  
  
-   **SNDPOR** -寄件者的連接埠 （SAP 系統，外部子系統）  
  
-   **SNDPRT** -夥伴寄件者的類型  
  
-   **SNDPFC** -夥伴寄件者的函式  
  
-   **SNDPRN** -合作夥伴的寄件者數目  
  
-   **SNDSAD** -寄件者地址 (SADR)  
  
-   **SNDLAD** -寄件者的邏輯位址  
  
-   **RCVPOR** -接收埠  
  
-   **RCVPRT** -夥伴類型的接收器  
  
-   **RCVPFC** -合作夥伴的收件者的函式  
  
-   **RCVPRN** -合作夥伴的收件者數目  
  
-   **RCVSAD**位收件者地址 (SADR)  
  
-   **RCVLAD**位收件者的邏輯位址  
  
-   **CREDAT** -建立  
  
-   **CRETIM** -建立時間  
  
-   **REFINT** -傳輸檔案 （EDI 交換）  
  
-   **REFGRP** -訊息群組 （EDI 訊息群組）  
  
-   **REFMES** -訊息 （EDI 訊息）  
  
-   **ARCKEY** -訊息外部封存金鑰  
  
-   **序列**-序列化  
  
-   **DOCTYP** -IDOC 類型 （這僅提供 EDI_DC。 應該會出現在內容屬性，但應該只升級為版本 2 Idoc）  
  
 **TID** – 代表 SAP 系統所傳送的連入 TRFC 呼叫 TID。  
  
 **GUID** – 代表 GUID 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會在內部使用。 這會有一對一的對應，與從 SAP 系統接收 TID。  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)