---
title: "範例商務案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BTAHL7, business example
- examples, business processes
- health care organizations, business example
- business processes, example
ms.assetid: 54bfbe45-4638-4488-bbd8-c642926a35d3
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a74fafbac364469b1afdba5365c2af87cc4fa2d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sample-business-scenario"></a>範例商務案例
醫療保健處理程序通常很複雜，而且涉及許多系統。 範例是一位病患進入醫院，時發生的程序，並讓醫生傳送實驗室測試病患。 參與這個程序有五個合作對象：  
  
-   顧及醫生  
  
-   醫院註冊系統  
  
-   臨床訂單輸入系統  
  
-   實驗室系統  
  
-   計費系統  
  
 在此程序可能會執行下列步驟：  
  
1.  顧及家裡有醫生註冊病患。  
  
    1.  ADT ^ O04 註冊訊息廣播醫院註冊系統。  
  
    2.  ADT ^ 訂閱訊息，包括臨床訂單輸入系統和實驗室系統的所有部門都收到 O04 訊息。  
  
2.  家裡有醫生排序從實驗室設備診斷研究。  
  
    1.  ORM ^ O01 訂單訊息從臨床訂單輸入系統的商務規則驗證之後傳送。  
  
    2.  ORM ^ 實驗室系統收到 O01 訊息。  
  
3.  實驗室接收訂單，並傳回確認訊息。  
  
    1.  ORR ^ O02 訂單確認訊息傳送實驗室系統指出，可以執行順序。  
  
    2.  ORR ^ 臨床訂單輸入系統收到 O02 訊息。  
  
4.  完成測試時，實驗室會將結果傳送至家裡有醫生和其他部門。  
  
    1.  ORU ^ 從實驗室系統 R01 測試結果訊息傳送。  
  
    2.  ORU ^ R01 收到訊息時臨床訂單輸入系統和計費系統。  
  
    3.  介面引擎會送出電子郵件訊息中，以 doctor，收到其無線 PDA 的實驗室結果。  
  
## <a name="the-btahl7-solution"></a>BTAHL7 方案  
 以上所述的範例商務案例是需要整合醫療保健系統的範例。 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]與[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 提供此功能的下列功能的案例的解決方案：  
  
1.  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]整合的所有系統參與中樞-支點安排方式。 每個系統會直接與通訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 它們並沒有直接與彼此通訊。  
  
2.  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]原生處理 HL7 編碼訊息。 需要任何自訂程式碼。  
  
3.  ADT ^ O04 註冊訊息廣播給所有訂閱的系統。 發行者訂閱者的訊息模型[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]提供有彈性地設定和維護的訂閱訊息的系統清單。 您可以新增至系統，或它們從清單中刪除訂用帳戶而不會影響系統的其餘部分。  
  
4.  商務規則，用來驗證 ORM ^ 可以動態變更 O01 訂單訊息，而不會影響系統的其餘部分。  
  
5.  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可以設定為自動產生 ORR ^ O02 訂單 (ACK) 訊息。  
  
6.  如有必要，您可以任何與其他人進行傳送，訊息批次，並在收到的批次中處理它們。  
  
7.  您可以驗證所有的訊息在引擎也可以根據[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]HL7 組織發佈 2 X 結構描述。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何解決商務需求](../../adapters-and-accelerators/accelerator-hl7/how-biztalk-server-solves-the-business-need2.md)