---
title: "設定外寄批次 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75e6f41a-0e24-47bf-9234-125791c62044
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de6b7ef0a8683374322d4b6f720bc1ebd1ed4b06
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-an-outgoing-batch"></a>設定外寄批次
若要定義 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將交易集批次處理成 EDI 交換的方式，您必須為協議建立一或多個批次組態。 所有由 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 關聯至該協議且符合批次篩選條件準則的交換，都會根據該批次組態的相同釋放準則進行批次處理和釋放。  
  
 批次組態包括了批次名稱、批次識別碼、篩選條件定義、群組定義、批次釋放準則和批次啟動準則。 所有屬性和與批次相關的選項都位於**批次組態**頁面的單向協議索引標籤中**協議屬性** 對話方塊。 若要建立協議的批次組態，請參閱[設定批次處理 (X12)](../core/configuring-batching-x12.md)。  
  
> [!NOTE]
>  批次的文件標準是由協議屬性本身決定。 例如，如果協議是針對 X12 訊息，則批次的文件標準會是 X12。  
  
## <a name="batch-categories"></a>批次類別  
 使用右上角的下拉式清單**批次組態**頁面，來決定所顯示的批次組態。  
  
-   **所有**： 顯示所有批次組態。  
  
-   **Active**： 僅顯示作用中批次組態。  
  
-   **非作用中**： 僅顯示非作用中批次組態。  
  
## <a name="batch-identification"></a>批次識別  
 批次識別包含批次名稱、描述、批次識別碼和批次協調流程執行個體識別碼。  
  
### <a name="batch-name"></a>批次名稱  
 根據指定的批次名稱建立批次組態**批次組態**頁面的單向協議索引標籤中**協議屬性** 對話方塊。 多個批次可以共用相同的組態設定，但是必須具有唯一的批次名稱。  
  
### <a name="batch-description"></a>批次描述  
 批次描述文字方塊可提供批次組態的描述。  
  
### <a name="batch-id"></a>批次識別碼  
 批次識別碼會自動產生[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中建立新的批次組態時**批次組態**頁面。 BatchMarker 管線元件使用此值，為符合特定批次組態之批次篩選條件的內送交換加上旗標。 此值也會做為與特定批次組態相關聯之批次處理協調流程的訂閱篩選條件。  
  
### <a name="orchestration-instance-id"></a>協調流程執行個體識別碼  
 針對此批次組態啟動之批次協調流程執行個體的協調流程執行個體識別碼。  
  
## <a name="batch-filter"></a>批次篩選條件  
 批次建立根據中套用的批次篩選條件定義**批次組態**頁面的單向協議索引標籤中**協議屬性** 對話方塊。 在這個篩選條件中，您會決定要批次處理哪些交易集或訊息。 您可以在批次協調流程的執行個體已啟動的情況下，同時變更這個篩選條件的值。 變更這個篩選條件並不會影響批次釋放準則。  
  
> [!NOTE]
>  如果您變更作用中批次的批次篩選條件，則由於 Biztalk Server 會快取此資訊的關係，您將需要等候 15 分鐘的時間讓新的篩選條件準則變成作用中。 無法修改此重新整理間隔。  
>   
>  若要強制將新的篩選條件立即變成作用中，請重新啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 主控件程序。  
  
 外寄批次可包含多個群組，但一種交易類型只能有一個群組。 一個群組可以包含多個交易集，但每個交易集的交易類型都必須相同。  
  
 多個批次組態可以共用同一個批次篩選條件，而符合多個批次篩選條件的文件將會路由至所有相符的批次。  
  
## <a name="group-definition"></a>群組定義  
 您可以透過在協議屬性中定義功能群組標頭 (X12 編碼為 GS，EDIFACT 編碼為 UNG)，決定批次輸出中的群組組成方式。 群組則會根據其「交易集識別代碼」(ST1，X12 適用) 或「訊息類型」(UNH2.1，EDIFACT 適用)、所屬版本及其目標命名空間來加以定義。 例如，交換可以包含組合了一種訊息類型的一個群組，以及另一個組合有其他種訊息類型的群組。 如需有關設定群組的詳細資訊，請參閱[設定 EDI 屬性](../core/configuring-edi-properties.md)。  
  
> [!NOTE]
>  交換中的群組則未定義順序。  
  
## <a name="batch-release-criteria"></a>批次釋放準則  
 會根據設定的準則釋放批次**批次組態**頁面的單向協議索引標籤中**協議屬性** 對話方塊。 批次可能會根據下列任一方法來加以釋放：  
  
-   根據每小時、每天或每週一次的排程。  
  
-   當交易集達到可湊成群組的特定數目。  
  
-   當交易集達到可湊成交換的特定數目。  
  
-   當字元達到可處理成批次的特定數目。  
  
-   當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 外部的應用程式執行了外部觸發程序。  
  
 如果您選取**傳送空的批次訊號**屬性**批次排程**對話方塊中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]批次排定即使已經沒有訊息要傳送時，會送出空的批次訊息接收批次處理協調流程。  
  
