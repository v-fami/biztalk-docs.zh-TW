---
title: 建立 FRR 用於接收來自 SWIFT 接收位置 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive locations, creating
- creating, receive locations
- FRR, creating receive locations
ms.assetid: e10857f4-21cb-4c09-8eed-cb6e9b0a0aa9
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e43ac2ac0fab9b2a29a44784032f9d3369833ae2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22210150"
---
# <a name="creating-the-frr-receive-location-for-receiving-from-swift"></a>建立 FRR 用於接收來自 SWIFT 接收位置
若要執行 FIN 回應重新調整，您需要建立成 A4SWIFT SWIFT 網路接收的訊息的接收位置。  
  
> [!NOTE]
>  建議您設定兩個接收位置接收訊息從 SAA： 一個用於接收取景位置調整/Nan，另一個收到的其他所有訊息。 若要設定兩個接收位置，您必須從 SAA 在兩個 MQSeries 佇列接收訊息： 一個用於取景位置調整/Nan，一個用於所有其他訊息類型。  
  
 **摘要**  
  
 建立具有下列屬性和元件的接收位置：  
  
|屬性/元件|設定|  
|-------------------------|-------------|  
|接收埠|單向連接埠|  
|傳輸類型|MQSeries|  
|佇列定義 (MQSeries)|MQSeries server<br />佇列管理員<br />佇列|  
|接收處理常式|BizTalkServerApplication|  
|接收管線|A4SWIFT 接收管線所建立的 FRR|  
  
### <a name="to-add-an-frr-receive-location-for-receiving-from-swift"></a>新增 FRR 接收位置接收來自 SWIFT  
  
1.  在 BizTalk Server 管理主控台中，展開**BizTalk Server 管理**， **BizTalk 群組**，**應用程式**，和**BizTalk 應用程式1**節點。  
  
2.  以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。  
  
3.  在 [接收埠屬性] 對話方塊中**名稱**方塊中，輸入接收埠，例如 FRRSWIFTReceivePort 的名稱。  
  
4.  按一下**套用**來繫結連接埠，然後按一下**確定**。  
  
5.  在管理主控台中，以滑鼠右鍵按一下**接收位置**，指向 **新增**，然後按一下 **單向接收位置**。  
  
6.  在 [選取接收埠] 對話方塊中，選取您剛才的接收埠建立，，然後按一下**確定**。  
  
7.  在 [接收位置屬性] 對話方塊中**名稱**方塊中，輸入接收位置，例如 FRRSWIFTReceiveLocation 的名稱。  
  
8.  在**傳輸** 區段中，針對**類型**文字方塊中，選取**MQSeries**。  
  
9. 按一下**設定**。  
  
10. 在 [MQSeries 傳輸屬性] 對話方塊中，按一下**佇列定義**，然後按一下省略符號 (**...**) 按鈕。  
  
11. 在**佇列定義**對話方塊中，輸入 MQSeries server 佇列管理員，並加入佇列。 按一下 **[確定]**。  
  
12. 在**MQSeries 傳輸屬性**對話方塊方塊中，確認內容會視需要。 按一下 **[確定]**。  
  
    > [!NOTE]
    >  如需 MQSeries 傳輸屬性的詳細資訊，請參閱 MQSeries 文件。  
  
13. 在 [接收位置屬性] 對話方塊的**接收處理常式**，選取**BizTalkServerApplication**。  
  
14. 如**接收管線** 區段中，選取 A4SWIFT 接收管線 FRR 所建立。  
  
15. 按一下**套用**，然後按一下  **確定**  
  
16. 在 [BizTalk 總管] 中，以滑鼠右鍵按一下您剛才的接收位置建立，，然後按一下**啟用**。