---
title: '逐步解說 (EDIFACT): 接收 EDI 交換並傳回通知 |Microsoft Docs'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 02751f0c-8e7e-4879-93e4-8bc475640756
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b221d47a64f603db697b99c7e5a60b1cb1a67bd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018888"
---
# <a name="walkthrough-edifact-receiving-edi-interchanges-and-sending-back-an-acknowledgement"></a>逐步解說 (EDIFACT)：接收 EDI 交換並傳回通知
本逐步解說提供一組逐步執行的程序，來使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 建立可接收 EDIFACT 交換的解決方案。 在這個解決方案中，EDIFACT 交換會從一個交易夥伴 (Fabrikam) 傳送至另一個交易夥伴 (Contoso)。  

## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  

## <a name="how-the-solution-receives-edifact-interchanges"></a>解決方案如何接收 EDIFACT 交換  
 解決方案會執行下列作業：  

> [!NOTE]
>  這份清單中的事件可能不會按照所示的順序發生。  

1.  從交易夥伴 Fabrikam 接收一般檔案 EDIFACT 交換。  

2.  將 EDIFACT 交換比對其結構描述來進行驗證、將訊息解譯到 XML 中，並將訊息 XML 放置在 MessageBox 中。  

3.  產生表示已收到 EDI 交換的技術通知 (訊息回條)，並將其放置在 MessageBox 中。  

4.  產生表示接受或拒絕接收 EDI 交換的功能通知，並將其放置在 MessageBox 中。  

5.  透過單向 FILE 傳送埠拾取訊息 XML，並組合訊息 EDI 交換。  

6.  傳送 EDI 交換至 Contoso 本機資料夾。  

7.  透過單向 FILE 傳送埠拾取技術通知，並組合交換。  

8.  傳送技術通知至 Fabrikam 本機資料夾。  

9. 透過單向 FILE 傳送埠拾取功能通知，並組合交換。  

10. 傳送功能通知至 Fabrikam。  

## <a name="the-functionality-in-this-solution"></a>此解決方案中的功能  
 為了完成這個逐步解說，將會啟用下列功能：  

- 這個解決方案是專為使用 EDIFACT 編碼的交換而設計。  

  > [!NOTE]
  >  如需有關如何建立類似的解決方案，為 X12 交換的指示，請參閱[逐步解說 (X12)： 接收 EDI 交換和傳送，將通知傳回](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md)。  

- 將針對內送交換執行 EDI 類型和擴充驗證。  

- 將會產生技術和功能通知，以傳回給交換傳送者。  

- 這個解決方案使用單向接收位置與 FILE 傳輸類型。  

  > [!NOTE]
  >  您可以使用雙向請求回應接收埠和位置來接收訊息，但是如果這樣做的話，就不能對接收位置使用 FILE 傳輸類型。 如需詳細資訊，請參閱 <<c0> [ 設定連接埠來接收 EDI 訊息和通知](../core/configuring-a-port-to-receive-edi-messages-and-acknowledgments.md)。  

- EDI 報告將會啟用，並會儲存交易集，以從交換狀態報告進行檢視。  

- 為了測試目的，解決方案會使用三個傳送埠，將 EDIFACT 交換和建立的通知傳送至本機資料夾。  

  下圖顯示這個解決方案的架構：  

  ![接收 EDIFACT 交換及傳送通知](../core/media/edifact-walkthrough.gif "EDIFACT_Walkthrough")  

## <a name="configuring-and-testing-the-walkthrough"></a>設定和測試逐步解說  
 這個解決方案所需的程序包含下列步驟：  

- 將必要的訊息結構描述加入 BizTalk 專案，然後建置並部署此專案，讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可以使用該結構描述來處理收到的交換。  

- 建立單向接收埠，以便讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 從交易夥伴接收 EDIFACT 交換並產生通知。 此接收位置繫結至 Fabrikam 用來放置要傳送到 Contoso 的 EDIFACT 交換的檔案資料夾。  

  > [!NOTE]
  >  您可以使用雙向請求回應接收埠和位置來接收訊息，但是如果這樣做的話，就不能對接收位置使用 FILE 傳輸類型。  

- 建立兩個傳送埠，一個會將 EDI 交換傳送到 Contoso 本機資料夾，而另一個會將技術與功能通知傳送到 Fabrikam 本機資料夾。  

  > [!NOTE]
  >  和 X12 通知不同，功能與技術通知的訊息類型是一樣的。 因此，使用 `BTS.MessageType` 內容屬性建立的傳送埠篩選條件會篩選這兩種通知，並將它們傳送到相同的資料夾。  

- 為 Fabrikam 與 Contoso 建立合作對象 (交易夥伴)。  

