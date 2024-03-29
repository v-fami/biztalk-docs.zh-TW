---
title: 步驟 10： 設定 X12 和 AS2 交易夥伴協議 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8fcdb3af-727a-4d20-9dcf-cf162e7d3398
caps.latest.revision: 46
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: beae325fa0a0cfcc2c4a63f3134ccb39e5e243d8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996039"
---
# <a name="step-10-configure-the-x12-and-as2-trading-partner-agreement"></a>步驟 10： 設定 X12 和 AS2 交易夥伴協議
![步驟 11-10](../core/media/tut-step10-of-11.gif "Tut_Step10_of_11")  

 在本步驟中，您將設定要透過 HTTP 傳輸 EDIINT/AS2 編碼訊息的 X12 和 AS2 交易夥伴協議。 此 Fabrikam 合作對象會傳送 EDI 交換至 Contoso，再由 Contoso 將 997 通知和非同步 MDN 傳回 Fabrikam。  

## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  

### <a name="to-create-an-as2-agreement"></a>若要建立 AS2 協議  

1. 按一下 **開始**，按一下**所有程式**，按一下  **Microsoft BizTalk Server**，然後按一下**BizTalk Server 管理**。  

2. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下**合作對象**在主控台樹狀目錄中，然後在**合作對象與商務設定檔**頁面上，以滑鼠右鍵按一下 **[fabrikam_profile]**，指向**新增**，然後按一下**協議**。  

3. 在 [**一般屬性**] 頁面上，如**名稱**文字方塊中，輸入協議的名稱。  

4. 從**通訊協定**下拉式清單中，選取**AS2**。  

5. 在 **第二個夥伴**區段中，從**名稱**下拉式清單中，選取**Contoso**。  

6. 在 **第二個夥伴**區段中，從**設定檔**下拉式清單中，選取**contoso_profile**。  

    您會發現兩個新的索引標籤取得新增旁**一般** 索引標籤。每個索引標籤各用於設定一個單向 AS2 協議。  

7. 在 **一般**索引標籤**一般屬性**頁面上，於**一般主控件設定**區段中，選取**開啟報告**。  

8. 在上執行下列工作**Fabrikam-> Contoso**  索引標籤。  

   1.  上**識別碼**頁面上，輸入值**AS2-從**並**AS2-以**。 針對**AS2-從**，輸入`Fabrikam`。 針對**AS2-To**，輸入`Contoso`。  

   2.  在 **驗證**頁面上，選取**使用協議設定進行驗證與 MDN 取代訊息標頭**核取方塊  

       > [!NOTE]
       >  設定此屬性可確保產生 MDN 時使用的是合作對象屬性，而不是使用已接收之 AS2 訊息的 AS2 標頭。  

   3.  在 **通知 (Mdn)** 頁面上，執行下列動作：  

       1.  選取 **的 要求 MDN**核取方塊。  

       2.  請確定**要求簽署的 MDN**核取方塊。  

       3.  選取 **要求非同步 MDN**核取方塊。  

       4.  在 **回條傳遞選項 (URL)** 文字方塊中，輸入`http://localhost/Fabrikam/Default.aspx?Destination=_MDNToFabrikam`。  

9. 在上執行下列工作**Contoso-> Fabrikam**  索引標籤。  

   1. 上**識別碼**頁面上，輸入值**AS2-從**並**AS2-以**。 針對**AS2-從**，輸入`Contoso`。 針對**AS2-To**，輸入`Fabrikam`。  

   2. 上**傳送埠**頁面**交換設定**區段的**傳送埠**清單中，如**名稱**選取**Send_Async_997**。  

      > [!NOTE]
      >  Send_Async_997 傳送埠需要進入**傳送埠**清單，讓[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以解析外寄 997 訊息的合作對象。 傳送管線會將傳送埠的名稱與合作對象屬性中的傳送埠進行比對。 必須這麼做的原因是，這樣一來 [AS2-To] 屬性不會在訊息的內容中升級，而該屬性是傳送管線試圖解析合作對象時會最先比對的項目。 如需詳細資訊，請參閱 <<c0> [ 外寄 AS2 訊息的協議解析](../core/agreement-resolution-for-outgoing-as2-messages.md)。  

10. 按一下 **[套用]**。  

11. 按一下 [確定] 。 中新增的協議會列為**協議**一節**合作對象與商務設定檔**窗格。 預設會啟用新增的協議。  

### <a name="to-create-an-x12-agreement"></a>若要建立 X12 協議  

1. 以滑鼠右鍵按一下 **[fabrikam_profile]**，指向**新增**，然後按一下**協議**。  

2. 在 [**一般屬性**] 頁面上，如**名稱**文字方塊中，輸入協議的名稱。  

3. 從**通訊協定**下拉式清單中，選取**X12**。  

4. 在 **第二個夥伴**區段中，從**名稱**下拉式清單中，選取**Contoso**。  

5. 在 **第二個夥伴**區段中，從**設定檔**下拉式清單中，選取**contoso_profile**。  

    您會發現兩個新的索引標籤取得新增旁**一般** 索引標籤。每個索引標籤各用於設定一個單向 X12 協議。  

6. 在 **一般**索引標籤**一般屬性**頁面上，於**一般主控件設定**區段中，選取**開啟報告**，，然後選取 **儲存訊息內容 reporting**。  

7. 在上執行下列工作**Fabrikam-> Contoso**  索引標籤。  

   1. 上**識別碼**下方的頁面上**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，並**ISA8**) 對應到您的測試訊息中那些標頭欄位的值。 本教學課程中，將**ISA5**要**ZZ**， **ISA6**至**7654321**， **ISA7**至**ZZ**，並**ISA8**要**1234567**。  

      > [!NOTE]
      >  對於傳送者和接收者，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 需要辨識符號與識別碼欄位，才能執行協議解析。 它會比對的值**ISA5**， **ISA6**， **ISA7**，以及**ISA8**交換標頭與協議屬性中。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會比對傳送者辨識符號和識別項 （不需接收者辨識符號和識別項） 也解析協議。 若 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法解析協議，它將會使用後援協議屬性。  

   2. 上**通知**下方的頁面上**交換設定**區段中，選取**預期 997**核取方塊。  

   3. 上**驗證**下方的頁面上**交換設定**區段中，確定**檢查 ISA13 是否重複**選項未核取。  

      > [!NOTE]
      >  清除**檢查 ISA13 是否重複**屬性可讓您接收相同訊息的多個執行個體。  

   4. 在上**本機主機設定**頁面**交換設定**區段底下**接收者的設定**，清除**通知的路由設定為上的傳送管線要求-回應接收埠**。  

      > [!NOTE]
      >  清除此屬性，讓您可透過個別傳送埠傳送 997 通知，而不是透過與雙向接收埠關聯的傳送埠傳送。  

