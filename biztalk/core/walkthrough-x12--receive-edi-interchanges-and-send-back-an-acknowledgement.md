---
title: 逐步解說 (X12)： 接收 EDI 交換並傳回通知 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 25d2b5f3-6bd1-413c-aace-e4dd71f80403
caps.latest.revision: 45
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2951f0aa07875adcbdd7d4effbf1c4663435dc6a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003071"
---
# <a name="walkthrough-x12-receiving-edi-interchanges-and-sending-back-an-acknowledgement"></a>逐步解說 (X12)：接收 EDI 交換並傳回通知
本逐步解說提供一組逐步執行的程序，來使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 建立可接收 EDI 交換的解決方案。 在此解決方案中，EDI 交換是從交易夥伴 Fabrikam 傳送給另一個交易夥伴 Contoso。  

## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  

## <a name="how-the-solution-receives-edi-interchanges"></a>解決方案如何接收 EDI 交換  
 解決方案會執行下列作業：  

> [!NOTE]
>  這份清單中的事件可能不會按照所示的順序發生。  

1.  從交易夥伴 Fabrikam 接收一般檔案的 EDI 交換。  

2.  驗證 EDI 交換 (根據其結構描述)、將訊息解譯成 XML，並將訊息 XML 放置在 MessageBox 中。  

3.  產生 997 通知給接收的 EDI 交換，並將其放置在 MessageBox 中。  

4.  產生 TA1 通知給接收 EDI 交換，並將其放置在 MessageBox 中。  

5.  透過單向傳送埠拾取訊息 XML，並組合訊息 EDI 交換。  

6.  傳送 EDI 交換給 Contoso。  

7.  透過單向傳送埠收取 997 XML，並組合 997 EDI 交換。  

8.  傳送 997 交換給 Fabrikam。  

9. 透過單向傳送埠拾取 TA1 XML，並組合 TA1 EDI 交換。  

10. 傳送 TA1 交換給 Fabrikam。  

## <a name="the-functionality-in-this-solution"></a>此解決方案中的功能  
 為了完成這個逐步解說，將會啟用下列功能：  

- 這個解決方案是專為使用 X12 編碼 (而非 EDIFACT 編碼) 的交換所設計。  

  > [!NOTE]
  >  針對 HIPAA 使用的組態與針對 X12 編碼使用的組態近乎相同。 如需有關如何針對 EDIFACT 建立相似之解決方案的指示，請參閱 <<c0> [ 逐步解說 (EDIFACT): 接收 EDI 交換和傳送，將通知傳回](../core/walkthrough-edifact--receive-edi-interchanges-and-send-an-acknowledgement.md)。  

- 將針對內送交換執行 EDI 類型和擴充驗證。  

- 將會產生技術和功能通知，以傳回給交換傳送者。  

- 這個解決方案使用單向接收位置與 FILE 傳輸類型。  

  > [!NOTE]
  >  您可以使用雙向請求回應接收埠和位置來接收訊息，但是如果這樣做的話，就不能對接收位置使用 FILE 傳輸類型。 如需詳細資訊，請參閱 <<c0> [ 設定連接埠來接收 EDI 訊息和通知](../core/configuring-a-port-to-receive-edi-messages-and-acknowledgments.md)。  

- EDI 報告將會啟用，並會儲存交易集，以從交換狀態報告進行檢視。  

- 為了測試目的，解決方案會使用三個傳送埠，將 EDI 交換和建立的通知傳送至本機資料夾。  

  下圖顯示這個解決方案的架構：  

  ![接收 EDI 交換](../core/media/c54cca56-c658-4081-9e2f-bf28ba647cda.gif "c54cca56-c658-4081-9e2f-bf28ba647cda")  

## <a name="configuring-and-testing-the-walkthrough"></a>設定和測試逐步解說  
 這個解決方案所需的程序包含下列步驟：  

- 將必要的訊息結構描述加入 BizTalk 專案，然後建置並部署此專案，讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可以使用該結構描述來處理收到的交換。  

