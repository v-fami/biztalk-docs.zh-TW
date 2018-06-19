---
title: 設定驗證 （X12 交換設定） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fdad7016-1d66-4d11-b620-c28368f00133
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0edfe66791fa5c041c66a3adddde61730afe54ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233270"
---
# <a name="configuring-validation-x12-interchange-settings"></a>設定驗證 (X12 交換設定)
X12 交換驗證產生設定會定義 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 如何在收到的交換中檢查重複的交換控制編號。  
  
> [!NOTE]
>  此處所說明的設定也適用於 HIPAA 交換驗證。  
  
> [!IMPORTANT]
>  任何屬性已停用此頁面上即使您清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-validation"></a>若要設定驗證  
  
1.  建立 X12 編碼協議中所述[設定一般設定 (X12)](../core/configuring-general-settings-x12.md)。 若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤底下**交換設定**區段中，按一下**驗證**。  
  
3.  選取**交換控制編號**核取方塊以啟用接收管線封鎖重複的交換。 若選取上述核取方塊，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將會檢查該交換控制編號，確定所接收交換的交換控制編號 (ISA13) 與該交換控制編號不相符。 如果偵測到相符項目時，接收管線不會處理交換。  
  
4.  如果**交換控制編號**選取時，在**檢查重複的 isa13 內**欄位中，輸入將使用特定執行檢查重複交換的天數交換控制編號。  
  
5.  選取**群組控制編號**，避免接收管線處理具有重複群組控制編號 (GS6) 的交換。  
  
6.  選取**交易集控制編號**，避免接收管線處理具有重複交易集控制編號 (ST2) 的交換。  
  
7.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交換設定 (X12)](../core/configuring-interchange-settings-x12.md)