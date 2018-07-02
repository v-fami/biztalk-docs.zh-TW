---
title: 建立傳送至 SWIFT 的 FRR 傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, send ports
- send ports, creating
- FRR, creating send ports
ms.assetid: 1ad766db-d1da-437a-a520-a3b04f0695c4
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1583072986eba20b5a0202e6973a5c08095aab01
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972319"
---
# <a name="creating-the-frr-send-port-for-sending-to-swift"></a>建立傳送至 SWIFT 的 FRR 傳送埠
若要執行 FIN 回應對帳，您必須建立傳送埠傳送訊息，以從[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]SWIFT 網路。  

 **摘要**  

 建立傳送埠的下列屬性和元件：  


|     屬性/元件      |                                                               設定                                                                |
|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
|          傳送埠          |                                                         靜態單向連接埠                                                          |
|       傳輸類型        |                                                               MQSeries                                                               |
| 佇列定義 (MQSeries) |                                                 MQSeries server 佇列管理員佇列                                                  |
|        傳送管線        | [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]建立 FRR 傳送管線 |
|           篩選           |                                                     下表所示                                                      |

### <a name="to-add-a-custom-send-port-for-sending-to-swift"></a>若要新增自訂的傳送埠傳送至 SWIFT  

1. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態一個 waySend 埠**。  

2. 在傳送埠屬性 對話方塊中，在**名稱**方塊中，輸入傳送埠，例如 FRRSWIFTSendPort 的名稱。  

3. 針對**型別**，選取**MQSeries**。  

4. 按一下 **設定**。  

5. 在 [MQSeries 傳輸屬性] 對話方塊中，按一下**佇列定義**，然後按一下省略符號 （...） 按鈕。  

6. 在 [佇列定義] 對話方塊中，輸入 MQSeries server、 佇列管理員和佇列。 按一下 [確定] 。  

7. 在 [MQSeries 傳輸屬性] 對話方塊中，確認內容會視需要。 按一下 [確定] 。  

   > [!NOTE]
   >  如需 MQSeries 傳輸屬性的詳細資訊，請參閱 MQSeries 文件。  

8. 在傳送埠屬性 對話方塊中，如**傳送處理常式**，確認已選取 biztalkserverapplication。  

9. 針對**傳送管線**，選取[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]建立 FRR 傳送管線。  

10. 按一下 **篩選器**左的窗格中，然後執行下列動作：  


    |   使用   |                            以進行此動作                             |
    |--------------|-------------------------------------------------------------------|
    | **屬性** |  選取  **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**。  |
    | **[運算子]** |                          選取  **==**。                           |
    |  **ReplTest1**   |                          型別**False**。                          |
    |  **群組**   |                          選取 **和**。                          |
    | **屬性** | 型別**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SwiftBound**。 |
    | **[運算子]** |                          選取  **==**。                           |
    |  **ReplTest1**   |                          型別 **，則為 True**。                           |


11. 按一下 **套用**，然後按一下**確定**。  

12. 以滑鼠右鍵按一下傳送埠，然後按一下**啟動**。
