---
title: "找不到輸入內文路徑運算式內容 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed294662-a94e-4fbb-b125-878a27107eab
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 879b846900441cfced9e4a875d7c2ad74310e701
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-find-content-for-inbound-body-path-expression"></a>找不到輸入內文路徑運算式的內容
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|訊息中找不到輸入內文路徑運算式 "{0}" 的內容|  
  
## <a name="explanation"></a>說明  
 經由執行內文路徑運算式來從內送訊息中擷取的內容不含任何資料。  
  
## <a name="user-action"></a>使用者動作  
 請確定內文路徑運算式正確無誤，而且內送訊息具有正確的資料。  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2.  在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  找出您的應用程式，然後再找出您的傳輸。  
  
4.  以滑鼠右鍵按一下傳輸名稱。  
  
5.  按一下 **[屬性]**。  
  
6.  在 連接埠**類型**清單中，選取正確的連接埠。  
  
7.  按一下**設定**。  
  
8.  在 WCF **[***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**訊息**] 索引標籤。  
  
9. 在**輸入 BizTalk 訊息內文**區段中，檢查的資訊**內文路徑運算式**。