## <a name="batch-activation-criteria"></a>批次啟動準則  
 只有在符合批次啟動準則時，才會根據批次釋放準則來釋放批次。 若要啟動協調流程執行個體，您必須按**啟動**按鈕**批次組態**頁面的單向協議索引標籤中**協議屬性** 對話方塊。 這樣會建立批次組態的協調流程執行個體。 如果**啟動**按鈕為可按，目前尚未啟動的批次組態的協調流程執行個體。  
  
 您按下之後**啟動** 按鈕，只有當下列條件成立時，將批次收集訊息：  
  
-   這些訊息符合批次篩選條件中的準則。  
  
-   日期和時間是之後輸入的日期時間**啟動**欄位。  
  
-   日期和時間是在輸入值之前**結束**欄位或處理的批次的數字是否小於或等於中發生次數**發生幾次之後結束**欄位或**沒有結束日期**選取選項。 所有的三個選項都適用於**終止**> 一節。  
  
 啟動準則中設定**批次組態**頁面的單向協議索引標籤中**協議屬性** 對話方塊。  
  
 您已按下之後**啟動**按鈕來啟動批次處理協調流程執行個體，訊息將不會收集批次之前提及的時間**啟動**屬性已通過。  在**批次組態**頁面上，如果**立即開始**未選取和**啟動**日期時間設定為早於您按時間值**啟動** 按鈕，批次處理將會立即啟動協調流程為作用中。 如果啟動日期時間是在未來時間，批次處理將會在該時間開始。  
  
 您可以設定**啟動**是未來的日期時間的日期時間。 不過，如果您按一下**啟動**按鈕時**啟動**日期時間是在未來，將會啟動協調流程執行個體，但會收集任何訊息，直到開始的日期時間，就會發生。 BatchMarker 管線元件會等到開始日期時間到了，才會升級要將訊息路由到路由協調流程或是批次處理協調流程時所需要的適當屬性。 這樣一來，系統就不會批次處理該訊息。 不過，訊息將會挑選任何傳送埠或協調流程個別的訊息訂閱。 如需 BatchMarker 管線元件功用的詳細資訊，請參閱[組合批次 EDI 交換](../core/assembling-a-batched-edi-interchange.md)。  
  
## <a name="batch-termination-criteria"></a>批次終止準則  
 訊息會停止收集批次**結束**日期時間或之後的中的發生次數**發生幾次之後結束**屬性。 如果您不想要停用批次處理協調流程，請選取**沒有結束日期**選項。  
  
> [!NOTE]
>  如果**發生幾次之後結束**已選取屬性，空的批次訊號計數朝結束批次啟動範圍需要用到發生次數。 如果發生通常會導致發出空批次訊號的情況 (在批次已排程傳送時，批次處理協調流程卻沒有收到任何訊息)，但是卻由於該訊號未設定而沒有傳送任何空的批次訊號時，發生次數也會進行遞增。  
  
## <a name="see-also"></a>另請參閱  
 [批次處理外寄 EDI 訊息](../core/batching-outgoing-edi-messages.md)