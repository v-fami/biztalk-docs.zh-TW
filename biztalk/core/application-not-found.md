---
title: 找不到的應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c37680b2-b38a-40f3-bb27-7b7281299ec3
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2a2b42a74001cfdc374d20052a8369ae535347d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230198"
---
# <a name="application-not-found"></a>找不到的應用程式
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|應用程式"{0}"找不到。請確認有預設的 BizTalk 組態資料庫中的應用程式|  
  
## <a name="explanation"></a>說明  
 此錯誤表示 BizTalk 會使用不存在於 BizTalk 資料庫的應用程式。  
  
## <a name="user-action"></a>使用者動作  
 您可以使用下列程序來設定有效的應用程式。  
  
#### <a name="to-configure-a-valid-application"></a>若要設定有效的應用程式  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2.  在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  請確定應用程式存在。 否則，請選取不同的有效應用程式。