---
title: 如何設定傳送埠的傳輸進階選項 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, transport options [send ports]
- configuring, send ports
- send ports, transport options
- managing [send ports], configuring
- managing [send ports], transport options
ms.assetid: b0033e09-3c18-4e53-a470-e12978e61ba1
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3aada2fa4f32e66c88f295e96bd71a9330cfb988
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023876"
---
# <a name="how-to-configure-transport-advanced-options-for-a-send-port"></a>如何設定傳送埠的傳輸進階選項
您可以使用 BizTalk Server 管理主控台來設定傳送埠的傳輸進階選項。 這些選項可決定傳送埠如何處理訊息，例如訊息失敗時重試傳送訊息的次數，以及該連接埠的服務窗口排程。  
  
> [!NOTE]
> **開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** ，您可以啟用排序的傳遞的動態傳送埠，根據配接器類型而定。 此選項只適用於配接器類型排序的傳遞保證靜態傳送埠，例如 File 配接器或 FTP 配接器的位置。
> 
> 請考慮六個訊息： M1、 M2，M3、 M4、 M5 和 M6。 M1、 M3、 M5 是為了檔案位置。 M2、 M4 和 M6 是適用於 FTP。 排序的傳遞動態傳送埠可確保已排序 M1、 M3 和 M5;與 M2、 M4 和 M6 分別排序。 
> 
> 對於不支援排序的傳遞這些配接器類型，目前沒有任何可用來設定動態傳送埠屬性。 在執行階段，會自動決定其傳輸選項。  
> 
> **適用於舊版的 BizTalk** ，使用動態連接埠，沒有任何設定，因為傳輸選項會自動決定在執行階段可用的屬性。

  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="controlling-send-port-priority"></a>控制傳送埠優先順序  
 [傳輸進階選項] 的 [優先順序] 設定可控制訊息從 MessageoBox 移除的順序。 具有較高優先順序的連接埠會比具有較低優先順序的連接埠更早處理，使較高優先順序的連接埠相對於單一主控件中的其他傳送埠來的重要。  
  
 優先順序在對某些要求類型需要低回應時間的實例中相當有用。 例如，如果有多個連接埠連接到不同的系統，以處理一般要求及互動式要求時。 互動式要求需要低回應時間，所有當互動式要求送出後，您可能想要盡快確認此要求已處理完成。  
  
 BizTalk Server 不會嘗試公平處理 MessageBox 中具有不同優先順序的訊息。 如果在處理開始時，MessageBox 中具有兩個不同優先順序的項目數量相等，較低優先順序的項目就會在所有高優先順序項目處理完之後才會進行處理。 如果高優先順序的數量很大，具有較低優先順序的項目可能永遠都不會進行處理。 換句話說，較低優先順序的項目將發生嚴重缺乏的情況。  
  
> [!WARNING]
>  若要將訊息嚴重缺乏的風險降到最低，請在實際負載下徹底測試您的應用程式，確定所有的訊息都已處理。 未測試您的方案可能造成未處理的訊息。  
  
 BizTalk Server 會在內部為每個訂閱指派優先順序。 優先順序可以從 1 (最高優先順序) 到 10 (最低優先順序) 的任何數字。 因為啟動訂閱的預設優先順序為 7，相互關聯訂閱的預設優先順序為 5，所以相互關聯訊息將比啟動訂閱更早傳遞。  
  
## <a name="configure-the-transport-options"></a>設定傳輸選項 
  
1.  開啟 [BizTalk Server 管理] 。  
  
2.  展開 BizTalk 群組，然後再展開 BizTalk 應用程式。  
  
3.  選取 **傳送埠**，以滑鼠右鍵按一下傳送埠，以設定，然後選取**屬性**。  
  
4.  在左窗格中，選取**傳輸進階選項**。  
  
5.  下表中所述，設定傳輸進階選項，然後選取**確定**。  只有部分的下列屬性可供使用動態傳送埠。
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |**重試計數**|指定傳送埠在訊息失敗時重新傳送訊息的次數。 預設值為 3；允許的範圍由 0 至 1,000。|  
    |**重試間隔**|以分鐘為單位指定重新傳送訊息嘗試之間的間隔。 預設值是 5;允許的範圍是從 0 到 525,600。|  
    |**優先權**|設定重新傳送嘗試的優先順序。|  
    |**排序的傳遞**|選取此核取方塊，依照接收順序來傳送訊息。|  
    |**停止傳送後續訊息目前訊息失敗**|選取此核取方塊以停止傳送跟隨在失敗訊息之後的後續訊息。 此功能時才可使用**排序的傳遞**選項。|  
    |**啟用失敗訊息的路由**|選取此選項以啟用失敗訊息的路由。|  
    |**啟用服務窗口**|選取此選項，以指定開始時間及停止時間的方式來指定傳送埠每日運作的時段。|  
    |**開始時間**|指定傳送埠每日開始傳送訊息的時間。 此功能時才可使用**啟用服務窗口**選項。|  
    |**停止時間**|指定傳送埠每日停止傳送訊息的時間。 此功能時才可使用**啟用服務窗口**選項。|  
  
## <a name="see-also"></a>另請參閱  
[訊息的排序傳遞](../core/ordered-delivery-of-messages.md)  
 [建立和設定傳送埠](../core/creating-and-configuring-send-ports.md)