---
title: 無法匯入組態 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2887da50-4f74-4259-a7d6-c87bc9b9fc58
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e565b466e4f9ce8af3745948952b4318a029ff2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286678"
---
# <a name="unable-to-import-configuration"></a>無法匯入組態
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|無法匯入組態檔"{0}"|  
  
## <a name="explanation"></a>說明  
 可能有這項錯誤的原因很多：  
  
-   組態檔可能包含無效的字元，以指定的編碼方式。  
  
-   根項目可能已遺失。  
  
-   根層級的資料可能不正確。  
  
> [!NOTE]
>  這種情況，以及使用者動作，僅適用於 Wcf-custom 和 WCF CustomIsolate 配接器。  
  
## <a name="user-action"></a>使用者動作  
 您可以使用下列程序，匯入有效的組態檔。  
  
#### <a name="to-import-a-valid-configuration-file"></a>若要匯入有效的組態檔  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2.  在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  找出您的應用程式，然後再找出您的傳輸。  
  
4.  以滑鼠右鍵按一下傳輸名稱。  
  
5.  按一下 **[屬性]**。  
  
6.  在 連接埠**類型**清單中，選取正確的連接埠。  
  
7.  按一下**設定**。  
  
8.  在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**匯入/匯出**] 索引標籤。  
  
9. 按一下 **[匯入]**。 匯入有效的完整組態檔。  
  
 您也可以藉由使用服務組態編輯器中將它開啟來確認組態檔的有效性 **(開始 > 所有程式 > Windows SDK)** （此步驟中假設您已安裝 Windows SDK）。開啟**svcConfigEditor.exe**並確認每一個屬性的組態檔。