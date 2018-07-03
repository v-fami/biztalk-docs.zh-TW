---
title: 管理批次 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82755840-4e00-4fed-80e0-1a22b248c0bf
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af801bd6ec61c883d81e7ea6fd15e92f2186b777
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021525"
---
# <a name="managing-batches"></a>管理批次
如何以手動方式控制版本的批次交換，使用的控制項頂端**批次組態**頁面的單向協議索引標籤**協議屬性**對話方塊 (在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台) X12 和 EDIFACT 編碼的。 這項控制與下列控制項有關：  
  
- **啟動批次**。 啟動批次處理協調流程執行個體。 選取後**啟動**批次處理項目 按鈕，在啟動範圍內的執行個體時所收集。  
  
- **覆寫批次**。 建立批次使用現有的項目，並立即傳送。 在批次完成傳送之後，批次處理協調流程就會依據已建立的設定，繼續進行批次處理。  
  
- **停止批次**。 停用批次處理協調流程已啟動執行個體。 選取後**停止**按鈕，協調流程從現有的批次元素建立批次、 將交換傳遞給 EDI 傳送管線，並終止管線。  
  
  控制項處理單一批次組態。  
  
  當您按下時，BizTalk 所採取的動作**開始**取決於按鈕**篩選**準則，**版本**準則，和**啟用**範圍設定在**批次組態**頁面。 篩選準則決定哪些訊息要批次處理。 釋放準則決定何時要釋放批次。 啟動範圍屬性則決定已啟動的批次處理協調流程執行個體是否會收集批次處理項目。 如需有關這些設定的詳細資訊，請參閱 <<c0> [ 設定外寄批次](../core/configuring-an-outgoing-batch.md)。  

本主題說明如何啟動、 停止、 覆寫，以及刪除批次。  

> [!NOTE]
>  如需有關如何設定批次的指示，請參閱 <<c0> [ 設定 X12 批次處理](../core/configuring-batching-x12.md)或是[設定 EDIFACT 批次處理](../core/configuring-batching-edifact.md)。 
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
> [!NOTE]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員群組的成員可以啟動、停止或覆寫批次，但無法變更任何與批次處理相關的組態設定。 您必須是成員[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理員群組，來變更批次組態。  
  
## <a name="start-stop-and-override-batches"></a>啟動、 停止及覆寫批次  
  
1. 開啟 **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration**，展開 [BizTalk 群組]，然後選取**合作對象**。  
  
2. 在 **合作對象與商務設定檔**頁面的 **協議**區段中，以滑鼠右鍵按一下您想要啟動、 停止或覆寫批次組態的協議。  
  
3. 在單向協議索引標籤**協議屬性**，選取**批次組態**頁面。  
  
4. 在 **批次組態**頁面上，選取您想要啟動、 停止或覆寫批次的索引標籤。  
  
5. 確認篩選準則、釋放準則和啟動範圍屬性符合所需要的設定。  
  
   > [!NOTE]
   >  如果您是隸屬[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]操作員群組，而非[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組，您可以啟動、 停止或覆寫批次。 但是，您無法變更批次組態設定。 設定為可見，但如果您變更設定，且然後選取**確定**，得到的權限錯誤。  
  
6. 如果尚未啟動的批次處理協調流程執行個體，請選取**啟動**來啟動執行個體。  
  
   > [!NOTE]
   >  - 您所見，批次處理協調流程執行個體具有尚未啟動是否**開始** 按鈕已啟用，並**批次處理未啟動**下方顯示**啟動**控制項。  
   >  - 如果您已按下**開始**按鈕，並已啟動批次處理協調流程執行個體，但是批次收集任何項目，然後確認在 datetime**啟用**發生文字方塊。 如果沒有，則**啟用**日期必須設定為目前的日期或更早版本。  
  
7. 若要傳送的批次的交換，不符合釋放準則時，請選取**覆寫**。  
  
   > [!NOTE]
   >  選取**覆寫**批次的交換進行傳送，但不會影響批次處理協調流程執行個體，啟動準則或釋放準則的啟用狀態。  
  
8. 若要停用批次處理協調流程的執行個體，請選取**停止**。  
  
   > [!NOTE]
   >  選取**停止**導致批次的交換進行傳送，且正在終止批次處理協調流程執行個體。  
  
9. 選取  **確定**或是**取消**以關閉**協議屬性**。  

## <a name="delete-batches"></a>刪除批次  
  
1. 在   **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration**，選取**合作對象**。  
  
2. 在 **合作對象與商務設定檔**頁面的 **協議**區段中，以滑鼠右鍵按一下您想要刪除的批次組態的協議。  
  
3. 在單向協議索引標籤**協議屬性**對話方塊中，選取**批次組態**頁面。  
  
4. 在 **批次組態**頁面上，選取您想要刪除的批次的索引標籤。  
  
5. 在索引標籤頁面的右上角，選取**刪除**。  
  
6. 選取  **確定**以關閉**協議屬性**。  

  
## <a name="see-also"></a>另請參閱  
 [設定外寄批次](../core/configuring-an-outgoing-batch.md)  
 [管理 EDI 和 AS2 解決方案](../core/managing-edi-and-as2-solutions.md)