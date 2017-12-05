---
title: "EDIFACT CONTRL 通知 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95e1c244-d700-48d3-9416-032ead6d4d6d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ddbc35fecd2412632f0c4a81750a3662e6e7bf11
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="edifact-contrl-acknowledgment"></a>EDIFACT CONTRL 通知
CONTRL 通知 (ACK) 可以做為 EDIFACT 編碼訊息的技術和功能通知。 如果是做為技術通知，CONTRL 訊息會指示接收交換。 如果是做為功能通知，CONTRL 訊息會指示接收或拒絕已接收的交換、群組或訊息，並列出錯誤或不支援的功能。  
  
 完整的 CONTRL 訊息是做為功能通知。 技術通知會重複使用功能通知的區段。 如果您已在合作對象屬性中選取技術和功能通知，傳送合作對象或全域屬性，BizTalk Server 會產生兩則 CONTRL 訊息： 技術 CONTRL 通知和功能 CONTRL 通知。  
  
 CONTRL 通知符合 EFACT_<VERSION\<版本號碼\>number>_contrl.xsd 結構描述。  
  
## <a name="technical-acknowledgement"></a>技術通知  
 技術通知表示交換的接收者：  
  
-   已經接收主旨交換；  
  
-   確認已檢查主旨交換的部分，以便確保複製至報告 UCI 區段的資料元素句法正確；  
  
-   已經接受責任，會將主旨交換的其他部分，告知通知或拒絕的傳送者；  
  
-   已採取合理的預防措施，確保已將此等訊息通知傳送者。  
  
## <a name="functional-acknowledgement"></a>功能通知  
 功能通知表示交換的接收者：  
  
-   已經接收已通知交換的參考層級；  
  
-   已經檢查已通知參考層級內沒有嚴重的語法錯誤，以防進一步處理交換；  
  
-   已經檢查服務區段的所有已通知部分語意正確 (若無報告任何錯誤)；  
  
-   會遵守服務區段之已通知參考層級內所要求的動作；  
  
-   已經接受責任，若稍後在相關部分偵測到上述語法或語意錯誤，或該部分於已傳送的 CONTRL 訊息被通知之後，因為某些原因無法處理，不會以傳送 CONTRL 訊息的方式，而會以其他方式通知傳送者；  
  
-   已採取合理的預防措施，以確保偵測這類錯誤並已通知傳送者。  
  
 拒絕表示交換的接收者：  
  
-   因為 CONTRL 訊息內所述原因，無法通知主旨交換或其相關部分；  
  
-   不會針對主旨交換遭拒絕之部分內的商務資訊，採取任何進一步動作。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [EDIFACT CONTRL 訊息作為技術通知](../core/edifact-contrl-message-as-technical-acknowledgment.md)  
  
-   [EDIFACT CONTRL 訊息作為功能通知](../core/edifact-contrl-message-as-functional-acknowledgment.md)  
  
## <a name="see-also"></a>請參閱  
 [EDI 通知結構](../core/edi-acknowledgment-structure.md)