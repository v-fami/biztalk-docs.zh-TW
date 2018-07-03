---
title: 啟用多個接收單一訊息中的交換 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c98bcd2e-495a-49d8-a471-6e23b1e161f9
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77af57fb4a72e2e0c039b512d4e6f30659ccedd5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006847"
---
# <a name="enabling-the-receiving-of-multiple-interchanges-in-a-single-message"></a>啟用接收單一訊息中的多重交換
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可以處理包含多個交換的訊息。 對於 X12 訊息，這類訊息會包含多重 ISA 標頭和 IEA 結尾。 對於 EDIFACT 訊息，這類訊息會包含多重 UNA/UNB 標頭和 UNZ 結尾。  
  
 若要讓 EDI 解譯器在 EdiReceive 或 AS2EdiReceive 管線，以剖析單一訊息中的多個交換，您必須設定**DetectMID**管線屬性 **，則為 True**。 (MID 表示多重交換解譯)。根據預設，此屬性是設定為 True。  
  
 當包含 EDI 解譯器的接收管線收到具有多重交換的訊息時，解譯器會剖析交換標頭到交換結尾的每個交換。 這項處理會根據下列規則執行：  
  
- 相同訊息中的所有交換必須是相同的編碼類型 (X12 或 EDIFACT)。 如果訊息包含多個編碼類型的交換，EDI 解譯器會處理與訊息中第一個交換編碼類型相同的所有交換。 解譯器會忽略與第一個交換的編碼類型不同的所有交換。  
  
- EDI 解譯器會忽略某個交換的交換結尾與下一個交換的交換標頭之間的任何字元。  
  
- 如果您啟用選取的驗證**驗證失敗時捨棄訊息**或**驗證失敗時保留訊息**屬性，接收埠，然後[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]將如果多個訊息的交換中的任何一個失敗時，請擱置整個訊息。  
  
- 如果啟用驗證，而且相同訊息中的任何一個交換未解析為協議，然後在訊息中的所有交換將遭都擱置，並沒有通知就會傳回，即使這些交換確實可解析為協議.  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-enable-the-receiving-of-multiple-interchanges-in-a-message"></a>若要啟用接收單一訊息中的多重交換  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下**接收位置**節點，以滑鼠右鍵按一下您要啟用成接收多個接收位置交換在單一訊息中，然後按一下  **屬性**。  
  
2. 按一下接收管線 (必須是 EdiReceive 或 AS2EdiReceive) 旁的省略符號。  
  
3. 在 [**設定管線**] 對話方塊中，將**DetectMID**管線屬性 **，則為 True**。  
  
4. 按一下  **確定**，然後按一下**確定**一次。  
  
## <a name="see-also"></a>另請參閱  
 [設定 EDI 解決方案的連接埠](../core/configuring-ports-for-an-edi-solution.md)