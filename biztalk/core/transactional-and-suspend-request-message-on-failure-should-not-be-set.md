---
title: "交易選項&quot;交易式&quot;和錯誤處理選項&quot;擱置失敗的要求訊息&quot;應該不能兩者都設定為 false |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc6c66cc-6713-4396-b0d4-ac6a0e72164f
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf8c47e364fccdb310167e56c6556423c2d4b39d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="transactions-option-quottransactionalquot-and-the-error-handling-option-quotsuspend-request-message-on-failurequot-should-not-both-be-set-to-false"></a>交易選項&quot;交易式&quot;和錯誤處理選項&quot;擱置失敗的要求訊息&quot;應該不能兩者都設定為 false
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|「 交易式 」 中的 交易 選項和錯誤處理選項 「 擱置失敗的要求訊息 應該不能兩者都設定為 false 後可能會發生訊息遺失。 一個或兩個選項設為 true。|  
  
## <a name="explanation"></a>說明  
 Wcf-netmsmq 配接器的選項中**交易式**和**擱置失敗的要求訊息**應該不能兩者都設定為 false （未勾選）。 如果失敗的訊息提交不會回復為異動，雖然訊息不會暫停，而且不是儲存在訊息方塊中，可能會發生訊息遺失。  
  
## <a name="user-action"></a>使用者動作  
 您可以使用下列程序來確認配接器設定。  
  
#### <a name="to-verify-adapter-settings"></a>若要確認介面卡設定  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2.  在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  找出您的應用程式，然後再找出您的傳輸。  
  
4.  以滑鼠右鍵按一下傳輸名稱。  
  
5.  按一下 **[屬性]**。  
  
6.  在 連接埠**類型**清單中，選取正確的連接埠。  
  
7.  按一下**設定**。  
  
8.  在**Wcf-netmsmq 傳輸屬性**對話方塊中，按一下 [**繫結**] 索引標籤。  
  
9. 在**交易**區段中，決定如果**交易式**已核取。  
  
10. 按一下**訊息** 索引標籤。  
  
11. 決定如果**擱置失敗的要求訊息**已核取。  
  
    > [!NOTE]
    >  這些步驟僅適用於接收位置。