- 建立單向接收埠，以便讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 從交易夥伴接收 EDI 交換並產生通知。 此接收位置繫結至檔案資料夾，而 Fabrikam 會在此資料夾放置要傳送給 Contoso 的 EDI 交換。  

  > [!NOTE]
  >  您可以使用雙向請求回應接收埠和位置來接收訊息，但是如果這樣做的話，就不能對接收位置使用 FILE 傳輸類型。  

- 建立三個傳送埠，一個會將 EDI 交換傳送到 Contoso 本機資料夾、另一個會將 997 通知傳送到 Fabrikam 本機資料夾，而另一個則將 TA1 通知傳送到 Fabrikam 本機資料夾。  

- 為 Fabrikam 與 Contoso 建立合作對象 (交易夥伴)。  

- 分別為兩個交易夥伴建立商務設定檔。  

- 為要接收的訊息和要傳送的通知設定 EDI 屬性，來在兩個設定檔之間建立協議。  

- 使用測試 EDI 交換以測試逐步解說。  

  > [!NOTE]
  >  對於測試訊息，您可以使用 EDI 介面開發人員教學課程中所使用的 SamplePO.txt 檔案。 該檔案隨附於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ 資料夾中。 這是 X12 850 訊息。  

### <a name="configuring-the-walkthrough"></a>設定逐步解說  
 本節說明設定逐步解說的程序。  

##### <a name="to-deploy-the-message-schema"></a>若要部署訊息結構描述  

