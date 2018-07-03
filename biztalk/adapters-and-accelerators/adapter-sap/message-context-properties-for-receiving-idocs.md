---
title: 接收 idoc 用的訊息內容屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDOCs, message context properties for receiving
ms.assetid: fadb2284-2f55-49c2-bae9-95325f1be539
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f99c403648ec2fae7fd9ee93f349f7c1fe69434
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999799"
---
# <a name="message-context-properties-for-receiving-idocs"></a>接收 idoc 用的訊息內容屬性
接收 IDOC 使用 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，則[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援下列的訊息內容屬性。  
  
 **IDOC 控制記錄的屬性。**  
  
- **TABNAM** -資料表結構的名稱  
  
- **MANDT** -用戶端  
  
- **DOCNUM** -IDOC 號碼  
  
- **DOCREL** -IDOC 的 SAP 版本  
  
- **狀態**-IDOC 的狀態  
  
- **直接**-方向  
  
- **OUTMOD** -輸出模式  
  
- **表現**-覆寫輸入處理中  
  
- **測試**-測試旗標  
  
- **IDOCTYP** -基本類型的名稱  
  
- **CIMTYP** -延伸模組 （由客戶定義）  
  
- **MESTYP** -訊息類型  
  
- **MESCOD** -訊息代碼  
  
- **MESFCT** -訊息函式  
  
- **STD** -EDI 標準的旗標  
  
- **STDVRS** -EDI 標準、 版本和版次  
  
- **STDMES** -EDI 訊息類型  
  
- **SNDPOR** -寄件者的連接埠 （SAP 系統，外部子系統）  
  
- **SNDPRT** -合作夥伴的寄件者的類型  
  
- **SNDPFC** -合作夥伴的寄件者的函式  
  
- **Sndprn 則**-合作夥伴的寄件者數目  
  
- **SNDSAD** -寄件者地址 (SADR)  
  
- **SNDLAD** -寄件者的邏輯位址  
  
- **RCVPOR** -接收埠  
  
- **RCVPRT** -接收者的夥伴類型  
  
- **RCVPFC** -合作夥伴的收件者的函式  
  
- **RCVPRN** -合作夥伴的收件者數目  
  
- **RCVSAD** -收件者地址 (SADR)  
  
- **RCVLAD** -收件者的邏輯位址  
  
- **CREDAT** -上建立  
  
- **CRETIM** -建立時間  
  
- **REFINT** -傳輸檔案 （EDI 交換）  
  
- **REFGRP** -訊息群組 （EDI 訊息群組）  
  
- **REFMES** -訊息 （EDI 訊息）  
  
- **ARCKEY** -機碼的外部訊息封存  
  
- **序列**-序列化  
  
- **DOCTYP** -IDOC 類型 （這僅適用於 EDI_DC。 應該會出現在內容屬性，但應該只升級為版本 2 Idoc）  
  
  **TID** – 表示 SAP 系統所傳送的連入的 TRFC 呼叫 TID。  
  
  **GUID** – 代表 GUID 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會在內部使用。 這有一對一的對應與 TID 來自 SAP 系統它。  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)