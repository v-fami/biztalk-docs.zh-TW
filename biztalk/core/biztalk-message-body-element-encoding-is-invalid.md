---
title: BizTalk 訊息內文項目編碼方式則無效 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b407e5c3-4655-4b2f-8ecc-30eb080ec47c
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b1835371e5c042d3ddc46558cbf97970f6bfc6c
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="biztalk-message-body-element-encoding-is-invalid"></a>BizTalk 訊息內文項目編碼不正確
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|제품 이름|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|제품 버전|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|이벤트 ID|0|  
|이벤트 원본|0|  
|구성 요소|0|  
|심볼 이름|0|  
|訊息文字|BizTalk 訊息內文元素編碼"{0}"無效。 預期的編碼方式:"xml"，"base64"、"hex"或"string"|  
  
## <a name="explanation"></a>說明  
 此錯誤表示 BizTalk 內文範本選項用於外寄訊息中。不過，指定 BizTalk 內文的編碼類型不正確。  
  
## <a name="user-action"></a>使用者動作  
 您可以使用下列程序來設定編碼類型。  
  
#### <a name="to-configure-the-encoding-type"></a>若要設定的編碼類型  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2.  在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  응용 프로그램을 찾은 다음 전송을 찾습니다.  
  
4.  전송 이름을 마우스 오른쪽 단추로 클릭합니다.  
  
5.  **속성**을 클릭합니다.  
  
6.  在 連接埠 **類型** 清單中，選取正確的連接埠。  
  
7.  按一下  **設定**。  
  
8.  在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**訊息**] 索引標籤。  
  
9. 在 **輸出 WCF 訊息內文** 區段中，按一下 **範本-由範本指定內容** 選項按鈕。 在 **XML** BizTalk 主體的格式應該是文字方塊中，   
    \<**bts 訊息主體 xmlns ="http://www.microsoft.com/schemas/bts2007"編碼方式 ="[xml&#124;base64&#124;十六進位&#124;字串]"/** \> (有效的值，也就是區分大小寫，編碼為 xml&#124;base64&#124;十六進位&#124;字串)