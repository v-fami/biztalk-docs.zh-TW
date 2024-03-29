---
title: 管理協議 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.admin.resultsobject.agreement
ms.assetid: e9c6cdd1-8c17-4b1e-a556-2b287593bb9d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4151c96d815022efc9e7e2adc6beb25e9af8f513
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975127"
---
# <a name="managing-agreements"></a>管理協議
交易夥伴協議 (TPA) 的定義是，兩個交易夥伴之間透過特定 B2B 通訊協定交易訊息時所採用的決定性與繫結性協議。 請參閱[交易夥伴協議](../core/trading-partner-agreement.md)。 

本主題會示範如何建立、 檢視、 編輯、 啟用、 停用，或刪除協議。  

## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  

## <a name="create-an-agreement"></a>建立協議  

1. 開啟**BizTalk Server 管理**，展開 BizTalk 群組，然後選取**合作對象**。 
2. 在 **合作對象與商務設定檔**頁面上，以滑鼠右鍵按一下您要建立，選取協議的商務設定檔**新增**，然後選取**協議**。  

3. 在 **一般屬性**: 

   1. 在 **協議參數**區段中，執行下列動作：  


      |   使用   |                                                                                                                                                                                                                                                                                                                                                                                                                                                     以進行此動作                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
      |--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |   **名稱**   |                                                                                                                                                                                                                                                                                                                                                                                                                                           輸入協議名稱                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |    **ID**    |                                                                                                                                                                                                                                                                                                                                                                列示協議的唯一識別。 此文字方塊是唯讀的並顯示協議識別碼之後您選取,**套用**第一個時間，以及設定會被接受。                                                                                                                                                                                                                                                                                                                                                                |
      |  **狀態**  |                                                                                                                                                                                                                                                                                                                                                 指定協議的狀態。 根據預設，在建立協議**Active**狀態。 如果您想要停用時建立的第一個選取的協議**停用**從下拉式清單。                                                                                                                                                                                                                                                                                                                                                  |
      | **通訊協定** | 指定協議的通訊協定。<br /><br /> -若為 X12 編碼通訊協定，請選取**X12**從下拉式清單。 請參閱[設定 X12 特定協議屬性](../core/configuring-x12-specific-agreement-properties.md)<br />-若為 EDIFACT 編碼通訊協定，請選取**EDIFACT**從下拉式清單。  請參閱[設定 EDIFACT 特定協議屬性](../core/configuring-edifact-specific-agreement-properties.md)。<br />-若為 AS2 編碼通訊協定，請選取**AS2**從下拉式清單。 請參閱[設定 AS2 協議屬性](../core/configuring-as2-agreement-properties.md)。 <br/><br/>**注意**<br/>  單向協議索引標籤中會提供協議屬性。 當您選取要用來建立協議的第二個設定檔之後，單向協議索引標籤就會顯示。 您會在下列步驟中選取第二個夥伴。 |


   2. 在 **第一夥伴**區段中，執行下列動作：  


      |     使用     |                                                                                                      以進行此動作                                                                                                       |
      |------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |     **名稱**     |                                             顯示要建立協議的商務設定檔所屬之夥伴名稱。 此文字方塊會處於唯讀狀態。                                             |
      |   **設定檔**    |                                                        顯示您正在為它建立協議的設定檔名稱。 此文字方塊會處於唯讀狀態。                                                         |
      | **通訊協定的設定** | 如果您在商務設定檔中建立了 X12 通訊協定集，即可從下拉式清單中選取該集合。 如果您未在商務設定檔建立 X12 通訊協定集，可以保留空白。 |


   3. 在 **第二個夥伴**區段中，執行下列動作：  

      |使用|以進行此動作|  
      |--------------|----------------|  
      |**名稱**|從下拉式清單中選取要與他的商務設定檔建立協議的合作對象。|  
      |**設定檔**|從下拉式清單中選取要和它建立協議的設定檔。|  
      |**通訊協定的設定**|如果您在商務設定檔中建立了 X12 通訊協定集，即可從下拉式清單中選取該集合。 如果您未在商務設定檔建立 X12 通訊協定集，可以保留空白。|  

      > [!TIP]
      >  按下`CTRL`，選取 商務設定檔，將會在協議，以滑鼠右鍵按一下其中一個商務設定檔，然後選取**新增**，然後選取**協議**。 值夥伴名稱與兩個夥伴的商務設定檔中會自動填入**協議屬性** 對話方塊。  

      > [!NOTE]
      >  當您選取另一個設定檔時，兩個索引標籤已新增旁**一般** 索引標籤。每個索引標籤各代表兩個合作對象之間的一個單向協議。 您可以使用索引標籤來輸入協議屬性。  

   4. 選取 **啟用協議**核取方塊以啟用協議，並執行下列動作：  


      |    使用     |                                        以進行此動作                                        |
      |-----------------|------------------------------------------------------------------------------------------|
      |    **來源**     |               選取的日期和時間的協議的有效來源。                |
      | **沒有結束日期** | 如果不想設定停用協議的結束日期，請選取此選項。 |
      |   **結束於**    |       選取此選項即可輸入的日期和時間之前有效協議。        |


   5. 在 **一般主控件設定**區段中，執行下列動作：  


      |                使用                 |                                                                                                                                                                     以進行此動作                                                                                                                                                                     |
      |-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |       **將錯誤記錄到事件記錄檔**       |                                         選取此選項可將 EDI 引擎 (EDI 管線、批次處理協調流程、路由協調流程等) 產生的任何錯誤，與內容資訊一起記錄至 Windows 事件檢視器。<br/><br/>**請注意**： 不適用於 AS2 協議。                                         |
      |      **將警告記錄到事件記錄檔**      |                                       選取此選項可將 EDI 引擎 (EDI 管線、批次處理協調流程、路由協調流程等) 產生的任何警告，與內容資訊一起記錄至 Windows 事件檢視器。 <br/><br/>**請注意**： 不適用於 AS2 協議。                                        |
      |          **開啟報表**          | 選取此選項可顯示所有 EDI 訊息 （內送和外寄） 的狀態項目上**EDI 交換和相互關聯的 ACK 狀態**索引標籤**群組概觀**頁面[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如果未選取，則會不顯示任何狀態項目。 |
      | **儲存報告訊息內容** |                                                                       如果您選取**開啟報告**，選取此選項可儲存交易設定的追蹤 (BizTalkDTADb) 資料庫的 EDI 資料表中。 <br/><br/>**請注意**： 不適用於 AS2 協議。                                                                        |


4. 在 **一般**索引標籤**連絡人資訊**頁面上，執行下列動作：  

   1.  在  **Contact1**索引標籤上，輸入與您要建立協議的合作對象的設定檔的連絡資訊。 這項資料是僅供參考;它不是由 BizTalk 執行階段。  

   2.  若要新增連絡人的另一個索引標籤，選取**的新連絡人** 索引標籤。  

   3.  若要刪除連絡人索引標籤，選取**刪除**從右上角的索引標籤頁。  

       > [!NOTE]
       >  您無法刪除**Contact1**  索引標籤。您只能刪除您新增的索引標籤。  

5. 在 **一般**索引標籤**其他屬性**頁面上，執行下列動作：  

   > [!NOTE]
   >  您在此頁面輸入的資訊不是由 BizTalk Server 進行任何處理;這項資料是僅供參考之用。  

   1.  在 **其他屬性**方格中，輸入您想要新增的任何資訊與相關的合作對象或協議名稱 / 值組。  請輸入名稱-值組來儲存合作對象的任何資訊。 您可以視需要新增任意數目的名稱-值組。  

        刪除名稱 / 值組，請選取資料列，然後選取**刪除**從右上角。  

   2.  在 **文字 1**，**文字 2**，並**協議**文字方塊中，輸入合作對象的協議的相關資訊。  

   3.  選取**套用**以接受這些屬性，或選取**確定**完成組態設定。 任何一項動作會驗證設定。  

## <a name="view-or-change-an-agreement"></a>檢視或變更協議  

1.  在 [ **BizTalk Server 管理]**，選取**合作對象**。 

2. 在 **合作對象與商務設定檔**頁面上，選取任何擁有您想要檢視或編輯協議的兩個商務設定檔。  

3.  在 **協議**區段中，以滑鼠右鍵按一下 協議，然後再選取**屬性**。  

4.  在 **協議屬性**、 檢視或編輯協議。 您可以在不同的索引標籤和中的頁面上輸入的值**協議屬性**對話方塊方塊中，請參閱下列：  

    |如需|請參閱|  
    |--------------|--------------|  
    |X12 協議|[設定 X12 特定協議屬性](../core/configuring-x12-specific-agreement-properties.md)|  
    |EDIFACT 協議|[設定 EDIFACT 特定協議屬性](../core/configuring-edifact-specific-agreement-properties.md)|  
    |AS2 協議|[設定 AS2 協議屬性](../core/configuring-as2-agreement-properties.md)|  

5.  選取**套用**以接受這些屬性，或選取**確定**完成組態設定。 任何一項動作會驗證設定。 

## <a name="enable-or-disable-an-agreement"></a>啟用或停用協議  

1.  在 [ **BizTalk Server 管理]**，選取**合作對象**。 

2. 在 **合作對象與商務設定檔**頁面上，選取任何有您想要編輯合約的兩個商務設定檔。  

3.  在 **協議**區段中，以滑鼠右鍵按一下 協議，然後再選取**啟用**或是**停用**。 

    > [!NOTE]
    >  根據預設，初次建立的協議一定是啟用狀態。 **啟用**選項才可以使用只有當協議停用。 **停用**選項才可以使用只有在啟用協議時。  

## <a name="delete-an-agreement"></a>刪除合約  
1.  在 [ **BizTalk Server 管理]**，選取**合作對象**。 

2.  在 **合作對象與商務設定檔**頁面上，選取其中兩個商務設定檔具有您想要刪除的協議。  

3.  在 **協議**區段中，以滑鼠右鍵按一下您想要刪除此項目，然後選取 協議**刪除**。  

4.  在 **確認刪除協議**對話方塊中，選取**是**刪除協議。  


## <a name="see-also"></a>另請參閱  
 [管理 EDI 和 AS2 解決方案](../core/managing-edi-and-as2-solutions.md)