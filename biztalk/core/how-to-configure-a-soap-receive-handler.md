---
title: 如何設定 SOAP 接收處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [SOAP adapters], receive handlers
- SOAP adapters, receive handlers
- receive handlers, SOAP adapters
ms.assetid: e1174381-f36c-4131-83b7-26bfa879802e
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15c4f9e63b1b41592cdda3dd984e85f20373fd2f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968343"
---
# <a name="how-to-configure-a-soap-receive-handler"></a>如何設定 SOAP 接收處理常式
使用 [BizTalk Server 管理主控台]，可以設定 SOAP 接收處理常式設定。 若使用 [BizTalk Server 管理主控台] 設定配接器，則不需在 [BizTalk 總管] 中設定處理常式覆寫屬性。  
  
### <a name="to-change-global-variables-for-the-soap-receive-handler"></a>變更 SOAP 接收處理常式的全域變數  
  
1. 在 BizTalk Server 管理主控台中，依序展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開 **配接器**。  
  
2. 在展開的配接器清單中，按一下**SOAP**，在右窗格以滑鼠右鍵按一下您想要設定的接收處理常式，然後按一下**屬性**。  
  
3. 在 **配接器處理常式屬性**對話方塊的 **一般**索引標籤**主機名稱**清單中，選取與其相關聯，接收處理常式的主控，然後按一下 **確定**。  
  
## <a name="see-also"></a>另請參閱  
 [設定 SOAP 配接器](../core/configuring-the-soap-adapter.md)   
 [使用 Web 服務](../core/consuming-web-services.md)