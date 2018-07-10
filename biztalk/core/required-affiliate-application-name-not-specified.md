---
title: 未指定必要的分支機構應用程式名稱 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3e82a39-b052-4702-bfe2-700756a0ee6a
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5acadd366af7616bd84e1656fe3e5d75afd3673e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015301"
---
# <a name="required-affiliate-application-name-not-specified"></a>未指定必要的分支機構應用程式名稱
## <a name="details"></a>詳細資料  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  產品名稱   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| 產品版本 |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    事件識別碼     |                                         0                                          |
|  事件來源   |                                         0                                          |
|    元件    |                                         0                                          |
|  符號名稱  |                                         0                                          |
|  訊息文字   |                 未指定必要的分支機構應用程式名稱                  |
  
## <a name="explanation"></a>說明  
 **使用單一登入**，已經選取選項，但未指定分支機構應用程式名稱。  
  
## <a name="user-action"></a>使用者動作  
 您可以使用下列程序來設定分支機構應用程式名稱。  
  
#### <a name="to-configure-the-affiliate-application-name"></a>若要設定分支機構應用程式名稱  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。  
  
2. 在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**BizTalk 應用程式**。  
  
3. 找出您的應用程式，然後找出您的傳輸。  
  
4. 以滑鼠右鍵按一下傳輸名稱。  
  
5. 按一下 **[屬性]**。  
  
6. 在 連接埠**型別**清單中，選取**Wcf-custom**。  
  
7. 按一下 **設定**。  
  
8. 在  **Wcf-custom 傳輸屬性** 對話方塊中，按一下**認證** 索引標籤。  
  
9. 在 **使用者名稱認證**區段中，為指定值**分支機構應用程式**。  
  
   如需有關建立 SSO 分支機構應用程式，請參閱 [http://go.microsoft.com/fwlink/?LinkId=94347](http://go.microsoft.com/fwlink/?LinkId=94347)