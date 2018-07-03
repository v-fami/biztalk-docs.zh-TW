---
title: 步驟 8c： 設定 HI 系統的合作對象資訊 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4ac5c113-7ee7-4009-8ca3-d263f74c7a8d
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aba42674a78bbed850c0994ec23c477c36b29c2b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970823"
---
# <a name="step-8c-configure-party-information-for-the-hi-system"></a>步驟 8c： 設定 HI 系統的合作對象資訊
在此步驟中，您可以設定 HI 系統的合作對象資訊。  

### <a name="to-configure-the-hi-system-party-information"></a>若要設定 HI 系統的合作對象資訊  

1. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**合作對象**，指向**新增**，然後按一下**合作對象**。  

2. 在 [合作對象屬性] 對話方塊中，在**名稱**方塊中，輸入**Tutorial_HISystem**。  

3. 在主控台樹狀目錄中，按一下**傳送埠**。  

4. 在 傳送埠 窗格中，按一下 中的空白欄位**名稱**欄中，選取**Tutorial_MllpSend**，然後按一下**確定**。  

5. 按一下 **開始**，指向**程式**，指向**Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 設定總管**。  

6. 在 [BTAHL7 設定總管] 中，選取**MSH 對應**索引標籤，然後再執行下列動作：  


   | 使用  |                                             以進行此動作                                             |
   |-----------|----------------------------------------------------------------------------------------------------|
   | **MSH3**  | 型別**BTAHL7**， **IE**，並**UUID**第一次，第二個，，和第三個訊息方塊中，分別。 |
   | **MSH5**  | 型別**HI**，**系統**，並**GUID**第一次，第二個，，和第三個訊息方塊中，分別。 |
   | **MSH9**  |           型別**ADT**並**A04**在第一個和第二個訊息方塊中分別。            |
   | **MSH12** |                                           型別**2.4**。                                            |
   | **MSH15** |         選取  **SU**之後成功傳輸訊息的傳送通知。          |
   | **MSH16** |                            選取  **NE**永遠不會傳送通知。                            |


7. 按一下 **儲存**，然後關閉 BTAHL7 設定總管。  

   > [!NOTE]
   >  您不需要建立合作對象資訊 BTAHL7 介面引擎系統，因為並不需要在此案例的組態資訊。  

   請繼續進行[步驟 9： 重新啟動 BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server.md)。