---
title: 不支援的安全性演算法套件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 11696fed-c3a8-4b11-8249-9f99f7abc8f2
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43cce7cd315c3bdfa3835014c2cf1f6a8c7077f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286902"
---
# <a name="unsupported-security-algorithm-suite"></a>不支援的安全性演算法套件
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|不支援的安全性演算法組合： {0}|  
  
## <a name="explanation"></a>說明  
 當接收位置或傳送埠的安全性演算法套件屬性設定不正確的值時，就會發生此錯誤。  
  
## <a name="user-action"></a>使用者動作  
 請確定的交易通訊協定屬性設為有效的值。  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2.  在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  找出您的應用程式，然後再找出您的傳輸。  
  
4.  以滑鼠右鍵按一下傳輸名稱。  
  
5.  按一下 **[屬性]**。  
  
6.  在 連接埠**類型**清單中，選取**Wcf-nettcp**。  
  
7.  按一下**設定**。  
  
8.  在**Wcf-nettcp 傳輸屬性**對話方塊中，按一下 [**安全性**] 索引標籤。  
  
9. 在**訊息安全性**區段中，請確認值**演算法套件**正確無誤。