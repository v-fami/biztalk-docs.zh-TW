---
title: 如何設定傳送埠備份傳輸選項 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, send ports
- managing [send ports], configuring
- configuring, backing up [send ports]
- managing [send ports], backup options
- send ports, configuring
- send ports, backup options
ms.assetid: f05f57a6-e62b-4640-a6e2-cb73e9de2a14
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ff8b1354772290ce9e04742a6130a6f6f2df627
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248374"
---
# <a name="how-to-configure-backup-transport-options-for-a-send-port"></a>如何設定傳送埠的備份傳輸選項
本主題描述如何使用 BizTalk Server 管理主控台來設定傳送埠的備份傳輸選項。 您指定的備份傳輸會在主要傳輸無法運作時生效。 設定主要傳輸所述[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。  
  
> [!NOTE]
>  因為傳輸選項是在執行階段自動決定的，動態連接埠沒有可供設定的屬性。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-specify-transport-options-for-a-send-port"></a>指定傳送埠的傳輸選項  
  
1.  按一下**啟動**，按一下 **程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀結構中，展開您要為其設定傳送埠備份傳輸選項的 BizTalk 群組與 BizTalk 應用程式。  
  
3.  展開**傳送埠**，以滑鼠右鍵按一下傳送埠設定，請按一下**屬性**，然後按一下 **備份傳輸**。  
  
4.  下表中所述，設定備份傳輸選項，然後按一下**確定**。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**型別**|從下拉式清單選取適當的備份傳輸類型或傳輸通訊協定。 若連接埠是請求-回應連接埠，則清單中只會顯示支援請求-回應的傳輸類型。|  
    |**設定**|選取備份傳輸類型後，按一下**設定**，然後設定 傳輸屬性。 如需有關如何設定屬性的詳細資訊，請按一下**協助**。|  
    |**傳送處理常式**|從下拉式清單選取傳送配接器執行所在的主控件執行個體。|  
    |**重試計數**|指定傳送埠在訊息失敗時重新傳送訊息的次數。 預設值為 3；允許的範圍由 0 至 1,000。|  
    |**重試間隔**|以分鐘為單位指定重新傳送訊息嘗試之間的間隔。 預設值是 5;允許的範圍是從 0 到 525600。|  
  
## <a name="see-also"></a>另請參閱  
 [建立和設定傳送埠](../core/creating-and-configuring-send-ports.md)