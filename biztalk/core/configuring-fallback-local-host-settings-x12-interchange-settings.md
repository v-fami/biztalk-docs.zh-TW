---
title: 設定後援本機主機設定 （X12 交換設定） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b552fa2b-1154-491f-9bcf-aaba3b8f343f
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57763ad613025f475ae141a884bd9994a8e8a209
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012559"
---
# <a name="configuring-fallback-local-host-settings-x12-interchange-settings"></a>設定後援本機主機設定 (X12-交換設定)
本機主機設定控制了處理 EDI 交換的方式。 此頁面上的設定可分成兩個類別 - 接收者的設定 (用於內送交換) 與傳送者的設定 (用於外寄交換)。 在接收者的設定中，您可以指定 ST02 (通知控制編號) 的產生方式。 在傳送者的設定中，您可以指定為外寄訊息產生控制編號的方式。  
  
> [!NOTE]
>  此處所說明的設定也適用於 HIPAA 交換。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-local-host--receivers-settings"></a>若要設定本機主機 - 接收者的設定  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**X12 後援設定**。  
  
2. 在  **X12 後援設定**對話方塊中，於**X12 協議頁面**索引標籤之下**交換設定**區段中，按一下**本機主機設定**.  
  
3. 若要指定通知中使用的交易集控制編號範圍，請輸入中的值**ACK 控制編號 (ST02)** 欄位。 在中間兩個欄位中輸入數值，並在必要時於前置詞和尾碼欄位中輸入英數字元值。 中間幾個欄位是必要欄位，其中包含控制編號的最小值與最大值；前置詞和尾碼則是選用欄位。 這三個欄位的最大長度都是 9 個字元。  
  
    若要重設目前的交易集控制編號的最小值，請按一下**重設**。 請檢查**重設為較低的限制，超出範圍時**重設下限的控制編號，一旦已超過最大值。  
  
### <a name="to-configure-local-host--senders-settings"></a>若要設定本機主機 - 傳送者的設定  
  
1.  針對**交換控制編號 (ISA13)**，輸入數字以供 BizTalk Server 產生外寄交換的交換控制編號值範圍。 輸入最小為 1，最大為 999999999 的數值。 這是必要的欄位。  
  
     若要重設控制編號，指定的最小值，請按一下**重設** 按鈕。 請檢查**重設為較低的限制，超出範圍時**自動重設為最小值 如果超過最大值。  
  
2.  針對**群組控制編號 (GS06)**，輸入 BizTalk Server 應該用於群組控制編號的數字的範圍。 輸入最少 1 個字元，最多 9 個字元的數字值。 這是必要的欄位。  
  
     若要重設的群組控制編號，指定的最小值，請按一下**重設** 按鈕。 請檢查**重設為較低的限制，超出範圍時**自動重設為最小值 如果超過最大值。  
  
3.  針對**交易集控制編號 (ST02)**，按一下**套用新識別碼**，然後輸入選擇性的前置詞和後置詞的一系列的數字的值為必要的中間欄位及英數字元值。 這四個欄位的最大長度都是 9 個字元。  
  
     若要重設目前的交易集控制編號的最小值，請按一下**重設**。 選取 **重設為較低的限制，超出範圍時**的最小值重設控制編號，如果已超過最大值。  
  
4.  按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交換處理的 X12 後援協議屬性](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)