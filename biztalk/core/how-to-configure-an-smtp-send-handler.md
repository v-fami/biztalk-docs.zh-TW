---
title: 如何設定 SMTP 傳送處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 2015-10-22
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send handlers, SMTP adapters
- SMTP adapters, send handlers
- configuring [SMTP adapters], send handlers
ms.assetid: b68a36ce-f0a5-4302-a405-bb154c935f47
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99dc71cf04d8a80b3a88630908a814957c83b8cb
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
ms.locfileid: "22248494"
---
# <a name="how-to-configure-an-smtp-send-handler"></a>如何設定 SMTP 傳送處理常式
您可以在「BizTalk 管理」主控台中設定 SMTP 傳送處理常式屬性。 若屬性不是在個別 SMTP 傳送埠中設定，這些傳送處理常式屬性就會當作傳送埠組態值。  
  
### <a name="to-change-global-variables-for-an-smtp-send-handler"></a>變更 SMTP 傳送處理常式的全域變數  
  
1.  在 BizTalk Server 管理主控台中，依序展開[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開 **配接器**。  
  
2.  在展開的配接器清單中，按一下  **SMTP**, ，在右窗格，以滑鼠右鍵按一下您想要設定的傳送處理常式，然後按一下 **屬性**。  
  
3.  在 **配接器處理常式屬性** 對話方塊的  **一般** 索引標籤的 **主機名稱** 清單中，選取主控件與傳送處理常式將會產生關聯，然後按一下 **屬性**。  
  
4.  在 **SMTP 傳輸屬性** 對話方塊的  **屬性** 索引標籤上，執行下列動作︰  
  
    |使用|動作|  
    |--------------|----------------|  
    |**SMTP 伺服器名稱和 TCP 連接埠**|**[!INCLUDE[bts2013r2](../includes/bts2013r2-md.md)]**<br /><br /> 必要。 輸入 SMTP 伺服器名稱和 （選擇性） 若要傳送訊息時使用的 TCP 連接埠號碼。 例如，您可以輸入︰<br /><br /> -mySMTPserver<br />-mySMTPserver.internet.com:2525<br /><br /> **在舊版的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**  （包括 BizTalk Server 2013)，僅輸入 SMTP 伺服器名稱。 TCP 連接埠 25 是硬式編碼。<br /><br /> 最大長度：256|  
    |**（電子郵件地址）**|必要。 輸入電子郵件地址，放在 SMTP **從** 標頭。<br /><br /> 最大長度：256|  
    |**驗證類型**|輸入要使用的 SMTP 伺服器的驗證類型。<br /><br /> 選項：<br /><br /> -   **不需要驗證**<br />-   **基本驗證**<br />-   **處理序帳戶 (NTLM)**<br /><br /> 預設值：處理帳戶 (NTLM)|  
    |**使用者名稱**|輸入要用於 SMTP 伺服器驗證的使用者名稱。<br /><br /> 此屬性需要一個值，如果 **驗證類型** 是 **基本驗證**。<br /><br /> 最小長度：00<br /><br /> 最大長度：256|  
    |**密碼**|輸入要用於驗證的 SMTP 伺服器的密碼。<br /><br /> 此屬性需要一個值，如果 **驗證類型** 是 **基本驗證**。<br /><br /> 最小長度：00<br /><br /> 最大長度：256|  
  
5.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [設定 SMTP 配接器](../core/configuring-the-smtp-adapter.md)