---
title: "需要未指定服務憑證指紋 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca853667-83b5-41f2-9b54-8117b87e27d3
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6dc43d9ed50aaacd108b275063cf00d18aea743
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="required-service-certificate-thumbprint-not-specified"></a>未指定必要的服務憑證指紋
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|未指定必要的服務憑證指紋|  
  
## <a name="explanation"></a>說明  
 未設定服務的 WCF 傳送埠的安全性設定所需的憑證屬性。  
  
## <a name="user-action"></a>使用者動作  
 您可以使用下列程序來設定服務憑證屬性。  
  
#### <a name="to-configure-the-service-certificate-property"></a>若要設定服務憑證屬性  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2.  在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  找出您的應用程式，然後再找出您的傳輸。  
  
4.  以滑鼠右鍵按一下傳輸名稱。  
  
5.  按一下 **[屬性]**。  
  
6.  在 連接埠**類型**清單中，選取正確的連接埠。  
  
7.  按一下**設定**。  
  
8.  在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**安全性**] 索引標籤。  
  
9. 請確認**服務憑證**屬性設定。  
  
 如需有關憑證的詳細資訊，請參閱下列資源：  
  
-   [WCF 配接器安裝憑證](../core/installing-certificates-for-the-wcf-adapters.md)