---
title: BizTalk 訊息內文元素編碼無效 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b407e5c3-4655-4b2f-8ecc-30eb080ec47c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6bca7046606461dd3368224364c21dd48ea5dfb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967967"
---
# <a name="biztalk-message-body-element-encoding-is-invalid"></a>BizTalk 訊息內文元素編碼不正確
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                |
|-----------------|----------------------------------------------------------------------------------------------------------------|
|  產品名稱   |               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]               |
| 產品版本 |                           [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                           |
|    事件識別碼     |                                                       0                                                        |
|  事件來源   |                                                       0                                                        |
|    元件    |                                                       0                                                        |
|  符號名稱  |                                                       0                                                        |
|  訊息文字   | BizTalk 訊息內文元素編碼 "{0}" 無效。 預期的編碼方式:"xml"，"none"|"base64"、"hex"或"string" |
  
## <a name="explanation"></a>說明  
 此錯誤表示 BizTalk 內文 範本選項用於外寄訊息中;不過，指定 BizTalk 內文的編碼類型無效。  
  
## <a name="user-action"></a>使用者動作  
 您可以使用下列程序來設定編碼類型。  
  
#### <a name="to-configure-the-encoding-type"></a>若要設定的編碼類型  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。  
  
2. 在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3. 找出您的應用程式，然後找出您的傳輸。  
  
4. 以滑鼠右鍵按一下傳輸名稱。  
  
5. 按一下 **[屬性]**。  
  
6. 在 連接埠**型別**清單中，選取正確的連接埠。  
  
7. 按一下 **設定**。  
  
8. 在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**訊息**] 索引標籤。  
  
9. 在 **輸出 WCF 訊息內文**區段中，按一下**範本-由範本指定內容**選項按鈕。 在 [ **XML** BizTalk 內文的格式應為文字] 方塊中，   
    \<**bts 訊息主體 xmlns ="<http://www.microsoft.com/schemas/bts2007>"編碼 ="[xml&#124;base64&#124;十六進位&#124;字串]"/** \> (有效的值，也就是區分大小寫，編碼為 xml&#124;base64&#124;十六進位&#124;字串)