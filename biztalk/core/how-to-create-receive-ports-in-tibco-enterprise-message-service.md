---
title: "如何建立 TIBCO Enterprise Message Service 中的接收埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive ports, creating
- creating receive ports
ms.assetid: ca623c81-3dd3-4824-a586-28055d01fe9f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a85fad9dc0936baa0c3f584581d5483a30fedf6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-receive-ports-in-tibco-enterprise-message-service"></a>如何在 TIBCO Enterprise Message Service 中建立接收埠
請遵循下列步驟來建立接收埠。  
  
### <a name="to-create-a-receive-port"></a>建立接收埠  
  
1.  在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 所需應用程式。  
  
2.  以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。  
  
3.  在**接收埠屬性**視窗，請在**一般**頁面上，執行下列動作：  
  
    1.  在**名稱**欄位中，輸入`ReceiveFromTIBCOEMS`。  
  
    2.  在**驗證**群組方塊中，指定使用驗證時，如何處理的訊息。  
  
    3.  選取**啟用的路由失敗訊息**核取方塊。  
  
4.  在**接收位置**頁面上，執行下列動作：  
  
    1.  按一下 **[新增]**。  
  
    2.  在**接收位置**視窗，請在**一般**頁面上，輸入**名稱**接收位置。  
  
    3.  從**類型**下拉式清單中，選取傳輸類型，以及從**接收處理常式**下拉式清單中，選取傳輸位址。  
  
    4.  從**接收管線**下拉式清單中，選取接收管線。  
  
    5.  在**排程**頁面上，選取**開始日期**和**結束日期**限制接收文件。  
  
    6.  選取**啟用服務窗口**核取方塊。  
  
    7.  按一下 **[確定]**。  
  
5.  在**輸入對應**頁面上，選取輸入的對應轉換文件上選取的連接埠。  
  
6.  在**追蹤**頁面上，選取所需的追蹤訊息內文和追蹤訊息屬性。  
  
7.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [設定 TIBCO 企業訊息服務傳輸屬性的接收埠](../core/set-tibco-enterprise-message-service-transport-properties-for-the-receive-port.md)