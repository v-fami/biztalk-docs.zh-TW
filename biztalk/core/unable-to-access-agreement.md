---
title: 無法存取協議 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 72890ee9-54c9-48ed-8c6e-8b329d79c68b
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b9c8d8126a7b38d95adfce1e813dd2a86ccde24
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024532"
---
# <a name="unable-to-access-agreement"></a>無法存取協議
## <a name="details"></a>詳細資料  

|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                              UnableToLocateAS2PartyError                               |
|  訊息文字   |            無法存取協議。 AS2From: {0} AS2To: {1}。 錯誤： {2}             |

## <a name="explanation"></a>說明  
 此錯誤表示 BizTalk Server 找不到指定的辨識符號和值的合作對象。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，建立以給定限定詞的合作對象別名：  

1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  

2. 在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後按一下**合作對象**。  

3. 以滑鼠右鍵按一下正確的合作對象。  

4. 按一下 **[屬性]**。  

5. 在 [*合作對象名稱*]**合作對象屬性**對話方塊中，輸入**EDIINT-AS2 From 值**中**名稱**資料行。  

6. 輸入中的合作對象名稱**值**資料行。  

7. 按一下 [確定] 。
