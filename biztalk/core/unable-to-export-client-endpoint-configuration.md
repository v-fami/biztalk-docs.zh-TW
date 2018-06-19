---
title: 無法匯出用戶端端點組態 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d93fe5e-fdb2-49c5-86de-d428b1ecda7f
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 941d42ff01bcf578bd7ba7c426c6fe5ca2bfbce3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286950"
---
# <a name="unable-to-export-client-endpoint-configuration"></a>無法匯出用戶端結束點組態
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|無法將用戶端結束點組態匯出到 "{0}"|  
  
## <a name="explanation"></a>說明  
 此錯誤表示下列其中一個狀況：  
  
-   使用者沒有寫入目的地的權限。  
  
     \- 或 -  
  
-   某些必要的屬性未正確指定，例如**位址 (URI)** 和**繫結的型別**。  
  
## <a name="user-action"></a>使用者動作  
 使用下列程序來驗證使用者權限，並確認**位址 (URI)** 和**繫結的型別**設定是否有效。  
  
#### <a name="to-verify-user-permissions-and-confirm-settings"></a>確認使用者權限，並確認設定  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2.  在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  找出您的應用程式，然後再找出您的傳輸。  
  
4.  以滑鼠右鍵按一下傳輸名稱。  
  
5.  按一下 **[屬性]**。  
  
6.  在 連接埠**類型**清單中，選取正確的連接埠。  
  
7.  按一下**設定**。  
  
8.  在 WCF **[***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**繫結**] 索引標籤。  
  
9. 請確定允許寫入到目的資料夾。  
  
10. 請檢查**行為** 索引標籤和**端點身分識別**中的設定**一般**索引標籤，確定其皆有效。  
  
> [!NOTE]
>  您必須具有目的地資料夾寫入權限。 請連絡機器的系統管理員，以取得這些權限。