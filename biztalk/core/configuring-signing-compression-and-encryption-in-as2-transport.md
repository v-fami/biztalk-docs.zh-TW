---
title: 設定簽署、 壓縮和 AS2 傳輸中的加密 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bc3537a7-c065-4a33-a375-29e7902b5ffa
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a154255cb64fcebafa2ef8164714e46bf5673ba
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007199"
---
# <a name="configuring-signing-compression-and-encryption-in-as2-transport"></a>設定 AS2 傳輸中的簽章、壓縮和加密
您可以從「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台」設定數位簽章、簽章驗證、加密和解密。 此設定需要您為 AS2 管線和 BizTalk 合作對象設定適當的屬性。  
  
## <a name="using-as2-pipelines"></a>使用 AS2 管線  
 為了保護輸入 AS2 訊息，請在您的接收位置中使用 AS2 接收管線 (AS2EdiReceive 或 AS2Receive)。 「AS2 解碼器」會針對 AS2 訊息解密、解壓縮和/或執行簽章驗證。 如需有關執行操作的詳細資訊，請參閱的 < AS2 解碼器 > 一節[AS2 接收元件](../core/as2-receive-components.md)。  
  
 為了保護輸出 AS2 訊息，請在您的傳送埠中使用 AS2 傳送管線 (AS2EdiSend 或 AS2Send)。 「AS2 編碼器」會針對輸出 AS2 訊息執行簽署、壓縮和加密。 如需有關執行操作的詳細資訊，請參閱的 < AS2 編碼器 > 一節[AS2 傳送元件](../core/as2-send-components.md)。  
  
> [!IMPORTANT]
>  一旦訊息已簽署，簽章 BLOB 便不得變更， 否則簽章會損毀。 界限標頭 (或界限標頭外的任何內容) 可以變更，但在界限標頭內的任何內容都不可以變更。  
  
## <a name="setting-as2-agreement-properties"></a>設定 AS2 協議屬性  
 您可以設定 AS2 協議屬性來設定簽章和加密處理，如下所示：  
  
- 簽章、 壓縮，及/或加密輸出訊息，請檢查**訊息應該簽署**，**訊息應該壓縮**，並**訊息應該加密**上的屬性**驗證**（適用於外寄的 AS2 訊息） 中的單向協議索引標籤頁面**協議屬性** 對話方塊。  
  
- 若要要求簽署的 MDN 以回應輸出訊息，請檢查**要求 MDN**並**要求簽署的 MDN**上的屬性**通知 (Mdn)** 頁面單向協議索引標籤**協議屬性** 對話方塊。  
  
- 指定輸入的訊息簽署、 壓縮和/或加密，請檢查**使用協議設定進行驗證與 MDN 取代訊息標頭**屬性，**訊息應該簽署**屬性，**訊息應該壓縮**屬性，而**訊息應該加密**屬性**驗證**單向協議 頁面索引標籤 （適用於內送的 AS2 訊息）**協議屬性** 對話方塊。  
  
  > [!NOTE]
  >  當**使用協議設定進行驗證與 MDN 取代訊息標頭**選取屬性，會忽略所有內送訊息的標頭詳細資料和處理該訊息會根據協議設定。  
  
- 若要選取的輸入的訊息屬性會覆寫時，指定簽署的 MDN 以回應傳入訊息，**使用協議設定進行驗證與 MDN 取代訊息標頭**屬性，檢查**要求簽署的 MDN**上的屬性**通知 (Mdn)** 頁面**協議屬性** 對話方塊。  
  
  > [!NOTE]
  >  當**使用協議設定進行驗證與 MDN 取代訊息標頭**選取屬性，會忽略所有內送訊息的標頭詳細資料和處理該訊息會根據協議設定。  
  
- 時不會覆寫輸入的訊息屬性，以回應傳入訊息，指定簽署的 MDN (**使用協議設定進行驗證與 MDN 取代訊息標頭**清除)，但不會在訊息標頭指定簽章，請檢查**簽署要求的 MDN，如果配置通知選項標頭不存在，或簽署回條通訊協定標頭設為選擇性**屬性上的**接收者 MDN 設定**頁**協議屬性** 對話方塊。  
  
- 若要指定外寄 AS2 訊息的 BizTalk 群組屬性所指定不同的簽署憑證，請選取**覆寫群組簽章憑證**在**簽章憑證**頁面的單向協議索引標籤**協議屬性**對話方塊方塊中，並指定簽署的憑證。 如果設定此屬性，將會使用提供的憑證簽署任何解析為協議的 AS2 訊息**簽章憑證**頁面上，並不是由憑證提供做為 BizTalk 群組屬性的一部分。  
  
  如需有關設定合作對象屬性的詳細資訊，請參閱 <<c0> [ 設定 AS2 屬性](../core/configuring-as2-properties.md)。  
  
## <a name="see-also"></a>另請參閱  
 [AS2 安全性](../core/as2-security.md)   
 [設定 AS2 的憑證](../core/configuring-certificates-for-as2.md)   
 [AS2 訊息](../core/as2-messages.md)   
 [AS2 接收元件](../core/as2-receive-components.md)   
 [AS2 傳送元件](../core/as2-send-components.md)   
 [設定 AS2 屬性](../core/configuring-as2-properties.md)