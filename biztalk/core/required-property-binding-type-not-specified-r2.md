---
title: "所需的屬性繫結類型未指定 (R2) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8e45783-6454-44e2-867e-e30092725f51
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a34de62453bd252e110edd0caf8a71996f25ae3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="required-property-binding-type-not-specified-r2"></a>未指定必要的繫結類型屬性 (R2)
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|未指定必要的繫結類型屬性|  
  
## <a name="explanation"></a>說明  
 設定 WCF-Custom 或 WCF-CustomIsolated 傳輸時，您未設定 [繫結類型] 屬性。  
  
## <a name="user-action"></a>使用者動作  
 您可以使用下列程序來設定繫結類型屬性。  
  
#### <a name="to-configure-the-binding-type-property"></a>若要設定的繫結類型屬性  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2.  在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  找出您的應用程式，然後再找出您的傳輸。  
  
4.  以滑鼠右鍵按一下傳輸名稱。  
  
5.  按一下 **[屬性]**。  
  
6.  在 連接埠**類型**清單中，選取正確的連接埠。  
  
7.  按一下**設定**。  
  
8.  在**WCF-[***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**繫結**] 索引標籤。  
  
9. 中指定值**繫結的型別**清單。  
  
 如需有關如何設定繫結的詳細資訊，請參閱下列資源：  
  
-   [如何設定 Wcf-customisolated 接收位置](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [如何設定 Wcf-custom 接收位置](../core/how-to-configure-a-wcf-custom-receive-location.md)  
  
-   [如何設定 Wcf-custom 傳送埠](../core/how-to-configure-a-wcf-custom-send-port.md)