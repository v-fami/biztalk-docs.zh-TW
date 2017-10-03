---
title: "如何在協調流程中使用連接埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, adding ports
- Port Configuration Wizard [Orchestration Designer], configuring ports
- ports, operations
- operations, adding to ports
- configuring, ports
- ports, deleting
- deleting, ports
- ports, Port Configuration Wizard [Orchestration Designer]
- ports, adding to orchestrations
- ports, configuring
ms.assetid: da8665cd-ccde-4949-b5f5-01f9f8be5ce8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3edef29376d8724d93192040ee88951ced245ac3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-ports-in-orchestrations"></a>如何在協調流程中使用連接埠
新增連接埠到協調流程的方式，和新增控制項到 Web Form 或 Windows Form 的方式類似。 您也可以使用 [協調流程檢視] 視窗來新增連接埠。  
  
### <a name="to-add-a-new-port"></a>新增連接埠  
  
-   以滑鼠右鍵按一下**連接埠介面**或**角色連結**，然後按一下 **新連接埠**。  
  
     -或者-  
  
     在協調流程檢視] 視窗中，以滑鼠右鍵按一下**連接埠**，然後按一下 [**新連接埠**。  
  
     DesignTip 會出現在尚未完全設定的連接埠上。  
  
    > [!TIP]
    >  您也可以拖曳到連接埠**角色連結**。  
  
### <a name="to-add-and-configure-a-new-port"></a>新增及設定新連接埠  
  
1.  從**BizTalk 協調流程** 索引標籤的 工具箱 拖曳**連接埠**圖形拖曳到**連接埠介面**或**角色連結**。  
  
     -或者-  
  
     以滑鼠右鍵按一下**連接埠介面**或**角色連結**，然後按一下 **新設定連接埠**。  
  
     -或者-  
  
     在協調流程檢視] 視窗中，以滑鼠右鍵按一下**連接埠**，然後按一下 [**新設定連接埠**。  
  
     「連接埠組態精靈」隨即出現。  
  
2.  請遵照精靈中的步驟設定連接埠。 如需詳細資訊，請參閱[如何執行連接埠組態精靈](../core/how-to-run-the-port-configuration-wizard.md)。  
  
### <a name="to-remove-a-port"></a>移除連接埠  
  
-   以滑鼠右鍵按一下要移除，然後按一下 連接埠**刪除**。  
  
    > [!NOTE]
    >  如果您刪除連接埠連接到後**傳送**或**接收**圖形的協調流程中編譯之後，在圖形上的連接埠作業將不會被刪除，而且您會收到錯誤時您嘗試編譯。 將圖形連接到其他連接埠，並重新設定連接埠作業。  
  
### <a name="to-configure-a-port-by-using-the-port-configuration-wizard"></a>使用連接埠組態精靈來設定連接埠  
  
1.  以滑鼠右鍵按一下要設定，然後再按一下的通訊埠**設定連接埠**。  
  
2.  遵循設定連接埠的連接埠組態精靈中的步驟。 如需詳細資訊，請參閱[如何執行連接埠組態精靈](../core/how-to-run-the-port-configuration-wizard.md)。  
  
### <a name="to-configure-a-port-manually-by-using-the-properties-window"></a>使用屬性視窗來手動設定連接埠  
  
1.  選取要設定的連接埠。  
  
2.  在 [屬性] 視窗中，指定以下屬性：  
  
    |屬性|Description|  
    |--------------|-----------------|  
    |連接埠類型|決定與連接埠相關的通訊模式、作業及多部分訊息類型。|  
    |通訊方向|決定此協調流程是此通訊的傳送者或接收者。|  
    |通訊模式|決定連接埠是用於「要求-回應」通訊或「單向」通訊 (這個屬性由**連接埠類型**屬性和是唯讀的。)|  
    |繫結|決定訊息如何抵達其目的地：<br /><br /> 直接—與其他協調流程通訊。<br /><br /> 動態—與執行階段所決定的端點通訊。<br /><br /> 稍後指定—與系統管理員在設定階段所決定的端點通訊。<br /><br /> 立即指定—與設計階段已知的端點通訊。|  
    |識別碼|在協調流程中針對此連接埠所使用的名稱。|  
    |排序的傳遞|針對接收埠，確保以指定順序發佈至 MessageBox 資料庫的訊息是以與發佈至 MessageBox 的相同順序傳遞給每一個相符的訂閱者。 如需詳細資訊，請參閱[排序訊息傳遞](../core/ordered-delivery-of-messages.md)。|  
    |傳遞通知|針對傳送埠，決定是否要在訊息成功傳送時收到通知。 如需詳細資訊，請參閱 < 傳遞通知 > 中[如何設定 「 傳送 」 圖形](../core/how-to-configure-the-send-shape.md)。|  
  
3.  指定的剩餘屬性由**繫結**屬性：  
  
    -   直接繫結—用於直接與其他協調流程通訊時。  
  
        |屬性|Description|  
        |--------------|-----------------|  
        |夥伴協調流程連接埠|決定會直接與夥伴協調流程繫結的連接埠。|  
  
    -   動態繫結—用於與執行階段所決定的端點通訊時。  
  
        |屬性|Description|  
        |--------------|-----------------|  
        |接收管線|決定要用於內送訊息的管線。|  
        |傳送管線|決定要用於外寄訊息的管線。|  
  
    -   稍後指定—用於與系統管理員所設定的端點通訊時。  
  
    -   立即指定—用於與設計階段已知的端點通訊時。  
  
        |屬性|Description|  
        |--------------|-----------------|  
        |接收管線|決定要用於內送訊息的管線。|  
        |傳送管線|決定要用於外寄訊息的管線。|  
        |傳輸|決定要用於傳送訊息的傳輸。|  
        |URI|決定傳送訊息的位置。|  
  
### <a name="to-add-a-port-operation"></a>新增連接埠作業  
  
-   以滑鼠右鍵按一下您想要新增作業，然後按一下的通訊埠**新作業**。  
  
### <a name="to-remove-a-port-operation"></a>移除連接埠作業  
  
-   以滑鼠右鍵按一下要移除，然後按一下 連接埠作業**刪除**。