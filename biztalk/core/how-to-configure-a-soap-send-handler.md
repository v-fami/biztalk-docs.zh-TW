---
title: 如何設定 SOAP 傳送處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send handlers, SOAP adapters
- SOAP adapters, denial of service
- denital of service, HTTP adapters
- configuring [SOAP adapters], send handlers
- configuring [SOAP adapters], denial of service
- SOAP adapters, send handlers
- denial of service, SOAP adapters
ms.assetid: fd610a3f-ca10-42e0-b81e-219e07e33830
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4bcbe39861c37db348e1e37752fbad6d9616033
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005479"
---
# <a name="how-to-configure-a-soap-send-handler"></a>如何設定 SOAP 傳送處理常式
使用下列程序，來設定 SOAP 傳送處理常式。  

> [!CAUTION]
>  當使用 HTTP 或 SOAP 配接器處理常式時，建議您安裝這些處理常式的主控件執行個體，在 Microsoft[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]電腦。  

### <a name="to-change-global-variables-for-a-soap-send-handler"></a>變更 SOAP 傳送處理常式的全域變數  

1. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，展開**BizTalk 群組**，展開**平台設定**，然後展開**配接器**。  

2. 在展開的配接器清單中，按一下**SOAP**，在右窗格以滑鼠右鍵按一下您想要設定的傳送處理常式，然後按一下**屬性**。  

3. 在 **配接器處理常式屬性**對話方塊的 **一般**索引標籤**主機名稱**清單中，選取與其相關聯的接收處理常式的主控。  

4. 在  **Proxy**索引標籤上，執行下列動作。  


   |   使用    |                                                                                                                  以進行此動作                                                                                                                   |
   |---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **使用 Proxy** |                                                                                          指示 SOAP 傳送處理常式是否要使用 Proxy 伺服器。                                                                                          |
   |  **Server**   |                  指定 Proxy 伺服器的名稱。<br /><br /> 此屬性只需要一個值，如果**使用 proxy**已選取。<br /><br /> 類型：字串<br /><br /> 最小長度：00<br /><br /> 最大長度：256                   |
   |   **通訊埠**    | 指定 SOAP 傳送處理常式使用的連接埠。<br /><br /> 此屬性只需要一個值，如果**使用 proxy**已選取。<br /><br /> 預設值： 80<br /><br /> 類型：Long<br /><br /> 最小值：0<br /><br /> 最大值： 65535 |
   | **使用者名稱** |             指定要用於驗證的使用者名稱。<br /><br /> 此屬性只需要一個值，如果**使用 proxy**已選取。<br /><br /> 類型：字串<br /><br /> 最小長度：00<br /><br /> 最大長度：256             |
   | **密碼**  |             指定要用於驗證的密碼。<br /><br /> 此屬性只需要一個值，如果**使用 proxy**已選取。<br /><br /> 類型：字串<br /><br /> 最小長度：00<br /><br /> 最大長度：256              |


5. 按一下 [確定] 。  

## <a name="see-also"></a>另請參閱  
 [設定 SOAP 配接器](../core/configuring-the-soap-adapter.md)   
 [發佈 Web 服務](../core/publishing-web-services.md)