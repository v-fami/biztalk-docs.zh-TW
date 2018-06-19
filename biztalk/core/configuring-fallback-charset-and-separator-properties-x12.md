---
title: 設定後援字元集與分隔符號屬性 (X12) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 477f4952-6a4e-4e98-a37f-f6e1fe7db3d3
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 633ea22c611eb0fab994fd62250b9cb9ff8a0f2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233838"
---
# <a name="configuring-fallback-charset-and-separator-properties-x12"></a>設定後援字元集與分隔符號屬性 (X12)
在後援協議中，您可以指定建立 X12 外寄訊息的信封時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 用來驗證合作對象屬性的字元集。 您也可以指定要在交換的區段中使用的分隔字元與結束字元。  
  
> [!NOTE]
>  此處所說明的設定也適用於 HIPAA 交換。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-the-character-set-and-separators"></a>若要設定字元集和分隔符號  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**X12 後援設定**。  
  
2.  在**X12 後援設定**對話方塊中，於**X12 協議頁面**索引標籤，下方**交換設定**區段中，按一下**字元集與分隔符號**.  
  
3.  從**要使用的字元集**下拉式清單中，選取 X12 字元集用來驗證您輸入協議屬性。  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 只會使用這個設定來驗證相關協議屬性的輸入值。 當接收管線或傳送管線進行執行階段處理時，將會忽略此字元集屬性。  
  
4.  如**資料項目**，輸入單一字元[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]用以分隔複合資料元素包含兩個或多個簡單資料元素，以及不屬於複合元素的簡單資料元素。 選取**Char**字元資料元素或**Hex**十六進位資料元素。 當您變更格式時，您所輸入的字元將自動變更**Char**至**Hex** ，反之亦然。  
  
5.  如**元件元素分隔符號 (ISA16)**，輸入單一字元[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]用以分隔複合資料元素中的簡單資料元素。 選取**Char**字元資料元素或**Hex**十六進位資料元素。 當您變更格式時，您所輸入的字元將自動變更**Char**至**Hex** ，反之亦然。  
  
6.  如**區段結束字元**，輸入單一字元[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]要用來表示 EDI 區段結束。 選取**Char**字元資料元素或**Hex**十六進位資料元素。 當您變更格式時，您所輸入的字元將自動變更**Char**至**Hex** ，反之亦然。  
  
7.  如**尾碼**，選取的字元，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]將是搭配區段識別項中，使用**無**， **CR** （歸位字元）、 **LF**（換行字元），或**CR LF** （歸位字元/換）。 如果您指定尾碼，區段結束字元資料元素即可為空白。 如果區段結束字元留白，您就必須指定尾碼。 區段結束字元和尾碼的組合可以是下列任何一項：  
  
    -   區段結束字元  
  
    -   區域結束字元 + 歸位字元  
  
    -   區域結束字元 + 歸位字元/換行字元  
  
    -   歸位字元  
  
    -   換行字元  
  
    -   歸位字元/換行字元  
  
8.  如果裝載資料含有也用來當做資料、 區段或元件分隔字元，請檢查**取代內容中的分隔符號**並指定取代字元。 產生 X12 外寄訊息時，內容資料中的所有分隔符號字元都將被取代為指定的字元。 選取**Char**字元資料元素或**Hex**十六進位資料元素。 當您變更格式時，您所輸入的字元將自動變更**Char**至**Hex** ，反之亦然。  
  
9. 按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定 X12 後援協議屬性的交換處理](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)