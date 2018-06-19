---
title: 設定後援信封屬性 （EDIFACT 交易集設定） |Microsoft 文件
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
ms.openlocfilehash: c93f9aae6d67e5dc56d383626e36d1db412be9d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233718"
---
# <a name="configuring-fallback-envelope-properties-edifact-transaction-set-settings"></a>設定後援信封屬性 (EDIFACT 交易集設定)
在**信封**頁面**交易集設定** 區段中，您可以定義 BizTalk Server 如何產生傳送至合作對象之 EDIFACT 編碼交換的 UNG 區段。  
  
 UNG 區段是識別和指定 EDIFACT 編碼交換之功能群組的標頭。 其中包含準備功能群組的日期與時間資訊，以及功能群組中文件的類型與版本資訊。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-define-the-ung-segments"></a>若要定義 UNG 區段  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**EDIFACT 後援設定**。  
  
2.  在**EDIFACT 後援設定**對話方塊中，於**EDIFACT 協議頁面**索引標籤，下方**交易集設定**區段中，按一下**信封**.  
  
3.  如**功能群組識別碼 (UNG1)**，輸入最少一個字元，最多六個字元的英數字元值。 這是必要的欄位。  
  
4.  輸入值，以識別**應用程式傳送者 (UNG2)**。  
  
    -   如**識別 (UNG2.1)**，輸入最少一個字元，最多 35 個字元的英數字元值。 這是必要的欄位。  
  
    -   如**代碼辨識符號 (UNG2.2)**，輸入最少一個字元，最多四個字元的英數字元值。 這是選擇性欄位。  
  
5.  輸入值，以識別**應用程式收件者 (UNG3)**。  
  
    -   如**識別 (UNG3.1)**，輸入最少一個字元，最多 35 個字元的英數字元值。 這是必要的欄位。  
  
    -   如**代碼辨識符號 (UNG3.2)**，輸入最少一個字元，最多四個字元的英數字元值。 這是選擇性欄位。  
  
6.  如**控管單位 (UNG6)**，輸入最少一個字元，最多兩個字元的英數字元值。 這是必要的欄位。  
  
7.  輸入值，以識別**訊息版本 (UNG7)**。  
  
    -   如**版本 (UNG7.1)**，輸入最少一個字元，最多三個字元的英數字元值。 這是必要的欄位。  
  
    -   如**版次 (UNG7.2)**，輸入最少一個字元，最多三個字元的英數字元值。 這是必要的欄位。  
  
    -   如**關聯指定代碼 (UNG7.3)**，輸入最少 1 個字元，最多 6 個字元的英數字元值。 這是選擇性欄位。  
  
8.  如**應用程式密碼 (UNG8)**，輸入最少一個字元，最多 14 個字元的英數字元值。 這是必要的欄位。  
  
9. 按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [EDIFACT 後援協議屬性設定為交易集設定](../core/configuring-edifact-fallback-agreement-properties-for-transaction-set-settings.md)