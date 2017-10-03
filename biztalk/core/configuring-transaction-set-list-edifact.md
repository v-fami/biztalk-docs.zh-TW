---
title: "設定交易集清單 (EDIFACT) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b03ace75-70bf-47c9-9a94-df813d7cab1e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f6b4d9a5aae6c8758d3a6d4f46d18f9a820fabd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-transaction-set-list-edifact"></a>設定交易集清單 (EDIFACT)
[!INCLUDE[prague](../includes/prague-md.md)] 可讓您定義在處理 EDI 交換時要一律包括或排除的交易集清單。 本節提供如何建立交易集清單的指示。  
  
> [!IMPORTANT]
>  任何屬性已停用此頁面上即使您清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-a-transaction-set-list"></a>若要設定交易集清單  
  
1.  建立 EDIFACT 編碼協議中所述[設定一般設定 (EDIFACT)](../core/configuring-general-settings-edifact.md)。 若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤底下**交易集設定**區段中，按一下**交易集清單**。  
  
3.  選取**支援從清單中的交易集**選項，如果您想要建立必須一律先處理的交易集的清單。  
  
    > [!NOTE]
    >  如果您所收到的通常是特定交易類型 (例如 APERAK) 的交換，則應使用此選項。 在此情況下，您應將該交易類型新增至清單中，而使其他類型的交易集完全不會受到處理。  
  
4.  選取**排除交易集從清單**選項，如果您想要建立絕不處理的交易集的清單。  
  
    > [!NOTE]
    >  如果您所收到的通常是各種不同的交易類型，則應使用此選項。 在此情況下，您應將這些交易類型新增至您不會為其取得任何交易集的清單。  
  
5.  按一下空白儲存格**UNH2.1**資料行然後從下拉式清單中選取的交易集您想要排除的型別。  
  
6.  若要從清單中刪除交易類型，選取交易類型的資料列，然後按一下**刪除**。  
  
7.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交易集設定 (EDIFACT)](../core/configuring-transaction-set-settings-edifact.md)