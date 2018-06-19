---
title: 步驟 6： 設定傳送埠，以便將資料傳送至您的組織 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 796570ca-8178-4679-9213-d67a2a189bf9
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b513725024aec755515ccac998745220ee5dfa7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277006"
---
# <a name="step-6-configure-a-send-port-to-send-data-to-your-organization"></a>步驟 6： 設定傳送埠，以便將資料傳送至您的組織
![步驟 6 的 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-6of9.gif "Step_6of9")  
  
 在這個步驟中，您會設定傳送埠，以便將 850 訊息從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送到代表您組織的 OrderSystem 合作對象。 這個傳送埠會套用**Inbound4010850_to_OrderFile**對應，對應中指定的格式輸出訊息從輸入訊息的格式轉換成。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-configure-a-send-port-for-the-850-message"></a>若要指定 850 訊息的傳送埠  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**管線**，然後按一下 **重新整理**。  
  
    > [!NOTE]
    >  您可能必須先重新整理管線，才可以為您將要建立的傳送埠選取 SendOrderFilePipeline。  
  
2.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。  
  
3.  在**傳送埠屬性**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|輸入`toOrderSystem`。|  
    |**型別**|選取**檔案**。|  
    |**設定**|按一下**設定**。|  
  
    > [!NOTE]
    >  傳送埠的傳輸類型是 FILE，因為測試訊息是將傳送到資料夾的一般檔案。  
  
4.  在**FILE 傳輸屬性**對話方塊方塊中，執行下列動作，然後按一下**確定**:  
  
    |使用|動作|  
    |--------------|----------------|  
    |**目的地資料夾**|按一下**瀏覽**，然後在**瀏覽資料夾**對話方塊中，移至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\ 案例 A\toOrderSystem|  
    |**檔案名稱**|輸入`%MessageID%.txt`，然後按一下 **確定**。|  
  
    > [!NOTE]
    >  值設定為**檔案名稱**屬性可確保，輸出檔會使用副檔名.txt。  
  
5.  在**傳送埠屬性**對話方塊中，針對**傳送管線**，選取**SendOrderFilePipeline**。  
  
    > [!NOTE]
    >  **SendOrderFilePipeline**傳送管線包括的一般檔案組合器來組合.txt 輸出檔案中，使用對應來源為輸入 850 訊息資料。 因為輸出檔案是 .txt 檔案，所以它不會出現在「交換/通知」狀態報告中。  
  
6.  在主控台樹狀目錄中，按一下**篩選**，然後執行下列步驟：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性**|選取**BTS。ReceivePortName**。|  
    |**運算子**|選取 **==** 。|  
    |**值**|輸入`ReceiveEDI_fromTHEM_A`。|  
    |**群組依據**|選取**和**。|  
    |**屬性**|在下一行中，選取**BTS。MessageType**。|  
    |**運算子**|選取 **！ =**。|  
    |**值**|輸入`http://schemas.microsoft.com/Edi/X12#X12_997_Root`。|  
  
    > [!NOTE]
    >  篩選器將確保此傳送埠將收取由 Receive_EDI_fromTHEM_A 接收位置所收到的訊息，而該傳送埠將不會收取 997 通知，而只收取 850 訊息。  
  
7.  在主控台樹狀目錄中，按一下 **[輸出對應]**。 在**輸出對應**窗格，請在**對應**資料行，第一個資料列上，選取**Inbound4010850_to_OrderFile**。 (中的項目**來源文件**資料行都將是 X12_00401_850。)  
  
    > [!NOTE]
    >  這個步驟可確保輸出訊息將會包含只對應來源為根據的輸入訊息資料的**Inbound4010850_to_OrderFile**對應。  
  
8.  按一下 **[確定]**。  
  
9. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 **傳送埠**。 以滑鼠右鍵按一下**toOrderSystem**，然後按一下 **啟動**登錄並啟動 連接埠。  
  
## <a name="next-steps"></a>後續步驟  
 設定傳送埠 (**toTHEM_997**) 將 997 通知送回給 Fabrikam，如中所述[步驟 7： 設定傳送埠以傳送通知給您的交易夥伴](../core/step-7-configure-a-send-port-to-send-the-acknowledgment-to-trading-partner.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設定靜態傳送埠以傳送 EDI 交換和通知](../core/configuring-a-static-send-port-to-send-edi-interchanges-and-acknowledgments.md)