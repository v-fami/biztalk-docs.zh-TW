---
title: 設定簽署、 壓縮和加密 AS2 傳輸 |Microsoft 文件
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
ms.openlocfilehash: 88309f17e335708b6e73109972c6c02d75ee483c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233974"
---
# <a name="configuring-signing-compression-and-encryption-in-as2-transport"></a>設定 AS2 傳輸中的簽章、壓縮和加密
您可以從「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台」設定數位簽章、簽章驗證、加密和解密。 此設定需要您為 AS2 管線和 BizTalk 合作對象設定適當的屬性。  
  
## <a name="using-as2-pipelines"></a>使用 AS2 管線  
 為了保護輸入 AS2 訊息，請在您的接收位置中使用 AS2 接收管線 (AS2EdiReceive 或 AS2Receive)。 「AS2 解碼器」會針對 AS2 訊息解密、解壓縮和/或執行簽章驗證。 如需有關如何這麼的詳細資訊，請參閱的 < AS2 解碼器 > 一節[AS2 接收元件](../core/as2-receive-components.md)。  
  
 為了保護輸出 AS2 訊息，請在您的傳送埠中使用 AS2 傳送管線 (AS2EdiSend 或 AS2Send)。 「AS2 編碼器」會針對輸出 AS2 訊息執行簽署、壓縮和加密。 如需有關如何這麼的詳細資訊，請參閱的 < AS2 編碼器 > 一節[AS2 傳送元件](../core/as2-send-components.md)。  
  
> [!IMPORTANT]
>  一旦訊息已簽署，簽章 BLOB 便不得變更， 否則簽章會損毀。 界限標頭 (或界限標頭外的任何內容) 可以變更，但在界限標頭內的任何內容都不可以變更。  
  
## <a name="setting-as2-agreement-properties"></a>設定 AS2 協議屬性  
 您可以設定 AS2 協議屬性來設定簽章和加密處理，如下所示：  
  
-   簽署、 壓縮，和 （或) 加密輸出訊息，請檢查**訊息應該簽署**，**訊息應該壓縮**，和**訊息應該加密**屬性上的**驗證**（適用於外寄的 AS2 訊息） 中之單向協議索引標籤頁面**協議屬性** 對話方塊。  
  
-   若要要求簽署的 MDN 以回應輸出訊息，請檢查**要求 MDN**和**要求簽署的 MDN**屬性**通知 (Mdn)** 頁面單向協議索引標籤**協議屬性** 對話方塊。  
  
-   指定傳入的訊息簽署、 壓縮和/或加密，請檢查**對驗證與 MDN 使用協議設定，而非訊息標頭**屬性，**訊息應該簽署**屬性，**訊息應該壓縮**屬性，而**訊息應該加密**屬性**驗證**頁面的單向協議索引標籤 （適用於內送的 AS2 訊息） 的**協議屬性** 對話方塊。  
  
    > [!NOTE]
    >  當**對驗證與 MDN 使用協議設定，而非訊息標頭**屬性選取，所有內送訊息的標頭詳細資料會被忽略，處理該訊息會根據協議設定。  
  
-   若要選取的輸入的訊息屬性會覆寫時，指定簽署的 MDN 以回應傳入訊息，**對驗證與 MDN 使用協議設定，而非訊息標頭**屬性，檢查**要求簽署的 MDN**屬性**通知 (Mdn)** 頁面**協議屬性** 對話方塊。  
  
    > [!NOTE]
    >  當**對驗證與 MDN 使用協議設定，而非訊息標頭**屬性選取，所有內送訊息的標頭詳細資料會被忽略，處理該訊息會根據協議設定。  
  
-   若要指定簽署的 MDN 以回應傳入訊息，不會覆寫輸入的訊息屬性 (**對驗證與 MDN 使用協議設定，而非訊息標頭**清除)，但訊息標頭不指定簽章檢查**簽署要求的 MDN，如果配置通知選項標頭不存在，或簽署回條通訊協定標頭設定為選擇性**屬性**接收者 MDN 設定**頁面**協議屬性** 對話方塊。  
  
-   若要指定與外寄 AS2 訊息的 BizTalk 群組屬性中指定不同的簽署憑證，請選取**覆寫群組簽章憑證**中**簽章憑證**單向協議索引標籤的頁面**協議屬性**對話方塊方塊中，並指定簽署憑證。 如果設定此屬性，將會使用所提供的憑證簽署任何解析為協議的 AS2 訊息**簽章憑證**頁面上，並不是由憑證提供做為 BizTalk 群組屬性的一部分。  
  
 如需有關設定合作對象屬性的詳細資訊，請參閱[設定 AS2 屬性](../core/configuring-as2-properties.md)。  
  
## <a name="see-also"></a>另請參閱  
 [AS2 安全性](../core/as2-security.md)   
 [設定 AS2 的憑證](../core/configuring-certificates-for-as2.md)   
 [AS2 訊息](../core/as2-messages.md)   
 [AS2 接收元件](../core/as2-receive-components.md)   
 [AS2 傳送元件](../core/as2-send-components.md)   
 [設定 AS2 屬性](../core/configuring-as2-properties.md)