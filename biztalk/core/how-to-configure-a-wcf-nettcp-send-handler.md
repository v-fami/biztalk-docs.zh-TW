---
title: 如何設定 Wcf-nettcp 傳送處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send handlers, WCF-NetTcp adapters
- configuring [WCF-NetTcp adapters], send handlers
- WCF-NetTcp adapters, global variables
- configuring [WCF-NetTcp adapters], global variables
ms.assetid: c60fe03d-7e11-4e08-9a24-8ff443eee9c1
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02451dba6755e4db0c10d7cce20141468a67694f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247910"
---
# <a name="how-to-configure-a-wcf-nettcp-send-handler"></a>如何設定 WCF-NetTcp 傳送處理常式
使用下列程序，定 WCF-NetTcp 傳送處理常式。  
  
### <a name="to-change-global-variables-for-a-wcf-nettcp-send-handler"></a>若要變更 WCF-NetTcp 傳送處理常式的全域變數  
  
1.  在 BizTalk 管理主控台中，展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開 **配接器**。  
  
2.  在展開的配接器清單中，按一下  **Wcf-nettcp**，在右窗格，以滑鼠右鍵按一下您想要設定的傳送處理常式，然後按一下**屬性**。  
  
3.  在**配接器處理常式屬性**對話方塊**一般**索引標籤的**主機名稱**清單中，選取與其相關聯的傳送處理常式的主機。  
  
4.  在**一般**索引標籤上，按一下 **屬性**。 在**傳送處理常式**索引標籤上，執行下列動作。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**連線數目上限**|指定快取在連接集區中的每個端點之輸出連線最大數目。 這會限制每個唯一遠端端點快取中的連線數目。 您應該將這個值設定為大於您預計要為任何特定遠端端點快取存放的最大連線數。 如果作用中輸出連線數目超過這個最大值，則服務對於在此傳送處理常式下執行的 WCF-NetTcp 傳送埠，可能顯得反應遲緩。<br /><br /> 預設值是 10。|  
  
5.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [使用 WCF 服務](../core/consuming-wcf-services.md)   
 [設定 Wcf-nettcp 配接器](../core/configuring-the-wcf-nettcp-adapter.md)