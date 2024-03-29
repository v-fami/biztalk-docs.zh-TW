---
title: 如何設定 BizTalk Server 來傳送加密的 MIME/SMIME 訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 14f67152-5f80-4040-a9d6-0819fab7fcb5
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02f8bb1c1cb11df4d3438f6a8d8af38edf547ea7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981279"
---
# <a name="how-to-configure-biztalk-server-to-send-encrypted-mimesmime-messages"></a>如何設定 BizTalk Server 傳送加密的 MIME/SMIME 訊息
本主題描述如何設定 BizTalk Server 以使用憑證來傳送加密的 MIME/SMIME 訊息。 下列程序也適用於設定透過 AS2 傳輸的加密訊息傳送。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本主題中的程序，您必須為 BizTalk Server 系統管理員群組的成員登入。  
  
### <a name="to-configure-biztalk-server-to-send-encrypted-messages"></a>若要設定 BizTalk Server 傳送加密的訊息  
  
1. 建立管線來傳送加密的訊息，如下所示：  
  
   > [!NOTE]
   >  設定 AS2 傳輸來傳送加密的訊息，AS2EdiSend 和 AS2Send 管線，因為包含在時，不需要此步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]做這個函式。  
  
   1.  建立傳送管線，然後將 MIME/SMIME 編碼器管線元件拖曳至管線的 「 編碼 」 階段。  
  
   2.  在 [**屬性**] 視窗中，設定 MIME/SMIME 編碼器管線元件啟用加密內容 **，則為 True**。  
  
       > [!NOTE]  
       >  將管線部署至 BizTalk 群組之後，您可以使用 BizTalk Server 管理主控台來設定管線元件屬性。  
  
   3.  建置和部署傳送管線。  
  
2. 設定傳送埠來傳送加密的訊息，如下所示：  
  
   1.  新增您建立的資料包含 BizTalk 應用程式包括的接收位置來接收加密的訊息的傳送管線的 BizTalk 組件。  
  
       > [!NOTE]  
       >  設定 AS2 傳輸來傳送加密的訊息，因為 AS2Send 和 AS2EdiSend 管線會包含在 「 BizTalk EDI 應用程式時，不需要此步驟。  
  
   2.  您在上一個程序中建立的傳送管線的 BizTalk 應用程式中設定的傳送埠。  
  
   3.  將指定的加密憑證，以滑鼠右鍵按一下傳送埠，按一下您已安裝**屬性**，然後按一下**憑證**。 按一下 **瀏覽**，瀏覽至您想要指派給這個傳送埠，然後按一下 憑證**確定**。  
  
       > [!NOTE]  
       >  如果憑證不存在的本機電腦上，在**指紋**方塊中輸入或貼上憑證指紋，然後再按一下**確定**。 憑證指紋的格式為 HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH，其中 H 是十六進位數字。