- 分別為兩個交易夥伴建立商務設定檔。  

- 為要接收的訊息和要傳送的通知設定 EDI 屬性，來在兩個設定檔之間建立協議。  

- 使用測試 EDIFACT 交換以測試逐步解說。 就本逐步解說而言，您可以將下列程式碼複製並貼到文字檔中。 此檔案的結構描述為 EFACT_D98A_APERAK.xsd。  

  ```  
  UNA:+,?*'  
  UNB+UNOB:1+7654321:ZZZ+1234567:ZZZ+353501:3023+UNB5'  
  UNG+INVOIC+UNG2.1:ZZZ+UNG3.1:ZZZ+060413:2314+UNG5+UN+D:98B'  
  UNH+UNH1+APERAK:D:98A:UN++13+UNH5.1+UNH6.1+UNH7.1'  
  BGM+1+C10601'  
  DTM+10'  
  FTX+AAA++C10701+C10801'  
  CNT+1:14'  
  RFF+AAA'  
  DTM+10'  
  NAD+AA+C08201+C05801+C08001+C05901'  
  CTA++C05601'  
  COM+C07601:AA'  
  ERC+C90101'  
  FTX+AAA++C10701+C10801'  
  RFF+AAA'  
  FTX+AAA++C10701+C10801'  
  UNT+15+UNH1'  
  UNE+1+UNG5'  
  UNZ+1+UNB5'  
  ```  

### <a name="configuring-the-walkthrough"></a>設定逐步解說  
 本節說明設定逐步解說的程序。  

##### <a name="to-deploy-the-message-schema"></a>若要部署訊息結構描述  

