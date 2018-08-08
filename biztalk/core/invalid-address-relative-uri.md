---
title: 無效的位址 (相對 uri) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9a953f3e-3768-4e61-8f25-ea958a5a701a
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd362112a8edff37650aaa83da9c6ab33d0d697a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37017396"
---
# <a name="invalid-address-relative-uri"></a>無效的位址 (相對 uri)
## <a name="details"></a>詳細資料  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  產品名稱   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| 產品版本 |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    事件識別碼     |                                        000                                         |
|  事件來源   |                                         0                                          |
|    元件    |                                         0                                          |
|  符號名稱  |                                         0                                          |
|  訊息文字   |                  無效的位址配置;必須是"{0}」 配置。                   |
  
## <a name="explanation"></a>說明  
 您未提供的外掛式的 WCF 接收位置的語式正確的相對位址。 比方說， http://localhost/svc 無法運作，因為相對位址。 您無法設定的位址屬性的外掛式 WCF 接收位置的絕對位址。  
  
## <a name="user-action"></a>使用者動作  
 您可以使用下列程序來設定接收位置位址。  
  
#### <a name="to-configure-the-receive-location-address"></a>若要設定接收位置位址  
  
1. 按一下 **開始**，按一下**所有程式**，按一下 **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** ，然後按一下**BizTalk Server 管理**。  
  
2. 在 [主控台根目錄中，展開**BizTalk Server 管理]**，展開**BizTalk 群組**，然後展開**應用程式**。  
  
3. 找出您的應用程式，並尋找您的傳輸。  
  
4. 以滑鼠右鍵按一下傳輸名稱。  
  
5. 按一下 **[屬性]**。  
  
6. 在 連接埠**型別**清單中，選取正確的連接埠。  
  
7. 按一下 **設定**。  
  
8. 在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**一般**] 索引標籤。  
  
9. 在 **位址 (URI)** 文字方塊中，變更地址，使其開始以正斜線 （"/"）。  
  
   如需有關接收位置，請參閱下列資源：  
  
-   [如何設定 Wcf-customisolated 接收位置](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [如何設定 Wcf-wshttp 接收位置](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [如何設定 Wcf-basichttp 接收位置](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)