---
title: 結構化的交換 XML 訊息的序列化期間發生的錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 97939bfd-d1ee-455a-9952-4f25db020e7c
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e5ce0694b60afcb743c138d3059a78f63f6fcb5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994295"
---
# <a name="structural-error-encountered-during-serialization-of-an-interchange-xml-message"></a>結構化的交換 XML 訊息的序列化期間發生的錯誤
## <a name="details"></a>詳細資料  

|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                                  InvalidXmlNodeFound                                   |
|  訊息文字   |    結構化的交換 Xml 訊息的序列化期間發生的錯誤     |

## <a name="explanation"></a>說明  
 此錯誤表示，交換 XML 訊息序列化期間遇到結構錯誤。 BTS 尋找 Xmlstartelement 或 EndElement，但改為遇到不同的 XML 節點型別。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定訊息結構正確，並再試一次：  

1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  

2. 在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，然後按一下**BizTalk 群組**。  

3. 在右窗格中，按一下**群組中樞** 索引標籤。  

4. 按一下 **擱置服務執行個體**。  

5. 按兩下的訊息。  

6. 在 **服務詳細資料** 視窗中，按一下**訊息** 索引標籤。  

7. 一次按兩下的訊息。  

8. 在左窗格中，按一下**訊息部分 / b**。  

9. 判斷訊息結構是否正確。
