---
title: 範例商務案例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BTAHL7, business example
- examples, business processes
- health care organizations, business example
- business processes, example
ms.assetid: 54bfbe45-4638-4488-bbd8-c642926a35d3
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6b88bd76a1fac2ebfa5c2f75a6abbf78aab75b7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966903"
---
# <a name="sample-business-scenario"></a>商務案例範例
醫療保健的程序通常很複雜，而且牽涉到許多系統。 範例是發生於某個病患進入醫院中，程序，並讓醫生傳送實驗室測試病患。 參與此程序有五個合作對象：  
  
- 參加醫生  
  
- 醫院註冊系統  
  
- 臨床訂單輸入系統  
  
- 實驗室系統  
  
- 計費系統  
  
  在此程序可能會執行下列步驟：  
  
1.  參加醫生註冊病患。  
  
    1.  ADT ^ O04 註冊訊息廣播醫院註冊系統。  
  
    2.  ADT ^ 訂閱訊息，包括臨床訂單輸入系統和實驗室系統的所有部門都收到 O04 訊息。  
  
2.  醫生排序從實驗室設備的診斷研究。  
  
    1.  ORM ^ O01 訂單訊息會從臨床訂單輸入系統的商務規則驗證之後傳送。  
  
    2.  ORM ^ 與實驗系統收到 O01 訊息。  
  
3.  實驗室環境接收訂單，並會傳回確認。  
  
    1.  ORR ^ O02 訂單確認訊息系統傳送的實驗室，表示可以執行的順序。  
  
    2.  ORR ^ 臨床訂單輸入系統收到 O02 訊息。  
  
4.  測試完成時，實驗室環境會將結果傳送至醫生和其他部門。  
  
    1.  ORU ^ R01 測試結果的訊息傳來與實驗系統。  
  
    2.  ORU ^ R01 收到訊息時臨床訂單輸入系統和計費系統。  
  
    3.  介面引擎會送出電子郵件訊息中，醫生，他無線 PDA 的實驗室結果會接收到。  
  
## <a name="the-btahl7-solution"></a>BTAHL7 方案  
 以上所述的範例商務案例是健康照護系統整合所需的範例。 Microsoft BizTalk Accelerator for HL7 MicrosoftBizTalk 伺服器 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 提供的解決方案，此案例中，具有下列功能：  
  
1. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 將所有參與中樞-支點安排系統相整合。 每個系統會直接與通訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 它們不必向彼此直接通訊。  
  
2. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 原生處理 HL7 編碼訊息。 需要任何自訂程式碼。  
  
3. ADT ^ O04 註冊訊息廣播給所有訂閱的系統。 發行者訂閱傳訊模型[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]提供設定和維護的訂閱訊息的系統清單中的彈性。 您可以新增至系統，或刪除這些訂用帳戶清單中，而不會影響系統的其餘部分。  
  
4. 商務規則，用來驗證 ORM ^ 可以動態變更 O01 訂單訊息，而不會影響系統的其餘部分。  
  
5. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 可以設定為自動產生 ORR ^ O02 訂單 (ACK) 訊息。  
  
6. 如有必要，您可以任何與其他人進行傳送，訊息批次，並在收到的批次中處理它們。  
  
7. 您可以驗證所有的訊息引擎中，而是針對[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]HL7 組織發佈 2 X 結構描述。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何解決商務需求](../../adapters-and-accelerators/accelerator-hl7/how-biztalk-server-solves-the-business-need2.md)