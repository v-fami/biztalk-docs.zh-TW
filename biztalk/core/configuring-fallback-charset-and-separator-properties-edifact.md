---
title: 設定後援字元集和分隔符號屬性 (EDIFACT) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9eadc9c1-ebec-42f5-a9ca-06cb28bebcdf
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8d36df63d1bcad0ebd39bd828a1a9407e6cc480
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977103"
---
# <a name="configuring-fallback-charset-and-separator-properties-edifact"></a>設定後援字集和分隔符號屬性 (EDIFACT)
在後援協議中，您可以指定在建立 EDIFACT 外寄訊息的信封時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會用來驗證合作對象屬性的字元集 (UNA)。 您也可以指定要對交換中的區段使用的分隔符號和結束字元 (UNB)。  
  
 在 UNA 區段中，您可以定義 BizTalk Server 如何針對產生傳送至合作對象的 EDIFACT 編碼交換來產生 UNA 區段。 UNA 區段會定義在 EDIFACT 編碼的交換中，用來當做分隔符號和指標的字元。 只有當此交換包含非標準的分隔符號字元時，才能使用這個區段。  
  
 在 UNB 區段中，您可以定義要使用的 EDIFACT 字元集。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-the-character-set-and-separators"></a>若要設定字元集和分隔符號  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**EDIFACT 後援設定**。  
  
2. 在  **EDIFACT 後援設定**對話方塊的  **EDIFACT 協議頁面**索引標籤之下**交換設定**區段中，按一下**字元集和分隔符號**。  
  
3. 在 **語法 (UNB1)** 區段中，執行下列動作：  
  
   1.  針對**識別項 (UNB1.1)**，輸入要套用到外寄交換的 EDIFACT 字元集。 這是必要的欄位。  
  
   2.  針對**版本 (UNB1.2)**，選取一個介於**1**並**4**。 這是選擇性欄位。  
  
4. 在 **分隔符號**區段中，執行下列動作：  
  
   1.  針對**元件資料元素分隔符號 (UNA1)**，輸入元件資料元素分隔符號分隔複合資料元素內的簡單資料元素的值。 選取  **Char**字元資料元素或**Hex**十六進位資料元素。 如果您變更字元的格式，輸入的字元就會自動變更。  
  
   2.  針對**資料元素分隔符號 (UNA2)**，輸入會分隔複合資料元素，其中包含兩個或多個簡單資料元素或簡單資料元素不屬於複合資料元素分隔符號的值。 選取  **Char**字元資料元素或**Hex**十六進位資料元素。 如果您變更字元的格式，輸入的字元就會自動變更。  
  
   3.  針對**小數點標記 (UNA3)**，選取 外寄交換中使用的小數點標記。  
  
   4.  針對**釋放指示符號 (UNA4)**，輸入釋放指示符號，指出接下來的字元不是語法分隔符號、 結束字元或釋放字元，但屬於原始資料的值。 選取  **Char**字元資料元素或**Hex**十六進位資料元素。 如果您變更字元的格式，輸入的字元就會自動變更。  
  
   5.  針對**重複分隔符號 (UNA5)**，交易集內重複的區段用來分隔為重複分隔符號輸入值。 選取  **Char**字元資料元素或**Hex**十六進位資料元素。 如果您變更字元的格式，輸入的字元就會自動變更。  
  
   6.  針對**區段結束字元 (UNA6)**，指出 EDI 區段結尾的區段結束字元輸入的值。  
  
   7.  針對**UNA6 尾碼**，選取的字元，BizTalk Server 將搭配區段識別項，可能**無**， **CR** （歸位字元）、 **LF**（換行字元），或**CR LF** （歸位字元/換行）。 如果您指定尾碼，區段結束字元資料元素即可為空白。 如果區段結束字元留白，您就必須指定尾碼。 區段結束字元和尾碼的組合可以是下列任何一項：  
  
       -   區段結束字元  
  
       -   區域結束字元 + 歸位字元  
  
       -   區域結束字元 + 歸位字元/換行字元  
  
       -   歸位字元  
  
       -   換行字元  
  
       -   歸位字元/換行字元  
  
5. 按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證和接受變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交換處理的 EDIFACT 後援協議屬性](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)