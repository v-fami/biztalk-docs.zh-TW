---
title: 設定後援信封屬性 （X12 交易集設定） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a951f70-07d5-4a58-b1ea-e7117a45c545
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6225a931a991d4b4fb85a23525c53fe01f9e52db
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021371"
---
# <a name="configuring-fallback-envelope-properties-x12-transaction-set-settings"></a>設定後援信封屬性 (X12-交易集設定)
在 [**信封**頁面**交易集設定**] 區段中，您可以定義 BizTalk Server 如何產生傳送至合作對象的 X12 編碼交換的 GS 區段。 GS 區段可識別並指定 X12 編碼交換的功能群組。  
  
> [!NOTE]
>  這個主題也適用於 HIPAA 相關設定。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-define-the-gs-segments"></a>定義 GS 區段  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**X12 後援設定**。  
  
2. 在  **X12 後援設定**對話方塊中，於**X12 協議頁面**索引標籤之下**交易集設定**區段中，按一下**信封**.  
  
3. 針對**功能代碼 (GS01)**，從下拉式清單中選取值。  
  
4. 針對**應用程式傳送者 (GS02)**，輸入最少 2 個，最多 15 個英數字元值。 這是必要的欄位。  
  
5. 針對**應用程式接收者 (GS03)**，輸入最少 2 個，最多 15 個英數字元值。 這是必要的欄位。  
  
6. 針對**日期格式 (GS04)**，從下拉式清單中選取 CCYYMMDD 或 YYMMDD。 這是必要的欄位。  
  
7. 針對**時間格式 (GS05)**，從下拉式清單中選取 HHMM、 HHMMSS 或 HHMMSSdd。 這是必要的欄位。  
  
8. 針對**負責單位 (GS07)**，從下拉式清單中選取值。  
  
9. 針對**文件識別項 (GS08)**，輸入最少 1 個，最多 12 個英數字元值。 這是選擇性欄位。  
  
10. 按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交易集設定的 X12 後援協議屬性](../core/configuring-x12-fallback-agreement-properties-for-transaction-set-settings.md)