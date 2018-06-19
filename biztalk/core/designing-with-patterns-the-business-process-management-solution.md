---
title: 使用模式進行設計： 商務程序管理解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- patterns [process management solutions], examples
- patterns [process management solutions], designing
- examples, programming patterns
- designing, programming patterns
ms.assetid: 0583f4a4-01db-4d5b-a1f5-1694c1ddbd30
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91da8c63fc46ee90696e257bfd6142b5088af305
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239662"
---
# <a name="designing-with-patterns-the-business-process-management-solution"></a>使用模式進行設計： 商務程序管理解決方案
商務程序管理解決方案顯示在 BizTalk 應用程式中建構程序管理員的方式。 解決方案使用元件以選取和控制訂單處理階段的順序。 解決方案會在傳遞訂單以進行處理之前，接收訂單 (可能用於新的服務、變更或取消服務)、加以記錄和認可訂單。 處理包含一或多個處理訂單的階段。 最後，解決方案會將最終回應傳回至原始訂單要求。  
  
 設計良好的程序管理解決方案可讓您從程序新增或刪減階段，無須重新建構應用程式的其他部分。 此解決方案中採取的方法就可以這麼做。 訂單程序分成不連續的獨立階段。 所有階段都是從相同的連接埠讀取，並使用篩選條件來判斷要處理的訊息。 這會在下一節＜模式＞中詳細說明。  
  
 此解決方案也接受透過 Web 服務輸入，雖然您也可以透過 FTP 連線以此解決方案使用非服務介面。 此功能模擬在批次系統中使用應用程式的方式。  
  
## <a name="patterns"></a>模式  
 下圖顯示前面小節中所描述的商務程序管理解決方案中的模式簡化版本。  
  
 ![商務程序管理解決方案模式](../core/media/bts-cp-business-process-management-patterns.gif "bts_cp_Business_Process_Management_Patterns")  
  
 解決方案包含下列部分： 服務介面、 FTP 通道、 各種轉譯程式、 處理序管理員，以及兩個處理階段。 前置處理區段中的四個轉譯器會建立回到服務介面的通知訊息、在歷史或追蹤資料庫中產生項目，以及在服務系統中製作項目。 第四個轉譯器會建立程序管理員所需的訊息。 接著，程序管理員控制處理階段。  
  
 在許多程序管理員實作中，管理員會追蹤處理狀態。 如圖所示，此實作會加以修改。 在此解決方案中，程序管理員在訊息中設定旗標，以指示下一個處理訊息的處理階段。 然後各個階段使用篩選條件來決定是否要處理特定訊息。  
  
 使用此方法，程序管理員不需維護任何路由資訊。 在管理員和各階段之間的所有訊息都使用相同的連接埠。 若要新增階段，只需要在適當的連接埠上新增傳送和接收的元件，以及正確階段編號的篩選條件。 您不需要變更程序管理員本身。  
  
 請注意，還有很多內容不在圖形內。 處理階段可能 (事實上確實會) 和後端程序通訊。 解決方案也會在程序中的多處收集歷史資訊。 或許，最值得注意的是未指定程序管理員的邏輯。 此外，未指定使用同步或非同步連線。 這些會在下列各節中考量。  
  
## <a name="see-also"></a>另請參閱  
 [商務程序管理解決方案中的模式](../core/patterns-in-the-business-process-management-solution.md)   
 [轉譯商務程序管理解決方案的模式](../core/translating-the-patterns-of-the-business-process-management-solution.md)