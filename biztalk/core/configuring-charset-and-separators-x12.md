---
title: 設定字元集和分隔符號 (X12) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6249f2e1-70b0-4960-bbc4-0c3fefd26faa
caps.latest.revision: 29
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9615e3cdcf46872ff2d07ecdff4ea7288f09f94f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976687"
---
# <a name="configuring-charset-and-separators-x12"></a>設定字元集與分隔符號 (X12)
在夥伴協議中，您可以指定建立 X12 外寄訊息的信封時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 用來驗證合作對象屬性的字元集。 您也可以指定要在交換的區段中使用的分隔字元與結束字元。  
  
> [!NOTE]
>  此處所說明的設定也適用於 HIPAA 交換。  
> 
> [!IMPORTANT]
>  下列屬性會停用此頁面上清除**本機 BizTalk 可處理支援此合作對象傳送訊息的合作對象所接收的訊息**時建立您要為其建立的合作對象 核取方塊協議。  
> 
> - **資料元素**  
>   -   **元件元素分隔符號 (ISA16)**  
>   -   **區段結束字元**  
>   -   **後置詞**  
>   -   **取代內容中的分隔符號**  
> 
>   只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。 例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 A]-> [合作對象 B**單向協議索引標籤。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-the-character-set-and-separators"></a>若要設定字元集和分隔符號  
  
1. 建立 X12 編碼協議中所述[設定的一般設定 (X12)](../core/configuring-general-settings-x12.md)。 若要更新現有的協議，以滑鼠右鍵按一下協議**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2. 在單向協議索引標籤底下**交換設定**區段中，按一下**字元集和分隔符號**。  
  
3. 從**要使用的字元集**下拉式清單中，選取 X12 字元集來驗證您輸入協議屬性。  
  
   > [!NOTE]
   >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 只會使用這個設定來驗證相關協議屬性的輸入值。 當接收管線或傳送管線進行執行階段處理時，將會忽略此字元集屬性。  
  
4. 針對**資料項目**，輸入單一字元[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]將用以分隔複合資料元素，其中包含兩個或多個簡單資料元素和不屬於複合元素的簡單資料元素。 選取  **Char**字元資料元素或**Hex**十六進位資料元素。 當您變更格式時，您所輸入的字元將會自動變更**Char**要**Hex** ，反之亦然。  
  
5. 針對**元件元素分隔符號 (ISA16)**，輸入單一字元[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]用來分隔複合資料元素內的簡單資料元素。 選取  **Char**字元資料元素或**Hex**十六進位資料元素。 當您變更格式時，您所輸入的字元將會自動變更**Char**要**Hex** ，反之亦然。  
  
6. 針對**區段結束字元**，請輸入單一字元，用以指出 EDI 區段的結尾。 選取  **Char**字元資料元素或**Hex**十六進位資料元素。  
  
    如果類型是**Char**，預設值是**~**。  
  
    如果類型是**Hex**，預設值是**7E**。  
  
    這是必要的資料元素。  
  
    這個項目限制為 ASCII 字元集中的值。 這個屬性不會根據 [一般] 頁面中定義的 X12 字元集進行驗證。  
  
    當您變更格式時，您所輸入的字元將會自動變更**Char**要**Hex** ，反之亦然。  
  
7. 針對**後置詞**，選取要使用的字元**使用**區段結束字元值。 這些選項包括：  
  
   - **無**: Default  
  
   - **CR**： 歸位字元  
  
   - **LF**： 換行字元  
  
   - **CR LF**： 歸位/換  
  
     區段結束字元和尾碼的組合可包含下列項目：  
  
   - **任何**區段結束字元 +**無**後置詞  
  
   - **任何**區段結束字元 + **CR**後置詞  
  
   - **任何**區段結束字元 + **CR LF**後置詞  
  
   - **D （十六進位）** 區段結束字元 +**無**尾碼： 這個組合就如同區段結束字元空白且尾碼設定為 CR。  
  
   - （十六進位） 區段結束字元 +**無**尾碼： 這個組合就如同區段結束字元空白且尾碼設定為 LF。  
  
   - **D （十六進位）** 區段結束字元 + **LF**尾碼： 這個組合就如同區段結束字元為 CR 且尾碼設定為 LF。  
  
8. 如果裝載資料含有也可以當作資料、 區段或元件分隔符號的字元，請檢查**取代內容中的分隔符號**並指定取代字元。 產生 X12 外寄訊息時，內容資料中的所有分隔符號字元都將被取代為指定的字元。 選取  **Char**字元資料元素或**Hex**十六進位資料元素。 當您變更格式時，您所輸入的字元將會自動變更**Char**要**Hex** ，反之亦然。  
  
9. 按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交換設定 (X12)](../core/configuring-interchange-settings-x12.md)