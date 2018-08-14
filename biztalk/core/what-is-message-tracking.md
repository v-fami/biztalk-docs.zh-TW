---
title: 什麼是訊息追蹤？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HAT, metadata
- HAT, messages
- messages, tracking
- data, HAT
- metadata, tracking
- tracking, metadata
- HAT, data security
- tracking, messages
- configuring [HAT tracking], messages
- data, security
ms.assetid: 51cec59d-b411-4d8f-b771-7b2cf0f38945
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 944261c6193020c158f707b7f8d39c55ce2d058f
ms.sourcegitcommit: ed9590dbcd97c12a1fe5ce2cdf8d826492cccdff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39640122"
---
# <a name="what-is-message-tracking"></a>什麼是訊息追蹤？
訊息是資料的電子執行個體，通常在兩個執行的商務程序或應用程式之間進行交換。 訊息執行個體是由訊息內文、訊息屬性和中繼資料組成的。  
  
 您可以使用 BizTalk Server 管理主控台來啟用訊息內文和訊息屬性追蹤。 在那裡，您也可以檢視追蹤的訊息內文，包括結構描述資訊、強式名稱和產生之訊息的所有升級屬性。  
  
## <a name="message-body"></a>訊息內文  
 追蹤訊息內文可以提供已傳送和已接收訊息的記錄。 您必須開啟訊息內文追蹤，才能在服務執行個體處理完成後儲存訊息。 設定完追蹤選項後，可能需要幾分鐘的時間才能檢視訊息。  
  
> [!IMPORTANT]
>  必須在所有 MessageBox 資料庫上執行 SQL Server Agent 服務。 TrackedMessages_Copy_\<MessageBoxName\>工作讓訊息內文可供追蹤查詢和 WMI。 若要有效率地複製訊息內文，保留在 MessageBox 資料庫中的人員，並會定期複製到 BizTalk 追蹤 (BizTalkDTADb) 資料庫 TrackedMessages_Copy_\<MessageBoxName\>作業。 執行 SQL Server Agent 服務也是讓封存和清除這兩個程序正常運作的必要條件。  
  
 透過已追蹤訊息可以提供確認回條、進行疑難排解，並且在過去的交易中執行資料採礦。 您可以於連接埠、管線和協調流程的輸入和輸出追蹤訊息內文。 您可以使用 BizTalk Server 管理主控台、「作業」物件模型 (OM) (建議) 或透過 Windows Management Instrumentation (WMI) 應用程式發展介面 (API) 來復原這些訊息。  
  
 BizTalk Server 不會追蹤沒有成功通過其中一個追蹤點的訊息。 在某些情況下，例如它是無效的因為當擱置的訊息，或如果沒有主應用程式等待訊息，可能就已擱置佇列中沒有正在追蹤。 若終止此訊息，將不會有任何關於此訊息的記錄。  
  
> [!IMPORTANT]
>  訊息內文追蹤不對等於合法追蹤，而且也不支援不可否認性。  
  
## <a name="message-properties"></a>訊息屬性  
 訊息屬性中包括升級屬性、路由資訊以及交易夥伴資料。 訊息屬性追蹤在結果清單中為每個訊息提供升級屬性的記錄，讓您可從已追蹤的數千個訊息中找到特定的訊息。 您便可使用其中一個屬性追蹤訊息本身的子集。  
  
 若要追蹤內容屬性，請定義內容中使用的命名空間屬性結構描述來儲存屬性。 在此檢視中可以選取要追蹤的內容屬性。BizTalk Server 追蹤這些屬性的方式，與追蹤升級訊息屬性的方式相同。  
  
> [!NOTE]
>  請確定您在結構描述中為屬性指定不同的名稱。 若建立重複名稱，會出現錯誤訊息。  
  
 例如，您可以使用「結構描述編輯器」升級 Purchase Order 結構描述的 PO Number 欄位。 然後，使用 [尋找訊息] 檢視，即可找到包含該追蹤欄位之特定值的訊息執行個體，如 PO Number = 16995。  
  
 訊息屬性追蹤所產生的負擔遠低於訊息內文追蹤，因為「訊息屬性追蹤」只會追蹤選取的欄位。 設定完訊息屬性的追蹤選項後，可能需要幾分鐘的時間才能檢視屬性。  
  
## <a name="metadata"></a>中繼資料  
 中繼資料像是訊息執行個體識別項、協調流程或管線記錄訊息，也就是協調流程或管線記錄訊息以及其他相關追蹤詳細資料的地方。 為使 MessageBox 資料庫中的訊息可以路由到商務程序，訊息中必須包含訊息類型及來源等內容屬性。 這些屬性即成為中繼資料。 訊息與服務執行個體追蹤會使用訂閱準則，對這些中繼資料進行查詢。  
  
 透過 BizTalk Server 管理主控台，您可以藉由選取特定的系統結構描述來升級內容屬性。 系統結構描述位於 Applications\BizTalk.System\Schemas 節點。 BizTalk Server 會全域追蹤這些內容屬性 — 也就是所有訊息現在會都追蹤特定的內容屬性。 這種作法可能會大幅增加 BizTalk 追蹤資料庫的大小。  
  
## <a name="sensitive-data"></a>機密資料  
 您可以保全以下資料，確保這些資料不會出現在對應的結構描述屬性視窗中，如此一來就不能加以追蹤。  
  
-   適用於**isSensitive**屬性至屬性結構描述中的任何機密屬性，如此就不會再顯示在訊息屬性追蹤組態選項。  
  
-   所有現成傳輸都包含標示為機密的密碼，因此無法追蹤這些傳輸。  
  
-   此外，這些機密屬性不再存在於「管理」資料庫內，所以若您直接在資料庫中設定追蹤選項，就不能追蹤這些屬性。  
  
-   如果您追蹤網路上輸出的訊息內文，訊息追蹤會從已追蹤訊息內文的捷徑移除所有傳輸屬性。 因此，訊息追蹤除了從已追蹤訊息內文的捷徑移除所有的輸出傳輸屬性外，也會從輸入傳輸移除屬性。  
  
    > [!IMPORTANT]
    >  升級的屬性可以包含機密資料。 如果從 [群組中樞] 頁面的追蹤查詢追蹤的屬性，其中包含機密資料，以執行追蹤查詢的權限的任何使用者可以檢視此資料。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk Server 管理主控台設定追蹤](http://msdn.microsoft.com/49b7f9d3-60b5-41bd-ba8b-029253926bef)
