---
title: 交易選項&quot;Transactional&quot;和 錯誤處理選項&quot;失敗時擱置要求訊息&quot;應該不能兩者都設定為 false |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc6c66cc-6713-4396-b0d4-ac6a0e72164f
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3818ddba18b89aedd1185f5ad87f3682dd5686a7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971415"
---
# <a name="transactions-option-quottransactionalquot-and-the-error-handling-option-quotsuspend-request-message-on-failurequot-should-not-both-be-set-to-false"></a>交易選項&quot;Transactional&quot;和 錯誤處理選項&quot;失敗時擱置要求訊息&quot;應該不能兩者都設定為 false
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                  |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                |
| 產品版本 |                                                                            [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                                            |
|    事件識別碼     |                                                                                                        0                                                                                                         |
|  事件來源   |                                                                                                        0                                                                                                         |
|    元件    |                                                                                                        0                                                                                                         |
|  符號名稱  |                                                                                                        0                                                                                                         |
|  訊息文字   | 交易選項 「 交易式 」 和錯誤處理選項 「 失敗時擱置要求訊息 」 應該不能兩者都設定為 false 因為可能會造成訊息遺失。 請設定一個或兩個選項為 true。 |
  
## <a name="explanation"></a>說明  
 Wcf-netmsmq 配接器的選項中**Transactional**並**失敗時擱置要求訊息**應該不能兩者都設定為 false （未核取）。 如果失敗的訊息提交不會回復為交易，雖然訊息不會暫停，而不是儲存在訊息方塊中，可能會造成訊息遺失。  
  
## <a name="user-action"></a>使用者動作  
 您可以使用下列程序來確認介面卡設定。  
  
#### <a name="to-verify-adapter-settings"></a>若要確認介面卡設定  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。  
  
2. 在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3. 找出您的應用程式，然後找出您的傳輸。  
  
4. 以滑鼠右鍵按一下傳輸名稱。  
  
5. 按一下 **[屬性]**。  
  
6. 在 連接埠**型別**清單中，選取正確的連接埠。  
  
7. 按一下 **設定**。  
  
8. 在  **Wcf-netmsmq 傳輸屬性** 對話方塊中，按一下**繫結** 索引標籤。  
  
9. 在 **交易**區段中，判斷**交易式**已核取。  
  
10. 按一下 [**訊息**] 索引標籤。  
  
11. 判斷是否**失敗時擱置要求訊息**已核取。  
  
    > [!NOTE]
    >  這些步驟僅適用於對接收位置。