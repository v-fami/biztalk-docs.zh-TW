---
title: "管理商務設定檔 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.admin.resultsobject.businessprofile
ms.assetid: cf98c5a4-71bb-440b-8172-717ed0eb8373
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 434979376e679f1098557dc5b55f50e599ed21cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="managing-business-profiles"></a>管理商務設定檔
商務設定檔代表組織中的商務部門。 就像組織可以有各種部門，合作對象可以有各種[商務設定檔](http://msdn.microsoft.com/library/f8286130-57fe-40ed-9fd8-81da2c8baaaf)。 
  
商務設定檔代表組織中的商務部門。 就像組織可以有許多部門一樣 (會計、採購、出貨等)，合作對象也可以有許多商務設定檔，分別代表組織中的各部門。 商務設定檔屬性包含下列資訊：  
  
-   一般資訊，例如商務設定檔名稱  
  
-   可以與商務設定檔產生關聯的唯一識別項  
  
-   編碼設定 （適用於 X12 與 EDIFACT 訊息） 和[通訊協定設定](../core/protocol-settings.md)(AS2)，定義如何在商務設定檔可以傳送或接收來自另一個合作對象的訊息。  
  
本主題說明如何建立、 檢視、 編輯或刪除商務設定檔。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
## <a name="create-a-business-profile"></a>建立商務設定檔  
  
1.  在**BizTalk Server 管理**，展開 [BizTalk 群組] 並選取**合作對象**。 
2. 在**合作對象與商務設定檔**選取窗格中，以滑鼠右鍵按一下合作對象 a**新增**，然後選取**商務設定檔**。  
  
3.  在**一般**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|輸入商務設定檔名稱。|  
    |**說明**|輸入商務設定檔的說明。|  
    |**其他屬性 – 名稱/值**|請輸入名稱-值組來儲存合作對象的任何資訊。 您可以視需要新增任意數目的名稱-值組。 **注意：**名稱 / 值組不會由 BizTalk Server 進行任何處理; 此資料僅供資訊。|  
    |**Delete**|選取即可刪除選取的名稱 / 值組。|  
  
4.  視需要新增商務設定檔的商務識別。 在**識別**索引標籤上，執行下列動作：  
  
    > [!NOTE]
    >  在此階段，新增商務識別並非必要動作。 您可以更新版本中，新增商務識別，做為商務設定檔的協議的一部分。 如果您選擇要新增商務識別現在，他們就可以建立此商務設定檔的協議時。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|選取空白資料格，然後從下拉式方格中，選取提供給組織的獨特的商務識別驗證內文。 例如， **D-U-N-S (Dun & Bradstreet)**。 兩個商務夥伴可以選擇一個彼此都同意的商務識別。 如需這類案例中，選取**使用者相互定義**（適用於 EDIFACT) 或**使用者相互定義 (X12)** （適用 X12)。|  
    |**Qualifier**|會顯示您針對所選取的值為基礎的預先定義的值**名稱**。|  
    |**值**|輸入商務識別的值。 提供商務識別的值時，必須考量下列事項。<br /><br /> -針對指定的合作對象，您可以使用相同的識別名稱與識別值組合的多個商務設定檔。 例如，您可以讓兩個商務設定檔的合作對象**名稱**為**使用者相互定義 (X12)**和**值**為**THEM**。<br />-透過合作對象，您不能有兩個商務設定檔使用相同的識別名稱與識別值組合。|  
    |**移除**|選取要移除選取的識別。|  
  
5.  視需要，新增 X12 編碼訊息、 EDIFACT 編碼訊息或 AS2 傳輸的通訊協定設定的通訊協定設定。 請參閱[設定商務設定檔屬性](../core/configuring-business-profile-properties.md)。  
  
6.  選取**套用**接受這些屬性，或選取**確定**來完成組態設定。 任何一項動作會驗證設定。  
  
## <a name="view-or-change-a-business-profile"></a>檢視或變更商務設定檔  
  
1.  在**BizTalk Server 管理**，選取**合作對象**。 

2. 在**合作對象與商務設定檔**] 窗格中，展開 [合作對象節點以查看其下方的商務設定檔。 以滑鼠右鍵按一下您想要編輯，然後選取 商務設定檔**屬性**。  
  
3.  在**設定檔屬性** 對話方塊中，檢視或編輯設定檔。 如需有關可以在不同的頁面指定之值的詳細**設定檔屬性**對話方塊中，請參閱[設定商務設定檔屬性](../core/configuring-business-profile-properties.md)。  
  
4.  選取**套用**接受這些屬性，或選取**確定**來完成組態設定。 任何一項動作會驗證設定。  

## <a name="delete-a-business-profile"></a>刪除商務設定檔  
  
1.  在**BizTalk Server 管理**，選取**合作對象**。  
  
3.  在**合作對象與商務設定檔**] 窗格中，展開 [合作對象節點以查看其下方的商務設定檔。  
  
4.  以滑鼠右鍵按一下您想要刪除，然後選取 在商務設定檔**刪除**。 
  
5.  在**確認刪除商務設定檔**對話方塊中，選取**是**刪除商務設定檔。  


## <a name="see-also"></a>另請參閱  
 [管理 EDI 和 AS2 解決方案](../core/managing-edi-and-as2-solutions.md)