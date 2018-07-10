---
title: WCF 用戶端必須允許模擬使用單一登入 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b5b9f294-4d8a-4a12-91e8-8d325db7c420
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2d5ebfc9853f10417c1d2ad2c41a0d2531ff6de
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971471"
---
# <a name="wcf-client-must-allow-impersonation-to-use-single-sign-on"></a>WCF 用戶端必須允許模擬使用單一登入
## <a name="details"></a>詳細資料  

|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  產品名稱   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| 產品版本 |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    事件識別碼     |                                         0                                          |
|  事件來源   |                                         0                                          |
|    元件    |                                         0                                          |
|  符號名稱  |                                         0                                          |
|  訊息文字   |           WCF 用戶端必須允許模擬使用單一登入            |

## <a name="explanation"></a>說明  
 在 接收位置中啟用單一登入 (SSO)，但 WCF 用戶端不允許模擬。  

## <a name="user-action"></a>使用者動作  
 請確定叫用服務的 WCF 用戶端允許模擬。  

1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。  

2. 在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  

3. 找出您的應用程式，然後找出您的傳輸。  

4. 以滑鼠右鍵按一下傳輸名稱。  

5. 按一下 **[屬性]**。  

6. 在 連接埠**型別**清單中，選取**Wcf-custom** (或**WCF CustomIsolate**)。  

7. 按一下 **設定**。  

8. 在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**行為**] 索引標籤。  

9. 在 **行為**區段中，按一下**ServiceAuthorization**。 在 **組態**區段中，屬性**ImpersonateCallerForAllOperations**應該設定為 **，則為 True**。  

10. 在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**其他**] 索引標籤。  

11. 在認證章節中，選取選項**使用單一登入**。
