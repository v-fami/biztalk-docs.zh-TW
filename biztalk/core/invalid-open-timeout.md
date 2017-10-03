---
title: "無效的開啟逾時 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0047cf43-fcc3-40b4-abeb-bf1b6e7a422b
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00a9c87eb3a7213bc627681e3191717733a25513
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-open-timeout"></a>無效的開啟逾時
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|無效的開啟逾時。 有效範圍： 0 到 23 小時，0 到 59 分鐘的時間，以及 0 到 59 秒。|  
  
## <a name="explanation"></a>說明  
  
## <a name="user-action"></a>使用者動作  
 您可以使用下列程序來設定逾時時間範圍。  
  
#### <a name="to-configure-the-timeout-range"></a>若要設定的逾時範圍  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2.  在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  找出您的應用程式，然後再找出您的傳輸。  
  
4.  以滑鼠右鍵按一下傳輸名稱。  
  
5.  按一下 **[屬性]**。  
  
6.  在 連接埠**類型**清單中，選取正確的連接埠。  
  
7.  按一下**設定**。  
  
8.  在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**繫結**] 索引標籤。  
  
9. 確定逾時範圍有效。 可接受的值為 0 到 23 小時，0 到 59 分鐘的時間，以及 0 到 59 秒數。