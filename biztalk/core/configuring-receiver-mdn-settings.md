---
title: "設定接收者 MDN 設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eae6431d-a2b9-4889-a29c-720e801a644e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dafe17a0ad357b840b31d8a10c67e1ae3cc1e415
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-receiver-mdn-settings"></a>設定接收者 MDN 設定
在接收者 MDN 設定中，您可以根據 AS2 訊息標頭，指定控制 MDN 產生方式的屬性。  
  
> [!IMPORTANT]
>  任何屬性已停用**合作對象 a-> 合作對象 B**單向協議索引標籤，如果您清除了**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊合作對象 a。不過，所有屬性已停都用中相同頁面**合作對象 B-> 合作對象 A**索引標籤上，如果您建立合作對象 a 時選取此核取方塊  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-receiver-mdn-settings"></a>若要設定接收者 MDN 設定  
  
1.  建立 AS2 協議中所述[設定一般設定 (AS2)](../core/configuring-general-settings-as2.md)。 若要更新現有的 AS2 協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤底下**本機主機設定**區段中，按一下**接收者 MDN 設定**。  
  
3.  如果您沒有勾選**對驗證與 MDN 使用協議設定，而非訊息標頭**屬性**驗證** 頁面上，您可以選擇讓傳送 MDN 的合作對象簽署 MDN，如果會啟用產生 MDN**配置通知至**AS2 標頭，但**配置通知選項**標頭沒有啟用簽署。 這種情形**配置通知選項**未設定或設定為選擇性。 您可以按一下**簽署要求的 MDN，如果不預設配置通知選項標頭，或簽署回條通訊協定標頭設定為選擇性**。  
  
4.  您可以輸入中的文字**MDN 文字**讓傳送 MDN 將它加入至 MDN 訊息 （在 Content-description 欄位） 的合作對象的欄位。 不論 MDN 是根據 AS2 標頭還是協議屬性來產生，都適用這個設定。  
  
5.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定本機主機設定 (AS2)](../core/configuring-local-host-settings-as2.md)