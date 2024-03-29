---
title: 動態傳送埠處理常式是可設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eb8f5ef-af95-4b2e-9a43-6f1240b25855
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea7fb4a2f877baf70c0684c57b83e5f32edaa4d6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971775"
---
# <a name="dynamic-send-port-handler-is-configurable"></a>可設定動態傳送埠處理常式
建立動態傳送埠時，可針對「每一個」安裝的配接器設定配接器傳送處理常式。 請考慮下列案例：  
  
 **狀況**  
  
 應用程式中有兩個 ESB 行程。 Itinerary1 使用動態傳送埠將資料傳送至檔案共用。 Itinerary2 使用動態傳送埠傳送電子郵件。 動態傳送埠過去是在配接器的預設主控件中執行。 Itinerary1 主要是以小量 - 大型訊息大小案例為目標。 Itinerary2 是以大量 - 小型訊息大小案例為目標。 因為一個配接器只有一個預設主控件，所有會使用相同的主控件來路由傳送所有訊息，因而使效能降低。  
  
 **變更**  
  
 若要改善動態傳送埠的效能，可以將配接器傳送處理常式設定為使用任何主控件。 在 ESB 案例中，Itinerary1 使用 HostA 將資料傳送至檔案共用。 Itinerary2 使用 HostB 連接埠傳送電子郵件。  
  
## <a name="select-a-send-handler"></a>選取 傳送處理常式  
 建立動態單向傳送埠或動態請求-回應傳送埠時，可針對每一個安裝的配接器設定傳送處理常式。 步驟：  
  
1. 在**BizTalk Server 管理**主控台中，展開**BizTalk 群組 [*GroupName*]**，展開**應用程式**，然後展開包含傳送埠的應用程式。  
  
2. 以滑鼠右鍵按一下**傳送埠**，按一下**新增**，然後按一下**動態單向傳送埠**或是**動態請求-回應傳送埠**。  
  
3. 在 **屬性**，按一下**設定**。  
  
    配接器會與預設傳送處理常式一起列出。 按一下向下箭頭以選取不同的主控件。  
  
4. 按一下 **確定**儲存設定。  
  
5. 取消登錄，並重新編列新的動態傳送埠。  
  
6. 重新啟動原始的主控件執行個體。  
  
7. 重新啟動新的主控件執行個體。  
  
   其他傳送埠設定選項包含：  
  
- [如何設定傳送埠的傳輸進階選項](http://go.microsoft.com/fwlink/p/?LinkId=267697)  
  
- [如何設定傳送埠備份傳輸選項](http://go.microsoft.com/fwlink/p/?LinkId=267698)  
  
- [如何設定傳送埠的輸出對應](http://go.microsoft.com/fwlink/p/?LinkId=267699)  
  
- [如何設定傳送埠的篩選](http://go.microsoft.com/fwlink/p/?LinkId=267700)  
  
- [如何指派憑證給傳送埠](http://go.microsoft.com/fwlink/p/?LinkId=267701)  
  
- [如何設定傳送埠的追蹤](http://go.microsoft.com/fwlink/p/?LinkId=267702)  
  
  您可以微調不同的主控件。 下列連結將討論效能最佳化：  
  
  [一般 BizTalk Server 最佳化](http://go.microsoft.com/fwlink/p/?LinkId=267703)  
  
  [管理 BizTalk Server 效能設定](http://go.microsoft.com/fwlink/p/?LinkId=267704)