1. 在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，建立或開啟 BizTalk 專案。  

   > [!NOTE]
   >  本主題假設您已經在「BizTalk EDI 應用程式」中加入了自己應用程式的參考 (包含 EDI 結構描述、管線和協調流程)， 如果沒有，請參閱[如何將參考加入 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。  

2. 以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下**現有項目**。 移至結構描述的資料夾[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\EDIFACT\D98A，，然後按兩下您的結構描述 (**EFACT_D98A_APERAK.xsd**)。  

   > [!NOTE]
   >  如果您使用本主題所提供的範例測試訊息，您必須使用**EFACT_D98A_APERAK.xsd**結構描述。  

   > [!NOTE]
   >  如果 EDI 結構描述尚未解壓縮至 \XSD_Schema\EDI 資料夾，執行**MicrosoftEdiXSDTemplates.exe** \XSD_Schema\EDI 資料夾結構描述解壓縮至預設資料夾中的檔案。  

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

5. 針對**目的地資料夾**，瀏覽至要接收交換的資料夾。 您已在此程序的步驟 1 中，建立此資料夾。 針對**檔案遮罩**，輸入交換格式，例如 **\*.edi**或是 **\*.txt**。  

6. 按一下 [確定] 。  

7. 在 **傳送管線**，選取**EdiSend**。  

8. 在主控台樹狀目錄中，選取**篩選器**。 輸入訂閱 EDI 交換的篩選條件。 例如，對於**屬性**，輸入**BTS。MessageType**; 對於**運算子**，輸入**==**; 及針對**值**輸入交換的結構描述`http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006#EFACT_D98A_APERAK`。  

   > [!NOTE]
   >  上述篩選條件設定可以確保會將交換 (而非通知) 傳送到與此傳送埠相關的資料夾。  

9. 按一下 [確定] 。  

10. 在主控台樹狀目錄中，按一下**傳送埠**。 在 **傳送埠**窗格中，以滑鼠右鍵按一下您的傳送埠，然後**開始**。  

##### <a name="to-create-a-static-one-way-send-port-to-send-the-acknowledgments"></a>若要建立靜態單向傳送埠以傳送通知  

1. 在 Windows 檔案總管中，建立本機資料夾，以便傳送技術與功能通知至此本機資料夾。  

2. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **靜態單向傳送埠**。  

3. 在 [**傳送埠屬性**] 對話方塊中，傳送埠的名稱。  

4. 在 **傳輸**區段中，選取**檔案**的**型別**，然後按一下**設定**。  

5. 針對**目的地資料夾**，瀏覽至要接收兩個通知的資料夾。 您已在此程序的步驟 1 中，建立此資料夾。 針對**檔案遮罩**，輸入交換格式，例如 **\*.edi**或是 **\*.txt**。  

6. 按一下 [確定] 。  

7. 在 **傳送管線**，選取**EdiSend**。  

8. 在主控台樹狀目錄中，選取**篩選器**。 輸入訂閱通知的篩選條件。 例如，對於**屬性**，輸入**BTS。MessageType**; 對於**運算子**，輸入**==**; 以及**值**通知中，輸入的結構描述`http://schemas.microsoft.com/Edi/Edifact#Efact_Contrl_Root`。  

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

3. 從**通訊協定**下拉式清單中，選取**EDIFACT**。  

4. 在 **第二個夥伴**區段中，從**名稱**下拉式清單中，選取**Contoso**。  

5. 在 **第二個夥伴**區段中，從**設定檔**下拉式清單中，選取**contoso_profile**。  

    您會發現兩個新的索引標籤取得新增旁**一般** 索引標籤。每個索引標籤各用於設定一個單向協議，而每個單向協議各代表一筆完整的訊息交易 (包含訊息傳輸與通知傳輸)。  

6. 在 **一般**索引標籤**一般屬性**頁面上，於**一般主控件設定**區段中，選取**開啟報告**，，然後選取 **儲存訊息內容 reporting**。  

7. 在上執行下列工作**Fabrikam-> Contoso**  索引標籤。  

   1. 上**識別碼**下方的頁面上**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**UNB2.1**， **UNB2.2**， **UNB3.1**，以及**UNB3.2**) 對應到您的測試訊息中那些標頭欄位的值。  

      > [!NOTE]
      >  對於傳送者和接收者，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 需要辨識符號與識別碼欄位，才能執行協議解析。 它會比對的值**UNB2.1**， **UNB2.2**， **UNB3.1**，以及**UNB3.2**交換標頭中的屬性協議。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會比對傳送者辨識符號和識別項 （不需接收者辨識符號和識別項） 也解析協議。 若 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法解析協議，它將會使用後援協議屬性。  
      > 
      > [!NOTE]
      >  如果您使用的稍早在本主題，做為測試訊息中提供的範例訊息，設定**UNB2.1**要**7654321**， **UNB2.2**至**ZZZ – 使用者相互定義**， **UNB3.1**要**1234567**，和**UNB3.2**至**ZZZ – 使用者相互定義**。  

   2. 在上**通知**頁面**交換設定** 區段中，核取**訊息回條 (CONTRL 預期)** 和**通知 (預期有 CONTRL)**。  

   3. 上**信封**下方的頁面上**交換設定** 區段中，核取**套用 UNA 區段 （字串服務建議）** 和**套用 UNG 區段 （功能群組標頭）**。  

   4. 上**驗證**下方的頁面上**交換設定**區段中，確定**交換控制編號 (UNB5)** 選項未核取。  

      > [!NOTE]
      >  清除**交換控制編號 (UNB5)** 屬性可讓您接收相同訊息的多個執行個體。  

   5. 上**字元集和分隔符號**下方的頁面上**交換設定**區段中，選取**CR LF**選項**UNA6 尾碼**。  

   6. 在上**本機主機設定**下方的頁面上**交換設定**區段中，清除**通知的路由設定為傳送管線在要求-回應接收埠**選項。  

      > [!NOTE]
      >  如果您使用雙向接收埠以接收交換並傳回通知，您會檢查**通知的路由設定為傳送管線在要求-回應接收埠**。  

   7. 上**傳送埠**下方的頁面上**交換設定**區段中，將會接收來自 Fabrikam 交換的傳送埠和接收的傳送埠建立關聯從 Contoso 的通知。 在 **傳送埠**格線下方**名稱** 欄中，按一下空白儲存格，並從下拉式清單中，選取 建立從 Fabrikam 接收 EDI 交換的傳送埠。 針對為了接收技術與功能通知而建立的傳送埠，重複此步驟。  

   8. 上**驗證**下方的頁面上**交易集設定**區段中，保留**EDI 類型驗證**核取，並檢查**擴充類型驗證**.  

   9. 如果您使用其中一個隨附之標準結構描述[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請在**本機主機設定**頁面下**交易集設定**區段中，選取要用來將結構描述的命名空間處理內送交換。 如果使用自訂的結構描述，請輸入中的值**自訂目標命名空間**方格中，以便[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以判斷命名空間使用群組和交易集標頭值。  

   10. 在上**信封**下方的頁面上**交易集設定**區段中，輸入在格線的第一行中的所有資料行的值。  


       |          使用           |                                以進行此動作                                 |
       |-----------------------------|---------------------------------------------------------------------------|
       |         **預設值**         |                            選取 **預設**。                            |
       | **針對訊息類型 UNH2.1** |         選取測試訊息，訊息類型**APERAK**。         |
       |         **UNH2.2**          |                       輸入 EDI 版本， **D**。                       |
       |         **UNH2.3**          |                    輸入版本號碼， **98A**。                     |
       |         **UNH2.5**          |                         您可以讓此處保持空白。                         |
       |    **目標命名空間**     |          選取  **<http://schemas.microsoft.com/Edi/Edifact>**。           |
       |          **UNG1**           |               指定功能群組識別碼**INVOIC**。                |
       |         **UNG2.1**          |         輸入應用程式傳送者識別的值。          |
       |         **UNG2.1**          | 輸入值，應用程式傳送者代碼辨識符號，如**ZZZ**。 |
       |         **UNG3.1**          |          輸入應用程式接收者識別的值。           |
       |         **UNG3.2**          |  值，輸入應用程式接收者代碼辨識符號，例如**ZZZ**。  |
       |          **UNG6**           |        輸入控管單位的值。 範例中，**取消**。         |
       |         **UNG7.1**          |          輸入訊息類型版本號碼。 範例中， **D**。           |
       |         **UNG7.2**          |         輸入訊息類型版次號碼。 範例中， **98A**。          |
       |         **UNG7.3**          |                         您可以讓此處保持空白。                         |
       |          **UNG8**           |                         您可以讓此處保持空白。                         |


8. 在上執行下列工作**Contoso-> Fabrikam**  索引標籤。  

   > [!NOTE]
   >  在此逐步解說中，我們在索引標籤中指定必要值，以便可以順利地建立協議。 若要成功建立協議，兩個單向協議索引標籤必須已定義的值**UNG2.1**， **UNG2.2**， **UNG3.1**，和**UNG3.2**.  

   > [!NOTE]
   >  雖然通知屬於同一個訊息交易的一部分，在中設定通知的產生方式的相關的屬性**Contoso-> Fabrikam**  索引標籤。這是必要的因為通知內容屬性傳送者和接收者限定詞設定為您在指定的值相反**Contoso-> Fabrikam**  索引標籤。比方說，如果傳送者和接收者識別碼設為 7654321 與 1234567 中的**Fabrikam-> Contoso**  索引標籤、 寄件者與接收者內容屬性會在通知中設為 1234567 與 7654321。 另外那一個單向協議索引標籤通常也會分別將傳送者與接收者識別碼設為 1234567 與 7654321。 因此，通知訊息會解析成該協議，並將挑選屬性設定。 因此，如果您想要讓通知使用不同的項目分隔符號，或如果您想要讓通知使用 CR LF，指定中的屬性**Contoso-> Fabrikam**  索引標籤。  
   >   
   >  在概念上，將會從傳送者與接收者辨識符號與在通知的內容屬性中所設定值相同的任一個單向協議索引標籤中挑選通知的屬性。 但為便於實際應用，通常會在您所建立由交換解析而成之協議的其他單向協議索引標籤中設定此屬性。  

   1.  上**識別碼**下方的頁面上**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**UNG2.1**， **UNG2.2**， **UNG3.1**，以及**UNG3.2**) 對應到您的測試訊息中那些標頭欄位的值。  

       > [!NOTE]
       >  如果您使用的稍早在本主題，做為測試訊息中提供的範例訊息，設定**UNB2.1**要**1234567**， **UNB2.2**至**ZZZ – 使用者相互定義**， **UNB3.1**要**7654321**，和**UNB3.2**至**ZZZ – 使用者相互定義**。  

9. 按一下 **[套用]**。  

10. 按一下 [確定] 。 中新增的協議會列為**協議**一節**合作對象與商務設定檔**窗格。 預設會啟用新增的協議。  

### <a name="testing-the-walkthrough"></a>測試逐步解說  
 本節提供關於如何測試逐步解說的資訊。  

##### <a name="to-test-the-walkthrough"></a>若要測試逐步解說  

1. 在 Windows 檔案總管中，將測試 EDI 交換置放到本機接收資料夾中。  

   > [!NOTE]
   >  對於測試訊息，您可以使用本主題先前提供的範例訊息。 將訊息複製到文字檔，並以 .txt 副檔名儲存檔案。 如果您使用此訊息，則必須部署 EFACT_D98A_APERAK.xsd 結構描述。 結構描述使用，請執行**MicrosoftEdiXSDTemplates.exe**檔案 （位於 \XSD_Schema\EDI 資料夾中），將結構描述解壓縮至預設資料夾。 然後，[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\EDIFACT\D98A 下就會出現 EFACT_D98A_APERAK.xsd 結構描述。  

2. 開啟與交換傳送埠相關聯的資料夾，並確認其中有包含 EDI 交換。  

3. 開啟與通知傳送埠相關聯的資料夾，並確認其中包含技術與功能通知。  

## <a name="see-also"></a>另請參閱  
 [開發和設定 BizTalk Server EDI 解決方案](../core/developing-and-configuring-biztalk-server-edi-solutions.md)