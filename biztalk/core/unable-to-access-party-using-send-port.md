---
title: 若要存取合作對象無法使用傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ffacba77-76e8-4f03-be26-134a9999d6c1
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cdff3eed53ae042be064bd2e02ff5cecf68c6021
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976413"
---
# <a name="unable-to-access-party-using-send-port"></a>若要存取合作對象無法使用傳送埠
## <a name="details"></a>詳細資料  

|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       AS2 引擎                                       |
|  符號名稱  |                       UnableToLocateAS2PartyBySendPortNameError                        |
|  訊息文字   |                      若要存取合作對象無法使用傳送埠： {0}                       |

## <a name="explanation"></a>說明  
 此錯誤表示傳送管線找不到指定相關聯的合作對象傳送外寄 AS2 訊息的連接埠。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請將合作對象與指定的傳送埠產生關聯：  

1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  

2. 在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後按一下**合作對象**。  

3. 以滑鼠右鍵按一下正確的合作對象。  

4. 按一下 **[屬性]**。  

5. 在 [*合作對象名稱*]**合作對象屬性**對話方塊中，在左窗格中，按一下 **傳送埠**。  

6. 輸入傳送埠名稱，在**傳送埠**清單。  

7. 按一下 [確定] 。
