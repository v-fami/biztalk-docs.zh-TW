---
title: "如何建立 PeopleSoft Enterprise 的傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating send ports
- send ports, creating
ms.assetid: 374261ce-2cb5-4193-a0a2-658f989b2c60
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b6b5caa44976aec7a4afb8e0eccf5b1f8904111
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-send-ports-for-peoplesoft-enterprise"></a>如何建立 PeopleSoft Enterprise 的傳送埠
請依照下列步驟使用 BizTalk Server 管理主控台建立傳送埠。  
  
## <a name="creating-a-send-port"></a>建立傳送埠  
  
#### <a name="to-create-a-send-port"></a>建立傳送埠  
  
1.  在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 所需應用程式。  
  
2.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。  
  
3.  在**傳送埠屬性**對話方塊方塊中，執行下列動作：  
  
    1.  輸入傳送埠名稱，例如`SSOSendToPeopleSoft`。  
  
    2.  從**類型**下拉式清單中，選取**PeopleSoft**。  
  
    3.  從**傳送處理常式**下拉式清單中，選取 URI。  
  
    4.  從 傳送管線 下拉式清單中，選取  **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。  
  
    5.  從**接收管線**下拉式清單中，選取**[microsoft.biztalk.defaultpiplelines.xmlreceive]**。  
  
    6.  按一下**設定**以設定傳送埠。  
  
4.  在**PeopleSoft 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    1.  展開**配接器必要屬性**，並輸入**應用程式伺服器路徑**， **JAVA_HOME**，**使用者名**， **密碼**，以及 Jar 檔案，以連接至 Peoplesoft 系統。  
  
         您不需要設定登入資訊。  
  
    2.  在此清單中，選取您建立用來代表 PeopleSoft 系統的 SSO 分支機構應用程式。  
  
    3.  如**使用 SSO**，選取**是**。  
  
    4.  按一下 **[確定]**。  
  
5.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [建立 PeopleSoft 傳送處理常式](../core/creating-peoplesoft-send-handlers.md)