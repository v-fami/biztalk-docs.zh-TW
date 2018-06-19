---
title: 如何設定 Wcf-nettcp 接收處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-NetTcp adapters, global variables
- receive handlers, WCF-NetTcp adapters
- configuring [WCF-NetTcp adapters], global variables
- configuring [WCF-NetTcp adapters], receive handlers
ms.assetid: a4a283d1-21de-4d6b-9cb5-f2f9f823903b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69598bc1ce0bda41269fa91a0618fb040e741b28
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247518"
---
# <a name="how-to-configure-a-wcf-nettcp-receive-handler"></a>如何設定 WCF-NetTcp 接收處理常式
請使用下列程序設定 WCF-NetTcp 接收處理常式。  
  
### <a name="to-change-global-variables-for-a-wcf-nettcp-receive-handler"></a>若要變更 WCF-NetTcp 接收處理常式的全域變數  
  
1.  在 BizTalk 管理主控台中，展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開 **配接器**。  
  
2.  在展開的配接器清單中，按一下  **Wcf-nettcp**，在右窗格，以滑鼠右鍵按一下您想要設定的接收處理常式，然後按一下**屬性**。  
  
3.  在**配接器處理常式屬性**對話方塊**一般**索引標籤的**主機名稱**清單中，選取與其相關聯的接收處理常式的主機。  
  
4.  在**一般**索引標籤上，按一下 **屬性**上**接收處理常式**索引標籤上，執行下列動作。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**連線數目上限**|指定待命程式最多可以擁有等待應用程式接受的連線數目。 超過此配額值時，則會捨棄新的傳入連線，而非等待接受連線。<br /><br /> 預設值是 10。|  
  
5.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [設定 Wcf-nettcp 配接器](../core/configuring-the-wcf-nettcp-adapter.md)   
 [發佈 WCF 服務](../core/publishing-wcf-services.md)