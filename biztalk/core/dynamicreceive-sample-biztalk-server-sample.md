---
title: DynamicReceive 範例 （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0fa7c934-7ec3-45ad-b226-c8c53934ecb1
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af89bac79614268f4648f688d8cabfc913ed2277
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974127"
---
# <a name="dynamicreceive-sample-biztalk-server-sample"></a>DynamicReceive 範例 (BizTalk Server 範例)
DynamicReceive 範例示範在動態指定 MQSeries 佇列的 URI 時，如何從 MQSeries 佇列接收 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 訊息。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例會動態建立 MQSeries 佇列所指定**queueManager**，**佇列**，並**server**變數。 它會啟用動態接收案例，並取得[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中指定的篩選準則為基礎的動態指定 MQSeries 佇列的訊息**MQMD_MsgId**並**MQMD_CorrelId**訊息屬性。  
  
## <a name="how-this-sample-was-designed-and-why"></a>此範例的設計方式和原因  
 MQSeries 配接器可以透過在協調流程中指定佇列的 URI 位址，從 MQSeries 佇列動態接收訊息。 您可以在協調流程中使用請求-回應傳送埠來達成這項功能。  
  
 若要動態接收訊息，指定下列項目中的**運算式**協調流程中的圖形：  
  
1. 啟用動態接收藉由設定下列屬性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]訊息： **MQSeries.DynamicReceive** = `'Yes'`  
  
2. 設定連接埠 URI，以指定取得訊息的來源位址。 您可以選擇指定下列選項：  
  
   -   之前收到的訊息，使用指定的等待間隔**MQSeries.WaitInterval**訊息上的屬性。  
  
   -   指定接收訊息的比對準則。 比對準則的選項包括**訊息識別碼**， **CorrelationID**， **GroupID**，以及**MessageSequenceNumber**。 請參閱 < 屬性相關至 BizTalk Server >，網址[ http://go.microsoft.com/fwlink/?LinkId=89396 ](http://go.microsoft.com/fwlink/?LinkId=89396)如需詳細資訊。  
  
   使用這些屬性建立訊息之後，便會使用請求-回應傳送埠將它傳送到 MQSeries 佇列。 這個傳送埠會使用指定的比對選項，讓配接器從指定的 URI 接收訊息。 產生的結果如下：  
  
- 如果符合用來取得訊息的篩選準則，便會從佇列擷取訊息，然後再將訊息傳回給協調流程。  
  
- 如果不符合用來取得訊息的篩選準則，則會傳回虛擬回應。 這表示指定的選項並未從佇列傳回任何訊息。  
  
  使用動態接收功能可以讓您擁有更多的彈性，因為您不需要有固定的接收位置。 在某些情況下，您可能必須等到執行階段才會知道 URI。 動態接收功能可讓您動態決定訊息的取得來源。 這也表示您不需要在協調流程內實作佇列合約。  您可以等待，以根據指定的比對準則，使用動態指定的 URI 從 MQSeries 佇列取得訊息。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 \<*範例路徑*\>\Samples\AdaptersUsage\MQSeriesAdapter\DynamicReceive  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|||  
|-|-|  
|檔案|描述|  
|DynamicReceive.btproj,<br /><br /> DynamicReceive.sln|應用程式的專案和方案檔。|  
|DynamicReceive e.odx|應用程式的 BizTalk 協調流程檔案。|  
|Setup.bat|用來建立金鑰檔、編譯專案及部署專案的批次檔。|  
  
## <a name="how-to-use-this-sample"></a>如何使用此範例  
 指定**Microsoft.XLANGs.BaseTypes.Address**對於您的解決方案。 變更**MQSeries.WaitInterval**來指定當您預期收到的回應訊息。 更新 (或加入) 比對選項；如果您想取得所有訊息，則請移除比對選項。  
  
## <a name="building-and-running-the-sample"></a>建置和執行範例  
  
#### <a name="to-create-the-sample"></a>若要建立範例  
  
1. 在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中建立新的協調流程。  
  
2. 啟用動態接收作業，藉由設定**MQSeries.DynamicReceive**屬性上的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]訊息給`'Yes'`。  
  
3. 指定要從其中取得訊息的設定位址**連接埠 URI**。  
  
4. 可以選擇指定下列兩個選項：  
  
   1.  之前使用，以取得訊息，指定等待間隔**MQSeries.WaitInterval**訊息上的屬性。  
  
   2.  指定接收訊息的比對準則。 如需詳細資訊，請參閱「比對選項」說明。  
  
5. 在協調流程中變更下列變數，以指定取得訊息的來源：  
  
   -   **佇列**， **queueManager**，以及**server**。 這些用來建置 URI**運算式**圖形。  
  
6. 修改**運算式**圖形，以視需要取消註解動態佇列建立和比對選項。  
  
7. 您可以使用下列其中一種方法來建置及部署專案：  
  
   -   開啟方案，以滑鼠右鍵按一下方案總管 中的專案，按一下**屬性**檢視專案屬性。 在 [簽署] 索引標籤上按一下**\<新增...\>** 中**選擇強式名稱金鑰檔**下拉式方塊。 然後提供金鑰檔名稱，並部署。  
  
   -   或者，執行用來建立金鑰檔、建置專案及部署專案的 setup.bat 檔案。  
  
#### <a name="to-run-the-sample"></a>執行範例  
  
1.  將協調流程繫結到 BizTalk 主控件。  
  
2.  啟用協調流程建立的檔案接收埠。 變更檔案接收位置從**c:\temp\in**至適當的檔案資料夾。  
  
3.  登錄並啟動建立的兩個傳送埠。 其中一個連接埠屬於動態的請求-回應連接埠類型，另一個則是檔案傳送埠，也是傳送訊息的佇列。 請務必將它設定為正確的位置。  
  
4.  若要啟動協調流程，請將檔案放到輸入資料夾中。 這樣會叫用 MQSeries 配接器並呼叫**MQSAgent2** COM + 元件，以取得訊息指定的伺服器上。 接收訊息會出現在檔案傳送埠中指定的資料夾位置。  
  
5.  如果沒有任何訊息找到符合指定準則**運算式**圖形，將虛擬訊息放入輸出資料夾。 若要停用比對選項，請取消註解中的最後兩行**運算式**圖形。  
  
## <a name="comments"></a>註解  
  
-   如果佇列採動態方式建立，但卻不會動態刪除，則在啟動下一個協調流程時，將會發生錯誤。  
  
-   雖然這個範例只指定了一種選項，但是還有其他方法可以動態設定 URI。 例如，URI 可以透過讀取訊息內容中的某個屬性來設定。  
  
-   如果佇列中沒有任何訊息符合比對選項，便會傳回虛擬訊息。  
  
-   因為這個範例使用的是動態傳送埠，所以可能必須指定其他選項，例如重試和交易。 將訊息傳送到動態請求-回應連接埠之前，請先使用配接器所公開的內容屬性來設定這些選項。  
  
-   MQSeries 佇列可以建立及使用刪除動態**MQSAdapterAdmin2**介面。 如何動態建立 MQSeries 佇列的範例，請參閱 < 支援的佇列的管理 >，網址[ http://go.microsoft.com/fwlink/?LinkId=89400 ](http://go.microsoft.com/fwlink/?LinkId=89400)。