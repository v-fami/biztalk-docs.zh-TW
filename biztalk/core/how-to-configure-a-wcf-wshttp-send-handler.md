---
title: 如何設定 Wcf-wshttp 傳送處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-WSHttp adapters, global variables
- configuring [WCF-WSHttp adapters], send handlers
- configuring [WCF-WSHttp adapters], global variables
- send handlers, WCF-WSHttp adapters
ms.assetid: b2c30edb-8f7b-4d3c-812b-5b877c47fda1
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11566bcc902ccbda33b6b15922292390df3d5201
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248454"
---
# <a name="how-to-configure-a-wcf-wshttp-send-handler"></a>如何設定 WCF-WSHttp 傳送處理常式
您可以透過下列程序，設定 WCF-WSHttp 傳送處理常式。  
  
> [!CAUTION]
>  使用 WCF-WSHttp 配接器處理常式時，建議您在 [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] 或 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 電腦上安裝這些處理常式的主控件執行個體。  
  
### <a name="to-change-global-variables-for-a-wcf-wshttp-send-handler"></a>若要變更 WCF-WSHttp 傳送處理常式的全域變數  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開**配接器**。  
  
2.  在展開的配接器清單中，按一下  **Wcf-wshttp**，在右窗格，以滑鼠右鍵按一下您想要設定的傳送處理常式，然後按一下**屬性**。  
  
3.  在**配接器處理常式屬性**對話方塊**一般**索引標籤的**主機名稱**清單中，選取與其相關聯的接收處理常式的主機。  
  
4.  在**一般**索引標籤上，按一下**屬性**上**Proxy**索引標籤上，執行下列動作。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**使用 Proxy**|指出這個傳送埠是否要使用 Proxy 伺服器。<br /><br /> 預設值為清除核取方塊。|  
    |**位址**|指定 Proxy 伺服器的位址。 使用**https**或**http**根據安全性組態的配置。 這個位址後面可以加上冒號和連接埠編號， 例如 http://127.0.0.1:8080。<br /><br /> 這個屬性的值才需要**使用 proxy**已選取。<br /><br /> 類型：字串<br /><br /> 最大長度：256<br /><br /> 預設為空字串。|  
    |**使用者名稱**|指定要用於驗證的使用者名稱。 若使用整合式或基本驗證，則使用者名稱也包括網域，即「網域\使用者名稱」。 如果使用摘要式驗證，則使用者名稱不包含網域\\。<br /><br /> 這個屬性的值才需要**使用 proxy**已選取。<br /><br /> 類型：字串<br /><br /> 最小長度：00<br /><br /> 最大長度：256<br /><br /> 預設為空字串。|  
    |**密碼**|指定要用於驗證的密碼。<br /><br /> 這個屬性的值才需要**使用 proxy**已選取。<br /><br /> 類型：字串<br /><br /> 最小長度：00<br /><br /> 最大長度：256<br /><br /> 預設為空字串。|  
  
5.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [設定 Wcf-wshttp 配接器](../core/configuring-the-wcf-wshttp-adapter.md)