---
title: 無法建立繫結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fbe1bd54-6031-4f90-a445-c1647b382a1a
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 567b3d88ced85f427fde492cd3e68cefaaf47394
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999201"
---
# <a name="cannot-create-binding"></a>無法建立繫結
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                               |
| 產品版本 |                                           [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                           |
|    事件識別碼     |                                                                       0                                                                        |
|  事件來源   |                                                                       0                                                                        |
|    元件    |                                                                       0                                                                        |
|  符號名稱  |                                                                       0                                                                        |
|  訊息文字   | 無法建立繫結，因為未指定繫結類型。 指定繫結類型，例如"basicHttpBinding"、"wsHttpBinding"或"customBinding |
  
## <a name="explanation"></a>說明  
 您未設定 BindingType 屬性程式碼中設定 Wcf-custom 或 Wcf-customisolated 傳輸之後。 或者，問題可能是其他程式碼路徑中。 值必須在繫結設定的使用者介面中。 檢閱組態，並確定已從下拉式清單中，接收位置屬性 區域中選定繫結類型。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，檢閱設定 Wcf-custom 或 Wcf-customisolated 傳輸的程式碼。 請確認**BindingType**屬性中的 XML 資料**TransportTypeData** ITransportInfo 介面的屬性已正確設定。  
  
 此外，指定繫結型別**basicHttpBinding**， **wsHttpBinding**，或**customBinding**。  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。  
  
2. 在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3. 找出您的應用程式，然後找出您的傳輸。  
  
4. 以滑鼠右鍵按一下傳輸名稱。  
  
5. 按一下 **[屬性]**。  
  
6. 在 連接埠**型別**清單中，選取正確的連接埠。  
  
7. 按一下 **設定**。  
  
8. 在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**繫結**] 索引標籤。  
  
9. 請確定指定的值時，則在**繫結的型別**清單。  
  
   如需有關如何設定繫結的詳細資訊，請參閱下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  
  
-   [如何設定 Wcf-customisolated 接收位置](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [如何設定 Wcf-custom 接收位置](../core/how-to-configure-a-wcf-custom-receive-location.md)  
  
-   [如何設定 Wcf-custom 傳送埠](../core/how-to-configure-a-wcf-custom-send-port.md)