---
title: "如何建立 JD Edwards EnterpriseOne 的傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards EnterpriseOne adapters, send ports
- send ports, creating [JD Edwards EnterpriseOne adapters]
- adapters [JD Edwards EnterpriseOne adapters], send ports
- send ports, JD Edwards EnterpriseOne adapters
- creating, send ports [JD Edwards EnterpriseOne adapters]
ms.assetid: 687f9207-ad3e-41ea-8640-5b9b6efbc14e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36a3e8d2d3e8e1db230a03d9c4a0351d3a0f8394
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-send-ports-for-jd-edwards-enterpriseone"></a>如何建立 JD Edwards EnterpriseOne 的傳送埠
使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 建立傳送埠。  
  
### <a name="to-create-a-send-port"></a>建立傳送埠  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft BizTalk Server**，然後按一下  **BizTalk Server 管理**。  
  
2.  在 BizTalk Server 管理主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，並展開**應用程式**，然後展開您要建立傳送埠的應用程式。  
  
3.  以滑鼠右鍵按一下**傳送埠**按一下**新增**，然後按一下 **靜態請求-回應連接埠**。  
  
4.  在**傳送埠屬性**對話方塊方塊中，執行下列動作：  
  
    -   在**名稱**方塊中，輸入傳送埠名稱 (例如， `SendToJDE`)。  
  
    -   從**類型**下拉式清單中，選取**JDEdwards**。  
  
    -   從**傳送處理常式**下拉式清單中，選取傳送處理常式位址。  
  
5.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [建立 JD Edwards EnterpriseOne 傳送處理常式](../core/creating-jd-edwards-enterpriseone-send-handlers.md)