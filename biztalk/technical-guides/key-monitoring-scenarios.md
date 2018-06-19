---
title: 主要監視案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fee90fd2-fb85-409f-827e-6ee3c8e13b4c
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99f8f1427f5f5535b6c446dae3057b4d80754a7f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298766"
---
# <a name="key-monitoring-scenarios"></a>重要監視案例
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operations Manager 2007 R2/2012年管理組件包含下表中所述的重要監視案例數。  
  
### <a name="biztalk-server-monitoring-scenarios"></a>BizTalk Server 監控實例  
  
|狀況|Description|  
|--------------|-----------------|  
|擱置的訊息警示|監視與解決擱置的訊息相關的問題是 BizTalk Server 環境中常見的操作工作。 BizTalk Server 管理組件可讓您監視和疑難排解擱置的訊息事件有效率的方式。 當您處理訊息時 BizTalk Server 中發生訊息擱置的兩種： 輸入訊息擱置和輸出訊息擱置。<br /><br /> 對於輸入訊息，處理錯誤或是缺少訂閱的各種可能會導致訊息被擱置。 有些傳輸可以設定為要擱置訊息或不要擱置訊息。 對於輸出訊息，所有的處理錯誤都會導致訊息擱置。<br /><br /> 對於輸入訊息，每個配接器寫入暫止的警示規則。 此方法提供更大的彈性來處理內送端的訊息擱置。 您可以加入不同的回應動作根據配接器，例如通知。 您可以另外自訂 BizTalk Server 管理組件，藉由建立自訂規則。 對於輸出訊息，所有的訊息永遠擱置任何種類的傳輸時間失敗。|  
|警示隱藏原則|擱置訊息規則會採用不同的隱藏項目原則比通常會套用於其他規則。 會根據警示名稱、警示來源與電腦及網域來隱藏警示。<br /><br /> 歸併警示來源為基礎，每個擱置的訊息規則的警示來源也包含從擱置的訊息事件擷取的參數。 此參數便是在其上接收或傳輸訊息的 URI。<br /><br /> 在相同的 URI 上發生的錯誤通常是因為相同的原因。 因此，我們建議您建立相同的根本原因的單一警示，即使存在多個相關的錯誤事件。 這可讓您擁有一個警示，導致一個根，可讓您更輕鬆地修正問題發生時。 根據 Uri 精簡的警示減少不必要的警示，並促進有效率的追蹤待處理問題。 如果發生訊息擱置的 URI 中沒有先前的擱置警示存在，便會建立新的警示。|  
|BAM 技術協助警示|已知與商務使用者的商務活動監控 (BAM) 入口網站使用者通常是了解的商務層級指標 」 和 「 商務活動。 使用監視彙總指示器、 完整的內含式商務交易，或搜尋具有特定屬性的交易的 BAM 入口網站，若要進一步調查。 不過，商務使用者通常不了解 IT 基礎結構層級問題的層面。 在調查特定交易，BAM 入口網站可讓商務使用者可以從 IT 作業人員調查 IT 基礎結構層級交易要求技術協助。<br /><br /> BAM 入口網站可透過技術協助要求，讓商務使用者不需經手這些工作。 要求技術協助建立裝載 BAM 入口網站之電腦的事件檢視器中的應用程式記錄檔中的項目。 這個事件包含的使用者和其他重要資訊，例如訊息執行個體識別項、 服務執行個體識別碼，與 BizTalk Server 群組資訊所要求技術協助活動的相關詳細資料。<br /><br /> BizTalk Server 管理組件包含可觸發偵測 BAM 技術協助事件警示的規則。 建立這個警示的規則是「錯誤：需要 BAM 技術協助。」 為每個從 BAM 入口網站提交的要求建立新的警示。|  
|BizTalk Messagebox 和主控件|BizTalk Server 管理組件加入了效能閾值規則，提供全面性的健康情況的 BizTalk MessageBox 資料庫和佇列。 提供兩種類型的臨界值規則：<br /><br /> -適用於以一般方式，也就是所有 BizTalk 主控件，所有 BizTalk MessageBox 資料庫的規則。<br />-為特定的 BizTalk 主控件或 MessageBox 專用規則。<br /><br /> 一般規則會監控所有 BizTalk Server 主控件或 MessageBox 資料庫根據通用閾值。 例如，「監控 HostQ 大小」規則會根據通用閾值監控所有 BizTalk Server 主控件的工作佇列。 如果三個主控件存在，所有工作佇列都監視由相同的規則，並且任何主控件工作佇列超越通用閾值時，會發生的警示。<br /><br /> BizTalk Server 主控件專用規則可讓您將不同的臨界值設定為不同的主控件和 MessageBox 資料庫。 例如，「監控 HostQ 大小 – BizTalkServerApplication」規則是監控 BizTalkServerApplication 主控件工作佇列的主控件專用規則。 您所定義的特定效能計數器執行個體的特定 Operations Manager 提供者和臨界值規則中使用該提供者。<br /><br /> 主控件\MessageBox 專用規則是以範本規則的形式提供，用來做為建立適用於個別環境之規則的指引。 一般規則必須以環境特有的閾值來設定。 BizTalk 主控件/MessageBox 專用規則必須根據範本規則和適當閾值來建立。<br /><br /> BizTalk Server 加入了自我節流功能，可協助防止多載根據各種不同的參數。 導致節流發生的暫時負載過重並非重大的作業事件。 但是，在穩定的環境中不應該持續發生節流事件，這可能表示基礎結構層級有根本的問題。 BizTalk Server 管理組件提供主動式監視的這類持續節流狀況與效能閾值監控器根據下列條件：<br /><br /> BizTalk Server 服務處理序記憶體<br />-正在處理的訊息數目<br />-BizTalk Server 程序中執行緒數目<br />-BizTalk 資料庫佇列的大小|  
|協調流程失敗|擱置協調流程的監視是另一個常見案例。 協調流程可能會失敗，因為許多原因而包含協調流程引擎問題、.NET 元件發生問題，以及程式邏輯。 請務必啟用快速判斷問題的來源，並繼續擱置的協調流程時固定的運算子。|  
|服務監視|BizTalk Server 需要許多服務正在執行才能正確運作。 這些服務的狀態將會對應至類別代表不同的 BizTalk 服務監視器。|  
|應用程式監視|BizTalk Server 在引進群組方案成品的應用程式的概念。 應用程式監視會偵測應用程式層級的失敗造成的影響。|