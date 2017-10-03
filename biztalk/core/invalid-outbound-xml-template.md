---
title: "無效的輸出 XML 範本 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f29bb60-8c04-4921-84bf-c629540a1c83
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f58d230b481e611879637ff1b6ae08c2eed0313f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-outbound-xml-template"></a>無效的輸出 XML 範本
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|無效的輸出 XML 範本|  
  
## <a name="explanation"></a>說明  
 可能有多個原因。 輸出 WCF 訊息本文的範本可能不是有效的 XML。 它可能包含無效的字元，以指定的編碼方式。 根項目可能已遺失。 根層級的資料可能不正確。  
  
## <a name="user-action"></a>使用者動作  
 請確認範本運算式具有有效的 XML 程式碼。 請確定它並未包含任何無效字元且有一個根項目。  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2.  在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  找出您的應用程式，然後再找出您的傳輸。  
  
4.  以滑鼠右鍵按一下傳輸名稱。  
  
5.  按一下 **[屬性]**。  
  
6.  在 連接埠**類型**清單中，選取正確的連接埠。  
  
7.  按一下**設定**。  
  
8.  在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**訊息**] 索引標籤。  
  
9. 在**輸出 WCF 訊息內文**區段中，選取**範本--由範本指定內容**。  
  
10. 在**XML**文字，請確認有效的 XML 程式碼。  
  
 如需有關範本的詳細資訊，請參閱下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [指定訊息本文為 WCF 配接器](../core/specifying-the-message-body-for-the-wcf-adapters.md)