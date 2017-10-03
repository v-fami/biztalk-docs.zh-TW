---
title: "無法取得資料庫或伺服器名稱 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0590f43b-0aec-491f-bca5-c50ab12552a5
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16c694acdc78b704eb6f2578df99239442fd897e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="could-not-get-the-database-or-the-server-names"></a>無法取得資料庫或伺服器名稱
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|-|  
|訊息文字|無法取得資料庫或伺服器名稱|  
  
## <a name="explanation"></a>說明  
 此錯誤表示 BizTalk 無法從登錄讀取 BizTalkMgmtDb 名稱和伺服器名稱。 這項錯誤的可能原因在於未設定 BizTalk 群組。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請設定 BizTalk 群組：  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  展開 [主控台根目錄] 中的 [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。  
  
3.  以滑鼠右鍵按一下**BizTalk 群組**。  
  
4.  按一下 **[屬性]**。  
  
5.  在左窗格中，按一下 **一般**。  
  
6.  確認**伺服器**名稱和**資料庫**名稱正確無誤。