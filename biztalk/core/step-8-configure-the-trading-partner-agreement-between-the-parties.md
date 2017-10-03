---
title: "步驟 8： 設定合作對象之間交易夥伴協議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f532f85-3f09-4b60-b7bb-817ee3c79899
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25e49bf5dcae7324fa3b68fe5080d094b4a2f603
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-8-configure-the-trading-partner-agreement-between-the-parties"></a>步驟 8： 設定合作對象之間交易夥伴協議
![步驟 8 的 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-8of9.gif "Step_8of9")  
  
 在此步驟中，您要設定 X12 交易夥伴協議定義交換 X12 參數兩個交易夥伴，OrderSystem 與 Fabrikam 之間的訊息。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-configure-an-agreement"></a>若要設定協議  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft BizTalk Server**，然後按一下  **BizTalk Server 管理**。  
  
2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 **合作對象**的主控台樹狀目錄中，然後在**合作對象與商務設定檔**頁面上，以滑鼠右鍵按一下**[fabrikam_profile]**，指向 **新增**，然後按一下 **協議**。  
  
3.  在**一般屬性** 頁面上，針對**名稱**文字方塊中，輸入協議的名稱。  
  
4.  從**通訊協定**下拉式清單中，選取**X12**。  
  
5.  在**第二個合作對象** 區段中，從**合作對象**下拉式清單中，選取**OrderSystem**。  
  
6.  在**第二個合作對象** 區段中，從**商務**下拉式清單中，選取**ordersystem_profile**。  
  
     您會發現兩個新的索引標籤取得旁新增**一般** 索引標籤。每個索引標籤各用於設定一個單向協議，而每個單向協議各代表一筆完整的訊息交易 (包含訊息傳輸與通知傳輸)。  
  
7.  在**一般**索引標籤**一般屬性**頁面上，於**一般主控件設定**區段中，選取**開啟報告**，然後選取**儲存報告的訊息內容**。  
  
8.  在上執行下列工作**Fabrikam-> OrderSystem**  索引標籤。  
  
    1.  在**識別碼**頁面**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，和**ISA8**) 對應到您的測試訊息中標頭欄位的值。  
  
        |使用|動作|  
        |--------------|----------------|  
        |**傳送者辨識符號 (ISA5)**|選取**ZZ-使用者相互定義**。|  
        |**寄件者識別項 (ISA6)**|輸入**THEM**。|  
        |**接收者辨識符號 (ISA7)**|選取**ZZ-使用者相互定義**。|  
        |**接收者識別項 (ISA8)**|輸入**美國**。|  
  
        > [!NOTE]
        >  對於傳送者和接收者，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 需要辨識符號與識別碼欄位，才能執行協議解析。 它會比對的值**ISA5**， **ISA6**， **ISA7**，和**ISA8**交換標頭與協議屬性中。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]也比對傳送者辨識符號和識別項 （不需接收者辨識符號和識別項） 來解析協議。 若 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法解析協議，它將會使用後援協議屬性。  
  
    2.  在**通知**頁面的 **交換設定**區段中，按一下**預期 997**。 若是選取這個核取方塊，則會提示接收管線在收到 850 交換時產生 997 通知。  
  
    3.  在**驗證**頁面**交換設定**區段中，請確定**交換控制編號 （檢查重複的 isa13）**未選項。  
  
        > [!NOTE]
        >  清除**檢查重複的 ISA13**屬性可讓您接收相同訊息的多個執行個體。  
  
    4.  在**本機主機設定**頁面的 **交換設定**區段中，清除**通知的路由設定為傳送管線在要求-回應接收埠**。  
  
        > [!NOTE]
        >  清除**通知的路由設定**屬性是必要的因為這個解決方案會傳回非同步通知透過個別傳送埠，而不是透過與雙向關聯的傳送埠將同步通知接收埠。  
  
    5.  在**本機主機設定**頁面**交易集設定**區段中，選取要用來處理內送交換的結構描述的命名空間。  
  
        |使用|動作|  
        |--------------|----------------|  
        |**預設值**|選取欄中的核取方塊|  
        |**如 ST1**|選取**850-Purchase Order**。|  
        |**GS2**|輸入**THEM**。|  
        |**目標命名空間**|選取**http://schemas.microsoft.com/BizTalk/EDI/X12/2006**。|  
  
        > [!NOTE]
        >  設定屬性可以讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 判斷要用於處理內送 850 交換的結構描述。 如果交換的 GS02 和 ST01 值是輸入在格線行中，則將會使用同一行的目標命名空間來判斷要使用的結構描述。  
  
