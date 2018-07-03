---
title: 設定後援信封屬性 （EDIFACT 交易集設定） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b56a5a93-35ac-4293-b00e-28dcd89dfa2a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f060b37004346ae5b7419acbe9f1fcf1d128179
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37020258"
---
# <a name="configuring-fallback-envelope-properties-edifact-transaction-set-settings"></a>設定後援信封屬性 (EDIFACT 交易集設定)
在 [**信封**頁面**交易集設定**] 區段中，您可以定義 BizTalk Server 如何產生傳送至合作對象的 EDIFACT 編碼交換的 UNG 區段。  
  
 UNG 區段是識別和指定 EDIFACT 編碼交換之功能群組的標頭。 其中包含準備功能群組的日期與時間資訊，以及功能群組中文件的類型與版本資訊。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-define-the-ung-segments"></a>若要定義 UNG 區段  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**EDIFACT 後援設定**。  
  
2. 在  **EDIFACT 後援設定**對話方塊中，於**EDIFACT 協議頁面**索引標籤之下**交易集設定**區段中，按一下**信封**.  
  
3. 針對**功能群組識別碼 (UNG1)**，輸入最少一個字元，最多 6 個字元的英數字元值。 這是必要的欄位。  
  
4. 輸入值，以找出**應用程式傳送者 (UNG2)**。  
  
   -   針對**識別 (UNG2.1)**，輸入最少一個字元，最多 35 個字元的英數字元值。 這是必要的欄位。  
  
   -   針對**代碼辨識符號 (UNG2.2)**，輸入最少一個字元，最多四個字元的英數字元值。 這是選擇性欄位。  
  
5. 輸入值，以找出**應用程式收件者 (UNG3)**。  
  
   -   針對**識別 (UNG3.1)**，輸入最少一個字元，最多 35 個字元的英數字元值。 這是必要的欄位。  
  
   -   針對**代碼辨識符號 (UNG3.2)**，輸入最少一個字元，最多四個字元的英數字元值。 這是選擇性欄位。  
  
6. 針對**控管單位 (UNG6)**，輸入最少一個字元，最多 2 個字元的英數字元值。 這是必要的欄位。  
  
7. 輸入值，以找出**訊息版本 (UNG7)**。  
  
   -   針對**版本 (UNG7.1)**，輸入最少一個字元，最多 3 個字元的英數字元值。 這是必要的欄位。  
  
   -   針對**版次 (UNG7.2)**，輸入最少一個字元，最多 3 個字元的英數字元值。 這是必要的欄位。  
  
   -   針對**關聯指定代碼 (UNG7.3)**，輸入最少 1 個字元，最多 6 個字元的英數字元值。 這是選擇性欄位。  
  
8. 針對**應用程式密碼 (UNG8)**，輸入最少一個字元，最多 14 個字元的英數字元值。 這是必要的欄位。  
  
9. 按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交易集設定的 EDIFACT 後援協議屬性](../core/configuring-edifact-fallback-agreement-properties-for-transaction-set-settings.md)