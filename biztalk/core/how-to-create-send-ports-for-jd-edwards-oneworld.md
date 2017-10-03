---
title: "如何建立 JD Edwards OneWorld 傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating send ports
- send ports, creating
ms.assetid: 858425ef-bdb7-4d2d-90ca-b3655e389749
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc77fd72171983ab2fbc7de42ddf36d770d045c6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-send-ports-for-jd-edwards-oneworld"></a>如何建立 JD Edwards OneWorld 的傳送埠
使用下列程序來建立傳送埠。  
  
### <a name="to-create-a-send-port"></a>建立傳送埠  
  
1.  在 BizTalk Server 管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後瀏覽至必要的應用程式。  
  
2.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。  
  
    > [!NOTE]
    >  您也可以使用**靜態單向連接埠**。  
  
3.  在**傳送埠屬性**對話方塊中，於**名稱**欄位中，輸入傳送埠名稱 (例如，輸入**SendToJDE**。)  
  
4.  在**類型**下拉式清單中，選取**[jdeoneworld]**。  
  
5.  在**URI**下拉式清單中，選取傳送處理常式。  
  
6.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [建立 JD Edwards OneWorld 傳送處理常式](../core/creating-jd-edwards-oneworld-send-handlers.md)