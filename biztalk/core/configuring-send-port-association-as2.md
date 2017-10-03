---
title: "設定傳送埠關聯 (AS2) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8624d4c-cee8-4072-bff7-2468d83a06de
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b509c8e89f60f195def01c1fa94ea7d415cfa1d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-send-port-association-as2"></a>設定傳送埠關聯 (AS2)
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用傳送埠關聯來解析外寄 AS2 訊息的協議。 解析 AS2 訊息所用協議的方法是，將訂閱該訊息的傳送埠和與協議相關聯的傳送埠進行比對。 本主題提供如何將傳送埠關聯至協議的指示。  
  
> [!IMPORTANT]
>  在 [!INCLUDE[prague](../includes/prague-md.md)] 中，傳送埠關聯是在協議層級完成。 但是在 BizTalk Server 2009 中，傳送埠是在合作對象層級受到關聯。 回溯相容性，**傳送埠**頁面也會提供做為合作對象屬性的一部分 (請參閱[設定一般合作對象屬性 (AS2)](../core/configuring-general-party-properties-as2.md))。 當您將傳送埠與協議相關聯後，傳送埠設定也會傳播到合作對象設定，而您就可以在此頁面看到該傳送埠關聯。 但是，並非反之亦然。 在您將傳送埠與合作夥伴相關聯後，該傳送埠無法自動出現在協議設定中。  
  
> [!IMPORTANT]
>  傳送埠關聯格線會停用此頁面如果您清除了**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。  
>   
>  只有在對應於合作對象送出交換屬性的單向協議索引標籤上，此格線才會變成停用狀態。 例如，如果您在兩個合作對象的合作對象 A 與合作對象 B 建立合作對象 a 清除該核取方塊，在方格上已停用**合作對象 a-> 合作對象 B**單向協議索引標籤。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-send-port-association"></a>若要設定傳送埠關聯  
  
1.  建立 AS2 協議中所述[設定一般設定 (AS2)](../core/configuring-general-settings-as2.md)。 若要更新現有的 AS2 協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤上，按一下 **傳送埠**。  
  
3.  按一下下方的空白儲存格**名稱**資料行，然後從下拉式清單中，選取 傳送埠與協議產生關聯。 **URI**資料行會顯示傳送埠位址。  
  
4.  若要移除傳送埠關聯，請選取 傳送埠的資料列，然後按一下**移除**。  
  
5.  若要查看傳送埠的屬性，選取 傳送埠的資料列，然後按一下**屬性**。  
  
6.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定 AS2 協議屬性](../core/configuring-as2-agreement-properties.md)