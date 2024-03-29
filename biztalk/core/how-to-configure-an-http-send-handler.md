---
title: 如何設定 HTTP 傳送處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send handlers, HTTP adapters
- configuring [HTTP adapters], send handlers
- HTTP adapters, send handlers
ms.assetid: 821bf30c-b220-4ded-953d-7e745c0698b9
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e3db1c7dd108bbd2aa9eb35dc4e3c3d7edba2f9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000399"
---
# <a name="how-to-configure-an-http-send-handler"></a>如何設定 HTTP 傳送處理常式
使用下列程序，來變更與 HTTP 傳送處理常式關聯的主控件。  

> [!NOTE]
>  每個主控件只可和一個傳送處理常式建立關聯。  
> 
> [!CAUTION]
>  當使用 HTTP 或 SOAP 配接器處理常式時，建議您安裝這些處理常式的主控件執行個體，在 Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]電腦。  

### <a name="to-change-global-variables-for-an-http-send-handler"></a>變更 HTTP 傳送處理常式的全域變數  

1. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，展開**BizTalk 群組**，展開**平台設定**，然後展開**配接器**。  

2. 在展開的配接器清單中，按一下**HTTP**，在右窗格以滑鼠右鍵按一下您想要設定的傳送處理常式，然後按一下**屬性**。  

3. 在 **配接器處理常式屬性**對話方塊的 **一般**索引標籤**主機名稱**清單中，選取與其相關聯的傳送處理常式的主控。  

4. 在 **屬性**索引標籤上，執行下列動作。  


   |         使用          |                                                                                                                                                                                                 以進行此動作                                                                                                                                                                                                  |
   |---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **要求逾時 （秒）** | 指定等待伺服器回應的逾時 (以秒為單位)。<br /><br /> 若設定為零 (0)，則 HTTP 配接器會根據要求訊息的大小來計算逾時。<br /><br /> 若未提供任何值，則會使用處理常式的值。<br /><br /> **預設值：** 0<br /><br /> **類型：** 長<br /><br /> **最小值：** 0<br /><br /> **最大值：** MAX_LONG |
   |   **重新導向上限**   |                                                                                                       指定允許訊息傳送的重新導向上限。<br /><br /> **預設值：** 5<br /><br /> **類型：** Int<br /><br /> **最小值：** 0<br /><br /> **最大值：** 10                                                                                                       |
   |     **內容類型**      |                                                                 指定要求訊息的內容類型。<br /><br /> 若未提供任何值，則會使用處理常式的值。<br /><br /> **預設值：** Text/XML<br /><br /> **類型：** 字串<br /><br /> **最小長度：** 0<br /><br /> **最大長度：** 256                                                                  |


5. 在  **Proxy**索引標籤上，執行下列動作。  


   |   使用    |                                                                                                                          以進行此動作                                                                                                                           |
   |---------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **使用 Proxy** |                                                                指定 HTTP 傳送處理常式是否要使用 Proxy 伺服器。<br /><br /> **預設值：** False<br /><br /> **類型：** 布林                                                                |
   |  **Server**   |               指定此傳送埠的 Proxy 伺服器位址。<br /><br /> 此屬性需要一個值，如果**使用 proxy**是 **，則為 True**。<br /><br /> **類型：** 字串<br /><br /> **最小長度：** 0<br /><br /> **最大長度：** 256                |
   |   **通訊埠**    | 指定此傳送埠的 Proxy 伺服器連接埠。<br /><br /> 此屬性需要一個值，如果**使用 proxy**是 **，則為 True**。<br /><br /> **預設值：** 80<br /><br /> **類型：** 長<br /><br /> **最小值：** 0<br /><br /> **最大值：** 65535 |
   | **使用者名稱** |      指定要用於 Proxy 伺服器驗證的使用者名稱。<br /><br /> 此屬性需要一個值，如果**使用 proxy**是 **，則為 True**。<br /><br /> **類型：** 字串<br /><br /> **最小長度：** 0<br /><br /> **最大長度：** 256       |
   | **密碼**  |        指定要用於 Proxy 伺服器驗證的使用者密碼。<br /><br /> 此屬性需要一個值，如果**使用 proxy**是 **，則為 True**。<br /><br /> **類型：** 字串<br /><br /> **最小長度：** 0<br /><br /> **最大長度：** 256        |


6. 按一下 [確定] 。  

## <a name="see-also"></a>另請參閱  
 [設定 HTTP 配接器](../core/configuring-the-http-adapter.md)