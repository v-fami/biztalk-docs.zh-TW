---
title: 無法匯出服務端點設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 795145fa-0ce4-498f-a82e-eb752a5f4764
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2418517b7695aedd5c80a950a9b74faf5d380346
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973351"
---
# <a name="unable-to-export-service-endpoint-configuration"></a>無法匯出服務端點組態
## <a name="details"></a>詳細資料  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  產品名稱   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| 產品版本 |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    事件識別碼     |                                         0                                          |
|  事件來源   |                                         0                                          |
|    元件    |                                         0                                          |
|  符號名稱  |                                         0                                          |
|  訊息文字   |              無法將服務端點組態匯出到"{0}」              |
  
## <a name="explanation"></a>說明  
 此錯誤表示使用者可能沒有寫入目的地的權限。 或某些必要的屬性未正確指定，例如位址 (URI) 和繫結類型。  
  
## <a name="user-action"></a>使用者動作  
 您可以使用下列程序來設定的端點身分識別。  
  
#### <a name="to-configure-the-endpoint-identity"></a>若要設定的端點身分識別  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。  
  
2. 在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3. 找出您的應用程式，然後找出您的傳輸。  
  
4. 以滑鼠右鍵按一下傳輸名稱。  
  
5. 按一下 **[屬性]**。  
  
6. 在 連接埠**型別**清單中，選取正確的連接埠。  
  
7. 按一下 **設定**。  
  
8. 在 WCF **[**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**繫結** 索引標籤。  
  
9. 請確定允許的目的地資料夾的寫入。  
  
10. 請檢查**行為** 索引標籤和**端點身分識別**中的設定**一般**索引標籤，確定其皆有效。  
  
    > [!NOTE]
    >  您必須在目的地資料夾中具有寫入權限。 請連絡機器的系統管理員，以取得這些權限。