---
title: "設定傳送埠關聯 (X12) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 496beb0a-fabf-416e-bc3c-d8537097b50e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d81eee157c84677470e542c5d4ee5f9bf2cb5df5
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="configuring-send-port-association-x12"></a>設定傳送埠關聯 (X12)
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用傳送埠關聯以解析外寄 EDI 交換的協議。 解析 EDI 交換所用協議的方法是，將訂閱該訊息的傳送埠和與協議相關聯的傳送埠進行比對。 本主題提供如何將傳送埠關聯至協議的指示。  
  
> [!NOTE]
>  如果相同的傳送埠與多個協議關聯，BizTalk Server 會產生錯誤。  
  
> [!IMPORTANT]
>  在 BizTalk Server 傳送埠關聯是只能在協議層級。 但是在 BizTalk Server 2009 中，傳送埠是在合作對象層級受到關聯。 回溯相容性，**傳送埠**頁面也會提供做為合作對象屬性的一部分 (請參閱[設定一般合作對象屬性](../core/configuring-general-party-properties.md))。 當您將傳送埠與協議相關聯後，傳送埠設定也會傳播到合作對象設定，而您就可以在此頁面看到該傳送埠關聯。 但是，並非反之亦然。 在您將傳送埠與合作夥伴相關聯後，該傳送埠無法自動出現在協議設定中。  
  
> [!NOTE]
>  此處所說明的設定也適用於 HIPAA 交換。  
  
> [!IMPORTANT]
>  傳送埠關聯格線會停用此頁面如果您清除了**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。  
>   
>  只有在對應於合作對象送出交換屬性的單向協議索引標籤上，此格線才會變成停用狀態。 例如，如果您在兩個合作對象的合作對象 A 與合作對象 B 建立合作對象 a 清除該核取方塊，在方格上已停用**合作對象 a-> 合作對象 B**單向協議索引標籤。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-associate-send-ports-with-an-agreement"></a>若要將傳送埠與協議相關聯  
  
1.  建立 X12 編碼協議中所述[設定一般設定 (X12)](../core/configuring-general-settings-x12.md)。 若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤底下**交換設定**區段中，按一下**傳送埠**。  
  
3.  按一下下方的空白儲存格**名稱**資料行，然後從下拉式清單中，選取 傳送埠與協議產生關聯。 **URI**資料行會顯示傳送埠位址。  
  
4.  若要移除傳送埠關聯，請選取 傳送埠的資料列，然後按一下**移除**。  
  
5.  若要查看傳送埠的屬性，選取 傳送埠的資料列，然後按一下**屬性**。  
  
6.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>請參閱  
 [設定交換設定 (X12)](../core/configuring-interchange-settings-x12.md)