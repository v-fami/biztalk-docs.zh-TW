---
title: 如何設定 Windows SharePoint Services 傳送處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [Windows SharePoint Services adapters], send handlers
- send handlers, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, send handlers
ms.assetid: 457767d9-6e39-4553-9bbe-212fcb7c04bc
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8e110fb2a671fc839fb96cfdc2ad03169649e6e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25969132"
---
# <a name="how-to-configure-a-windows-sharepoint-services-send-handler"></a>如何設定 Windows SharePoint Services 傳送處理常式
使用下列程序，變更與 Windows SharePoint Services 傳送處理常式關聯的主控件。  
  
> [!NOTE]
>  每個主控件只可和一個傳送處理常式建立關聯。  
  
### <a name="to-change-global-variables-for-a-windows-sharepoint-services-send-handler"></a>變更 Windows SharePoint Services 傳送處理常式的全域變數  
  
1.  在 BizTalk Server 管理主控台中，按一下以展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，然後按一下以展開**BizTalk 群組 [\<servername\>:\<管理資料庫\>]**，按一下以展開**平台設定**，然後按一下以展開**配接器**。 配接器清單會出現在資料夾下。  
  
2.  按一下**Windows SharePoint Services**，在右窗格中，以滑鼠右鍵按一下您想要設定，然後按一下 傳送處理常式**屬性**。  
  
3.  在**配接器處理常式屬性**對話方塊**一般**索引標籤的**主機名稱**清單中，選取與其相關聯的傳送處理常式的主機。  
  
4.  在**一般**索引標籤上，按一下 **屬性**。  
  
5.  在**Windows SharePoint Services 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |傳送批次大小|Windows SharePoint Services Web 服務視為一個批次進行處理的文件數目上限。 預設值是 20。 **注意：** 的最小值為 1。|  
  
## <a name="see-also"></a>請參閱  
 [如何設定 Windows SharePoint Services 接收位置](../core/how-to-configure-a-windows-sharepoint-services-receive-location.md)   
 [如何設定 Windows SharePoint Services 傳送埠](../core/how-to-configure-a-windows-sharepoint-services-send-port.md)   
 [如何建立傳送埠](../core/how-to-create-a-send-port2.md)   
 [Windows SharePoint Services 配接器屬性參考](../core/windows-sharepoint-services-adapter-properties-reference.md)   
 [Windows SharePoint Services 配接器運算式](../core/windows-sharepoint-services-adapter-expressions.md)   
 [支援的 Windows SharePoint Services 資料行類型](../core/supported-windows-sharepoint-services-column-types.md)