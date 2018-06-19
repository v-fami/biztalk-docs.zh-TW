---
title: 模稜兩可的憑證參考 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a7a6a60d-97e6-4c60-86be-83efb4a50f99
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 304ded9572ba6598f7f2132a678a14b2b3301c10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230702"
---
# <a name="ambiguous-certificate-reference"></a>模稜兩可的憑證參考
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|模稜兩可的憑證參考。找到一個以上的有效憑證|  
  
## <a name="explanation"></a>說明  
 找不到一個以上的有效憑證。  
  
#### <a name="user-action"></a>使用者動作  
 請確認只有一個已設定有效的憑證。  
  
## <a name="verify-certificate"></a>驗證憑證 
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2.  在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  找出您的應用程式，然後再找出您的傳輸。  
  
4.  以滑鼠右鍵按一下傳輸名稱。  
  
5.  按一下 **[屬性]**。  
  
6.  在 連接埠**類型**清單中，選取正確的連接埠。  
  
7.  按一下**設定**。  
  
8.  在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**一般**] 索引標籤。  
  
9. 按一下 **[編輯]**。  
  
10. 在**識別編輯器**對話方塊方塊中，請確定中的搜尋準則**憑證參考**區段已正確設定成指出憑證中的只有一個憑證**存放區名稱**。  
  
## <a name="verify-a-certificate-for-the-wcf-custom-and-the-wcf-customisolated-adapters"></a>Wcf-custom 和 Wcf-customisolated 配接器的驗證認證  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。  
  
2.  在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  找出您的應用程式，然後再找出您的傳輸。  
  
4.  以滑鼠右鍵按一下傳輸名稱。  
  
5.  按一下 **[屬性]**。  
  
6.  在 連接埠**類型**清單中，選取正確的連接埠。  
  
7.  按一下**設定**。  
  
8.  在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**行為**] 索引標籤。  
  
9. 請確定中的搜尋準則**憑證參考**區段已正確設定成指出憑證中的只有一個憑證**存放區名稱**。  
  
10. 在 [憑證] 嵌入式管理單元，請確定只有一個憑證已安裝 WCF 傳輸到您設定的搜尋準則。  
  
## <a name="see-also"></a>另請參閱
[WCF 配接器安裝憑證](../core/installing-certificates-for-the-wcf-adapters.md)  
 