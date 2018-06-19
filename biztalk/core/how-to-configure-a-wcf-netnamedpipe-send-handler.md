---
title: 如何設定 Wcf-netnamedpipe 傳送處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-NetNamedPipe adapters, global adapters
- configuring [WCF-NetNamedPipe adapters], global adapters
- send handlers, WCF-NetNamedPipe adapters
- configuring [WCF-NetNamedPipe adapters], send handlers
ms.assetid: 1f281649-d09f-44eb-8af5-1f83233fab60
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 079d490ab8af28292c5f6adc6d98c8f64c5b16fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248014"
---
# <a name="how-to-configure-a-wcf-netnamedpipe-send-handler"></a>如何設定 WCF-NetNamedPipe 傳送處理常式
請使用下列程序設定 WCF-NetNamedPipe 傳送處理常式。  
  
### <a name="to-change-global-variables-for-a-wcf-netnamedpipe-send-handler"></a>若要變更 WCF-NetNamedPipe 傳送處理常式的全域變數  
  
1.  在 BizTalk Server 管理主控台中，展開  [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開  **配接器**。  
  
2.  在展開的配接器清單中，按一下  **Wcf-netnamedpipe**，在右窗格，以滑鼠右鍵按一下您想要設定的傳送處理常式，然後按一下**屬性**。  
  
3.  在**配接器處理常式屬性**對話方塊**一般**索引標籤的**主機名稱**清單中，選取與其相關聯的傳送處理常式的主機。  
  
4.  在**一般**索引標籤上，按一下 **屬性**。 在**傳送處理常式**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**連線數目上限**|指定快取在連接集區中的每個端點之輸出連線最大數目。 這會限制每個唯一遠端端點快取中的連線數目。 您應該將這個值設定為大於您預計要為任何特定遠端端點快取存放的最大連線數。 如果作用中輸出連線數目超過這個最大值，則對於在此傳送處理常式下執行的 WCF-NetNamedPipe 傳送埠，服務可能會顯得反應遲緩。<br /><br /> 預設值是 10。|  
  
5.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [使用 WCF 服務](../core/consuming-wcf-services.md)   
 [設定 Wcf-netnamedpipe 配接器](../core/configuring-the-wcf-netnamedpipe-adapter.md)