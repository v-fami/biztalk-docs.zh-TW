---
title: 排程器無法排程批次 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ac6d79c-c995-4c95-a4da-ee2f50b9a13a
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bef1df18d88f8497fde440383d63bc64eefdd69a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269190"
---
# <a name="scheduler-was-unable-to-schedule-the-batch"></a>排程器無法排程批次
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|批次處理引擎|  
|符號名稱|-|  
|訊息文字|排程器無法排程批次|  
  
## <a name="explanation"></a>說明  
 此錯誤表示排程器無法判斷下一個出現的批次釋放。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定排定的批次釋放是有效的：  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後按一下**合作對象**。  
  
3.  以滑鼠右鍵按一下正確的合作對象。  
  
4.  按一下 **[屬性]**。  
  
5.  在 [*合作對象名稱*]**合作對象屬性**] 對話方塊的左窗格中，按一下 [**傳送埠**。  
  
6.  輸入傳送埠名稱，在**傳送埠**清單。  
  
7.  按一下 **[確定]**。