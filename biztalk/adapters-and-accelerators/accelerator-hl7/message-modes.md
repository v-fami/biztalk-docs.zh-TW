---
title: 訊息模式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message modes, about message modes
- messages, message modes
- message modes, HL7 messages
ms.assetid: 2d832b67-6f0e-45e1-95ac-cb80b74a7831
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfce63f527dbe9643228b3b47a509b404e78c510
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009135"
---
# <a name="message-modes"></a>訊息模式
有兩個基本概念的基礎 HL7 的所有訊息。 這些概念解決不同的方式交換資料的獨立系統可以進行互動，並提供一段時間內的分散式的醫療保健系統支援的互通性需求的結構。 下面所列的概念定義 HL7 設計背後的基礎佈景主題：  
  
- **傳訊模式**。 三個基本的用途的資訊交換辨識： 廣播要求資訊 (interrogative)，（宣告） 的資訊，並要求系統採取的動作上 （必要）。 每個用途有其特定需求和訊息流程的模式。  
  
- **通知模式**。 需要支援緊密和鬆散結合的訊息的樣式。 HL7 的通知模式讓傳送應用程式需要回應的接收者，或是啟用為了保證訊息傳遞基礎的網路。  
  
- **當地語系化**。 需要支援本機的特定需求，讓站台特定的資料引入訊息規格的實體。  
  
- **發展**。 需要支援許多介面和許多應用程式的站台，藉由啟用標準版本之間的互通性。 這可讓實體階段介面升級，而不需要同時升級所有介面。  
  
  Microsoft BizTalk Accelerator for HL7 的下列函式 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 支援上述的需求：  
  
- HL7 通知模式。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 支援的原始通知模式藉由傳遞回原始訊息寄件者的應用程式通知。  
  
- 不同的傳訊模式。 這可讓廣播至多個目的地，並結合至相關聯的查詢回應的查詢。  
  
- 支援多種版本，包括 XML 和直立線符號分隔的編碼方式。  
  
- 若要啟用各種不同的環境 HL7 版本和升級之間的對應。  
  
- 協調流程中的當地語系化 （自訂）。  
  
- 若要支援偵錯和評估新的介面的工具。  
  
## <a name="see-also"></a>另請參閱  
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)   
 [使用 HL7 2.xml 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)   
 [訊息類型和事件](../../adapters-and-accelerators/accelerator-hl7/message-types-and-events.md)   
 [HL7 傳訊](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md)