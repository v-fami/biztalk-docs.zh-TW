---
title: "無法匯出組態 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64f09af4-00a0-47cb-889e-d9aeb7266eb2
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bd7f27a2779819fff934008cc9924dfe01e6064
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-export-configuration"></a>無法匯出組態
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|無法匯出組態檔"{0}"|  
  
## <a name="explanation"></a>說明  
 某些必要的屬性未正確指定，例如位址 (URI) 和繫結類型。  
  
## <a name="user-action"></a>使用者動作  
 您可以使用下列程序來驗證屬性正確無誤。  
  
#### <a name="to-verify-properties"></a>若要確認屬性  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2.  在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  找出您的應用程式，然後再找出您的傳輸。  
  
4.  以滑鼠右鍵按一下傳輸名稱。  
  
5.  按一下 **[屬性]**。  
  
6.  在 連接埠**類型**清單中，選取正確的連接埠。  
  
7.  按一下**設定**。  
  
8.  在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**匯入/匯出**] 索引標籤。  
  
9. 按一下 **[匯出]**。  
  
10. 請確定已正確指定必要的屬性。 配置的位址 (URI) 必須正確地符合繫結型別。