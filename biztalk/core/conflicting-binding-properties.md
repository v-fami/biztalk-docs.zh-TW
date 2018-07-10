---
title: 衝突的繫結屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b08c317e-a617-464b-9ee4-007fb41d99b2
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 271b9efa9d30d5c315bfd6061bfbf011289ea620
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012079"
---
# <a name="conflicting-binding-properties"></a>繫結屬性衝突
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                         |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                    |
| 產品版本 |                                               [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                |
|    事件識別碼     |                                                                            0                                                                            |
|  事件來源   |                                                                            0                                                                            |
|    元件    |                                                                            0                                                                            |
|  符號名稱  |                                                                            0                                                                            |
|  訊息文字   | 衝突的繫結屬性： MsmqAuthenticationMode ={0}和 MsmqProtectionLevel ={1}無效。 變更其中一個屬性，以解決衝突 |
  
## <a name="explanation"></a>說明  
 Wcf-netmsmq 傳輸 MSMQ 保護層級屬性設定為**登**或是**EncryptAndSign**無 MSMQ 驗證模式。  
  
## <a name="user-action"></a>使用者動作  
 MSMQ 保護等級或 MSMQ 保護層級屬性與一致的 [MSMQ 驗證模式] 屬性變更。  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。  
  
2. 在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3. 找出您的應用程式，然後找出您的傳輸。  
  
4. 以滑鼠右鍵按一下傳輸名稱。  
  
5. 按一下 **[屬性]**。  
  
6. 在 連接埠**型別**清單中，選取正確的連接埠。  
  
7. 按一下 **設定**。  
  
8. 在  **Wcf-netmsmq 傳輸屬性** 對話方塊中，按一下**安全性** 索引標籤。  
  
9. 檢查 MSMQ 中的值**驗證模式**清單並**MSMQ 保護等級**清單。  
  
   如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  
  
-   [如何設定 Wcf-netmsmq 傳送埠](../core/how-to-configure-a-wcf-netmsmq-send-port.md)  
  
-   [如何設定 Wcf-netmsmq 接收位置](../core/how-to-configure-a-wcf-netmsmq-receive-location.md)