1. 在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，建立或開啟 BizTalk 專案。  

   > [!NOTE]
   >  本主題假設您已經在「BizTalk EDI 應用程式」中加入了自己應用程式的參考 (包含 EDI 結構描述、管線和協調流程)， 如果沒有，請參閱[如何將參考加入 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。  

2. 以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下**現有項目**。 移至結構描述所在的資料夾 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI，然後按兩下該結構描述。  

   > [!NOTE]
   >  如果 EDI 結構描述尚未解壓縮至 \XSD_Schema\EDI 資料夾，執行**MicrosoftEdiXSDTemplates.exe** \XSD_Schema\EDI 資料夾結構描述解壓縮至預設資料夾中的檔案。  
   > 
   > [!NOTE]
   >  如果您使用 EDI 介面開發人員教學課程中所用的 SamplePO.txt 檔案，則必須使用隨附於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI 資料夾中的 X12_00401_850.xsd 結構描述。 您不得使用 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema 資料夾中的 X12 850 結構描述。  

3. 將組件金鑰檔案加入專案，然後建置並部署組件。  

##### <a name="to-create-a-one-way-receive-port-for-fabrikam-to-receive-the-edi-interchange"></a>建立單向接收埠 (供 Fabrikam 使用) 以接收 EDI 交換  

1. 在 Windows 檔案總管中，建立本機資料夾，以接收交換。  

2. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**接收埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **單向接收埠**。  

3. 將接收連接埠，再按一下**接收位置**在主控台樹狀目錄中。  

4. 按一下 **[新增]**。  

5. 接收位置命名，選取**檔案**for**型別**，然後按一下**設定**。  

6. 瀏覽至資料夾**接收資料夾**文字方塊。 您已在此程序的步驟 1 中，建立此資料夾。 輸入檔案遮罩，例如 **\*.edi**或是 **\*.txt**。  

7. 按一下 [確定] 。  

8. 針對**接收管線**，選取**EdiReceive**。  

9. 按一下 [ **[確定]** 中**接收位置屬性**] 對話方塊。 按一下 [ **[確定]** 中再次**接收埠屬性**] 對話方塊。  

10. 在主控台樹狀目錄中，按一下**接收位置**。 在 **接收位置**窗格中，以滑鼠右鍵按一下您接收位置，然後按一下**啟用**。  

##### <a name="to-create-a-static-one-way-send-port-for-contoso-to-send-the-edi-interchange"></a>建立靜態單向傳送埠 (供 Contoso 使用) 以傳送 EDI 交換  

1. 在 Windows 檔案總管中，建立本機資料夾，以便將測試交換傳送至此本機資料夾。  

2. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **靜態單向傳送埠**。  

3. 在 [**傳送埠屬性**] 對話方塊中，傳送埠的名稱。  

4. 在 **傳輸**區段中，選取**檔案**的**型別**，然後按一下**設定**。  

5. 針對**目的地資料夾**，瀏覽至要接收交換的資料夾。 您已在此程序的步驟 1 中，建立此資料夾。 針對**檔案遮罩**，輸入交換格式，例如 **\*.edi**或是 **\*.xml**。  

6. 按一下 [確定] 。  

7. 在 **傳送管線**，選取**EdiSend**。  

8. 在主控台樹狀目錄中，選取**篩選器**。 輸入訂閱 EDI 交換的篩選條件。 例如，對於**屬性**，輸入**BTS。MessageType**; 對於**運算子**，輸入**==**; 以及**值**的交換中，輸入結構描述，例如http://schemas.microsoft.com/BizTalk/Edi/X12/2006#X12_00401_850.  

   > [!NOTE]
   >  上述篩選條件設定可以確保會將交換 (而非通知) 傳送到與此傳送埠相關的資料夾。  

9. 按一下 [確定] 。  

10. 在主控台樹狀目錄中，按一下**傳送埠**。 在 **傳送埠**窗格中，以滑鼠右鍵按一下您的傳送埠，然後**開始**。  

##### <a name="to-create-a-static-one-way-send-port-to-send-the-997n-acknowledgment"></a>若要建立靜態單向傳送埠以傳送 997n 通知  

1. 在 Windows 檔案總管中，建立本機資料夾，以便傳送 997 通知至此本機資料夾。  

2. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **靜態單向傳送埠**。  

3. 在 [**傳送埠屬性**] 對話方塊中，傳送埠的名稱。  

4. 在 **傳輸**區段中，選取**檔案**的**型別**，然後按一下**設定**。  

5. 針對**目的地資料夾**，瀏覽至要接收 997 通知的資料夾。 您已在此程序的步驟 1 中，建立此資料夾。 針對**檔案遮罩**，輸入交換格式，例如 **\*.edi**或是 **\*.txt**。  

6. 按一下 [確定] 。  

7. 在 **傳送管線**，選取**EdiSend**。  

8. 在主控台樹狀目錄中，選取**篩選器**。 輸入訂閱 997 通知的篩選條件。 例如，對於**屬性**，輸入**BTS。MessageType**; 對於**運算子**，輸入**==**; 及針對**值**比方說，在通知中，輸入的結構描述`http://schemas.microsoft.com/Edi/X12#X12_997_Root`.  

9. 按一下 [確定] 。  

10. 在主控台樹狀目錄中，按一下**傳送埠**。 在 **傳送埠**窗格中，以滑鼠右鍵按一下您的傳送埠，然後**開始**。  

##### <a name="to-create-a-static-one-way-send-port-to-send-the-ta1-acknowledgment"></a>若要建立靜態單向傳送埠以傳送 TA1 通知  

1. 在 Windows 檔案總管中，建立本機資料夾，以便傳送 TA1 通知至此本機資料夾。  

2. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **靜態單向傳送埠**。  

3. 在 [**傳送埠屬性**] 對話方塊中，傳送埠的名稱。  

4. 在 **傳輸**區段中，選取**檔案**的**型別**，然後按一下**設定**。  

5. 針對**目的地資料夾**，瀏覽至要接收 TA1 通知的資料夾。 您已在此程序的步驟 1 中，建立此資料夾。 針對**檔案遮罩**，輸入交換格式，例如 **\*.edi**或是 **\*.txt**。  

6. 按一下 [確定] 。  

7. 在 **傳送管線**，選取**EdiSend**。  

8. 在主控台樹狀目錄中，選取**篩選器**。 輸入訂閱 TA1 通知的篩選條件。 例如，對於**屬性**，輸入**BTS。MessageType**; 對於**運算子**，輸入**==**; 及針對**值**比方說，在通知中，輸入的結構描述http://schemas.microsoft.com/Edi/X12#X12_TA1_Root.  

9. 按一下 [確定] 。  

10. 在主控台樹狀目錄中，按一下**傳送埠**。 在 **傳送埠**窗格中，以滑鼠右鍵按一下您的傳送埠，然後**開始**。  

##### <a name="to-create-a-party-and-a-business-profile-for-fabrikam"></a>若要為 Fabrikam 建立合作對象與商務設定檔  

1. 以滑鼠右鍵按一下**合作對象**中的節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下**合作對象**。  

2. 輸入的名稱中的合作對象**名稱**文字方塊中，然後按一下**確定**。  

   > [!NOTE]
   >  藉由選取**本機 BizTalk 可處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定要建立的合作對象為相同的組織也裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. 據此，建立協議時將會啟用或停用某些屬性。 不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。  

3. 以滑鼠右鍵按一下合作對象名稱、 指向**的新**，然後按一下**商務設定檔**。  

4. 在 **設定檔屬性**對話方塊的 **一般**頁面上，輸入**fabrikam_profile**中**名稱**文字方塊。  

   > [!NOTE]
   >  當您建立合作對象時，會同時建立設定檔。 您可以重新命名再使用該設定檔，而不需建立新設定檔。 若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。 在 **一般**頁面上，指定設定檔的名稱。  

##### <a name="to-create-a-party-and-a-business-profile-for-contoso"></a>若要為 Contoso 建立合作對象與商務設定檔  

1. 以滑鼠右鍵按一下**合作對象**中的節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下**合作對象**。  

2. 輸入的名稱中的合作對象**名稱**文字方塊中，然後按一下**確定**。  

   > [!NOTE]
   >  藉由選取**本機 BizTalk 可處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定要建立的合作對象為相同的組織也裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. 據此，建立協議時將會啟用或停用某些屬性。 不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。  

3. 以滑鼠右鍵按一下合作對象名稱、 指向**的新**，然後按一下**商務設定檔**。  

4. 在 **設定檔屬性**對話方塊的 **一般**頁面上，輸入**contoso_profile**中**名稱**文字方塊。  

   > [!NOTE]
   >  當您建立合作對象時，會同時建立設定檔。 您可以重新命名再使用該設定檔，而不需建立新設定檔。 若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。 在 **一般**頁面上，指定設定檔的名稱。  

##### <a name="to-create-an-agreement-between-the-two-business-profiles"></a>在兩個商務設定檔之間建立協議  

1. 以滑鼠右鍵按一下 **[fabrikam_profile]**，指向**新增**，然後按一下**協議**。  

2. 在 [**一般屬性**] 頁面上，如**名稱**文字方塊中，輸入協議的名稱。  

3. 從**通訊協定**下拉式清單中，選取**X12**。  

4. 在 **第二個夥伴**區段中，從**名稱**下拉式清單中，選取**Contoso**。  

5. 在 **第二個夥伴**區段中，從**設定檔**下拉式清單中，選取**contoso_profile**。  

    您會發現兩個新的索引標籤取得新增旁**一般** 索引標籤。每個索引標籤各用於設定一個單向協議，而每個單向協議各代表一筆完整的訊息交易 (包含訊息傳輸與通知傳輸)。  

6. 在 **一般**索引標籤**一般屬性**頁面上，於**一般主控件設定**區段中，選取**開啟報告**，，然後選取 **儲存訊息內容 reporting**。  

7. 在上執行下列工作**Fabrikam-> Contoso**  索引標籤。  

   1. 上**識別碼**下方的頁面上**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，並**ISA8**) 對應到您的測試訊息中那些標頭欄位的值。  

      > [!NOTE]
      >  對於傳送者和接收者，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 需要辨識符號與識別碼欄位，才能執行協議解析。 它會比對的值**ISA5**， **ISA6**， **ISA7**，以及**ISA8**交換標頭與協議屬性中。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會比對傳送者辨識符號和識別項 （不需接收者辨識符號和識別項） 也解析協議。 若 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法解析協議，它將會使用後援協議屬性。  
      > 
      > [!NOTE]
      >  如果您使用 「 EDI 介面開發人員教學課程 」 中的 SamplePO.txt 檔案做為測試訊息，設定**ISA5**要**ZZ**， **ISA6**至**THEM**， **ISA7**要**ZZ**，和**ISA8**至**美國**。  

   2. 上**收條**頁面**交換設定** 區段中，核取**預期 TA1**並**預期 997**。  

   3. 上**驗證**下方的頁面上**交換設定**區段中，確定**檢查 ISA13 是否重複**選項未核取。  

      > [!NOTE]
      >  清除**檢查 ISA13 是否重複**屬性可讓您接收相同訊息的多個執行個體。  

   4. 在上**字元集和分隔符號**下方的頁面上**交換設定**區段中，選取**CR LF**選項。  

   5. 在上**本機主機設定**下方的頁面上**交換設定**區段中，清除**通知的路由設定為傳送管線在要求-回應接收埠**選項。  

      > [!NOTE]
      >  如果您使用雙向接收埠以接收交換並傳回通知，您會檢查**通知的路由設定為傳送管線在要求-回應接收埠**。  

   6. 上**傳送埠**下方的頁面上**交換設定**區段中，將會接收來自 Fabrikam 交換的傳送埠和接收的傳送埠建立關聯從 Contoso 的通知。 在 **傳送埠**格線下方**名稱** 欄中，按一下空白儲存格，並從下拉式清單中，選取 建立從 Fabrikam 接收 EDI 交換的傳送埠。 針對建立來接收 TA1 通知的傳送埠與建立來接收 997 通知的傳送埠，重複執行此步驟。  

   7. 上**驗證**下方的頁面上**交易集設定**區段中，保留**EDI 類型驗證**核取，並檢查**擴充驗證**.  

   8. 如果您使用其中一個隨附之標準結構描述[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請在**本機主機設定**頁面下**交易集設定**區段中，選取要用來將結構描述的命名空間處理內送交換。 如果使用自訂的結構描述，請輸入中的值**自訂目標命名空間**方格中，以便[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以判斷命名空間使用群組和交易集標頭值。  

   9. 在上**信封**下方的頁面上**交易集設定**區段中，輸入在格線的第一行中的所有資料行的值。  


      |       使用       |                                                                                                                                    以進行此動作                                                                                                                                    |
      |----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |     **預設值**      |   選取 **預設**。 **注意：** 當您選取這個資料列的預設值為**GS1**， **GS2**， **GS3**， **[gs7]**，以及**GS8**習慣即使的值**交易型別**，**版本/版次**，和**目標命名空間**不相符的訊息。   |
      | **交易類型** |                                                                                                     選取測試訊息，訊息類型**850-Purchase Order**。                                                                                                      |
      | **版本/版次**  |                                                                                                                        輸入 EDI 版本， **00401**。                                                                                                                         |
      | **目標命名空間** |                                                                                                                選取  **<http://schemas.microsoft.com/Edi/X12>**。                                                                                                                |
      |       **GS1**        |                                                                                           確認已選取測試訊息的訊息類型， **PO-Purchase Order (850)**。                                                                                           |
      |       **GS2**        |                                                                                                                    輸入應用程式傳送者的值。                                                                                                                     |
      |       **GS3**        |                                                                                                                   輸入應用程式接收者的值。                                                                                                                    |
      |       **GS4**        | 選取您想要的日期格式。 **注意：** 您必須在下拉式清單中選取值，不只是按一下要顯示預設值的欄位。 如果您按一下欄位而未從下拉式清單中選取值，實際上不會選取值。 |
      |       **GS5**        |                                                                                                                      選擇您要的時間格式。                                                                                                                       |
      |       **[GS7]**        |                                                                                                                選取  **X-Accredited 的 Standards Committee X12**。                                                                                                                |
      |       **GS8**        |                                                                                                             確認已輸入 EDI 版本， **00401**。                                                                                                             |

      > [!NOTE]
      >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將設定值，如 GS01，GS02，GS03、 GS04、 GS05、 GS07 和輸出的輸入值為基礎的通知的 GS08**交易類型**，**版本/版次**，和**目標命名空間**。 傳送管線會嘗試將交易集類型、X12 版本和目標命名空間，與訊息標頭中的對應值進行比對。 如果成功，則會使用相關聯的 GS 值**交易類型**，**版本/版次**，並**目標命名空間**值。  

8. 在上執行下列工作**Contoso-> Fabrikam**  索引標籤。  

   > [!NOTE]
   >  在此逐步解說中，我們在索引標籤中指定必要值，以便可以順利地建立協議。 若要成功建立協議，兩個單向協議索引標籤必須已定義的值**ISA5**， **ISA6**， **ISA7**，以及**ISA8**。  

   > [!NOTE]
   >  雖然通知屬於同一個訊息交易的一部分，在中設定通知的產生方式的相關的屬性**Contoso-> Fabrikam**  索引標籤。這是必要的因為通知內容屬性傳送者和接收者限定詞設定為您在指定的值相反**Contoso-> Fabrikam**  索引標籤。例如，如果傳送者和接收者識別碼設為 THEM 與 US 中的**Fabrikam-> Contoso**  索引標籤、 寄件者與接收者內容屬性會設定為 US 與在通知中。 一般而言，其他單向協議索引標籤也會分別將傳送者與接收者識別項設定為 US 與 THEM。 因此，通知訊息會解析成該協議，並將挑選屬性設定。 因此，如果您想要讓通知使用不同的項目分隔符號，或如果您想要讓通知使用 CR LF，指定中的屬性**Contoso-> Fabrikam**  索引標籤。  
   >   
   >  在概念上，將會從傳送者與接收者辨識符號與在通知的內容屬性中所設定值相同的任一個單向協議索引標籤中挑選通知的屬性。 但為便於實際應用，通常會在您所建立由交換解析而成之協議的其他單向協議索引標籤中設定此屬性。  

   1.  上**識別碼**下方的頁面上**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，並**ISA8**) 對應到您的測試訊息中那些標頭欄位的值。  

       > [!NOTE]
       >  如果您使用 「 EDI 介面開發人員教學課程 」 中的 SamplePO.txt 檔案做為測試訊息，設定**ISA5**要**ZZ**， **ISA6**至**美國**， **ISA7**要**ZZ**，和**ISA8**至**THEM**。  

9. 按一下 **[套用]**。  

10. 按一下 [確定] 。 中新增的協議會列為**協議**一節**合作對象與商務設定檔**窗格。 預設會啟用新增的協議。  

### <a name="testing-the-walkthrough"></a>測試逐步解說  
 本節提供關於如何測試逐步解說的資訊。  

##### <a name="to-test-the-walkthrough"></a>若要測試逐步解說  

1. 在 Windows 檔案總管中，將測試 EDI 交換置放到本機接收資料夾中。  

   > [!NOTE]
   >  對於測試訊息，您可以使用 EDI 介面開發人員教學課程中所使用的 SamplePO.txt 檔案。 該檔案隨附於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial 資料夾中。 這是 X12 850 訊息。 如果您使用這個訊息，則必須完成 X12_00401_850.xsd 結構描述的部署 (該結構描述隨附於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI 資料夾)。 您不得使用 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema 資料夾中的 X12 850 結構描述。  

2. 開啟與交換傳送埠相關聯的資料夾，並確認其中有包含 EDI 交換。  

3. 開啟與 997 通知傳送埠相關聯的資料夾，並確認其中有包含 997 通知。  

4. 開啟與 TA1 通知傳送埠相關聯的資料夾，並確認其中有包含 TA1 通知。  

## <a name="see-also"></a>另請參閱  
 [開發和設定 BizTalk Server EDI 解決方案](../core/developing-and-configuring-biztalk-server-edi-solutions.md)