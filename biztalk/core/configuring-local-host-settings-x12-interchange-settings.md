---
title: 設定本機主機設定 （X12 交換設定） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c66c1e63-c654-4ccb-b424-34c06f1ce94e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca40e971b4c19af1490fa320fc2eb303640a438b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006055"
---
# <a name="configuring-local-host-settings-x12-interchange-settings"></a>設定本機主機設定 (X12 交換設定)
本機主機設定控制了處理 EDI 交換的方式。 此頁面上的設定可分成兩個類別 - 接收者的設定 (用於內送交換) 與傳送者的設定 (用於外寄交換)。 在接收者的設定中，您可以指定輸入批次要分割為交易集或是保留。 若是保留，您就可以指定發生錯誤時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 是否暫停交換或交易集。 在傳送者的設定中，您可以指定為外寄訊息產生控制編號的方式。  
  
> [!NOTE]
>  此處所說明的設定也適用於 HIPAA 交換。  
> 
> [!IMPORTANT]
>  下列屬性已停用**合作對象 A]-> [合作對象 B**單向協議索引標籤，如果您清除**本機 BizTalk 可處理支援此合作對象傳送訊息的合作對象所接收的訊息**合作對象 a 的核取方塊  
> 
> - 下的所有屬性**寄件者的設定**一節。  
> 
>   同樣地，下列屬性會停用在相同的頁面上**合作對象 B]-> [合作對象 A**索引標籤上，如果您在建立合作對象 a 時選取此核取方塊  
> 
> - 下的所有屬性**接收者的設定**一節。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-local-host--receivers-settings"></a>若要設定本機主機 - 接收者的設定  
  
1. 建立 X12 編碼協議中所述[設定的一般設定 (X12)](../core/configuring-general-settings-x12.md)。 若要更新現有的協議，以滑鼠右鍵按一下協議**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2. 在單向協議索引標籤底下**交換設定**區段中，按一下**本機主機設定**。  
  
3. 清除**通知的路由設定為傳送管線在要求-回應接收埠**不同的通知傳送埠傳回。 將此屬性保持為選取狀態，即可在與雙向要求-回應接收埠關聯的傳送埠傳回通知。  
  
4. 若要指定通知中使用的交易集控制編號範圍，請輸入中的值**ACK 控制編號 (ST02)** 欄位。 在中間兩個欄位中輸入數值，並在必要時於前置詞和尾碼欄位中輸入英數字元值。 中間幾個欄位是必要欄位，其中包含控制編號的最小值與最大值；前置詞和尾碼則是選用欄位。 這三個欄位的最大長度都是 9 個字元。  
  
    若要重設目前的交易集控制編號的最小值，請按一下**重設**。 請檢查**重設為較低的限制，超出範圍時**重設下限的控制編號，一旦已超過最大值。  
  
5. 選取 **遮罩內容屬性中的安全性/授權/密碼資訊**啟用遮罩，防止資訊的內容屬性中的授權/密碼安全性資訊 （ISA2 和 ISA4 欄位） 核取方塊洩漏。  
  
   > [!NOTE]
   >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 收到訊息時，會將 ISA 標頭升級至訊息的內容中。 在沒有遮罩的情況下，任何具有系統管理員權限的人員都可以存取內容中的安全性資訊。 若要遮罩此資訊，請[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]取代資訊的每個字元**#** 字元。 這是單向的程序： **#** 字元無法轉換成實際的字元。  
  
6. 在 **輸入批次處理選項**下拉式清單中，執行下列動作：  
  
   1.  選取預設選項**將交換分割為交易集-暫停發生錯誤的交易集**以指定 BizTalk Server 應該剖析每個交易集的交換為個別的 XML 文件中。 然後，BizTalk Server 便會將適當的信封套用至交易集，並將交易集文件路由到 MessageBox 中。 使用此選項時，如果交換中的一或多個交易集驗證失敗，BizTalk Server 將只會暫停這些交易集。  
  
   2.  選取 **將交換分割為交易集-暫停發生錯誤的交換**以指定 BizTalk Server 應該剖析每個交易集的交換為個別的 XML 文件中。 然後，BizTalk Server 便會將適當的信封套用至交易集，並將交易集文件路由到 MessageBox 中。 使用此選項時，如果交換中的一或多個交易集的驗證失敗，BizTalk Server 便會暫停整個交換。  
  
   3.  選取 **保留交換-發生錯誤時暫停交換**以指定 BizTalk Server 應該讓交換維持不變，建立整個批次交換的 XML 文件。 使用此選項時，如果交換中的一或多個交易集的驗證失敗，BizTalk Server 便會暫停整個交換。  
  
   4.  選取 **保留交換-發生錯誤時暫停交易集**以指定 BizTalk Server 應該讓交換維持不變，建立整個批次交換的 XML 文件。 使用此選項時，如果交換中的一或多個交易集的驗證失敗，BizTalk Server 便只會暫停這些交易集，但繼續處理其他所有的交易集。  
  
       > [!NOTE]
       >  如果您選取**保留交換-發生錯誤時暫停交換**或是**保留交換-發生錯誤時暫停交易集**，交換、 群組和交易集區段屬性 （其中判斷 BizTalk Server 如何建立外寄交換的 ISA、 GS 和 ST 標頭） 不適用。 該交換、群組，以及將保留之交換中的交易集標頭，都會在傳送管線處理該交換的傳送時加以保留。  
  
### <a name="to-configure-local-host--senders-settings"></a>若要設定本機主機 - 傳送者的設定  
  
1.  針對**交換控制編號 (ISA13)**，輸入數字以供 BizTalk Server 產生外寄交換的交換控制編號值範圍。 輸入最小為 1，最大為 999999999 的數值。 這是必要的欄位。  
  
     若要重設控制編號，指定的最小值，請按一下**重設** 按鈕。 請檢查**重設為較低的限制，超出範圍時**自動重設為最小值 如果超過最大值。  
  
2.  針對**群組控制編號 (GS06)**，輸入 BizTalk Server 應該用於群組控制編號的數字的範圍。 輸入最少 1 個字元，最多 9 個字元的數字值。 這是必要的欄位。  
  
     若要重設的群組控制編號，指定的最小值，請按一下**重設** 按鈕。 請檢查**重設為較低的限制，超出範圍時**自動重設為最小值 如果超過最大值。  
  
3.  針對**交易集控制編號 (ST02)**，按一下**套用新識別碼**然後輸入選擇性的前置詞和後置詞的一系列的數字的值為必要的中間欄位及英數字元值。 這四個欄位的最大長度都是 9 個字元。  
  
     若要重設目前的交易集控制編號的最小值，請按一下**重設**。 選取 **重設為較低的限制，超出範圍時**的最小值重設控制編號，如果已超過最大值。  
  
4.  按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交換設定 (X12)](../core/configuring-interchange-settings-x12.md)