9. 在上執行下列工作**OrderSystem-> Fabrikam**  索引標籤。  
  
    1.  在**識別碼**頁面**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，和**ISA8**) 對應到您的測試訊息中標頭欄位的值。  
  
        |使用|動作|  
        |--------------|----------------|  
        |**傳送者辨識符號 (ISA5)**|選取**ZZ-使用者相互定義**。|  
        |**寄件者識別項 (ISA6)**|輸入**美國**。|  
        |**接收者辨識符號 (ISA7)**|選取**ZZ-使用者相互定義**。|  
        |**接收者識別項 (ISA8)**|輸入**THEM**。|  
  
    2.  在**字元集和分隔符號**頁面的 **交換設定**區段中，選取**CR LF**如**尾碼**屬性。  
  
    3.  在**傳送埠**頁面**交換設定**區段中，fabrikam 會傳送通知的傳送埠產生關聯。 在**傳送埠**方格下方**名稱**資料行，按一下空白儲存格，然後從下拉式清單中，選取 傳送埠 (**toTHEM_997**) 建立，以便傳送 997通知給 Fabrikam。  
  
    4.  在**信封**頁面**交易集設定**區段中，輸入在格線的第一行中的所有資料行的值。  
  
        |使用|動作|  
        |--------------|----------------|  
        |**預設值**|選取核取方塊**預設**資料行。 **注意：**當您選取這個資料列的預設值為**GS1**， **GS2**， **GS3**， **GS7**，和**GS8**可用即使值**交易類型**，**版本/版次**，和**目標命名空間**都不符合訊息。|  
        |**交易類型**|選取的測試訊息，訊息類型**850-Purchase Order**。|  
        |**版本/版次**|輸入 EDI 版本， **00401**。|  
        |**目標命名空間**|選取**http://schemas.microsoft.com/Edi/X12**。|  
        |**GS1**|確認**PO-Purchase Order (850)**已選取。|  
        |**GS2**|輸入**1234567**。<br /><br /> **寄件者應用程式識別碼。**|  
        |**GS3**|輸入**0000000**。<br /><br /> **接收者應用程式識別碼。**|  
        |**GS4**|選取**CCYYMMDD**。 **注意：**您必須在下拉式清單中選取值，不只是按一下欄位以顯示預設值。 如果您按一下欄位而未從下拉式清單中選取值，實際上不會選取值。|  
        |**GS5**|選取**HHMM**。|  
        |**GS7**|選取**X-Accredited 的 Standards Committee X12**。|  
        |**GS8**|確認**00401**已輸入。|  
  
        > [!NOTE]
        >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]將值，來設定 GS01、 GS02、 GS03、 GS04、 GS05、 GS07 和 GS08 輸出的輸入值為基礎的通知**交易類型**，**版本/版次**，和**目標命名空間**。 傳送管線會嘗試將交易集類型、X12 版本和目標命名空間，與訊息標頭中的對應值進行比對。 如果成功，它會使用相關聯的 GS 值**交易類型**，**版本/版次**，和**目標命名空間**值。  
  
10. 按一下 **[套用]**。  
  
11. 按一下 **[確定]**。 新增的協議會列在**協議**區段**合作對象與商務設定檔**窗格。 預設會啟用新增的協議。  
  
12. 重新啟動 BizTalk 服務。 在 BizTalk Server 管理主控台中，在**平台設定**，按一下**主控件執行個體**，以滑鼠右鍵按一下**BizTalkServerApplication**，然後按一下  **重新啟動**。  
  
    > [!NOTE]
    >  BizTalk 服務在 EDI 狀態報告啟動或停用之後必須重新啟動，讓變更生效。  
  
## <a name="next-steps"></a>後續步驟  
 測試 EDI 解決方案中所述[步驟 9： 測試 EDI 解決方案](../core/step-9-test-the-edi-solution.md)  
  
## <a name="see-also"></a>另請參閱  
 [設定編碼協議屬性](../core/configuring-encoding-agreement-properties.md)