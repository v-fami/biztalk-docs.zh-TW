---
title: 步驟 7： 設定傳送埠來傳送通知給交易夥伴 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a082870-894c-4f64-a575-3681d8a5c4ea
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 59d36aaaf33673095c664363da5b3417bbd1cde4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279062"
---
# <a name="step-7-configure-a-send-port-to-send-the-acknowledgment-to-your-trading-partner"></a>步驟 7： 設定要傳送給交易夥伴的通知的傳送埠
![步驟 7 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-7of9.gif "Step_7of9")  
  
 您可以在此步驟中設定要傳送由所產生的 997 通知訊息的傳送埠[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]至 Fabrikam **toTHEM_997**資料夾。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-configure-a-send-port-that-subscribes-to-the-997-acknowledgment"></a>設定訂閱 997 通知的傳送埠  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。  
  
2.  在**傳送埠屬性**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|輸入`toTHEM_997`。|  
    |**型別**|選取**檔案**。|  
    |**設定**|按一下**設定**。|  
  
    > [!NOTE]
    >  傳送埠的傳輸類型是 FILE，因為 997 是將傳送到資料夾的一般檔案。  
  
3.  在**FILE 傳輸屬性**對話方塊方塊中，執行下列動作，然後按一下**確定**:  
  
    |使用|動作|  
    |--------------|----------------|  
    |**目的地資料夾**|按一下**瀏覽**，然後在**瀏覽資料夾**對話方塊中，移至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI 介面 Developer Tutorial\ProcessEDI_TestLocations\ Scenario a\tothem_997。|  
    |**檔案名稱**|輸入`%MessageID%.txt`，然後按一下 **確定**。|  
  
    > [!NOTE]
    >  值設定為**檔案名稱**屬性可確保，輸出檔會使用副檔名.txt。  
  
4.  在**傳送埠屬性**對話方塊中，針對**傳送管線**，選取**EdiSend**。  
  
    > [!NOTE]
    >  用來傳送 EDI 交換 (除了透過 AS2 傳輸所傳送的交換之外) 的傳送管線是 EdiSend 管線 (透過 AS2 傳輸所傳送的 EDI 交換則使用 AS2EdiSend 傳送管線傳送)。  
  
5.  在主控台樹狀目錄中，按一下**篩選**，然後執行下列步驟：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性**|選取**BTS。MessageType**。|  
    |**運算子**|選取 **==** 。|  
    |**值**|輸入**http://schemas.microsoft.com/Edi/X12#X12_997_Root**。|  
  
    > [!NOTE]
    >  篩選條件可確保傳送埠將挑選 997 訊息類型的訊息。  
  
6.  按一下 **[確定]**。  
  
7.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 **傳送埠**。 以滑鼠右鍵按一下**toTHEM_997**，然後按一下 **啟動**登錄並啟動 連接埠。  
  
8.  在 BizTalk Server 管理主控台的主控台樹狀目錄中，按一下 **平台設定**，然後按一下 **主控件執行個體**。 在 主控件執行個體 窗格中，按一下**BizTalkServerApplication**，然後按一下 **重新啟動**。  
  
## <a name="next-steps"></a>後續步驟  
 中所述，建立兩個交易夥伴之間的協議[步驟 8： 設定合作對象之間交易夥伴協議](../core/step-8-configure-the-trading-partner-agreement-between-the-parties.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設定靜態傳送埠以傳送 EDI 交換和通知](../core/configuring-a-static-send-port-to-send-edi-interchanges-and-acknowledgments.md)