8. 在上執行下列工作**Contoso-> Fabrikam**  索引標籤。  

   1. 上**識別碼**下方的頁面上**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，並**ISA8**) 對應到您的測試訊息中那些標頭欄位的值。  針對此逐步解說中，設定**ISA5**要**ZZ**， **ISA6**至**1234567**， **ISA7**到**ZZ**，並**ISA8**要**7654321**。  

   2. 在上**字元集和分隔符號**頁面**交換設定** 區段中，如**後置詞**，選取**CR LF**。  

   3. 上**信封**下方的頁面上**交易集設定**區段中，執行下列動作：  


      |       使用       |                                                                                                                                              以進行此動作                                                                                                                                               |
      |----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |     **預設值**      |              選取 **預設**。 **注意：** 當您選取這個資料列的預設值為**GS1**， **GS2**， **GS3**， **[gs7]**，以及**GS8**習慣即使的值**交易型別**，**版本/版次**，和**目標命名空間**不相符的訊息。              |
      | **交易類型** |                                                                                                          例如，選取您的測試訊息的訊息類型**864-簡訊**。                                                                                                           |
      | **版本/版次**  |                                                                                                                                           請輸入**00401**。                                                                                                                                            |
      | **目標命名空間** |                                                                                                                    選取  **<http://schemas.microsoft.com/BizTalk/EDI/X12/2006>**。                                                                                                                    |
      |       **GS1**        |                                                                                                確認已選取測試訊息的訊息類型，例如**TX-簡訊 (864)**。                                                                                                |
      |       **GS2**        |                                                                                                                                             請輸入**01**。                                                                                                                                             |
      |       **GS3**        |                                                                                                                                          請輸入**7654321**。                                                                                                                                           |
      |       **GS4**        | 選取您想要的日期格式。 選取  **CCYYMMDD**。 **注意：** 您必須在下拉式清單中選取值，不只是按一下要顯示預設值的欄位。 如果您按一下欄位而未從下拉式清單中選取值，實際上不會選取值。 |
      |       **GS5**        |                                                                                                                      選擇您要的時間格式。 選取  **HHMMSSdd**。                                                                                                                       |
      |       **[GS7]**        |                                                                                                                   選取  **T-Transportation Data Coordinating Committee (TDCC)**。                                                                                                                   |
      |       **GS8**        |                                                                                                                      確認已輸入 EDI 版本做**00401**。                                                                                                                       |


9. 按一下 **[套用]**。  

10. 按一下 [確定] 。 中新增的協議會列為**協議**一節**合作對象與商務設定檔**窗格。 預設會啟用新增的協議。  

11. 重新啟動 BizTalk 服務。 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，在**平台設定**，按一下**主控件執行個體**，以滑鼠右鍵按一下**BizTalkServerApplication**，然後按一下  **重新啟動**。  

## <a name="next-steps"></a>後續步驟  
 您會測試 AS2 方案，如中所述[步驟 11： 測試 AS2 方案](../core/step-11-test-the-as2-solution.md)。  

## <a name="see-also"></a>另請參閱  
 [設定 AS2 屬性](../core/configuring-as2-properties.md)   
 [設定 EDI 屬性](../core/configuring-edi-properties.md)