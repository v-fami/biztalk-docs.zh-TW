---
title: 無效的 proxy 位址 （用於傳送處理常式和傳送埠） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ccedd23e-7d44-4419-b519-e04511e1f176
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d33af2f4fa068294c38ecb4146cd1f8d05d68aea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257814"
---
# <a name="invalid-proxy-address-for-send-handler-and-send-port"></a>無效的 proxy 位址 （用於傳送處理常式和傳送埠）
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|無效的 proxy 位址： {0}|  
  
## <a name="explanation"></a>說明  
 未提供 WCF 傳送處理常式或 WCF 傳送埠具有有效的 proxy 位址。  
  
## <a name="user-action"></a>使用者動作  
 您可以使用下列程序來設定 proxy 位址。  
  
#### <a name="to-configure-a-proxy-address"></a>若要設定的 proxy 位址  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** ，然後按一下**BizTalk Server 管理**。  
  
2.  在 主控台根目錄中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  找出您的應用程式，然後再找出您的傳輸。  
  
4.  以滑鼠右鍵按一下傳輸名稱。  
  
5.  按一下 **[屬性]**。  
  
6.  在 連接埠**類型**清單中，選取正確的連接埠。  
  
7.  按一下**設定**。  
  
8.  在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [ **Proxy** ] 索引標籤。  
  
9. 確認中的 proxy 位址**Proxy 設定**區段已正確設定。  
  
 如需有關傳送埠與傳送處理常式的詳細資訊，請參閱下列資源：  
  
-   [如何設定 Wcf-wshttp 傳送埠](../core/how-to-configure-a-wcf-wshttp-send-port.md)  
  
-   [如何設定 Wcf-basichttp 傳送埠](http://msdn.microsoft.com/library/acdb50fa-57fe-4657-9561-b6b2f4919c7f)  
  
-   [如何設定 Wcf-basichttp 傳送處理常式](http://msdn.microsoft.com/library/18dcc616-4732-42f8-bd64-e55a5ebbaa49)  
  
-   [如何設定 Wcf-wshttp 傳送處理常式](../core/how-to-configure-a-wcf-wshttp-send-handler.md)  
  
-   [如何設定 Wcf-custom 傳送埠](../core/how-to-configure-a-wcf-custom-send-port.md)